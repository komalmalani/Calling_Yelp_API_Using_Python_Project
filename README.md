# Problem Statement
To understand what are APIs and call an API through python
# What is an API ?
An application programming interface (API) is a way for two or more computer programs to communicate with each other. It is a collection of communication protocols and subroutines used by various programs to communicate between them.It takes the request from the user and sends it to the service provider and then again sends the result generated from the service provider to the desired user.
References:
https://www.geeksforgeeks.org/introduction-to-apis/
https://en.wikipedia.org/wiki/API

# what is HTTP?
Websites that expose a web API typically use the HTTP method for the request.
HTTP (Hypertext Transfer Protocol) is a protocol which allows the fetching of resources. It is the foundation of any data exchange on the Web and it is a client-server protocol, which means requests are initiated by the recipient, usually the Web browser.
References:
https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview
[Just into data API Call](https://www.justintodata.com/python-api-call-to-request-data/#:~:text=Python%20Example%20%231%3A%20Yelp%20API%20call%201%20Step,...%204%20Step%20%234%3A%20Check%20the%20Response%20)

Assume we are using the web browser to communicate with the server from a website. Each time we want the site to do something (for example, send the data), we must submit an HTTP request (make an API call) to the server. Then the server provides a response message as the answer. The response could contain the data requested (if applicable) and some other information like completion status.

The two common HTTP request methods for API calls are GET and POST:

Within a GET request, the query strings/parameters are sent in the URL, which is easy to bookmark or save. But we can only send ASCII characters and a limited amount of data. Requests using GET should only retrieve data.
Within a POST request, the query parameters typically are sent in the body of the request message. This method is a little more secure. We can send both ASCII and binary data and more data than a GET request. This method can be used to send data to the server.

# What are ome common HTTP response status codes ?
- 200: The request was a success. – the data requested should be in the response.
- 400: Bad Request – the request was invalid due to bad syntax.
- 401: Unauthorized – missing or incorrect authentication credentials.
- 403: Forbidden – you are not allowed to see the data requested based on your authentication.
- 404: Not Found – the URL is invalid, or the resource does not exist, or you are unauthorized to see it.
- 502: Bad Gateway – the servers might have issues.

# Python Example #1: Yelp API call
## Step #1: Read the Documentation
It is always advisable to read documentation for any API that you want to call to know
1. the data we can request for.
2. the parameters we can set when asking for data.
3. sample requests and responses.

For example, to find the Yelp API document, you can search ‘Yelp API’ in the web browser. Within the Yelp [developers](https://www.yelp.com/developers/) page, we can see different tools offered by Yelp; we’ll focus on the Yelp Fusion.

Yelp Fusion has several Business Endpoints. Each endpoint is a path that’s used to retrieve different data from the API. For example, the /businesses/search endpoint returns up to 1000 businesses based on the provided search criteria. It has some basic information about the business

## Step #2: Create Authentication Keys
The APIs usually require authentication when we call for data. This often has 2 steps:

1. register for a (developer) account of the website.
2. create an app and generate the API keys.

You can think of the API keys as credentials that authenticate you as the user of the API. The API keys should be kept secret like other passwords
The Yelp Fusion API [documentation](https://docs.developer.yelp.com/docs/fusion-authentication) provides detailed instructions on how to set up the authentication. You can follow it to obtain the API key before moving onto the next step.
## Step #3: Create Request
We will use python to call yelp API using 'requests' package
In python file, we will star coding by
1. Importing "requests" package
2. Copy the Yelp API key and assign it to a variable api_key
3. Find out the base URL for the API endpoint. For example, the base URL for the Yelp Fusion business search is https://api.yelp.com/v3/businesses/search.

We’ll be sending a GET request to call for data. Before using the GET method, let’s specify the input variables with this basic information:

### headers with the API key.
Following the API sample code structure, we set up the request headers as a dictionary with the authentication information.
### search_api_url with the API endpoint URL (https://api.yelp.com/v3/businesses/search).
### params with some search parameters/criteria.
For example, we can search for 50 businesses with the term “coffee” located in ‘Toronto, Ontario’, as shown in the code below.
For more details about the parameters, you can look at the documentation. There are some mandatory parameters and some optional parameters.
### timeout
Then we can feed these variables and form the GET response object called response. We also set timeout = 5 to stop Requests from waiting for a response after 5 seconds.
## Step #4: Check the Response
- print(response.url) : To check the response URL
- print(response.status_code) : Status code for success
- print(response.headers) : Headers
- data_dict=response.json() #Converting response in dictionary
- data_dict['businesses'][0] - First Business

