![TailwindAPI.com - PHP SDK](https://user-images.githubusercontent.com/5537083/78453825-8eb9cc80-7694-11ea-8c5d-4c551d565820.png)

# TailwindAPI.com - PHP SDK

A `CURL` wrapper to build TailwindCSS with PHP.

Installed PostCSS plugins: 
* [Autoprefixer](https://github.com/postcss/autoprefixer)
* [CSSNano](https://github.com/cssnano/cssnano)
* [PostCSS Nested](https://github.com/postcss/postcss-nested)
* [PostCSS Prefix Selector](https://github.com/RadValentin/postcss-prefix-selector)

Installed TailwindCSS plugins:
* [Tailwind Custom Forms](https://github.com/tailwindcss/custom-forms)

### Default usage

```php
// Load
require('tailwindapi.php');

// Init
$tailwind = new TailwindAPI();

// Build
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
        
        .btn{
            
            @apply bg-blue-500 font-bold;
            
            &:hover{
                @apply bg-blue-800;
            }
            
        }
        
        @tailwind utilities;
    ',
    'config' => '
        module.exports = {
            theme: {
                colors: {
                    indigo: "#5c6ac4",
                    blue: "#007ace",
                    red: "#de3618",
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

### Prefixer usage

```php
$css = $tailwind->build(array(
    'prefixer' => '.my-prefix'
));
```

```php
$css = $tailwind->build(array(
    'prefixer' => array(
        'prefix' => '.my-prefix',
        'exclude' => array('html')
    )
));
```

### Ouput to file

```php
$tailwind->build(array(
    'output' => 'path/to/output.css', // PHP will need write permission
));
```
