**RTB Project**

OpenRTB Dynamic Native Ads API Specification Version 1

February 2015

**Introduction**

The Native Ads sub-group of the IAB OpenRTB Project assembled in May
2014 to develop a new supplementary API specification for companies
interested in an open protocol for the automated trading of Native Ads
enabled media across a broader range of platforms, devices, and
advertising solutions. This document is the culmination of those
efforts.

**About the IAB’s Networks & Exchanges Committee:**

The IAB Networks & Exchanges Committee is comprised of senior leaders
of ad networks and ad exchanges member companies. The committee is
dedicated to furthering the interests of digital ecosystem in today's
complex ad marketplace. Committee objectives are to foster the highest
standards of professionalism and accountability in relationships with
publishers, advertisers, intermediaries, and the agency community, to
develop programs that enable revenue growth, and to create best
practices that protect consumers and the industry.

The OpenRTB Project is a working group within the IAB Advertising
Technology Council.

This document can be found at [*www.iab.net*](http://www.iab.net/)

IAB Contact Information:

Brendan Riordan-Butterworth Director of Technical Standards, IAB
[*brendan@iab.net*](mailto:brendan@iab.net)

**License**

OpenRTB Specification by [*OpenRTB* is](http://openrtb.info/) licensed
under a [*Creative Commons Attribution
3.0*](http://creativecommons.org/licenses/by/3.0/)

[*License*, b](http://creativecommons.org/licenses/by/3.0/)ased on a
work at [*openrtb.info*. P](http://openrtb.info/)ermissions beyond the
scope of this license may be available at [*http://openrtb.info*.
T](http://openrtb.info/)o view a copy of this license, visit
[*http://creativecommons.org/licenses/by/3.0/*
o](http://creativecommons.org/licenses/by/3.0/)r write to Creative
Commons, 171 Second Street, Suite 300, San Francisco, CA 94105, USA.

*Table of Contents*

**Before You Get Started
...............................................................................................5**

**1
Introduction.........................................................................................................6**

1.1 Mission / Overview
..............................................................................................................................6

1.2 Credits / Project History
....................................................................................................................6

1.3
Resources..................................................................................................................................................
7

1.4 Version History
......................................................................................................................................
7

**2 Native Ads Basics
.................................................................................................7**

2.1 IAB Core Six
.............................................................................................................................................
7

2.2 Data Format
.............................................................................................................................................
9

2.3 Versioning
................................................................................................................................................9

2.4 Customization and
Extensions.........................................................................................................9

**3 Bid Request Details
............................................................................................
10**

3.1 Native Object Hierarchy
..................................................................................................................
10

**4 Native Ad Request Markup Details
.....................................................................
11**

4.1 Native Markup Request Object
.....................................................................................................
11

4.2 AssetObject
...........................................................................................................................................
12

4.3 Title Object
............................................................................................................................................
13

4.4 Image
Object.........................................................................................................................................
13

4.5 Video
Object..........................................................................................................................................
14

4.6 Data Object
............................................................................................................................................
15

**5 Native Ad Bid Response Markup
........................................................................
16**

5.1 Native Ad Creative JSON
..................................................................................................................
16

5.2 Native Object
........................................................................................................................................
16

5.3 Asset Object
..........................................................................................................................................
17

5.4 Title Object
............................................................................................................................................
18

5.5 Image
Object.........................................................................................................................................
18

5.6 Data Object
............................................................................................................................................
19

5.7 Video
Object..........................................................................................................................................
19

5.8 Link Object
............................................................................................................................................
20

**6 Bid Request/Response
Samples..........................................................................
21**

6.1 App Wall Example
..............................................................................................................................
21

*6.1.1 Bid Request*
............................................................................................................
21

*6.1.2 Bid
Response*..........................................................................................................
22

6.2 Chat List
Example...............................................................................................................................
24

*6.2.1 Bid Request*
............................................................................................................
24

*6.2.2 Bid
Response*..........................................................................................................
25

6.3 Content Stream with Video Element Example
.......................................................................
26

*6.3.1 Bid Request*
............................................................................................................
26

*6.3.2 Bid
Response*..........................................................................................................
28

6.4 Google Text
Ad.....................................................................................................................................
29

*6.4.1 Bid Request*
............................................................................................................
29

*6.4.2 Bid
Response*..........................................................................................................
30

**7 Reference Lists/Enumerations
............................................................................
31**

7.1 Native Layout IDs
...............................................................................................................................
31

7.2 Native Ad Unit IDs
..............................................................................................................................
31

7.3 Data Asset
Types.................................................................................................................................
32

7.4 Image Asset Types
.............................................................................................................................
33

**8 Implementation Notes
.......................................................................................
34**

8.1 Multi Placement Bid Requests
......................................................................................................
34

**Before You Get Started**

This specification contains a detailed explanation of a sub-protocol
of the OpenRTB real-time bidding interface. Not all objects are
required, and each object may contain a number of optional parameters.
To assist a first time reader of the specification, we have indicated
which fields are essential to support a minimum viable real time
bidding interface for various scenarios (banner, video, mobile, etc.).

A minimal viable interface should include the **required** and
**recommended** parameters, but the scope for these parameters may be
limited to specific scenarios. In these cases, the scope will be
qualified with the applicable scenarios (e.g., **required for native
impressions** and **recommended for native impressions**). Conversely,
if the scope is not qualified, it applies to all scenarios.

Optional parameters may be included to ensure maximum value is derived
by the parties.

**Required** parameters *must* be included.

**Recommended** parameters *should* be included unless there is a
compelling reason to omit them.

**Optional** parameters *may* be included at your discretion.

**IMPORTANT:** Since **recommended** parameters are not required, they
may not be available from all supply sources. It is suggested that all
parties to OpenRTB transaction complete the integration checklist
(please refer to OpenRTB 2.3) to identify which parameters the supply
side supports in the bid request, and which parameters the demand side
requires for ad decisioning.

**1 Introduction**

**1.1 Mission / Overview**

The mission of the OpenRTB Native project is to spur standardization
and greater growth in the Real-Time Bidding (RTB) marketplace for
Native Ads by providing open industry standards for communication
between buyers of advertising and sellers of publisher inventory.

This specification is a sub-protocol of OpenRTB 2.3 to allow for the
delivery of native advertising formats, as their specifics differ from
publisher to publisher. In May 2013, a separate IAB subcommittee has
been formed to define the request and response structures of native ad
units.

Establishing a true open standard for this new format will be
instrumental to native ads

adoption by app publishers and demand side platforms. With a common
framework on the buy- side, the industry as a whole will benefit from
increased demand for native ad formats.

**1.2 Credits / Project History**

Neal Richter & Avinash Shahdadpuri, Rubicon Project

Jim Butler, Nexage

Adam Morgenlender & Gabor Cselle, Twitter Narayanan Balakrishnan &
Anand Narayanan, InMobi Giuseppe Di Mauro, PubMatic

Ilya Kaplun, Visible Measures Jennifer Lum, Adelphic Wesley Biggs,
Byyd

Benoit Grouchko & Elisabeth Rotrou, Criteo

David Hernandez, AOL

Rajaraman Periasamy, RocketFuel

Jin Yu, OpenX

Anton Roslov, Phorm Andraž Tori, Zemanta Osvaldo Doederlein, Google

**1.3 Resources**

---------------------------------------------------------------------------------------------------------------------------
> **Resource Location**
---------------------------------------------------------------------------------------------------------------------------
> OpenRTB Website [http://openrtb.info](http://openrtb.info/)

> OpenRTB Native Ads Project Page [http://github.com/openrtb/OpenRTB/N](http://github.com/openrtb/OpenRTB/)ativeAds.html

> Developer / Product Manager [http://groups.google.com/group/openrtb-native](http://groups.google.com/group/openrtb-dev)
>
> Mailing List
---------------------------------------------------------------------------------------------------------------------------

**1.4 Version History**

Version 0.99.10.24 PUBLIC DRAFT October 24, 2014

Version 0.99.10.27 PUBLIC DRAFT October 27, 2014

Version 1.0.0.0 EXTERNAL DRAFT November 19, 2014

Version 1.0.0.1 EXTERNAL DRAFT December 14, 2014

Version 1.0.0.2 FINAL DRAFT January 23, 2015

**2 Native Ads Basics**

Native advertising is an online advertising method in which the
advertiser attempts to gain attention by providing content in the
context of the user's experience. Native ad formats match both the
form and function of the user experience in which it is placed. This
is in contrast to traditional banner or interstitials ads, which are
displayed in a separate space of predefined and universal size,
without regard to their surroundings.

**2.1 IAB Core Six**

The [*IAB Native Advertising Playbook*
lists](http://www.iab.net/media/file/IAB-Native-Advertising-Playbook2.pdf)
six types of native ad units:

● In Feed Units

● Paid Search Units

● Recommendation Widgets

● Promoted Listings

● IAB Standard with Native Elements

● Custom / “Can’t be contained”

Some examples for native ad formats are shown below.

**2.2 Data Format**

As this specification outlines an optional sub-protocol of the main
OpenRTB protocol payload, the format must follow that of its parent.
Please refer to the main OpenRTB specification for details of various
formats that may be used

**2.3 Versioning**

The Native Object in the Bid Request (OpenRTB 2.3) contains a “ver”
field defining the version of the OpenRTB native extension.

**2.4 Customization and Extensions**

The OpenRTB Native Ads spec allows for exchange specific customization
and extensions of the specification. Any object may contain
extensions. In order to keep extension fields consistent across
platforms, they should consistently be named ‘ext’.

**3 Bid Request Details**

RTB transactions are initiated when an exchange or other supply source
sends a bid request to a bidder. The bid request consists of a bid
request object, at least one impression object, and may optionally
include additional objects providing impression context.

**3.1 Native Object Hierarchy**

Following is the object hierarchy for a bid request. The new Native
Object is another optional element of the impression object, and can
be specified as an alternative to or in conjunction with a banner
object or video object.

**4 Native Ad Request Markup Details**

**4.1 Native Markup Request Object**

The Native Object defines the native advertising opportunity available
for bid via this bid request. It *must* be included directly in the
impression object if the impression offered for auction is a native ad
format.

The **Default** column dictates how optional parameters should be
interpreted if explicit values are not provided.

-----------------------------------------------------------------------------------------------------------------------------
> **Field Scope Type Default Description**
-----------------------------------------------------------------------------------------------------------------------------
> *ver* optional string 1 Version of the Native Markup version in use.

> *layout* **recommended** integer - The Layout ID of the native ad
>
> unit. See the table of **Native**
>
> **Layout IDs** below.

> *adunit* **recommended** integer - The Ad unit ID of the native ad
>
> unit. See the Table of **Native Ad Unit IDs** below for a list of supported core ad units.

> *plcmtcnt* optional integer 1 The number of identical
>
> placements in this Layout. Refer to Section 8.1 **Multi Placement Bid Requests**.

> *seq* optional integer 0 xx (see the **IAB Core Six** layout
>
> types). 0 for the first ad, 1 for the second ad, and so on. This is not the sequence number of the content in the stream.

> *assets* **required** array of - An array of **Asset Objects**. Any
>
> objects bid must comply with the array of elements expressed by the Exchange.

> *ext* optional object - This object is a placeholder that
>
> may contain custom JSON agreed to by the parties to support flexibility beyond the standard defined in this specification
-----------------------------------------------------------------------------------------------------------------------------

**4.2 AssetObject**

The main container object for each asset requested or supported by
Exchange on behalf of the rendering client. Any object that is
required is to be flagged as such. Only one of the

{title,,img,video,data} objects should be present in each object. All
others should be null/absent. The id is to be unique within the
AssetObject array so that the response can be aligned.

-----------------------------------------------------------------------------------------------------------------------------
> **Field Scope Type Default Description**
-----------------------------------------------------------------------------------------------------------------------------
> *id* **required** int - Unique asset ID, assigned by exchange. Typically a counter for the array.

> *required* optional int 0 Set to 1 if asset is required
>
> (exchange will not accept a bid without it)

> *title* optional1 object - Title object for title assets. See
>
> **Title Object** definition.

> *img* optional1 object - Image object for image assets.
>
> See **Image Object** definition.

> *video* optional1 object - Video object for video assets.
>
> See the **Video Object** definition.
>
> Note that in-stream video ads are not part of Native. Native ads may contain a video as the ad creative itself.

> *data* optional1 object - Data object for ratings, prices
>
> etc. See **Data Object** definition.

> *ext* optional object - This object is a placeholder that
>
> may contain custom JSON agreed to by the parties to support flexibility beyond the standard defined in this specification
-----------------------------------------------------------------------------------------------------------------------------

1: asset object may contain only one of title, img, data or video.

**4.3 Title Object**

The Title object is to be used for title element of the Native ad.

> **Field**   > **Scope**                        > **Type**   > **Default**   > **Description**
------------- ---------------------------------- ------------ --------------- -------------------------------------
> *len*       > **required**                     > integer    > -             > Maximum length of the text in
                                                                              > the title element.
> *ext*       > optional                         > object     > -             > This object is a placeholder that
              > may contain custom JSON
              > agreed to by the parties to
              > support flexibility beyond the
              > standard defined in this
              > specification

**4.4 Image Object**

The Image object to be used for all image elements of the Native ad
such as Icons, Main Image, etc.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
> **Field Scope Type Default Description**
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
> *type* optional integer - Type ID of the image element supported by the publisher. The publisher can display this information in an appropriate format. See Table **Image Asset Types** for commonly used examples.

> *w* optional integer - Width of the image in pixels.

> *wmin* **recommended** integer - The minimum requested width
>
> of the image in pixels. This
>
> option should be used for any rescaling of images by the client. Either *w* or *wmin* should be transmitted. If only *w* is
>
> included, it should be considered an exact requirement.

> *h* optional integer - Height of the image in pixels.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

*hmin* **recommended** integer - The minimum requested height of the
image in pixels. This option should be used for any rescaling of
images by the client. Either *h* or *hmin* should be transmitted. If
only *h* is included, it should be considered an exact requirement.

*mimes* optional array of strings

l types allowed

itelist of content MIME types supported. Popular MIME types include,
t are not limited to “image/jpg” “image/gif”.

ch implementing Exchange should have their own list of supported types
 the integration docs. See

ikipedia's MIME page f](http://en.wikipedia.org/wiki/MIME)or more
formation and links to all IETF RFCs.

 blank, assume all types are allowed.

*ext* optional object - This object is a placeholder that may contain
custom JSON agreed to by the parties to support flexibility beyond the
standard defined in this specification

**4.5 Video Object**

The video object to be used for all video elements supported in the
Native Ad. This corresponds to the Video object of OpenRTB 2.3.
Exchange implementers can impose their own specific restrictions. Here
are the required attributes of the Video Object. For optional
attributes please refer to OpenRTB 2.3.

> **Field**   > **Scope**      > **Type**     > **Default**   > **Description**
------------- ---------------- -------------- --------------- -----------------------------------------------------------------------------------------------------------------------------
> *mimes*     > **required**   > array                        > Content MIME types supported.
                               > of strings                   > Popular MIME types include,but are not limited to “video/x-ms- wmv” for Windows Media, and “video/x-flv” for Flash Video.

*minduration* **required** integer - Minimum video ad duration in
seconds.

*maxduration* **required** integer - Maximum video ad duration in
seconds.

*protocols* **required** array of integers

An array of video protocols the publisher can accept in the bid
sponse. See OpenRTB 2.3

Table 5.8 Video Bid Response Protocols for a list of possible values.

*ext* optional object - This object is a placeholder that may contain
custom JSON agreed to by the parties to support flexibility beyond the
standard defined in this specification

**4.6 Data Object**

The Data Object is to be used for all non-core elements of the native
unit such as Ratings, Review Count, Stars, Download count,
descriptions etc. It is also generic for future of Native elements not
contemplated at the time of the writing of this document.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
> **Field Scope Type Default Description**
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
> *type* **required** integer - Type ID of the element supported by the publisher. The publisher can display this information in an appropriate format. See Table 7.3 **Data Asset Types** for commonly used examples.

> *len* optional integer - Maximum length of the text in
>
> the element’s response.

> *ext* optional object - This object is a placeholder that
>
> may contain custom JSON
>
> agreed to by the parties to support flexibility beyond the standard defined in this specification
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**5 Native Ad Bid Response Markup**

The structure and contents of the Bid Response is the same as in the
OpenRTB standard. The difference is how ad creative is returned. The
native creative is returned as a JSON-encoded string in the *adm*
field of the Bid Object, or in response to calling the URL given in
the *nurl* field of the Bid Object.

**5.1 Native Ad Creative JSON**

The JSON returned in adm or in response to nurl is a JSON string with
the following attributes:

> **Field**   > **Scope**      > **Type**   > **Default**   > **Description**
------------- ---------------- ------------ --------------- ---------------------------
> *native*    > **required**   > object     > -             > Top level Native object

**5.2 Native Object**

The native object is the top level JSON object which identifies a
native response. The native object has following attributes

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
> **Field Scope Type Default Description**
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
> *ver* optional integer 1 Version of the Native Markup version in use.

> *assets* **required** array of - List of native ad’s assets.
>
> objects

> *link* **required** object - Destination Link. This is default
>
> link object for the ad. Individual assets can also have a link object which applies if the asset is activated (clicked). If the asset doesn’t have a link object, the parent link object applies. See LinkObject Definition

> *imptrackers\[\]* optional array of - Array of impression tracking
>
> strings URLs, expected to return a 1x1 image or 204 response - typically only passed when using 3rd
>
> party trackers.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

---------------------------------------------------------------------------------------------------------------------------------------------------------------------
> *jstracker*   > optional   > string   > - Optional JavaScript impression
                                        >
                                        > tracker. This is a valid HTML, Javascript is already wrapped in
                                        >
                                        > &lt;script&gt; tags. It should be executed at impression time where it can be supported.
--------------- ------------ ---------- -----------------------------------------------------------------------------------------------------------------------------
> *ext*         > optional   > object   > - This object is a placeholder that
                                        >
                                        > may contain custom JSON agreed to by the parties to support flexibility beyond the standard defined in this specification
---------------------------------------------------------------------------------------------------------------------------------------------------------------------

**5.3 Asset Object**

Corresponds to the Asset Object in the request. The main container
object for each asset requested or supported by Exchange on behalf of
the rendering client. Any object that is required is to be flagged as
such. Only one of the {title,img,video,data} objects should be present
in each object. All others should be null/absent. The id is to be
unique within the AssetObject array so that the response can be
aligned.

-------------------------------------------------------------------------------------------------------------------
> **Field Scope Type Default Description**
-------------------------------------------------------------------------------------------------------------------
> *id* **required** int - Unique asset ID, assigned by exchange, must match one of the asset IDs in request

> *required* optional int 0 Set to 1 if asset is required.
>
> (bidder requires it to be displayed).

> *title* optional1 object - Title object for title assets. See
>
> **Title Object** definition.

> *img* optional1 object - Image object for image assets.
>
> See **Image Object** definition.

> *video* optional1 object - Video object for video assets.
>
> See **Video Object** definition.
>
> Note that in-stream video ads are not part of Native. Native ads may contain a video as the ad creative itself.

> *data* optional1 object - Data object for ratings, prices
>
> etc.
-------------------------------------------------------------------------------------------------------------------

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
> *link*   > optional   > object   > - Link object for call to actions.
                                   >
                                   > The link object applies if the asset item is activated (clicked). If there is no link object on the asset, the parent link object on the bid response applies.
---------- ------------ ---------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------
> *ext*2   > optional   > object   > - This object is a placeholder that
                                   >
                                   > may contain custom JSON agreed to by the parties to support flexibility beyond the standard defined in this specification
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

1: asset object may contain only one of title, img, data or video.

2: Bidders are encouraged not to use asset.ext for exchanging text
assets. Use data.ext with custom type instead.

**5.4 Title Object**

Corresponds to the Title Object in the request, with the value filled
in.

> **Field**   > **Scope**                        > **Type**   > **Default**   > **Description**
------------- ---------------------------------- ------------ --------------- -------------------------------------
> *text*      > **required**                     > String     > -             > The text associated with the text
                                                                              > element.
> *ext*       > optional                         > object     > -             > This object is a placeholder that
              > may contain custom JSON
              > agreed to by the parties to
              > support flexibility beyond the
              > standard defined in this
              > specification

**5.5 Image Object**

Corresponds to the Image Object in the request. The Image object to be
used for all image elements of the Native ad such as Icons, Main
Image, etc.

> **Field**   > **Scope**      > **Type**   > **Default**   > **Description**
------------- ---------------- ------------ --------------- ---------------------------
> *url*       > **required**   > string     > -             > URL of the image asset.

> *w*     > **recommended**                  > integer   > - Width of the image in pixels.
--------- ---------------------------------- ----------- ---------------------------------------
> *h*     > **recommended**                  > integer   > Height of the image in pixels.
> *ext*   > optional                         > object    > - This object is a placeholder that
          > may contain custom JSON
          > agreed to by the parties to
          > support flexibility beyond the
          > standard defined in this
          > specification

**5.6 Data Object**

Corresponds to the Data Object in the request, with the value filled
in. The Data Object is to be used for all miscellaneous elements of
the native unit such as Ratings, Review Count, Stars, Downloads, Price
count etc. It is also generic for future of Native elements not
contemplated at the time of the writing of this document.

-----------------------------------------------------------------------------------------------------------------------------
> **Field Scope Type Default Description**
-----------------------------------------------------------------------------------------------------------------------------
> *label* optional string - The optional formatted string name of the data type to be displayed.

> *value* **required** string - The formatted string of data to
>
> be displayed. Can contain a formatted value such as “5 stars” or “\$10” or “3.4 stars out of 5”.

> *ext* optional object - This object is a placeholder that
>
> may contain custom JSON agreed to by the parties to support flexibility beyond the standard defined in this specification
-----------------------------------------------------------------------------------------------------------------------------

**5.7 Video Object**

Corresponds to the Video Object in the request, yet containing a value
of a conforming VAST tag as a value.

> **Field**   > **Scope**      > **Type**   > **Default**   > **Description**
------------- ---------------- ------------ --------------- -------------------
> *vasttag*   > **required**   > string     > -             > VAST xml.

**5.8 Link Object**

Used for ‘call to action’ assets, or other links from the Native ad.
This Object should be associated to its peer object in the parent
Asset Object or as the master link in the top level Native Ad response
object. When that peer object is activated (clicked) the action should
take the user to the location of the link.

-----------------------------------------------------------------------------------------------------------------------------
> **Field Scope Type Default Description**
-----------------------------------------------------------------------------------------------------------------------------
> *url* **required** string - Landing URL of the clickable link.

> *clicktrackers\[\]* optional array of - List of third-party tracker URLs to
>
> strings be fired on click of the URL.

> *fallback* optional string - Fallback URL for deeplink. To be
>
> (URL) used if the URL given in url is not
>
> supported by the device.

> *ext* optional object - This object is a placeholder that
>
> may contain custom JSON agreed to by the parties to support flexibility beyond the standard defined in this specification
-----------------------------------------------------------------------------------------------------------------------------

**6 Bid Request/Response Samples**

**6.1 App Wall Example**

The ad might look like -

***6.1.1 Bid Request***

{

"native": { "assets": \[

{

"id": 1, "required": 1, "title": {

"len": 30

}

},

{

"id": 2, "required": 0, "data": {

"type": 3,

"len": 5

}

},

{

"id": 3, "required": 1, "img": {

"type": 1, "w": 64, "h": 64, "mimes": \[

"image/png"

\]

}

},

{

"id": 4, "required": 0, "data": {

"type": 2,

"len": 10

}

}

\]

}

}

***6.1.2 Bid Response***

{

"native": { "ver": 1, "link": {

"url": "deeplink://deeplink/url/into/app", "fallback": "http:
//i.am.a/URL", "clicktrackers": \[

"http: //a.com/a",

"http: //b.com/b"

\]

},

"imptrackers": \[

"http: //a.com/a",

"http: //b.com/b"

\],

"assets": \[

{

"id": 1, "title": {

"text": "InstallBOA"

},

"link": {

"url": "http: //i.am.a/URL"

}

},

{

"id": 2, "data": {

"value": 5

}

},

{

"id": 3, "img": {

"url": "http: //cdn.mobad.com/ad.png", "w": 64,

"h": 64

}

},

{

"id": 4, "data": {

"value": "Install"

},

"link": {

"url": "http: //i.am.a/URL"

}

}

\]

}

}

**6.2 Chat List Example**

***6.2.1 Bid Request***

{

"native": { "layout": 4, "assets": \[

{

"id": 1, "required": 1, "title": {

"len": 30

}

},

{

"id": 2, "required": 0, "data": {

"type": 2,

"len": 100

}

},

{

"id": 3, "required": 1, "img": {

"type": 1, "w": 64, "h": 64, "mimes": \[

"image/png"

\]

}

}

\]

}

}

***6.2.2 Bid Response***

{

"native": { "ver": 1, "link": {

"url": "deeplink://deeplink/url/into/app", "fallback": "http:
//i.am.a/URL", "clicktrackers": \[

"http: //a.com/a",

"http: //b.com/b"

\]

},

"imptrackers": \[

"http: //a.com/a", "http: //b.com/b"

\],

"assets": \[

{

"id": 1, "title": {

"text": "Install BOA"

}

},

{

"id": 2, "data": {

"value": "Manage Finances on your phone"

}

},

{

"id": 3, "img": {

["url": "http://cdn.mobad.com/ad.png",](http://cdn.mobad.com/ad.png)

"w": 64, "h": 64

}

}

\]

}

}

**6.3 Content Stream with Video Element Example**

***6.3.1 Bid Request***

{

"native": { "layout": 6,

"assets": \[

{

"id": 1, "required": 1, "title": {

"len": 30

}

},

{

"id": 2, "required": 0, "data": {

"type": 3,

"len": 10

}

},

{

"id": 3, "required": 1, "img": {

"w": 64, "h": 64, "mimes": \[

"image/png"

\]

}

},

{

"id": 4, "video": {

"linearity": 1, "minduration": 15, "maxduration": 30, "protocols": \[

"VAST 2.0"

\]

}

},

{

"id": 5, "required": 0, "data": {

"type": 2,

"len": 10

}

}

\]

}

}

***6.3.2 Bid Response***

{

"native": { "ver": 1, "link": {

"url": "deeplink://deeplink/url/into/app", "fallback": "http:
//i.am.a/URL", "clicktrackers": \[

"http: //a.com/a",

"http: //b.com/b"

\]

},

"assets": \[

{

"id": 1, "title": {

"text": "Install BOA"

}

},

{

"id": 2, "data": {

"value": 5

}

},

{

"id": 3, "img": {

["url": "http://cdn.mobad.com/ad.png", "w":
1200,](http://cdn.mobad.com/ad.png)

"h": 627

}

},

{

"id": 4, "video": {

"vasttag": "&lt;VAST version=’2.0’&gt;&lt;/VAST&gt;"

}

},

{

"id": 5, "data": {

"value": "Click"

},

"link": {

["url": "http://i.am.a/URL"](http://i.am.a/URL)

}

}

\]

}

}

**6.4 Google Text Ad**

An Google text ad with title, description 1, description 2 and display
url can be represented as -

***6.4.1 Bid Request***

{

"native": { "assets": \[

{

"id": 1, "title": {

"len": 25

}

},

{

"id": 2, "data": {

"type": 2,

"len": 35

}

},

{

"id": 3, "data": {

"type": 10,

"len": 35

}

},

{

"id": 4, "data": {

"type": 11, "len": 35

}

}

\]

}

}

***6.4.2 Bid Response***

{

"native": { "ver": 1, "link": {

"url": "deeplink://deeplink/url/into/app", "fallback": "http:
//i.am.a/URL", "clicktrackers": \[

"http: //a.com/a",

"http: //b.com/b"

\]

},

"assets": \[

{

"id": 1, "title": {

"text": "Plasma Television"

}

},

{

"id": 2, "data": {

"value": "Huge range of equipment on sale"

}

},

{

"id": 3, "data": {

"value": "Free delivery. Order now."

}

},

{

"id": 4, "data": {

"value": "mybestplasmatvstore.com"

}

}

\]

}

}

**7 Reference Lists/Enumerations**

**7.1 Native Layout IDs**

Below is a list of the core layouts described in the introduction
above.

An implementing exchange may not support all asset variants or
introduce new ones unique to that system.

--------------------------------------------------
> **Layout ID Description**
--------------------------------------------------
> *1* Content Wall

> *2* App Wall

> *3* News Feed
>
> *4* Chat List
>
> *5* Carousel

> *6* Content Stream

> *7* Grid adjoining the content
>
> *500+* Reserved for Exchange specific layouts.
--------------------------------------------------

**7.2 Native Ad Unit IDs**

Below is a list of the core ad unit ids described by IAB here
[*http://www.iab.net/media/file/IABNativeAdvertisingPlaybook120413.pdf*](http://www.iab.net/media/file/IABNativeAdvertisingPlaybook120413.pdf)

In feed unit is essentially a layout, it has been removed from the
list. The in feed units can be identified via the layout parameter on
the request.

An implementing exchange may not support all asset variants or
introduce new ones unique to that system.

------------------------------------------------------
> **Ad Unit ID Description**
------------------------------------------------------
> *1* Paid Search Units

> *2* Recommendation Widgets

> *3* Promoted Listings

> *4* In-Ad (IAB Standard) with Native Element Units
>
> *5* Custom /”Can’t Be Contained”

> *500+* Reserved for Exchange specific formats.
------------------------------------------------------

**7.3 Data Asset Types**

Below is a list of common asset element types of native advertising at
the time of writing this spec. This list is non-exhaustive and
intended to be extended by the buyers and sellers as the format
evolves.

An implementing exchange may not support all asset variants or
introduce new ones unique to that system.

---------------------------------------------------------------------------------------------------------------
> **Type Name Description Format**
>
> **ID**
---------------------------------------------------------------------------------------------------------------
> *1* sponsored Sponsored By message where response should text contain the brand name of the sponsor.
>
> *2* desc Descriptive text associated with the product or text service being advertised.

> *3* rating Rating of the product being offered to the user. number
>
> For example an app’s rating in an app store from formatted as
>
> 0-5. string

> *4* likes Number of social ratings or “likes” of the product number being offered to the user. formatted as

string
---------------------------------------------------------------------------------------------------------------

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
> *5* downloads Number downloads/installs of this product number formatted as string
>
> *6* price Price for product / app / in-app purchase. Value number should include currency symbol in localised formatted as format. string
>
> *7* saleprice Sale price that can be used together with price to number indicate a discounted price compared to a regular formatted as price. Value should include currency symbol in string localised format.
>
> *8* phone Phone number formatted string
>
> *9* address Address text
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
> *10* desc2 Additional descriptive text associated with the text product or service being advertised

> *11* displayurl Display URL for the text ad text

> *12* ctatext CTA description - descriptive text describing a ‘call text to action’ button for the destination URL.

> *500+* XXX Reserved for Exchange specific usage numbered Unknown above 500
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**7.4 Image Asset Types**

Below is a list of common image asset element types of native
advertising at the time of writing this spec. This list is
non-exhaustive and intended to be extended by the buyers and sellers
as the format evolves.

An implementing exchange may not support all asset variants or
introduce new ones unique to that system.

**Type**

**ID**

Name Description**

> *1* Icon Icon image
----------------------------------------------------------------------
> *2* Logo Logo image for the brand/app.
> *3* Main Large image preview for the ad
> *500+* XXX Reserved for Exchange specific usage numbered above 500

**8 Implementation Notes**

**8.1 Multi Placement Bid Requests**

If the bid request has a placement count (“plcmtcnt”) greater than 1,
then the implication is that the bidder is submitting bids to a
Generalized Second Price auction where multiple identical placements
are being offered in the same content feed or stream.

Example: If a bid request is for 5 ad placements within a feed based
layout. The bidder can return 1-5 bids. The exchange runs a
generalized second price auction across these bids. The bidder can
potentially win between 0-5 placements in the auction.

An example bid response would look like

{

"id": "1234567890", "seatbid": \[{

"bid": \[{

"id": "1", "impid": "1", "price": 10,

"nurl": "http://adserver.com/WinNoticeUrlThatReturnsNative1",

"adm":"&lt;native response&gt;"

},

"bid": \[{

"id": "2", "impid": "1", "price": 20,

["nurl":
"http://adserver.com/WinNoticeUrlThatReturnsNative2"](http://adserver.com/WinNoticeUrlThatReturnsNative2)

"adm":"&lt;native response&gt;"

}\]

}\]

}
