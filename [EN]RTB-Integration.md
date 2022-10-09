**SHAREit-Publisher RTB Integration**

Table of Content

1 Overview

2 Steps for Integration

3 Real Time Bid

​	3.1 Data Transmission

​	3.2 HTTP Request

​	3.3 HTTP Response

​	3.4 Display Volume and Cost Calculation

4 Real Time Bid RTB Interface Parameter

​	4.1 Bid Request

​		4.1.1 source object

​		4.1.2 regs object

​		4.1.3 imp object

​		4.1.4 metric object

​		4.1.5 banner object

​		4.1.6 format object

​		4.1.7 video object

​		4.1.8 audio object

​		4.1.9 native object

​		4.1.10 native request object

​		4.1.11 asset request object

​		4.1.12 title object

​		4.1.13 img object

​		4.1.14 data object

​		4.1.15 pmp object

​		4.1.16 deal object

​		4.1.17 site object

​		4.1.18 app object

​		4.1.19 publisher object

​		4.1.20 content object

​		4.1.21 producer object

​		4.1.22 device object

​		4.1.23 geo object

​		4.1.24 user object

​		4.1.25 data object

​		4.1.26 segment object

​		4.2 Bid Response

​		4.2.1 seatbid object

​		4.2.2 bid object

​		4.2.3 native ad response

​		4.2.4 asset response object

​		4.2.5 title object

​		4.2.6 Img object

​		4.2.7 data object

​		4.2.8 video object

​		4.2.9 link object

5 RTB Interface Enumerated Value List

​	5.1 IAB Category Enumerated Value

​	5.2 Banner Ad Type Enumerated Value

​	5.3 Creative Attribute Enumerated Value

​	5.4 Ad Position Enumerated Value

​	5.5 Expandable Direction Enumerated Value

​	5.6 API Frame Enumerated Value

​	5.7 Video Linearity Enumerated Value

​	5.8 Video Bid Response Protocol Enumerated Value

​	5.9 Video Placement Types Enumerated Value

​	5.10 Playback Methods Enumerated Value

​	5.11 Playback Cessation Modes Enumerated Value

​	5.12 Start Delay Enumerated Value

​	5.13 Production Quality Enumerated Value

​	5.14 Companion Types Enumerated Value

​	5.15 Content Delivery Methods Enumerated Value

​	5.16 Feed Types Enumerated Value

​	5.17 Volume Normalization Modes Enumerated Value

​	5.18 Content Context Enumerated Value

​	5.19 IQG Media Ratings Enumerated Value

​	5.20 Location Type Enumerated Value

​	5.21 Device Type Enumerated Value

​	5.22 Connection Type Enumerated Value

​	5.23 IP Location Services Enumerated Value

​	5.24 No-Bid Reason Codes Enumerated Value

​	5.25 Loss Reason Codes Enumerated Value

​	5.26 Data Asset Types Enumerated Value

RTB Request Example 

​	1a) native icon image request example 

​	1b) native large image request example

​	1c) native video image request example

​    1d) banner request example

​    1e) video request example

RTB Response Example

​	2a) native icon image response example 

​	2b) native large image response example

​	2c) native video image response example

​    2d) banner response example

​    2e) video response example



# 1 Overview

This document provides instructions for the integration of SHAREit Midas system with external Publisher system. It describes the requirements and steps needed to enable interface connection based on open RTB.

 

# 2 Steps for Integration

To enable Publisher to connect with Midas, the steps include:

* Sign contract: Mutual agreement contract between SHAREit and Publisher.
* Register Publisher account: Contact SHAREit Operations PIC to register Publisher account in Midas system in order to receive the token. Note: Currently Midas doesn't support auto-registration, and it is necessary to contact SHAREit and provide relevant information in order to complete the account registration. 
* Proceed to system integration set-up: Publisher needs to follow this document to build interface and set up integration. If there is any issue encountered during the process, Midas will provide Product and Tech PIC to support and solve the issue accordingly. 
* Test: After integration is set up, Publisher and Midas need to arrange testing for the integration and make adjustments when necessary.
* Live: After test completes, SHAREit PIC from business team will follow up with official launch of integrated online traffic and start to record cost.

 

# 3 Real Time Bid

## 3.1 Data Transmission

The connection between Publisher and Midas follows HTTP communication protocol, to send Bid Request via POST mode as the content for HTTP request, and use data in JSON format.

 

## 3.2 HTTP Request

HTTP POST mode is used to send Bid Request, instead of HTTP GET mode, as it enables more content to be attached and supports binary data better.

 

Request thread：

|Name|Value|Remark|
|:----|:----|:----|
|x-openrtb-version|2.5|open rtb version|

## 3.3 HTTP Response

If Midas is participating in bid / auction, HTTP response status code should be 200, which allows it to return to Bid Request. If not, HTTP response status code should be 204.

 

## 3.4 Display Volume and Cost Calculation

Display / Impression volume is based on the reported statistics via burl link, and is used for cost calculation. Publisher needs to ensure no repetitive reporting of each unique display, and all reported display volume is within the duration as defined by Midas to be counted as valid.

 

Midas defines the valid duration (in seconds) between the bid / auction and the actual display / impression using field ‘bidresponse.seatbid.bid.exp’.

 

# 4 Real Time Bid RTB Interface Parameter 

## 4.1 Bid Request

| **Parameter name** | **Type**     | **Required?** | **Description**                                                                                                                                                                                                                                                                                                 |
|:-------------------|:-------------|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                 | string       | Yes           | The only identification for Bid Request                                                                                                                                                                                                                                                                         |
| imp                | object array | Yes           | 1 request can include only 1 impression object at a time, which represents a specific ad display placement/position. Details can be found in **imp object** parameter definition below                                                                                                                          |
| site               | object       | Yes           | Site object info of Publisher, recommended to use only on site instead of website. Details can be found in **site object** parameter definition below                                                                                                                                                           |
| app                | object       | Yes           | App object info of Publisher, recommended to use only on app instead of website. Details can be found in **app object** parameter definition below                                                                                                                                                              |
| device             | object       | Yes           | Device info. Details can be found in **device object** parameter definition below                                                                                                                                                                                                                               |
| user               | object       | Yes           | Device user / Ad audience. Details can be found in **user object** parameter definition below                                                                                                                                                                                                                   |
| test               | integer      | No            | Indicator of test mode in which auctions are not billable,where 0 = live mode, 1 = test mode  ,default 0                                                                                                                                                                                                        |
| at                 | integer      | No            | Bid settlement auction type. Value of 1 means it follows First-price auction, while value of 2 means it follows Second-price plus auction, default 2                                                                                                                                                            |
| tmax               | integer      | No            | Maximum time in milliseconds the exchange allows for bids to be received including Internet latency to avoid timeout                                                                                                                                                                                            |
| wseat              | string array | No            | White list of buyer seats (e.g., advertisers, agencies) allowed to bid on this impression.                                                                                                                                                                                                                      |
| bseat              | string array | No            | Block list of buyer seats (e.g., advertisers, agencies) restricted from bidding on this impression.                                                                                                                                                                                                             |
| allimps            | integer      | No            | Flag to indicate if Exchange can verify that the impressions offered represent all of the impressions available in context(e.g., all on the web page, all video spots such as pre/mid/post roll) to support road-blocking. 0 = no or unknown, 1 = yes, the impressions offered represent all that are available |
| cur                | string array | No            | Array of allowed currencies for bids on this bid request using ISO-4217 alpha codes. Recommended only if the exchange accepts multiple currencies.                                                                                                                                                              |
| walng              | string array | No            | White list of languages for creatives using ISO-639-1-alpha-2.                                                                                                                                                                                                                                                  |
| bcat               | string array | No            | Blocked advertiser categories using the IAB content categories. Refer to List 5.1.                                                                                                                                                                                                                              |
| badv               | string array | No            | Domain name in blacklist                                                                                                                                                                                                                                                                                        |
| bapp               | string array | No            | App name in blacklist.On Android, these should be bundle or package names (e.g., com.foo.mygame). On iOS, these are numeric IDs.                                                                                                                                                                                |
| source             | object       | No            | A Sorce object that provides data about theinventory source. Details can be found in **source object** parameter definition below                                                                                                                                                                               |
| regs               | object       | No            | Any industry, legal, or governmental regulations in force                                                                                                                                                                                                                                                       |
| ext                | object       | No            | Placeholder for exchange-specific extensions to OpenRTB                                                                                                                                                                                                                                                         |

 

### 4.1.1 source object

| **Parameter name** | **Type**   | **Required?**         | **Description**                                                                                                       |
|:-------------------|:-----------|:----------------------|:----------------------------------------------------------------------------------------------------------------------|
| fd                 | integer    | Yes                   | Entity responsible for the final impression sale decision, where0 = exchange, 1 = upstream source                     |
| tid                | string     | Yes                   | Transaction ID that must be common across all participants in this bid request (e.g., potentially multiple exchanges) |
| pchain             | string     | Yes                   | Payment ID chain string containing embedded syntax described in the TAG Payment ID Protocol v1.0                      |
| ext                | object     | No                    | Placeholder for exchange-specific extensions to OpenRTB                                                               |

 

### 4.1.2 regs object

| **Parameter name** | **Type**   | **Required?**         | **Description**                                                                                                                                                  |
|:-------------------|:-----------|:----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| coppa              | integer    | Yes                   | Flag indicating if this request is subject to the COPPA regulations established by the USA FTC, where 0 = no, 1 = yes. Refer to Section 7.5 for more information |
| ext                | object     | No                    | Placeholder for exchange-specific extensions to OpenRTB                                                                                                          |

 

### 4.1.3 imp object

| **Parameter name**         | **Type**      | **Required?**               | **Description**                                                                                                                                                                                                              |
|:---------------------------|:--------------|:----------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                         | string        | Yes                         | The only identification in a Bid Request for the specific display traffic sold. 1 request can include only 1 display traffic at a time                                                                                       |
| metric                     | object array  | No                          | An array of Metric object. Details can be found in **metric object** parameter definition below                                                                                                                              |
| banner                     | object        | Yes for Banner traffic      | Refer to **banner object**                                                                                                                                                                                                   |
| video                      | object        | Yes for Video traffic       | Refer to **video object**                                                                                                                                                                                                    |
| audio                      | object        | Yes for Audio traffic       | Refer to **audio object**                                                                                                                                                                                                    |
| native                     | object        | Yes for Native traffic      | Refer to **native object** (Supports only Native ad placement)                                                                                                                                                               |
| pmp                        | object        | Yes for private marketplace | A Pmp object containing any privatemarketplace deals in effect for this impression.  Details can be found in **pmp object** parameter definition below                                                                       |
| displaymanager             | string        | No                          | Name of ad mediation partner, SDK technology, or player responsible for rendering ad (typically video or mobile). Used by some ad servers to customize ad code by partner. Recommended for video and/or apps                 |
| displaymanagerver          | string        | No                          | Version of ad mediation partner, SDK technology, or player responsible for rendering ad (typically video or mobile). Used by some ad servers to customize ad code by partner. Recommended for video and/or apps              |
| instl                      | integer       | No                          | 1 = the ad is interstitial or full screen, 0 = not interstitial                                                                                                                                                              |
| tagid                      | string        | No                          | Fixed identification of each specific ad display placement/position                                                                                                                                                          |
| bidfloor                   | float         | No                          | Minimum CPM bid price for this display traffic                                                                                                                                                                               |
| bidfloorcur                | string        | No                          | Bid price currency, currently it only supports USD                                                                                                                                                                           |
| clickbrowser               | integer       | No                          | Indicates the type of browser opened upon clicking the creative in an app, where 0 = embedded, 1 = native                                                                                                                    |
| secure                     | integer       | No                          | Parameter to indicate if Bid Request needs HTTPS encrypted info and markup to ensure data privacy.Value of 0 means it doesn't need. Value of 1 means it needs. If left blank, means unknown, i.e. it doesn't need encryption |
| iframebuster               | string array  | No                          | Array of exchange-specific names of supported iframe busters                                                                                                                                                                 |
| exp                        | integer       | No                          | Duration that may elapse between the auction and the actual display / impression.Unit is in seconds                                                                                                                          |
| ext                        | object        | No                          | Placeholder for exchange-specific extensions to OpenRTB                                                                                                                                                                      |

 

### 4.1.4 metric object
| **Parameter name** | **Type**      | **Required?** | **Description**                                                                                                                                                                             |
|:-------------------|:--------------|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| type               | string        | Yes           | Type of metric being presented using exchange curated string names which should be published to bidders a priori                                                                            |
| value              | float         | Yes           | Number representing the value of the metric. Probabilities must be in the range 0.0 – 1.0                                                                                                   |
| vendor             | string        | Yes           | Source of the value using exchange curated string names which should be published to bidders a priori. If the exchange itself is the source versus a third party, “EXCHANGE” is recommended |
| ext                | object        | No            | Placeholder for exchange-specific extensions to OpenRTB                                                                                                                                     |

 

### 4.1.5 banner object
| **Parameter name** | **Type**       | **Required?** | **Description**                                                                                                                                                                                                                                |
|:-------------------|:---------------|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| format             | object array   | 否             | Array of format objects (Section 3.2.10) representing the banner sizes permitted. If none are specified, then use of the h and w attributes is highly recommended. Refer to **format object**                                                  |
| w                  | integer        | Yes           | Exact width in device independent pixels (DIPS); If not specified wmin and wmax , this value refers to the required display width, otherwise refers to the desired width                                                                       |
| h                  | integer        | Yes           | Exact height in device independent pixels (DIPS); If not specified hmin and hmax , this value refers to the required display height, otherwise refers to the desired height                                                                    |
| wmax               | integer        | No            | Deprecated in favor of the format array. Maximum width in device independent pixels (DIPS)                                                                                                                                                     |
| hmax               | integer        | No            | Deprecated in favor of the format array. Maximum height in device independent pixels (DIPS)                                                                                                                                                    |
| wmin               | integer        | No            | Deprecated in favor of the format array. Minimum width in device independent pixels (DIPS)                                                                                                                                                     |
| hmin               | integer        | No            | Deprecated in favor of the format array. Minimum height in device independent pixels (DIPS)                                                                                                                                                    |
| btype              | integer array  | No            | Blocked banner ad types. Refer to List 5.2.                                                                                                                                                                                                    |
| battr              | integer array  | No            | Blocked creative attributes. Refer to List 5.3.                                                                                                                                                                                                |
| pos                | integer        | No            | Ad position on screen. Refer to List 5.4.                                                                                                                                                                                                      |
| mimes              | string array   | No            | Content MIME types supported. Popular MIME types may include "application/x-shockwave-flash", “image/jpg”, and “image/gif”。SHAREit support "image/jpg"，"image/png", and "image/gif"                                                            |
| topframe           | integer        | No            | Indicates if the banner is in the top frame as opposed to an iframe, where 0 = no, 1 = yes                                                                                                                                                     |
| expdir             | integer array  | No            | Directions in which the banner may expand. Refer to List 5.5                                                                                                                                                                                   |
| api                | integer array  | No            | List of supported API frameworks for this impression. Refer to List 5.6. If an API is not explicitly listed, it is assumed not to be supported                                                                                                 |
| id                 | string         | No            | Unique identifier for this banner object. Recommended when Banner objects are used with a Video object to represent an array of companion ads. Values usually start at 1 and increase with each object; should be unique within an impression. |
| vcm                | integer        | No            | Relevant only for Banner objects used with a Video object in an array of companion ads. Indicates the companion banner rendering mode relative to the associated video, where 0 = concurrent, 1 = end-card                                     |
| ext                | object         | No            | Placeholder for exchange-specific extensions to OpenRTB                                                                                                                                                                                        |

 

### 4.1.6 format object
| **Parameter name** | **Type**       | **Required?**   | **Description**                                                                                                                                                             |
|:-------------------|:---------------|:----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| w                  | integer        | Yes             | Exact width in device independent pixels (DIPS); If not specified wmin and wmax , this value refers to the required display width, otherwise refers to the desired width    |
| h                  | integer        | Yes             | Exact height in device independent pixels (DIPS); If not specified hmin and hmax , this value refers to the required display height, otherwise refers to the desired height |
| wratio             | integer        | No              | Relative width when expressing size as a ratio                                                                                                                              |
| hratio             | integer        | No              | Relative height when expressing size as a ratio                                                                                                                             |
| wmin               | integer        | No              | The minimum width in device independent pixels (DIPS) at which the ad will be displayed the size is expressed as a ratio                                                    |
| ext                | object         | No              | Placeholder for exchange-specific extensions to OpenRTB                                                                                                                     |

****

 

### 4.1.7 video object

| **Parameter name** | **Type**      | **Required?** | **Description**                                                                                                                                                                                                                                                                            |
|:-------------------|:--------------|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| mimes              | string array  | Yes           | Supported content mime-type. Currently it only supports ‘video/mp4’                                                                                                                                                                                                                        |
| minduration        | integer       | Yes           | Minimum video ad length. Unit is in seconds                                                                                                                                                                                                                                                |
| maxduration        | integer       | Yes           | Maximum video ad length. Unit is in seconds                                                                                                                                                                                                                                                |
| protocols          | integer array | Yes           | Applicable video protocol for Publisher in Bid Response.   Refer to List 5.8.                                                                                                                                                                                                              |
| protocol           | integer       | DEPRECATED    | Applicable video protocol for Publisher in Bid Response. Refer to List 5.8.                                                                                                                                                                                                                |
| w                  | integer       | Yes           | Width of the video player in device independent pixels (DIPS)                                                                                                                                                                                                                              |
| h                  | integer       | Yes           | Height of the video player in device independent pixels (DIPS)                                                                                                                                                                                                                             |
| startdelay         | integer       | No            | Indicates the start delay in seconds for pre-roll, mid-roll, or post-roll ad placements. Refer to List 5.12 for additional generic values                                                                                                                                                  |
| placement          | integer       | No            | Placement type for the impression. Refer to List 5.9                                                                                                                                                                                                                                       |
| linearity          | integer       | No            | Indicates if the impression must be linear, nonlinear, etc. If none specified, assume all are allowed. Refer to List 5.7                                                                                                                                                                   |
| skip               | integer       | No            | Indicates if the player will allow the video to be skipped, where 0 = no, 1 = yes. If a bidder sends markup/creative that is itself skippable, the Bid object should include the attr array with an element of 16 indicating skippable video. Refer to List 5.3                            |
| skipmin            | integer       | No            | Videos of total duration greater than this number of seconds can be skippable; only applicable if the ad is skippable                                                                                                                                                                      |
| skipafter          | integer       | No            | Number of seconds a video must play before skipping is enabled; only applicable if the ad is skippable                                                                                                                                                                                     |
| sequence           | integer       | No            | If multiple ad impressions are offered in the same bid request, the sequence number will allow for the coordinated delivery of multiple creatives                                                                                                                                          |
| battr              | integer array | No            | Blocked creative attributes. Refer to List 5.3                                                                                                                                                                                                                                             |
| maxextended        | integer       | No            | Maximum extended ad duration if extension is allowed. If blank or 0, extension is not allowed. If -1, extension is allowed, and there is no time limit imposed. If greater than 0, then the value represents the number of seconds of extended play supported beyond the maxduration value |
| minbitrate         | integer       | No            | Minimum bit rate in Kbps                                                                                                                                                                                                                                                                   |
| maxbitrate         | integer       | No            | Maximum bit rate in Kbps                                                                                                                                                                                                                                                                   |
| boxingallowed      | integer       | No            | Indicates if letter-boxing of 4:3 content into a 16:9 window is allowed, where 0 = no, 1 = yes                                                                                                                                                                                             |
| playbackmethod     | integer array | No            | Playback methods that may be in use. If none are specified, any method may be used. Refer to List 5.10                                                                                                                                                                                     |
| playbackend        | integer       | No            | The event that causes playback to end. Refer to List 5.11                                                                                                                                                                                                                                  |
| pos                | integer       | No            | Ad position on screen. Refer to List 5.4                                                                                                                                                                                                                                                   |
| delivery           | integer array | No            | Supported delivery methods (e.g., streaming, progressive). If none specified, assume all are supported. Refer to List 5.15                                                                                                                                                                 |
| companionad        | object array  | No            | Array of Banner objects if companion ads are available                                                                                                                                                                                                                                     |
| api                | integer array | No            | List of supported API frameworks for this impression. Refer to List 5.6. If an API is not explicitly listed, it is assumed not to be supported                                                                                                                                             |
| companiontype      | integer array | No            | Supported VAST companion ad types. Refer to List 5.14. Recommended if companion Banner objects are included via the companionad array                                                                                                                                                      |
| ext                | object        | No            | Placeholder for exchange-specific extensions to OpenRTB                                                                                                                                                                                                                                    |

 

