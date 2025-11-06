## Кастомный Select 

Проект содержит нативный `<select>` со стилизацией без JavaScript, оформленный по БЭМ. Реализованы состояния `:hover`, `:focus-visible`, `:invalid`, `:disabled`, плавные переходы, адаптация для тёмной темы и режимов доступности.


### Структура БЭМ
- `select` — блок
- `select__label` — подпись
- `select__wrapper` — обёртка для позиционирования и иконки
- `select__control` — сам `<select>`
- `select__icon` — декоративная стрелка (не перехватывает события)
- `select__help` — вспомогательный/ошибочный текст
- Модификаторы размера блока: `select_size_s`, `select_size_m`, `select_size_l`

Пример разметки:

```html
<div class="select select_size_m">
  <label class="select__label" for="country">Выберите страну</label>
  <div class="select__wrapper">
    <select class="select__control" id="country" name="country" aria-describedby="country-help" required>
      <option value="" disabled selected>Выберите страну</option>
      <option value="ua">Украина</option>
      <option value="pl">Польша</option>
    </select>
    <span class="select__icon" aria-hidden="true"></span>
  </div>
  <p class="select__help" id="country-help">Пожалуйста, выберите страну.</p>
  <div class="spacer"></div>
  <button type="submit" class="button">Отправить</button>
  <!-- Кнопка и спейсер вынесены в классы, без инлайновых стилей -->
  <!-- Размер можно сменить: select select_size_s / select select_size_l -->
  <!-- Для состояния ошибки используется :invalid у .select__control -->
  <!-- Сообщение .select__help появляется через :has(.select__control:invalid) -->
</div>
```

### Доступность и семантика
- Используется нативный `<select>` и связанный `<label>` — лучшая семантика без JS.
- Сообщение об ошибке связано через `aria-describedby`.
- Видимый фокус реализован через `:focus-visible` и CSS-переменные кольца.

### Валидация
- Включена нативная HTML-валидация (`required`).
- Красная подсветка при ошибке (`:invalid`) и зелёная при валидном значении (`:valid`).
- Текст ошибки показывается через селектор `:has(.select__control:invalid)` у блока.

### Темизация и единицы измерения
- Все размеры — в `rem/em` (px не используется).
- Цвета и геометрия вынесены в CSS-переменные (`:root`).
- Поддержка тёмной темы через `@media (prefers-color-scheme: dark)`.
- Сниженное движение — `@media (prefers-reduced-motion: reduce)`.
- Высокая контрастность — `@media (forced-colors: active)`.

### Браузерная поддержка
- Основа — нативный `<select>`: поддерживается широко.
- Селектор `:has()` для показа `.select__help` поддерживается в современных Chrome/Edge/Safari/Firefox. В старых браузерах текст ошибки может не анимироваться/не показываться автоматически; валидность самого поля сохранится.

### Кнопка и утилиты
- `.button` — стили кнопки отправки без инлайновых стилей.
- `.spacer` — вертикальный отступ между элементами.

### Изменение размеров
Примените модификатор к блоку:

```html
<div class="select select_size_s">...</div>
<div class="select select_size_m">...</div>
<div class="select select_size_l">...</div>
```


