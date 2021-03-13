# PHP 7.1

[1. Nullable types](#nullable-types)

[2. Iterable and Void Returns](#iterable-and-void-returns)

[3. Multi-Catch Exception Handling](#multi-catch-exception-handling)

[4. Chia mảng đối xứng](#chia-mảng-đối-xứng)

[5. Keys Can Now Be Used in Lists](#keys-can-now-be-used-in-lists)

[6. More Negative String Offsets](#more-negative-string-offsets)

## Nullable types

có thể check null cho tham số truyền vào hoặc kết quả trả về

```php
function showColor(?string $color) {
    if ($color) {
        echo $color;
    }
}

showColor( '#ff9900' );
// Works just fine, a string has been given

showColor( null );
// Works fine, null is allowed
```

## Iterable and Void Returns

```php
function perform_a_job() : void {
    return;
    // This is fine, it returns null
}

function perform_a_task() : void {
    // This is also fine, it returns null
}

function perform_another_task() : void {
    return true;
    // This will return an error since it is not void
}
```

```php
function fonc01(iterable $data) {
    foreach ($data as $key => $val) {
        //....
    }
}

fonc01(new SplFixedArray(5));
// Works kist fine, SplFixedArray implements Iterator
// See http://php.net/manual/en/class.splfixedarray.php
```

## Multi-Catch Exception Handling

```php
try {
    // some code
} catch (FirstException | SecondException $e) {
    // handle first and second exceptions
}
```

## Chia mảng đối xứng

```php
$arr = [
    [0, 'Nguyen Van A'],
    [1, 'Tran Thi B']
  ];
  [$id, $name] = $arr[0];
  echo $id; //0
  echo $name; //Nguyen Van A
```

## Keys Can Now Be Used in Lists

```php
$data = [
    ["id" => 1, "name" => 'Tom'],
    ["id" => 2, "name" => 'Fred'],
];

// list() style
list("id" => $id1, "name" => $name1) = $data[0];

// [] style
["id" => $id1, "name" => $name1] = $data[0];

// list() style
foreach ($data as list("id" => $id, "name" => $name)) {
    // logic here with $id and $name
}

// [] style
foreach ($data as ["id" => $id, "name" => $name]) {
    // logic here with $id and $name
}
```

## More Negative String Offsets

```php
$name = "Daniel";
echo "My name ends in an '$name[-1]'. Nice!";
```
