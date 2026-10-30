ПРОЕКТ «БИОМЫ И ИЗМЕРЕНИЯ» — интернет-магазин парфюмерии в пиксельном стиле
Практика CSS (лекции 6–7): блочная модель, текст, ссылки, позиционирование

Страницы: index.html, catalog.html, about.html, delivery.html, contact.html, cart.html
Стили:    style.css (единственный файл, подключён ко всем страницам через <link>)
Картинки: папка images (флаконы *.png, фон шапки bg-nav.jpg, фон баннера bcgdi.jpg)

Flexbox, Grid и медиазапросы не используются: сетка карточек и меню
сделаны через display: inline-block, как требует задание.


1. ПАЛИТРА (5 основных цветов)
--------------------------------------------------------------------
#140118   тёмно-фиолетовый   фон страницы, фон полей формы
#222222   тёмно-серый        карточки, форма, корзина, подложка шапки и подвала
#6a3fb5   фиолетовый         рамки карточек, кнопки, активный пункт меню, тень шапки
#ffff55   жёлтый             цены, hover-состояния, бейдж «Хит», заголовки секций
#55ffff   бирюзовый          заголовки карточек, ссылки в тексте, бейдж акции
          (тот же цвет записан как rgb(85, 255, 255) у a:link и .note)

Нейтральные: white (основной текст) и black (пиксельные тени и рамки).
Оттенок акцента #8a5fd5 — hover кнопок, посещённые ссылки, старая цена.

Все три записи цвета: название (white, black), HEX (#6a3fb5), RGB (rgb(85, 255, 255)
и rgba(20, 1, 24, 0.9) у подложки баннера).


2. СПИСОК КЛАССОВ
--------------------------------------------------------------------
Контейнер и текст
  .container        колонка контента: max-width 1100px, margin: 0 auto
  .page             отступы основной области страницы
  .page__title      заголовок h1 страницы
  .section          смысловой блок страницы, отступ снизу 48px
  .section__title   заголовок h2 блока
  .intro            вводный абзац по центру
  .text             блок обычного текста, абзацы с text-indent
  .note             мелкая курсивная подпись

Шапка и меню
  .header           закреплённая шапка (sticky, z-index 100)
  .logo             название магазина, ссылка на главную
  .menu             блок навигации
  .menu__list       сброшенный список (list-style: none; padding: 0)
  .menu__item       пункт меню, display: inline-block
  .menu__link       ссылка меню, display: block + padding (кликабелен весь пункт)
  .menu__link--active   подсветка текущей страницы

Баннер главной
  .hero             баннер с фоновой текстурой
  .hero__box        полупрозрачная подложка с текстом
  .hero__title      заголовок h1 баннера
  .hero__text       текст баннера

Карточки
  .cards            контейнер сетки, text-align: center
  .card             карточка: inline-block, position: relative, рамка, тень
  .card--compact    компактная карточка на главной (описание скрыто)
  .card--info       текстовая карточка без картинки (о нас, доставка, контакты)
  .card__img        картинка флакона, display: block, margin: 0 auto
  .card__title      название аромата
  .card__subtitle   русское название, пол, семейство (курсив)
  .card__desc       описание характера
  .card__notes      пирамида нот
  .card__price      цена
  .card__old-price  старая цена с line-through
  .badge            бейдж в углу карточки, position: absolute
  .badge--sale      бейдж акции (бирюзовый)

Кнопки и списки
  .btn              кнопка и ссылка-кнопка, display: inline-block
  .btn--secondary   второстепенная кнопка (серая)
  .list             маркированный список с квадратным маркером
  .list--steps      нумерованный список шагов (decimal-leading-zero)

Форма
  .form             карточка формы, max-width 600px по центру
  .form__label      подпись поля, display: block
  .form__field      поле ввода, display: block, width 100%
  .form__status     строка статуса под формой

Корзина
  .cart__items      список товаров
  .cart__empty      сообщение «корзина пуста», скрыто через display: none
  .cart-item        строка товара
  .cart-item__img   картинка товара, inline-block
  .cart-item__info  название и цена, inline-block
  .cart-item__name  название товара
  .cart-item__price количество и цена
  .cart__summary    блок итога
  .cart__total      строка «Итого»
  .cart__actions    кнопки корзины

