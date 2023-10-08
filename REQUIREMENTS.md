
# `invoke-uri` Requirements

## General

* **iwr-req-100**: The `invoke-uri` GitHub Action shall run within the GitHub Actions continuous integration ecosystem as a public composite action.
* **iwr-req-101**: The action shall strictly use the built-in shell features of GitHub Actions and shall not use a third-party runtime such as `node.js` or `python`. This is so that the dependency management and maintenance of the action can be kept at a minimum.
* **iwr-req-102**: The action shall support GitHub native runners with the following operating systems regardless of their language configuration: `windows-latest`, `ubuntu-latest` and `macOS-latest`.
* **iwr-req-103**: The action shall support self-hosted runners if they are running `Windows Server 2019 Standard`, or later.

## Inputs

### method

* **iwr-req-200**: The action shall take the input argument `method`, which should be any of the following values (case-sensitive): `DEFAULT`, `DELETE`, `GET`, `HEAD`, `MERGE`, `OPTIONS`, `PATCH`, `POST`, `PUT` or `TRACE`. 
* **iwr-req-201**: The `method` argument should be validated (including the case sensitivity), and if the validation fails then the action should fail and throw an error.
*  **iwr-req-202**: The `method` input argument is optional and if it is not supplied then the default value shall be `GET`.
* **iwr-req-203**: The `method` input argument should be hardened against injection-style attacks so that it is not possible to perform arbitrary console commands from arbitrary user input.

### uri

* **iwr-req-204**: The action shall take the input argument `uri`, which should be a valid resource URI.
* **iwr-req-205**: The `uri` argument should be validated: the  length of the `uri` should be less than or equal to 2048 characters, and the `uri` should start with a valid protocol (case-sensitive): `http` or `https`.
* **iwr-req-206**: The `uri` input argument should be hardened against injection-style attacks so that it is not possible to perform arbitrary console commands from arbitrary user input.

### content-type

* **iwr-req-207**: The action shall take the input argument `content-type`, which should be any valid content type i.e. `text/plain` or `text/plain; charset=iso-8859-5`.
* **iwr-req-208**: The `content-type` argument should be validated: the full length of `content-type` should be less than or equal to 256 characters.
* **iwr-req-209**: The `media-type` part of the `content-type` should be validated: it should be one of the following: `text/plain`, `application/octet-stream`, `text/css`, `text/csv`, `text/html`, `application/json`, `application/ld+json`, `text/javascript`, `application/pdf`, `application/xml` or `application/zip`.
* **iwr-req-210**: The `charset` part of the `content-type` should be validated: it should be excluded, or be a preceding space and then one of the following: `utf-8` or `iso-8859-5`.
* **iwr-req-211**: The `content-type` input argument is optional, and if it is not supplied then the default value shall be `application/json`, which is the default value of certain developer tools, such as Postman.
* **iwr-req-212**: The `content-type` input argument should be hardened against injection-style attacks so that it is not possible to perform arbitrary console commands from arbitrary user input.
