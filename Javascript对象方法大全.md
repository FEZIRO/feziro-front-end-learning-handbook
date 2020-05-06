# Javascript对象方法大全

整理自FEZIRO，参考自MDN web docs

## Object对象

 名称 | 类型 | 方法
-|-|-
Object | 静态方法 | **Object(任意值)**：构造函数<br/><br/>**Object.create(对象)**：该方法可以指定原型对象和属性，返回一个新的对象。<br/><br/>**Object.keys(对象)**：获取对象所有键<br/><br/>**Object.entries(对象)**：返回二维数组的对象键值对<br/><br/>**Object.values(对象)**：获取所有对象值<br/><br/>**Object.getOwnPropertyDescriptor(对象,对象内属性名)**：获取某个属性的描述对象<br/><br/>**Object.getOwnPropertyDescriptors(对象)**：获取多个属性的描述对象<br/><br/>**Object.getOwnPropertyNames(对象)**：可获取对象可枚举和不可枚举的属性<br/><br/>**Object.defineProperty(对象，对象属性名，操作)**：通过描述对象，定义单个属性。<br/><br/>**Object.defineProperties(对象，{属性名1：操作，属性名2：操作})**：通过描述对象，定义多个属性。<br/><br/>**Object.preventExtensions(对象)**：防止对象扩展<br/><br/>**Object.isExtensible(对象)**：判断对象是否可扩展<br/><br/>**Object.seal(对象)**：禁止对象配置<br/><br/>**Object.isSealed(对象)**：判断一个对象是否可配置<br/><br/>**Object.freeze(对象)**：冻结一个对象<br/><br/>**Object.isFrozen(对象)**：判断一个对象是否被冻结<br/><br/>**Object.getPrototypeOf(对象)**：获取对象的Prototype对象<br/><br/>**Object.assign(对象1，对象2)**：合并对象<br/><br/>**Object.is(值1，值2)**：判断两值是否相等<br/><br/>**Object.getPrototypeOf(对象)**：返回当前对象的原型<br/><br/>**Object.getOwnPropertySymbols(对象)**：获取所有symbol类型的属性 
Object | 实例方法 | **Object.prototype.valueOf()**：返回当前对象对应的值<br/><br/>**Object.prototype.toString()**：返回当前对象对应的字符串形式<br/><br/>**Object.prototype.toLocaleString()**：返回当前对象对应的本地字符串形式<br/><br/>**Object.prototype.hasOwnProperty()**：判断某个属性是否为当前对象自身的属性，还是继承自原型对象的属性<br/><br/>**Object.prototype.isPrototypeOf()**：判断当前对象是否为另一个对象的原型<br/><br/>**Object.prototype.propertyIsEnumerable()**：判断某个属性是否可枚举 




<br/><br/>

## Array对象
 名称 | 类型 | 方法
