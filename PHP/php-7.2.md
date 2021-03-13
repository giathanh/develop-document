# PHP 7.2

[1. New object type](#new-object-type)

[2. Object return type declarations](#object-return-type-declarations)

[3. Parameter Type Widening](#parameter-type-widening)

[4. Trailing commas in list syntax](#trailing-commas-in-list-syntax)

[5. Ghi đè abstract method](#ghi-đè-abstract-method)

## New object type

```php
class MyClass {
	public $var = '';
}

class FirstChild extends MyClass {
	public $var = 'My name is Jim';
}
class SecondChild extends MyClass {
	public $var = 'My name is John';
}

$firstchild = new FirstChild;
$secondchild = new SecondChild;

function test(object $arg) {
	return $arg->var;
}

echo test($firstchild);

echo test($secondchild);
```

## Object return type declarations

```php
class MyClass {
	public $var = 'Hello World';
}

$myclass = new MyClass;

function test(MyClass $arg) : object {
	return $arg;
}

echo test($myclass)->var;
```

## Parameter Type Widening
Giờ đây bạn đã có thể thay đổi type của parameter được định nghĩa ở interface cha
```php
class MyClass {
	public function myFunction(array $myarray) { /* ... */ }
}

class MyChildClass extends MyClass {
	public function myFunction($myarray) { /* ... */ }
}
```

## Trailing commas in list syntax

```php
use Foo\Bar\{
    Foo,
    Bar,
    Baz,
};

$foo = [
    'foo',
    'bar',
];
```

## Ghi đè abstract method

```php
abstract class A
{
    abstract function test(string $s);
}

abstract class B extends A
{
    // overridden - still maintaining contravariance for parameters and covariance for return
    abstract function test($s) : int;
}
```