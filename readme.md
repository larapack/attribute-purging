# attribute-purging
Allows you to define what attributes in your Eloquent Model which should be not be inserted into the database.

## Installing

Install using Composer `composer require larapack/attribute-purging`.

## Usage

First add the trait `Purgeable` to your Eloquent Model.
```
<?php

namespace App;

use Larapack\AttributePurging\Purgeable;

class User
{
  use Purgeable;
  
  /**
   * @var array List of attribute names which should be purged
   */ 
  protected $purge = ['foo']; // set the attribute names you which to purge
  
  //...
}
```

Test:
```
$user = new App\User;
$user->foo = 'bar';
$user->save(); // The attribute 'foo' will not be saved to the database.
echo $user->foo; // Will still returns 'bar' as long you hold the same instance of the object.
```
