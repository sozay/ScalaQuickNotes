# ScalaQuickNotes
Scala programming language quick review code structure

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


