# Правильный палиндром

#средне #яндекс

Дана строка `s`. Верните `true`, если `s` является палиндромом, или `false` в противном случае.
Фраза является палиндромом, если после преобразования всех заглавных букв в строчные и удаления всех символов, кроме букв и цифр,
она читается одинаково слева направо и справа налево.

Буквенно-цифровые символы включают латинские буквы и цифры.

**Пример 1:**  

```
Ввод: s = "A man, a plan, a canal: Panama"
Вывод: true
Объяснение: строка "amanaplanacanalpanama" является палиндромом
```

**Пример 2:**

```
Ввод: s = "AbaCdaba"
Вывод: false
```

**Ограничения:**

- `len(s) >= 1`

# Решение

```Java
import java.util.*;

public class Solution {
    public boolean isPalindrome(String s) {
        int p1 = 0, p2 = s.length() - 1;
        while (p1 < p2) {
            if (!Character.isLetterOrDigit(s.charAt(p1))) {
                p1++;
                continue;
            }
            if (!Character.isLetterOrDigit(s.charAt(p2))) {
                p2--;
                continue;
            }
            if (Character.toLowerCase(s.charAt(p1)) != Character.toLowerCase(s.charAt(p2))) {
                return false;
            }
            p1++;
            p2--;
        }

        return true;
    }
}
```

Решение с 4 попытки

# Fails

## Fail 1

```java
import java.util.*;

public class Solution {
    public boolean isPalindrome(String s) {
        int p1 = 0, p2 = s.length() - 1;
        while (p1 < p2) {
            if (!Character.isLetterOrDigit(s.chartAt(p1))) {
                p1++;
                continue
            }
            if (!Character.isLetterOrDigit(s.chartAt(p2))) {
                p2--;
                continue
            }
            if (s.chartAt(p1) != s.chartAt(p2)) {
                return false;
            }
            p1++;
            p2--;
        }

        return true;
    }
}
```

Не добавил точку с запятой после continue почему-то, это очень плохо и минус балл.

## FAIL 2

```java
import java.util.*;

public class Solution {
    public boolean isPalindrome(String s) {
        int p1 = 0, p2 = s.length() - 1;
        while (p1 < p2) {
            if (!Character.isLetterOrDigit(s.chartAt(p1))) {
                p1++;
                continue;
            }
            if (!Character.isLetterOrDigit(s.chartAt(p2))) {
                p2--;
                continue;
            }
            if (s.chartAt(p1) != s.chartAt(p2)) {
                return false;
            }
            p1++;
            p2--;
        }

        return true;
    }
}
```

Здесь ошибка и того хуже. Опечатка в названии метода `charAt` -> `chartAt`. Ужас

## FAIL 3

```java
import java.util.*;

public class Solution {
    public boolean isPalindrome(String s) {
        int p1 = 0, p2 = s.length() - 1;
        while (p1 < p2) {
            if (!Character.isLetterOrDigit(s.charAt(p1))) {
                p1++;
                continue;
            }
            if (!Character.isLetterOrDigit(s.charAt(p2))) {
                p2--;
                continue;
            }
            if (Character.toLowerCase(s.charAt(p1)) != Character.toLowerCase(s.charAt(p2))) {
                return false;
            }
            p1++;
            p2--;
        }

        return true;
    }
}
```

По какой-то причине я вообще решил проигнорировать условие, что для сравнения все заглавные буквы должны приводиться к строчным.
Задача реально сложная, но общую идею решения я вспомнил сразу, так что это лайк мне