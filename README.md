# Scala Quick Notes
Scala programming language quick language review

**Defined immutable** 
```scala
val x 
```

**String interpolation**
```scala
val approc = 255/133f
println(s"Pi, using 355/113, is about $approx." )
val item = "apple"
s"How do you like them ${item}s?"
```

**Convert  value to a value of the desired type: asInstanceOf[<type>]**
```scala
5.asInstanceOf[Long]
```

**Check type: isInstanceOf**
```scala
(5.0).isInstanceOf[Float]
```

**Convert a value to compatible value: to<type>**
```scala
20.toByte; 47.toFloat
```

**Tuble:**
```scala
val info = (5, "Korben", true)
//get second
val name = info._2
```
**Expression Blocks**
```scala
val amount = {val x = 5 * 20; x + 10}
val result = if ( false ) "what does this return?" else "heyo"
Case:
  	val kind = day match {
		case "MON" | "TUE" | "WED" | "THU" | "FRI" =>
	          "weekday"
	        case "SAT" | "SUN" =>
	          "weekend"
	        case other => 
		"wtf"
	      }
	• case _ => <one or more expressions> ( _  means any here)
```
**ForMap**
```scala
for (x <- 1 to 7) { println(s"Day $x:") }
//Return collection 
for (i <- 1 to 20) yield i
//or
for (i <- 1 to 20 if i % 3 == 0) yield I
```	
**Option[T] is a container for zero or one element of a given type.**
```scala
val capitals = Map("France" -> "Paris", "Japan" -> "Tokyo")
capitals.get( "France" ) //Some(Paris)
capitals.get( "Turkey" ) //None
```	
**define a function**
```scala
def multiplier(x: Int, y: Int): Int = { x * y }
	
def log(d: Double) = println(f"Got value $d%.2f")
def log(d: Double) { println(f"Got value $d%.2f") }
	
//Call without parenthesis
def  hi(): String = "hi"
	
//call with >>hi   or hi()
		
def formatEuro(amt: Double) = f"€$amt%.2f"
		
//>>formateuro {val rate=1.32; 0.235 + 0.7123 + rate * 5.32}
```
**Vararg Parameters**
```scala
def sum(items: Int*): Int = {
	var total = 0
	for(i <- items) total+= i
	total
}
```
**Parameters Group**
```scala
def max(x: Int)(y: Int) = if (x > y) x else y
var larger = max(20)(39)
```
**Type generic function**
```scala
def identity[A](a: A): A = a
	
val s: String = identity[String]("hello")   
//Or better
Identity("hello")  //because scala provides is type inference
```
**Invoke with operator notation**
```scala
d.compare(18)
d compare 18.0
3.+(4)
3 + 4
```	
**Function more**
- Function types
```scala
Int => Int
def double(x: Int): Int= x * 2
val myDouble: (Int) => Int = double
```		
- Function as parameter
```scala
def safeStringOp(s: String, f: String => String) = {
	if (s != null) f(s) else s
}
```
- Function Literals
```scala
val doubler = (x: Int) => x * 2
val hello = (name: string) => s"Hello $name"
safeStringOp("Ready", (s: String) => s.reverse)
```
**Placeholder syntax**

It can be used when (a) the explicit type of the function is specified outside the literal and (b) the parameters are used no more than once.
```scala
val doubler: Int : Int => _ * 2
safeStringOp("Ready",_.reverse)
```
**Partially Applied Func**
```scala
def factorof(x: Int,y:Int) = y%x == 0
def multipleOf3 = factorOf(3,_: Int)
val isEven = factorOf(2) _
```

**Send Function literal as parameter**
```scala
val timedUUID = safeStringOp(uuid) { s =>
	val now = System.currentTimeMillis
	val timed = s.take(24) + now
	timed.toUpperCase
}
```
**Collections**
```scala
List(123,23,1232)
val A = List(123,23,1232)
a.head  //123
a.tail     //1232
a(1)       //23
```
**Loop**
```scala
var total = 0; for (i <- numbers) { total += i }
```

**foreach,map,reduce**

```scala
val colors = List("red", "green", "blue")
colors.foreach( (c: String) => println(c) )

//map:convert a new single list element to another value list
val sizes = colors.map( (c: String) => c.size )

//combines two list elm. in to single
val total = numbers.reduce( (a: Int, b: Int) => a + b )

**FlatMap**
val list = List(1,2,3,4,5)
list: List[Int] = List(1, 2, 3, 4, 5)

def g(v:Int) = List(v-1, v, v+1)
//>>g: (v: Int)List[Int]

list.map(x => g(x))
//>>res0: List[List[Int]] = List(List(0, 1, 2), List(1, 2, 3), List(2, 3, 4), List(3, 4, 5), List(4, 5, 6))

list.flatMap(x => g(x))
//>>res1: List[Int] = List(0, 1, 2, 1, 2, 3, 2, 3, 4, 3, 4, 5, 4, 5, 6)


Set(10,20,20,30,20)
val sum = unique.reduce( (a: Int, b: Int) => a + b )    //60
    
al colorMap = Map("red" -> 0xFF0000, "green" -> 0xFF00,"blue" -> 0xFF)
Val redRGB = colorMap("red")
colorMap.contains("white")
for (pairs <- colorMap) { println(pairs) }
//>>(red,16711680)….


//In function
def visit(i: List[Int]) { if (i.size > 0) { print(i.head + ", ");
visit(i.tail) } }

val numbers = 1 :: 2 :: 3 :: Nil
//numbers: List[Int] = List(1, 2, 3)

val f = List(23, 8, 14, 21) filter (_ > 18)

val p = List(1, 2, 3, 4, 5) partition (_ < 3)
//>>p: (List[Int], List[Int]) = (List(1, 2),List(3, 4, 5))

List("apple", "to") sortBy (_.size)
 
List(34, 29, 18) contains 29

//Addition
Val first = Nil.::(1)
2 :: first

Val app = List(1,2,3) :+5

List(1,2):::List(2,3)

List(1,2,3) drop 2
```