-|-|-
Array | 静态方法 | **Array()**：构造函数<br/><br/>**Array.isArray()**：判断是否是数组类型<br/><br/>**Array.from()**：将类数组转换成数组（ES6）<br/><br/>**Array.of(值1，值2...)**：将参数转化为数组 
Array | 实例方法 | **Array.prototype.valueOf()**：求值****<br/><br/>**Array.prototype.toString()**：数组转字符串，以逗号隔开<br/><br/>**Array.prototype.push(值)**：数组后添加值 **(原数组更改)**<br/><br/>**Array.prototype.pop()**：数组后删除值 **(原数组更改)**<br/><br/>**Array.prototype.shift()**：数组前删除值 **(原数组更改)**<br/><br/>**Array.prototype.unshift(值)**：数组前添加值 **(原数组更改)**<br/><br/>**Array.prototype.join(分隔符)**：以指定参数作为分隔符，将所有数组成员连接为一个字符串返回。如果不提供参数，默认用逗号分隔 **(原数组不改)**<br/><br/>**Array.prototype.contact(值1，值2...)**：多个数组的合并。它将新数组的成员，添加到原数组成员的后部，然后返回一个新数组 **(原数组不改)**<br/><br/>**Array.prototype.reverse()**：反转数组顺序 **(原数组更改)**<br/><br/>**Array.prototype.slice(开始位置，结束位置)**：<br/><br/>包含开始位，不含结束位，提取目标数组的一部分，返回一个新数组 **(原数组不改)**<br/><br/>**Array.prototype.splice(开始位，个数，添加值1，添加值2...)**：用于删除原数组的一部分成员，并可以在删除的位置添加新的数组成员，返回值是被删除的元素 **(原数组更改)**<br/><br/>**Array.prototype.sort((值1，值2)=>{})**：对数组成员进行排序，默认是按照字典顺序排序**(原数组更改)**<br/><br/>**Array.prototype.map((当前值，索引，原数组)=>{})**：数组的所有成员依次传入参数函数，然后把每一次的执行结果组成一个新数组返回**(原数组不改)**<br/><br/>**Array.prototype.some((当前值)=>{})**：返回一个布尔值，表示判断数组成员是否符合某种条件，只要一个成员的返回值是**true**，则整个**some**方法的返回值就是**true**，否则返回**false**<br/><br/>**Array.prototype.every((当前值)=>{})**：返回一个布尔值，表示判断数组成员是否符合某种条件，所有成员的返回值都是**true**，整个**every**方法才返回**true**，否则返回**false**<br/><br/>**Array.prototype.forEach((数值，索引，原数组)=>{})**：遍历数组<br/><br/>**Array.prototype.filter((当前值)=>{})**：返回过滤后新数组**(原数组不改)**<br/><br/>**Array.prototype.reduce((当前累计值，下一个值)=>{})**：从左到右累加<br/><br/>**Array.prototype.reduceRight((当前累计值，下一个值)=>{})**：从右到左累加<br/><br/>**Array.prototype.indexOf(值)**：返回给定元素在数组中第一次出现的位置，如果没有出现则返回**-1**<br/><br/>**Array.prototype.lastIndexOf(值)**：返回给定元素在数组中最后一次出现的位置，如果没有出现则返回-1<br/><br/>**Array.prototype.values()**：返回新的****Array Iterator**** 对象，该对象包含数组每个索引的值<br/><br/>**Array.prototype.keys()**：返回一个包含数组中每个索引键的Array Iterator对象。<br/><br/>**Array.prototype.flat(数组层次数)**：返回展平后的新数组(原数组不变)<br/><br/>**Array.prototype.fill(填充值，开始填充位置，结束填充位置)**：填充数组**(原数组改变)**<br/><br/>**Array.prototype.find((值，索引，原数组)=>{})**：返回数组中满足提供的测试函数的第一个元素的值。否则返回 **undefined**<br/><br/>**Array.prototype.findIndex((值，索引，原数组)=>{})**：返回数组中满足提供的测试函数的第一个元素**索引**。否则返回-1<br/><br/> 
<br/><br/>

## Function对象

| 名称     | 类型     | 方法                                                         |
| -------- | -------- | ------------------------------------------------------------ |
| Function | 静态方法 | **Function()**：构造函数                                       |
| Function | 实例方法 | **Function.prototype.toString()**：返回一个表示当前函数源代码的字符串<br/><br/>**Function.prototype.call(新上下文，参数1，参数2...)**：在新的上下文执行当前函数<br/><br/>**Function.prototype.apply(新上下文，[参数1，参数2...])**：在新的上下文执行当前函数，第二个参数为数组<br/><br/>**Function.prototype.bind(新上下文，参数1，参数2...)**：返回一个新的上下文函数<br/><br/> |
| Function | 静态属性 | **Function.name**：函数名字<br/><br/>**Function.length**：函数形参个数<br/><br/>**arguments**：类数组，在函数内部使用，可获取参数 |

<br/><br/>

## Boolen对象

| 名称   | 类型     | 方法                                         |
| ------ | -------- | -------------------------------------------- |
| Boolen | 静态方法 | **Boolen()**：构造函数，可转换类型或者生成实例 |
| Boolen | 实例方法 | **Boolen.prototype.valueOf()**：获取值         |

<br/><br/>

## Reflect对象

