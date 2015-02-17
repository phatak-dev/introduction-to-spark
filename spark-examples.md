## Create RDD


### In-memory data

    val lines = List("hello how are you","i am fine how are you?")
    val rdd = sc.makeRDD(lines)
    rdd.collect()

### From file

    val fileRDD = sc.textFile("README.md")
    fileRDD.collect()


## Word Count example

    val words = fileRDD.flatMap(line => line.split("\\s+"))
    val wordsMapping = words.map(word => (word,1))   // Pair
    val result = wordsMapping.reduceByKey((a,b) => a+b) // Shuffle RDD
    result.collect()

## Types of RDD

  * MappedRDD

  * FlatMappedRDD

  * Shuffle RDD

  * Double RDD

  etc


## Double RDD example

    val doubleList = List(1.0,2.0,4.0,5.0)
    val doubleRDD = sc.makeRDD(doubleList)
    doubleRDD.sum

    /*
       This will give error
       fileRDD.sum
    */


## Filtering

    val sparkLines = fileRDD.filter(line => line.contains("spark"))


## Count

    sparkLines.count()




## Key,Value pair operations

    val salesRDD = sc.textFile("sales.csv")
    val customerPair = salesRDD.map(line => {
       val cols = line.split(",")
       ( cols(1),  cols(3).toDouble)
    })



### countByKey

    customerPair.countByKey


### groupByKey

    val groupByCustomer = customerPair.groupByKey
    groupByCustomer.collect()


### lookUp

    val lookUpCustomer = customerPair.lookup("1")


### joins

    val customerRDD = sc.textFile("customers.csv")
    val customerInfo = customerRDD.map(value => {
      val cols = value.split(",")
     (cols(0), cols(1))
    })

    val joinedRDD = customerPair.join(customerInfo)



## Caching

    customerRDD.cache()

    //Removing underneath file customers.csv

    customerRDD.collect()



