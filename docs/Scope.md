# Project Scope

### Table of Contents
0. [Sprint 0 - Inception Phase](#sprint-0---inception-phase)
1. [Sprint 1 - Setup Foundation](#sprint-1---setup-foundation)
2. [Sprint 2 - Enhance Capabilities](#sprint-2---enhance-capabilities)
3. [Sprint 3 - Add Searching](#sprint-3---add-searching)
4. [Sprint 4 - Innovation Sprint](#sprint-4---innovation-sprint)

> For an architectural overview please refer to the [High Level Design](https://github.com/brignano/ccsu-senior-project-fall-2020/wiki/High-Level-Design)

<br/>

---
<br/>

## Sprint 0 - Inception Phase  
1. Review and complete the [Guidebook.md](Guidebook.md)
2. Create a new frontend project
3. Create a new backend project
4. Complete proof of concept for database

<br/>

---
<br/>

## Sprint 1 - Setup Foundation
### 1. Add a responsive UI screen to the frontend.

<h4>This should contain:</h4>

- Form input:
    - Policy Number
    - Location (Address where the Loss occurred)
    - Category of Claim (see [iii.org](https://www.iii.org/publications/insurance-handbook/insurance-basics/auto-insurance-basics) for the 6 possible categories)
    - Description of Claim
- Submit button.  


### 2. Add a new API endpoint to the backend.

<h3>/addClaim</h3>    
    
> This should insert the data to your database
    
<h4>Request</h4>


```http
POST /addClaim HTTP/1.1
Host: {endpoint}
Authorization: {auth}
Content-Type: application/x-www-form-urlencoded
Content-Length: {len}

    policyNumber={PolicyNumber}
    &location={Location}
    &category={Category}
    &description={Description}
```
    
<h4>Response</h4>
    
```http
HTTP/1.1 200 OK
Date: {}
Content-Type: {}
Content-Length: {}
```
    
<br/>

---
<br/>

## Sprint 2 - Enhance Capabilities
### 1. Call to your new API endpoint `/addClaim` from the frontend ```onSubmit()``` of the Submit button

```
http://{backend-ip}:{backend-port}/addClaim
```

### 2. Add a new API endpoint to the backend.

<h3>/getCoordinates</h3> 

> This should return the location coordinates using [Google Geocoding API](https://developers.google.com/maps/documentation/geocoding/overview#GeocodingResponses)

<h4>Request</h4>

```http
GET /getCoordinates HTTP/1.1
Host: {endpoint}
Authorization: {auth}
Content-Type: application/x-www-form-urlencoded
Content-Length: {len}

    location={location}
```

    **Note:** `CWC8+R9 Mountain View, CA, USA` _becomes_ `CWC8%2BR9%20Mountain%20View%20CA%20USA`

<h4>Response</h4>

```http
HTTP/1.1 200 OK
Date: {}
Content-Type: {}
Content-Length: {}
```

<br/>

---
<br/>

## Sprint 3 - Add Searching
1. Make a GET request from the UI screen to your API endpoint (**/getCoordinates**) ```onBlur()``` of the address input field
- This should append the Address to the endpoint as a GET request parameter (```http://localhost:8080/getCoordinates?address=CWC8%2BR9%20Mountain%20View%20CA%20USA```)
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
- This should append the Policy Number to the endpoint as a GET request parameter (``http://localhost:8080/getClaims?policyNumber=123456```)
- As a result, your backend API should respond to the UI with the list of claims for that policy number in your database

<br/>

---
<br/>

## Sprint 4 - Innovation Sprint
> Great work, you have successfully created a frontend that can both read and write to a database by using a backend and even communicated with another third-party API (Google Maps API). So what's next? You tell us.  

#### ood for thought,
- Add ability to attach an additional document (i.e. image) to the claim (and store in database)
- Add another GET parameter to **/getClaims** API endpoint that enables claims to be returned by category (```http://localhost:8080/getClaims?category=Collision```)
- Add ability to autocomplete the address as the user is typing (see [Google Maps API Places Autocomplete](https://developers.google.com/maps/documentation/javascript/places-autocomplete))
- Implement HIG UX KIT (see [References.md#frontend](References.md#frontend))
- To be continued…
