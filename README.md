# PHP Credit Card Validator

[![License](https://poser.pugx.org/irabbi360/php-credit-card-validator/license)](https://packagist.org/packages/irabbi360/php-credit-card-validator)
[![Latest Stable Version](https://poser.pugx.org/irabbi360/php-credit-card-validator/version)](https://packagist.org/packages/irabbi360/php-credit-card-validator)
[![Total Downloads](https://poser.pugx.org/irabbi360/php-credit-card-validator/downloads)](https://packagist.org/packages/irabbi360/php-credit-card-validator)
[![Daily Downloads](https://poser.pugx.org/irabbi360/php-credit-card-validator/d/daily)](https://packagist.org/packages/irabbi360/php-credit-card-validator)

Validates popular debit and credit card numbers against regular expressions and the Luhn algorithm.
It also validates the CVC and the expiration date.

## Installation

Require the package in `composer.json`

```json
"require": {
    "irabbi360/php-credit-card-validator": "1.*"
},
```

If you are using Laravel, add an alias in `config/app.php`

```php
'aliases' => array(

    'App'             => 'Illuminate\Support\Facades\App',
    ...
    'View'            => 'Illuminate\Support\Facades\View',

    'CreditCard'      => 'Irabbi360\CreditCard',

),
```

## Usage

### Validate a card number knowing the type:

```php
$card = CreditCard::validCreditCard('5500005555555559', 'mastercard');
print_r($card);
```

Output:

```
Array
(
    [valid] => 1
    [number] => 5500005555555559
    [type] => mastercard
)
```

### Validate a card number and return the type:

```php
$card = CreditCard::validCreditCard('371449635398431');
print_r($card);
```

Output:

```
Array
(
    [valid] => 1
    [number] => 371449635398431
    [type] => amex
)
```

### Validate the CVC

```php
$validCvc = CreditCard::validCvc('234', 'visa');
var_dump($validCvc);
```

Output:

```
bool(true)
```

### Validate the expiration date

```php
$validDate = CreditCard::validDate('2013', '07'); // past date
var_dump($validDate);
```

Output:

```
bool(false)
```

## Tests

Execute the following command to run the unit tests:

    vendor/bin/phpunit
