The sample log I'm using to mess around with is a Windows Server ISS
log. I used this link as a resource for the status codes:

[[https://forums.ivanti.com/s/article/IIS-Status-Codes?language=en_US]{.underline}](https://forums.ivanti.com/s/article/IIS-Status-Codes?language=en_US)

### Searching and Commands

intuitive searching, allows for boolean AND OR NOT. can also use
parentheses. can filter by time, most helpful. allows \* for wildcards.
use backslashes "\\" to escape quotes within quotes

commands start by adding a "\|" pipe character.

This sample log I have is pretty barebones, I wish I had a more diverse
log to play around with commands

Here is a command I made that would count the number of events with
sc_status="331" and then split the count based on the value of the field
cs_method. I have no idea what the field cs_method refers to, or what
most of this sample log means for the most part, so I can't really
provide any analysis on the results, but I still like messing around
with the data.

![](output\Random Splunk Notes/media/image3.png){width="9.603685476815398in"
height="3.7054680664916884in"}

Then, I made an additional filter to remove any cs_method that has
counts greater than 36170 (completely arbitrary)

![](output\Random Splunk Notes/media/image1.png){width="9.463542213473316in"
height="3.2826662292213475in"}

I also learned about a "replace" command. I think it could be good for
huge edits to the log. Here, I added a command to replace the host name
with just "AWAD" for fun.

![](output\Random Splunk Notes/media/image2.png){width="7.28007217847769in"
height="4.223958880139983in"}
