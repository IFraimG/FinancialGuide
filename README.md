# FinancialGuide

Веб-приложение для анализа финансов и доходов, разработанное в рамках хакатона VTB API 2024.

[![Netlify](https://img.shields.io/badge/deploy-netlify-00C7B7)](https://xmisfinancialguide.netlify.app/)

## Технологии

- TypeScript
- Vue3 (Composition API)
- Vue-Router
- vue-chart.js
- SCSS
- Vite
- ESLint + Prettier
- Netlify (деплой)

## Архитектурные решения

### Компонентная структура
Компоненты разбиты по доменным директориям: `feature_main` и `feature_financy`. Переиспользуемые UI-примитивы вынесены в `components/ui`.

### Визуализация данных через Chart.js
Страница анализа доходов строит два линейных графика через `vue-chart.js`: динамика фактических доходов по месяцам и сравнение с потенциальным доходом от инвестиций. Настройки осей, легенды и цветовой схемы вынесены в `src/utils/chartSettings.ts`.

### Интеграция с Banking API
Приложение ориентировано на работу с API банкинга. Токен доступа передаётся через переменную окружения `VITE_API_ACCESS_TOKEN`, которая настраивается отдельно для dev- и production-сборок через файлы `.env.dev` и `.env.production`.

### Разделение стилей по фичам
SCSS-файлы структурированы зеркально компонентам: `feature_main/` и `feature_financy/`. Глобальная цветовая палитра вынесена в `colors.scss`, базовые сбросы и типографика — в `base.scss`.

## Структура проекта
```
├── .github/
├── .vscode/
├── cypress/                         
├── public/
├── src/
│   ├── assets/
│   │   ├── images/
│   │   └── styles/
│   │       ├── base.scss
│   │       ├── colors.scss           
│   │       ├── main.scss
│   │       ├── feature_financy/
│   │       │   ├── financy_main.scss
│   │       │   └── media/
│   │       │       └── media_financy_main.scss
│   │       └── feature_main/
│   │           ├── main_footer.scss
│   │           ├── main_header.scss
│   │           ├── main_main.scss
│   │           ├── main_modal.scss
│   │           └── media/
│   │               ├── media_main_header.scss
│   │               └── media_main_main.scss
│   ├── components/
│   │   ├── feature_financy/
│   │   │   └── FinancyAds.vue         # Блок рекомендаций по инвестициям
│   │   ├── feature_main/
│   │   │   ├── CustomFooter.vue
│   │   │   ├── CustomHeader.vue
│   │   │   ├── MainInfo.vue           # Баланс, доходы, реквизиты, детали счёта
│   │   │   └── ModalAuth.vue          # Модальное окно авторизации
│   │   └── ui/
│   │       └── MainCard.vue          
│   ├── router/
│   │   └── index.ts                  
│   ├── stores/            
│   ├── utils/
│   │   └── chartSettings.ts           
│   ├── views/
│   │   ├── FinancyView.vue            # Анализ доходов с линейными графиками
│   │   ├── HomeView.vue               # Главная страница (баланс, авторизация)
│   │   └── NotFound.vue              # Страница 404
│   ├── App.vue
│   └── main.ts
├── .editorconfig
├── .env.dev                           # VITE_API_ACCESS_TOKEN (development)
├── .env.production                    # VITE_API_ACCESS_TOKEN (production)
├── .gitignore
├── .prettierrc.json
├── cypress.config.ts
├── env.d.ts
├── eslint.config.js
├── index.html
├── package.json
├── tsconfig.app.json
├── tsconfig.json
├── tsconfig.node.json
├── tsconfig.vitest.json
├── vite.config.ts
├── vitest.config.ts
└── yarn.lock
```
