# Дневник ошибок

## Ошибка 1

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> diff = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int difference = target - nums[i];
            Integer diffItemIndex = diff.get(difference);
            if (diffItemIndex != null) {
                return new int[] {diffItemIndex, i};
            } else {
                diff.put(nums[i], i);
            }
        }
    }
}
```

Отсутствует `return null;` в конце метода, если мы так и не найдем нужную пару чисел. 
Несмотря на то, что условиями гарантируется наличие 1 такой пары чисел всегда, структура данных массив целых чисел нам этого не гарантирует.
Поскольку джава является строгим языком, то мы должны явно обработать такой кейс, иначе программа не скомпилируется. 