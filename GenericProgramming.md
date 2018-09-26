## 泛型编程的根源
The roots of generic programming
> generic programming is a programming style in which algorithms are written at the most abstract possible level independent of the form of the data on which these algorithms will be carried out

泛型编程是一种编程风格，其中算法以尽可能抽象的方式编写，而不依赖于将在其上执行这些算法的数据形式。

这个概念由在1989年首次被David Musser和Alexander Stepanov提出[1.参考]。

## Java中的泛型编程
在Java中有泛型类和泛型方法之分，这些都是表现形式的改变，实质还是将算法尽可能地抽象化，不依赖具体的类型。
> generics add a way to specify concrete types to general purposes classes and methods that operated on Object before

通用的类和方法，具有代表性的就是集合类。在Java1.5之前，Java中的泛型都是通过单根继承的方式实现的。比如：
```
public class ArrayList // before  Java SE 5.0
{
    public Object get(int i)
    public void add(Object o)
    public boolean contains(Object o);
    private Object[] elementData;
}
```
虽然算法足够通用了，但是这样会带来两个问题。一个是类型不安全，还有一个是每次使用时都得强制转化。
例如：
```
List list = new ArrayList();
list.add(1);

assertThat(list.get(0), instanceOf(Integer.TYPE));
assertThat((Integer)list.get(0), is(1)); //存在强制转换
```

因为这个类里只有Object的声明，所以任意类型的对象都可以加入到这个集合当中，在使用过程中就会存在强制到具体的类型失败的问题，这将丧失编译器检查的好处。
```
List list = new ArrayList();
list.add(1);
list.add("any type");

assertThat(list.get(1), instanceOf(String.class));
assertThat((Integer) list.get(1), is(1));//-> java.lang.ClassCastException: java.lang.String cannot be cast to java.lang.Integer
```

2005 Java SE 5引入了泛型，不仅有效地提高了算法的通用程度，同时也保留强类型语言在编译期检查的好处。
> Generics This long-awaited enhancement to the type system allows a type or method to operate on objects of various types while providing compile-time type safety. It adds compile-time type safety to the Collections Framework and eliminates the drudgery of casting.

所以上述的程序会写成这样：
```
List<Integer> list = new ArrayList<Integer>();
list.add(1);
// list.add("no way"); 编译出错
assertThat(list.get(0), instanceOf(Integer.TYPE));
assertThat(list.get(0), is(1)); // 不需要强制转换
```

泛型编程指的是在强类型语言当中，针对暂未确定的类型进行编程的方式。这些类型最终通过参数指定并被实例化。泛型这个词可能不是通用的，在不同的语言实现中，具有不同的命名。在Java/Kotlin/C#中称为泛型（Generics），在ML/Scala/Haskell中称为Parametric Polymorphism，而在C++中被叫做模板（Template），比如最负盛名的C++中的STL。任何编程方法的发展一定是有其目的，泛型也不例外。泛型的主要目的是加强类型安全和减少强制转换的次数。

减少类型转换次数比较容易理解，在没有泛型（参数化类型）的时候，装进容器的数据，其类型信息丢失了，所以取出来的时候需要进行类型转换。例如：
```
List list = new ArrayList();
list.add(1);

assertThat(list.get(0), instanceOf(Integer.TYPE));
assertThat((Integer)list.get(0), is(1)); //存在强制转换
```
如果有了泛型，我们就不需要这样的类型转化。
```
List<Integer> list = new ArrayList<Integer>();
list.add(1);

assertThat(list.get(0), instanceOf(Integer.TYPE));
assertThat(list.get(0), is(1)); // 不需要强制转换
```
在静态语言中，编译期间的检查非常重要，因为它可以有效地避免低级错误。这些低级错误就是类型安全解决的问题。类型安全包含了赋值安全和调用安全。其底层实质上就是在某块内存中，始终存在被同种类型的指针指向。
1. 类型赋值检查
```
long l_num = 1L;
int i_num = l_num; // 编译错误
```
在强类型的语言当中，类型不一致是无法互相赋值的。

