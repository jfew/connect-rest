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
- **item_count** _(optional)_ - Number of results returned per search response. Default is 10. Can specify up to 300.
- **item_start_number** _(optional)_ - Start offset for results returned per search response. Default is 1. Cannot exceed total number of results.
- **sort_order** _(optional)_ - Order of search results. Specific to editorial vs creative image family searches.
- **refinement_options_set** _(optional)_ - Specify a configuration name for the number and types of refinements returned in search results for further filtering.
- **coordination_id** _(optional)_ - An ID unique to the request for coordination and debugging purposes.

- **collections** _(optional)_ — Comma-separated list of CollectionIds on which to filter search results.
- **collections_filter_mode** _(optional)_ — Specify whether collections filter is including or excluding specified collection IDs from search results. Valid values are "include" and "exclude." Default is "include" when a value is specified for "collections."
- **editorial_segments** _(optional)_ - Only applicable to searches where image_family is set to "editorial." Valid values are "news," "sports," "entertainment," "publicity," "royalty" and "archival."
- **exclude_nudity** _(optional)_ - Filters out potentially objectionable nude images from search results.
- **file_types** _(optional)_ - Filter search results by EPS or JPG images.
- **graphic_styles** _(optional)_ - Filter search results by photography vs illustration.
- **image_families** _(optional)_ - Filter search results by editorial vs creative images.
- **licensing_models** _(optional)_ - Filter search results by RightsManaged vs RightsReady vs RoyaltyFree.
- **orientations** _(optional)_ - Filter search results by landscape vs portrait vs square vs panoramic.
- **product_offerings** _(optional)_ - Filter search results by the user's download products (PremiumAccess vs EasyAccess vs EditorialSubscription).
- **refinements** _(optional)_ - Filter search results by refinement IDs returned by a previous search for the same searchphrase.
- **date_created_start** _(optional)_ - Return search results by create date starting with this datetime. Must be used in conjunction with date_created_end.
- **date_created_end** _(optional)_ - Return search results by create date ending with this datetime. Must be used in conjunction with date_created_start.
- **event_id** _(optional)_ - Return search results belonging to the specified Event ID.
- **keyword_ids** _(optional)_ - Return search results belonging to the specified comma-separated list of keyword IDs.
- **specific_persons** _(optional)_ - Return search results belonging to the specified comma-separated list of personality IDs.













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