| 名称    | 类型     | 方法                                                         |
| ------- | -------- | ------------------------------------------------------------ |
| Reflect | 静态方法 | **Reflect.apply(要调用的函数, 新的上下文,[参数1,参数2])**：和object.prototype.apply功能类似<br/><br/>**Reflect.construct(target, argumentsList[, newTarget])**：用于创建对象<br/><br/>**Reflect.defineProperty(目标对象, 属性名, 操作)**：等同于 Object.defineProperty() 方法，唯一不同是返回 Boolean值确认是否成功定义。<br/><br/>**Reflect.deleteProperty(target, propertyKey)**：删除对象属性，类似delete操作符<br/><br/>**Reflect.get(对象, 属性[, 接收器])**：从 对象 target[propertyKey]中读取属性类似，但它是通过一个函数执行来操作的。<br/><br/>**Reflect.getOwnPropertyDescriptor(对象, 属性)**：和Object.getOwnPropertyDescriptor()方法相似。如果在对象中存在，则返回给定的属性的属性描述符。否则返回 undefined<br/><br/>**Reflect.getPrototypeOf(对象)**：和Object.getPrototypeOf()一样<br/><br/>**Reflect.has(对象, 属性)**：检查对象是否拥有当前属性，和in操作符作用相同<br/><br/><br/><br/>**Reflect.isExtensible(target)**：判断一个对象是否可扩展 （即是否能够添加新的属性），如果该方法的第一个参数不是一个对象（原始值），那么将造成一个 TypeError异常。对于 Object.isExtensible()，非对象的第一个参数会被强制转换为一个对象。<br/><br/>**Reflect.ownKeys(target)**：Reflect.ownKeys 方法返回一个由目标对象自身的属性键组成的数组。它的返回值等同于Object.getOwnPropertyNames(target).concat(Object.getOwnPropertySymbols(target))。如果目标不是 Object，抛出一个 TypeError<br/><br/>Reflect.setPrototypeOf(target, prototype)：和Object.setPrototypeOf一样<br/><br/>Reflect.set(目标对象, 属性名, 属性值[, receiver])：设置属性<br/><br/>Reflect.preventExtensions()：阻止新添加属性，和Object.preventExtensions()一样<br/><br/> |

<br/><br/>

## Number对象

| 名称   | 类型     | 方法                                                         |
| ------ | -------- | ------------------------------------------------------------ |
| Number | 静态方法 | **Number()**：构造函数，可转换类型或者生成实例<br/><br/>             |
| Number | 静态属性 | **Number.POSITIVE_INFINITY**：正的无限，指向**Infinity**<br/><br/>**Number.NEGATIVE_INFINITY**：负的无限，指向**-Infinity**<br/><br/> **Number.NaN**：表示非数值，指向**NaN**<br/><br/>**Number.MIN_VALUE**：表示最小的正数（即最接近0的正数，在64位浮点数体系中为**5e-324**），相应的，最接近0的负数为**-Number.MIN_VALUE** <br/><br/>**Number.MAX_SAFE_INTEGER**：表示能够精确表示的最大整数，即**9007199254740991**<br/><br/> **Number.MIN_SAFE_INTEGER**：表示能够精确表示的最小整数，即**-9007199254740991** |
| Number | 实例方法 | **Number.prototype.valueOf()**：获取值<br/><br/>**Number.prototype.toString()**：将一个数值转为字符串<br/><br/>**Number.prototype.toFixed(指定位数)**：先将一个数转为指定位数的小数，然后返回这个小数对应的字符串<br/><br/>**Number.prototype.toExponential()**：(小数点后有效数字的位数，范围为0到100)：将一个数转为科学计数法形式<br/><br/>**Number.prototype.toPrecision(有效数个数)**：将一个数转为指定位数的有效数字<br/><br/>**Number.prototype.toLocaleString('zh-Hans-CN', { style: 'currency', currency: 'CNY' }) **：表示当前数字在该地区的当地书写形式。<br/><br/> |

<br/><br/>

## String对象

