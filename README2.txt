https://www.edureka.co/blog/hadoop-tutorial/

https://www.edureka.co/blog/mapreduce-tutorial/

https://www.edureka.co/blog/pig-tutorial/

https://www.edureka.co/blog/operators-in-apache-pig

http://cs.boisestate.edu/~amit/research/code-camp-2011-mapreduce-hadoop.pdf

http://www.hadoopwizard.com/install-hadoop-on-windows-in-3-easy-steps-for-hortonworks-sandbox-tutorial/

HADOOP_HOME=D:/hadoop-2.8.1
HADOOP_CONF=D:/hadoop-2.8.1/etc/hadoop
HADOOP_MAPRED_HOME=D:/hadoop-2.8.1
HADOOP_COMMON_HOME=D:/hadoop-2.8.1
HADOOP_HDFS_HOME=D:/hadoop-2.8.1
YARN_HOME=D:/hadoop-2.8.1
HADOOP_PID_DIR=%HADOOP_HOME%/hadoop_data\hdfs\pid



HADOOP_COMMON_LIB_NATIVE_DIR=%HADOOP_HOME%/lib/native

PATH=%HADOOP_HOME%/bin

LD_LIBRARY_PATH=%HADOOP_HOME%/lib/native

****************************

http://toodey.com/2015/08/10/hadoop-installation-on-windows-without-cygwin-in-10-mints/

http://hadooponwindows.blogspot.in/2016/09/apache-hadoop-installation-on-windows.html

http://www.filewatcher.com/m/hadoop-2.7.1.tar.gz.210606807-0.html

http://log.malchiodi.com/2015/12/09/installing-hadoop-271-from-scratch-2015-version/

mapred-site.xml

<?xml version="1.0"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<!--
  Licensed under the Apache License, Version 2.0 (the "License");
  you may not use this file except in compliance with the License.
  You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License. See accompanying LICENSE file.
-->

<!-- Put site-specific property overrides in this file. -->

<configuration>
	<property>
		<name>mapreduce.framework.name</name>
		<value>yarn</value>
	</property>

</configuration>

****************

yarn-site.xml

<?xml version="1.0"?>
<!--
  Licensed under the Apache License, Version 2.0 (the "License");
  you may not use this file except in compliance with the License.
  You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License. See accompanying LICENSE file.
-->
<configuration>

<!-- Site specific YARN configuration properties -->
	<property>
		<name>yarn.nodemanager.aux-services</name>
		<value>mapreduce_shuffle</value>
	</property>
	
	<property>
		<name>yarn.nodemanager.auxservices.mapreduce.shuffle.class</name>
		<value>org.apache.hadoop.mapred.ShuffleHandler</value>
	</property>

</configuration>
*********************************

hdfs-site.xml

<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<!--
  Licensed under the Apache License, Version 2.0 (the "License");
  you may not use this file except in compliance with the License.
  You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License. See accompanying LICENSE file.
-->

<!-- Put site-specific property overrides in this file. -->

<configuration>
	<property>
            <name>dfs.replication</name>
            <value>1</value>
     </property>
     <property>
            <name>dfs.namenode.name.dir</name>
            <value>file:/hadoop-2.7.2/hadoop_data/hdfs/namenode</value>
     </property>
     <property>
            <name>dfs.datanode.data.dir</name>
            <value>file:/hadoop-2.7.2/hadoop_store/hdfs/datanode</value>
     </property>
     <property>
            <name>dfs.permissions</name>
            <value>false</value>
     </property>

</configuration>

********************************

core-site.xml

<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<!--
  Licensed under the Apache License, Version 2.0 (the "License");
  you may not use this file except in compliance with the License.
  You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License. See accompanying LICENSE file.
-->

<!-- Put site-specific property overrides in this file. -->

<configuration>
	<property>
		<name>fs.default.name</name>
		<value>hdfs://localhost:9000</value>
	</property>
</configuration>

*********************

to start hadoop

1   go to hadoop bin dir
		bin/hadoop namenode -format

2   goto sbin

		start-dfs.bat


		start-yarn.bat

		mr-jobhistory-daemon.bat start historyserver


to know the processes

jps

to check

http://localhost:50070

******************

to copy the file to the hdfs

hadoop dfs -put D:/path/to/file/input  /

to read the file
hadoop dfs -cat /input

to run the code
hadoop jar hadoop-mapreduce-examples.jar wordcount /input  /outpudir

