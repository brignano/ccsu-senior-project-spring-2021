# Project Scope

### Table of Contents
1. [v1 (Sprint 1 - Setup Foundation)](#v1-sprint-1--setup-foundation)
2. [v2 (Sprint 2 - Enhance Capabilities)](#v2-sprint-2--enhance-capabilities)
3. [v3 (Sprint 3 - Add Searching)](#v3-sprint-3--add-searching)
4. [v4 (Sprint 4 - Innovation Sprint)](#v4-sprint-4--innovation-sprint)

## v1 (Sprint 1 - Setup Foundation)
1. Develop a responsive UI screen. This should contain,
- A way to input the required data:
  - Policy Number
  - Location (Address)
  - Category of Claim (see iii.org for the 6 categories)
  - Description of Claim
- A submit button
2. Create a backend API.
3. Add an API endpoint - **/addClaim** - to your backend that accepts a POST request
- The body of this POST request will contain the above 4 data points
- As the result of this POST request, the 4 data points contained in the request body should be stored in a database

## v2 (Sprint 2 - Enhance Capabilities)
1. Make a POST request from the UI screen to your API endpoint (**/addClaim**) ```onSubmit()``` of the submit button
- This should send all the data entered by the user (assuming all required fields were filled) in the POST request to your backend API
- As a result, this data should get stored in your database by the backend API
2. Add an API endpoint - **/getCoordinates** - to your backend that accepts a GET request
- The parameter of this GET request should be an address  
>(CWC8+R9 Mountain View, CA, USA is CWC8%2BR9%20Mountain%20View%20CA%20USA)
- As a result of this GET request, you should return the addresses coordinates using Google Geocoding API (https://developers.google.com/maps/documentation/geocoding/overview#GeocodingResponses)

## v3 (Sprint 3 - Add Searching)
1. Make a GET request from the UI screen to your API endpoint (**/getCoordinates**) ```onBlur()``` of the address input field
- This should append the Address to the endpoint as a GET request parameter (i.e. http://localhost:8080/getCoordinates?address=CWC8%2BR9%20Mountain%20View%20CA%20USA)
- As a result, your backend API should respond to the UI with the coordinates of this address that it got from Google Geocode API
2. Add a read-only UI field that displays the coordinates once they are returned by your API but is disabled from direct user input
3. Add API endpoint - **/getClaims** - to your backend that accepts a GET request
- The parameter of this GET request should be a Policy Number
- As a result of this GET request, you should return all of the claims in your database for that Policy Number
4. Add another responsive UI screen. This should contain,
- A way to input the required data:
  - Policy Number
- A search button
5. Make a GET request from the new UI screen to your API endpoint (**/getClaims**) ```onSubmit()``` of the search button
- This should append the Policy Number to the endpoint as a GET request parameter (i.e. http://localhost:8080/getClaims?policyNumber=123456)
- As a result, your backend API should respond to the UI with the list of claims for that policy number in your database

## v4 (Sprint 4 - Innovation Sprint)
1. Innovation sprint
> Great work, you have successfully created a frontend that can both read and write to a database by using a backend and even communicated with another third-party API (Google Maps API). So what's next? You tell us.  
#### Food for thought,
- Add ability to attach an additional document (i.e. image) to the claim (and store in database)
- Add another GET parameter to **/getClaims** API endpoint that enables claims to be returned by category (i.e. http://localhost:8080/getClaims?category=Collision)
- To be continued…