### 4.1.8 audio object

| **Parameter name**  | **Type**       | **Required?** | **Description**                                                                                                                                                                                                                                                                                        |
|:--------------------|:---------------|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| mimes               | string array   | Yes           | Supported content mime-type. Currently it only supports “audio/ mp4”                                                                                                                                                                                                                                   |
| minduration         | integer        | Yes           | Minimum audio ad length. Unit is in seconds                                                                                                                                                                                                                                                            |
| maxduration         | integer        | Yes           | Maximum audio ad length. Unit is in seconds                                                                                                                                                                                                                                                            |
| protocols           | integer array  | Yes           | Applicable audio protocol for Publisher in Bid Response.   Refer to List 5.8.                                                                                                                                                                                                                          |
| protocol            | integer        | DEPRECATED    | Applicable audio protocol for Publisher in Bid Response. Refer to List 5.8.                                                                                                                                                                                                                            |
| startdelay          | integer        | No            | Indicates the start delay in seconds for pre-roll, mid-roll, or post-roll ad placements. Refer to List 5.12 for additional generic values                                                                                                                                                              |
| sequence            | integer        | No            | If multiple ad impressions are offered in the same bid request, the sequence number will allow for the coordinated delivery of multiple creatives                                                                                                                                                      |
| battr               | integer array  | No            | Blocked creative attributes. Refer to List 5.3                                                                                                                                                                                                                                                         |
| maxextended         | integer        | No            | Maximum extended ad duration if extension is allowed. If blank or 0, extension is not allowed. If -1, extension is allowed, and there is no time limit imposed. If greater than 0, then the value represents the number of seconds of extended play supported beyond the maxduration value             |
| minbitrate          | integer        | No            | Minimum bit rate in Kbps                                                                                                                                                                                                                                                                               |
| maxbitrate          | integer        | No            | Maximum bit rate in Kbps                                                                                                                                                                                                                                                                               |
| delivery            | integer array  | No            | Supported delivery methods (e.g., streaming, progressive). If none specified, assume all are supported. Refer to List 5.15                                                                                                                                                                             |
| companionad         | object array   | No            | Array of Banner objects if companion ads are available                                                                                                                                                                                                                                                 |
| api                 | integer array  | No            | List of supported API frameworks for this impression. Refer to List 5.6. If an API is not explicitly listed, it is assumed not to be supported                                                                                                                                                         |
| companiontype       | integer array  | No            | Supported DAAST companion ad types. Refer to List 5.14. Recommended if companion Banner objects are included via the companionad array                                                                                                                                                                 |
| maxseq              | integer        | No            | The maximum number of ads that can be played in an ad pod                                                                                                                                                                                                                                              |
| feed                | integer        | No            | Type of audio feed. Refer to List 5.16                                                                                                                                                                                                                                                                 |
| stitched            | integer        | No            | Indicates if the ad is stitched with audio content or delivered independently, where 0 = no, 1 = yes                                                                                                                                                                                                   |
| nvol                | integer        | No            | Volume normalization mode. Refer to List 5.17                                                                                                                                                                                                                                                          |
| ext                 | object         | No            | Placeholder for exchange-specific extensions to OpenRTB                                                                                                                                                                                                                                                |

 

### 4.1.9 native object

| **Parameter name**  | **Type**      | **Required?** | **Description**                                                                                                                                                                                              |
|:--------------------|:--------------|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| request             | string        | Yes           | Request must follow Native ad specification. Refer to **native request object** for details                                                                                                                  |
| ver                 | string        | Yes           | Use Dynamic Native Ads API version, default version is 1.2                                                                                                                                                   |
| api                 | integer array | No            | Supported API frame of the display. Section **5.6 API frame** is the reference of its enumerated values. Default setting of this parameter is that it doesn't support any enumerated value, unless specified |
| battr               | integer array | No            | Restrictions of material attributes. Section **5.3 Creative attribute list** is the reference of its enumerated values                                                                                       |
| ext                 | object        | No            | Placeholder for exchange-specific extensions to OpenRTB                                                                                                                                                      |

 

### 4.1.10 native request object

| **Parameter name** | **Type**     | **Required?** | **Description**                                                                                                                                                  |
|:-------------------|:-------------|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| assets             | object array | Yes           | Use **asset request object** to show the requirement of Native ad for assets and other elements. All assets and other elements should follow this request object |
| ver                | string       | Yes           | Native Markup version, default version is 1.2                                                                                                                    |

****

 

### 4.1.11 asset request object 

| **Parameter name** | **Type** | **Required?** | **Description**                                                                                                                                            |
|:-------------------|:---------|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                 | integer  | Yes           | The only identification ID of the object                                                                                                                   |
| required           | integer  | Yes           | Indicate if the asset object is a must-have for client (bidder) in order to get a bid accepted. Value of 1 means yes. Value of 0 means it is not necessary |
| title              | object   | No            | Title object for title assets. Refer to **title object**                                                                                                   |
| img                | object   | No            | Image object for image assets. Refer to **img object**                                                                                                     |
| video              | object   | No            | Video object for video assets. Refer to **video object**                                                                                                   |
| data               | object   | No            | Data object for data assets, eg. brand, description, rating, pricing etc.Refer to **data object**                                                          |

****

 

### 4.1.6 title object 

| **Parameter name** | **Type** | **Required?** | **Description**                                                               |
|:-------------------|:---------|:--------------|:------------------------------------------------------------------------------|
| len                | integer  | Yes           | Maximum title text length. Recommended text length is 25, 90, 140 characters  |

****

 

### 4.1.13 img object 

| **Parameter name** | **Type**     | **Required?** | **Description**                                                                    |
|:-------------------|:-------------|:--------------|:-----------------------------------------------------------------------------------|
| type               | integer      | Yes           | Indicate the specific type of image. Icon image: Value = 1 Large image: Value = 3  |
| w                  | integer      | No            | Image width                                                                        |
| wmin               | integer      | Yes           | Minimum image width. Unit is in pixels                                             |
| h                  | integer      | No            | Image height / length                                                              |
| hmin               | integer      | Yes           | Minimum image height / length. Unit is in pixels                                   |
| mimes              | string array | No            | Supported image mime-type, including but not limited to ‘image/jpg’and ‘image/gif’ |

****

 

### 4.1.14 video object 

| **Parameter name** | **Type**      | **Required?** | **Description**                                                           |
|:-------------------|:--------------|:--------------|:--------------------------------------------------------------------------|
| mimes              | string array  | Yes           | Supported content mime-type. Currently it only supports ‘video/mp4’       |
| minduration        | integer       | Yes           | Minimum video ad length. Unit is in seconds                               |
| maxduration        | integer       | Yes           | Maximum video ad length. Unit is in seconds                               |
| protocols          | integer array | Yes           | Applicable video protocol for Publisher in Bid Response.Refer to List 5.8 |

****

 

### 4.1.15 data object 

| **Parameter name** | **Type**     | **Required?** | **Description**                                                                                                                                |
|:-------------------|:-------------|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------|
| type               | string array | Yes           | Indicate data object type ID. Each data object has a specific type. Section **5.12 Data Asset Type** is the reference of its enumerated values |
| len                | integer      | Yes           | Maximum number of characters allowed                                                                                                           |

 

### 4.1.16 pmp object

| **Parameter name** | **Type**        | **Required?** | **Description**                                                                                                                                                                                |
|:-------------------|:----------------|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| private_auction    | integer         | No            | Indicator of auction eligibility to seats named in the Direct Deals object, where 0 = all bids are accepted, 1 = bids are restricted to the deals specified and the terms thereof. default 0   |
| deals              | object array    | No            | Array of Deal objects that convey the specific deals applicable to this impression. Refer to **deal object**                                                                                   |
| ext                | object          | No            | Placeholder for exchange-specific extensions to OpenRTB                                                                                                                                        |

 

### 4.1.17 deal object

| **Parameter name** | **Type**      | **Required?** | **Description**                                                                                                                                                                 |
|:-------------------|:--------------|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                 | string        | Yes           | A unique identifier for the direct deal                                                                                                                                         |
| bidfloor           | float         | No            | Minimum CPM bid price for this display traffic ，default 0                                                                                                                       |
| bidfloorcur        | string        | No            | Bid price currency, currently it only supports USD ,default "USD"                                                                                                               |
| at                 | integer       | Yes           | Optional override of the overall auction type of the bid request, where 1 = First Price, 2 = Second Price Plus, 3 = the value passed in bidfloor is the agreed upon deal price. |
| wseat              | string array  | No            | Whitelist of buyer seats (e.g., advertisers, agencies) allowed to bid on this deal.                                                                                             |
| wadomain           | string array  | No            | Array of advertiser domains (e.g., advertiser.com) allowed to bid on this deal                                                                                                  || ext                        | object        | No            | Placeholder for exchange-specific extensions to OpenRTB                                                                                                                                                                                    |
| ext                | object        | No            | Placeholder for exchange-specific extensions to OpenRTB                                                                                                                         |

 

### 4.1.18 site object

| **Parameter name** | **Type**        | **Required?** | **Description**                                                                                                   |
|:-------------------|:----------------|:--------------|:------------------------------------------------------------------------------------------------------------------|
| id                 | string          | Yes           | Exchange definition of Site ID                                                                                    |
| name               | string          | No            | Site name                                                                                                         |
| domain             | string          | No            | Domain of the site (e.g., “mysite.foo.com”)                                                                       |
| cat                | string array    | No            | Array of IAB content categories of the site. Refer to List 5.1                                                    |
| sectioncat         | string array    | No            | Array of IAB content categories that describe the currentsection of the site. Refer to List 5.1                   |
| pagecat            | string array    | No            | Array of IAB content categories that describe the current page or view of the site. Refer to List 5.1             |
| page               | string          | No            | URL of the page where the impression will be shown                                                                |
| ref                | string          | No            | Referrer URL that caused navigation to the current page                                                           |
| search             | string          | No            | Search string that caused navigation to the current page                                                          |
| mobile             | integer         | No            | Indicates if the site has been programmed to optimize layout when viewed on mobile devices, where 0 = no, 1 = yes |
| privacypolicy      | integer         | No            | Indicates if the site has a privacy policy, where 0 = no, 1 = yes                                                 |
| publisher          | object          | No            | Details about the Publisher of the site. Refer to **publisher object**                                            |
| content            | object          | No            | Details about the Content within the site. Refer to **content object**                                            |
| keywords           | string          | No            | Comma separated list of keywords about the site                                                                   |
| ext                | object          | No            | Placeholder for exchange-specific extensions to OpenRTB                                                           |

 

### 4.1.19 app object 

| **Parameter name** | **Type**       | **Required?** | **Description**                                                                                       |
|:-------------------|:---------------|:--------------|:------------------------------------------------------------------------------------------------------|
| id                 | string         | Yes           | Exchange  definition of App ID                                                                        |
| name               | string         | No            | App name                                                                                              |
| bundle             | string         | Yes           | App package name info                                                                                 |
| domain             | string         | No            | App domain name, eg. mygame.foo.com                                                                   |
| storeurl           | string         | No            | App store URL for an installed app; for IQG 2.1 compliance                                            |
| cat                | string array   | No            | App IAB category.Section **5.1 IAB category** is the reference of its enumerated values               |
| sectioncat         | string array   | No            | Array of IAB content categories that describe the currentsection of the site. Refer to List 5.1       |
| pagecat            | string array   | No            | Array of IAB content categories that describe the current page or view of the site. Refer to List 5.1 |
| ver                | string         | No            | App version                                                                                           |
| privacypolicy      | integer        | No            | Indicates if the app has a privacy policy, where 0 = no, 1 = yes                                      |
| publisher          | object         | No            | Details about the Publisher of the app. Refer to **publisher object**                                 |
| content            | object         | No            | Details about the Content within the app. Refer to **content object**                                 |
| keywords           | string         | No            | Comma separated list of keywords about the app                                                        |
| ext                | object         | No            | Placeholder for exchange-specific extensions to OpenRTB                                               |

 

### 4.1.20 publisher object 

| **Parameter name** | **Type**       | **Required?**   | **Description**                                                                         |
|:-------------------|:---------------|:----------------|:----------------------------------------------------------------------------------------|
| id                 | string         | Yes             | Publisher ID, to apply for token info                                                   |
| name               | string         | No              | Publisher name                                                                          |
| domain             | string         | No              | Publisher's highest domain name, eg. ‘publisher.com’                                    |
| cat                | string array   | No              | Array of IAB content categories that describe the publisher.Refer to List 5.1           |
| ext                | object         | No              | Placeholder for exchange-specific extensions to OpenRTB                                 |

****

 

### 4.1.21 content object

| **Parameter name**  | **Type**      | **Required?** | **Description**                                                                                                |
|:--------------------|:--------------|:--------------|:---------------------------------------------------------------------------------------------------------------|
| id                  | string        | No            | ID uniquely identifying the content                                                                            |
| episode             | integer       | No            | Episode number                                                                                                 |
| title               | string        | No            | Content title                                                                                                  |
| series              | string        | No            | Content series                                                                                                 |
| season              | string        | No            | Content season (e.g., “Season 3”)                                                                              |
| artist              | string        | No            | Artist credited with the content                                                                               |
| genre               | string        | No            | Genre that best describes the content (e.g., rock, pop, etc)                                                   |
| album               | string        | No            | Album to which the content belongs; typically for audio                                                        |
| isrc                | string        | No            | International Standard Recording Code conforming to ISO3901                                                    |
| producer            | object        | No            | Details about the content Producer. Refer to **producer object**                                               |
| url                 | string        | No            | URL of the content, for buy-side contextualization or review                                                   |                                        |
| cat                 | string array  | No            | Array of IAB content categories that describe the content producer. Refer to List 5.1                          |
| prodq               | integer       | No            | Production quality. Refer to List 5.13                                                                         |
| videoquality        | integer       | DEPRECATED    | Deprecated in favor of prodq. Video quality. Refer to List 5.13                                                |
| context             | integer       | No            | Type of content (game, video, text, etc.). Refer to List 5.18                                                  |
| contentrating       | string        | No            | Content rating (e.g., MPAA)                                                                                    |
| userrating          | string        | No            | User rating of the content (e.g., number of stars, likes, etc.)                                                |
| qagmediarating      | integer       | No            | Media rating per IQG guidelines. Refer to List 5.19                                                            |
| keywords            | string        | No            | Comma separated list of keywords describing the content                                                        |
| livestream          | integer       | No            | 0 = not live, 1 = content is live (e.g., stream, live blog)                                                    |
| sourcerelationship  | integer       | No            | 0 = indirect, 1 = direct                                                                                       |
| len                 | integer       | No            | Length of content in seconds; appropriate for video or audio                                                   |
| language            | string        | No            | Content language using ISO-639-1-alpha-2                                                                       | 
| embeddable          | integer       | No            | Indicator of whether or not the content is embeddable (e.g.,an embeddable video player), where 0 = no, 1 = yes |
| data                | object array  | No            | Additional content data.  Refer to **data object**                                                             |
| ext                 | object        | No            | Placeholder for exchange-specific extensions to OpenRTB                                                        |

****

 

### 4.1.22 producer object

| **Parameter name** | **Type**       | **Required?**   | **Description**                                                                        |
|:-------------------|:---------------|:----------------|:---------------------------------------------------------------------------------------|
| id                 | string         | Yes             | Content producer or originator ID                                                      |
| name               | string         | No              | Content producer or originator name (e.g., “Warner Bros”)                              |
| domain             | string         | No              | Highest level domain of the content producer (e.g., “producer.com”)                    |
| cat                | string array   | No              | Array of IAB content categories that describe the content producer. Refer to List 5.1. |
| ext                | object         | No              | Placeholder for exchange-specific extensions to OpenRTB                                |

****

 

### 4.1.23 device object 

| **Parameter name** | **Type**  | **Required?** | **Description**                                                                                                                                                  |
|:-------------------|:----------|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ua                 | string    | Yes           | User-Agent field in HTTP request thread of user device                                                                                                           |
| geo                | object    | Yes           | Current geographic info of user. Refer to **geo object**                                                                                                         |
| dnt                | integer   | Yes           | ‘Do Not Track’ identification set by browser in HTTP thread. Value of 0 means tracking is not restricted. Value of 1 means tracking is restricted / not allowed. |
| lmt                | integer   | Yes           | Indicate user's authorization for ad tracking. Value of 0 means tracking is not restricted. Value of 1 means tracking is restricted / not allowed.               |
| ip                 | string    | Yes           | ipv4 address of user's current network                                                                                                                           |
| ipv6               | string    | No            | ipv6 address of user's current network                                                                                                                           |
| devicetype         | integer   | No            | Device type. Section **5.21 Device type** is the reference of its enumerated values                                                                              |
| make               | string    | No            | Device manufacturer (eg. ‘Apple’)                                                                                                                                |
| model              | string    | No            | Device model (eg. ‘iPhone’)                                                                                                                                      |
| os                 | string    | No            | Operation system (eg. Android, iOS)                                                                                                                              |
| osv                | string    | No            | Operation system version                                                                                                                                         |
| hwv                | integer   | No            | Hardware version of the device (e.g., “5S” for iPhone 5S)                                                                                                        |
| h                  | integer   | No            | Screen physical height / length.Unit is in pixels                                                                                                                |
| w                  | integer   | No            | Screen physical width.Unit is in pixels                                                                                                                          |
| ppi                | integer   | No            | Screen size.Unit is in pixel per inch                                                                                                                            |
| pxratio            | float     | No            | The ratio of physical pixels to device independent pixels                                                                                                        |
| js                 | integer   | No            | Indicate if js is supported. Value of 0 means not supported. Value of 1 means supported.                                                                         |
| geofetch           | integer   | No            | Indicates if the geolocation API will be available to JavaScript code running in the banner, where 0 = no, 1 = yes                                               |
| flashver           | string    | No            | Version of Flash supported by the browser                                                                                                                        |
| language           | string    | No            | Device language, following ISO-639-1-alpha-2. If unknown, put ‘unknown’                                                                                          |
| carrier            | string    | No            | Carrier or ISP (e.g., “VERIZON”) using exchange curated string names which should be published to bidders a priori.                                              |
| mccmnc             | string    | No            | Mobile network carrier                                                                                                                                           |
| connectiontype     | integer   | No            | Network connection mode. Section **5.8 Network Connection Mode** is the reference of its enumerated values                                                       |
| ifa                | string    | No            | Identification used by client.Andorid: gaid, iOS: idfa                                                                                                           |
| didsha1            | string    | No            | Hardware device ID (eg. IMEI), via SHA1 hash                                                                                                                     |
| didmd5             | string    | No            | Hardware device ID (eg. IMEI), via MD5 hash                                                                                                                      |
| dpidsha1           | string    | No            | Platform device ID (eg. Android ID), via SHA1 hash                                                                                                               |
| dpidmd5            | string    | No            | Platform device ID (eg. Android ID), via MD5 hash                                                                                                                |
| macsha1            | string    | No            | Device MAC address, via SHA1 hash                                                                                                                                |
| macmd5             | string    | No            | Device MAC address, via MD5 hash                                                                                                                                 |
| ext                | object    | No            | Placeholder for exchange-specific extensions to OpenRTB                                                                                                          |

 