hadoop dfs -ls /outputdir

to read file

hadoop dfs -cat /outputdir/part-r-0000

hadoop examples

D:\hadoop-2.8.1\share\hadoop\mapreduce>hadoop jar hadoop-mapreduce-examples-2.7.1.jar

moving file to hadoop

D:\hadoop-2.8.1\share\hadoop\mapreduce>hadoop dfs -put C:\Users\venkatram.veerareddy\Desktop\input.txt /

reading a file 

D:\hadoop-2.8.1\share\hadoop\mapreduce>hadoop dfs -cat /input.txt

running the examples
D:\hadoop-2.8.1\share\hadoop\mapreduce>hadoop jar hadoop-mapreduce-examples-2.7.1.jar wordcount /input.txt /wcOutEx


to see the outputdir

D:\hadoop-2.8.1\share\hadoop\mapreduce>hadoop dfs -ls /wcOutEx

D:\hadoop-2.8.1\share\hadoop\mapreduce>hadoop dfs -cat /wcOutEx/part-r-00000



D:\hadoop-2.8.1\share\hadoop\mapreduce>hadoop jar d:\work\hadoop\out\artifacts\WordCount_jar\WordCount.jar \input.txt \venn

D:\hadoop-2.8.1\share\hadoop\mapreduce>hadoop dfs -cat /venn/part-r-00000

******************************

import java.io.IOException;
import java.util.*;
import org.apache.hadoop.fs.Path;
import org.apache.hadoop.conf.*;
import org.apache.hadoop.io.IntWritable;
import org.apache.hadoop.io.LongWritable;
import org.apache.hadoop.io.Text;

import org.apache.hadoop.mapreduce.Job;
import org.apache.hadoop.mapreduce.Mapper;
import org.apache.hadoop.mapreduce.Reducer;
import org.apache.hadoop.mapreduce.lib.input.FileInputFormat;
import org.apache.hadoop.mapreduce.lib.output.FileOutputFormat;
import org.apache.hadoop.mapreduce.lib.output.TextOutputFormat;


/**
 * Created by venkatram.veerareddy on 7/26/2017.
 */
public class WordCount {

    public static class Map extends Mapper<LongWritable, Text, Text, IntWritable>{
        public void map(LongWritable key, Text value, Context context)
                throws IOException, InterruptedException{
            String line = value.toString();
            StringTokenizer tokenizer = new StringTokenizer(line);
            while(tokenizer.hasMoreTokens()){
                value.set(tokenizer.nextToken());
                context.write(value, new IntWritable(1));
            }
        }
    }

    public static class Reduce extends Reducer<Text, IntWritable, Text, IntWritable>{
        public void reduce(Text key, Iterable<IntWritable> values, Context context)
                throws IOException, InterruptedException{
            int sum = 0;
            for(IntWritable w: values){
                sum += w.get();
            }
            context.write(key, new IntWritable(sum));
        }
    }

    public static void main(String[] args) throws Exception{
        Configuration conf = new Configuration();
        Job job = Job.getInstance(conf,"WordCount");
        job.setJarByClass(WordCount.class);
        job.setMapperClass(Map.class);
        job.setReducerClass(Reduce.class);

        job.setOutputKeyClass(Text.class);
        job.setOutputValueClass(IntWritable.class);


        job.setInputFormatClass(org.apache.hadoop.mapreduce.lib.input.TextInputFormat.class);
        job.setOutputFormatClass(TextOutputFormat.class);

        Path outputPath = new Path(args[1]);
        FileInputFormat.addInputPath(job, new Path(args[0]));
        FileOutputFormat.setOutputPath(job, new Path(args[1]));
        outputPath.getFileSystem(conf).delete(outputPath,true);
        System.exit(job.waitForCompletion(true) ? 0 : 1);

    }
}
*****************
ftp://ftp.ncdc.noaa.gov/pub/data/uscrn/products/daily01

https://www.eduonix.com/blog/bigdata-and-hadoop/hadoop-project-on-ncdc-national-climate-data-center-noaa-dataset/


**************************************

import java.io.IOException;
import org.apache.hadoop.fs.Path;
import org.apache.hadoop.conf.*;
import org.apache.hadoop.io.IntWritable;
import org.apache.hadoop.io.LongWritable;
import org.apache.hadoop.io.Text;

