## Type inference

    val integer = 1 // inferred as int

    val doubleValue = 1.0

    val array = Array(1,2,4,5)

    val list = List(1,2,4,5)


## Functions

    def add( a : Int , b :Int) = a+b

    add (10,20)


## Function variables

    val functionVariable = (a:Int) => a+1
    functionVariable(10)


## Collection

    val list = List(1,2,4,5,6)

### map

    val addOne = list.map(value => value + 1)

### flatMap

     val lines = List("hello how are you","i am fine how are you?")
     val words = lines.flatMap(line => line.split("\\s+")

###  Tuple

    val tupleList = words.map(word => (word,1))

### reduce

     val list = List(1,2,4,5,6)
     val sum = list.reduce((a,b) => a+b)














