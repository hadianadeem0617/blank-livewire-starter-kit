# Blank Livewire Starter Kit — Laravel Livewire 3 Boilerplate 🚀

[![Releases](https://img.shields.io/badge/Releases-Download-blue?logo=github)](https://github.com/hadianadeem0617/blank-livewire-starter-kit/releases)

![Laravel + Livewire](https://laravel.com/img/logomark.min.svg) ![Livewire](https://user-images.githubusercontent.com/315070/175547482-cb00f6b7-0e2a-4b8e-b0f4-1b4f4f5a5f3d.png)

Download the packaged release from https://github.com/hadianadeem0617/blank-livewire-starter-kit/releases, save the asset, and run the included setup script or installer that ships with the release.

This repository provides a minimal, well-structured starter kit for Laravel apps that use Livewire 3 and Tailwind. It gives you a clear base to build on while keeping the stack small and focused. The kit does not include any authentication scaffolding.

- If you want the release archive, go to the Releases page linked above and download the asset you need.
- After downloading, run the installer included in the release distribution (for example, a setup.sh or install.php file).

## Why use this starter kit

- Keep the backend in PHP and Blade while building reactive UI with Livewire.
- Skip heavy JS frameworks for common app UIs.
- Ship a focused stack: Laravel, Livewire 3, Tailwind CSS, Volt theme (UI).
- Start with a clean code layout and common build scripts.

## Features

- Livewire 3 components and lifecycle examples
- Blade-first approach for pages and UI
- Tailwind CSS preconfigured with sensible defaults
- Laravel Volt theme integration for layout and components
- Vite build config tuned for Laravel + Livewire
- Example components: modal, table, form wiring
- No auth or user scaffolding; add what you need

## Tech stack

- Laravel (latest LTS compatible)
- Livewire 3
- Tailwind CSS
- Vite
- Laravel Volt theme
- Composer, NPM/Yarn

## Requirements

- PHP 8.1 or later
- Composer 2+
- Node.js 16+ and npm or Yarn
- A database driver (MySQL, PostgreSQL, SQLite)
- Git for code management

## Quick start

1. Clone the repo or download a release build from the Releases page:
   https://github.com/hadianadeem0617/blank-livewire-starter-kit/releases
2. Move into the project folder.
3. Install PHP dependencies with Composer.
4. Install frontend dependencies and build assets.
5. Copy .env.example to .env and set the app key.
6. Run migrations and seeders if included.
7. Start the dev server.

Example commands:

```bash
git clone https://github.com/hadianadeem0617/blank-livewire-starter-kit.git
cd blank-livewire-starter-kit

composer install
cp .env.example .env
php artisan key:generate

npm install
npm run dev

php artisan migrate
php artisan serve
```

If you downloaded a release asset from the Releases page, extract the archive, then run the included setup script. The release bundle includes a setup script to automate dependency install and basic configuration.

## Project structure

- app/ — core app code and Livewire components
- resources/views/ — Blade templates and layouts
- resources/js/ — entry points for Vite and Livewire scripts
- resources/css/ — Tailwind entry
- routes/ — web and api routes
- database/ — migrations and seeders
- tests/ — example tests
- vite.config.js — Vite + Laravel config
- tailwind.config.js — Tailwind config
- composer.json, package.json — dependency manifests

## Livewire usage notes

- Components live in app/Http/Livewire or app/Livewire depending on preferred structure.
- Use wire:model, wire:click, and lifecycle hooks for reactive UI.
- For file uploads, use Livewire's temporary upload handling.
- Prefer small, focused components for reuse.

Example Livewire component:

```php
namespace App\Http\Livewire;

use Livewire\Component;

class Counter extends Component
{
    public int $count = 0;

    public function increment()
    {
        $this->count++;
    }

    public function render()
    {
        return view('livewire.counter');
    }
}
```

And Blade:

```blade
<div>
  <button wire:click="increment">Increment</button>
  <span>{{ $count }}</span>
</div>
```

## Frontend and Tailwind

- Tailwind is configured with Purge to remove unused styles in production.
- Vite handles asset bundling and HMR.
- The Volt theme provides base styles and components. Override the theme in resources/css and component slots.

Common scripts in package.json:

- npm run dev — start Vite dev server
- npm run build — build production assets
- npm run prod — alias for production build

## Environment and config

- Copy .env.example to .env
- Set DB_CONNECTION, DB_HOST, DB_DATABASE, DB_USERNAME, DB_PASSWORD
- Set APP_URL for correct asset generation
- Set MAIL and queue drivers as needed

Run these commands after adjusting .env:

```bash
php artisan key:generate
php artisan migrate
php artisan cache:clear
php artisan route:clear
```

## Testing

- PHPUnit is configured for basic tests.
- Use php artisan test or vendor/bin/phpunit.
- Add tests in tests/Feature and tests/Unit.

Example:

```bash
php artisan test --filter ExampleTest
```

## Common artisan commands

- php artisan migrate
- php artisan migrate:fresh --seed
- php artisan make:livewire ComponentName
- php artisan vendor:publish --tag=livewire:assets
- php artisan optimize

## Deployment guidelines

- Build assets with npm run build on CI.
- Run composer install with --no-dev on production.
- Set APP_ENV=production and APP_DEBUG=false.
- Use a process manager (Supervisor, systemd) for queues and workers.
- Serve via PHP-FPM + Nginx, or use Forge / Vapor as you prefer.

## No authentication included

This starter kit does not include auth scaffolding. You can add:

- Laravel Breeze for simple auth
- Laravel Fortify for custom auth flows
- Jetstream or other packages if you need teams or session features

Keep auth code separate for clarity. The starter kit keeps scope small so teams can pick the auth system they need.

## Contributing

- Fork the repo and open a pull request.
- Keep changes small and focused.
- Add tests for new behavior.
- Follow PSR-12 and Laravel conventions.
- Refer to the official Laravel contribution guide for process and standards.

Official contribution docs: https://laravel.com/docs/contributions

## Code of conduct

This project follows a code of conduct to keep the community safe and respectful. Please see the Code of Conduct file in the repo for details.

## FAQ

Q: Can I use this with existing Laravel projects?
A: Yes. Extract the Livewire and Tailwind configs you need and merge them into your project. Watch for Vite config differences.

Q: Does this support SSR?
A: Livewire does not use server-side rendering like classic SSR. It keeps Blade on the server and syncs UI with small AJAX calls.

Q: Where do I add global JS?
A: Use resources/js/app.js and import from there. Vite will bundle it.

## Troubleshooting

- Assets not loading: confirm APP_URL and run npm run build.
- Livewire events not firing: ensure @livewireScripts is in your layout and Vite includes Livewire plugin assets if used.
- Migration issues: check DB connection and run php artisan migrate:fresh.

## Resources

- Livewire docs: https://livewire.laravel.com
- Laravel starter kits: https://laravel.com/docs/starter-kits
- Tailwind CSS: https://tailwindcss.com
- Vite: https://vitejs.dev

## Releases

Download a packaged release, then run the setup script that comes with the release build. Visit the Releases page to pick a version and extract the archive:

https://github.com/hadianadeem0617/blank-livewire-starter-kit/releases

## License

This project uses the MIT License. See the LICENSE file for details.

## Credits

- Laravel and the framework team
- Livewire maintainers
- Tailwind CSS authors
- Community contributors and testers

<!-- End of README -->