**Mutable it**

List, Set, and Map immutable collections , howewer, they can transformed into new collections
```scala
val nums = collection.mutable.Buffer[Int]()
//Convert Mutable
val m = Map("AAPL" -> 597, "MSFT" -> 40)
var l = m.toBuffer
```


**Array**

Mutable
```scala
var l = Array("red","green","purple")
```

Sequence
indexed (direct-access) lists like Vector
```scala
val inks = Seq('c','m','y','k')
```
##Class
```scala
class Car(val make: String, var reserved: Boolean) {
	def reserve(r: Boolean): Unit = { reserved = r }
}

class Lotus(val color: String, reserved: Boolean) extends
  Car("Lotus", reserved)
```

**Anonymous Classes**
```scala
abstract class Listener { def trigger }

val myListener = new Listener {
        def trigger { println(s"Trigger at ${new java.util.Date}") }
     }
 ```

**Apply methods**

Uses as default method
```scala
class Multiplier(factor: Int) {
	def apply(input: Int) = input * factor
}

val tripled = tripleMe.apply(10)
val tripled = tripleMe(10)
```

**Lazy Values**
```scala
class RandomPoint {
	val x = { println("creating x"); util.Random.nextInt }  //calculated on creation
	lazy val y = { println("now y"); util.Random.nextInt }
}
```

**Package**
```scala
//import All elements
import collection.mutable._
//More than more
import collection.mutable.{Queue,ArrayBuffer}
```

**Protected,private exist**

Private class: Can access only from same package classes

Final class: Like property, method, class an never be overridden any of subclasses

**Objects, Case Classes, and Traits**

Objects known in object-oriented design as a singleton.An object gets automatically instantiated the first time it is accessed in a running JVM

```scala
object Hello { println("in Hello"); def hi = "hi" }

//with constructer
class Multiplier(val x: Int) { def product(y: Int) = x * y }

object Multiplier { def apply(x: Int) = new Multiplier(x) }
```

**Case Classes**

includes several automatically generated methods,Case classes work great for data transfer objects like apply,copy,equals,hasCode,toString,unapply

```scala
case class Character(name: String, isThief: Boolean)
val h = Character("Hadrian", true)    
val r = h.copy(name = "Royce")        
h == r   //False
```
**Traits**

- can extend multiple traits at the same time
- traits cannot be instantiated
- There is no interface element in scala,traits is used for this

```scala
trait Equal {
   def isEqual(x: Any): Boolean
   def isNotEqual(x: Any): Boolean = !isEqual(x)
}
```

trait is very similar abstract classes in java
-but abstract classes can have constructer parameter
-abstract classes are interoperable with java, traits also is, but only they don't contain implementation 

**Importing Instance Members**
```scala
val latteReceipt = Receipt(123, 4.12, "fred", "Medium Latte")
import latteReceipt._
println(s"Sold a $title for $amount to $who")   //Receipt elements
```
**Implicit classes**

type-safe way to “monkey-patch” new methods and fields onto existing classes
```scala
object ImplicitClasses {
        implicit class Hello(s: String) { def hello = s"Hello, $s" }
        def test = {
          println( "World".hello )
        }
     }
```
**Types**
```scala
 type UserInfo = Tuple2[Int,String]
 val u: UserInfo = new UserInfo(123, "George")
```


**TRY**
```scala
val number = try {
	DangerousService.queryNextNumber
} catch { case e: Exception =>
 	e.printStackTrace
 	60
}
```

Try blocks return always a value
Working try:
```scala
def parseURL(url: String): Try[URL] = Try(new URL(url))
val url = parseURL(Console.readLine("URL: ")) getOrElse new URL("http://duckduckgo.com")
```
**FUTURE**

allow you to work with asynchronous code in a type-safe and straightforward manner without
resorting to concurrent primitives like threads or semaphores

```scala
val number1F = Future { DangerousAndSlowService.queryNextNumber }  //async
val number2F = Future { DangerousAndSlowService.queryNextNumber } //async

number1F.onSuccess { case number1 =>
number2F.onSuccess { case number2 =>
	println(number1 + number2)
	}
}


//OR better

val sumF = number1F.flatMap { number1 =>
number2F.map { number2 =>
	number1 + number2
 	}
}

//OR

val sumF = for {
	number1 <- number1F
	number2 <- number2F
 } yield number1 + number2
 ```
