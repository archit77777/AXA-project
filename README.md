# AXA-project

Code can be run using:
pip3 install -r requirements.txt
spark-submit AXA_Spark.py

If parameter tuning needed:
spark-submit --master yarn \
--deploy-mode cluster \
--executor-memory 2G \
--executor-cores 3 \
AXA_Spark.py

Points considered while writing this code:
1) It used master local but this shouldn't be used in the production environment.
   We can use any master we want in the spark-submit script.
2) Cluster tuning paremeters should be specified while using spark-submit command. Ideal way:
spark-submit \
--master yarn \
--deploy-mode cluster \
--executor-memory 2G \
--executor-cores 3

3) The Action_time column has been converted to the local timestamp, but we can format it to UTC too if needed.
4) Data has been written to CSV files but in high scale systems it should be written to parquet files.
5) Input Files can be read from folders, different directories and from command line.
6) This project can be setup on Docker too. Not done for this project to save time.
7) We can define the SparkSession in a different file so that it can be used with a number of other code files.
   It has the benefit of re-using only 1 SparkSession in all the difference code files.
