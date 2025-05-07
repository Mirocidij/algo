# Дневник решений

## Ссылка на задачу

https://leetcode.com/problems/two-sum/

## Оптимальное решение которое работает за O(n) по времени и O(n) по памяти на Java

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

        return null;
    }
}
```

## Объяснение

Находясь на определенном элементе массива nums мы всегда знаем, какого числа нам не хватает, чтобы получился target. Вычисляется это по формуле target - nums[i].
Мы заводим словарик в котором ключами будут выступать значения элементов массива nums, а ключами их индексы. Таким образом, находясь на определеном элементе мы можем проверить,
а нет ли в нашем массиве такого элемента, который в сумме с текущим давал бы target. Если он есть, то мы возвращаем ответ, если его нет, то мы добавляем в хешмап элемент массива и его индекс `put(nums[i], i)`.