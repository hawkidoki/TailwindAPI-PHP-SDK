# TailwindAPI.com - PHP SDK

A `CURL` wrapper to build TailwindCSS with PHP.

### Default usage

```php
require('tailwindapi.php');

$css = $tailwind->build(); // Return default Tailwind compilation
```

### Default arguments

```php
$css = $tailwind->build(array(
    'css'           => false, // Default Tailwind PostCSS (@tailwind base; @tailwind components; @tailwind utilities;)
    'config'        => false, // Default Tailwind Config
    'autoprefixer'  => true,  // Autoprefixer enabled
    'minify'        => true,  // Minify enabled
    'output'        => false, // Return compiled CSS
));
```

### Custom inline configuration

```php
$css = $tailwind->build(array(
    'css' => '
        @tailwind base;
        @tailwind components;
        @tailwind utilities;
    ',
    'config' => '
    module.exports = {
        theme: {
            colors: {
                indigo: '#5c6ac4',
                blue: '#007ace',
                red: '#de3618',
            }
        }
    }
    ',
));
```

### Custom configuration files

```php
$css = $tailwind->build(array(
    'css' => 'path/to/postcss-file.css',
    'config' => 'path/to/config.js',
));
```

### Ouput to file

```php
$tailwind->build(array(
    'output' => 'path/to/output.css', // PHP will need write permission
));
```
