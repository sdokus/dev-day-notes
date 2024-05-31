# Intro to The Events Calendar REST API 
## What is REST API?

Essentially, REST (REpresentation State Transfer) API is like a bridge that allows different parts of your website to communicate and share information (AKA state). In other words, it can be a way for you (the client) to communicate with your website (the server) through HTTP requests. When you make a request, the server will send back a response based on which action and endpoint you are requesting.

When trying to access the REST API, certain things should be considered for best results:

HTTP requests involve GET - fetch a resource, PUT - update a resource, POST - create a resource, and DELETE - remove a resource. 

All requests to the API should be done only over HTTPS. Considering security, HTTPS connections ensure privacy for the users working with the API.

If something is blocking the REST API endpoints your calendar won't work properly - the endpoints are required by our V2 views (More on this in the troubleshooting section below)

This guide will walk you through how to get your calendar function. You can find a more advanced guide here and our technical documentation here.

## Base URL for The Events Calendar

There is a lot more information about WordPress REST API, though from here on out we are going to focus on just the REST API for The Events Calendar (TEC). The recipe for all TEC REST API calls starts with the same basic ingredients, called the base URL:

[your-site-URL]/wp-json/tribe/events/v1/{endpoint}

Let's break this down further.

[your-site-URL]/ - this is the part of the request asking where we want to get information from (AKA which server)

/wp-json/tribe/events/v1 - this indicates that we want information from TEC events in a JSON format
    The wp-json actually is part of WP Core REST API (https://developer.wordpress.org/rest-api/key-concepts/#routes-endpoints)

/{endpoint} - this part is what we are asking about

Using our demo site as an example, this is what our request would look like to return all events (you can test this by putting the URL right into your browser):

GET https://demo.theeventscalendar.com/wp-json/tribe/events/v1/events

And that would return a JSON that looks something like this:

{
"events": [
{
"id": 1762,
"global_id": "demo.theeventscalendar.com?id=1762",
"global_id_lineage": [
"demo.theeventscalendar.com?id=1762"
],
"author": "2",
"status": "publish",
"date": "2022-12-01 12:36:40",
"date_utc": "2022-12-01 17:36:40",
"modified": "2023-12-19 14:00:59",
"modified_utc": "2023-12-19 19:00:59",
"url": "https://demo.theeventscalendar.com/event/hosted-dinner-with-chef-monica-geller/",
"rest_url": "https://demo.theeventscalendar.com/wp-json/tribe/events/v1/events/1762",
"title": "Hosted Dinner with Chef Monica Geller",
"description": "<p>Join Chef Moinca Geller for a Hosted Dinner! She will discuss how her weight loss contributed to her wanting to be a chef all while preparing her guests a healthy, balanced meal for you to enjoy.</p>",
"excerpt": "",
"slug": "hosted-dinner-with-chef-monica-geller"
... // cut short for brevity

As you can see if you tried going directly to that URL, the response can be very long - luckily there are a bunch of different endpoints to explore so you can get the response that you're looking for!