| 名称   | 方法类型 | 方法                                                         |
| ------ | -------- | ------------------------------------------------------------ |
| String | 静态方法 | **String()**：构造函数，可转换类型或者生成实例<br/><br/>**String.fromCharCode(Unicode 码点)**：返回值是这些码点组成的字符串 |
| String | 实例方法 | **String.prototype.valueOf()**：获取值<br/><br/>**String.prototype.length**：返回字符串的长度<br/><br/>**String.prototype.charAt(字符位置)**：返回指定位置的字符<br/><br/>**String.prototype.charCodeAt(字符位置)**：返回字符串指定位置的 Unicode 码点（十进制表示）<br/><br/>**String.prototype.concat(字符1，字符2...)**：连接两个字符串，返回一个新字符串，不改变原字符串<br/><br/>**String.prototype.slice(开始位置，结束位置)**：从原字符串取出子字符串并返回，不改变原字符串<br/><br/>**String.prototype.substring(开始位置，结束位置)**：从原字符串取出子字符串并返回，不改变原字符串<br/><br/>**String.prototype.substr(开始位置，截取长度)**：用于从原字符串取出子字符串并返回，不改变原字符串<br/><br/>**String.prototype.indexOf()**：用于确定一个字符串在另一个字符串中第一次出现的位置，返回结果是匹配开始的位置。如果返回**-1**，就表示不匹配。<br/><br/>**String.prototype.lastIndexOf()**：用法跟**indexOf**方法一致，从尾部开始匹配<br/><br/>**String.prototype.trim()**：去除字符串两边空格<br/><br/>**String.prototype.toLowerCase()**：将一个字符串全部转为小写<br/><br/>**String.prototype.toUpperCase()**：将一个字符串全部转为大写<br/><br/>**String.prototype.match(正则表达式)**：用于确定原字符串是否匹配某个子字符串，返回一个数组，成员为匹配的第一个字符串。如果没有找到匹配，则返回**null**。<br/><br/>**String.prototype.search(正则表达式)**：**search**方法的用法基本等同于**match**，但是返回值为匹配的第一个位置。如果没有找到匹配，则返回**-1**。<br/><br/>**String.prototype.replace(正则表达式，字符串)**：用于替换匹配的子字符串，一般情况下只替换第一个匹配（除非使用带有**g**修饰符的正则表达式）。<br/><br/>**String.prototype.split(规则)**：给定规则分割字符串，返回一个由分割出来的子字符串组成的数组。<br/><br/>**String.prototype.localeCompare(比较对象)**：用于比较两个字符串。它返回一个整数，如果小于0，表示第一个字符串小于第二个字符串；如果等于0，表示两者相等；如果大于0，表示第一个字符串大于第二个字符串。JavaScript 采用的是 Unicode 码点比较，单该方法的最大特点，就是会考虑自然语言的顺序。举例来说，正常情况下，大写的英文字母小于小写字母。<br/><br/>**String.prototype.endsWith(搜索字符[, length])**：判断当前字符串是否是以另外一个给定的子字符串“结尾”的，根据判断结果返回 true 或 false<br/><br/>**String.prototype.startsWith(搜索字符[, length])**：判断当前字符串是否是以另外一个给定的子字符串“开头”的，根据判断结果返回 true 或 false<br/><br/>**String.prototype.includes(搜索字符串，位置)**：<br/><br/>**String.prototype.padEnd(目标长度 [, 填充字符串])**：<br/><br/>**String.prototype.padStart(目标长度 [, 填充字符串])**：<br/><br/>**String.prototype.**repeat(字符串重复次数)：次数不能是负数，小数点会转换为整数<br/><br/>**String.prototype.trimStart()**：去除左边空白字符<br/><br/>**String.prototype.trimEnd()**：去除右边空白字符 |

<br/><br/>

## Math对象

