**phpy is library for php**

***

You can use python in php with it

***
**Install**

```batch
composer require raeen/phpy
```

**Python**

We use these libraries for create phpy.py:

```python
import sys
import json
import base64
import numpy as np
import cv2
```

Import phpy.py file in Python/include/php.py 

***
**Get Data from php**

Get datas to python file
```python
import include.phpy as phpy

print({'name' : phpy.get_data(1)['name'] , 'library' : phpy.get_data(1)['library'] , 'text' : phpy.get_data(2)})
```
For Get data you must get_data( Number Of Send data )

For return data you must use print function
***

**Push data from python**
```python
phpy.push_data(data)
```
It's just 
```python
json.dumps(data)
```
***
**Push image from python**

It function for pushing data from python to php

Example for reading image
```python
cv2.imread()
```
```python
videoCaptureObject = cv2.VideoCapture(0)
ret, frame = videoCaptureObject.read()
```

Pushing image
```python
phpy.push_image(img,type)
```
***
**Send data from php**

Create and Send data from php to python 

You can send infinite data

```php
require_once "../vendor/autoload.php";

use app\core\App;

$app = new App();
$python = $app->python;

$data1 = [
    'name' => 'raeen',
    'library' => 'phpy'
];
$data2 = "test";
$output = $python->gen("../Python/test2.py", $data1, $data2);
```
***
**Show result**

```php
$output = $python->gen(path,datas...)
```

In $output you have python result also you can gen_line() function for return last line of result

If result is json , you should use this

```php
$python->dump($json_data,$pre_tag)
```
This function for json decoding 

If $pre_tag is true , show result in pre tag
***
**Show Img**

You can use this function to genrate what's return from phpy.push_img()
```php
$python->img($output,$type,$show,$style)
```
**$type must be same type in php.push_img()**

If $show is true , show image in img tag

Also you can set style for this

Example
```php
$python->img($output,$type,true,
[
    'border' => '1px solid red'
]
)
```
***
**Path**

For example , I have image file in this diractory but python file in Python/**.py and I want to send path to it . for this in must to send this path ../my-img Or use this functiuon for send path file

```php
$python->path_file(__Dir__,path form this file)
```

Or send path diractory 
```php
$python->path(__Dir__,path form this file)
```
***
**Ini**

If you have loop in php file it's very good to add this function in top of file

```php
$python->ini()
```
***
**Example**

There are examples in php and python diractory
***
**BY RAEEN AHANI**"# phpy" 
