# QA report

Проверено для GitHub Pages:

- Google Translate, его виджет, cookie и загрузочные скрипты отсутствуют.
- Во всех пяти собственных локалях одинаковый набор ключей.
- Все ключи, используемые HTML-страницами, существуют в каждой локали.
- Пять официальных EULA встроены непосредственно в `terms.html`.
- `terms.html` не использует `fetch()` и не требует HTTP-сервера.
- Все страницы подключают только `assets/css/site.css` и отложенный `assets/js/site.js`.
- Синтаксис объединённого JavaScript проверен командой `node --check`.
- Локальные ссылки на CSS, JavaScript, favicon и страницы проверены.
- `404.html` и `.nojekyll` находятся в корне публикации.
- Архив проверен на целостность.

Полноценный визуальный прогон в реальном браузере в этом окружении не выполнялся.


## v2 fixes

- Replaced the English-language placeholder with a CSS-drawn United States flag (13 stripes, blue canton, star field).
- Rebuilt language picker opening/closing with direct event bindings, explicit open state and a higher stacking layer.
- Changed geolocation to network-first detection; a 30-minute cache is fallback-only.
- Added live recheck on focus/visibility, footer click recheck, query overrides and `?geotest=1`.
- Automatic region language changes no longer overwrite the user's manually saved language.

## Validation performed for this package

- `node --check assets/js/site.js`: passed.
- Static local-link validation for all HTML pages: passed.
- Translation parity: 173 keys in each of `en`, `uk`, `ru`, `be`, and `kk`.
- Inline Chromium/Playwright interaction test: language menu opens, closes, and changes language; passed with no console or page errors.
- Responsive picker test at 390 px, 768 px, and 1365 px viewport widths: passed.
- Terms test: all five embedded documents switch without network requests; passed.
- United States flag CSS test: stripe field, blue canton, and star field are all rendered; passed.
- Geolocation state test with mocked live provider responses: KZ → UA change is detected after `ChillGeo.refresh()`; passed.
- Real external geolocation requests could not be executed inside the isolated build container, so production detection relies on the documented HTTPS providers and keeps manual test overrides available.

## Russian hero layout regression

- Added a locale-specific desktop grid for `ru` so the long word “ВОССТАНАВЛИВАЙ” cannot force the interactive ChillOS preview into a narrow column.
- The preview now keeps a stable 520 px desktop width (480 px at the narrow end of the desktop breakpoint).
- Other locales and mobile/tablet breakpoints are unchanged.

## v4 hero layout regression fix

- The hero uses one global column for all locales.
- The live system preview is rendered below the text rather than beside it.
- Russian and other long headings can no longer reduce the preview width.
- Responsive limits remain in place at 1100 px, 820 px and 560 px.


## v5 flag policy update

- Ukrainian language and regional visuals remain unchanged.
- Russian language icons now use the official white-blue-red national flag.
- Belarusian language icons now use the official red-green national flag with a neutral CSS ornament at the hoist.
- English and Kazakh icons already used their official national flags and were left unchanged.
- All flag icons remain CSS-only and require no image downloads.