| 名称 | 类型     | 方法                                                         |
| ---- | -------- | ------------------------------------------------------------ |
| Math | 静态属性 | **Math.E**：常数**e**。<br/><br/>**Math.LN**：2 的自然对数。<br/><br/>**Math.LN10**：10 的自然对数。<br/><br/>**Math.LOG2E**：以 2 为底的**e**的对数。 <br/><br/>**Math.LOG10E**：以 10 为底的**e**的对数<br/><br/>**Math.PI**：常数**π**。<br/><br/>**Math.SQRT1_2**：0.5 的平方根。<br/><br/>**Math.SQRT2**：2 的平方根。 |
| Math | 静态方法 | **Math.abs(数值)**：绝对值<br/><br/>**Math.ceil(数值)**：向上取整，返回小于参数值的最大整数（地板值）<br/><br/>**Math.floor(数值)**：向下取整，返回大于参数值的最小整数（天花板值）。<br/><br/>**Math.max(数值，数值...)**：最大值<br/><br/>**Math.min(数值，数值...)**：最小值 <br/><br/>**Math.pow(数值，数值)**：指数运算，以第一个参数为底数、第二个参数为幂的指数值，幂次方<br/><br/>**Math.sqrt(数值)**：平方根，返回参数值的平方根。如果参数是一个负值，则返回**NaN**<br/><br/>**Math.log(数值)**：自然对数<br/><br/>**Math.exp(数值)**：**e**的指数，返回常数**e**的参数次方<br/><br/>**Math.round(数值)**：四舍五入<br/><br/>**Math.random()**：随机数<br/><br/>**Math.sin(弧度值)**：返回参数的余弦<br/><br/>**Math.tan(弧度值)**：返回参数的正切<br/><br/>**Math.asin(弧度值)**：返回参数的反正弦<br/><br/>**Math.asin(弧度值)**：返回参数的反余弦<br/><br/>**Math.atan(弧度值)**：返回参数的反正切<br/><br/> |

<br/><br/>

## Date对象

| 名称 | 方法类型 | 方法                                                         |
| ---- | -------- | ------------------------------------------------------------ |
| Date | 静态方法 | **Date()**：构造函数<br/><br/>**Date.now()**：返回当前时间距离时间零点（1970年1月1日 00:00:00 UTC）的毫秒数，相当于 Unix 时间戳乘以1000<br/><br/>**Date.parse()**：解析日期字符串，返回该时间距离时间零点（1970年1月1日 00:00:00）的毫秒数<br/><br/>**Date.UTC()**：接受年、月、日等变量作为参数，返回该时间距离时间零点（1970年1月1日 00:00:00 UTC）的毫秒数。 |
| Date | 实例方法 | **Date.prototype.valueOf()**：返回实例对象距离时间零点（1970年1月1日00:00:00 UTC）对应的毫秒数，该方法等同于**getTime**方法<br/><br/>**Date.prototype.toString()**：返回一个完整的日期字符串<br/><br/>**Date.prototype.toUTCString()**：返回对应的 UTC 时间，也就是比北京时间晚8个小时<br/><br/>**Date.prototype.toISOString()**：返回对应时间的 ISO8601 写法<br/><br/>**Date.prototype.toJSON()**：返回一个符合 JSON 格式的 ISO 日期字符串，与**toISOString**方法的返回结果完全相同<br/><br/>**Date.prototype.toDateString()**：返回日期字符串（不含小时、分和秒）<br/><br/>**Date.prototype.toTimeString()**：返回时间字符串（不含年月日）<br/><br/>**Date.prototype.toLocaleString()**：将 Date 实例转为表示本地时间的字符串，完整的本地时间<br/><br/>**Date.prototype.toLocaleDateString()**：将 Date 实例转为表示本地时间的字符串，本地日期（不含小时、分和秒）<br/><br/>**Date.prototype.toLocaleTimeString()**：将 Date 实例转为表示本地时间的字符串，本地时间（不含年月日）<br/><br/>**Date.prototype.getTime()**：返回实例距离1970年1月1日00:00:00的毫秒数，等同于**valueOf**方法<br/><br/>**Date.prototype.getDate()**：返回实例对象对应每个月的几号（从1开始）<br/><br/>**Date.prototype.getDay()**：返回星期几，星期日为0，星期一为1，以此类推<br/><br/>**Date.prototype.getFullYear()**：返回四位的年份<br/><br/>**Date.prototype.getMonth()**：返回月份（0表示1月，11表示12月）<br/><br/>**Date.prototype.getHours()**：返回小时（0-23）<br/><br/>**Date.prototype.getMilliseconds()**：返回毫秒（0-999）<br/><br/>**Date.prototype.getMinutes()**：返回分钟（0-59）<br/><br/>**Date.prototype.getSeconds()**：返回秒（0-59）<br/><br/>**Date.prototype.getTimezoneOffset()**：返回当前时间与 UTC 的时区差异，以分钟表示，返回结果考虑到了夏令时因素。<br/><br/>**Date.prototype.setDate(date)**：设置实例对象对应的每个月的几号（1-31），返回改变后毫秒时间戳<br/><br/>**Date.prototype.setFullYear(year [, month, date])**：设置四位年份<br/><br/>**Date.prototype.setHours(hour [, min, sec, ms])**：设置小时（0-23）<br/><br/>**Date.prototype.setMilliseconds()**：设置毫秒（0-999）<br/><br/>**Date.prototype.setMinutes(min [, sec, ms])**：设置分钟（0-59）<br/><br/>**Date.prototype.setMonth(month [, date])**：设置月份（0-11）<br/><br/>**Date.prototype.setSeconds(sec [, ms])**：设置秒（0-59）<br/><br/>**Date.prototype.setTime(milliseconds)**：设置毫秒时间戳<br/><br/>**Date.prototype.getUTCDate()**<br/><br/>**Date.prototype.getUTCFullYear()**<br/><br/>**Date.prototype.getUTCMonth()**<br/><br/>**Date.prototype.getUTCDate()**<br/><br/>**Date.prototype.getUTCHours()**<br/><br/>**Date.prototype.getUTCMinutes()**<br/><br/>**Date.prototype.getUTCSeconds()**<br/><br/>**Date.prototype.getUTCMilliseconds()**<br/><br/>**Date.prototype.setUTCDate()**<br/><br/>**Date.prototype.setUTCFullYear()**<br/><br/>**Date.prototype.setUTCHours()**<br/><br/>**Date.prototype.setUTCMilliseconds()**<br/><br/>**Date.prototype.setUTCMinutes()**<br/><br/>**Date.prototype.setUTCMonth()**<br/><br/>**Date.prototype.setUTCSeconds()** |

