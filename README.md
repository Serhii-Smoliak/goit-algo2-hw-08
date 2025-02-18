# goit-algo2-hw-08

----

# Завдання 1. Реалізація Rate Limiter з використанням алгоритму Sliding Window для обмеження частоти повідомлень у чаті

## Приклад використання
```bash
  python task1.py
```

## Виведе:
### Симуляція потоку повідомлень

| Повідомлення | Користувач | Статус                |
|--------------|------------|-----------------------|
| 1            | 2          | ✓                     |
| 2            | 3          | ✓                     |
| 3            | 4          | ✓                     |
| 4            | 5          | ✓                     |
| 5            | 1          | ✓                     |
| 6            | 2          | × (очікування 7.2с)   |
| 7            | 3          | × (очікування 7.0с)   |
| 8            | 4          | × (очікування 6.5с)   |
| 9            | 5          | × (очікування 6.6с)   |
| 10           | 1          | × (очікування 6.8с)   |

**Очікуємо 4 секунди...**

### Нова серія повідомлень після очікування

| Повідомлення | Користувач | Статус                |
|--------------|------------|-----------------------|
| 11           | 2          | ✓                     |
| 12           | 3          | × (очікування 0.1с)   |
| 13           | 4          | ✓                     |
| 14           | 5          | × (очікування 0.3с)   |
| 15           | 1          | × (очікування 1.0с)   |
| 16           | 2          | × (очікування 8.4с)   |
| 17           | 3          | ✓                     |
| 18           | 4          | × (очікування 7.7с)   |
| 19           | 5          | ✓                     |
| 20           | 1          | ✓                     |

## Висновок:
Симуляція показує, що успішна доставка повідомлень чергується з очікуванням через затримки, але більшість повторних спроб завершуються успіхом.

----

# Завдання 2. Реалізація Rate Limiter з використанням алгоритму Throttling для обмеження частоти повідомлень у чаті

## Приклад використання
```bash
  python task1.py
```

## Виведе:
### Симуляція потоку повідомлень (Throttling)

| Повідомлення | Користувач | Статус             |
|--------------|------------|--------------------|
| 1            | 2          | ✓                  |
| 2            | 3          | ✓                  |
| 3            | 4          | ✓                  |
| 4            | 5          | ✓                  |
| 5            | 1          | ✓                  |
| 6            | 2          | × (очікування 8.5с) |
| 7            | 3          | × (очікування 8.1с) |
| 8            | 4          | × (очікування 7.4с) |
| 9            | 5          | × (очікування 7.0с) |
| 10           | 1          | × (очікування 6.8с) |

Очікуємо 10 секунд...

### Нова серія повідомлень після очікування

| Повідомлення | Користувач | Статус             |
|--------------|------------|--------------------|
| 11           | 2          | ✓                  |
| 12           | 3          | ✓                  |
| 13           | 4          | ✓                  |
| 14           | 5          | ✓                  |
| 15           | 1          | ✓                  |
| 16           | 2          | × (очікування 8.3с) |
| 17           | 3          | × (очікування 8.4с) |
| 18           | 4          | × (очікування 7.7с) |
| 19           | 5          | × (очікування 7.5с) |
| 20           | 1          | × (очікування 7.1с) |

## Висновок:
Алгоритм Throttling ефективно обмежує частоту повідомлень, забезпечуючи мінімальний інтервал очікування між ними.