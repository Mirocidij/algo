# Сортировка элементов в квадрате

#two-pointers

#легко 

#вк #т-банк #озон #яндекс 

### Условие

Дан массив nums, отсортированный в неубывающем порядке. Нужно вернуть отсортированный массив, состоящий из всех элементов массива nums, возведенных в квадрат.

Неубывающий порядок – порядок, где каждый следующий элемент больше или равен предыдущему.

#### Примеры:

```
Ввод: nums = [-3,-2,0,1,3,5]
Вывод: [0,1,4,9,9,25]
Пример 2:
```

```
Ввод: nums = [-5,-3,-1]
Вывод: [1,9,25]
Ограничения:
```

#### Ограничения

- len(nums) >= 1

### Решение

```Java
import java.util.*;

public class Solution {

    public List<Integer> sortedSquares(List<Integer> nums) {

        var result = new ArrayList<Integer>(nums.size());

        int p1 = 0, p2 = nums.size() - 1;

        while (p1 <= p2) {

            if (Math.abs(nums.get(p1)) > Math.abs(nums.get(p2))) {

                result.add(nums.get(p1) * nums.get(p1));

                p1++;

            } else {

                result.add(nums.get(p2) * nums.get(p2));

                p2--;

            }

        }

        Collections.reverse(result);

        return result;

    }

}
```

Сдано со второй попытки

### Ошибки

#### Fail 1

```Java
import java.util.*;

public class Solution {

    public List<Integer> sortedSquares(List<Integer> nums) {

        var result = new ArrayList<Integer>(nums.size());

        int p1 = 0, p2 = nums.size() - 1;

        while (p1 <= p2) {

            if (Math.abs(nums.get(p1)) > Math.abs(nums.get(p2))) {

                result.add(nums.get(p1) * nums.get(p1));

                p1++;

            } else {

                result.add(nums.get(p2) * nums.get(p2));

                p2--;

            }

        }

        Collections.revert(result);

        return result;

    }

}
```

`Collections.revert(result);` - Такого метода не существует, существует только метод reverse(); Наверное, это не критично, но стоит запомнить.