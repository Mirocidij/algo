# Неточный поиск

#легко #т-банк 

Даны две строки `s` и `t` ``. Необходимо определить, можно ли получить строку `s` ``, удаляя некоторые (возможно, ни одного) символы из строки `t` ``, не изменяя порядок оставшихся символов.

**Пример 1:**  

Ввод: s = "abc", t = "a1b2c3"
Вывод: True
Объяснение: Можно удалить цифры из t, чтобы получить t = "abc"

**Пример 2:**

Ввод: s = "abc", t = "acb"
Вывод: False

**Ограничения:**

- `len(s) ≥ 0`
- `len(t) ≥ 0`
- Строки `s` и `t` содержат только `ascii` символы

# Solution

```java
import java.util.*;

// time: O(n + m)
// space: O(1)
public class Solution {
    public boolean fuzzyMatch(String s, String t) {
        int p1 = 0, p2 = 0;
        while (p1 < s.length() && p2 < t.length()) {
            if (s.charAt(p1) == t.charAt(p2)) {
                p1++;
                p2++;
            } else {
                p2++;
            }
        }

        return p1 == s.length();
    }
}
```

Сдано с первой попытки

Хотя эталон с сайта выглядит вот так 

```java
import java.util.*;

public class Solution {
    public boolean fuzzyMatch(String s, String t) {
        int p1 = 0;
        int p2 = 0;

        // Пока не достигли конца хотя бы одной из строк
        while (p1 < s.length() && p2 < t.length()) {
            if (s.charAt(p1) == t.charAt(p2)) {
                // Если символы совпадают — продвигаем указатель по s
                p1++;
            }
            // Всегда двигаем указатель по t
            p2++;
        }
        return p1 == s.length();
    }
}
```