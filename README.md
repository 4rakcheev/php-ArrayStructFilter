# ArrayStructFilter

## Using
```php
$list = [
            [
                'int'=>1,
                'value'=>null,
                'color'=>'red',
            ],
            [
                'int'=>0,
                'value'=>'string',
                'color'=>'red',
            ],
            [
                'int'=>1,
                'value'=>'second_string',
                'color'=>'brown',
            ],
        ];
        
$brownFilter = new AStructFilter($list, ['int'=>1, 'color'=>'brown'], AStructFilter::CONDITION_AND);
$result = $brownFilter->run();
print_r($result);
```
## Result
```bash
Array
(
    [2] => Array
        (
            [int] => 1
            [value] => second_string
            [color] => brown
        )
 
)
```
