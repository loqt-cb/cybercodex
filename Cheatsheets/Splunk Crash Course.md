-Search Queries-
index="dataset" chooses a dataset, * would select any or all indexes.
earliest=0, tells splunk to start looking at the first event in the dataset, preventing the need to change the date range.

The sampling on the side allows you to select the size of the pool of events sampled in the search.

Fields allow filtering for the type of event that is listed.

noisy means excessive traffic.

search src = "ipaddr" searches source ip addresses

-commands-
sort - sorts the events returned by a search
ex:     sort time asc (sorts chronologically)
        sort limit=2 time asc (shows the first two events from the search query

stats - provides statistics about the results from the search query

table - create a custom table of the data we want to display, and hide everything else.
ex:     | table date, time, srcip, dstport, action, msg. (a table with the date, time, srcip, dstport, action, and msg.)

uniq - used to retrieve unique values from our search results.

-alerts-

1. Search query:
    Decide what activity you want to generate an alert. An example would be an external IP trying to Secure shell into a server.

2. Search timing:
    Set how often Splunk is going to run the search query to look for any activity that makes the alert conditions.
    There are two options:
        Continuously run this search query to look for related activity in real time
        Run this search query on a set schedule.

3. Alert Trigger:
    Designing the alert to trigger for an event that you would actually want it to occur. Example used was that you do not want an alert to trigger every time someone gets their password wrong, but rather 4 or 5 times.

4. Alert Action
    Determining what you actually want to happen when an alert triggers. Examples include an email notificaiton, log, adding an alert to recently triggered alerts.

To create your own rule:
First, write a search query, ionce it is written click save as, and then alert.
Give it permissions, whether or not you want to be the only one to access the alert or have it shared.
Then determine the alert type, whether you want it to be scheduled or real-time.
Then, set the actions you want it to take, what will happen once the alert is active.