import org.apache.hadoop.mapreduce.Job;
import org.apache.hadoop.mapreduce.Mapper;
import org.apache.hadoop.mapreduce.Reducer;
import org.apache.hadoop.mapreduce.lib.input.FileInputFormat;
import org.apache.hadoop.mapreduce.lib.output.FileOutputFormat;
import org.apache.hadoop.mapreduce.lib.output.TextOutputFormat;
/**
 * Created by venkatram.veerareddy on 7/27/2017.
 */
public class MaxMinTemperature {



    public static class Map extends Mapper<LongWritable, Text, Text, IntWritable>{
        public static final int MISSING = 9999;
        public void map(LongWritable key, Text value, Context context)
                throws IOException, InterruptedException{

            String line = value.toString();
            if(!(line.length() == 0)){
                String date = line.substring(6,14);
                int tempMax = (int)Float.parseFloat(line.substring(39,45).trim());

                int tempMin = (int)Float.parseFloat(line.substring(47,53).trim());

                if(tempMax > 35.0 && tempMax != MISSING){
                    context.write(new Text("Hot Day " + date), new IntWritable(tempMax));
                }

                if(tempMin < 10.0 && tempMax != MISSING){
                    context.write(new Text("Cold Day " + date), new IntWritable(tempMin));
                }
            }

        }
    }

    public static class Reduce extends Reducer<Text, IntWritable, Text, IntWritable>{
        public void reduce(Text key, Iterable<IntWritable> values, Context context)
                throws IOException, InterruptedException{

            int temp = 0;
            for(IntWritable w: values){
                temp = w.get();
            }
            context.write(key, new IntWritable(temp));
        }
    }

    public static void main(String[] args) throws Exception{
        Configuration conf = new Configuration();
        Job job = Job.getInstance(conf,"MaxMinTemperature");
        job.setJarByClass(MaxMinTemperature.class);
        job.setMapperClass(Map.class);
        job.setReducerClass(Reduce.class);

        job.setOutputKeyClass(Text.class);
        job.setOutputValueClass(IntWritable.class);


        job.setInputFormatClass(org.apache.hadoop.mapreduce.lib.input.TextInputFormat.class);
        job.setOutputFormatClass(TextOutputFormat.class);

        Path outputPath = new Path(args[1]);
        FileInputFormat.addInputPath(job, new Path(args[0]));
        FileOutputFormat.setOutputPath(job, new Path(args[1]));
        outputPath.getFileSystem(conf).delete(outputPath,true);
        System.exit(job.waitForCompletion(true) ? 0 : 1);

    }


}


puting file into hadoop

D:\hadoop-2.8.1\share\hadoop\mapreduce>hadoop dfs -put D:/work/min-max-temp.txt /

reading file from hadoop
D:\hadoop-2.8.1\share\hadoop\mapreduce>hadoop dfs -cat /min-max-temp.txt

D:\hadoop-2.8.1\share\hadoop\mapreduce>hadoop jar d:\work\MaxMinTemp\out\artifacts\MaxMinTemp_jar\MaxMinTemp.jar \min-max-temp.txt \temperature

hadoop dfs -ls /temperature

hadoop dfs -cat /temperature/part-r-00000

*****************************************************************
https://github.com/aamend/lastfm-mapreduce

import java.io.IOException;
import java.util.HashSet;
import java.util.Set;

import org.apache.hadoop.fs.Path;
import org.apache.hadoop.conf.*;
import org.apache.hadoop.io.IntWritable;
import org.apache.hadoop.io.LongWritable;
import org.apache.hadoop.io.Text;

import org.apache.hadoop.mapreduce.Job;
import org.apache.hadoop.mapreduce.Mapper;
import org.apache.hadoop.mapreduce.Reducer;
import org.apache.hadoop.mapreduce.lib.input.FileInputFormat;
import org.apache.hadoop.mapreduce.lib.output.FileOutputFormat;
import org.apache.hadoop.mapreduce.lib.output.TextOutputFormat;
/**
 * Created by venkatram.veerareddy on 7/27/2017.
 */
public class LastFM {

    public class LastFMConstants {
        public static final int USER_ID = 0;
        public static final int TRACK_ID = 1;
        public static final int SHARED = 2;
        public static final int RADIO = 3;
        public static final int SKIPPED = 4;
    }