2\. 类型调用检查
 Clojure就是一门强类型语言，而且还是一门函数式语言，所以重新赋值不被允许，它的类型安全表现在针对类型的调用安全。
```
user=> (+ "" 1)
...
java.lang.ClassCastException: java.lang.String cannot be cast to java.lang.Number
```
这里存在一个隐式类型转化的过程，但是由于String无法转化成Number，所以方法调用失败。由于Clojure是动态语言，所以只有在运行时才会抛出错误。

另一个简单的例子，如果一个类型不存在某个方法，那就没法去调用它。在动态强类型语言中，运行时一定会报错。其实质是类型是内存堆上的一块区域，如果该区域之上没有想要调用的方法，那么调用在编译期或者运行期间一定会出错。
```
new Object().sayNothing() // 编译出错
```
为什么说类型安全对于开发人员友好，这个特性对于编程语言很重要？其实这可以追溯到三次编程范式解决的根本问题上。Clean Architecture（架构整洁之道）一书中，对于结构化，面向对象和函数式编程语言做了很透彻的分析。

首先我们得明确一点，这些范式从来没有扩展编程语言的能力，而是在不同方面对编程语言的能力进行了约束。

>1. 结构化编程
对程序的直接控制进行约束和规范，goto considered harmful.
2. 面向对象编程
对程序的间接控制进行约束和规范，pointer considered harmful.
3. 函数式编程
对程序的赋值进行约束和规范，mutability considered harmful.

按照这样的思路，泛型编程无非是对既有的范式做了进一步的约束。

## Kotlin中的泛型编程
### parameterized function 参数化函数
```
fun <T> random(one: T, two: T, three: T): T
```
### parameterized type 参数化类型
```
class Dictionary<K, V>
```
### bounded polymorphism 限定参数化类型
```
fun <T : Comparable<T>> min(first: T, second: T): T {
    val k = first.compareTo(second)
    return if (k <= 0) first else second
}
```
如果需要用多个边界来限定类型，则需要用到`where`语句，表达`T`被多个边界类或者接口限制。
```
class MultipleBoundedClass<T> where T : Comparable<T>, T : Serializable
```
### invariance 不变
```
open class Animal
class Dog : Animal()
class Cat : Animal()
class Box<T>(val elements: MutableList<T>) {
    fun add(t: T) = elements.add(t)
    fun last(): T = elements.last()
}

fun foo(box: Box<Animal>){
}

val box = Box(mutableListOf(Dog()))
// -> val box: Box<Dog> = Box(mutableListOf(Dog()))
box.add(Dog()) // ok
box.add(Cat()) // 编译错误
```
这里出现的编译错误，原因是box的真实类型是`Box<Dog>`，所以尝试向`Box<Dog>`中添加`Cat`对象是不会成功的。这样总能保证类型安全。

`Dog`是`Animal`的子类型，那么编译器是否承认`Box<Dog>`是`Box<Animal>`的子类型，在使用时进行隐式转换呢？
```
val box: Box<Animal> = Box(mutableListOf(Dog())) // type inference failed. Expected type mismatch.
```
编译器是不会允许这样行为发生。原因就是这样做，会导致类型不安全。
假如这种转换是允许的，那么我们就可以继续添加其它继承了`Animal`的子类对象，比如：
```
val box: Box<Animal> = Box(mutableListOf(Dog())
box.add(Cat())
```
这样就导致`Box<Animal>`里面同时保存了`Dog`和`Cat`的对象，正如前面提到的，在运行时，调用可能就会抛出`ClassCastException`，所以这是类型不安全的。

```
fun foo(box: Box<Animal>){
}

val box = Box(mutableListOf(Dog()))
// val box: Box<Dog> = Box(mutableListOf(Dog()))
foo(box) // 编译错误
// 等同于 -> 
val animalBox: Box<Animal> = box // 编译错误
```

