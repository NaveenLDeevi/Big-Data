# Big-Data-Clustering-Mahout
K-Means Clustering
The K-Means algorithm is to cluster data points into different partitions based on some distance
measures. In this part, you need to do K-Means algorithm in both Command line and your own
Mapper/Reducer to find clusters of given files using Euclidean distance (see page 32 of slides)
Did the following,
1. Download and unzip data from Reuters newswire
https://kdd.ics.uci.edu/databases/reuters21578/reuters21578.html
2. Create tf-idf vector representing .sgm documents using command line. You may use
a. $mahout seqdirectory for converting documents to SequenceFile format
b. $mahout seq2sparse for creating vectors from SequenceFile
For more information, please read
https://mahout.apache.org/users/basics/creating-vectors-from-text.html
We have to do this step because Mahout command line takes TF-IDF VectorWritable
input for doing KMeans on text documents
3. Use $mahout kmeans command line to find cluster centroids.
a. Set k=4, maxIter=10 , and distance function as
Check mahout kmeans command line:
https://mahout.apache.org/users/clustering/k-means-commandline.html
b. input : The TF-IDF file generated from step 2.
c. output : The command line will generate a sequence file . You should make it
human-readable using $mahout clusterdump command.
https://mahout.apache.org/users/clustering/cluster-dumper.html
4. Write a MapReduce program to find centroids and its members with k-means clustering.
Your program must have the following parameters:
a. input : Download input_kmeans.txt from Blackboard. The file has the
following format:
id1<\tab>number1,number2,...,number10
id2<\tab>number1,number2,...,number10
...
b. output : Output centroids and their members
cluster1<\tab>id1, id2,...
cluster2<\tab>id1, id2,...
...
c. k : Number of centroids. Set k=4 .
d. maxIter : Stop criterion. For simplicity, stop after a certain number of iterations.
Set maxIter=10 .
