

# Summary
Integration with postgres can be used to store data from Api’s, as well as retrieving data from databases.

# API AutoFlow Version:
Configuration config.json was created using AutoFlow version __0.2.5__

# Need help?
Is you have questions about this example, feel free to post your question on the community "<a href="https://interactor.com/autoflow/questions" target="_blank">Ask Questions</a>" website.

# Storing data:

## Step 1. Create flow
* Create an HTTP Server
* Create an endpoint
  * NOTE: under properties the method must be GET
* From the right panel, press Action tab -> communication, Drag and drop HTTP-Request to the end of the flow
* From the right panel, press Action tab -> json, Drag and drop decode to the end of the flow
* From the right panel, press Action tab -> database -> postgres, drag and drop PostgresSQL-Query
![Image](https://github.com/API-AutoFlow/api-to-postres/blob/master/img/1.png)

## Step 2. Make API Call
### Communication/HTTP-request
#### Properties:
> * url: Api of which data is being requested
> * Method: GET
> * Body: blank
> * Header: blank
> * Query: blank
> * Timeout: Default

#### Output:
> * Output-location: Drag and drop the request body from right panel

## Step 3. Decode Data for easier access
### Json/decode
#### Properties:
> * json: drag drop the request body from right data panel

#### Output:
> * At-location: drag and drop the response body from the right panel

## Step 4. Prepare Postgres query
### String/join
Since the data from API is going to change, we need to prep the Postgress query with whatever we get from the API.

To do that we use the String/join action and join the query message with data from the API call.

#### Properties:
> * json: drag drop the request body from right data panel

## Step 5. Postgress DB call
### Database/postgres/query
#### Properties:
> * Query: SQL string for entering database
> * Address: location of database
> * Port: 5432
> * Username: username of database server
> * Password: password of database server
> * Database: Which database to query
> * Format: Processed
