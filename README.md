# mifekspro.github.io

Статический сайт-витрина: портативный лаунчер, отдельная «Битва построек» и сервер для неё.
Без Google-скриптов, без Firebase, без внешних API — только HTML/CSS/JS, поэтому ничего не «слетит».

## Состав

- `index.html` — главная: карточки скачивания, шаги, команды сервера
- `404.html` — страница ошибки
- `favicon.svg` — иконка
- `.nojekyll` — отключает обработку Jekyll на GitHub Pages (нужен, чтобы файлы отдавались как есть)

## Как опубликовать (5 минут)

1. Войди в GitHub под новым аккаунтом `mifekspro`.
2. Создай репозиторий с именем **`mifekspro.github.io`** (именно так), тип Public, без README.
3. Залей файлы из этой папки в ветку `main`:

```bash
cd C:\Users\ми\Desktop\mifekspro.github.io
git init
git add .
git commit -m "site: launcher and build battle"
git branch -M main
git remote add origin https://github.com/mifekspro/mifekspro.github.io.git
git push -u origin main
```

4. В репозитории: Settings → Pages → Source: **Deploy from a branch**, Branch: `main`, папка `/ (root)` → Save.
5. Через 1–2 минуты сайт откроется на **https://mifekspro.github.io**

Пока репозитория нет, адрес `mifekspro.github.io` отдаёт **404** — это нормально, страница ещё не создана.

## Куда положить архивы

GitHub Pages не принимает файлы больше 100 МБ, а архивы весят 56–213 МБ.
Поэтому архивы кладём в **Releases** того же репозитория (до 2 ГБ на файл):

1. Репозиторий → Releases → Draft a new release, тег `v1.0`.
2. Прикрепи три файла (кнопка Attach binaries):
   - `mifekspro-portable.zip` (213 МБ)
   - `bitva-postroek-standalone.zip` (56 МБ)
   - `bitva-postroek-server.zip` (182 МБ)
3. Publish release. Ссылки будут вида:
   `https://github.com/mifekspro/mifekspro.github.io/releases/download/v1.0/mifekspro-portable.zip`
4. Впиши их в `index.html` в блок `DOWNLOADS`:

```js
var DOWNLOADS = {
  portable:   "https://github.com/mifekspro/mifekspro.github.io/releases/download/v1.0/mifekspro-portable.zip",
  standalone: "https://github.com/mifekspro/mifekspro.github.io/releases/download/v1.0/bitva-postroek-standalone.zip",
  server:     "https://github.com/mifekspro/mifekspro.github.io/releases/download/v1.0/bitva-postroek-server.zip"
};
```

5. `git add index.html && git commit -m "links" && git push`

## Где сейчас лежат архивы

`E:\BuildBattle\`

- `mifekspro-portable.zip` — лаунчер + Java 25 + Minecraft 26.3 + моды
- `bitva-postroek-standalone.zip` — только «Битва построек» + Java
- `bitva-postroek-server.zip` — Fabric-сервер 26.3 + мод + Java

## Проверка после публикации

- `https://mifekspro.github.io` — открывается главная
- `/404.html` — красивая ошибка
- кнопки «Скачать ZIP» ведут на файлы релиза
