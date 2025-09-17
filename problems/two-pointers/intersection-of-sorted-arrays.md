# Общие элементы массивов

#легко #яндекс

Даны два отсортированных по возрастанию массива `nums1` и `nums2`. Необходимо вернуть новый массив `nums3`, который содержит все общие элементы из `nums1` и `nums2` .

Результат должен быть также отсортирован по возрастанию.Если элементы встречаются в массивах несколько раз, то их нужно продублировать в ответе.

**Пример 1:**  

```
Ввод: nums1 = [-3,2,2,5,8,19,31], nums2 = [1,2,2,2,6,19,52]
Вывод: [2,2,19]
```

**Пример 2:**

```
Ввод: nums1 = [-5,4], nums2 = [1,2]
Вывод: []
```

**Пример 3:**

```
Ввод: nums1 = [], nums2 = [1,2]
Вывод: []
```

**Ограничения:**

- `len(nums1), len(nums2) >= 0`
# Решение

```java
import java.util.*;

// time: O(n+m)
// space: O(min(n, m))
public class Solution {
    public List<Integer> intersect(List<Integer> nums1, List<Integer> nums2) {
        var result = new ArrayList<Integer>();
        int p1 = 0, p2 = 0;
        while (p1 < nums1.size() && p2 < nums2.size()) {
            if (nums1.get(p1) < nums2.get(p2)) {
                p1++;
                continue;
            }
            if (nums1.get(p1) > nums2.get(p2)) {
                p2++;
                continue;
            }
            result.add(nums1.get(p1));
            p1++;
            p2++;
        }
        return result;
    }
}
```

# FAILS

## FAIL 1

```java
import java.util.*;

// time: O(n+m)
// space: O(min(n, m))
public class Solution {
    public List<Integer> intersect(List<Integer> nums1, List<Integer> nums2) {
        var result = new ArrayList();
        int p1 = 0, p2 = 0;
        while (p1 < nums1.size() || p2 < nums2.size()) {
            if (nums1.get(p1) < nums2.get(p2)) {
                p1++;
                continue;
            }
            if (nums1.get(p1) > nums2.get(p2)) {
                p2++;
                continue;
            }
            result.add(nums1.get(p1));
            p1++;
            p2++;
        }
        return result;
    }
}
```

Вообще не указал дженерик и обосрался с условием выхода из цикла. Надо было &&, а я поставил ||