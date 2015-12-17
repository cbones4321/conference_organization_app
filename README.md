App Engine application for the Udacity training course.

## Products
- [App Engine][1]

## Language
- [Python][2]

## APIs
- [Google Cloud Endpoints][3]

## Setup Instructions
1. Update the value of `application` in `app.yaml` to the app ID you
   have registered in the App Engine admin console and would like to use to host
   your instance of this sample.
1. Update the values at the top of `settings.py` to
   reflect the respective client IDs you have registered in the
   [Developer Console][4].
1. Update the value of CLIENT_ID in `static/js/app.js` to the Web client ID
1. (Optional) Mark the configuration files as unchanged as follows:
   `$ git update-index --assume-unchanged app.yaml settings.py static/js/app.js`
1. Run the app with the devserver using `dev_appserver.py DIR`, and ensure it's running by visiting your local server's address (by default [localhost:8080][5].)
1. (Optional) Generate your client library(ies) with [the endpoints tool][6].
1. Deploy your application.


[1]: https://developers.google.com/appengine
[2]: http://python.org
[3]: https://developers.google.com/appengine/docs/python/endpoints/
[4]: https://console.developers.google.com/
[5]: https://localhost:8080/
[6]: https://developers.google.com/appengine/docs/python/endpoints/endpoints_tool

## Submission Instructions

1. Speakers are implemented as a property of Sessions. 
I believe that this was the easiest implementation and that is why I choose this route.
Sessions are a child of Conferences, so Conferences are the Ancestor/Parent of Sessions.
Each Session is created with a Conference as the parent.
A Conference can have multiple Sessions, but a Session can be tied to only one Conference.
Also each Session can have only one Speaker. I have chosen name, highlights, speaker and
typeOfSession to all be StringProperty because they are should all be text values.
Name is also a required field for a Session to be created. 
typeOfSession is a repeated field that can hold multiple values. 
Date is a DateProperty because it is a date. 
startTime was created as a TimeProperty because it is the best for time properties. 
Also duration was created as a IntegerProperty because the duration records the duration of a meeting in minutes.

2. I have added a new query.
It can be called using the followinng endpoints method: **getHalfHourSessionsByLarry**. 
The purpose of this query is to return all half hour Sessions that are created by the speaker 'Larry Scott'.
This would be useful for people that would like to register only for 30 min sessions that are by 'Larry Scott'.
I have updated the indexes so that this query works properly.

3. I have added a new query. 
It can be called using the followinng endpoints method: **getLateSessions**. 
The purpose of this query is to return all sessions thatn are after 4pm.
This would be useful for people that would like to see sessions that are later in the afternoon. 
I have updated the indexs so that this query works properly.

4. The problem with implementing this query, is that DataStore does not allow queries with 
multiple inequality filters over multiple properties. 
One way to solve the presented problem is to add a new field.
This field could be used to tell if a session is after 7 pm. 
With the addition of the new field you can grab all Sessions that are before 7 pm
and use the inequality filter to determine whether a session is a workshop or not. 
This is why it is important to figure out what queries will be used in the design phase.
