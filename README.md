# lodash-use
lodash的使用

废话不多，直接开始吧--------------------

## 循环对象、数组----_.forEach
> 回调函数的两个参数，第一个是*数组元素值/属性值*，第二个是*索引/属性*
```angularjs
    // 循环数组
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
  // 循环对象
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

## 根据数组元素删除数组元素----

## 根据index删除数组元素----

## 根据数组元素找到相应index----_.indexOf、 _.findIndex
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

## 删除对象属性----_.omit
```angularjs
    var obj3 = {
        name: '明明',
        home: '北京',
        school: '清华大学',
    };
    console.log(_.omit(obj3, 'name')); // {home: "北京", school: "清华大学"}
```

## 在对象数组中，根据属性值返回相应对象/对象的索引----

## 把字符串分割为数组----_.split
```angularjs
    const str = '2017/08/24';
    const str1 = 'bawofenkai';
    const split = _.split(str, '/');
    const split1 = _.split(str1, '');
    console.log(split); //  ["2017", "08", "24"]
    console.log(split1); //  ["b", "a", "w", "o", "f", "e", "n", "k", "a", "i"]
```
## 检查是否为对象----_.isPlainObject
```angularjs
    var obj4 = {
        name: '明明',
        home: '北京',
        school: '清华大学',
    };
    var arr = [1,33];
    console.log(_.isPlainObject(obj4)); // true
    console.log(_.isPlainObject(arr)); // false
```

## 检查是否为数组----

## 检查是否为字符串----

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

## 给对象添加属性---_.set
> 为什么会用到这个属性呢？ 答：在用Vue的时候，会遇到obj[age]，这样给对象添加了属性，但是在dom没有及时显现的情况，那是因为Vue不认为obj发生了变化，所以用'_.set'方法就解决了这个问题。
```angularjs
    var obj = {name: '小芳'};
    _.set(obj, 'age', 22);
    console.log(obj);// { age : 22, name : "小芳", }
```
## 数组反转----

## 将字符串转换为驼峰命名---_.camelCase
```angularjs
    const str2 = 'show-camel';
    const str3 = 'show/camel';
    const str4 = 'show camel';
    console.log(_.camelCase(str2)); // showCamel
    console.log(_.camelCase(str3)); // showCamel
    console.log(_.camelCase(str4)); // showCamel
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
