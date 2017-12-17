# AppUsage-Tracker

# Authors
Yu Kaiwen - yu.kaiwen.amelie@gmail.com

# Contents
1. Introduction
2. Description of Application 
3. Scenario of Execution
4. Principal Functionalities
5. Each Components of Application
6. Global Architecture  
7. Justification of the Usage of Techniques  
8. Plan of Project
9. Conclusion

# Introduction 
In this report, I will first introduce my application AppUsage Tracker. Then I will describe in detail the whole process for a user to interact this application. From the detailed description of interacting process, I can abstract the main functionalities of this application, so that I can transform these literal descriptions of functionalities to the technical problems and build these components of application. After I combined these components, there comes the global architecture of application. I’ll explain the reason that I build this architecture and the tools that I use for build it before I talk about the plan of project.

# Description of Application 
AppUsage Tracker is an Android application who tracks the usage of all the applications on that device who installs this application. 

It shows a no-ordered list of the total time of usage and the total open times for each application. The user can choose to see daily data, weekly data, monthly data or yearly data. The user can choose to sort the list in descending order or increasing order according to the total time of usage or the total open times.

It offers the user a functionality to analyse these information of the usage of applications to know the three applications that the user used the most frequently and the longest time in that day or that month or that year. These three applications can be seen as what the user most needs and likes. The user can add these three applications’ shortcuts to the welcome screen of this application by settings so that the user can redirect to these applications easily. The user can add the three most favorite application applications of a day (or a week or a month or a year) by settings.

# Scenario of Execution

# Principal Functionalities
1. Show a no-ordered list of the total time of usage and the total open times for each application (daily/weekly/monthly/yearly)
2. Sort this list according to the total time of usage or the total open times in descending order or increasing order
Analyse this (daily/weekly/monthly/yearly) list of information of usage according to both of these two attributes (total time of usage and total open times) to get the three applications which have both the highest time and the highest open times
3. Add the shortcuts of these three (daily/weekly/monthly/yearly) most favorite applications to the welcome screen of this application by settings 

# Technical Details for Each Functionality
- For realising the 4.1 functionality, I’ll use the UsageStatsManager of the android.app.usage API to get the information of usage of each application from the android device. This API is new after the android 5.0. 
What information of usage can the android device provide? It records these main information for each application : 
- The last used time
- The total time in foreground
- The timestamps that in that day, the app changed its statues (from foreground to background, from background to foreground)
- The timestamps that the app changed its settings (from landscape to portrait, from portrait to landscape)
- The identifier information of the app (the package name, the activity name etc.)

The android device stores on the device 7 days’ daily information of usage,  4 weeks’ weekly information of usage, 6 months’ monthly information of usage and 2 years’ yearly information of usage. 

In order to allow the user to check the results of the previous each time’s requirement of information of usage, I’ll store the information of usage got from the android device each time the user asks this application to do it. The process will be like : the user opens this application, clicks the button to get the list of information of usage, once this collection of data is done, the data will be stored on the remote server automatically. 

For simplicity, the user can only check the daily information of usage of the day started from the moment the user asks to the previous moment one-day ago. Similarly, the weekly information of usage of the week started from the moment the user asks to the previous moment one-week  ago, the monthly information of usage of the month started from the moment the user asks to the previous moment one-month ago, the yearly information of usage of the year started from the moment the user asks to the previous moment one-year ago.

- For realising the 4.2 functionality, it should use an algorithm of sorting. 
Since the list of information of usage has three columns, the application’s name, the total time of usage and the total open times of this application, the algorithm of sorting can sort the whole list according to either of these two attributes (time/times) of each application in descending order or increasing order.

- For realising the 4.3 functionality, I’ll use the clustering method, K-Means, of undirected Data Mining to analyse a list of two-attribute data. 

Since both the total time of usage and the total open times can only be positive, all the data collected can only show up in the first quadrant. The horizontal axis is the total time of usage. The vertical axis is the total open times. 
We can imagine the location of total data as a square map whose borders are decided by the most outside data. If we divide this square map in this first quadrant into 4 quadrants again, then the object of the clustering method, K-Means, is to divide the data into 4 natural groups and find the group which locates itself in the first quadrant of this square map (if there’s no such group, then find the group in the fourth quadrant of this square map, since in this application, we suppose that the total time of usage is more important for the user than the total open times. It gives more weight to the total time than the total open times.) 

How can we find such a group? We can use the location of the center point of each group to find such a group. This group is a list of two-attribute elements. If the total number of elements in this list is not greater than 3, then show these applications to the user. If there are more than 3 elements in this list, sort this list in descending order according to the attribute, the total time of usage (since it has more weight than the other attribute), and then show the three applications listed on top to the user. 

- For realising the 4.4 functionality, when I get the information of usage of applications on the android device, I can also get the information of each application itself like its package name which can help me to redirect to and open this application from my application. This can be easily done on the activity.

# Global Architecture


# Justification of the Usage of Techniques 
# Plan of Project
# Conclusion


