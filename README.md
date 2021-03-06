# superobject
数组转化的超级对象

# how to use
## step 1
- npm install -g cnpm --registry=https://registry.npm.taobao.org
- cnpm install superobject --save

- 或者使用 yarn add superobject

## step 2
最好在全局引用
import 'superobject';

- use

<pre>
var arr = [
    { id: 1, a: 1, b: 2, c: 3 },
    { id: 2, a: 1, b: 3, c: 4 },
    { id: 3, a: 1, b: 4, c: 5 },
    'a',
    'b',
    true,
    3,
    3,
    [4, 5],
];

var mysuperobject = arr.superobject();

实现方法很简单，你可以直接打印arr.superobject()查看结果。
superobject存在的意义在于，当你想根据id从数组取值时，不得不
对该数组进行遍历，当查询对次时会多次调用遍历函数；
在这之前，我们先把数组转化成超级对象，当我们想要查询某个
id对应的信息时，直接取值即可，除了初次的转化，无需其它运算。

同时应当注意的是，应尽量少的使用arr.superobject()方法调用，
否则superobject也就失去了意义。

<h4>一、查询数组内元素为键值对象的信息</h4>
1、key=value的查询方式（查询到多条记录）
console.log(mysuperobject['a=1']);
{ 
    accurate: false, // 是否查询到精确记录
    superInfo: '目标包含多个搜索内容，具体见参数explainArr或arr', 
    explainArr: [ // 带有index标记的信息集合
        { value: { ... }, index: 0 },
        { value: { ... }, index: 2 }, 
        ...
    ],
    arr: [ ... ] // 原始记录信息集合
} 
2、key=value的查询方式（查询到精确记录）
console.log(mysuperobject['id=1']);
{ 
    accurate: true, // 是否查询到精确记录
    index: 0,
    superInfo: "以获取精准定位，目标=this",
    value: {id: 1, a: 1, b: 2, c: 3}
}

<h4>二、查询数组内元素为非对象的信息</h4>
1、value的查询方式（查询到多条记录）
console.log(mysuperobject[3]);
2、value的查询方式（查询到精确记录）
console.log(mysuperobject[true]);
显示信息同一

<h4>三、同状态下的多次查询（查询到多条记录情况下）</h4>
var searchResult1 = mysuperobject['a=1'].arr;
var searchResult2 = searchResult1.superobject()['b=3'];

解决重复劳动力是一件很有意义的事情，
有什么好的想法，欢迎一起成长交流
WeChat：mrliaojun
</pre>

### github
[Jared](https://github.com/aisriver/superobject.git)