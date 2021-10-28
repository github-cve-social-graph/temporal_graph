# temporal_graph
This repo aims to generate temporal graph to understand how user events with respect to a github issue change over time particularly scraping data from: https://github.com/torvalds/linux

The code folder contains the users_to_issues_temporal_graph.ipynb that does the following:
1. Using perceval to fetch github issues within a time period.
2. Using the github timeline API (https://docs.github.com/en/rest/reference/issues#timeline) for each issue to fetch events which provides us information about users who were involved in an issue. Involvement could be any github issue events like subscribe, comment, react, pushing commits, merging etc. (https://docs.github.com/en/developers/webhooks-and-events/events/issue-event-types).
3. The following csv are generated:
a. issues.csv - csv contains a list of issues with columns id which represents unique issue id and label specifies the issue number.
b. users.csv - csv contains a list of users with columns id representing unique user id and label is the user name.
c. edgeList.csv -csv contains the relationship between issues and users along with a timestamp. It contains the columns: source, target, type, label, timeset, weight. 
The source contains the userId and the target is the issueId, type tells us if it is directed or not and the label gives a name to the relationship telling us about which user event was performed by the user towards the issue. The timeset contains the timestamp when the event was performed. 
Note: All the above three files( a to c) can be used to generate a timeline graph using gephi, whose file is also available under images. 
d. temporal_edgeList.csv - This csv is similiar to the above just that it contains three columns - source, target and time. This is done because generating temporal graph using pathpy, simply requires this format to work with. A html file is generated which is available under images. 

Since the data is already available, executing the notebook from the third cell onwards should suffice. 
The html file under images contains the temporal graph. 