Подвал и прочее
  .footer           подвал с текстурой
  .footer__list     сброшенный список ссылок
  .footer__item     пункт подвала, display: inline
  .footer__link     ссылка подвала
  .footer__copy     строка копирайта
  .to-top           кнопка «Наверх», position: fixed, z-index 50

Единственный id-селектор: #cart-total (итоговая сумма, элемент существует
на сайте в одном экземпляре, поэтому id здесь уместен).


3. ТАБЛИЦА «СВОЙСТВО → ГДЕ ПРИМЕНЕНО»
--------------------------------------------------------------------
Селекторы
  тег                     body, img, h1/h2/h3, a:link
  класс                   .card, .btn, .menu__link и ещё 50+ классов
  id                      #cart-total
  потомок                 .card--compact .card__desc, .cart__actions .btn, .list li
  группа                  h1, h2, h3 { font-weight: normal }  /  .card__desc, .card__notes
  *                       * { box-sizing: border-box; margin: 0 }

Цвета и шрифты
  font-family списком     body: "Press Start 2P", "Courier New", monospace
  Google Fonts            Press Start 2P (поддерживает кириллицу)
  font-size в rem         body 0.75rem, h1 1.5rem, подписи 0.625rem, бейдж 0.5rem
  font-weight             h1, h2, h3 — normal (у пиксельного шрифта одно начертание,
                          синтетический bold размывает буквы)
  font-style              .card__subtitle, .note — italic
  line-height             body 1.6; .card__desc 1.7; .page__title 1.3
  text-align              .cards, .page__title (center), .cart__summary (right)
  text-transform          .menu__link, .page__title, .badge — uppercase
  letter-spacing          .page__title 2px, .logo 1px
  text-decoration         a:link underline, a:hover none, .card__old-price line-through
  text-indent             .text p — 24px (красная строка)
  text-shadow             заголовки и ссылки шапки — пиксельная тень

Блочная модель
  box-sizing              * { box-sizing: border-box } в начале файла
  width / max-width       .card width 100% + max-width 320px; .container max-width 1100px
  height                  .to-top 48px
  max-width: 100% у img   img { max-width: 100%; height: auto }
  margin: 0 auto          .container, .form, .hero__box, .card__img, .intro
  padding — 1 значение    .card--... padding: 24px (.form), 16px (.cart-item)
  padding — 2 значения    .btn 12px 16px, .card 24px 16px
  padding — 3 значения    .page 32px 16px 48px, .header 16px 0 0
  padding — 4 значения    .hero__box 24px 16px 32px 16px
  margin — 3 значения     .card 0 8px 24px, .card__img 0 auto 16px
  margin — 4 значения     .list 0 0 16px 24px, .cart__actions .btn 0 0 8px 8px
  border                  .card 2px solid #6a3fb5, .btn 3px solid black
  border-radius           .card, .btn, .form, .to-top — 4px; .badge — 2px
  box-shadow              .card 4px 4px 0 black (пиксельная тень), .header 0 4px 0 #6a3fb5,
                          .form__field:focus 0 0 0 2px #ffff55
  background-color        body, .card, .btn, .badge, .form__field
  background (shorthand)  .header и .footer: цвет + bg-nav.jpg + позиция / размер + repeat-x;
                          .hero: bcgdi.jpg с размером 240px

Ссылки, списки, меню
  LVHA                    a:link → a:visited → a:hover → a:active (ссылки в тексте);
                          тот же порядок у .menu__link, .footer__link, .logo, .btn, .to-top
  ссылка-кнопка           .btn: inline-block, padding, background, :hover
                          (<a class="btn"> «Смотреть каталог», «В корзину», «В каталог»)
  список со своим маркером  .list (square, жёлтый маркер через ::marker),
                          .list--steps (decimal-leading-zero)
  сброшенный список       .menu__list и .footer__list: list-style: none; padding: 0
  горизонтальное меню     ul.menu__list > li.menu__item (inline-block) > a.menu__link (block)

display
  block                   .menu__link, .card__img, .form__label, .form__field, .to-top
  inline                  .footer__item (пункты подвала идут строкой), .card__old-price
  inline-block            .menu__item, .card, .btn, .logo, .cart-item__img, .cart-item__info
  none                    .card--compact .card__desc (на главной длинное описание скрыто),
                          .cart__empty (сообщение о пустой корзине скрыто, пока есть товары)

position
  relative + absolute     .card { position: relative } и .badge { position: absolute;
                          top: -2px; right: -2px } — бейдж в углу карточки
  sticky                  .header { position: sticky; top: 0 } — шапка едет за прокруткой
  fixed                   .to-top { position: fixed; right: 16px; bottom: 16px }
  relative (сдвиг)        .btn:active { top: 3px; left: 3px } — кнопка «вдавливается»
  z-index                 .header 100, .to-top 50, .badge 1 — шапка и кнопка не прячутся
                          под карточками с тенями

Единицы
  rem                     все размеры шрифта
  %                       .card width 100%, .form__field width 100%, .cart-item__info 60%
  px                      рамки, тени, отступы (шаг 8px), max-width контейнеров


4. ПРИМЕР СПЕЦИФИЧНОСТИ
--------------------------------------------------------------------
В файле есть общее правило для ссылок в тексте:

    a:link { color: rgb(85, 255, 255); text-decoration: underline; }

Пункты меню — тоже ссылки, но они должны быть белыми и без подчёркивания:

    .menu__link:link, .menu__link:visited { color: white; text-decoration: none; }

Специфичность a:link = (0,1,1): один псевдокласс + один тег.
Специфичность .menu__link:link = (0,2,0): класс + псевдокласс.
(0,2,0) больше (0,1,1), поэтому побеждает правило с классом независимо от
порядка в файле. То же самое с .btn:link (кнопки белые) и .footer__link:link.

Мы на этом споткнулись: сначала text-decoration: none стояло в простом
правиле .menu__link (0,1,0), и подчёркивание от a:link (0,1,1) всё равно
оставалось, хотя правило с классом шло ниже в файле. Порядок не помог,
потому что специфичность важнее порядка.

Второй пример — порядок правил: .card__desc задаёт блок с текстом, а идущее
ниже .card--compact .card__desc { display: none } скрывает его на главной.
Здесь побеждает и более высокая специфичность (два класса), и порядок.


5. САМОСТОЯТЕЛЬНО ИЗУЧЕННЫЕ СВОЙСТВА
--------------------------------------------------------------------
:focus          .form__field:focus — при вводе рамка поля становится жёлтой и
                появляется внешняя обводка через box-shadow. Без этого пользователь
                не видит, в каком поле курсор, потому что outline отключён.
::marker        .list li::marker { color: #ffff55 } — красит только маркер списка,
                не трогая текст пункта.
image-rendering: pixelated — флаконы нарисованы на сетке 24×36 пикселей; без этого
                браузер размывает их при увеличении.
scroll-behavior: smooth на html — кнопка «Наверх» прокручивает страницу плавно.


6. ЕДИНЫЙ ШАГ ОТСТУПОВ
--------------------------------------------------------------------
Все padding и margin кратны 8px: 8, 16, 24, 32, 48.
Исключения только у декоративных сдвигов: тень 3–4px, бейдж −2px (на толщину рамки),
нажатие кнопки 3px.


7. ЧТО НЕ ПОЛУЧИЛОСЬ / ЗАМЕЧАНИЯ
--------------------------------------------------------------------
- Корзина и форма пока статичные: JavaScript в этом задании не требовался,
  поэтому кнопки «Удалить», «Очистить», «Оформить заказ» и «Отправить» ничего не делают.
  Товары в корзине показаны как пример вёрстки.
- Скидки на Creeper, Deep Dark и Taiga (−20%, −15%, −10%) выставлены для примера,
  их легко поменять в index.html и catalog.html.
- Без медиазапросов (они запрещены на этом этапе) на узких экранах карточки
  просто переносятся на новую строку, а меню занимает две строки.
- Между inline-block карточками остаётся небольшой зазор от пробелов в HTML,
  это нормальное поведение inline-block.
- Две картинки с персонажем игры в папке images остались от предыдущего этапа
  и на страницах не используются.
