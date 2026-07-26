# ChillOS Website — GitHub Pages build

Готовый статический сайт ChillOS Python Core без серверной части и без системы сборки.

## Публикация на GitHub Pages

Загрузите содержимое этой папки в корень ветки, выбранной в **Settings → Pages**. Файл `.nojekyll` отключает обработку Jekyll, а `404.html` используется GitHub Pages как пользовательская страница Not Found.

Главная страница: `index.html`.

## Локализация

На сайте используется только собственный словарь в `assets/js/site.js`:

- English
- Українська
- Русский
- Беларуская
- Қазақша

Google Translate и связанные cookie, виджеты и внешние скрипты полностью отсутствуют. Язык сохраняется в `localStorage`. Геолокация определяет только первоначальный язык и региональные элементы:

- Украина → украинский;
- Россия → русский;
- Казахстан → казахский;
- Беларусь → автоматический выбор языка отключён;
- остальные страны → английский.

Ручной выбор всегда имеет приоритет. Для проверки используются параметры `?geo=UA`, `?geo=RU`, `?geo=KZ`, `?geo=BY` и `?lang=en|uk|ru|be|kk`.

## Условия использования

Все пять официальных редакций EULA встроены непосредственно в `terms.html`. Страница не выполняет `fetch`, не зависит от каталога `assets/legal` и работает на GitHub Pages и при открытии через `file://`.

## Оптимизация

Сайт использует один CSS-файл `assets/css/site.css` и один отложенно загружаемый JavaScript-файл `assets/js/site.js`. Нижние секции применяют `content-visibility`, а геоопределение запускается после первичной отрисовки, имеет тайм-аут и кешируется на семь дней. Внешних библиотек и фреймворков нет.

## Шрифт

CSS ожидает лицензированную копию шрифта по пути:

`assets/fonts/GoogleSans.ttf`

Файл шрифта в архив не включён. При его отсутствии используется системный sans-serif. На сайте размещена ссылка на официальную страницу Google Sans.

## Основные страницы

- `index.html` — главная и интерактивная HTML/CSS/JS-симуляция ChillOS;
- `developers.html` — правила разработки и распространения;
- `dmca.html` — политика DMCA;
- `terms.html` — полностью встроенные условия использования;
- `404.html` — стилизованная критическая ошибка.

Репозиторий проекта: https://github.com/chillosprod/chillos-python-core


## Region detection and testing (v2)

The site now performs a fresh IP-country check on every page load and uses the short local cache only if all live providers fail. It also checks again when the tab regains focus, which makes VPN changes visible after returning to the page. Click the regional status in the footer to force an immediate recheck.

Test modes:

- `?geo=UA`, `?geo=RU`, `?geo=KZ`, `?geo=BY` — fixed region override.
- `?geotest=1` — opens a local region test panel; switch between Auto, UA, RU, KZ, BY and Standard without a VPN.
- `?resetLocale=1` — clears the manually saved language before testing automatic language selection.
- Combined example: `index.html?geotest=1&resetLocale=1`.

## Layout fix in v4

The live ChillOS interface simulation is now placed below the hero text on every language and desktop width. This prevents long translated headings from compressing the preview.


### Flag display

Language selectors use the official national flags for English (United States), Ukrainian, Russian, Belarusian and Kazakh. The Ukrainian regional presentation remains unchanged. No opposition or alternative political flags are used.