    public static class UniqueListenerMapper extends Mapper<LongWritable, Text, Text, IntWritable>{
        IntWritable trackId = new IntWritable();
        IntWritable userId = new IntWritable();
        public void map(LongWritable key, Text value, Context context)
                throws IOException, InterruptedException{

            String[] parts = value.toString().split("[|]");
            trackId.set(Integer.parseInt(parts[LastFMConstants.TRACK_ID]));
            userId.set(Integer.parseInt(parts[LastFMConstants.USER_ID]));
            context.write(new Text(trackId.toString()), userId);

        }
    }

    public static class UniqueListenerReduceer extends Reducer<Text, IntWritable, Text, IntWritable>{
        public void reduce(Text key, Iterable<IntWritable> values, Context context)
                throws IOException, InterruptedException{

            Set<Integer> userIdSet = new HashSet<>();
            for(IntWritable w: values){
                userIdSet.add(w.get());
            }
            context.write(key, new IntWritable(userIdSet.size()));
        }
    }

    public static void main(String[] args) throws Exception{
        Configuration conf = new Configuration();
        Job job = Job.getInstance(conf,"LastFM");
        job.setJarByClass(LastFM.class);
        job.setMapperClass(UniqueListenerMapper.class);
        job.setReducerClass(UniqueListenerReduceer.class);

        job.setOutputKeyClass(Text.class);
        job.setOutputValueClass(IntWritable.class);


        job.setInputFormatClass(org.apache.hadoop.mapreduce.lib.input.TextInputFormat.class);
        job.setOutputFormatClass(TextOutputFormat.class);

        Path outputPath = new Path(args[1]);
        FileInputFormat.addInputPath(job, new Path(args[0]));
        FileOutputFormat.setOutputPath(job, new Path(args[1]));
        outputPath.getFileSystem(conf).delete(outputPath,true);
        System.exit(job.waitForCompletion(true) ? 0 : 1);

    }


}

hadoop dfs -put D:/work/lastfm.txt /

hadoop dfs -cat /lastfm.txt

hadoop jar d:\work\LastFm\out\artifacts\LastFm_jar\LastFm.jar \lastfm.txt \lastfm

hadoop dfs -ls /lastfm

hadoop dfs -cat /lastfm/part-r-00000

data

17|220|1|1|0
13|230|1|0|1
14|120|0|1|0
17|220|1|1|0
12|260|1|1|0
15|10|1|1|0
15|10|0|0|1
18|200|1|1|0
18|200|0|1|0
12|260|1|0|1
19|220|1|1|0
12|200|1|0|1
19|210|0|1|0

***********************************


HIVE

create database myretail

show databases

use <database name>



describe extended <tableName>

LOAD DATA LOCAL INPATH '/home/cloudera/hive_demo/recharge.input' INTO TABLE recharge

hadoop fs -ls /user/hive/warehouse/telecom.db

hadoop fs -lsr /user/hive/warehouse/telecom.db

create external table recharge_extrnl(rechange string, valume int, name string)
row format delimited fields terminated by "," LOCATION '/hive_demo/extnl/';


create table transactions(txno INT, txndate String, custNo INT, amount DOUBLE,
category string, product string, city string,state string, spendBy string)
row format delimited fields terminated by "," stored as textfile;

hadoop fs -ls /user/hive/warehouse/

hadoop fs -ls /user/hive/warehouse/myretail.db

LOAD DATA LOCAL INPATH '/home/cloudera/hive_demo/trans.txt' INTO TABLE transaction

describe transactions

*********************************************************

scott stein

hbase commands

list

create 'htest', 'cf'

put 'htest', 'r1', 'cf:c1', 'v1'
put 'htest', 'r1', 'cf:c2', 'v2'
put 'htest', 'r1', 'cf:c3', 'v3'

scan 'htest'

get 'htest', 'r1'

put 'htest', 'r1', 'cf:c3', 'v3_updated'
put 'htest', 'r1', 'cf:c3', 'v3_updated again'

get 'htest', 'r1',{COLUMN=>'cf:c3', VERSION=>3}

get 'htest', 'r1',{COLUMN=>'cf:c3', TIMESTAMP=>'12121212'}

disable 'htest'
alter 'htest', {NAME=>'cf_altered'}
enable 'htest'
describe 'htest'

delete 'htest','r1','cf:c3'

scan 'htest'

disable 'htest'
drop 'htest'
list


https://www.youtube.com/watch?v=zF32ZRNlBWU   (good one HBase)
