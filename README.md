# Wire Extender

<p align="center">
  <a href="https://wire-elements.dev" target="_blank">
    <img src="https://github.com/wire-elements/wire-extender/assets/1133950/00f84b00-b0fd-492d-90df-b201126d1c64" width="180" alt="Wire Extender">
  </a>
</p>

<p align="center">
  <a href="https://packagist.org/packages/wire-elements/wire-extender"><img src="https://img.shields.io/packagist/dt/wire-elements/wire-extender" alt="Total Downloads"></a>
  <a href="https://packagist.org/packages/wire-elements/wire-extender"><img src="https://img.shields.io/packagist/v/wire-elements/wire-extender" alt="Latest Stable Version"></a>
  <a href="https://packagist.org/packages/wire-elements/wire-extender"><img src="https://img.shields.io/packagist/l/wire-elements/wire-extender" alt="License"></a>
</p>

## Embed Livewire Components Anywhere

Wire Extender allows you to embed any Livewire component on any website or even within a static HTML file. Imagine embedding your Livewire-powered forms, chat widgets, or any other interactive components across different web platforms!

## Quick Demo

Create a new HTML file on your local machine with the following contents to get a Livewire-powered click counter:

```html
<html>
<head>
    <script src="https://unpkg.com/@wire-elements/wire-extender" data-uri="https://wire-elements.dev"></script>
</head>
<body>
    <livewire data-component="counter" data-params='{"count":10}'></livewire>
</body>
</html>
```

## Installation

> **Note:** Wire Extender is currently in development. Pull requests and feedback are welcome! 😄

1. Require the package via Composer:

   ```bash
   composer require wire-elements/wire-extender
   ```

2. Configure CSRF token verification:

    - For Livewire 10, open `app/Http/Middleware/VerifyCsrfToken.php` and add the `IgnoreForWireExtender` trait.
    - For Livewire 11, create a new middleware and replace the default one. (See full documentation for details)

3. Adjust CORS settings:

   Open `config/cors.php` and add `livewire/*` to the `paths` array.

## Creating an Embeddable Component

Add the `#[Embeddable]` attribute to your Livewire component class:

```php
use WireElements\WireExtender\Attributes\Embeddable;

#[Embeddable]
class Counter extends Component
{
    // Your component logic here
}
```

## Embedding a Component

1. Publish the `wire-extender.js` library:

   ```bash
   php artisan vendor:publish --tag=wire-extender
   ```

2. Include the script on the website where you want to embed your Livewire component:

   ```html
   <script src="//your-domain.com/vendor/wire-elements/wire-extender.js"></script>
   ```

3. Define the component you want to embed:

   ```html
   <livewire data-component="counter" data-params='{"count":10}'>
     <!-- Placeholder... -->
   </livewire>
   ```

## Advanced Configuration

- Custom asset URLs
- CDN usage
- Placeholder content

For more details on these advanced topics, please refer to the [full documentation](https://wire-elements.dev/blog/embed-livewire-components-using-wire-extender).

## Contributing

We welcome contributions! Please feel free to submit pull requests or open issues on our [GitHub repository](https://github.com/wire-elements/wire-extender).

## License

Wire Extender is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).