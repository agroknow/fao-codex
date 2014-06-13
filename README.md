fao-codex
=========

Finder of FAO-Codex

Current implementation is based in a prior Ariadne implementation.
It's a front-end application implemented with HTML, CSS and Javascript.

## How to build and configure it:

The interface is implemented in three .html pages.
- index.html which is the landing page
- listing.html which is the listing page
- item.html which is the view item page

### index.html
this is mainly a static page with a search box and links with canned queries that lead to listing page

### listing.html
this is the page that shows the results of the search.
The javascript file that contains all the functionality for search is in /js/finder-js/finder.js (see also /docs/finder.html)

What is important in listing.html is the function `customizeFinder` which (surprizzeeee) customizes the finder.

#####The options here are:
- "selectedProviders": array with the providers we want to filter the results. i.e. ["aglrfaocdx", "oeeprints"].
	if empty returns all the collections.

- "externalSources": ["wp","scr","ss","gb"]

- "pageContainers": ['bottom','top']

- "facets": array with the facets we want to enable in our listing page. i.e. ["provider","language","lrt", "context", "iur"]

- "limitFacetDisplay": Object with arrays of facets limitations. i.e {"language":["en","es"]}

- "maxLengthDescription": int with the wanted length for description in snippets i.e 300

- "pageSize": int with the number of results per page

- "repositoryName": "Organic.Edunet" (find this in the ariadne.properties file inside your Ariadne folder  ex."repositoryName":"AriadneNext Repository")

- "serviceUrl":"http://54.228.180.124:8080/OE_Repos/api/ariadne/restp" (this is the url of the service we want to use)

### item.html
this is the page that shows all the information for a specific resource.
In head we call:

getItemJSONP('http://54.228.180.124:8080/akifRetriever/getAKIF?ids='+location.search.split("=")[1]);

we split the url in order to get the resource 'id' and create a request url for akifRetriever as a paramater to the function.
the getItemJSONP function is defined in /js/ariadne-json.js (see also /docs/ariadne-json.js ) and makes everything needed for rendering properly the results in
the html.



