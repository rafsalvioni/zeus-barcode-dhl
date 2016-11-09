# zeus-barcode-dhl
Provides a Objected-Oriented API to create, draw and manipulate barcode data using DHL (Deutsche Post) standards

## Example
Required packages...
```json
{
    "require": {
        "rafsalvioni/zeus-barcode-dhl": "1.*",
        "rafsalvioni/zeus-barcode-renderer-svg": "1.*"
    }
}
```
Code example
```php
<?php
require 'vendor/autoload.php';

use Zeus\Barcode\Renderer\SvgRenderer;

$bcs = [
    new \Zeus\Barcode\DHL\Leitcode('21348075016401'),
    new \Zeus\Barcode\DHL\Identcode('563102430313'),
];

$render = new SvgRenderer();
$render->merge = true;

foreach ($bcs as &$bc) {
    $bc->border = 2;
    $bc->showText = true;
    $bc->draw($render);
    $render->offsetTop += $bc->getTotalHeight() + 50;
}
$render->render();
```

