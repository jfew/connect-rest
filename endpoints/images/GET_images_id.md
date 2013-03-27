# Image Resources

    GET images/:id

## Description
Returns the metadata for a given Image ID.

***

## Requires authentication
Via /token endpoint, passed in via digest authentication.

***

## Parameters
- **language** _(optional)_ — Language in which to return certain image metadata (e.g. keywords, restrictions). Default is en-us.

***

## Return format
A JSON array of image objects.

***

## Errors
All known errors cause the resource to return HTTP error code header together with a JSON array containing at least 'status' and 'error' keys describing the source of error.

- **400 Bad Request** - The request is malformed or syntactically incorrect.
- **401 Unauthorized** - The specified application and/or user credentials are not recognized.
- **404 Not Found** - The resource is not found (i.e. invalid Image ID).

***

## Example
**Request**

    https://connect.gettyimages.com/api/images/:id

**Return**
``` json

{
"CoordinationId": "string",
    "Images": [
      {
        "ApplicableProductOfferings": [],
        "Artist": "string",
        "ArtistTitle": "string",
        "AuthorizationConstraints": [],
        "Caption": "string",
        "City": "string",
        "CollectionId": "string",
        "CollectionName": "string",
        "ColorType": "string",
        "Copyright": "string",
        "Country": "string",
        "CreditLine": "string",
        "DateCreated": "datetime",
        "DateSubmitted": "datetime",
        "EditorialSegments": [
          "string"
        ],
        "EditorialSourceId": "string",
        "EditorialSourceName": "string",
        "EventId": int,
        "EventIds": [
          int
        ],
        "GraphicStyle": "string",
        "ImageFamily": "string",
        "ImageId": "string",
        "Keywords": [
          {
            "Id": "string",
            "Text": "string",
            "Type": "string"
          }
        ],
        "LicensingModel": "string",
        "QualityRank": int,
        "ReferralDestinations": [
          {
            "SiteName": "string",
            "Url": "string"
          }
        ],
        "ReleaseMessage": "string",
        "Restrictions": [
          "string"
        ],
        "SizesDownloadableImages": [],
        "StateProvince": "string",
        "Title": "string",
        "UrlComp": "string",
        "UrlPreview": "string",
        "UrlWatermarkComp": "string",
        "UrlWatermarkPreview": "string"
      }
    ]
}

```
