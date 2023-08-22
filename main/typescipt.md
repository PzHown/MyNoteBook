[toc]
# TypeScipt

日期：2023.08.22

---

## 类型
1. 任何类型 `any`
2. 基元类型  `boolean`，`number`、`string`、`void`、`null` 和 `undefined` 类型以及用户定义的枚举或 `enum` 类型。
3. 对象类型和类型参数

### 布尔类型
最基本的数据类型是 `true` 或 `false` 值，称为布尔值。

### 数字类型和大整数类型
TypeScript 中的所有数字都是浮点数或大整数。 这些浮点数的类型为 `number`，而大整数的类型为 `bigint`。 除了十六进制和十进制字面量，TypeScript 还支持 ECMAScript 2015 中引入的二进制和八进制字面量。

### 字符串类型
关键字 `string` 表示以 Unicode UTF-16 代码单元的形式存储的字符序列。
- 在 TypeScript 中，还可以使用模板字符串，该模板字符串可以跨越多行并具有嵌入式表达式。 这些字符串由反撇号/反引号 (\`) 字符括起，并且嵌入式表达式的形式为 `${ expr }`。例如：
```TypeScript
let a: string = "Hello"
let b: string = `${a} World!`
console.log(b)
```

### void、null 和 undefined 类型
JavaScript 和 TypeScript 具有两个用于表示缺少的值或未初始化的值的基元值：`null` 和 `undefined` 。

### 枚举类型
对 JavaScript 的标准数据类型集的一个有用补充是枚举类型（即 `enum`）。语法如下：
```TypeScript
enum States {
    Apple,//默认0开头，可声明Apple=1，
    Orange，
    Banana，
    Watermelon
}
// 使用
var fruit: States = States.Watermelon;
```

### 任何类型
`any` 类型是可以无限制地表示任何 JavaScript 值的一种类型。
> any 的所有便利都以失去类型安全性为代价。 类型安全是使用 TypeScript 的主要动机之一。 如果不需要，应避免使用 any。

### unknown 类型
`unknown` 类型与 `any` 类型的相似之处在于，可以将任何值赋予类型 `unknown`。 但无法访问 `unknown` 类型的任何属性，也不能调用或构造它们。
> any 和 unknown 之间的核心区别在于你无法与 unknown 类型的变量进行交互；这样做会产生“编译器”错误。 any 将绕过所有编译时检查，并且在运行时评估对象；如果该方法或属性存在，它将表现出预期的效果。

### 类型断言
需要将变量视为其他数据类型，则可以使用类型断言。
1. 首选使用 `as` 语法：`(randomValue as string).toUpperCase();`
2. 使用尖括号：`(<string>randomValue).toUpperCase();`

### 联合类型
联合类型使用竖线 (`|`) 分隔每种类型。

### 交叉类型
交叉类型使用与号 (`&`) 分隔每种类型。它就是将多个类型组合。

### 集合类型

#### 数组

1. 使用元素类型后跟方括号 (`[]`) 来表示该元素类型的数组：
```TypeScript
let list:number[] = [1,2,3]
```
2. 第二种方式，通过语法 `Array<type>` 使用泛型 Array 类型：
```TypeScript
let list:Array<number> = [1,2,3]
```

#### 元组
拥有相同值类型的数组很有用，但有时一个数组可能包含混合类型的值。
```TypeScript
let list:[number,string] = [1,"2"]
```

## 接口

范例：
```TypeScript
interface Employee {
    firstName: string;
    lastName: string;
    fullName(): string;
}
```
> **接口与类型别名有何不同？**
> 类型别名是数据类型（例如联合、基元、交集、元组或其他任何类型）的定义。 另一方面，接口是描述数据形状（例如对象）的一种方法。 类型别名可以像接口一样使用；但有一些细微的差异。 主要区别在于，不能重新打开类型别名以添加新属性，而接口始终是可扩展的。 此外，只能使用类型别名描述并集或元组。

### 声明和实例化接口

属性类型|说明|示例
---|---|---
必须|除非另行指定，否则所有属性都是必需的。|`firstName: string;`
可选|在属性名称的末尾添加问号 (`?`)。 对于不是必需的属性，请使用此属性。 这可以防止类型系统在省略该属性时引发错误。|`firstName?: string;`
只读|在属性名称的前面添加 `readonly` 关键字。 对于只应在首次创建对象时修改的属性，请使用此属性。|`readonly firstName: string;`

#### 声明具有成员的接口
```TypeScript
interface IceCream {
   flavor: string;
   scoops: number;
}

let myIceCream: IceCream = {
   flavor: 'vanilla',
   scoops: 2
}

console.log(myIceCream.flavor);
```

### 接口扩展
示例：
```TypeScript
interface Sundae extends IceCream {
    sauce: 'chocolate' | 'caramel' | 'strawberry';
    nuts?: boolean;
    whippedCream?: boolean;
    instructions?: string;
}
```

### 创建可索引类型
```TypeScript
interface IceCreamArray {
    [index: number]: string;
}

let myIceCream: IceCreamArray;
myIceCream = ['chocolate', 'vanilla', 'strawberry'];
let myStr: string = myIceCream[0];
console.log(myStr);
```

## 类

模板：
```TypeScript
class Car {
    // Properties
    _make: string;
    _color: string;
    _doors: number;
    // Constructor
    constructor(make: string, color: string, doors = 4) {
        this._make = make;
        this._color = color;
        this._doors = doors;
    }
    // Accessors
    get make() {
        return this._make;
    }
    set make(make) {
        this._make = make;
    }
    ...
    // Methods
    accelerate(speed: number): string {
        return `${this.worker()} is accelerating to ${speed} MPH.`
    }
    ...

}
```
### 实例化

```TypeScript
let myCar1 = new Car('Cool Car Company', 'blue', 2);  // Instantiates the Car object with all parameters
```
### 扩展类
使用 `extends` 关键字从基类派生。