### 4.1.13 geo object 

| **Parameter name** | **Type**   | **Required?** | **Description**                                                                                                                                                                                              |
|:-------------------|:-----------|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| lat                | float      | No            | Latitude info, data range is (-90.0,+90.0). Negative value means South                                                                                                                                       |
| lon                | float      | No            | Longitude info, data range is (-180.0,+180.0). Negative value means West.                                                                                                                                    |
| type               | integer    | No            | Source type of geo info. Value of 1 means by GPS/Location service. Value of 2 means by IP address. Value of 3 means provided by user.Section **5.13 Location Type**is the reference of its enumerated values |
| accuracy           | integer    | No            | Accuracy in meters. When latitude/longitude info is obtained by GPS/Location service, this field is reported.                                                                                                |
| lastfix            | integer    | No            | Number of seconds since this geolocation fix was established. Note that devices may cache location data across multiple fetches. Ideally, this value should be from the time the actual fix was taken        |
| ipservice          | integer    | No            | IP address provider, applicable for type = 2.Section **5.14 IP Location Type **is the reference of its enumerated values                                                                                     |
| country            | string     | No            | Country code following ISO-3166-1-alpha-3                                                                                                                                                                    |
| region             | string     | No            | Region code following ISO-3166-2.If country is USA, 2-letter state code is used                                                                                                                              |
| regionfips104      | string     | No            | Region of a country using FIPS 10-4 notation. While OpenRTB supports this attribute, it has been withdrawn by NIST in 2008                                                                                   |
| metro              | string     | N0            | Google metro code; similar to but not exactly Nielsen DMAs. See Appendix A for a link to the codes                                                                                                           |
| city               | string     | No            | City code following UN/LOCODE                                                                                                                                                                                |
| zip                | string     | No            | Postal code                                                                                                                                                                                                  |
| utcoffset          | integer    | No            | Local time difference from UTC time, +/- in minutes                                                                                                                                                          |
| ext                | object     | No            | Placeholder for exchange-specific extensions to OpenRTB                                                                                                                                                      |

 

### 4.1.14 user object 

| **Parameter name** | **Type**     | **Required?** | **Description**                                                             |
|:-------------------|:-------------|:--------------|:----------------------------------------------------------------------------|
| id                 | string       | Yes           | User ID                                                                     |
| buyeruid           | string       | No            | User ID defined by buyer                                                    |
| gender             | string       | No            | Gender. Value of M means male, F means female, 0 means other gender.        |
| geo                | object       | No            | User geo info                                                               |
| yob                | integer      | No            | Year of birth, 4-digit number.                                              |
| keywords           | string       | No            | Keywords list of user's interests / intentions list, separated by comma (,) |
| customdata         | string       | No            | Customized data                                                             |
| data               | object array | No            | Extra user data. Each data object represents a different data source        |
| ext                | object       | No            | Placeholder for exchange-specific extensions to OpenRTB                     |

 

### 4.1.15 data object 

| **Parameter name** | **Type**     | **Required?** | **Description**                                                             |
|:-------------------|:-------------|:--------------|:----------------------------------------------------------------------------|
| id                 | string       | No            | ID of data provider                                                         |
| name               | string       | No            | Name of data provider                                                       |
| segment            | object array | No            | Data segment that includes the actual data info.Refer to **segment object** |
| ext                | object       | No            | Placeholder for exchange-specific extensions to OpenRTB                     |

****

 

### 4.1.16 segment object 

| **Parameter name** | **Type**     | **Required?** | **Description**                                         |
|:-------------------|:-------------|:--------------|:--------------------------------------------------------|
| id                 | string       | No            | Segment ID defined by data provider                     |
| name               | string       | No            | Segment name defined by data provider                   |
| value              | string       | No            | Segment value                                           |
| ext                | object       | No            | Placeholder for exchange-specific extensions to OpenRTB |

****

 

## 4.2 Bid Response

| **Parameter name** | **Type**     | **Required?** | **Description**                                                                           |
|:-------------------|:-------------|:--------------|:------------------------------------------------------------------------------------------|
| id                 | string       | Yes           | Identification for Bid Request, i.e. request id included in Bid Request section above     |
| seatbid            | object array | Yes           | One set of SeatBid object. If a bid is offered, at least one SeatBid is filled in         |
| bidid              | string       | No            | Response ID generated for each bidder, assisting with logs or tracking transaction        |
| cur                | string       | No            | Unit of bid currency used, code following ISO-4217. If left blank, USD is used by default |
| customdata         | string       | No            | Optional feature to allow a bidder to set data in the exchange’s cookie.                  |
| nbr                | integer      | No            | Reason for not bidding. Refer to List 5.24                                                |
| ext                | object       | No            | Placeholder for bidder-specific extensions to OpenRTB                                     |

### 4.2.1 seatbid object

| **Parameter name** | **Type**      | **Required?** | **Description**                                                                                                                                                               |
|:-------------------|:--------------|:--------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| bid                | object array  | Yes           | Array that includes at least 1 bid object. Each object is related to 1 display / impression                                                                                   |
| seat               | string        | No            | Seat identification that represents the client (bidder, eg. advertiser, agency) on whose behalf this bid is made                                                              |
| group              | interger      | No            | Indicate if all bids can win or fail at the same time. Default value is 0, meaning independent bid is allowed. Value of 1 means a group of bids win or fail at the same time. |
| ext                | object        | No            | Placeholder for bidder-specific extensions to OpenRTB                                                                                                                         |

 

### 4.2.2 bid object

Each bid object must have a corresponding imp id, indicating the bid is offered for the specific impression.

| **Parameter name**   | **Type**      | **Required?**       | **Description**                                                                                                                                                                                                                             |
|:---------------------|:--------------|:--------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                   | string        | Yes                 | Bid ID generated for each bidder, used for recording logs or tracking acitivity                                                                                                                                                             |
| impid                | string        | Yes                 | ID of imp object related to a Bid request                                                                                                                                                                                                   |
| price                | float         | Yes                 | CPM price for each display                                                                                                                                                                                                                  |
| nurl                 | string        | No                  | Nurl link for notification when a bid wins, and will then be used by transaction platform                                                                                                                                                   |
| burl                 | string        | No                  | Billing notice URL called by the exchange when a winning bid becomes billable based on exchange-specific business policy (e.g.,typically delivered, viewed, etc.).Substitution macros ${AUCTION_PRICE} may be included                      |
| lurl                 | string        | No                  | Loss notice URL called by the exchange when a bid is known to have been loss                                                                                                                                                                |
| adm                  | string        | Yes                 | Convey ad content.Native ad uses adm field to return ad content. Refer to **native ad response** below for more detailsVideo ad uses adm field to return ad content in vast format. Refer to **vast video response** below for more details |
| adid                 | string        | No                  | Preloaded ad ID that can be used when a bid offer wins                                                                                                                                                                                      |
| adomain              | string array  | No                  | Domain name of client, used for filtering check                                                                                                                                                                                             |
| bundle               | string        | Yes for install ads | App package name, eg. Android package name: com.foo.mygame, iOS package name: id907394059                                                                                                                                                   |
| iurl                 | string        | No                  | Image link to indicate ad campaign content, used for quality or security tracking                                                                                                                                                           |
| cid                  | string        | No                  | Campaign ID, to assist with ad QC. Each cid has one set of creatives, which is the creatives represented by iurl                                                                                                                            |
| crid                 | string        | No                  | ID of a set of creatives, to assist with ad QC                                                                                                                                                                                              |
| cat                  | string array  | No                  | IAB category of creative.Section **5.1 IAB category** is the reference of its enumerated values                                                                                                                                             |
| attr                 | integer array | No                  | Attribute array to describe creative.Section **5.3 Creative attribute list** is the reference of its enumerated values                                                                                                                      |
| api                  | integer       | No                  | Supported API frame of the display. Section **5.6 API frame** is the reference of its enumerated values                                                                                                                                     |
| protocol             | integer       | No                  | Supported video Bid Response protocol. Section **5.8 Video bid response protocol** is the reference of its enumerated values                                                                                                                |
| qagmediarating       | integer       | No                  | Indicate rating of creative content following IQG standard.Section **5.9 IQG media rating** is the reference of its enumerated values                                                                                                       |
| language             | string        | No                  | Language of the creative using ISO-639-1-alpha-2                                                                                                                                                                                            |
| dealid               | string        | No                  | Refer to deal.id****from the bid request if this bid pertains to a private marketplace direct deal                                                                                                                                          |
| w                    | integer       | No                  | Creative width. Unit is in pixels                                                                                                                                                                                                           |
| h                    | integer       | No                  | Creative height. Unit is in pixels                                                                                                                                                                                                          |
| wratio               | integer       | No                  | Relative width of the creative when expressing size as a ratio. Required for Flex Ads                                                                                                                                                       |
| hratio               | integer       | No                  | Relative height of the creative when expressing size as a ratio. Required for Flex Ads                                                                                                                                                      |
| exp                  | integer       | No                  | Duration that the bidder is willing to wait between the auction and the actual display / impression.Unit is in seconds, with default value of 3600                                                                                          |
| ext                  | object        | No                  | Placeholder for bidder-specific extensions to OpenRTB                                                                                                                                                                                       |

 

### 4.2.3 native ad response

Native ad response content is saved in **adm** field, with the content including 1 **native object**. Native format supports native version 1.2 protocol.

 

Native object has following attributes:

| **Parameter name** | **Type**         | **Required?** | **Description**                                                                                                                                  |
|:-------------------|:-----------------|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| ver                | string           | No            | Native Markup version in use                                                                                                                     |
| assets             | array of objects | Yes           | List of native ad's assets.Refer to **asset response object**                                                                                    |
| link               | object           | Yes           | Destination link if the ad is clicked.Refer to **link object**                                                                                   |
| imptrackers        | array of string  | Yes           | Array of impression tracking URLs.When a display / impression happens, tracking URLs are reported and used as the reference for cost calculation |
| ext                | Object           | No            | Placeholder that may contain custom JSON                                                                                                         |

 

### 4.2.4 asset response object

Asset response object must strictly follow asset object in the Bid Request. Each object corresponds to an ID, which matches with the asset request object ID.

| **Parameter name** | **Type**   | **Required?** | **Description**                                                           |
|:-------------------|:-----------|:--------------|:--------------------------------------------------------------------------|
| id                 | int        | Yes           | Asset ID that matches with ID in Bid Request                              |
| required           | int        | No            | Set to 1 if asset is required (bidder requires it to be displayed)        |
| title              | object     | No            | Title object for title assets. Refer to **title object**                  |
| img                | object     | No            | Image object for image assets. Refer to **img object**                    |
| video              | object     | No            | Video object for video assets. Refer to **video object**                  |
| data               | object     | No            | Data object for data assets, eg. rating, pricing.Refer to **data object** |
| link               | object     | No            | Destination link if the ad is clicked.Refer to **link object**            |
| ext                | object     | No            | Placeholder that may contain custom JSON                                  |
 
### 
### 4.2.5 title object

| **Parameter name** | **Type** | **Required?** | **Description**                          |
|:-------------------|:---------|:--------------|:-----------------------------------------|
| text               | string   | Yes           | Title text                               |
| len                | integer  | No            | Length of title text                     |
| ext                | object   | No            | Placeholder that may contain custom JSON |

 

### 4.2.6 Img object

| **Parameter name** | **Type** | **Required?** | **Description**                                                                                                                   |
|:-------------------|:---------|:--------------|:----------------------------------------------------------------------------------------------------------------------------------|
| type               | integer  | No            | Required for assetsurl or dcourl responses, not required for embedded asset responsesIcon image: Value = 1 Large image: Value = 3 |
| url                | string   | Yes           | URL of the image asset                                                                                                            |
| w                  | integer  | Yes           | Image width in pixels                                                                                                             |
| h                  | integer  | Yes           | Image height in pixels                                                                                                            |
| ext                | object   | No            | Placeholder that may contain custom JSON                                                                                          |

 

### 4.2.7 data object

| **Parameter name** | **Type** | **Required?** | **Description**                                                                 |
|:-------------------|:---------|:--------------|:--------------------------------------------------------------------------------|
| type               | integer  | No            | Type ID of data element, must follow **5.26 Data Asset Type**if to be submitted |
| label              | string   | No            | Name of data element, must follow **5.26 Data Asset Type**if to be submitted    |
| value              | string   | Yes           | Formatted string of data, based on the requirement of each data type            |
| ext                | object   | No            | Placeholder that may contain custom JSON                                        |

 

### 4.2.8 video object

Video response object uses vasttag parameter for video content in vast format. 

Note: Video in native ad response is just one type of assets. Therefore, it doesn't support impression and click tracking that aims only at video. Instead, it can support tracking of the rate of progress when a video is being played.

| **Parameter name** | **Type** | **Required?** | **Description**                        |
|:-------------------|:---------|:--------------|:---------------------------------------|
| vasttag            | string   | Yes           | Indicate video content in vast format  |

 

### 4.2.9 link object

| **Parameter name** | **Type**         | **Required?** | **Description**                                                 |
|:-------------------|:-----------------|:--------------|:----------------------------------------------------------------|
| url                | string           | Yes           | Landing URL of the clickable link                               |
| clicktrackers      | array of strings | No            | List of third-party tracker URLs tobe fired on click of the URL |
| ext                | object           | No            | Placeholder that may contain custom JSON                        |

# 
# **5 RTB Interface Enumerated Value List**

## 5.1 IAB Category Enumerated Value

| **Value**          |**Description**|
|:-------------------|:----|
| **IAB1**           |**Arts & Entertainment**|
| IAB1-1             |Books & Literature|
| IAB1-2             |Celebrity Fan/Gossip|
| IAB1-3             |Fine Art|
| IAB1-4             |Humor|
| IAB1-5             |Movies|
| IAB1-6             |Music|
| IAB1-7             |Television|
| IAB2               |**Automotive**|
| IAB2-1             |Auto Parts|
| **IAB2-2**         |Auto Repair|
| IAB2-3             |Buying/Selling Cars|
| IAB2-4             |Car Culture|
| IAB2-5             |Certified Pre-Owned|
| IAB2-6             |Convertible|
| IAB2-7             |Coupe|
| IAB2-8             |Crossover|
| IAB2-9             |Diesel|
| IAB2-10            |Electric Vehicle|
| IAB2-11            |Hatchback|
| IAB2-12            |Hybrid|
| IAB2-13            |Luxury|
| IAB2-14            |Minivan|
| IAB2-15            |Motorcycles|
| IAB2-16            |Off-Road Vehicles|
| IAB2-17            |Performance Vehicles|
| IAB2-18            |Pickup|
| IAB2-19            |Road-Side Assistance|
| IAB2-20            |Sedan|
| IAB2-21            |Trucks & Accessories|
| IAB2-22            |Vintage Cars|
| IAB2-23            |Wagon|
| **IAB3**           |**Business**|
| IAB3-1             |Advertising|
| IAB3-2             |Agriculture|
| IAB3-3             |Biotech/Biomedical|
| IAB3-4             |Business Software|
| IAB3-5             |Construction|
| IAB3-6             |Forestry|
| IAB3-7             |Government|
| IAB3-8             |Green Solutions|
| IAB3-9             |Human Resources|
| IAB3-10            |Logistics|
| IAB3-11            |Marketing|
| IAB3-12            |Metals|
| **IAB4**           |**Careers**|
| IAB4-1             |Career Planning|
| IAB4-2             |College|
| IAB4-3             |Financial Aid|
| IAB4-4             |Job Fairs|
| IAB4-5             |Job Search|
| IAB4-6             |Resume Writing/Advice|
| IAB4-7             |Nursing|
| IAB4-8             |Scholarships|
| IAB4-9             |Telecommuting|
| IAB4-10            |U.S. Military|
| IAB4-11            |Career Advice|
| **IAB5**           |**Education**|
| IAB5-1             |7-12 Education|
| IAB5-2             |Adult Education|
| IAB5-3             |Art History|
| IAB5-4             |College Administration|
| IAB5-5             |College Life|
| IAB5-6             |Distance Learning|
| IAB5-7             |English as a 2nd Language|
| IAB5-8             |Language Learning|
| IAB5-9             |Graduate School|
| IAB5-10            |Homeschooling|
| IAB5-11            |Homework/Study Tips|
| IAB5-12            |K-6 Educators|
| IAB5-13            |Private School|
| IAB5-14            |Special Education|
| IAB5-15            |Studying Business|
| **IAB6**           |**Family & Parenting**|
| IAB6-1             |Adoption|
| IAB6-2             |Babies & Toddlers|
| IAB6-3             |Daycare/Pre School|
| IAB6-4             |Family Internet|
| IAB6-5             |Parenting - K-6 Kids|
| IAB6-6             |Parenting teens|
| IAB6-7             |Pregnancy|
| IAB6-8             |Special Needs Kids|
| IAB6-9             |Eldercare|
| **IAB7**           |**Health & Fitness**|
| IAB7-1             |Exercise|
| IAB7-2             |ADD|
| IAB7-3             |AIDS/HIV|
| IAB7-4             |Allergies|
| IAB7-5             |Alternative Medicine|
| IAB7-6             |Arthritis|
| IAB7-7             |Asthma|
| IAB7-8             |Autism/PDD|
| IAB7-9             |Bipolar Disorder|
| IAB7-10            |Brain Tumor|
| IAB7-11            |Cancer|
| IAB7-12            |Cholesterol|
| IAB7-13            |Chronic Fatigue Syndrome|
| IAB7-14            |Chronic Pain|
| IAB7-15            |Cold & Flu|
| IAB7-16            |Deafness|
| IAB7-17            |Dental Care|
| IAB7-18            |Depression|
| IAB7-19            |Dermatology|
| IAB7-20            |Diabetes|
| IAB7-21            |Epilepsy|
| IAB7-22            |GERD/Acid Reflux|
| IAB7-23            |Headaches/Migraines|
| IAB7-24            |Heart Disease|
| IAB7-25            |Herbs for Health|
| IAB7-26            |Holistic Healing|
| IAB7-27            |IBS/Crohn’s Disease|
| IAB7-28            |Incest/Abuse Support|
| IAB7-29            |Incontinence|
| IAB7-30            |Infertility|
| IAB7-31            |Men’s Health|
| IAB7-32            |Nutrition|
| IAB7-33            |Orthopedics|
| IAB7-34            |Panic/Anxiety Disorders|
| IAB7-35            |Pediatrics|
| IAB7-36            |Physical Therapy|
| IAB7-37            |Psychology/Psychiatry|
| IAB7-38            |Senior Health|
| IAB7-39            |Sexuality|
| IAB7-40            |Sleep Disorders|
| IAB7-41            |Smoking Cessation|
| IAB7-42            |Substance Abuse|
| IAB7-43            |Thyroid Disease|
| IAB7-44            |Weight Loss|
| IAB7-45            |Women's Health|
| **IAB8**           |**Food & Drink**|
| IAB8-1             |American Cuisine|
| IAB8-2             |Barbecues & Grilling|
| IAB8-3             |Cajun/Creole|
| IAB8-4             |Chinese Cuisine|
| IAB8-5             |Cocktails/Beer|
| IAB8-6             |Coffee/Tea|
| IAB8-7             |Cuisine-Specific|
| IAB8-8             |Desserts & Baking|
| IAB8-9             |Dining Out|
| IAB8-10            |Food Allergies|
| IAB8-11            |French Cuisine|
| IAB8-12            |Health/Low-Fat Cooking|
| IAB8-13            |Italian Cuisine|
| IAB8-14            |Japanese Cuisine|
| IAB8-15            |Mexican Cuisine|
| IAB8-16            |Vegan|
| IAB8-17            |Vegetarian|
| IAB8-18            |Wine|
| **IAB9**           |**Hobbies & Interests**|
| IAB9-1             |Art/Technology|
| IAB9-2             |Arts & Crafts|
| IAB9-3             |Beadwork|
| IAB9-4             |Bird-Watching|
| IAB9-5             |Board Games/Puzzles|
| IAB9-6             |Candle & Soap Making|
| IAB9-7             |Card Games|
| IAB9-8             |Chess|
| IAB9-9             |Cigars|
| IAB9-10            |Collecting|
| IAB9-11            |Comic Books|
| IAB9-12            |Drawing/Sketching|
| IAB9-13            |Freelance Writing|
| IAB9-14            |Genealogy|
| IAB9-15            |Getting Published|
| IAB9-16            |Guitar|
| IAB9-17            |Home Recording|
| IAB9-18            |Investors & Patents|
| IAB9-19            |Jewelry Making|
| IAB9-20            |Magic & Illusion|
| IAB9-21            |Needlework|
| IAB9-22            |Painting|
| IAB9-23            |Photography|
| IAB9-24            |Radio|
| IAB9-25            |Roleplaying Games|
| IAB9-26            |Sci-Fi & Fantasy|
| IAB9-27            |Scrapbooking|
| IAB9-28            |Screenwriting|
| IAB9-29            |Stamps & Coins|
| IAB9-30            |Video & Computer Games|
| IAB9-31            |Woodworking|
| **IAB10**          |**Home & Garden**|
| IAB10-1            |Appliances|
| IAB10-2            |Entertaining|
| IAB10-3            |Environmental Safety|
| IAB10-4            |Gardening|
| IAB10-5            |Home Repair|
| IAB10-6            |Home Theater|
| IAB10-7            |Interior Decorating|
| IAB10-8            |Landscaping|
| IAB10-9            |Remodeling & Construction|
| **IAB11**          |**Law, Government, & Politics**|
| IAB11-1            |Immigration|
| IAB11-2            |Legal Issues|
| IAB11-3            |U.S. Government Resources|
| IAB11-4            |Politics|
| IAB11-5            |Commentary|
| **IAB12**          |**News**|
| IAB12-1            |International News|
| IAB12-2            |National News|
| IAB12-3            |Local News|
| **IAB13**          |**Personal Finance**|
| IAB13-1            |Beginning Investing|
| IAB13-2            |Credit/Debt & Loans|
| IAB13-3            |Financial News|
| IAB13-4            |Financial Planning|
| IAB13-5            |Hedge Fund|
| IAB13-6            |Insurance|
| IAB13-7            |Investing|
| IAB13-8            |Mutual Funds|
| IAB13-9            |Options|
| IAB13-10           |Retirement Planning|
| IAB13-11           |Stocks|
| IAB13-12           |Tax Planning|
| **IAB14**          |**Society**|
| IAB14-1            |Dating|
| IAB14-2            |Divorce Support|
| IAB14-3            |Gay Life|
| IAB14-4            |Marriage|
| IAB14-5            |Senior Living|
| IAB14-6            |Teens|
| IAB14-7            |Weddings|
| IAB14-8            |Ethnic Specific|
| **IAB15**          |**Science**|
| IAB15-1            |Astrology|
| IAB15-2            |Biology|
| IAB15-3            |Chemistry|
| IAB15-4            |Geology|
| IAB15-5            |Paranormal Phenomena|
| IAB15-6            |Physics|
| IAB15-7            |Space/Astronomy|
| IAB15-8            |Geography|
| IAB15-9            |Botany|
| IAB15-10           |Weather|
| **IAB16**          |**Pets**|
| IAB16-1            |Aquariums|
| IAB16-2            |Birds|
| IAB16-3            |Cats|
| IAB16-4            |Dogs|
| IAB16-5            |Large Animals|
| IAB16-6            |Reptiles|
| IAB16-7            |Veterinary Medicine|
| **IAB17**          |**Sports**|
| IAB17-1            |Auto Racing|
| IAB17-2            |Baseball|
| IAB17-3            |Bicycling|
| IAB17-4            |Bodybuilding|
| IAB17-5            |Boxing|
| IAB17-6            |Canoeing/Kayaking|
| IAB17-7            |Cheerleading|
| IAB17-8            |Climbing|
| IAB17-9            |Cricket|
| IAB17-10           |Figure Skating|
| IAB17-11           |Fly Fishing|
| IAB17-12           |Football|
| IAB17-13           |Freshwater Fishing|
| IAB17-14           |Game & Fish|
| IAB17-15           |Golf|
| IAB17-16           |Horse Racing|
| IAB17-17           |Horses|
| IAB17-18           |Hunting/Shooting|
| IAB17-19           |Inline Skating|
| IAB17-20           |Martial Arts|
| IAB17-21           |Mountain Biking|
| IAB17-22           |NASCAR Racing|
| IAB17-23           |Olympics|
| IAB17-24           |Paintball|
| IAB17-25           |Power & Motorcycles|
| IAB17-26           |Pro Basketball|
| IAB17-27           |Pro Ice Hockey|
| IAB17-28           |Rodeo|
| IAB17-29           |Rugby|
| IAB17-30           |Running/Jogging|
| IAB17-31           |Sailing|
| IAB17-32           |Saltwater Fishing|
| IAB17-33           |Scuba Diving|
| IAB17-34           |Skateboarding|
| IAB17-35           |Skiing|
| IAB17-36           |Snowboarding|
| IAB17-37           |Surfing/Body-Boarding|
| IAB17-38           |Swimming|
| IAB17-39           |Table Tennis/Ping-Pong|
| IAB17-40           |Tennis|
| IAB17-41           |Volleyball|
| IAB17-42           |Walking|
| IAB17-43           |Waterski/Wakeboard|
| IAB17-44           |World Soccer|
| **IAB18**          |**Style & Fashion**|
| IAB18-1            |Beauty|
| IAB18-2            |Body Art|
| IAB18-3            |Fashion|
| IAB18-4            |Jewelry|
| IAB18-5            |Clothing|
| IAB18-6            |Accessories|
| **IAB19**          |**Technology & Computing**|
| IAB19-1            |3-D Graphics|
| IAB19-2            |Animation|
| IAB19-3            |Antivirus Software|
| IAB19-4            |C/C++|
| IAB19-5            |Cameras & Camcorders|
| IAB19-6            |Cell Phones|
| IAB19-7            |Computer Certification|
| IAB19-8            |Computer Networking|
| IAB19-9            |Computer Peripherals|
| IAB19-10           |Computer Reviews|
| IAB19-11           |Data Centers|
| IAB19-12           |Databases|
| IAB19-13           |Desktop Publishing|
| IAB19-14           |Desktop Video|
| IAB19-15           |Email|
| IAB19-16           |Graphics Software|
| IAB19-17           |Home Video/DVD|
| IAB19-18           |Internet Technology|
| IAB19-19           |Java|
| IAB19-20           |JavaScript|
| IAB19-21           |Mac Support|
| IAB19-22           |MP3/MIDI|
| IAB19-23           |Net Conferencing|
| IAB19-24           |Net for Beginners|
| IAB19-25           |Network Security|
| IAB19-26           |Palmtops/PDAs|
| IAB19-27           |PC Support|
| IAB19-28           |Portable|
| IAB19-29           |Entertainment|
| IAB19-30           |Shareware/Freeware|
| IAB19-31           |Unix|
| IAB19-32           |Visual Basic|
| IAB19-33           |Web Clip Art|
| IAB19-34           |Web Design/HTML|
| IAB19-35           |Web Search|
| IAB19-36           |Windows|
| **IAB20**          |**Travel**|
| IAB20-1            |Adventure Travel|
| IAB20-2            |Africa|
| IAB20-3            |Air Travel|
| IAB20-4            |Australia & New Zealand|
| IAB20-5            |Bed & Breakfasts|
| IAB20-6            |Budget Travel|
| IAB20-7            |Business Travel|
| IAB20-8            |By US Locale|
| IAB20-9            |Camping|
| IAB20-10           |Canada|
| IAB20-11           |Caribbean|
| IAB20-12           |Cruises|
| IAB20-13           |Eastern Europe|
| IAB20-14           |Europe|
| IAB20-15           |France|
| IAB20-16           |Greece|
| IAB20-17           |Honeymoons/Getaways|
| IAB20-18           |Hotels|
| IAB20-19           |Italy|
| IAB20-20           |Japan|
| IAB20-21           |Mexico & Central America|
| IAB20-22           |National Parks|
| IAB20-23           |South America|
| IAB20-24           |Spas|
| IAB20-25           |Theme Parks|
| IAB20-26           |Traveling with Kids|
| IAB20-27           |United Kingdom|
| **IAB21**          |**Real Estate**|
| IAB21-1            |Apartments|
| IAB21-2            |Architects|
| IAB21-3            |Buying/Selling Homes|
| **IAB22**          |**Shopping**|
| IAB22-1            |Contests & Freebies|
| IAB22-2            |Couponing|
| IAB22-3            |Comparison|
| IAB22-4            |Engines|
| **IAB23**          |**Religion & Spirituality**|
| IAB23-1            |Alternative Religions|
| IAB23-2            |Atheism/Agnosticism|
| IAB23-3            |Buddhism|
| IAB23-4            |Catholicism|
| IAB23-5            |Christianity|
| IAB23-6            |Hinduism|
| IAB23-7            |Islam|
| IAB23-8            |Judaism|
| IAB23-9            |Latter-Day Saints|
| IAB23-10           |Pagan/Wiccan|
| **IAB24****IAB25** |**Uncategorized****Non-Standard Content**|
| IAB25-1            |Unmoderated UGC|
| IAB25-2            |Extreme Graphic/Explicit Violence|
| IAB25-3            |Pornography|
| IAB25-4            |Profane Content|
| IAB25-5            |Hate Content|
| IAB25-6            |Under Construction|
| IAB25-7            |Incentivized|
| **IAB26**          |**Illegal Content**|
| IAB26-1            |Illegal Content|
| IAB26-2            |Warez|
| IAB26-3            |Spyware/Malware|
| IAB26-4            |Copyright Infringement|

 

## 5.2 Banner Ad Type Enumerated Value

|**Value**|**Description**|
|:----|:----|:----|:----|
| 1 |XHTML Text Ad (usually mobile)|
| 2 |XHTML Banner Ad. (usually mobile)|
| 3 |JavaScript Ad; must be valid XHTML (i.e., Script Tags Included)|
| 4 |iframe|

 

## 5.3 **Creative Attribute Enumerated Value**

|**Value**|**Description**|
|:----|:----|
|1|Audio Ad(Auto-Play)|
|2|Audio Ad(User Initiated)|
|3|Expandable(Automatic)|
|4|Expandable(User Initiated - Click)|
|5|Expandable(User Initiated - Rollover)|
|6|In-Banner Video Ad (Auto-Play)|
|7|In-Banner Video Ad (User Initiated)|
|8|Pop (e.g., Over, Under, or Upon Exit)|
|9|Provocative or Suggestive Imagery|
|10|Shaky, Flashing, Flickering, Extreme Animation, Smileys|
|11|Surveys|
|12|Text Only|
|13|User Interactive (e.g., Embedded Games)|
|14|Windows Dialog or Alert Style|
|15|Has Audio On/Off Button|
|16|Ad Provides Skip Button (e.g. VPAID-rendered skip button on pre-roll video)|
|17|Adobe Flash|

 

## 5.4 Ad Position Enumerated Value

| **Value** | **Description**                                                                       |
|:----------|:--------------------------------------------------------------------------------------|
| 0         | Unknown                                                                               |
| 1         | Above the Fold                                                                        |
| 2         | DEPRECATED - May or may not be initially visible depending on screen size/resolution. |
| 3         | Below the Fold                                                                        |
| 4         | Header                                                                                |
| 5         | Footer                                                                                |
| 6         | Sidebar                                                                               |
| 7         | Full Screen                                                                           |


 
## 5.5 Expandable Direction Enumerated Value

| **Value** | **Description** |
|:----------|:----------------|
| :------   | :------------   |
| 1         | Left            |
| 2         | Right           |
| 3         | Up              |
| 4         | Down            |
| 5         | Full Screen     |


 
## 5.6 API Frame Enumerated Value

|**Value**|**Description**|
|:----|:----|
|1|VPAID 1.0|
|2|VPAID 2.0|
|3|MRAID-1|
|4|ORMMA|
|5|MRAID-2|
|6|MRAID-3|

 
## 5.7 Video Linearity Enumerated Value

| **Value** | **Description**            |
|:----------|:---------------------------|
| 1         | Linear / In-Stream         |
| 2         | Non-Linear / Overlay       |

 
## 5.8 Video Bid Response Protocol Enumerated Value

| **Value** | **Description**   |
|:----------|:------------------|
| 1         | VAST 1.0          |
| 2         | VAST 2.0          |
| 3         | VAST 3.0          |
| 4         | VAST 1.0 Wrapper  |
| 5         | VAST 2.0 Wrapper  |
| 6         | VAST 3.0 Wrapper  |
| 7         | VAST 4.0          |
| 8         | VAST 4.0 Wrapper  |
| 9         | DAAST 1.0         |
| 10        | DAAST 1.0 Wrapper |

 
## 5.9 Video Placement Types Enumerated Value

| **Value** | **Description**                                                                                                                                                                                                                                                                             |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1         | In-Stream. Played before, during or after the streaming video content that the consumer has requested (e.g., Pre-roll, Mid-roll, Post-roll).                                                                                                                                                |
| 2         | In-Banner. Exists within a web banner that leverages the banner space to deliver a video experience as opposed to another static or rich media format. The format relies on the existence of display ad inventory on the page for its delivery.                                             |
| 3         | In-Article. Loads and plays dynamically between paragraphs of editorial content; existing as a standalone branded message.                                                                                                                                                                  |
| 4         | In-Feed. Found in content, social, or product feeds.                                                                                                                                                                                                                                        |
| 5         | Interstitial/Slider/Floating. Covers the entire or a portion of screen area, but is always on screen while displayed (i.e. cannot be scrolled out of view). Note that a full-screen interstitial (e.g., in mobile) can be distinguished from a floating/slider unit by the imp.instl field. |

 
## 5.10 Playback Methods Enumerated Value

| **Value** | **Description**                                          |
|:----------|:---------------------------------------------------------|
| 1         | Initiates on Page Load with Sound On                     |
| 2         | Initiates on Page Load with Sound Off by Default         |
| 3         | Initiates on Click with Sound On                         |
| 4         | Initiates on Mouse-Over with Sound On                    |
| 5         | Initiates on Entering Viewport with Sound On             |
| 6         | Initiates on Entering Viewport with Sound Off by Default |

 
## 5.11 Playback Cessation Modes Enumerated Value

| **Value** | **Description**                                                                                           |
|:----------|:----------------------------------------------------------------------------------------------------------|
| 1         | On Video Completion or when Terminated by User                                                            |
| 2         | On Leaving Viewport or when Terminated by User                                                            |
| 3         | On Leaving Viewport Continues as a Floating/Slider Unit until Video Completion or when Terminated by User |

 

## 5.12 Start Delay Enumerated Value

| **Value** | **Description**                                  |
|:----------|:-------------------------------------------------|
| >0        | Mid-Roll (value indicates start delay in second) |
| 0         | Pre-Roll                                         |
| -1        | Generic Mid-Roll                                 |
| -2        | Generic Post-Roll                                |

 

## 5.13 Production Quality Enumerated Value

| **Value** | **Description**                        |
|:----------|:---------------------------------------|
| 0         | Unknown                                |
| 1         | Professionally Produced                |
| 2         | Prosumer                               |
| 3         | User Generated (UGC)                   |

 

## 5.14 Companion Types Enumerated Value

| **Value** | **Description**                   |
|:----------|:----------------------------------|
| 1         | Static Resource                   |
| 2         | HTML Resource                     |
| 3         | iframe Resource                   |

 

## 5.15 Content Delivery Methods Enumerated Value

| **Value** | **Description**      |
|:----------|:---------------------|
| 1         | Streaming            |
| 2         | Progressive          |
| 3         | Download             |

 

## 5.16 Feed Types Enumerated Value

| **Value** | **Description**            |
|:----------|:---------------------------|
| 1         | Music Service              |
| 2         | FM/AM Broadcast            |
| 3         | Podcast                    |

 

## 5.17 Volume Normalization Modes Enumerated Value

| **Value** | **Description**                         |
|:----------|:----------------------------------------|
| 0         | None                                    |
| 1         | Ad Volume Average Normalized to Content |
| 2         | Ad Volume Peak Normalized to Content    |
| 3         | Ad Loudness Normalized to Content       |
| 4         | Custom Volume Normalization             |

 

## 5.18 Content Context Enumerated Value

| **Value** | **Description**                                                                    |
|:----------|:-----------------------------------------------------------------------------------|
| 1         | Video (i.e., video file or stream such as Internet TV broadcasts)                  |
| 2         | Game (i.e., an interactive software game)                                          |
| 3         | Music (i.e., audio file or stream such as Internet radio broadcasts)               |
| 4         | Application (i.e., an interactive software application)                            |
| 5         | Text (i.e., primarily textual document such as a web page, eBook, or news article) |
| 6         | Other (i.e., none of the other categories applies)                                 |
| 7         | Unknown                                                                            |

 

## 5.19 IQG Media Ratings Enumerated Value

| **Value** | **Description**  |
|:----------|:-----------------|
| 1         | All Audiences    |
| 2         | Everyone Over 12 |
| 3         | Mature Audiences |

 

## 5.20 Location Type Enumerated Value

| **Value** | **Description**                         |
|:----------|:----------------------------------------|
| 1         | GPS/Location Services                   |
| 2         | IP Address                              |
| 3         | User provided (e.g., registration data) |

 

## 5.21 Device Type Enumerated Value

| **Value** | **Description**                      |
|:----------|:-------------------------------------|
| 1         | Mobile/Tablet Version 2.0            |
| 2         | Personal Computer Version 2.0        |
| 3         | Connected TV Version 2.0             |
| 4         | Phone New for Version 2.2            |
| 5         | Tablet New for Version 2.2           |
| 6         | Connected Device New for Version 2.2 |
| 7         | Set Top Box New for Version 2.2      |

 

## 5.22 Connection Type Enumerated Value

| **Value** | **Description**                       |
|:----------|:--------------------------------------|
| 0         | Unknown                               |
| 1         | Ethernet                              |
| 2         | WIFI                                  |
| 3         | Cellular Network – Unknown Generation |
| 4         | Cellular Network – 2G                 |
| 5         | Cellular Network – 3G                 |
| 6         | Cellular Network – 4G                 |
| 7         | Cellular Network – 5G                 |

 

## 5.23 IP Location Services Enumerated Value

| **Value** | **Description**               |
|:----------|:------------------------------|
| 1         | ip2location                   |
| 2         | Neustar (Quova)               |
| 3         | MaxMind                       |
| 4         | NetAcuity (Digital Element)   |

 

## 5.24 No-Bid Reason Codes Enumerated Value

| **Value** | **Description**                 |
|:----------|:--------------------------------|
| 0         | Unknown Error                   |
| 1         | Technical Error                 |
| 2         | Invalid Request                 |
| 3         | Known Web Spider                |
| 4         | Suspected Non-Human Traffic     |
| 5         | Cloud, Data center, or Proxy IP |
| 6         | Unsupported Device              |
| 7         | Blocked Publisher or Site       |
| 8         | Unmatched User                  |
| 9         | Daily Reader Cap Met            |
| 10        | Daily Domain Cap Met            |

 

## 5.25 Loss Reason Codes Enumerated Value

| **Value** | **Description**                                                                        |
|:----------|:---------------------------------------------------------------------------------------|
| 0         | Bid Won                                                                                |
| 1         | Internal Error                                                                         |
| 2         | Impression Opportunity Expired                                                         |
| 3         | Invalid Bid Response                                                                   |
| 4         | Invalid Deal ID                                                                        |
| 5         | Invalid Auction ID                                                                     |
| 6         | Invalid (i.e., malformed) Advertiser Domain                                            |
| 7         | Missing Markup                                                                         |
| 8         | Missing Creative ID                                                                    |
| 9         | Missing Bid Price                                                                      |
| 10        | Missing Minimum Creative Approval Data                                                 |
| 100       | Bid was Below Auction Floor                                                            |
| 101       | Bid was Below Deal Floor                                                               |
| 102       | Lost to Higher Bid                                                                     |
| 103       | Lost to a Bid for a PMP Deal                                                           |
| 104       | Buyer Seat Blocked                                                                     |
| 200       | Creative Filtered - General; reason unknown.                                           |
| 201       | Creative Filtered - Pending processing by Exchange (e.g., approval, transcoding, etc.) |
| 202       | Creative Filtered - Disapproved by Exchange                                            |
| 203       | Creative Filtered - Size Not Allowed                                                   |
| 204       | Creative Filtered - Incorrect Creative Format                                          |
| 205       | Creative Filtered - Advertiser Exclusions                                              |
| 206       | Creative Filtered – App Bundle Exclusions                                              |
| 207       | Creative Filtered - Not Secure                                                         |
| 208       | Creative Filtered - Language Exclusions                                                |
| 209       | Creative Filtered - Category Exclusions                                                |
| 210       | Creative Filtered - Creative Attribute Exclusions                                      |
| 211       | Creative Filtered - Ad Type Exclusions                                                 |
| 212       | Creative Filtered - Animation Too Long                                                 |
| 213       | Creative Filtered - Not Allowed in PMP Deal                                            |
| >= 1000   | Exchange specific (should be communicated to bidders a priori)                         |

 

## 5.26 Data Asset Types Enumerated Value

| **Value**  | **Description**                                                                                                                                                       |
|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| sponsored  | Sponsored By message where response should contain the brand name of the sponsor.                                                                                     |
| desc       | Descriptive text associated with the product or service being advertised. Longer length of text in response may be truncated or ellipsed by the exchange.             |
| rating     | Rating of the product being offered to the user. For example an app’s rating in an app store from 0-5.                                                                |
| likes      | Number of social ratings or “likes” of the product being offered to the user.                                                                                         |
| downloads  | Number downloads/installs of this product                                                                                                                             |
| price      | Price for product / app / in-app purchase. Value should include currency symbol in localised format.                                                                  |
| saleprice  | Sale price that can be used together with price to indicate a discounted price compared to a regular price. Value should include currency symbol in localised format. |
| phone      | Phone number                                                                                                                                                          |
| address    | Address                                                                                                                                                               |
| desc2      | Additional descriptive text associated with the product or service being advertised                                                                                   |
| displayurl | Display URL for the text ad. To be used when sponsoring entity doesn’t own the content. IE sponsored by BRAND on SITE (where SITE is transmitted in this field).      |
| ctatext    | CTA description - descriptive text describing a ‘call to action’ button for the destination URL.                                                                      |

 

# RTB Request Example

## 1a) native icon image request example

```json
{
  "id":"123",
  "imp": [{
    "id":"1",
    "tagid":"2049",
    "bidfloor":0.01,
    "bidfloorcur":"USD",
    "native": {
      "request":"{\"assets\":[{\"required\":1,\"img\":{\"type\":1,\"wmin\":84,\"hmin\":84}}],\"ver\": \"1.2\"}",
      "ver": "1.2"
    },
    "instl":0
  }],
  "app": {
    "storeurl":"",
    "ver":"8888888",
    "publisher": {
      "id":"de30a0c4-ed1c-42bd-a5ff-af65852ef34a"
    }
  },
  "device": {
    "ip":"1.1.1.1",
    "geo": {
      "country":"IDN"
    }
  }
}
```
## 1b) native large image request example

```json
{
  "id":"123",
  "imp":[{
    "id":"1",
    "tagid":"2049",
    "bidfloor":0.01,
    "bidfloorcur":"USD",
    "native": {
      "request": "{\"assets\":[{\"required\":1,\"img\":{\"type\":3,\"wmin\":600,\"hmin\":314}}],\"ver\": \"1.2\"}",
       "ver":"1.2"
    },
    "instl":0
  }],
  "app":{
    "storeurl":"",
    "ver":"8888888",
    "publisher":{
      "id":"de30a0c4-ed1c-42bd-a5ff-af65852ef34a"
    }
  },
  "device":{
    "ip":"1.1.1.1",
    "geo":{
      "country":"IDN"
    }
  }
}
```
## 1c) native video request example

```json
{
  "id":"32f94228-52d3-4bce-be88-5dd1d799ae4f",
  "imp": [{
    "id":"1",
    "tagid":"2061",
    "bidfloor":1.00,
    "bidfloorcur":"USD",
    "secure":0,
    "native":{
      "request":"{\"assets\":[{\"id\":1,\"required\":1,\"title\":{\"len \":100}},{\"id\":2,\"required \":0,\"data \":{\"type \":2,\"len \":100}},{\"id\":3,\"required \":0,\"img \":{\"type \":3}},{\"id \":4,\"required \":1,\"img \":{\"type\":1}},{\"id \":5,\"required \":0,\"img\":{\"type \":1}},{\"id\":6,\"required\":0,\"data\":{\"type \":12,\"len \":100}},{\"id\":7,\"required\":1,\"video\":{\"mimes\":[\"video/mp4\"],\"maxduration\":30,\"protocols\":[3],\"w\":1280,\"h\":720,\"linearity\":1,\"skip\":0,\"battr\":[16],\"maxbitrate\":2000,\"delivery\":[2],\"companionad\":[{\"w\":1280,\"h\":720,\"id\":\"1\",\"btype\":[1,2,4],\"battr\":[16],\"pos\":7,\"mimes\":[\"application/javascript\"],\"ext\":{\"orientation\":1}}]}}], \"ver\": \"1.2\"}",
        "ver":"1.2"
    }
  }],
  
  "app": {
    "id":"100461",
    "ver":"4050618",
    "publisher": {
      "id":"bd8b25d0-413e-4886-9adf-6a796ff47740"
    }
  },
  "device": {
    "ip":"1.1.1.1",
    "geo": {
      "country":"IDN",
      "type":2
    },
    "devicetype":4,
    "make":"WIKO",
    "model":"samsung-sm-g900a",
    "os":"android",
    "osv":"5.1.1",
    "language":"en",
    "carrier":"310410",
    "connectiontype":7,
    "ifa":"5731b4c8-7cc1-4a09-bb77-24f237d93a66",
    "didsha1":"ecae9042f3e549a4fd1af27a1ed38b5f682fa3ca",
    "didmd5":"c98de3c3706ae57c89f97c0778c8121d",
    "dpidsha1":"a07713adea29cd23fd10a2e81a4fb07e23e00fb7",
    "dpidmd5":"af4935679d392191157f687f48907492"
  },
  "at":1,
  "tmax":2000
}
```

## 1d）banner request example
```json
{
    "id": "123",
    "imp": [{
        "id": "1",
        "tagid": "2051",
        "bidfloor": 0.00001,
        "bidfloorcur": "USD",
        "banner":{
            "w":320,
            "h":50,
            "mimes": ["image/png", "image/jpg", "image/gif"]
        },
        "instl": 0
    }],
 
    "app": {
        "storeurl": "",
        "ver": "8888888",
        "publisher": {
            "id": "5e33f618-42a0-47f0-b7b1-9ad9866f3b9a"
        }
    },
    "device": {
        "ip": "1.1.1.1",
        "geo": {
            "country": "IDN"
        },
        "connectiontype": 7
    }
}
```



# RTB Response Example

## 2a) native icon image response example

```json
{
  "id":"123",
  "bidid":"47b61fdb-0c63-46fc-9343-df78cd5b700f",
  "seatbid":[{
    "bid":[{
      "id":"47b61fdb-0c63-46fc-9343-df78cd5b700f",
      "impid":"1",
      "price":289,
      "burl": "http://midas-tracker-dev.hellay.net/win.fcg?viewid=e6d8578664e2f10e11afa9c2e16cb37680d4df1e94d245ba2d33780f1edaba4ac6aa12fb51d3bf16e4e45ea2f5d7f6001a07323bea0c8e8feabe0dc8d191ef8ab417be2d03b8f2f42b670a47da2e4cfc471bc12cab9b8b93ea9f6096bc3754a4504199138bfc3de2175b25964e6353ca9390f6b7d21d46562d114b3ce6b79aff194ecdf27e608df0042697e7b0649503d67118df10c3755021e9f0de8f7a9b81239631fcaec5085653cc924139de74a362dd9e496589f008a5fe08421489a154726e484f2a9ffd7974a17970b211becc8a6e0cbeb0da71a2ae9adeb03e38ccd710ae582d51af0d38435548613dd6ccc224e2043f773fb9d19f781248676bd6cfeb60aebed339572462c42954267f6d5674eb418481a076e1e93a80211802c27dbe661bc5261764e6ce987657027a6622954100b11934fd1e5b5034a26c4eef9d554705b9f2ac51c3f0bd4a70dec9eb1e3de6f8fefd4f565a4c11a76f3c0cdf2b039cde4bc985eb65e5f5d73ef36b82b0a67ac3031310b383067f90eb6a5ae7259c9888337e30b69a5c1f0c089e4014766a861d9e6f391a6659687391ba1c3f8b3e4c1335b8a729d305b73b985ebd4e063cf47ca2b38f3312ab92df818eaf56342bea6633b7e9d2ae195fbf5200646ea3b3afaf413a76f1c6785087c65feec214112cbc835df6f6fcab32fdc31d1288e01128279a527a8c9601e290cbf7a138230eee2eaf3023cb15&auction_price=${AUCTION_PRICE}&sid=__SID__",
      "adm":"{\"ver\":\"1.2\",\"assets\":[{\"img\":{\"type\":1,\"url\":\"http://static-dev.rqmob.com/test/sa/20210710/53da2d2e6b4f1482ecc5afd2c15bc824__FILE_CM____FILE_CM480_720____WEBP__.png\",\"w\":84,\"h\":84}}],\"link\":{\"url\":\"https://play.google.com/store/apps/details?id=com.janel.doctor.ear\&hl=en\",\"clicktrackers\":[\"http://midas-tracker-dev.hellay.net/clk.fcg?viewid=e6d8578664e2f10e11afa9c2e16cb37680d4df1e94d245ba2d33780f1edaba4ac6aa12fb51d3bf16e4e45ea2f5d7f6001a07323bea0c8e8feabe0dc8d191ef8ab417be2d03b8f2f42b670a47da2e4cfc471bc12cab9b8b93ea9f6096bc3754a4504199138bfc3de2175b25964e6353ca9390f6b7d21d46562d114b3ce6b79aff194ecdf27e608df0042697e7b0649503d67118df10c3755021e9f0de8f7a9b81239631fcaec5085653cc924139de74a362dd9e496589f008a5fe08421489a154726e484f2a9ffd7974a17970b211becc8a6e0cbeb0da71a2ae9adeb03e38ccd710ae582d51af0d38435548613dd6ccc224e2043f773fb9d19f781248676bd6cfeb60aebed339572462c42954267f6d5674eb418481a076e1e93a80211802c27dbe661bc5261764e6ce987657027a6622954100b11934fd1e5b5034a26c4eef9d554705b9f2ac51c3f0bd4a70dec9eb1e3de6f8fefd4f565a4c11a76f3c0cdf2b039cde4bc985eb65e5f5d73ef36b82b0a67ac3031310b383067f90eb6a5ae7259c9888337e30b69a5c1f0c089e4014766a861d9e6f391a6659687391ba1c3f8b3e4c1335b8a729d305b73b985ebd4e063cf47ca2b38f3312ab92df818eaf56342bea6633b7e9d2ae195fbf5200646ea3b3afaf413a76f1c6785087c65feec214112cbc835df6f6fcab32fdc31d1288e01128279a527a8c9601f19dd0f5a75a3f7f38f1\&auction_price=${AUCTION_PRICE}\&sid=__SID__\",\"http://midas-tracker-dev.hellay.net/cpi_clk.fcg?log=eyJldmVudF9uYW1lIjoiQURfQ3BpQ2xpY2siLCJyZXF1ZXN0X2lkIjoiNDdiNjFmZGItMGM2My00NmZjLTkzNDMtZGY3OGNkNWI3MDBmIiwic3ViX3BsYXRmb3JtIjoiY3BpIiwiY2hhbm5lbCI6Ik9NQ19TREsiLCJjbGllbnRfaXAiOiIxLjEuMS4xIiwic2NyZWVuX3NpemUiOiIweDAiLCJjb3VudHJ5IjoiaWQiLCJQYXJhbXMiOlt7ImNhbXBhaWduX2lkIjoyMjM4LCJwb3NfaWQiOiIyMDQ5IiwiYWRfaWQiOjEwMDc2NiwiY2FtcF9uYW1lIjoicGFubHVoLXNhbiIsImFkX3BhY2thZ2VfbmFtZSI6ImNvbS5qYW5lbC5kb2N0b3IuZWFyIiwiY2lkIjozODgwMywiYmlkX3ByaWNlIjoxMjMwMDAwMDAsImVjcG0iOjI4OTU1MzgwNCwiZHNwX25hbWUiOiJTaGFyZWl0IiwiYXR0cl9wbGF0Zm9ybSI6MiwiYWRzZXRfaWQiOjEzNTAsImFkX25hbWUiOiJTQU4tU0RLIiwiYWRzZXRfbmFtZSI6IlNBTi1TREsiLCJwaHlfcG9zIjoiMjA0OSJ9XSwibWlkYXNfdmVyc2lvbiI6IjIuMCJ9\&sid=__SID__\"]},\"imptrackers\":[\"http://midas-tracker-dev.hellay.net/imp.fcg?viewid=e6d8578664e2f10e11afa9c2e16cb37680d4df1e94d245ba2d33780f1edaba4ac6aa12fb51d3bf16e4e45ea2f5d7f6001a07323bea0c8e8feabe0dc8d191ef8ab417be2d03b8f2f42b670a47da2e4cfc471bc12cab9b8b93ea9f6096bc3754a4504199138bfc3de2175b25964e6353ca9390f6b7d21d46562d114b3ce6b79aff194ecdf27e608df0042697e7b0649503d67118df10c3755021e9f0de8f7a9b81239631fcaec5085653cc924139de74a362dd9e496589f008a5fe08421489a154726e484f2a9ffd7974a17970b211becc8a6e0cbeb0da71a2ae9adeb03e38ccd710ae582d51af0d38435548613dd6ccc224e2043f773fb9d19f781248676bd6cfeb60aebed339572462c42954267f6d5674eb418481a076e1e93a80211802c27dbe661bc5261764e6ce987657027a6622954100b11934fd1e5b5034a26c4eef9d554705b9f2ac51c3f0bd4a70dec9eb1e3de6f8fefd4f565a4c11a76f3c0cdf2b039cde4bc985eb65e5f5d73ef36b82b0a67ac3031310b383067f90eb6a5ae7259c9888337e30b69a5c1f0c089e4014766a861d9e6f391a6659687391ba1c3f8b3e4c1335b8a729d305b73b985ebd4e063cf47ca2b38f3312ab92df818eaf56342bea6633b7e9d2ae195fbf5200646ea3b3afaf413a76f1c6785087c65feec214112cbc835df6f6fcab32fdc31d1288e01128279a527a8c9601f698cae6a06433d213ad0e27e61ecbf359716f\&auction_price=${AUCTION_PRICE}\&sid=__SID__\",\"http://midas-tracker-dev.hellay.net/cpi_imp.fcg?log=eyJldmVudF9uYW1lIjoiQURfQ3BpU2hvdyIsInJlcXVlc3RfaWQiOiI0N2I2MWZkYi0wYzYzLTQ2ZmMtOTM0My1kZjc4Y2Q1YjcwMGYiLCJzdWJfcGxhdGZvcm0iOiJjcGkiLCJjaGFubmVsIjoiT01DX1NESyIsImNsaWVudF9pcCI6IjEuMS4xLjEiLCJzY3JlZW5fc2l6ZSI6IjB4MCIsImNvdW50cnkiOiJpZCIsIlBhcmFtcyI6W3siY2FtcGFpZ25faWQiOjIyMzgsInBvc19pZCI6IjIwNDkiLCJhZF9pZCI6MTAwNzY2LCJjYW1wX25hbWUiOiJwYW5sdWgtc2FuIiwiYWRfcGFja2FnZV9uYW1lIjoiY29tLmphbmVsLmRvY3Rvci5lYXIiLCJjaWQiOjM4ODAzLCJiaWRfcHJpY2UiOjEyMzAwMDAwMCwiZWNwbSI6Mjg5NTUzODA0LCJkc3BfbmFtZSI6IlNoYXJlaXQiLCJhdHRyX3BsYXRmb3JtIjoyLCJhZHNldF9pZCI6MTM1MCwiYWRfbmFtZSI6IlNBTi1TREsiLCJhZHNldF9uYW1lIjoiU0FOLVNESyIsInBoeV9wb3MiOiIyMDQ5In1dLCJtaWRhc192ZXJzaW9uIjoiMi4wIn0\&sid=__SID__\"]}",
      "adid":"100766"
    }]
  }],
  "cur":"USD"
}
```
## 2b) native large image response example

```json
{
  "id":"123",
  "bidid":"292bb9a0-0782-4d36-b543-437b47d48fef",
  "seatbid":[{
    "bid":[{
      "id":"292bb9a0-0782-4d36-b543-437b47d48fef",
      "impid":"1",
      "price":286,
      "burl":"http://midas-tracker-dev.hellay.net/win.fcg?viewid=e6d8578664e2f10e11afa9c2e16cb37680d4df1e94d245ba2d33780f1edaba4ac6aa12fb51d3bf16e4e45ea2f5d7f6001a07323bea0c8e8feabe0dc8d191ef8ab417be2d03b8f2f42b650f47da2e4cfc41a095014a039da67c124ea7967efe7813bb7a17263fad53e827b61f999d776ff1cab439eac5ca4a5a90cec45454569c719dcaeb76ecee7917aa2e81aac1b96ee38c0faed998697cef41595637e9d1789ff24157fb37d290cfd4f37c4f87682e950964cada4915e29ade88ee663dcca4ef4080a3b2c18a39c819c8c68d685c27d4fe098fb694eab0fc95fdd54c55909b3783d7556de04d0b9e0a69556da80f1f3d5d7422078be5635fff6209f88e4240728987fcc3b0117f7a87bd743356242cc8518ea5fe9ea9e545354cdeb46fd1912a21fd776145ed8df1b7bb7d185bcf119adeebb6a0004f85202f4edb7a8822be24bfaf0e2372f0fdedc91dd8bc07c63c17b1e6f2c613863e4843124a3f7f2524aa6505bfa88c9dcc8133c8e11a0e4e7b71bc3a16ce3c8cb7025af21f84288355f9f330aae9c3fadf9177b6a2c81669ef00f0da7e95ef1562ebf10da4fa26849d609a370cfc8a6ea6052b1182dd14eeb31870ce4dc064b8be92fa58ba2f33aa7c3ae1b5c2cdd5d13a1a09335730d9bf1dd473e70f0c44eea10769dc831399256b411a96cd8791ca0e978fa858717c041af3cb8b5e96fcfbf4eb9fb1d6df74249cf5a46fc831e4bf&auction_price=${AUCTION_PRICE}&sid=__SID__",
      "adm":"{\"ver\":\"1.2\",\"assets\":[{\"img\":{\"type\":3,\"url\":\"http://static-dev.rqmob.com/test/sa/20210710/95def64e487533b5415faaf8486491f5__FILE_CM____FILE_CM480_720____WEBP__.png\",\"w\":660,\"h\":346}}],\"link\":{\"url\":\"https://play.google.com/store/apps/details?id=com.janel.doctor.ear\&hl=en\",\"clicktrackers\":[\"http://midas-tracker-dev.hellay.net/clk.fcg?viewid=e6d8578664e2f10e11afa9c2e16cb37680d4df1e94d245ba2d33780f1edaba4ac6aa12fb51d3bf16e4e45ea2f5d7f6001a07323bea0c8e8feabe0dc8d191ef8ab417be2d03b8f2f42b650f47da2e4cfc41a095014a039da67c124ea7967efe7813bb7a17263fad53e827b61f999d776ff1cab439eac5ca4a5a90cec45454569c719dcaeb76ecee7917aa2e81aac1b96ee38c0faed998697cef41595637e9d1789ff24157fb37d290cfd4f37c4f87682e950964cada4915e29ade88ee663dcca4ef4080a3b2c18a39c819c8c68d685c27d4fe098fb694eab0fc95fdd54c55909b3783d7556de04d0b9e0a69556da80f1f3d5d7422078be5635fff6209f88e4240728987fcc3b0117f7a87bd743356242cc8518ea5fe9ea9e545354cdeb46fd1912a21fd776145ed8df1b7bb7d185bcf119adeebb6a0004f85202f4edb7a8822be24bfaf0e2372f0fdedc91dd8bc07c63c17b1e6f2c613863e4843124a3f7f2524aa6505bfa88c9dcc8133c8e11a0e4e7b71bc3a16ce3c8cb7025af21f84288355f9f330aae9c3fadf9177b6a2c81669ef00f0da7e95ef1562ebf10da4fa26849d609a370cfc8a6ea6052b1182dd14eeb31870ce4dc064b8be92fa58ba2f33aa7c3ae1b5c2cdd5d13a1a09335730d9bf1dd473e70f0c44eea10769dc831399256b411a96cd8791ca0e978fa858717c041af3cb8b5e96fcfbf4f892aad4d91638832204\&auction_price=${AUCTION_PRICE}\&sid=__SID__\",\"http://midas-tracker-dev.hellay.net/cpi_clk.fcg?log=eyJldmVudF9uYW1lIjoiQURfQ3BpQ2xpY2siLCJyZXF1ZXN0X2lkIjoiMjkyYmI5YTAtMDc4Mi00ZDM2LWI1NDMtNDM3YjQ3ZDQ4ZmVmIiwic3ViX3BsYXRmb3JtIjoiY3BpIiwiY2hhbm5lbCI6Ik9NQ19TREsiLCJjbGllbnRfaXAiOiIxLjEuMS4xIiwic2NyZWVuX3NpemUiOiIweDAiLCJjb3VudHJ5IjoiaWQiLCJQYXJhbXMiOlt7ImNhbXBhaWduX2lkIjoyMjM4LCJwb3NfaWQiOiIyMDQ5IiwiYWRfaWQiOjEwMDc2NiwiY2FtcF9uYW1lIjoicGFubHVoLXNhbiIsImFkX3BhY2thZ2VfbmFtZSI6ImNvbS5qYW5lbC5kb2N0b3IuZWFyIiwiY2lkIjozODgyNiwiYmlkX3ByaWNlIjoxMjMwMDAwMDAsImVjcG0iOjI4NjI2MjYxNCwiZHNwX25hbWUiOiJTaGFyZWl0IiwiYXR0cl9wbGF0Zm9ybSI6MiwiYWRzZXRfaWQiOjEzNTAsImFkX25hbWUiOiJTQU4tU0RLIiwiYWRzZXRfbmFtZSI6IlNBTi1TREsiLCJwaHlfcG9zIjoiMjA0OSJ9XSwibWlkYXNfdmVyc2lvbiI6IjIuMCJ9\&sid=__SID__\",\"http://ping-test.rqmob.com/click?ad=SAN-SDK\&ad_id=100766\&ad_type={ad_type}\&adpos_id=2049\&adset={adset}\&adset_id=1350\&advid=29\&amp_app_id=7752\&android_id=\&app_id=\&app_type=3\&beyla_id=\&c={c}\&c_id=38826\&campid=1321943\&channel_pkg=\&channel_pkg_ver=0\&cost_currency={cost_currency}\&cost_model={cost_model}\&cost_value={cost_value}\&country_code=id\&device_id=\&ext_info={ext_info}\&gaid=\&imei={imei}\&imsi={imsi}\&ip=1.1.1.1\&is_offline=1\&is_pre_install={is_pre_install}\&midas_camp_id=2238\&midas_traffic_type=1\&os_version=\&other_category={other_category}\&pkg=com.janel.doctor.ear\&placement=2049\&platform=adshonor\&real_attrplat=2\&remote_ip=1.1.1.1\&requestid=292bb9a0-0782-4d36-b543-437b47d48fef\&sid={sid}\&site_id={site_id}\&uagent=\",\"http://midas-tracker-dev.hellay.net/effect.fcg?viewid=e6d8578664e2f10e11afa9c2e16cb37680d4df1e94d245ba2d33780f1edaba4ac6aa12fb51d3bf16e4e45ea2f5d7f6001a07323bea0c8e8feabe0dc8d191ef8ab417be2d03b8f2f42b650f47da2e4cfc41a095014a039da67c124ea7967efe7813bb7a17263fad53e827b61f999d776ff1cab439eac5ca4a5a90cec45454569c719dcaeb76ecee7917aa2e81aac1b96ee38c0faed998697cef41595637e9d1789ff24157fb37d290cfd4f37c4f87682e950964cada4915e29ade88ee663dcca4ef4080a3b2c18a39c819c8c68d685c27d4fe098fb694eab0fc95fdd54c55909b3783d7556de04d0b9e0a69556da80f1f3d5d7422078be5635fff6209f88e4240728987fcc3b0117f7a87bd743356242cc8518ea5fe9ea9e545354cdeb46fd1912a21fd776145ed8df1b7bb7d185bcf119adeebb6a0004f85202f4edb7a8822be24bfaf0e2372f0fdedc91dd8bc07c63c17b1e6f2c613863e4843124a3f7f2524aa6505bfa88c9dcc8133c8e11a0e4e7b71bc3a16ce3c8cb7025af21f84288355f9f330aae9c3fadf9177b6a2c81669ef00f0da7e95ef1562ebf10da4fa26849d609a370cfc8a6ea6052b1182dd14eeb31870ce4dc064b8be92fa58ba2f33aa7c3ae1b5c2cdd5d13a1a09335730d9bf1dd473e70f0c44eea10769dc831399256b411a96cd8791ca0e978fa858717c041af3cb8b5e96fcfbf4ff97b0c7de2834ae6eb4de3deb240e3b1ff423\&effect_type={EFFECT_TYPE}\&sid=__SID__\"]},\"imptrackers\":[\"http://midas-tracker-dev.hellay.net/imp.fcg?viewid=e6d8578664e2f10e11afa9c2e16cb37680d4df1e94d245ba2d33780f1edaba4ac6aa12fb51d3bf16e4e45ea2f5d7f6001a07323bea0c8e8feabe0dc8d191ef8ab417be2d03b8f2f42b650f47da2e4cfc41a095014a039da67c124ea7967efe7813bb7a17263fad53e827b61f999d776ff1cab439eac5ca4a5a90cec45454569c719dcaeb76ecee7917aa2e81aac1b96ee38c0faed998697cef41595637e9d1789ff24157fb37d290cfd4f37c4f87682e950964cada4915e29ade88ee663dcca4ef4080a3b2c18a39c819c8c68d685c27d4fe098fb694eab0fc95fdd54c55909b3783d7556de04d0b9e0a69556da80f1f3d5d7422078be5635fff6209f88e4240728987fcc3b0117f7a87bd743356242cc8518ea5fe9ea9e545354cdeb46fd1912a21fd776145ed8df1b7bb7d185bcf119adeebb6a0004f85202f4edb7a8822be24bfaf0e2372f0fdedc91dd8bc07c63c17b1e6f2c613863e4843124a3f7f2524aa6505bfa88c9dcc8133c8e11a0e4e7b71bc3a16ce3c8cb7025af21f84288355f9f330aae9c3fadf9177b6a2c81669ef00f0da7e95ef1562ebf10da4fa26849d609a370cfc8a6ea6052b1182dd14eeb31870ce4dc064b8be92fa58ba2f33aa7c3ae1b5c2cdd5d13a1a09335730d9bf1dd473e70f0c44eea10769dc831399256b411a96cd8791ca0e978fa858717c041af3cb8b5e96fcfbf4ff97b0c7de2834ae6eb4de3deb240e3b1ff423\&auction_price=${AUCTION_PRICE}\&sid=__SID__\",\"http://midas-tracker-dev.hellay.net/cpi_imp.fcg?log=eyJldmVudF9uYW1lIjoiQURfQ3BpU2hvdyIsInJlcXVlc3RfaWQiOiIyOTJiYjlhMC0wNzgyLTRkMzYtYjU0My00MzdiNDdkNDhmZWYiLCJzdWJfcGxhdGZvcm0iOiJjcGkiLCJjaGFubmVsIjoiT01DX1NESyIsImNsaWVudF9pcCI6IjEuMS4xLjEiLCJzY3JlZW5fc2l6ZSI6IjB4MCIsImNvdW50cnkiOiJpZCIsIlBhcmFtcyI6W3siY2FtcGFpZ25faWQiOjIyMzgsInBvc19pZCI6IjIwNDkiLCJhZF9pZCI6MTAwNzY2LCJjYW1wX25hbWUiOiJwYW5sdWgtc2FuIiwiYWRfcGFja2FnZV9uYW1lIjoiY29tLmphbmVsLmRvY3Rvci5lYXIiLCJjaWQiOjM4ODI2LCJiaWRfcHJpY2UiOjEyMzAwMDAwMCwiZWNwbSI6Mjg2MjYyNjE0LCJkc3BfbmFtZSI6IlNoYXJlaXQiLCJhdHRyX3BsYXRmb3JtIjoyLCJhZHNldF9pZCI6MTM1MCwiYWRfbmFtZSI6IlNBTi1TREsiLCJhZHNldF9uYW1lIjoiU0FOLVNESyIsInBoeV9wb3MiOiIyMDQ5In1dLCJtaWRhc192ZXJzaW9uIjoiMi4wIn0\&sid=__SID__\"]}",
      "adid":"100766",
      "bundle":"com.janel.doctor.ear"
     }]
   }],
   "cur":"USD"
}
```
## 2c) native video response example

