step 1: 
for setting account

install putty

maria_dev@127.0.0.1
port# 2222
password: maria_dev
step 2:
setting up super user

su root
Password: hadoop
it asks change password
give existing one -- hadoop
new password: vinny

after that exit
step 3:
setting up admin user

su root
password: root

after login-> enter following
ambari-admin-password-reset
it asks password for ambari admin
Please set the password for admin: vinny

after that, it starts the ambari server

then start the following command:

ambari-agent restart
step: 4
go to browser:

127.0.0.1:8080
username: admin
password: vinny

********************* below one is not needed for you ***********************

then exit

go to kafka server thru the putty:

username: maria_dev
password: vinny

cd /usr/hdp/current/kafka-broker
then goto bin

create a topic:

./kafka-topics.sh --create --zookeeper sandabox.hortonworks.com:2181 --replication-factor 1 --partitions 1 --topic venn

to list the topics 
./kafka-topics.sh --list --zookeeper sandbox.hortonworks.com 2181

for producing the data:

./kafka-console-producer.sh --broker-list sandbox.hortonworks.com:6667 --topic venn

after above command:

enter some messages and enter

open another session with putty

login to unix

cd /usr/hdp/current/kafka-broker/bin

./kafka-console-consumer.sh --bootstrap-server sandbox.hortonworks.com:6667 --zookeeper localhost:2181 --topic venn --from-beginning
