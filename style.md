### 格式

#### 命名格式

仓库：中划线

文件：
变量、函数、类等：驼峰

命名原则
语义化(优先使用英文)
紧致适用单字母命名(如：result→r, response → r, request → r)
变量优先使用名词，布尔值以is或has等适合表达与非关系的词为前缀，函数优先使用动词+名词

代码缩进使用2空格

行末无空格

每行最多140行个字符

优先使用单引号(除非写JSON)

使用===

花括号不在新的一行开始
```javascript
// Right
if (true) {
  console.log('winning');
}

// Wrong
if (true)
{
  console.log('losing');
}
````

变量声明

每声明一个变量使用一个声明表达式(var、let、const)。（便于调整顺序）
如果变量和函数块有依赖，则把变量声明和函数块放一起。

```javascript
// Right
var keys   = ['foo', 'bar'];
var values = [23, 42];

var object = {};
while (keys.length) {
  var key = keys.pop();
  object[key] = values.pop();
}

// Wrong
var keys = ['foo', 'bar'],
    values = [23, 42],
    object = {},
    key;

while (keys.length) {
  key = keys.pop();
  object[key] = values.pop();
}
```

### 函数

写小函数
> 保持函数尽量简短。一个好的函数就像幻灯片一样，在大房间的最后一排也能舒适的阅读。
所以不要指望他们拥有一个完美的视野，所以限制每个函数在15行之内。

> Keep your functions short. A good function fits on a slide that the people in the last row of a big room can comfortably read.
So don't count on them having perfect vision and limit yourself to ~15 lines of code per function.
尽早Return


避免if表达式的嵌套，总是尽早return。

```javascript
// Right
function isPercentage(val) {
  if (val < 0) {
    return false;
  }

  if (val > 100) {
    return false;
  }

  return true;
}


// Right
function isPercentage(val) {
  var isInRange = (val >= 0 && val <= 100);
  return isInRange;
}

// Wrong
function isPercentage(val) {
  if (val >= 0) {
    if (val < 100) {
      return true;
    } else {
      return false;
    }
  } else {
    return false;
  }
}
```

```javascript
避免嵌套函数
// Right:
setTimeout(function() {
  client.connect(afterConnect);
}, 1000);

function afterConnect() {
  console.log('winning');
}
// Wrong:
setTimeout(function() {
  client.connect(function() {
    console.log('losing');
  });
}, 1000);
```