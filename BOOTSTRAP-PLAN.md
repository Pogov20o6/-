# План подключения Bootstrap в проект «Биомы и измерения»

**Цель:** выровнять карточки и сделать адаптивные раскладки, не меняя внешний вид сайта и не трогая `style.css`.

**Подход:** используем только сборку утилит `bootstrap-utilities.min.css`. В ней нет Reboot (базовых стилей для `body`, заголовков, ссылок) и нет компонентов, поэтому она не конфликтует с нашими классами `container`, `btn`, `card`, `badge`.

---

## Шаг 1. Подключение (все 6 страниц)

В `<head>` каждой страницы добавить строку **перед** `style.css`:

```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap-utilities.min.css" rel="stylesheet">
<link rel="stylesheet" href="style.css">
```

Страницы: `index.html`, `catalog.html`, `about.html`, `delivery.html`, `contact.html`, `cart.html`.

> Полный `bootstrap.min.css` не подключать: он перекрасит шрифт, кнопки и карточки.

## Шаг 2. Добавить классы в разметку

Классы Bootstrap дописываются рядом с существующими, например `class="cards d-flex flex-wrap justify-content-center"`.

| Блок | Страницы | Добавить к существующему классу | Результат |
|---|---|---|---|
| `.cards` | index, catalog, about, delivery, contact | `d-flex flex-wrap justify-content-center` | карточки одной высоты в ряду |
| `.cart__actions` | cart | `d-grid gap-2 d-sm-flex justify-content-sm-end` | кнопки столбиком на телефоне, в строку на десктопе |
| `.cart-item` | cart | `d-flex align-items-center gap-3 flex-column flex-sm-row` | картинка, название и цена в одну линию |
| `.menu__list` | все | `d-flex flex-wrap justify-content-center gap-3` | ровные промежутки в меню |
| `.footer__list` | все | `d-flex flex-wrap justify-content-center gap-3` | ровные промежутки в футере |
| `.form` | contact | `d-grid gap-3` | одинаковые отступы между полями |
| кнопка формы | contact | `w-100` | кнопка во всю ширину формы |

## Шаг 3. Правила для всех

- **Не использовать** классы компонентов: `btn`, `card`, `badge`, `container`, `form-control`, `navbar`, `table`. Они меняют внешний вид.
- **Не править `style.css`.** Все изменения только в HTML.
- **Добавлять только те свойства, которых у элемента ещё нет в CSS.** Утилиты Bootstrap идут с `!important` и перебьют наши стили. Например, `d-flex` на `.cards` безопасен, а `text-start` на карточке отменит наше `text-align: center`.
- JavaScript-компоненты Bootstrap (модалки, аккордеоны, тосты) не использовать: им нужен полный CSS.

## Шаг 4. Проверка

- Открыть каждую страницу на ширине **375 px**, **768 px** и **1100 px**.
- Сравнить со скриншотами «до»: шрифт, цвета, рамки и тени должны остаться прежними.
- Убедиться, что карточки выровнены по высоте, а кнопки корзины не ломаются на телефоне.
- Проверить консоль браузера: ошибок загрузки CSS быть не должно.

## Шаг 5. Git

- Ветка `feature/bootstrap-utilities` от `main`.
- Один коммит на шаг: подключение, карточки, корзина, меню и футер, форма.
- Pull request в `main`, ревью одного человека из команды.

---

## Справка: какие классы можно, какие нельзя

| Можно (утилиты) | Нельзя (компоненты) |
|---|---|
| `d-flex`, `d-grid`, `d-none`, `d-md-block` | `btn`, `btn-primary` |
| `flex-wrap`, `flex-column`, `flex-sm-row` | `card`, `card-body` |
| `justify-content-*`, `align-items-*` | `badge` |
| `gap-1` … `gap-5` | `container`, `row`, `col-*` |
| `w-100`, `h-100` | `form-control`, `form-label` |
| `visually-hidden`, `text-truncate` | `navbar`, `nav-link` |

Документация по утилитам: https://getbootstrap.com/docs/5.3/utilities/api/
