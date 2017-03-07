# Promise

## 基本介绍
CatMicro框架内置的Promise对象有三个核心函数：`then`,`resolve`和`reject`。

* then 设置两个回调函数，分别用于接收`resolve`和`reject`传过来的值。
* resolve 将Promise设置为完成状态，并传递一个`value`值
* reject 将Promise设置为拒绝状态，并传递一个`reason`值

## 并行调用

Promise提供两个用于并行调用的方法`Promise::all`和`Promise::any`。

`Promise::all`接收一个数组作为参数，数组成员可以是一个值，也可以是一个Promise对象。该方法返回一个新的Promise对象，当且仅当数组中所有的对象都成功返回（普通的值直接返回，Promise对象需要进入完成状态并返回`value`）时，该对象的`resolve`回调被调用；任一对象进入拒绝状态，则该对象的`reject`对象会被调用。

`Promise::any`接收一个数组作为参数，数组成员可以是一个值，也可以是一个Promise对象。该方法返回一个新的Promise对象，当且仅当数组中所有的对象都被拒绝（普通的值直接返回认为是成功状态，Promise对象需要进入拒绝状态）时，该对象的`reject`回调被调用；任一对象返回成功，则该对象的`resolve`对象会被调用。

## 协程封装

Promise提供了一个`Promise::co`方法实现了协程的封装。开发者可以将需要使用协程的代码包裹在`Promise::co`函数的作用域内，如下所示：

```php
Promise::co(function(){
    $result = yield test_yield();
});
```