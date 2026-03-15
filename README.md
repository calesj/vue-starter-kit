# Laravel Vue Starter Kit

Personal starter kit based on Laravel 12 + Vue 3 + Inertia.js. Includes authentication pages, Tailwind CSS v4, TypeScript, SSR support, and a clean project structure ready to build on.

## Stack

- **Laravel 12** (PHP 8.2+)
- **Vue 3** with Composition API + `<script setup>`
- **Inertia.js v2**
- **Tailwind CSS v4**
- **TypeScript**
- **Vite 7** with SSR support
- **Ziggy** (named routes in JS)
- **VueUse** composable library

## Requirements

- PHP 8.2+
- Node.js 20+
- Composer

## Getting Started

```bash
# Via Laravel installer (recommended)
laravel new my-app --using=calesj/laravel-vue-starter-kit

# Or via Composer
composer create-project calesj/laravel-vue-starter-kit my-app
```

```bash
cd my-app
npm install
npm run dev
```

Both methods will automatically:

1. Copy `.env.example` to `.env`
2. Generate the application key
3. Create the SQLite database file
4. Run migrations

## Development

```bash
# Start all dev servers (Laravel, queue, Vite) concurrently
composer dev

# Or separately
php artisan serve
npm run dev
```

## Auth Routes

The following routes are registered out of the box:

| Method | URI                       | Name               | Description                 |
| ------ | ------------------------- | ------------------ | --------------------------- |
| GET    | `/login`                  | `login`            | Login page                  |
| POST   | `/login`                  | `login.store`      | Submit login                |
| GET    | `/forgot-password`        | `password.request` | Forgot password page        |
| POST   | `/forgot-password`        | `password.email`   | Send reset link             |
| GET    | `/reset-password/{token}` | `password.reset`   | Reset password page         |
| POST   | `/reset-password`         | `password.store`   | Submit new password         |
| POST   | `/logout`                 | `logout`           | Logout (auth middleware)    |
| GET    | `/dashboard`              | `dashboard`        | Dashboard (auth middleware) |

## Pages

```
resources/js/pages/
├── Welcome.vue          # Landing page
├── Dashboard.vue        # (create this for your app)
└── Auth/
    ├── Login.vue        # Login form
    ├── ForgotPassword.vue   # Forgot password form
    └── ResetPassword.vue    # Reset password form
```

## Building for Production

```bash
npm run build
php artisan optimize
```

## SSR

SSR is configured and ready. To run with SSR:

```bash
composer dev:ssr
```

## Linting & Formatting

```bash
# PHP
composer lint          # Fix with Pint
composer lint:check    # Check only

# JS/TS
npm run lint           # ESLint fix
npm run format         # Prettier fix
npm run types:check    # TypeScript check
```

## Testing

```bash
php artisan test
# or
composer test
```
