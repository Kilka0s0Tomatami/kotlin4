# Логирование жизненного цикла Activity

## 1. Запуск приложения
При запуске приложения в логах появятся следующие сообщения:
```
D/Lifecycle: onCreate called
D/Lifecycle: onStart called
D/Lifecycle: onResume called
```
**Обоснование:**
- `onCreate()` вызывается при создании Activity.
- `onStart()` вызывается, когда Activity становится видимой.
- `onResume()` вызывается, когда Activity переходит в активное состояние.

## 2. Включение режима поворота и поворот экрана
Логи при повороте экрана:
```
D/Lifecycle: onPause called
D/Lifecycle: onStop called
D/Lifecycle: onDestroy called
D/Lifecycle: onCreate called
D/Lifecycle: onStart called
D/Lifecycle: onResume called
```
**Обоснование:**
- При изменении конфигурации (поворот экрана) система уничтожает текущую Activity (`onPause()`, `onStop()`, `onDestroy()`).
- Затем создается новая Activity (`onCreate()`, `onStart()`, `onResume()`).

## 3. Сворачивание приложения
Логи при сворачивании:
```
D/Lifecycle: onPause called
D/Lifecycle: onStop called
```
**Обоснование:**
- `onPause()` вызывается перед скрытием Activity.
- `onStop()` вызывается, когда Activity полностью скрыта.

## 4. Вызов `finish()` в `onCreate()`
Логи при таком запуске:
```
D/Lifecycle: onCreate called
D/Lifecycle: onDestroy called
```
**Обоснование:**
- `finish()` завершает Activity сразу после `onCreate()`, поэтому вызывается `onDestroy()`.

## Вывод
Логирование позволяет проследить, как система управляет жизненным циклом Activity. При повороте экрана Activity пересоздается, при сворачивании — останавливается, а при `finish()` — сразу уничтожается.