### covariance 协变
但是这种限制太过于严苛了，如果我们只需要从这个box读取元素，而不需要往里面添加，那么这种转换就是类型安全的。具体原因稍后再说。

当`Dog`是`Animal`的子类型，那么`Box<Dog>`也是`Box<Animal>`的子类型，这种继承关系就是协变。在Kotlin中，我们需要使用`out`关键字表示这种关系。
```
class CovarianceBox<out T : Animal>(val elements: MutableList<out T>) {
    fun add(t: T) = elements.add(t) //编译错误
    fun last(): T = elements.last()
}
```
基于这种协变关系，我们可以这样调用
```
val dogs: CovarianceBox<Dog> = CovarianceBox(mutableListOf(Dog(), Dog()))
val animals: CovarianceBox<Animal> = dogs
print(animals.last())
```
我们注意上面的`CovarianceBox`的`add`方法出现了编译错误，原因就是在协变关系中，泛型参数只能作为输出参数，而不能作为输入参数。因为在拒绝了输入泛型参数的前提下，协变发生的时候，才不会出现强制转化的错误。举个例子：
```
val dogs: CovarianceBox<Dog> = CovarianceBox(mutableListOf(Dog(), Dog()))
val animals: CovarianceBox<Animal> = dogs
dogs.add(Cat()) // add在这里禁止了
```
如果`CovarianceBox`允许`add`方法，那么box里面就会同时存在多个子类型的实例，这样就会导致类型不安全，所以`out`修饰的参数化类型，只能在函数的返回值上出现。

不过，这种解决方式也不是万能的，属于杀敌一千，自损八百的战术。因为对于`Collection`而言，不可能做到任何泛型参数都不会出现在入参的位置上。
```
public interface Collection<out E> : Iterable<E> {
    public operator fun contains(element: @UnsafeVariance E): Boolean
    public fun containsAll(elements: Collection<@UnsafeVariance E>): Boolean
}
```
所以，针对这种情况，我们知道某些方法其实并不会有添加的操作，可以在入参的位置上加上`@UnsafeVariance`，以此消除掉编译器的错误。

### contravariance 逆变
当`Dog`是`Animal`的子类型，那么`Box<Animal>`也是`Box<Dog>`的子类型，这种继承关系就是逆变。在Kotlin中，我们需要使用`in`关键字表示这种关系。
```
class ContravarianceBox<in T>(val elements: MutableList<in T>) {
    fun add(t: T) = elements.add(t)
    fun first(): T = elements.first() // 编译错误
}
```
基于这种逆变关系，我们可以这样调用
```
val animals = ContravarianceBox(mutableListOf(Animal()))
val dogs: ContravarianceBox<Dog> = animals
dogs.add(Dog())
```
这个时候，类型始终是安全的。但是我们也注意到`ContravarianceBox`的`first`方法出现了编译错误，原因就是在逆变关系中，泛型参数只能作为输入参数，而不能作为输出参数。在拒绝了输出参数的前提下，逆变发生的时候，才不会出现强制转换的错误。
```
val animals = ContravarianceBox(mutableListOf(Animal()))
val dogs: ContravarianceBox<Dog> = animals
dogs.add(Dog())
val dog: Dog = dogs.first() // 编译错误
```

### reification 变现

```
reify is To convert mentally into a thing; to materialize.
```
Kotlin中的Reification的实现使用的是inline模式，就是在编译期间将类型进行原地替换。
```
// 定义
inline fun <reified T : Any> loggerFor(): Logger = LoggerFactory.getLogger(T::class.java)
// 使用
private val logger = loggerFor<AgreementFactory>()
```
因此，所以原来调用处的代码会在编译期间展开成如下：
```
private val logger = LoggerFactory.getLogger(AgreementFactory::class.java)
```
使用`reification`操作，可以精简掉很多模板代码。

