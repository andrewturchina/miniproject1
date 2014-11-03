ME495 Tag Tracking
========================


## Mini Project 1 ##

This is a project from ME495: Embedded Systems in Robotics. There is a written portion and a demo using turtlesim.


## Obtaining a copy of the repository for questions 1-2##

Clone the repository for [this homework](https://github.com/NU-MSR/me495_hw1)

## Question 1: The single node contains one publisher and one subscriber##
Start by running:
roscore  
rosrun me495_hw1 ros_cl_demo  

**(a) What are the names of the corresponding topics?**  

rostopic list gives:

demo_publish_topic  
demo_subscriber_topic


**(b) Describe the message definition for each of the topics.**

rostopic info demo_publish_topic  
Type: me495_hw1/ME495Pub  (package/message name)

Publishers:  
 /me495_cl_demo (http://msr-andrew15:40745/) 

Subscribers:  None

rosmsg show me495_hw1/ME495Pub  
std_msgs/Header header  
  uint32 seq  
  time stamp  
  string frame_id  
float32 time  
float32 configuration  

rostopic info demo_subscriber_topic  
Type: std_msgs/String  

Publishers: None  

Subscribers:  
/me495_cl_demo (http://msr-andrew15:40745/)  

rosmsg show std_msgs/String  
string data  

rosmsg show String  
[std_msgs/String]:  
string data  

rosmsg show ME495Pub  
[me495_hw1/ME495Pub]:  
std_msgs/Header header  
  uint32 seq  
  time stamp  
  string frame_id  
float32 time  
float32 configuration  


**(c) What packages define the messages?**  

me495_hw1/ME495Pub is defined in  me495_hw1 package  
std_msgs/String is defined in std_msgs package  


**(d) What frequency (approximately) does the publisher publish data at?**

50hz

~$ rostopic hz /demo_publish_topic  
subscribed to [/demo_publish_topic]  
average rate: 49.993  
	min: 0.019s max: 0.021s std dev: 0.00051s window: 47  
average rate: 50.000  
	min: 0.019s max: 0.021s std dev: 0.00052s window: 98  
average rate: 50.000  
	min: 0.019s max: 0.021s std dev: 0.00052s window: 148  
average rate: 49.998  
	min: 0.019s max: 0.021s std dev: 0.00052s window: 198  
average rate: 50.003  
	min: 0.019s max: 0.021s std dev: 0.00052s window: 248   


**(e) Use rqt plot to plot the data being published, what is the data?**

rqt_plot
/demo_publish_topic/time 
/demo_publish_topic/configuration 




**(f) Publish a message on the subscriber’s topic to trigger a callback in the node. What happens in the terminal where the node is running?**

rostopic pub /demo_subscriber_topic std_msgs/String "help me" 
[ INFO] [1413594651.604594995]: Manipulated String: em pleh

It's written backwards...except when I type racecar...


## Question 2: The node also contains a single service provider##

**(a) What is the name of the service?**

rosservice list  
/me495_cl_demo/get_loggers  
/me495_cl_demo/set_logger_level  
/me495_math_server  
/rosout/get_loggers  
/rosout/set_logger_level  

rosservice type me495_math_server   
me495_hw1/ME495Srv ( package / name of the service)

rosservice type /me495_cl_demo/get_loggers   
roscpp/GetLoggers  ( package / service name)  

rosservice type /me495_cl_demo/set_logger_level   
roscpp/SetLoggerLevel   


**(b) Describe the definition of the service request and response.**

rossrv show me495_hw1/ME495Srv   
uint32 input ( request )  

uint8 output ( response)  


**(c) What does this service do?**

This service gives the number of digits of numerical input. But it doesn't with string inputs.

rosservice call /me495_math_server "input: 100 "  

output: 3  

rosservice call /me495_math_server "input: 10000 "  

output: 5  



## Question 8: Write the node that makes the turtle follow a figure eight##

See code with comments below:

