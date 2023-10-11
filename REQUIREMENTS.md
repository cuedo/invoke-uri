
# `invoke-uri` Requirements

## General

*  **iwr-req-100**: The `invoke-uri` GitHub Action shall run within the GitHub Actions continuous integration ecosystem as a public composite action.

*  **iwr-req-101**: The action shall strictly use the built-in shell features of GitHub Actions and shall not use a third-party runtime such as `node.js` or `python`. This is so that the dependency management and maintenance of the action can be kept at a minimum.

*  **iwr-req-102**: The action shall support GitHub native runners with the following operating systems regardless of their language configuration: `windows-latest`, `ubuntu-latest` and `macOS-latest`.

*  **iwr-req-103**: The action shall support self-hosted runners if they are running `Windows Server 2019 Standard`, or later.

* **iwr-req-104**: The action shall invoke a web request. The characteristics of the web request can be defined by supplying input arguments to the action. The behaviour of the web request shall act consistently according to the input arguments only, and shall not depend on the platform of the runner.

## Inputs

### method

*  **iwr-req-200**: The action shall take the input argument `method`, which should be any of the following values (case-sensitive): `DEFAULT`, `DELETE`, `GET`, `HEAD`, `MERGE`, `OPTIONS`, `PATCH`, `POST`, `PUT` or `TRACE`.

*  **iwr-req-201**: The `method` argument shall be validated (including the case sensitivity), and if the validation fails then the action should fail and throw an error.

*  **iwr-req-202**: The `method` input argument is optional and if it is not supplied then the default value shall be `GET`.

*  **iwr-req-203**: The `method` input argument shall be hardened against injection-style attacks so that it is not possible to perform arbitrary console commands from arbitrary user input.

### uri

*  **iwr-req-204**: The action shall take the input argument `uri`, which should be a valid resource URI. This shall be the `uri` for the web request.

*  **iwr-req-205**: The `uri` argument should be validated: the length of the `uri` should be less than or equal to 2047 characters, and the `uri` should start with a valid protocol (case-sensitive): `http` or `https`.

*  **iwr-req-206**: The `uri` input argument shall be hardened against injection-style attacks so that it is not possible to perform arbitrary console commands from arbitrary user input.

### content-type

*  **iwr-req-207**: The action shall take the input argument `content-type`, which should be any valid content type i.e. `text/plain` or `text/plain; charset=iso-8859-5`.

*  **iwr-req-208**: The `content-type` argument shall be validated: the full length of `content-type` should be less than or equal to 255 characters.

*  **iwr-req-209**: The `media-type` part of the `content-type` should be validated: it should be one of the following: `text/plain`, `application/octet-stream`, `text/css`, `text/csv`, `text/html`, `application/json`, `application/ld+json`, `text/javascript`, `application/pdf`, `application/xml` or `application/zip`.

*  **iwr-req-210**: The `charset` part of the `content-type` should be validated: it should be excluded, or be a preceding space and then one of the following: `utf-8` or `iso-8859-5`.

*  **iwr-req-211**: The `content-type` input argument is optional, and if it is not supplied then the default value shall be `application/json`, which is the default value of certain developer tools, such as Postman.

*  **iwr-req-212**: The `content-type` input argument shall be hardened against injection-style attacks so that it is not possible to perform arbitrary console commands from arbitrary user input.

### save

* **iwr-req-213**: The action shall take the input argument `save`, which should be a valid file name, either relative or absolute.

* **iwr-req-214**: The `save` argument shall be validated: the full length of `save` should be less than or equal to 255 characters. Since `save` can be a relative file path, the actual filename might be longer than this. We will not attempt to validate this scenario, but the documentation should contain a warning that long file paths do not behave consistently between every platform.

* **iwr-req-215**: The `save` input argument is optional, and if it is not supplied then the result of the web request is not saved to any file.

* **iwr-req-216**: The `save` input argument shall be hardened against injection-style attacks so that it is not possible to perform arbitrary console commands from arbitrary user input.

* **iwr-req-217**: To mitigate an attack using relative path mechanisms, the `save` input argument shall only write the output to a file that does not exist. If the file already exists, then an error shall be thrown and the file will not be overwritten.

### user-agent

* **iwr-req-218**: The action shall take the `user-agent` input argument, which shall be any valid user agent.

* **iwr-req-219**: The `user-agent` argument shall be validated: the full length of `user-agent` should be less than or equal to 255 characters.

* **iwr-req-220**: The `user-agent` input argument is optional, and if it is not supplied then it shall be `Mozilla/5.0 (compatible; invoke-uri/1.0 for GitHub Actions)`.

* **iwr-req-221**: The `user-agent` input argument shall be hardened against injection-style attacks so that it is not possible to perform arbitrary console commands from arbitrary user input.
