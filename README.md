# Date.now Php
 
 
Browser. I tested calling this function running a perspective session via a browser. I'm getting strange behavior when data is inserted into the database (using only system.date.now and system.date.getTimezoneOffset, not any database now functions) from a client in the central timezone.
 
Our server is in the mountain timezone, I store timestamps in the database in 4 columns: UTC, CST, MST, and EST. I am now getting odd values in the database from users in the central time zone, which we just recently started having users in the central time zone.
 
**Download File ►►► [https://8tenquitratru.blogspot.com/?zb=2A0Tej](https://8tenquitratru.blogspot.com/?zb=2A0Tej)**


 
MS SQL Server? Its datetime column doesn't play nicely with java.util.Date, and converts to/from a localtime format using the gateway to DB connection properties, which is typically the gateway timezone.
 
Basically, I'm getting the UTC offset based on system.date.now, then getting the UTC time from that offset (assuming that the system.date.now() is not in UTC when called). I then assumed that system.date.getTimezone() would change and that's why I have the if statements at the bottom.
 
Don't do that. One instant in time, regardless of zone, is exactly and correctly represented by a java.util.Date object. If you serialize it and send to another machine, it **displays** in that machine's timezone, but is still the same point in real time.
 
But system.date.now() **IS** UTC. If you need to convert strings to/from UTC everywhere in your gateway, set your gateway timezone to UTC. If you need to use a variety of time zones in gateway scripts (and Perspective scripts), you will need to ask java to render in a specific time zone instead of the gateway timezone. Some techniques:
 
Let me emphasize what I wrote in an earlier comment: java.util.Date **objects** are UTC milliseconds under the hood. They already **are** UTC. Java converts them to strings for **display** in the JVM's timezone. When a java.util.Date object is serialized and transmitted to a client or designer, it travels **as UTC**. And then gets stringified in a local time zone wherever the stringification happens.
 
This. system.date.now() returns a Date object; system.date.addSeconds knows how to work with a Date object, and returns a modified one. Within Ignition, always use Date objects directly as much as you can - only format to string at the last possible moment for display purposes.
 
Generally it's a bad idea to be querying the historian databases because it's so much work due to the data compression and the data partitioning which, by default, creates a new table for each month. Let Ignition do all the grunt work for you.

So, I've got an integer array (length 6) that gets written to using this tag's value changed script. It's length 6 because as part of the process I update the current index and clear the next before incrementing the index.
 a2f82b0cb4
 
