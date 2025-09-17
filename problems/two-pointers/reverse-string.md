# Разворот строки

#легко  #озон

Дан список символов`chars`. Нужно развернуть`chars`и вернуть измененный список в качестве ответа.

**Пример 1:**

```
Ввод: chars = ["p","e","r","f","e","c","t","i","o","n"]
Вывод: ["n","o","i","t","c","e","f","r","e","p"]
```

**Пример 2:**

```
Ввод: chars = ["r","e","v","e","r","s","e"]
Вывод: ["e","s","r","e","v","e","r"]
```

**Ограничения:**

- `len(chars) >= 0`
- `chars` содержит только `ascii` символы


# Решение

```java
import java.util.*;

public class Solution {
    public List<Character> reverse(List<Character> chars) {
        int p1 = 0, p2 = chars.size() - 1;

        while(p1 < p2) {
            char c = chars.get(p1);
            chars.set(p1, chars.get(p2));
            chars.set(p2, c);
            p1++;
            p2--;
        }

        return chars;
    }
}
```

Решение сдано со 2 попытки

# FAILS

## FAIL 1

```java
import java.util.*;

public class Solution {
    public List<Character> reverse(List<Character> chars) {
        int p1 = 0, p2 = chars.size() - 1;

        while(p1 < p2) {
            char c = chars.get(p1);
            chars.set(p1, chars.get(p2));
            chars.set(p2, c);
        }

        return chars;
    }
}
```

Какая досада, забыл уменьшить счетчики. Ужас