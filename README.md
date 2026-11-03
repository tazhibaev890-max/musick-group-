# Состав — кабинет участника группы

Фронтенд на TypeScript для регистрации и входа участников, а также просмотра и редактирования профиля.

## Локальный запуск

```bash
npm install
npm run dev
```

Публикационная сборка: `npm run build` (готовый сайт появится в `dist/`).

## Авторизация и API

Используется JWT API `https://inai-col3.fishrungames.com`:

- `POST /api/register/` и `POST /api/login/` выдают access-токен; refresh-токен хранится backend в HttpOnly cookie.
- `POST /api/token/refresh/` обновляет access-токен.
- `POST /api/logout/` завершает сессию.
- `GET /api/profile/` и `PATCH /api/profile/` читают и обновляют профиль.
- `GET /api/specializations/` загружает список специализаций.

Access-токен хранится только в памяти вкладки. Запросы передают cookie через `credentials: include`.

## GitHub Pages

Workflow `.github/workflows/deploy.yml` собирает сайт при push в ветку `main` и публикует `dist/` через GitHub Pages. В настройках репозитория выберите **Settings → Pages → Build and deployment → Source: GitHub Actions**. В `vite.config.ts` используется относительный base path, поэтому сайт работает и в Pages-проекте вида `username.github.io/repository/`.
