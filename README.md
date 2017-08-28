# lodash-use
项目中用到的lodash,都是最基本的用法，详细的还得看文档

废话不多，直接开始吧--------------------

## 检查是否为数组----_.isArray
```angularjs
    console.log(_.isArray([])); // true
    console.log(_.isArray([111,222])); // true
    console.log(_.isArray({})); // false
```

## 检查是否为字符串----_.isString
```angularjs
    console.log(_.isString('2333q')); // true
    console.log(_.isString(3223)); // false
```

## 检查是否为数字类型----_.isNumber
> 所以NaN也会返回true

```angularjs
    console.log(_.isNumber(parseInt('2311'))); // true
    console.log(_.isNumber(parseInt('wwww'))); // true
    console.log(_.isNumber('www')); // false
    console.log(_.isNumber(3223)); // true
```

## 检查是否为对象----_.isPlainObjec、  _.isObject
> 前者判断的是单纯的对象
> 后者是广义上的对象，比如数组，正则，函数之类的，也会返回true
```angularjs
    // _.isPlainObjec
    var obj4 = {
        name: '明明',
        home: '北京',
        school: '清华大学',
    };
    var arr = [1,33];
    console.log(_.isPlainObject(obj4)); // true
    console.log(_.isPlainObject(arr)); // false
```

```angularjs
    //  _.isObject
    console.log(_.isObject([])); // true
    console.log(_.isObject({})); // true
    console.log(_.isObject(function () {

    })); // true
    console.log(_.isObject('')); // false
```


## 检查是否为NaN----_.isNaN
```angularjs
    console.log(_.isNaN(parseInt('2311'))); // false
    console.log(_.isNaN(parseInt('wwww'))); // true
    console.log(_.isNaN('www')); // false
    console.log(_.isNaN(3223)); // false
```

## 判断是否为空---_.isEmpty
> 可以用来判断空对象，空数组，空字符串,是undefined也会返回true
```angularjs
    console.log(_.isEmpty('')); // true
    console.log(_.isEmpty({})); // true
    console.log(_.isEmpty([])); // true
    
    const obj = {};
    console.log(obj.name); // undefined
    console.log(_.isEmpty(obj.name)); // true
```

## 循环对象、数组----_.forEach、 _.map
> 两个函数用法是一样的，只需将forEach换成map就行了
> 两个函数功能上有什么区别？？ _.forEach可以对每一个元素进行操作，
>_.map可以对元素进行操作且返回数组
> 回调函数的两个参数，第一个是*数组元素值/属性值*，第二个是*索引/属性*
```angularjs
    // _.forEach循环数组
    const arr2 = [33, 22, 555, 3443];
    _.forEach(arr2, (v, i) => {
        console.log(v, i);
    });
    // 33 0 
    // 22 1 
    // 555 2 
    // 3443 3
```
```angularjs
  // _.forEach循环对象
      var obj2 = {
          name: '明明',
          home: '北京',
          school: '清华大学',
      };
      _.forEach(obj2, (v, k) => {
          console.log(v, k);
      });
      // 明明 name 
      // 北京 home 
      // 清华大学 school
  
```
```angularjs
// _.map循环数组
    var user1 = [
        { 'user': '小红', 'age': 13, 'pet': '小猫', id: 11111 },
        { 'user': '花花', 'age': 22, 'pet': '狗狗', id: 22222 }
    ];
    console.log(_.map(user1, 'user')); // => ['小红', '小花']
    // -------------------------------------------------------
    console.log(_.map(user1, {'pet': '狗狗'})); // => [false, true]
    // -------------------------------------------------------
    console.log(_.map(user1, (n, i) => {
        return n.age * 2
    })); // [26, 44]
```
```angularjs
// _.map循环对象
    const obj2 = { 'user': '小红', 'age': 13, 'pet': '小猫', id: 11111 };
    console.log(_.map(obj2, (n) => {
        return n * 2
    })); // [NaN, 26, NaN, 22222]

```


## 数组截取----_.slice
> 返回起始位置到结束为止-1所在的元素
```angularjs
    const s = _.slice(['a', 'b', 'c', 'd', 'e', 'f'], 2, 4);
    console.log(s); // ["c", "d"]
```

## 取交集----_.intersection
```angularjs
console.log(_.intersection([2, 1, 3], [2, 3, 7], [3, 8])); // [3]
```


## 比较两个数组，返回第二个数组中没有的元素----_.difference
```angularjs
console.log(_.difference([2, 1, 7, 5], [2, 3])); // [1, 7, 5]
```


