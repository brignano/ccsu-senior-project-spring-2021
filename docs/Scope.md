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

- Form input: _(all required fields)_
    - Policy number
    - Address (where the Loss occurred)
    - Category of claim (see [iii.org](https://www.iii.org/publications/insurance-handbook/insurance-basics/auto-insurance-basics) for the 6 possible categories)
    - Description of claim
- Submit button  


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

```http
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
### 1. Call to your new API `/getCoordinates` from the frontend `onBlur()` of the Address input field

```http
http://{backend-ip}:{backend-port}/getCoordinates?address=24%20Sussex%20Drive%20Ottawa%20ON
```

### 2. Add a new _read-only_ field to the frontend screen that displays the coordinates returned from the API call above
### 3. Add a new API endpoint to the backend.

<h3>/getClaims</h3>

> This should return all of the claims filtered by the (optional) search criteria

<h4>Request</h4>

```http
GET /getClaims HTTP/1.1
Host: {endpoint}
Authorization: {auth}
Content-Type: application/x-www-form-urlencoded
Content-Length: {len}

    policyNumber?={policyNumber}
    &category?={Category}
```

<h4>Response</h4>

```http
HTTP/1.1 200 OK
Date: {}
Content-Type: {}
Content-Length: {}
```

<br/>


### 4. Add another responsive UI screen. This should contain,

<h4>This should contain:</h4>

- Form input: _(all optional fields)_
    - Policy number
    - Category
- Search button

### 5. Call to your new API `/getClaims` - from your new frontend screen - `onSubmit()` of the Search button field

```http
http://{backend-ip}:{backend-port}/getClaims
http://{backend-ip}:{backend-port}/getClaims?policyNumber=123456
http://{backend-ip}:{backend-port}/getClaims?category=Collision
http://{backend-ip}:{backend-port}/getClaims?policyNumber=123456&category=Collision
```

<br/>

---
<br/>

## Sprint 4 - Innovation Sprint
> Great work! You have successfully created a full stack application and even ingested data from another third-party (Google Maps) API. So what's next? You tell us.  

#### Food for thought,
- Add ability to attach an additional document (i.e. image) to the claim (and store in database)
- Add ability to autocomplete the address as the user is typing (see [Google Maps API Places Autocomplete](https://developers.google.com/maps/documentation/javascript/places-autocomplete))
- Implement HIG UX KIT (see [References.md#frontend](References.md#frontend))
- To be continued…
