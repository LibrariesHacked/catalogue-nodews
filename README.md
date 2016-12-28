# UK Public Libraries Catalogue Web Service

A web service project for searching multiple UK public library catalogues.

## What is it?

In the UK there are around 200 public library authorities, (generally) each one with their own Library Management System and associated Online Public Access Catalogue.

Despite being so many authorities, there are relatively few types of library systems, and fewer suppliers.  This project aims to define the interactions with each **type** of web catalogue in order to automate these into a single web service for all UK library services.

This will provide data aggregation opportunities such as being able to query the UK for the availability of a particular book, or manage a user's account across all their library services.

## Technologies used

The following key plugins/technologies are used - more specific details in third party licensing section.

| Name | Description |
| ---- | ----------- |
| Node JS | Server side JavaScript technology for creating web applications |
| Web | There is a webn front end to this project in order to display a basic search screen. |

## Authority Data

A list of UK public library authorities is included in the **data.json** file.  This has the library authority name and the **type** of library service, along with specific data required to search that service e.g. the web URL. 

It includes the ONS authority code for each authority.  This allows it to be combined with other datasets about that authority published elsewhere.

For example:

| Name | Code | Type | URL | TestISBN |
| ---- | ---- | ---- | --- | -------- |
| Aberdeen City | S12000033 | spydus | https://aberdeencity.spydus.co.uk/ | 9780747538493 |

## Build

The project uses Node Package Manager (NPM) for package management.  On downloading a copy of the project the required dependencies should be installed.  Assuming [Node](https://nodejs.org/en/) is already installed, to build:

```
npm install
```

## Run and deployment

The solution can be run on a local system with [Node JS](https://nodejs.org/) installed.  The solution will be available under localhost at **http://localhost:3000/**.

```
node server.js
```

The solution can be deployed into any production environment set up to run a [Node JS Project](https://nodejs.org/en/).

## Using the web service

The project implements the following web services.

| Service | Description |
| ------- | ----------- |
| Services | Returns stored data about library services. |
| Libraries | Returns branch/location information, taken from the online catalogue. |
| Availability | Returns availability of a particular book. |

### Services

Returns selected contents of the data.json file for each service.  This can be useful if wanting to create an interface that lists the library authorities to then be used in a search filter for retrieving other data.

| URL Route | Description | Example |
| ----- | ----------- | ------- |
| */libraries* | Returns a list of library authorities | *http://localhost:3000/services* |

### Libraries

| URL Route | Description | Example |
| ----- | ----------- | ------- |
| */libraries* | Returns a list of libraries for each service. | *http://localhost:3000/libraries* |
| */libraries?service=:service* | Filters the results to a particular library service. | *http://localhost:3000/libraries?service=Wiltshire* | 

### Availability

| Route | Description | Example |
| ----- | ----------- | ------- |
| */availabilityByISBN/:isbn* | Retrieves availability of a particular book by passing in ISBN.  | *http://localhost:3000/availabilityByISBN/9780747538493* |
| */availabilityByISBN/:isbn?service=:service* | Filters the results to a particular library service. | *http://localhost:3000/availabilityByISBN/9780747538493?service=Gloucestershire* |

Returns data showing the number of available/unavailable copies of the relevant book in each branch, for each library service.

## Third party licensing

In addition to Node, the project uses a number of third party plugins.

| Name | Description | Link | Licence |
| ---- | ----------- | ---- | ------- |
| cheerio | Provides parsing and querying of HTML.  | [Cheerio on GitHub](https://github.com/cheeriojs/cheerio) | [MIT](https://github.com/cheeriojs/cheerio/blob/master/Readme.md) |
| xml2js | Converts XML into JavaScript Objects. | [xml2js on GitHub](https://github.com/Leonidas-from-XIV/node-xml2js) | [MIT](https://github.com/Leonidas-from-XIV/node-xml2js/blob/master/LICENSE) |
| express | Minimalist web application framework for Node. | [Express on GitHub](https://github.com/expressjs/express) | [MIT](https://github.com/expressjs/express/blob/master/LICENSE) |
| request | Simplified HTTP requests framework. | [Request on GitHub](https://github.com/request/request) | [Apache](https://github.com/request/request/blob/master/LICENSE) |

## Licence

Original code licensed with [MIT Licence](Licence.txt).