```json
{
  "id":"32f94228-52d3-4bce-be88-5dd1d799ae4f",
  "bidid":"a5254b1b-f95d-42b5-8415-c660712532b2",
  "seatbid":[{
    "bid":[{
      "id":"a5254b1b-f95d-42b5-8415-c660712532b2",
      "impid":"1",
      "price":50,
      "burl":"http://midas-tracker-dev.hellay.net/win.fcg?viewid=e6d8578664e2f10e11afa9c0e96cb3762e56ab1614a0eb790bda8dee1f46ddd0ed054d91e419ea8b705890309607448e65f407e9336bc0a90533085ff8f141a42984adca526e1cca8ddf69757aecb73b05a22892d982a78aabbf0a1f6079b696e653900269900c16d45a364f062e705ec9adb3b1d6334b2746ef9f3ed20dc6ef05d95e16aa65e23c7e0b52cb1ce70ee639943f7b95625198ec7ac09435643ed9c4abd37f686f89f4ea123215aa700aa73005e728bcb45d054bb75ba53b2bb105286ce8941b833064268f1fb47f6cb00b0c3030e892027fc3178b7aeda7a0fe9efcb34e32ccd590569643552cae4cb5d6a359acb6b326faf3434c5ddf7574179869e6482ca8a5fdb4b7d344ed3cb022cabf9bd33e1316be063fefb6ac55113ec00eda60f87e50c3019442885a22873312f97ffd6fed0b69871925b9fee5b1923bde7212f824eea9c66deb48a60a8a20bfb895d26a3e1fb1614eefcdd8e16d899ba83e79803d451f3f8664ea3a4263915eadb1ac314f715062365ec0fe9a97e01f3cba17f73142e937034de4aeab9e5c64a445367dbff95805c26dba982d7d97914c5b2670f5528553a93a7aefa85e4875a35d79633e319c6e65f344f47b302ef3a76f9fad88bc3d3b7890b08097a4839a8c58dcb83027b0e80ce12ee7988f8660da46b8723f736122efbee4441724ba697a81160c9014e45ab023847a4f79ad987c1e49da43b7d3a0fb3b6e3ecc6f6cd1d9cccb166e7495fcd7d41bda6ca2cf7cadfd3e8825843f081c8faa098a34121a36ae4164&auction_price=${AUCTION_PRICE}&sid=__SID__",
    "adm":"{\"assets\":[{\"id\":1,\"title\":{\"text\":\"openrtb-this is ad title\",\"len\":14}},{\"id\":7,\"video\":{\"vasttag\":\"\<VAST version=\\\"3.0\\\"\>\<Ad id=\\\"100674\\\"\>\<InLine\>\<AdSystem\>\<![CDATA[midas]]\>\</AdSystem\>\<AdTitle\>\<![CDATA[openrtb-this is ad title]]\>\</AdTitle\>\<Impression\>\<![CDATA[http://midas-tracker-dev.hellay.net/imp.fcg?viewid=e6d8578664e2f10e11afa9c0e96cb3762e56ab1614a0eb790bda8dee1f46ddd0ed054d91e419ea8b705890309607448e65f407e9336bc0a90533085ff8f141a42984adca526e1cca8ddf69757aecb73b05a22892d982a78aabbf0a1f6079b696e653900269900c16d45a364f062e705ec9adb3b1d6334b2746ef9f3ed20dc6ef05d95e16aa65e23c7e0b52cb1ce70ee639943f7b95625198ec7ac09435643ed9c4abd37f686f89f4ea123215aa700aa73005e728bcb45d054bb75ba53b2bb105286ce8941b833064268f1fb47f6cb00b0c3030e892027fc3178b7aeda7a0fe9efcb34e32ccd590569643552cae4cb5d6a359acb6b326faf3434c5ddf7574179869e6482ca8a5fdb4b7d344ed3cb022cabf9bd33e1316be063fefb6ac55113ec00eda60f87e50c3019442885a22873312f97ffd6fed0b69871925b9fee5b1923bde7212f824eea9c66deb48a60a8a20bfb895d26a3e1fb1614eefcdd8e16d899ba83e79803d451f3f8664ea3a4263915eadb1ac314f715062365ec0fe9a97e01f3cba17f73142e937034de4aeab9e5c64a445367dbff95805c26dba982d7d97914c5b2670f5528553a93a7aefa85e4875a35d79633e319c6e65f344f47b302ef3a76f9fad88bc3d3b7890b08097a4839a8c58dcb83027b0e80ce12ee7988f8660da46b8723f736122efbee4441724ba697a81160c9014e45ab023847a4f79ad987c1e49da43b7d3a0fb3b6e3ecc6f6cd1d9cccb166e7495fcd7d41bda6ca2cf7cadfd3e88259037090d8ef619b830020e3eeedd3895de2a52\&auction_price=${AUCTION_PRICE}\&sid=__SID__]]\>\</Impression\>\<Impression\>\<![CDATA[http://midas-tracker-dev.hellay.net/cpi_imp.fcg?log=eyJldmVudF9uYW1lIjoiQURfQ3BpU2hvdyIsInJlcXVlc3RfaWQiOiJhNTI1NGIxYi1mOTVkLTQyYjUtODQxNS1jNjYwNzEyNTMyYjIiLCJzdWJfcGxhdGZvcm0iOiJjcGkiLCJjaGFubmVsIjoiT01DX1NESyIsImNsaWVudF9pcCI6IjEuMS4xLjEiLCJwbGF0Zm9ybSI6MSwib3NfdmVyc2lvbiI6IjUuMS4xIiwiaW1laSI6ImVjYWU5MDQyZjNlNTQ5YTRmZDFhZjI3YTFlZDM4YjVmNjgyZmEzY2EiLCJicmFuZCI6IldJS08iLCJtb2RlbCI6InNhbXN1bmctc20tZzkwMGEiLCJzY3JlZW5fc2l6ZSI6IjB4MCIsImxhbmd1YWdlIjoiZW4iLCJnYWlkIjoiNTczMWI0YzgtN2NjMS00YTA5LWJiNzctMjRmMjM3ZDkzYTY2IiwibmV0d29ya190eXBlIjo3LCJjb3VudHJ5IjoiaW4iLCJQYXJhbXMiOlt7ImNhbXBhaWduX2lkIjoyMTM2LCJwb3NfaWQiOiIyMDYxIiwiYWRfaWQiOjEwMDY3NCwiY2FtcF9uYW1lIjoi5p2o5bCR55GcLXNoYXJlaXQt5rWL6K-VLW9wZW5ydGIiLCJhZF9wYWNrYWdlX25hbWUiOiJjYy5mb3Jlc3RhcHAiLCJjaWQiOjM4Njk4LCJiaWRfcHJpY2UiOjEwMDAwMDAwMDAsImVjcG0iOjY4MjE5MzIwMCwiZHNwX25hbWUiOiJTaGFyZWl0IiwiYXR0cl9wbGF0Zm9ybSI6MSwiYWRzZXRfaWQiOjEyMzQsImFkX25hbWUiOiLmnajlsJHnkZwtb3BlbnJ0Yi0xOOinhOagvC3lsI_nsbMiLCJhZHNldF9uYW1lIjoi5p2o5bCR55GcLW9wZW5ydGIt5bCP57GzIiwicGh5X3BvcyI6IjIwNjEifV0sIm1pZGFzX3ZlcnNpb24iOiIyLjAifQ\&sid=__SID__]]\>\</Impression\>\<Creatives\>\<Creative id=\\\"38698\\\" AdID=\\\"100674\\\"\>\<Linear\>\<Duration\>00:00:15\</Duration\>\<TrackingEvents\>\<Tracking event=\\\"start\\\"\>\<![CDATA[http://midas-tracker-dev.hellay.net/play.fcg?viewid=e6d8578664e2f10e11afa9c0e96cb3762e56ab1614a0eb790bda8dee1f46ddd0ed054d91e419ea8b705890309607448e65f407e9336bc0a90533085ff8f141a42984adca526e1cca8ddf69757aecb73b05a22892d982a78aabbf0a1f6079b696e653900269900c16d45a364f062e705ec9adb3b1d6334b2746ef9f3ed20dc6ef05d95e16aa65e23c7e0b52cb1ce70ee639943f7b95625198ec7ac09435643ed9c4abd37f686f89f4ea123215aa700aa73005e728bcb45d054bb75ba53b2bb105286ce8941b833064268f1fb47f6cb00b0c3030e892027fc3178b7aeda7a0fe9efcb34e32ccd590569643552cae4cb5d6a359acb6b326faf3434c5ddf7574179869e6482ca8a5fdb4b7d344ed3cb022cabf9bd33e1316be063fefb6ac55113ec00eda60f87e50c3019442885a22873312f97ffd6fed0b69871925b9fee5b1923bde7212f824eea9c66deb48a60a8a20bfb895d26a3e1fb1614eefcdd8e16d899ba83e79803d451f3f8664ea3a4263915eadb1ac314f715062365ec0fe9a97e01f3cba17f73142e937034de4aeab9e5c64a445367dbff95805c26dba982d7d97914c5b2670f5528553a93a7aefa85e4875a35d79633e319c6e65f344f47b302ef3a76f9fad88bc3d3b7890b08097a4839a8c58dcb83027b0e80ce12ee7988f8660da46b8723f736122efbee4441724ba697a81160c9014e45ab023847a4f79ad987c1e49da43b7d3a0fb3b6e3ecc6f6cd1d9cccb166e7495fcd7d41bda6ca2cf7cadfd3e882584321b04bde7018421460ddfba3c99\&play_duration={PLAYDURATION}\&sid=__SID__]]\>\</Tracking\>\<Tracking event=\\\"firstQuartile\\\"\>\<![CDATA[http://midas-tracker-dev.hellay.net/play.fcg?viewid=e6d8578664e2f10e11afa9c0e96cb3762e56ab1614a0eb790bda8dee1f46ddd0ed054d91e419ea8b705890309607448e65f407e9336bc0a90533085ff8f141a42984adca526e1cca8ddf69757aecb73b05a22892d982a78aabbf0a1f6079b696e653900269900c16d45a364f062e705ec9adb3b1d6334b2746ef9f3ed20dc6ef05d95e16aa65e23c7e0b52cb1ce70ee639943f7b95625198ec7ac09435643ed9c4abd37f686f89f4ea123215aa700aa73005e728bcb45d054bb75ba53b2bb105286ce8941b833064268f1fb47f6cb00b0c3030e892027fc3178b7aeda7a0fe9efcb34e32ccd590569643552cae4cb5d6a359acb6b326faf3434c5ddf7574179869e6482ca8a5fdb4b7d344ed3cb022cabf9bd33e1316be063fefb6ac55113ec00eda60f87e50c3019442885a22873312f97ffd6fed0b69871925b9fee5b1923bde7212f824eea9c66deb48a60a8a20bfb895d26a3e1fb1614eefcdd8e16d899ba83e79803d451f3f8664ea3a4263915eadb1ac314f715062365ec0fe9a97e01f3cba17f73142e937034de4aeab9e5c64a445367dbff95805c26dba982d7d97914c5b2670f5528553a93a7aefa85e4875a35d79633e319c6e65f344f47b302ef3a76f9fad88bc3d3b7890b08097a4839a8c58dcb83027b0e80ce12ee7988f8660da46b8723f736122efbee4441724ba697a81160c9014e45ab023847a4f79ad987c1e49da43b7d3a0fb3b6e3ecc6f6cd1d9cccb166e7495fcd7d41bda6ca2cf7cadfd3e882584321b04bde7018421460f1d3c35c57b95\&play_duration={PLAYDURATION}\&sid=__SID__]]\>\</Tracking\>\<Tracking event=\\\"midpoint\\\"\>\<![CDATA[http://midas-tracker-dev.hellay.net/play.fcg?viewid=e6d8578664e2f10e11afa9c0e96cb3762e56ab1614a0eb790bda8dee1f46ddd0ed054d91e419ea8b705890309607448e65f407e9336bc0a90533085ff8f141a42984adca526e1cca8ddf69757aecb73b05a22892d982a78aabbf0a1f6079b696e653900269900c16d45a364f062e705ec9adb3b1d6334b2746ef9f3ed20dc6ef05d95e16aa65e23c7e0b52cb1ce70ee639943f7b95625198ec7ac09435643ed9c4abd37f686f89f4ea123215aa700aa73005e728bcb45d054bb75ba53b2bb105286ce8941b833064268f1fb47f6cb00b0c3030e892027fc3178b7aeda7a0fe9efcb34e32ccd590569643552cae4cb5d6a359acb6b326faf3434c5ddf7574179869e6482ca8a5fdb4b7d344ed3cb022cabf9bd33e1316be063fefb6ac55113ec00eda60f87e50c3019442885a22873312f97ffd6fed0b69871925b9fee5b1923bde7212f824eea9c66deb48a60a8a20bfb895d26a3e1fb1614eefcdd8e16d899ba83e79803d451f3f8664ea3a4263915eadb1ac314f715062365ec0fe9a97e01f3cba17f73142e937034de4aeab9e5c64a445367dbff95805c26dba982d7d97914c5b2670f5528553a93a7aefa85e4875a35d79633e319c6e65f344f47b302ef3a76f9fad88bc3d3b7890b08097a4839a8c58dcb83027b0e80ce12ee7988f8660da46b8723f736122efbee4441724ba697a81160c9014e45ab023847a4f79ad987c1e49da43b7d3a0fb3b6e3ecc6f6cd1d9cccb166e7495fcd7d41bda6ca2cf7cadfd3e882584321b04bde70184214616daafdc\&play_duration={PLAYDURATION}\&sid=__SID__]]\>\</Tracking\>\<Tracking event=\\\"thirdQuartile\\\"\>\<![CDATA[http://midas-tracker-dev.hellay.net/play.fcg?viewid=e6d8578664e2f10e11afa9c0e96cb3762e56ab1614a0eb790bda8dee1f46ddd0ed054d91e419ea8b705890309607448e65f407e9336bc0a90533085ff8f141a42984adca526e1cca8ddf69757aecb73b05a22892d982a78aabbf0a1f6079b696e653900269900c16d45a364f062e705ec9adb3b1d6334b2746ef9f3ed20dc6ef05d95e16aa65e23c7e0b52cb1ce70ee639943f7b95625198ec7ac09435643ed9c4abd37f686f89f4ea123215aa700aa73005e728bcb45d054bb75ba53b2bb105286ce8941b833064268f1fb47f6cb00b0c3030e892027fc3178b7aeda7a0fe9efcb34e32ccd590569643552cae4cb5d6a359acb6b326faf3434c5ddf7574179869e6482ca8a5fdb4b7d344ed3cb022cabf9bd33e1316be063fefb6ac55113ec00eda60f87e50c3019442885a22873312f97ffd6fed0b69871925b9fee5b1923bde7212f824eea9c66deb48a60a8a20bfb895d26a3e1fb1614eefcdd8e16d899ba83e79803d451f3f8664ea3a4263915eadb1ac314f715062365ec0fe9a97e01f3cba17f73142e937034de4aeab9e5c64a445367dbff95805c26dba982d7d97914c5b2670f5528553a93a7aefa85e4875a35d79633e319c6e65f344f47b302ef3a76f9fad88bc3d3b7890b08097a4839a8c58dcb83027b0e80ce12ee7988f8660da46b8723f736122efbee4441724ba697a81160c9014e45ab023847a4f79ad987c1e49da43b7d3a0fb3b6e3ecc6f6cd1d9cccb166e7495fcd7d41bda6ca2cf7cadfd3e882584321b04bde7018421460adcb5a4e74a7686688a608288\&play_duration={PLAYDURATION}\&sid=__SID__]]\>\</Tracking\>\<Tracking event=\\\"complete\\\"\>\<![CDATA[http://midas-tracker-dev.hellay.net/play.fcg?viewid=e6d8578664e2f10e11afa9c0e96cb3762e56ab1614a0eb790bda8dee1f46ddd0ed054d91e419ea8b705890309607448e65f407e9336bc0a90533085ff8f141a42984adca526e1cca8ddf69757aecb73b05a22892d982a78aabbf0a1f6079b696e653900269900c16d45a364f062e705ec9adb3b1d6334b2746ef9f3ed20dc6ef05d95e16aa65e23c7e0b52cb1ce70ee639943f7b95625198ec7ac09435643ed9c4abd37f686f89f4ea123215aa700aa73005e728bcb45d054bb75ba53b2bb105286ce8941b833064268f1fb47f6cb00b0c3030e892027fc3178b7aeda7a0fe9efcb34e32ccd590569643552cae4cb5d6a359acb6b326faf3434c5ddf7574179869e6482ca8a5fdb4b7d344ed3cb022cabf9bd33e1316be063fefb6ac55113ec00eda60f87e50c3019442885a22873312f97ffd6fed0b69871925b9fee5b1923bde7212f824eea9c66deb48a60a8a20bfb895d26a3e1fb1614eefcdd8e16d899ba83e79803d451f3f8664ea3a4263915eadb1ac314f715062365ec0fe9a97e01f3cba17f73142e937034de4aeab9e5c64a445367dbff95805c26dba982d7d97914c5b2670f5528553a93a7aefa85e4875a35d79633e319c6e65f344f47b302ef3a76f9fad88bc3d3b7890b08097a4839a8c58dcb83027b0e80ce12ee7988f8660da46b8723f736122efbee4441724ba697a81160c9014e45ab023847a4f79ad987c1e49da43b7d3a0fb3b6e3ecc6f6cd1d9cccb166e7495fcd7d41bda6ca2cf7cadfd3e882584321b04bde7018421461d1c146c45935266\&play_duration={PLAYDURATION}\&sid=__SID__]]\>\</Tracking\>\<Tracking event=\\\"resume\\\"\>\<![CDATA[http://midas-tracker-dev.hellay.net/play.fcg?viewid=e6d8578664e2f10e11afa9c0e96cb3762e56ab1614a0eb790bda8dee1f46ddd0ed054d91e419ea8b705890309607448e65f407e9336bc0a90533085ff8f141a42984adca526e1cca8ddf69757aecb73b05a22892d982a78aabbf0a1f6079b696e653900269900c16d45a364f062e705ec9adb3b1d6334b2746ef9f3ed20dc6ef05d95e16aa65e23c7e0b52cb1ce70ee639943f7b95625198ec7ac09435643ed9c4abd37f686f89f4ea123215aa700aa73005e728bcb45d054bb75ba53b2bb105286ce8941b833064268f1fb47f6cb00b0c3030e892027fc3178b7aeda7a0fe9efcb34e32ccd590569643552cae4cb5d6a359acb6b326faf3434c5ddf7574179869e6482ca8a5fdb4b7d344ed3cb022cabf9bd33e1316be063fefb6ac55113ec00eda60f87e50c3019442885a22873312f97ffd6fed0b69871925b9fee5b1923bde7212f824eea9c66deb48a60a8a20bfb895d26a3e1fb1614eefcdd8e16d899ba83e79803d451f3f8664ea3a4263915eadb1ac314f715062365ec0fe9a97e01f3cba17f73142e937034de4aeab9e5c64a445367dbff95805c26dba982d7d97914c5b2670f5528553a93a7aefa85e4875a35d79633e319c6e65f344f47b302ef3a76f9fad88bc3d3b7890b08097a4839a8c58dcb83027b0e80ce12ee7988f8660da46b8723f736122efbee4441724ba697a81160c9014e45ab023847a4f79ad987c1e49da43b7d3a0fb3b6e3ecc6f6cd1d9cccb166e7495fcd7d41bda6ca2cf7cadfd3e882584321b04bde7018421460c21ba10f3e2\&play_duration={PLAYDURATION}\&sid=__SID__]]\>\</Tracking\>\</TrackingEvents\>\<VideoClicks\>\<ClickThrough\>\</ClickThrough\>\</VideoClicks\>\<MediaFiles\>\<MediaFile delivery=\\\"progressive\\\" type=\\\"video/mp4\\\" width=\\\"720\\\" height=\\\"1280\\\"\>\<![CDATA[http://static-dev.rqmob.com/test/sa/20210518/3cac33a7d34ff7d482b05fc00b59622e.mp4]]\>\</MediaFile\>\</MediaFiles\>\</Linear\>\</Creative\>\<Creative\>\<CompanionAds\>\<Companion width=\\\"720\\\" height=\\\"1280\\\"\>\<CompanionClickThrough\>\</CompanionClickThrough\>\<TrackingEvents\>\</TrackingEvents\>\<StaticResource creativeType=\\\"image/png\\\"\>\<![CDATA[http://static-dev.rqmob.com/test/sa/20201012/e804e830061916a6d502c740eb009a9a__FILE_CM____FILE_CM480_720__.png]]\>\</StaticResource\>\<IFrameResource\>\</IFrameResource\>\</Companion\>\</CompanionAds\>\</Creative\>\</Creatives\>\<Description\>\<![CDATA[openrtb-this is ad description]]\>\</Description\>\<Survey\>\</Survey\>\</InLine\>\</Ad\>\</VAST\>\"}}],\"link\":{\"url\":\"https://play.google.com/store/apps/details?id=cc.forestapp\&hl=en\",\"clicktrackers\":[\"http://midas-tracker-dev.hellay.net/clk.fcg?viewid=e6d8578664e2f10e11afa9c0e96cb3762e56ab1614a0eb790bda8dee1f46ddd0ed054d91e419ea8b705890309607448e65f407e9336bc0a90533085ff8f141a42984adca526e1cca8ddf69757aecb73b05a22892d982a78aabbf0a1f6079b696e653900269900c16d45a364f062e705ec9adb3b1d6334b2746ef9f3ed20dc6ef05d95e16aa65e23c7e0b52cb1ce70ee639943f7b95625198ec7ac09435643ed9c4abd37f686f89f4ea123215aa700aa73005e728bcb45d054bb75ba53b2bb105286ce8941b833064268f1fb47f6cb00b0c3030e892027fc3178b7aeda7a0fe9efcb34e32ccd590569643552cae4cb5d6a359acb6b326faf3434c5ddf7574179869e6482ca8a5fdb4b7d344ed3cb022cabf9bd33e1316be063fefb6ac55113ec00eda60f87e50c3019442885a22873312f97ffd6fed0b69871925b9fee5b1923bde7212f824eea9c66deb48a60a8a20bfb895d26a3e1fb1614eefcdd8e16d899ba83e79803d451f3f8664ea3a4263915eadb1ac314f715062365ec0fe9a97e01f3cba17f73142e937034de4aeab9e5c64a445367dbff95805c26dba982d7d97914c5b2670f5528553a93a7aefa85e4875a35d79633e319c6e65f344f47b302ef3a76f9fad88bc3d3b7890b08097a4839a8c58dcb83027b0e80ce12ee7988f8660da46b8723f736122efbee4441724ba697a81160c9014e45ab023847a4f79ad987c1e49da43b7d3a0fb3b6e3ecc6f6cd1d9cccb166e7495fcd7d41bda6ca2cf7cadfd3e88259732131e89c815952846\&auction_price=${AUCTION_PRICE}\&sid=__SID__\",\"http://midas-tracker-dev.hellay.net/cpi_clk.fcg?log=eyJldmVudF9uYW1lIjoiQURfQ3BpQ2xpY2siLCJyZXF1ZXN0X2lkIjoiYTUyNTRiMWItZjk1ZC00MmI1LTg0MTUtYzY2MDcxMjUzMmIyIiwic3ViX3BsYXRmb3JtIjoiY3BpIiwiY2hhbm5lbCI6Ik9NQ19TREsiLCJjbGllbnRfaXAiOiIxLjEuMS4xIiwicGxhdGZvcm0iOjEsIm9zX3ZlcnNpb24iOiI1LjEuMSIsImltZWkiOiJlY2FlOTA0MmYzZTU0OWE0ZmQxYWYyN2ExZWQzOGI1ZjY4MmZhM2NhIiwiYnJhbmQiOiJXSUtPIiwibW9kZWwiOiJzYW1zdW5nLXNtLWc5MDBhIiwic2NyZWVuX3NpemUiOiIweDAiLCJsYW5ndWFnZSI6ImVuIiwiZ2FpZCI6IjU3MzFiNGM4LTdjYzEtNGEwOS1iYjc3LTI0ZjIzN2Q5M2E2NiIsIm5ldHdvcmtfdHlwZSI6NywiY291bnRyeSI6ImluIiwiUGFyYW1zIjpbeyJjYW1wYWlnbl9pZCI6MjEzNiwicG9zX2lkIjoiMjA2MSIsImFkX2lkIjoxMDA2NzQsImNhbXBfbmFtZSI6IuadqOWwkeeRnC1zaGFyZWl0Lea1i-ivlS1vcGVucnRiIiwiYWRfcGFja2FnZV9uYW1lIjoiY2MuZm9yZXN0YXBwIiwiY2lkIjozODY5OCwiYmlkX3ByaWNlIjoxMDAwMDAwMDAwLCJlY3BtIjo2ODIxOTMyMDAsImRzcF9uYW1lIjoiU2hhcmVpdCIsImF0dHJfcGxhdGZvcm0iOjEsImFkc2V0X2lkIjoxMjM0LCJhZF9uYW1lIjoi5p2o5bCR55GcLW9wZW5ydGItMTjop4TmoLwt5bCP57GzIiwiYWRzZXRfbmFtZSI6IuadqOWwkeeRnC1vcGVucnRiLeWwj-exsyIsInBoeV9wb3MiOiIyMDYxIn1dLCJtaWRhc192ZXJzaW9uIjoiMi4wIn0\&sid=__SID__\"]},\"imptrackers\":[\"http://midas-tracker-dev.hellay.net/imp.fcg?viewid=e6d8578664e2f10e11afa9c0e96cb3762e56ab1614a0eb790bda8dee1f46ddd0ed054d91e419ea8b705890309607448e65f407e9336bc0a90533085ff8f141a42984adca526e1cca8ddf69757aecb73b05a22892d982a78aabbf0a1f6079b696e653900269900c16d45a364f062e705ec9adb3b1d6334b2746ef9f3ed20dc6ef05d95e16aa65e23c7e0b52cb1ce70ee639943f7b95625198ec7ac09435643ed9c4abd37f686f89f4ea123215aa700aa73005e728bcb45d054bb75ba53b2bb105286ce8941b833064268f1fb47f6cb00b0c3030e892027fc3178b7aeda7a0fe9efcb34e32ccd590569643552cae4cb5d6a359acb6b326faf3434c5ddf7574179869e6482ca8a5fdb4b7d344ed3cb022cabf9bd33e1316be063fefb6ac55113ec00eda60f87e50c3019442885a22873312f97ffd6fed0b69871925b9fee5b1923bde7212f824eea9c66deb48a60a8a20bfb895d26a3e1fb1614eefcdd8e16d899ba83e79803d451f3f8664ea3a4263915eadb1ac314f715062365ec0fe9a97e01f3cba17f73142e937034de4aeab9e5c64a445367dbff95805c26dba982d7d97914c5b2670f5528553a93a7aefa85e4875a35d79633e319c6e65f344f47b302ef3a76f9fad88bc3d3b7890b08097a4839a8c58dcb83027b0e80ce12ee7988f8660da46b8723f736122efbee4441724ba697a81160c9014e45ab023847a4f79ad987c1e49da43b7d3a0fb3b6e3ecc6f6cd1d9cccb166e7495fcd7d41bda6ca2cf7cadfd3e88259037090d8ef619b830020e3eeedd3895de2a52\&auction_price=${AUCTION_PRICE}\&sid=__SID__\",\"http://midas-tracker-dev.hellay.net/cpi_imp.fcg?log=eyJldmVudF9uYW1lIjoiQURfQ3BpU2hvdyIsInJlcXVlc3RfaWQiOiJhNTI1NGIxYi1mOTVkLTQyYjUtODQxNS1jNjYwNzEyNTMyYjIiLCJzdWJfcGxhdGZvcm0iOiJjcGkiLCJjaGFubmVsIjoiT01DX1NESyIsImNsaWVudF9pcCI6IjEuMS4xLjEiLCJwbGF0Zm9ybSI6MSwib3NfdmVyc2lvbiI6IjUuMS4xIiwiaW1laSI6ImVjYWU5MDQyZjNlNTQ5YTRmZDFhZjI3YTFlZDM4YjVmNjgyZmEzY2EiLCJicmFuZCI6IldJS08iLCJtb2RlbCI6InNhbXN1bmctc20tZzkwMGEiLCJzY3JlZW5fc2l6ZSI6IjB4MCIsImxhbmd1YWdlIjoiZW4iLCJnYWlkIjoiNTczMWI0YzgtN2NjMS00YTA5LWJiNzctMjRmMjM3ZDkzYTY2IiwibmV0d29ya190eXBlIjo3LCJjb3VudHJ5IjoiaW4iLCJQYXJhbXMiOlt7ImNhbXBhaWduX2lkIjoyMTM2LCJwb3NfaWQiOiIyMDYxIiwiYWRfaWQiOjEwMDY3NCwiY2FtcF9uYW1lIjoi5p2o5bCR55GcLXNoYXJlaXQt5rWL6K-VLW9wZW5ydGIiLCJhZF9wYWNrYWdlX25hbWUiOiJjYy5mb3Jlc3RhcHAiLCJjaWQiOjM4Njk4LCJiaWRfcHJpY2UiOjEwMDAwMDAwMDAsImVjcG0iOjY4MjE5MzIwMCwiZHNwX25hbWUiOiJTaGFyZWl0IiwiYXR0cl9wbGF0Zm9ybSI6MSwiYWRzZXRfaWQiOjEyMzQsImFkX25hbWUiOiLmnajlsJHnkZwtb3BlbnJ0Yi0xOOinhOagvC3lsI_nsbMiLCJhZHNldF9uYW1lIjoi5p2o5bCR55GcLW9wZW5ydGIt5bCP57GzIiwicGh5X3BvcyI6IjIwNjEifV0sIm1pZGFzX3ZlcnNpb24iOiIyLjAifQ\&sid=__SID__\"]}",
      "adid":"100674"
    }]
  }],
  "cur":"USD"
}
```

