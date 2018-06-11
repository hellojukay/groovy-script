# 代码注释
和其他的编程语言一样Groovy脚本的注释有两中
* // 这是行注释
* /* 这是块注释 */

推荐使用块注释的方式

# 定义变量
Groovy是一种动态的编程语言，所以变量可以在脚本里面使用def关键字来定义
```shell
def x = "hello world"
println(x)
x = 100
println(x)
```
动态语言，并不是说Groovy没有类型，你也可以在定义变量的时候指定变量类型
```shell
Integer x =10
println(x)
// 类型不匹配，赋值会报错
x = "hello world"
println(x)
```
# 字符串模板
可以在字符串中直接使用模板替换变量
```
def name="hello jukay"
def age = 18
def hello = "Hello ${name}" 
def a = "i am ${age} years old"
println(name)
println(a)
```

# if/else条件表达式
```shell
def age = 18
if (age < 18){
    println("你是未成年人")
}else{
    println("你是成年人")
}
```

# Switch条件达表示
groovy的case语句如果不break，会一直往下面执行。
```shell
def c= 'C'
switch(c) {
    case 'A':
    println("you got A")
    break
    case 'B':
    println('you got B')
    case 'C':
    println("you got C")
    default:
    println('不知道你的成绩')
}
```

# 返回一个Boolean类型的值
```shell
def check(x){
    if (x > 1000){
        return true
    }
    return false
}
def check(x){
    return x > 1000
}
println(check(1000))
```

# null与空字符串
Groovy中null表示不指向任何对于，空字符串表示一个长度为0，不包含任何字符的字符串。一下脚本输出：不相等。
```shell
def a = null
if (a == ""){
    println("相等")
}else{
    println("不相等")
}
```

# 安全的操作对象
如果你要使用 . 来访问对于的属性或者放置，如果对象没有初始化，或者指向了null,那么就会产生空指针一样，我们可以使用?来避免这个问题，如下：
```shell

class Person{
    def getAge(){
        return 18
    }
}

def p = new Person();
println(p.getAge())
p = null
println(p?.getAge())
```
使用？的好处是，如果对象是空，并不会抛出空指针异常，而是吧表达式的值认为是null.

# 打印日志
使用println函数来打印日志，一般会结合使用字符串模板，如下：
```shell
def age=18
println("user age=${age}")
```

# 使用列表
初始化一个列表
```shell
def list = [1,2,3,4,'5']
// 定义一个空的列表
def empty_list = []
```
遍历一个列表
```shell
def list = [1,2,3,4]
for(i in list){
    println(i)
}
```
使用索引访问列表中的数据，并且修改他
```shell
println(list[0])
list[0] = "hello world"
for(i in list){
    println(i)
}
```
删除和添加列表中的数据
```shell
list.add("hellojukay")
for(i in list){
    println(i)
}
list.remove("hellojukay")
for(i in list){
    println(i)
}
```

# 使用Map结构
初始化一个map
```shell
def map = ['name':"Hellojukay", 'age':18]
// 定义一个空的map
def map2 = [:]
```
查找元素
```shell
println(map.get('name'))
println(map.get('sex')) // print null
println(map['fuck']) // print nulll
map['sex'] = true
println(map.get('sex')) // print true
map.remove('name') // 删除元素
```
遍历Map
```shell
def map = ['name':"Hellojukay", 'age':18]
for(e in map){
    printf("key=%s, value=%s\n",e.key,e.value)
}
```

# 使用range迭代
使用 .. 可以是快速的产一个一个序列,从i到j,如果i==j，那么会产生一个长度为1的列表
```shell
def range=1..100
for(i in range){
    println(i)
}
```
range是可以转化成数组或者list的
```shell
def range=1..1
for(i in range){
    println(i)
}
def arr= range.toArray()
println(arr)
def list = range.toList()
println(list)
list.add("hello")
println(list)
```
所以一般可以使用下面的方法来快速的生成数组或者list.
```shell
println((1..3).toArray())
println((1..3).toList())
```