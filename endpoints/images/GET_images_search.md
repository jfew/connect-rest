# Image Resources

    GET images/search

## Description
Return listing of 10 (up to 300) images from search results for a specified search term.

***

## Requires authentication
Via /token endpoint, passed in via digest authentication.

***

## Parameters
- **searchphrase** _(required)_ — A keyword to search for.

- **language** _(optional)_ — Language in which to return certain image metadata (e.g. keywords, restrictions). Default is en-us.
- **coordination_id** _(optional)_ - An ID unique to the request for coordination and debugging purposes.
- **collections** _(optional)_ — Comma-separated list of CollectionIds on which to filter search results.
- **collections_filter_mode** _(optional)_ — Specify whether collections filter is including or excluding specified collection IDs from search results. Valid values are "include" and "exclude." Default is "include" when a value is specified for "collections."
- **editorial_segments** _(optional)_ - Only applicable to searches where image_family is set to "editorial." Valid values are "news," "sports," "entertainment," "publicity," "royalty" and "archival."
- **item_count** _(optional)_ - 

***

## Return format
An array with the following keys and values:

- **current_page** — Number of the page that is returned.
- **total_pages** — Total number of pages in this feature's stream.
- **total_items** — Total number of items in this feature's stream.
- **images** — An array of Image objects.

***

## Errors
- **400 Bad Request** — The request issued is missing one or more of the required parameters or contains parameters in an invalid form.
- **401 Unauthorized** - The specified application and/or user credentials are not recognized.

***

## Example
**Request**

  GET http://connect.gettyimages.com/api/images/search?searchphrase=dachshund

**Return**
``` json

```