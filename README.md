# wp_theme_settings
**A custom WordPress class for creating theme settings page (Compatible Wordpress 4.5+, Tested on Wordpress 4.7.3)**

![Extras](http://i.imgur.com/UI3WnJk.png)

**Rework coming**

NOTE
----
This is a utility class intended to create a theme settings page. Read full [docs](https://github.com/mattiasghodsian/wp_theme_settings/wiki) and [changelog](https://github.com/mattiasghodsian/wp_theme_settings/blob/master/changelog.md)

Installation
------------
Place **wp_theme_settings.php**, **wp_theme_settings.js** and **wp_theme_settings.css**  in your WordPress theme folder `/wp-content/your-theme/`

Open your WordPress themes **functions.php** file  `/wp-content/your-theme/functions.php` add the following code:

```php
include 'wp_theme_settings.php';
```

Add both CSS & JS file to Wordpress with **admin_enqueue_scripts**

```php
add_action('admin_enqueue_scripts', 'wp_theme_settings_add_stylesheet');
function wp_theme_settings_add_stylesheet(){
  wp_enqueue_style('wp_theme_settings', get_template_directory_uri().'/wp_theme_settings.css');
  wp_register_script('wp_theme_settings',get_template_directory_uri() . '/wp_theme_settings.js', array( 'wp-color-picker' ));
  wp_enqueue_script('wp_theme_settings');
}
```



Example
------------
```php
include 'wp_theme_settings.php';

$wpts = new wp_theme_settings(
  array(
    'general' => array('description' => 'A custom WordPress class for creating theme settings page'),
    'settingsID' => 'wp_theme_settings',
    'settingFields' => array('wp_theme_settings_title'), 
    'tabs' => array(
      'general' => array('text' => 'General', 'dashicon' => 'dashicons-admin-generic' ),
      'buttons' => array('text' => 'Buttons')
      ),
  )
);

add_action('wpts_tab_general' , 'general');
function general(){
?>
<p><label>Title</label></p>
<input type="text" name="wp_theme_settings_title" value="<?php echo esc_attr( get_option('wp_theme_settings_title') ); ?>" />
<?php

}

add_action('admin_enqueue_scripts', 'wp_theme_settings_add_stylesheet');
function wp_theme_settings_add_stylesheet(){
  wp_enqueue_style('wp_theme_settings', get_template_directory_uri().'/wp_theme_settings.css');
  wp_register_script('wp_theme_settings',get_template_directory_uri() . '/wp_theme_settings.js', array('jquery'));
  wp_enqueue_script('wp_theme_settings');
}
```
# Donate
[![Beerpay](https://beerpay.io/mattiasghodsian/wp_theme_settings/badge.svg?style=flat-square)](https://beerpay.io/mattiasghodsian/wp_theme_settings)

[![Donate with Ethereum](https://en.cryptobadges.io/badge/small/0xBBB96204E45D11C9799c6B12E6eE6F0d4A071Ef5)](https://en.cryptobadges.io/donate/0xBBB96204E45D11C9799c6B12E6eE6F0d4A071Ef5)
