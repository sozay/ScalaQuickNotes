# ScalaQuickNotes
Scala programming language quick review code structure

Defined immutable 
	val x 

String interpolation
	val approc = 255/133f
	 println(s"Pi, using 355/113, is about $approx." )
	val item = "apple"
s"How do you like them ${item}s?"

Convert  value to a value of the desired type: asInstanceOf[<type>]  
	5.asInstanceOf[Long]

Check type: isInstanceOf 
	(5.0).isInstanceOf[Float]

Convert a value to compatible value: to<type>
	20.toByte; 47.toFloat