### type projection 类型投影
上述过程中，我们看到协变和逆变都是针对可以编辑的类。但是如果遇到已经存在的类，这件事就得运用类型投影技术。拿`Class`这个类举例：
```
val dog = Dog::class.java
val animal: Class<Animal> = dog //编译不通过
```
Kotlin中的type projection就是为了解决这个问题的。
```
val dog = Dog::class.java
val animal: Class<out Animal> = dog
```
同理，
```
val animal = Animal::class.java
val dog: Class<in Dog> = animal
```
我们来看一个真实的场景
```
val agreementClass: Class<RentalAgreement> = RentalAgreement::class.java

private val virtualTable = mapOf(RentalPayload.type to RentalAgreement::class.java)
private fun dispatch(type: String): Class<out 
Agreement<Payload>> {
    return virtualTable[type]
            ?: throw RuntimeException("No suitable Agreement of this type found, please check your type: $type")
}
```
只有这样，我们才能将具体的`Class<RentalAgreement>`投射到`Class<out Agreement<Payload>>`父类型之上，后续通过某种方式，实例化出`RentalAgreement`的实例，其继承自`Agreement<Payload>`。

## 泛型编程的思考
Bob 大叔的 Clean Code 一书的第六章《对象和数据结构》中提到了一个很有意思的现象：数据、对象的反对称性。在这里，数据结构暴露数据，没有提供有意义的函数；对象把数据隐藏起来，暴露操作数据的函数。

过程式代码会基于数据结构进行操作。例如：首先会定义好数据结构`Square`, `Circle`和`Triangle`，然后统一在`area(shape: Any)`的函数中求shape数据的面积，如：
```
fun area(shape: Any): Double {
    return when(shape) {
      is Square -> return shape.side * shape.side
      else -> 0.0
    }
}
```

而面向对象拥趸一定会嗤之以鼻——显然应该抽象出一个shape类包含`area`方法，让其它的形状类继承。如：
```
interface Shape {
    fun area(): Double
}

class Square(val side: Double) : Shape {
    override fun area(): Double {
        return side * side
    }
}
```
在添加新的形状的要求下，面向对象的代码是优于过程式的，因为面向对象对扩展开发了。而过程式代码却不得不修改原来的`area`方法实现。

但是，如果此时，需要添加一个求周长`primeter`的函数。相对于面向对象代码，过程式代码由于无需修改原来的实现，反而更加容易扩展。反观面向对象的代码，在接口`Shape`中添加一个`primeter`会导致所有的子类都得发生修改。

这就是数据和类型的反对称性。在变化方向不同的时候，它们面临的阻力也是不一样的。

如果此时，我们既想要过程式对方法扩展的优点，又执着面向对象自然的类型扩展的好处，该怎么办呢？可以考虑结合起来使用。

这样的结合不是说原有的双向阻力消失了，而是在不同的层次上应用各自的优点。也就是说，`Shape`需要求面积、周长，同时也要支持类型扩展，这种要求之下，基本不可能调解出一种符合开闭原则的方案。不过，如果对于所有`Shape`类，都需要统一进行某些操作，例如：集合的排序，过滤等等。那么合并两者的好处就变得可行了。

基于最先分析的通过继承的方式进行泛型编程的缺点：1. 太多强制转换 2. 非类型安全。恰当地引入了泛型`T`，以期编译期的占位和运行时的替换。不过没有限定的泛型大部分情况下是没有用处的，因为无限的抽象没有意思，所以需要更加精准的泛型限定。

在我们做完这一切以后，会惊喜地发现依赖倒置（DIP）原则贯穿始终。不论是继承体系，还是改善之后的泛型继承体系。它们秉持的原则就是在编译期，始终朝着稳定、抽象的方向移动，而且不断在易变、具体的方向延迟决策，直到运行时方能确定。
