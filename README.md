# CleanHTML

Making HTML clean since late 2012!

## Requirements
* PHP 5.2+
* HTMLPurifier
* php-xml

## How to use
```php

require 'cleanhtml.php';
$tidy = new CleanHTML('<p><strong>I need a shower. I am dirty HTML.</strong>');
$output = $tidy->Clean();
```

$output should now contain:
```html
<h2>I need a shower. I am dirty HTML.</h2>
```

Using the Clean function will remove tables, any Javascript or other non-friendly items that
you might not want to see from user submitted HTML.

## What does it do?
1. Removed additional spaces from HTML
2. Replaces multiple ``<br />`` tags with paragraph tags
3. Removes any ``<script>`` tags
4. Renames any ``<h1>`` tags to ``<h2>``
5. Changes ``<p><strong>`` tags to ``<h2>``
6. Replaces ``<h2><strong>`` with just ``<h2>`` tags
7. Removes weird ``<p><span>`` tags
8. Uses HTML purifier to only allow h1,h2,h3,h4,h5,p,strong,b,ul,ol,li,hr,pre,code tags
9. Runs steps 3->7 one more time, just to catch anything that might have missed by allowed tags
10. Outputs nice clean HTML \o/