## 根据数组元素删除数组元素---- _.pull、 _.pullAllBy
> 从头到尾，只要是一样的都删除
区别：可能前者是用于删除简单数组元素， 后者是删除复杂数组元素
```angularjs
// _.pull
    var array = ['a', 'b', 'c', 'a', 'b', 'c'];
    _.pull(array, 'a', 'c');
    console.log(array); // ['b','b'];
```
```angularjs
// _.pullAllBy
var arr8 = [{ 'x': 1 }, { 'x': 2 }, { 'x': 3 }, { 'x': 1 }];
    _.pullAllBy(arr8, [{ 'x': 1 }, { 'x': 3 }], 'x');
    console.log('aa', arr8); // [{x: 2}]
```


## 根据index删除数组元素----
> 没找到，还真是直接用原生的splice方法吧


## 根据数组元素找到相应index----_.indexOf、 _.findIndex
> 不同：_.indexOf用于简单数组；_.findIndex: 用于复杂数组
```angularjs
    // _.indexOf用于简单数组
    const arr = [33, 22, 555, 3443];
    console.log('index', _.indexOf(arr, 555)); // index 2
```
```angularjs
    // _.findIndex: 用于复杂数组
    var users = [
        { 'user': 'barney',  'active': false },
        { 'user': 'fred',    'active': false },
        { 'user': 'pebbles', 'active': true }
    ];
    console.log(_.findIndex(users, { 'user': 'fred', 'active': false })); // 1
    console.log(_.findIndex(users, 'active')); // 2
    console.log(_.findIndex(users, function (g) {
        // g是数组元素
        return g.user == 'barney';
    })); // 0
```


## 数组反转----_.reverse
```angularjs
    const arr4 = ['G', 'X', 'D'];
    console.log(_.reverse(arr4)); // ["D", "X", "G"]
```


## 排序---- _.sortBy
```angularjs
    var users = [
        { 'user': 'fred',   'age': 34, 'id': 3 },
        { 'user': 'barney', 'age': 44, 'id': 2 },
        { 'user': 'fred',   'age': 41, 'id': 2 },
        { 'user': 'barney', 'age': 34, 'id': 1 }
    ];
// -------------------------------------------
    console.log(_.sortBy(users, 'age'));
//    [{user: "fred", age: 34, id: 3},
//     {user: "barney", age: 34, id: 1},
//     {user: "fred", age: 41, id: 2},
//     {user: "barney", age: 44, id: 2}]
// -------------------------------------------
//    先按ID排，ID相同的情况下按age排
    console.log(_.sortBy(users, ['id', 'age']));
//    [{user: "barney", age: 34, id: 1},
//    {user: "fred", age: 41, id: 2},
//    {user: "barney", age: 44, id: 2},
//    {user: "fred", age: 34, id: 3}]
// -------------------------------------------
    // 也可以将字符串换成回调函数，像这样，返回的结果跟'age'一样
    console.log(_.sortBy(users, [function (o) {
        return o.age;
    }]));
```



## 删除对象属性----_.omit
```angularjs
    var obj3 = {
        name: '明明',
        home: '北京',
        school: '清华大学',
    };
    console.log(_.omit(obj3, 'name')); // {home: "北京", school: "清华大学"}
```


## 取出对象中的某些键值对组成新的对象----_.pick
```angularjs
var object = { 'a': 1, 'b': '2', 'c': 3 };
    console.log(_.pick(object, ['a', 'c'])); // {a: 1, c: 3}
```


## 返回对象的所有key---- _.keys
```angularjs
    const obj6 = {a: 222, b: 111, c:666, d:809};
    console.log(_.keys(obj6)); // ["a", "b", "c", "d"]
```

## 有的话就返回值，没有的话（undefined）返回给定默认值----_.get
> 通常用于排错

```angularjs
var obj5 = { 'a': [{ 'b': { 'c': 3 } }] };
    console.log(_.get(obj5, 'a[0].b.c')); // 3 
    console.log(_.get(obj5, 'a.b.c', '目前没有值啊')); // 目前没有值啊
```


## 给对象添加属性---_.set
> 为什么会用到这个属性呢？ 答：在用Vue的时候，会遇到obj[age]，这样给对象添加了属性，但是在dom没有及时显现的情况，那是因为Vue不认为obj发生了变化，所以用'_.set'方法就解决了这个问题。
```angularjs
    var obj = {name: '小芳'};
    _.set(obj, 'age', 22);
    console.log(obj);// { age : 22, name : "小芳", }
```


## 让对象中的某一个属性值作为整个对象的键----_.keyBy
```angularjs
    var array = [
        { 'dir': 'left', 'code': 97 },
        { 'dir': 'right', 'code': 100 }
    ];

    console.log(_.keyBy(array, 'dir'));
    // {
    //   left: {dir: "left", code: 97},
    //   right:{dir: "right", code: 100}
    // }
```