## 2d）banner response example
```json
{
    "id": "123",
    "bidid": "a1271eca-efa2-4f9f-8904-a853afec1289",
    "seatbid": [
        {
            "bid": [
                {
                    "id": "a1271eca-efa2-4f9f-8904-a853afec1289",
                    "impid": "1",
                    "price": 118.0806,
                    "burl": "https://midas-tracker-test.hellay.net/win.fcg?viewid=e6d8578664e2f10e11afa8c3eb6cb3763be39af447238100277632423c9c212f3987802acb093fa8f226d2beb00ad9aa5d901a36db98e81c1c0f1639ad363decc476977f6ba1dcb36318671a7a606d34961563c37535b94719f7eb4a8d53d8b3c80d002386ea6227bc2e50cdbcaa0c40a29bee9ef33b63c3f56ae4c59790d02b2be9ce6be9598e84f92c0efb7e9fdcf311fb0326d959dbd306031f78ae6a4a34675ad8bb6e84571c015638463b14fab8eded30cabefcf16c758eac517853709909da5be52230975657723bd0182b8eb7e92423a55066d07ab9c25a2c38cb0df2af9462c41155773054912137f7f508187acdfde64036bbcc7108237648df4168089d1ce5c8bae76768ae1f5a7cbda8f78a3c788123653da1a5f9294f7f410ac5a440063a7a62443efae33253b0e2bb16ed36a35b8720a1a75cd3a053a8f6415a00ecb94de70f89dff8f1e9dd5c1317a91c63f186f6e20d346da0aa4bbb9699eac716e961ac71a8048f0ad68c64b5e6ef9b3fec4e7969facea589f05d3fd1e9db885bcfea115dd393addc945f6de28f8ee1c2706e225370fc925762ef0ecb7317c28478b40b09f7b7611fc975cb19ea99226b086ca9c98895c8b86f12fa79b8086c1a3cff9f768f9b729c65121107709120f269c2ea863bda8797e77a98e3f177128fcbb4f46da9addbb1da7ef21f9aef6d0b9b1f4890d3cf764037f056e83dc7ed96a55cfab626fcf5903476d16ece901558cb0c2edc5a43cc57e4c95218c9d01e2e816d005a4f7e&auction_price=${AUCTION_PRICE}&sid=__SID__",
                    "adm":"<a class=\"_rnd_ad_128263\" style=\"display:inline-block;\"><img src=\"https://static-dev.rqmob.com/test/sa/20210804/42728fc75ca1bdadb5ab20fc3b84900b__FILE_CM____FILE_CM480_720____WEBP__.png\" width=\"320px\" height=\"50px\" /></a><script type=\"text/javascript\">window.MidasHTML = (function() {  this.$el = undefined;  this.args = {};  this.isViewable = false;  var bindClick = function() {    click_trackers = this.args.click_trackers;    target_url = this.args.target_url;    this.$el.onclick = function() {      emitTrackers(click_trackers);      window.open(target_url);    }  };  var emitTrackers = function emitTrackers(urls) {    urls.forEach(function(url) {      let obj = document.createElement(\"img\");              obj.src = url;              obj.style.display=\"none\";              this.$el.appendChild(obj);    });  };  var viewableCheck = function() {    if (this.isViewable) {  return;    }    var viewPortHeight = window.innerHeight || document.documentElement.clientHeight;    var viewPortWidth = window.innerWidth || document.documentElement.clientWidth;    var rec = this.$el.getBoundingClientRect();    this.isViewable = (rec.top >= -rec.height / 2 && rec.left >= -rec.width / 2 && rec.bottom <= viewPortHeight + rec.height / 2 && rec.right <= viewPortWidth + rec.width / 2);    if (this.isViewable) {      emitTrackers(args.impression_trackers);      bindClick();      this.isViewable = true;      clearInterval(this.timer)    }  };  var init = function(args) {    this.args = args;    this.$el = document.querySelector(\".\" + args.scope);    this.img = (this.$el.getElementsByTagName('img') || [])[0];    this.img.onload = () =>viewableCheck();    this.timer = setInterval(() =>viewableCheck(), 300);  };  return function(args) {    init(args);  }})();MidasHTML({\"click_trackers\":[\"https://midas-tracker-test.hellay.net/clk.fcg?viewid=e6d8578664e2f10e11afa8c3eb6cb3763be39af447238100277632423c9c212f3987802acb093fa8f226d2beb00ad9aa5d901a36db98e81c1c0f1639ad363decc476977f6ba1dcb36318671a7a606d34961563c37535b94719f7eb4a8d53d8b3c80d002386ea6227bc2e50cdbcaa0c40a29bee9ef33b63c3f56ae4c59790d02b2be9ce6be9598e84f92c0efb7e9fdcf311fb0326d959dbd306031f78ae6a4a34675ad8bb6e84571c015638463b14fab8eded30cabefcf16c758eac517853709909da5be52230975657723bd0182b8eb7e92423a55066d07ab9c25a2c38cb0df2af9462c41155773054912137f7f508187acdfde64036bbcc7108237648df4168089d1ce5c8bae76768ae1f5a7cbda8f78a3c788123653da1a5f9294f7f410ac5a440063a7a62443efae33253b0e2bb16ed36a35b8720a1a75cd3a053a8f6415a00ecb94de70f89dff8f1e9dd5c1317a91c63f186f6e20d346da0aa4bbb9699eac716e961ac71a8048f0ad68c64b5e6ef9b3fec4e7969facea589f05d3fd1e9db885bcfea115dd393addc945f6de28f8ee1c2706e225370fc925762ef0ecb7317c28478b40b09f7b7611fc975cb19ea99226b086ca9c98895c8b86f12fa79b8086c1a3cff9f768f9b729c65121107709120f269c2ea863bda8797e77a98e3f177128fcbb4f46da9addbb1da7ef21f9aef6d0b9b1f4890d3cf764037f056e83dc7ed96a55cfab626fcf5903476d16ece901558cb0c2edc5a43cc44e9d2501eabccb23ead\&auction_price=${AUCTION_PRICE}\&sid=__SID__\",\"https://midas-tracker-test.hellay.net/cpi_clk.fcg?log=eyJldmVudF9uYW1lIjoiQURfQ3BpQ2xpY2siLCJyZXF1ZXN0X2lkIjoiYTEyNzFlY2EtZWZhMi00ZjlmLTg5MDQtYTg1M2FmZWMxMjg5Iiwic3ViX3BsYXRmb3JtIjoiY3BpIiwiY2hhbm5lbCI6Ik9NQ19TREsiLCJjbGllbnRfaXAiOiIxLjEuMS4xIiwic2NyZWVuX3NpemUiOiIweDAiLCJuZXR3b3JrX3R5cGUiOjcsInBhY2thZ2VfbmFtZSI6InRydWVjYWxsZXIiLCJjb3VudHJ5IjoiaWQiLCJQYXJhbXMiOlt7ImNhbXBhaWduX2lkIjoyODYwLCJwb3NfaWQiOiIyMTUzIiwiYWRfaWQiOjEyODI2MywiYWRfcGFja2FnZV9uYW1lIjoiY29tLm1pZ28ubW9iaWxlIiwiY2lkIjo0NzUyMiwiY3RfY3ZyIjowLjAwMzkzNjAxNjc0OSwiYmlkX3ByaWNlIjoxNTAwMDAwMCwiZWNwbSI6NTkwNDAyNTEsImRzcF9uYW1lIjoiU2hhcmVpdCIsImF0dHJfcGxhdGZvcm0iOjEsImlzX2F1dG9fZG93bmxvYWQiOjEsImFkc2V0X2lkIjoyMzU1LCJhZF9uYW1lIjoi5bm_5ZGKMSIsImFkc2V0X25hbWUiOiJiYW5uZXIyNiIsInBoeV9wb3MiOiIyMTUzIn1dLCJtaWRhc192ZXJzaW9uIjoiMi4wIiwiYXBwX2lkIjoidHJ1ZWNhbGxlciJ9\&sid=__SID__\",\"http://ping-test.rqmob.com/click?ad=广告1\&ad_id=128263\&ad_type={ad_type}\&adpos_id=2153\&adset={adset}\&adset_id=2355\&advid=29\&amp_app_id=10053\&android_id=\&app_id=truecaller\&app_type=3\&beyla_id=\&c={c}\&c_id=47522\&campid=1440793\&channel_pkg=truecaller\&channel_pkg_ver=0\&cost_currency={cost_currency}\&cost_model={cost_model}\&cost_value={cost_value}\&country_code=id\&cut_type={cut_type}\&device_id=\&ext_info={ext_info}\&gaid=\&imei={imei}\&imsi={imsi}\&ip=1.1.1.1\&is_offline=1\&is_pre_install={is_pre_install}\&midas_camp_id=2860\&midas_traffic_type=1\&os_version=\&other_category={other_category}\&package_type={package_type}\&pkg=com.migo.mobile\&placement=2153\&platform=adshonor\&real_attrplat=1\&remote_ip=1.1.1.1\&requestid=a1271eca-efa2-4f9f-8904-a853afec1289\&sid={sid}\&site_id={site_id}\&uagent=\"],\"impression_trackers\":[\"https://midas-tracker-test.hellay.net/imp.fcg?viewid=e6d8578664e2f10e11afa8c3eb6cb3763be39af447238100277632423c9c212f3987802acb093fa8f226d2beb00ad9aa5d901a36db98e81c1c0f1639ad363decc476977f6ba1dcb36318671a7a606d34961563c37535b94719f7eb4a8d53d8b3c80d002386ea6227bc2e50cdbcaa0c40a29bee9ef33b63c3f56ae4c59790d02b2be9ce6be9598e84f92c0efb7e9fdcf311fb0326d959dbd306031f78ae6a4a34675ad8bb6e84571c015638463b14fab8eded30cabefcf16c758eac517853709909da5be52230975657723bd0182b8eb7e92423a55066d07ab9c25a2c38cb0df2af9462c41155773054912137f7f508187acdfde64036bbcc7108237648df4168089d1ce5c8bae76768ae1f5a7cbda8f78a3c788123653da1a5f9294f7f410ac5a440063a7a62443efae33253b0e2bb16ed36a35b8720a1a75cd3a053a8f6415a00ecb94de70f89dff8f1e9dd5c1317a91c63f186f6e20d346da0aa4bbb9699eac716e961ac71a8048f0ad68c64b5e6ef9b3fec4e7969facea589f05d3fd1e9db885bcfea115dd393addc945f6de28f8ee1c2706e225370fc925762ef0ecb7317c28478b40b09f7b7611fc975cb19ea99226b086ca9c98895c8b86f12fa79b8086c1a3cff9f768f9b729c65121107709120f269c2ea863bda8797e77a98e3f177128fcbb4f46da9addbb1da7ef21f9aef6d0b9b1f4890d3cf764037f056e83dc7ed96a55cfab626fcf5903476d16ece901558cb0c2edc5a43cc43ecc8431995c0eaa2ffa3eba822597172e50f\&auction_price=${AUCTION_PRICE}\&sid=__SID__\",\"https://midas-tracker-test.hellay.net/cpi_imp.fcg?log=eyJldmVudF9uYW1lIjoiQURfQ3BpU2hvdyIsInJlcXVlc3RfaWQiOiJhMTI3MWVjYS1lZmEyLTRmOWYtODkwNC1hODUzYWZlYzEyODkiLCJzdWJfcGxhdGZvcm0iOiJjcGkiLCJjaGFubmVsIjoiT01DX1NESyIsImNsaWVudF9pcCI6IjEuMS4xLjEiLCJzY3JlZW5fc2l6ZSI6IjB4MCIsIm5ldHdvcmtfdHlwZSI6NywicGFja2FnZV9uYW1lIjoidHJ1ZWNhbGxlciIsImNvdW50cnkiOiJpZCIsIlBhcmFtcyI6W3siY2FtcGFpZ25faWQiOjI4NjAsInBvc19pZCI6IjIxNTMiLCJhZF9pZCI6MTI4MjYzLCJhZF9wYWNrYWdlX25hbWUiOiJjb20ubWlnby5tb2JpbGUiLCJjaWQiOjQ3NTIyLCJjdF9jdnIiOjAuMDAzOTM2MDE2NzQ5LCJiaWRfcHJpY2UiOjE1MDAwMDAwLCJlY3BtIjo1OTA0MDI1MSwiZHNwX25hbWUiOiJTaGFyZWl0IiwiYXR0cl9wbGF0Zm9ybSI6MSwiaXNfYXV0b19kb3dubG9hZCI6MSwiYWRzZXRfaWQiOjIzNTUsImFkX25hbWUiOiLlub_lkYoxIiwiYWRzZXRfbmFtZSI6ImJhbm5lcjI2IiwicGh5X3BvcyI6IjIxNTMifV0sIm1pZGFzX3ZlcnNpb24iOiIyLjAiLCJhcHBfaWQiOiJ0cnVlY2FsbGVyIn0\&sid=__SID__\"],\"scope\":\"_rnd_ad_128263\",\"target_url\":\"https://play.google.com/store/apps/details?id=com.migo.mobile\&hl=en\"});</script>",
                    "adid": "128263",
                    "bundle": "com.migo.mobile"
                }
            ]
        }
    ],
    "cur": "USD"
}
```

