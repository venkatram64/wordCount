To start the hadoop go to sbin directory run the start-all.cmd

add hadoop-common-2.7.1.jar, hadoop-mapreduce-client-core-2.7.1 into class path

make executable jar then follow the following steps

step 1: moving file to hadoop


D:\hadoop-2.7.1\share\hadoop\mapreduce>hadoop dfs -put C:\Users\xxx\Desktop\input.txt /

step 2: reading a file

D:\hadoop-2.7.1\share\hadoop\mapreduce>hadoop dfs -cat /input.txt

step 3: running the examples
D:\hadoop\hadoop-2.7.1\sbin>hadoop jar D:\freelance-work\hadoopMR\wordCount\out\artifacts\wordCount_jar\wordCount.jar /input.txt /wcOutEx



step 4: to see the outputdir

D:\hadoop-2.7.1\share\hadoop\mapreduce>hadoop dfs -ls /wcOutEx

step 5: to see the outputdir results

D:\hadoop-2.7.1\share\hadoop\mapreduce>hadoop dfs -cat /wcOutEx/part-r-00000