<br/><br/>

## RegExp对象

| 名称   | 方法类型 | 方法                                                         |
| ------ | -------- | ------------------------------------------------------------ |
| RegExp | 静态方法 | **RegExp(规则)**：构造函数                                     |
| RegExp | 实例属性 | **RegExp.prototype.ignoreCase**：返回一个布尔值，表示是否设置了**i**修饰符<br/><br/> **RegExp.prototype.global**：返回一个布尔值，表示是否设置了**g**修饰符<br/><br/> **RegExp.prototype.multiline**：返回一个布尔值，表示是否设置了**m**修饰符。<br/><br/>**RegExp.prototype.flags**：返回一个字符串，包含了已经设置的所有修饰符，按字母排序<br/><br/>**RegExp.prototype.lastIndex**：返回一个整数，表示下一次开始搜索的位置。该属性可读写，但是只在进行连续搜索时有意义<br/><br/>**RegExp.prototype.source**：返回正则表达式的字符串形式（不包括反斜杠），该属性只读 |
| RegExp | 实例方法 | **RegExp.prototype.test(字符串)**：返回一个布尔值，表示当前模式是否能匹配参数字符串<br/><br/>**RegExp.prototype.exec(字符串)**：用来返回匹配结果。如果发现匹配，就返回一个数组，成员是匹配成功的子字符串，否则返回**null**。 |

<br/><br/>

## JSON对象

| 名称 | 方法类型     | 方法                                                         |
| ---- | ------------ | :----------------------------------------------------------- |
| JSON | 静态方法     | **JSON.stringify(值)**：将一个值转为 JSON 字符串<br/><br/>**JSON.parse(JSON字符)**：将 JSON 字符串转换成对应的值 |
| JSON | 参数对象方法 | **toJSon()**：如果参数对象有自定义的**toJSON**方法，那么**JSON.stringify**会使用这个方法的返回值作为参数，而忽略原对象的其他属性。 |

<br/><br/>

## Map对象

