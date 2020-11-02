# BigData-Spark-Project
I have found the top 10 word count using spark
## Input Data
1. I took data from "http://www.columbia.edu/~fdc/sample.html"
2. I kept only text and removed all extra characters using below command.
    sed -e 's/[^a-zA-Z]/ /g;s/  */ /g' columbia.txt > columbia_cleaned.txt
## Processed data using Spark
1. SetUp Spark :  https://github.com/denisecase/setup-spark
2. Open PS Admin run spark-shell 
3. val data = sc.textFile("hamlet_cleaned.txt")
4. val datasplit = data.flatMap(line => line.split(" "));
5. val mapdata = datasplit.map(word =>(word,1));
6. val reducedata = mapdata.reduceByKey(_+_);
7. val result = reducedata.sortBy(_._2, false)
8. result.take(10)
9. result.saveAsTextFile("Top10words")
## Visualization
![](Visual.png)
