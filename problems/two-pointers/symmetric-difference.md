# Симметричная разница массивов

#two-pointers

#средне
### Условие

Даны два массива `nums1` и `nums2`, отсортированные по возрастанию и состоящие из уникальных элементов. Нужно найти все элементы, которые встречаются только в одном из массивов и вернуть их в порядке возрастания.

**Пример 1:**  

```
Ввод: nums1 = [1,5,7,9], nums2 = [2,3,5,6,7,8]
Вывод: [1,2,3,6,8,9]
```

**Пример 2:**

```
Ввод: nums1 = [2,3], nums2 = [1]
Вывод: [1,2,3]
```

**Ограничения:**

- `len(nums1) + len(nums2) >= 1`

### Решение

```Java
import java.util.*;

// time: O(n+m)
// space: O(n+m)
// [1,3,5]
//        ↑
// [2,4,6]
//      ↑
// [1,2,3,4,5]
public class Solution {
    public List<Integer> findDifference(List<Integer> nums1, List<Integer> nums2) {
        int p1 = 0, p2 = 0;
        var result = new ArrayList<Integer>();
        while (p1 < nums1.size() && p2 < nums2.size()) {
            if (nums1.get(p1) < nums2.get(p2)) {
                result.add(nums1.get(p1));
                p1++;
            } else if (nums1.get(p1) > nums2.get(p2)) {
                result.add(nums2.get(p2));
                p2++;
            } else {
                p1++;
                p2++;
            }
        }
        if (p1 != nums1.size()) {
            while (p1 < nums1.size()) {
                result.add(nums1.get(p1));
                p1++;
            }
        }
        if (p2 != nums2.size()) {
            while (p2 < nums2.size()) {
                result.add(nums2.get(p2));
                p2++;
            }
        }
        return result;
    }
}
```

Сдано со второй попытки

Эталонным решением считается что-то вроде этого

```java
import java.util.*;

// time: O(n+m)
// space: O(n+m)
// [1,3,5]
//        ↑
// [2,4,6]
//      ↑
// [1,2,3,4,5]
public class Solution {
    public List<Integer> findDifference(List<Integer> nums1, List<Integer> nums2) {
        int p1 = 0, p2 = 0;
        var result = new ArrayList<Integer>();
        while (p1 < nums1.size() || p2 < nums2.size()) {
            if (p1 >= nums1.size()) {
                result.add(nums2.get(p2));
                p2++;
                continue;
            }
            if (p2 >= nums2.size()) {
                result.add(nums1.get(p1));
                p1++;
                continue;
            }

            if (nums1.get(p1) < nums2.get(p2)) {
                result.add(nums1.get(p1));
                p1++;
            } else if (nums1.get(p1) > nums2.get(p2)) {
                result.add(nums2.get(p2));
                p2++;
            } else {
                p1++;
                p2++;
            }
        }
        
        return result;
    }
}
```

### Ошибки

#### Fail 1

```Java
import java.util.*;

// time: O(n+m)
// space: O(n+m)
// [1,3,5]
//        ↑
// [2,4,6]
//      ↑
// [1,2,3,4,5]
public class Solution {
    public List<Integer> findDifference(List<Integer> nums1, List<Integer> nums2) {
        int p1 = 0, p2 = 0;
        var result = new ArrayList<Integer>();
        while (p1 < nums1.size() && p2 < nums2.size()) {
            if (nums1.get(p1) < nums2.get(p2)) {
                result.add(nums1.get(p1));
                p1++;
            } else if (nums1.get(p1) > nums2.get(p2)) {
                result.add(nums2.get(p2));
                p2++;
            } else {
                p1++;
                p2++;
            }
        }
        if (p1 != nums1.size()) {
            while (p1 < nums1.size()) {
                result.add(nums1.get(p1));
                p1++;
            }
        }
        if (p2 != nums2.size()) {
            while (p2 < nums2.size()) {
                result.add(nums2.get(p2));
                p2++;
            }
        }
        result result;
    }
}
```

`result result` Надо внимательно смотреть на автокомплит, обидная ошибка, особенно если бы мне за нее сняли баллы.