任何值（对象或者原始值）都可以作为一个键或一个值

| 名称 | 方法类型 | 方法                                                         |
| ---- | -------- | :----------------------------------------------------------- |
| Map  | 实例属性 | **Map.prototype.size**：返回一个Map对象的成员数量              |
| Map  | 实例方法 | **Map.prototype.get(属性名)**： 返回某个 **Map** 对象中的一个指定元素<br/><br/>**Map.prototype.set(属性名，属性值)**： 为 **Map** 对象添加或更新一个指定了键（**key**）和值（**value**）的（新）键值对 <br/><br/>**Map.prototype.has(属性名)**：返回一个bool值，用来表明map 中是否存在指定元素.<br/><br/>**Map.prototype.clear()**：移除Map对象中的所有元素<br/><br/>**Map.prototype.delete(属性名)**：用于移除 **Map** 对象中指定的元素<br/><br/>**Map.prototype.entries()**：返回一个新的包含 **[key, value]** 对的Iterator对象，返回的迭代器的迭代顺序与 **Map** 对象的插入顺序相同<br/><br/>**Map.prototype.forEach((当前值，属性名，当前对象)=>{})**：以插入顺序对 Map 对象中的每一个键值对执行一次参数中提供的回调函数。<br/><br/>**Map.prototype.keys()**：返回一个新的 ****Iterator**** 对象。它包含按照顺序插入 **Map** 对象中每个元素的key值<br/><br/>**Map.prototype.values()**：返回一个新的Iterator对象。它包含按顺序插入Map对象中每个元素的value值<br/><br/> |
| Map  | 静态方法 | **Map([属性名，属性值], []...)**：构造函数                     |

<br/><br/>

## WeakMap对象

键是弱引用的。其键必须是对象，而值可以是任意的。

| 名称    | 方法类型 | 方法                                                         |
| ------- | -------- | :----------------------------------------------------------- |
| WeakMap | 静态方法 | **WeakMap([属性名，属性值], []...)**：构造函数                 |
| WeakMap | 实例方法 | **WeakMap.prototype.get(属性名)**： 返回某个WeakMap 对象中的一个指定元素<br/><br/>**WeakMap.prototype.set(属性名，属性值)**： 为WeakMap 对象添加或更新一个指定了键（**key**）和值（**value**）的（新）键值对 <br/><br/>**WeakMap.prototype.has(属性名)**：返回一个bool值，用来表明WeakMap 中是否存在指定元素.<br/><br/>**WeakMap.prototype.delete(属性名)**：用于移除WeakMap 对象中指定的元素<br/><br/> |

<br/><br/>

## Set对象

