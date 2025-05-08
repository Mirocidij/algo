# Дневник ошибок

## Ошибка 1

```java
class Solution {
    public ListNode reverseList(ListNode head) {
        if (head == null) return null;

        ListNode prev = null;
        ListNode curr = head;

        while (current != null) {
            ListNode next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;
        }

        return prev;
    }
}
```

В while (current != null) мы ссылаемся на переменную current, хотя такая в коде не объявлена. Объявлена переменная curr.