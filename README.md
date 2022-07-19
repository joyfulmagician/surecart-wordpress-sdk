# SureCart Theme and Plugin Licensing SDK

- [Installation](#installation)


## Installation

Clone the repository in your project.

```
cd /path/to/your/project/folder
git clone https://github.com/surecart/wordpress-sdk.git licensing
```

Now include the dependencies in your plugin/theme.

```php
if ( ! class_exists( 'SureCart\Licensing\Client' ) ) {
    require_once __DIR__ . '/licensing/src/Client.php';
}
```


### Usage Example

Please refer to the **installation** step before start using the class.

You can obtain the **hash** for your plugin for the [Appsero Dashboard](https://dashboard.appsero.com). The 3rd parameter **must** have to be the main file of the plugin.

```php

if ( ! class_exists( 'SureCart\Licensing\Client' ) ) {
    require_once __DIR__ . '/licensing/src/Client.php';
}

// initialize client with your plugin name.
$client = new \SureCart\Licensing\Client( 'Your Plugin', __FILE__ );

// add the pre-built license settings page.
$client->settings()->add_page( 
    [
        'type'        => 'submenu', // Can be: menu, options, submenu
        'parent_slug' => 'your-plugin-menu-slug', // add your plugin menu slug.
        'page_title'  => 'Manage License',
        'menu_title'  => 'Manage License',
        'capability'  => 'manage_options',
        'menu_slug'   => $this->client->slug . '-manage-license',
        'icon_url'    => '',
        'position'    => null,
        'parent_slug' => '',
    ] 
);
```

Make sure you call this function directly, never use any action hook to call this function.

> For plugins example code that needs to be used on your main plugin file.
> For themes example code that needs to be used on your themes `functions.php` file.

## More Usage

```php
$client = new \SureCart\Licensing\Client(  'Twenty Twelve', __FILE__ );
```

## Set textdomain

You may set your own textdomain to translate text.

```php
$client->set_textdomain( 'your-project-textdomain' );
```