Set允许你存储任何类型的唯一值，无论是[原始值](https://developer.mozilla.org/zh-CN/docs/Glossary/Primitive)或者是对象引用

| 名称 | 方法类型 | 方法                                                         |
| ---- | -------- | :----------------------------------------------------------- |
| Set  | 静态属性 | **Set([值1，值2...])**：构造函数                               |
| Set  | 实例属性 | **Set.protoType.size**：返回set对象元素个数                    |
| Set  | 实例方法 | **Set.prototype.add(值)**： 向一个 Set 对象的末尾添加一个指定的值 <br/><br/>**Set.prototype.has(值)**：返回一个布尔值来指示对应的值value是否存在Set对象中<br/><br/>**Set.prototype.clear()**：清空一个 Set对象中的所有元素<br/><br/>**Set.prototype.delete(值)**：从一个 Set对象中删除指定的元素<br/><br/>**Set.prototype.entries()**：返回一个新的迭代器对象 ，这个对象的元素是类似 [value, value] 形式的数组<br/><br/>**Set.prototype.forEach((当前值，属性名，当前对象)=>{})**：根据集合中元素的插入顺序，依次执行提供的回调函数<br/><br/>**Set.prototype.values()**：返回一个 Iterator对象，该对象按照原Set 对象元素的插入顺序返回其所有元素。<br/><br/> |

<br/><br/>

## WeakSet对象

****WeakSet**** 对象允许你将*弱保持对象*存储在一个集合中

| 名称    | 方法类型 | 方法                                                         |
| ------- | -------- | :----------------------------------------------------------- |
| WeakSet | 静态方法 | **<u>WeakSet([值1，...])</u>**：构造函数                     |
| WeakSet | 实例方法 | **WeakSet.prototype.add(值)**：在WeakSet对象的最后一个元素后添加新的对象<br/><br/>**WeakSet.prototype.delete(值)**：从 WeakSet 对象中移除指定的元素<br/><br/>**WeakSet.prototype.has(值)**：根据 WeakSet 是否存在相应对象返回布尔值 |

<br/><br/>



# XMLHttpRequest对象

| 名称           | 方法类型     | 方法                                                         |
| -------------- | ------------ | :----------------------------------------------------------- |
| XMLHttpRequest | 实例属性     | <u>**readyState**</u>：xhr实例当前所处的状态<br/>（0表示代理被创建但未调用 open() ；1表示open() 方法已被调用；2表示send()已被调用并且头部和状态已经可获得；3表示下载中，responseText 属性已经包含部分数据；4表示下载操作已完成）<br/><br/><u>**onreadystatechange**</u>：监听readystate属性变化，直接赋值回调函数<br/><br/><u>**response**</u>：响应对象，其类型取决于 responseType 的值<br/><br/>**<u>responseText</u>**：返回值是当前从后端收到的内容<br/><br/><u>**responseType**</u>：返回响应数据的类型。它允许我们手动的设置返回数据的类型。如果我们将它设置为一个空字符串，它将使用默认的"text"类型<br/><br/>**<u>responseURL</u>**：返回响应的序列化URL，如果URL为空则返回空字符串。如果URL有锚点，则位于URL # 后面的内容会被删除。如果URL有重定向， **responseURL** 的值会是经过多次重定向后的最终 URL<br/><br/><u>**responseXML**</u>：返回一个包含请求检索的HTML或XML的Document<br/><br/><u>**status**</u>：响应中的状态码<br/><br/><u>**statusText**</u>：返回请求中由服务器返回的一个DOMString类型的文本信息，这则信息中也包含了响应的数字状态码<br/><br/><u>**timeout**</u>：请求超时时间，可以自行设置<br/><br/><u>**upload**</u>：**返回一个** XMLHttpRequestUpload对象，用来表示上传的进度。这个对象是不透明的，但是作为一个XMLHttpRequestEventTarget，可以通过对其绑定事件来追踪它的进度<br/><br/><u>**withCredentials**</u>：是一个Boolean类型，跨域请求是否提供凭据信息，即当前请求为跨域类型时是否在请求中协带cookie |
| XMLHttpRequest | 实例方法     | **<u>abort ()</u>**：如果该请求已被发出，**XMLHttpRequest.abort()** 方法将终止该请求。当一个请求被终止，它的 readyState 属性将被置为0（ **UNSENT** )<br/><br/>**<u>open (method, url, async, user, password)</u>** ：初始化一个请求<br/><br/>**<u>send (data)</u>**：用于发送 HTTP 请求<br/><br/>**<u>setRequestHeader(name, value)</u>**：设置HTTP请求头部<br/><br/>**<u>getResponseHeader(name)</u>**：返回包含指定头文本的字符串<br/><br/>**<u>getAllResponseHeaders()</u>**：返回所有的响应头<br/><br/>**<u>overrideMimeType(mimeType)</u>**：指定一个MIME类型用于替代服务器指定的类型，使服务端响应信息中传输的数据按照该指定MIME类型处理 |
| XMLHttpRequest | 实例事件监听 | <u>**onreadystatechange**</u>：监听readystate属性变化，直接赋值回调函数<br/><br/>**<u>abort：</u>**监听请求被打断<br/><br/>**<u>error</u>**：监听请求出错<br/><br/>**<u>load</u>**：监听请请求完成<br/><br/>**<u>loadstart</u>**：监听请求加载开始<br/><br/>**<u>loadend</u>**：监听请求加载结束<br/><br/>**<u>progress</u>**：监听请求进度<br/><br/>**<u>timeout</u>**：监听请求超时 |

<br/><br/>