## 把字符串分割为数组----_.split
```angularjs
    const str = '2017/08/24';
    const str1 = 'bawofenkai';
    const split = _.split(str, '/');
    const split1 = _.split(str1, '');
    console.log(split); //  ["2017", "08", "24"]
    console.log(split1); //  ["b", "a", "w", "o", "f", "e", "n", "k", "a", "i"]
```


## 删除字符串结尾的空格或其他指定字符----_.trimEnd

```angularjs
    console.log(_.trimEnd('  abc  ')); //   abc
    console.log(_.trimEnd('---abc---', '---')); // ---abc
```


## 转换为数字----_.parseInt、 _.toNumber
> 不同：_.parseInt转换为整型
_.toNumber 可以带小数点，但如果遇到非数字字符就会返回NaN
```angularjs
    console.log(_.parseInt('21125aaa')); // 21125
    console.log(_.parseInt(12.331)); // 12
```

```angularjs
    console.log(_.toNumber(3.2)); // 数字3.2
    console.log(_.toNumber('3.2')); // 数字3.2
```




## 将字符串转换为驼峰命名---_.camelCase
```angularjs
    const str2 = 'show-camel';
    const str3 = 'show/camel';
    const str4 = 'show camel';
    console.log(_.camelCase(str2)); // showCamel
    console.log(_.camelCase(str3)); // showCamel
    console.log(_.camelCase(str4)); // showCamel
```


## 字符串替换/截取----_.replace
```angularjs
    const str5 = 'happyNewYear';
    console.log(_.replace(str5, 'NewYear', 'Birthday')); // happyBirthday
    const str6 = 'config.json';
    console.log(_.replace(str6, '.json', '')); // config
```







## 对象数组中，根据属性值返回整个对象----_.find、 _.filter
> 区别：_.find只返回一条，并且返回的是一个对象；_.filter返回所有匹配上的项，返回的是一个数组

```angularjs
// _.find
 var user3 = [
        { 'user': 'barney',  'age': 36, 'active': true },
        { 'user': 'fred',    'age': 40, 'active': false },
        { 'user': 'pebbles', 'age': 1,  'active': true }
    ];
// ---------------------------------------------------------------------------------------
    console.log(_.find(user3, {'age': 1})); // {user: "pebbles", age: 1, active: true}
// ---------------------------------------------------------------------------------------
    console.log(_.find(user3, function (o) {
        return o.age < 40;
    })); // {user: "barney", age: 36, active: true}
    
```
```angularjs
// _.filter
    var arr7 = [
        { 'user': 'jray', 'age': 36, 'active': true },
        { 'user': 'fred',   'age': 40, 'active': false },
        { 'user': 'lili', 'age': 44, 'active': true },
    ];

    console.log(_.filter(arr7, function (o) {
        return o.active;
    }));
    
    // [
    //    {user: "jray", age: 36, active: true}, 
    //   {user: "lili", age: 44, active: true}
    // ]
```



## 克隆----_.clone、 _.cloneDeep
> 区别：_.clone克隆的元素的指针，而_.cloneDeep是重新开了一个区域，建立了新的指针。
>所以_.cloneDeep更严格一些。需要哪种，看例子自取把。
```angularjs
//    _.clone
        var arr5 = [{ 'a': 1 , 'c': {'d': 'like', 'e': 'eat'}}, { 'b': 2 }];
        var shallow = _.clone(arr5);
        console.log(shallow); // [{ 'a': 1 , 'c': {'d': 'like', 'e': 'eat'}}, { 'b': 2 }]
        // -------------------------------------------------------------------------------
        console.log(arr5[0] === shallow[0]); // true
```

```angularjs
//    _.cloneDeep
    var arr6 = [{ 'a': 1 }, { 'b': 2 }];
    var deep = _.cloneDeep(arr6);
    console.log(deep[0] === arr6[0]); // false
```

## 对象去重----_.defaults
> 从左往右，如果有重复的保留第一个
```angularjs
    console.log(_.defaults({'a': 1}, {'b': 2}, {'a': 3}, {'b': 222}, {'c': 2}));
    // {a: 1, b: 2, c: 2}
```

## 数组去重-----_.uniq
> 只能是这种单纯数组去重，复杂数组这个方法无能为力（比如对象数组这个方法就不行了）
```angularjs
    console.log(_.uniq(['a', 'b', 'a'])); // ["a", "b"]
```

## 获取对象，数字，字符串长度----_.size
```angularjs
    console.log(_.size({a: 222, b: 111, c:666, d:809})); // 4
    console.log(_.size([1, 2, 3])); // 3
    console.log(_.size('guanxiaotong')); // 12
```

## 函数被触发后，延时执行---- _.debounce
> 大概意思是这样，若要详细了解还得看文档
```angularjs
// 函数debounced，被触发后250毫秒再开始执行，执行的就是_.debounce的第一个参数（函数）
 var debounced = _.debounce((res)=> {console.log(res)}, 250, {});
```














