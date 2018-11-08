OpenRTB Native 动态广告API规范 版本1.1
==========
##简介

Native Ad 2014 年5月启动，隶属了IAB OpenRTB项目， 致力于开发一个开放的广告解决方案。

索引
更新日志
前言

1 简介

1.1 概述

1.2 项目历史

1.3 资源

1.4 版本历史

2 Native 概述

2.1 IAB 的六个核心

2.2 深入介绍In-Feed广告单元

2.3 数据格式

2.4 版本

2.5 自定义和扩展

3 Bid Request详解

3.1 Native 对象层级关系

4 Native Ad Request Markup 详解

4.1 Native Markup Request 对象

4.2 Asset 对象

4.3 Title 对象

4.4 Image 对象

4.5 Video 对象

4.6 Data 对象

5 Native Ad Response Markup 详解

5.1 Native Markup Response 对象

5.2 Asset 对象

5.3 Title 对象

5.4 Image 对象

5.5 Data 对象

5.6 Video 对象

5.7 Link 对象

6 Bid Request/Response 实例

6.1 Content Context, Clickout Response

Bid Request

Bid Response

6.2 Content Context, Video Response

Bid Request

Bid Response

7 参考列表/Enumerations

7.1 Native Layout IDs - 将要废弃

7.2 Native Ad Unit IDs - 将要废弃

7.3 内容分类列表

7.4 内容分类子列表

7.5 Placement 分类 IDs

7.6 Data Asset Types

7.7 Image Asset Types

8 Implementation Notes

8.1 Multi Placement Bid Requests

Change Log

-----------------------------------------------------------------------------------------------------------------------------
> **Version Date Section Link Change
-----------------------------------------------------------------------------------------------------------------------------
> 1.0 Jan 2015 Original Version

> 1.1 Oct 2015 Examples Correct ver field to a string in the examples

> 1.1 Oct 2015 Video request Added supported mime types to video request
>
> example example

> 1.1 Oct 2015 Miscellaneous typos and corrections throughout

> 1.1 Oct 2015 Native Request Further described how the ‘seq’ parameter is meant
>
> Object to be used

> 1.1 Oct 2015 Title Object Creative element standardization - created
>
> Data Asset Types recommended supported fields, lengths, and sizes for the image, title, and data asset objects to promote
>
> Image Asset Types standardization
-----------------------------------------------------------------------------------------------------------------------------

1.1 Oct 2015 Native Ad Request

Context IDs

Context Subtype IDs

Placement Type IDs

1.1 Oct 2015 Bid Request

Bid Response

rk as ‘to be deprecated’ AdUnitID and LayoutID, and replace with new
elds Context, Contextsubtype, and Placementtype to better reflect the
pes of inventory being transacted natively and the new [*In-* Feed IAB
ep
ve](http://www.iab.net/media/file/IAB_Deep_Dive_on_InFeed_Ad_Units.pdf)

ded note regarding direct-object representation in addition to
coded-string representation of native requests and responses.

Before You Get Started

This specification contains a detailed explanation of a sub-protocol
of the OpenRTB real-time bidding interface. Not all objects are
required, and each object may contain a number of optional parameters.
To assist a first time reader of the specification, we have indicated
which fields are essential to support a minimum viable real time
bidding interface for various scenarios.

A minimal viable interface should include the **required** and
recommended** parameters, but the scope for these parameters may be
limited to specific scenarios. In these cases, the scope will be
qualified with the applicable scenarios (e.g., **required for native
impressions** and **recommended for native impressions**). Conversely,
if the scope is not qualified, it applies to all scenarios.

Optional parameters may be included to ensure maximum value is derived
by the parties.

IMPORTANT:** Since **recommended** parameters are not required, they
may not be available from all supply sources. It is suggested that all
parties to OpenRTB transaction complete the integration checklist
(please refer to OpenRTB) to identify which parameters the supply side
supports in the bid request, and which parameters the demand side
requires for ad decisioning.

1 Introduction

1.1 Mission / Overview

The mission of the OpenRTB Native project is to spur standardization
and greater growth in the Real-Time Bidding (RTB) marketplace for
Native Ads by providing open industry standards for communication
between buyers of advertising and sellers of publisher inventory.

This specification is a sub-protocol of OpenRTB to allow for the
delivery of native advertising formats, as their specifics differ from
publisher to publisher. In May 2013, a separate IAB subcommittee was
formed to define the request and response structures of native ad
units;

version 1.0 was published in early 2015. Version 1.1 is designed to
fix errors, make clarifications, and promote further adoption through
refined standardization of assets and classification fields.

1.2 Credits / Project History

This document has been developed by the IAB Technology Lab’s OpenRTB
Native Subgroup. The OpenRTB Working Group mission and participation
list can be reviewed at:
[*http://www.iab.com/guidelines/real-time-bidding-rtb-project/*](http://www.iab.com/guidelines/real-time-bidding-rtb-project/)

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
Benu Shroff, Turn

Curt Larson, Sharethrough

Kuldeep Kapade, AdsNative

1.3 Resources

Resource Location

OpenRTB Website [http://openrtb.info](http://openrtb.info/)

OpenRTB Native Ads Project Page
[http://github.com/openrtb/OpenRTB/N](http://github.com/openrtb/OpenRTB/)ativeAds.htm
l

Developer / Product Manager Mailing

List

Making Sense of Programmatic Native

(“OpenRTB for native for dummies”)

ttp://groups.google.com/group/openrtb-native>

ttp://www.sharethrough.com/guides/programmati
native/](http://www.sharethrough.com/guides/programmatic-native/)

IAB Deep-Dive on In-Feed Ads
[http://www.iab.net/media/file/IAB\_Deep\_Dive\_on\_I](http://www.iab.net/media/file/IAB_Deep_Dive_on_InFeed_Ad_Units.pdf)

[nFeed\_Ad\_Units.pdf](http://www.iab.net/media/file/IAB_Deep_Dive_on_InFeed_Ad_Units.pdf)

IAB Native Advertising Playbook
[http://www.iab.net/media/file/IAB-Native-
Advertising-Playbook2.pdf](http://www.iab.net/media/file/IAB-Native-Advertising-Playbook2.pdf)

Guide to Native 1.1 [http://nativeadvertising.com/openrtb-2-4-and-
native-1-1-the-new-iab-standards-that-are-allowing-
native-ads-to-scale/](http://nativeadvertising.com/openrtb-2-4-and-native-1-1-the-new-iab-standards-that-are-allowing-native-ads-to-scale/)

1.4 Version History

Version 0.99.10.24 PUBLIC COMMENT DRAFT October 24, 2014

Version 0.99.10.27 PUBLIC COMMENT DRAFT October 27, 2014

Version 1.0.0.0 EXTERNAL DRAFT November 19, 2014

Version 1.0.0.1 EXTERNAL DRAFT December 14, 2014

Version 1.0.0.2 FINAL DRAFT January 23, 2015

Version 1.1 FINAL DRAFT March 22, 2015

2 Native Ads Basics

Native advertising is an online advertising method in which the
advertiser attempts to gain attention by providing content in the
context of the user's experience. Native ad formats match both the
form and function of the user experience in which it is placed. This
is in contrast to traditional banner or interstitials ads, which are
displayed in a separate space of predefined and universal size,
without regard to their surroundings.

2.1 IAB Core Six

The [*IAB Native Advertising Playbook
lists](http://www.iab.net/media/file/IAB-Native-Advertising-Playbook2.pdf)
six types of native ad units:

● In Feed Units

● Paid Search Units

● Recommendation Widgets

● Promoted Listings

● IAB Standard with Native Elements

● Custom / “Can’t be contained”

2.2 Deep Dive on In-Feed Ad Units

To help further define and clarify the types and categories of native
advertising, the IAB published a [*Deep Dive on In-Feed Ad Units
in](http://www.iab.net/media/file/IAB_Deep_Dive_on_InFeed_Ad_Units.pdf)
July 2015. Version 1.1 of the Native spec uses these concepts to
refine the definitions of ad types, detailed below as Context and
PlacementType, which will ultimately replace the previous LayoutID and
AdUnitID, which were defined in Native 1.0 and based on the original
Native Advertising Playbook referenced above.

Where found

Most common ad types/content objects

Most common types of links

Representative feed view

2.3 Data Format

As this specification outlines an optional sub-protocol of the main
OpenRTB protocol payload, the format must follow that of its parent.
Please refer to the main OpenRTB specification for details of various
formats that may be used

2.4 Versioning

The Native Object in the Bid Request (OpenRTB contains a “ver” field
defining the version of the

OpenRTB native extension*.

2.5 Customization and Extensions

The OpenRTB Native Ads spec allows for exchange specific customization
and extensions of the specification. Any object may contain
extensions. In order to keep extension fields consistent across
platforms, they should consistently be named “ext”.

3 Bid Request Details

RTB transactions are initiated when an exchange or other supply source
sends a bid request to a bidder. The bid request consists of a bid
request object, at least one impression object, and may optionally
include additional objects providing impression context.

3.1 Native Object Hierarchy

Following is the object hierarchy for a bid request. The new Native
Object is another optional element of the impression object, and can
be specified as an alternative to or in conjunction with a banner
object or video object.

Bid Request Object

Banner

Object

Native

 **Object

Request

Video Object



(other OpenRTB objects)

(other OpenRTB objects)

4 Native Ad Request Markup Details

4.1 Native Markup Request Object

The Native Object defines the native advertising opportunity available
for bid via this bid request. It will be included as a JSON-encoded
string in the bid request’s imp.native field or as a direct JSON
object, depending on the choice of the exchange. *While OpenRTB
2.3/2.4 supports only JSON-encoded strings, many exchanges have
implemented a formal object. Check with your integration docs.

The **Default** column dictates how optional parameters should be
interpreted if explicit values are not provided.

-------------------------------------------------------------------------------------------------------------------------------------------------------
> **Field Scope Type Default Description
-------------------------------------------------------------------------------------------------------------------------------------------------------
> ver optional string 1.1 Version of the Native Markup version in use.

> layout **recommended** integer - The Layout ID of the native ad
>
> **in 1.0, to be** unit. See the *Table of Layout IDs
>
> **deprecated** below.

> adunit **recommended** integer - The Ad unit ID of the native ad
>
> **in 1.0, to be** unit. See *Table of Ad Unit IDs
>
> **deprecated** below for a list of supported core ad units.

> context **recommended** integer - The context in which the ad
>
> appears. See *Table of Context* IDs below for a list of supported context types.

> contextsubtype optional integer - A more detailed context in which
>
> the ad appears. See *Table of* Context SubType IDs below for a list of supported context subtypes.

> plcmttype **recommended** integer - The design/format/layout of the
>
> ad unit being offered. See *Table
>
> of Placement Type IDs below for a list of supported placement types.

> plcmtcnt optional integer 1 The number of identical
>
> placements in this Layout. Refer Section 8.1 Multiplacement Bid Requests for further detail.

> seq optional integer 0 0 for the first ad, 1 for the second
>
> **ad**, and so on. Note this would generally NOT be used in combination with plcmtcnt - either you are auctioning multiple identical placements (in
>
> which case plcmtcnt&gt;1, seq=0) or you are holding separate
>
> auctions for distinct items in the feed (in which case plcmtcnt=1, seq=&gt;=1)

> assets **required** array of - An array of *Asset Objects*. Any
>
> objects bid response must comply with
-------------------------------------------------------------------------------------------------------------------------------------------------------

----------------------------------------------------------------------------------------------
        > the array of elements expressed
        >
        > in the bid request.
------- ----------------------------------- ---------- ---------------------------------------
> ext   > optional                          > object   > - This object is a placeholder that

        > may contain custom JSON agreed

        > to by the parties to support

        > flexibility beyond the standard

        > defined in this specification
----------------------------------------------------------------------------------------------

Note:** Prior to VERSION 1.1, the specification could be interpreted
as requiring the native request to have a root node with a single
field “native” that would contain the object above as its value. The
Native Markup Request Object specified above is now the root object.

4.2 Asset Object

The main container object for each asset requested or supported by
Exchange on behalf of the rendering client. Any object that is
required is to be flagged as such. Only one of the

{title,img,video,data} objects should be present in each object. All
others should be null/absent. The id is to be unique within the
AssetObject array so that the response can be aligned.

To be more explicit, it is the ID of each asset object that maps the
response to the request. So if a request for a title object is sent
with id 1, then the response containing the title should have

an id of 1.

New in version 1.1 of the spec, there are recommended
sizes/lengths/etc with some of the asset types. The goal for asset
requirements standardization is to facilitate adoption of native by
DSPs by limiting the diverse types/sizes/requirements of assets they
must have available to purchase

a native ad impression. While great diversity may exist in publishers,
advertisers/DSPs can not

be expected to provide infinite headline lengths, thumbnail aspect
ratios, etc. While we have not gone as far as creating a single
standard, we've honed in on a few options that cover the most common
cases. SSPs can deviate from these standards, but should understand
they may limit applicable DSP demand by doing so. DSPs should feel
confident that if they support these standards they'll be able to
access most native inventory.

---------------------------------------------------------------------------------------------------
> **Field Scope Type Default Description
---------------------------------------------------------------------------------------------------
> id **required** int - Unique asset ID, assigned by exchange. Typically a counter for the array.

> required optional int 0 Set to 1 if asset is required
>
> (exchange will not accept a bid without it)

> title **recommended** object - Title object for title assets. See
>
> 1 TitleObject definition.
---------------------------------------------------------------------------------------------------

img **recommended

1

ject - Image object for image assets.

See ImageObject definition.

video optional1 object - Video object for video assets.

See the Video request object definition. Note that in-stream (ie
preroll, etc) video ads are not part of Native. Native ads may contain
a video as the ad

creative itself.

data **recommended

1

ject - Data object for brand name, description, ratings, prices etc.
e DataObject definition.

ext optional object - This object is a placeholder that may contain
custom JSON agreed to by the parties to support flexibility beyond the
standard defined in this specification

1: each asset object may contain only one of title, img, data or
video.

4.3 Title Object

The Title object is to be used for title element of the Native ad.

> **Field**   > **Scope**                        > **Type**   > **Default**   > **Description
------------- ---------------------------------- ------------ --------------- -------------------------------------
> len         > **required**                     > integer    > -             > Maximum length of the text in
                                                                              > the title element.
                                                                              > **Recommended to be 25, 90, or
                                                                              > **140.
> ext         > optional                         > object     > -             > This object is a placeholder that
              > may contain custom JSON
              > agreed to by the parties to
              > support flexibility beyond the
              > standard defined in this
              > specification

4.4 Image Object

The Image object to be used for all image elements of the Native ad
such as Icons, Main Image, etc. **Recommended sizes and aspect ratios
are included in the *Image Asset Types* section.

Field Scope Type Default Description

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
> type    > optional          > integer    > -         > Type ID of the image element
                                                       >
                                                       > supported by the publisher. The publisher can display this information in an appropriate format. See Table *Image Asset* Types.
--------- ------------------- ------------ ----------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
> w       > optional          > integer    > -         > Width of the image in pixels.

> wmin    > **recommended**   > integer    > -         > The minimum requested width
                                                       >
                                                       > of the image in pixels. This option should be used for any rescaling of images by the client. Either w or wmin should be transmitted. If only w is
                                                       >
                                                       > included, it should be considered an exact requirement.

> h       > optional          > integer    > -         > Height of the image in pixels.

> hmin    > **recommended**   > integer    > -         > The minimum requested height
                                                       >
                                                       > of the image in pixels. This option should be used for any rescaling of images by the client. Either h or hmin should be transmitted. If only h is included, it should be considered an exact requirement.

> mimes   > optional          > array of   > All       > Whitelist of content MIME types
                              >            >           >
                              > strings    > types     > supported. Popular MIME types
                                           >           >
                                           > allowed   > include, but are not limited to
                                                       >
                                                       > “image/jpg” “image/gif”.

                                                       > Each implementing Exchange should have their own list of supported types in the integration docs. See
                                                       >
                                                       > [Wikipedia's MIME page f](http://en.wikipedia.org/wiki/MIME)or more information and links to all IETF RFCs.

                                                       > If blank, assume all types are allowed.

> ext     > optional          > object     > -         > This object is a placeholder that
                                                       >
                                                       > may contain custom JSON agreed to by the parties to support flexibility beyond the
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

standard defined in this specification

4.5 Video Object

The video object to be used for all video elements supported in the
Native Ad. This corresponds to the Video object of OpenRTB. Exchange
implementers can impose their own specific restrictions. Here are the
required attributes of the Video Object. For optional attributes
please refer to OpenRTB.

-----------------------------------------------------------------------------------------------------------------------------
> **Field Scope Type Default Description
-----------------------------------------------------------------------------------------------------------------------------
> mimes **required** array Content MIME types supported.
>
> of Popular MIME types include,but string are not limited to “video/x-ms-
>
> wmv” for Windows Media, and
>
> “video/x-flv” for Flash Video, or
>
> “video/mp4”. Note that native frequently does not support flash.

> minduration **required** integer - Minimum video ad duration in
>
> seconds.

> maxduration **required** integer - Maximum video ad duration in
>
> seconds.

> protocols **required** array of - An array of video protocols the
>
> integers publisher can accept in the bid response. See OpenRTB Table
>
> ‘Video Bid Response Protocols’
>
> for a list of possible values.

> ext optional object - This object is a placeholder that
>
> may contain custom JSON agreed to by the parties to support flexibility beyond the standard defined in this specification
-----------------------------------------------------------------------------------------------------------------------------

4.6 Data Object

The Data Object is to be used for all non-core elements of the native
unit such as Brand Name, Ratings, Review Count, Stars, Download count,
descriptions etc. It is also generic for future

native elements not contemplated at the time of the writing of this
document. In some cases, additional recommendations are also included
in the *Data Asset Types* table.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
> **Field Scope Type Default Description
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
> type **required** integer - Type ID of the element supported by the publisher. The publisher can display this information in an appropriate format. See *Data Asset Types* table for commonly used examples.

> len optional integer - Maximum length of the text in
>
> the element’s response.

> ext optional object - This object is a placeholder that
>
> may contain custom JSON agreed to by the parties to support flexibility beyond the standard defined in this specification
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

5 Native Ad Response Markup Details

The structure and contents of the Bid Response are the same as in the
OpenRTB standard. The difference is in how the ad creative is
returned. The native creative shall be returned as a JSON- encoded
string in the adm field of the Bid Object. Note some implementers have
chosen to use a direct object in a new field rather than JSON encoded
string.

5.1 Native Markup Response Object

The native object is the top level JSON object which identifies a
native response. The native object has following attributes:

------------------------------------------------------------------------------
> **Field Scope Type Default Description
------------------------------------------------------------------------------
> ver **optional** string “1.1” Version of the Native Markup version in use.

> assets **required** array of - List of native ad’s assets.
>
> objects

> link **required** object - Destination Link. This is default
>
> link object for the ad. Individual assets can also have a link object
------------------------------------------------------------------------------

imptrackers optional array of strings

which applies if the asset is activated(clicked). If the asset doesn’t
have a link object, the parent link object applies. See LinkObject
Definition

Array of impression tracking URLs, expected to return a 1x1 image or
4 response - typically only passed when using 3rd

party trackers.

jstracker optional string - Optional JavaScript impression tracker.
This is a valid HTML, Javascript is already wrapped in

&lt;script&gt; tags. It should be

executed at impression time where it can be supported.

ext optional object - This object is a placeholder that may contain
custom JSON agreed to by the parties to support flexibility beyond the
standard defined in this specification

Note:** Prior to VERSION 1.1, the native response’s root node was an
object with a single field “native” that would contain the object
above as its value. The Native Object specified above is now the root
object.

5.2 Asset Object

Corresponds to the Asset Object in the request. The main container
object for each asset requested or supported by Exchange on behalf of
the rendering client. Any object that is required is to be flagged as
such. Only one of the {title,img,video,data} objects should be present
in each object. All others should be null/absent. The id is to be
unique within the AssetObject array so that the response can be
aligned.

--------------------------------------------------------------------------------------------------------------------------------------------------
> **Field**   > **Scope**      > **Type**   > **Default**   > **Description
------------- ---------------- ------------ --------------- --------------------------------------------------------------------------------------
> id          > **required**   > int        > -             > Unique asset ID, assigned by exchange, must match one of the asset IDs in request.

> required    > optional       > int        > 0             > Set to 1 if asset is required.
                                                            >
                                                            > (bidder requires it to be displayed).
--------------------------------------------------------------------------------------------------------------------------------------------------

---------------------------------------------------------------------------
> title   > optional1   > object   > - Title object for title assets. See
                                   >
                                   > TitleObject definition.
--------- ------------- ---------- ----------------------------------------
> img     > optional1   > object   > - Image object for image assets.

                                   > See ImageObject definition.

> video   > optional1   > object   > - Video object for video assets.

                                   > See Video response object

                                   > definition. Note that in-stream

                                   > video ads are not part of Native.

                                   > Native ads may contain a video

                                   > as the ad creative itself.

> data    > optional1   > object   > - Data object for ratings, prices

                                   > etc.

> link    > optional    > object   > - Link object for call to actions.

                                   > The link object applies if the

                                   > asset item is activated (clicked).

                                   > If there is no link object on the

                                   > asset, the parent link object on

                                   > the bid response applies.

> ext2    > optional    > object   > - This object is a placeholder that

                                   > may contain custom JSON

                                   > agreed to by the parties to

                                   > support flexibility beyond the

                                   > standard defined in this

                                   > specification
---------------------------------------------------------------------------

1: asset object may contain only one of title, img, data or video.

2: Bidders are encouraged not to use asset.ext for exchanging text
assets. Use data.ext with custom type instead.

5.3 Title Object

Corresponds to the Title Object in the request, with the value filled
in.

--------------------------------------------------------------------------------------------------------------------------
> **Field**   > **Scope**      > **Type**   > **Default**   > **Description
------------- ---------------- ------------ --------------- --------------------------------------------------------------
> text        > **required**   > String     > -             > The text associated with the text element.

> ext         > optional       > object     > -             > This object is a placeholder that
                                                            >
                                                            > may contain custom JSON
                                                            >
                                                            > agreed to by the parties to support flexibility beyond the
--------------------------------------------------------------------------------------------------------------------------

standard defined in this specification

5.4 Image Object

Corresponds to the Image Object in the request. The Image object to be
used for all image elements of the Native ad such as Icons, Main
Image, etc.

-----------------------------------------------------------------------------------------------------------------------------
> **Field Scope Type Default Description
-----------------------------------------------------------------------------------------------------------------------------
> url **required** string - URL of the image asset.

> w **recommended** integer - Width of the image in pixels.

> h **recommended** integer Height of the image in pixels.

> ext optional object - This object is a placeholder that
>
> may contain custom JSON agreed to by the parties to support flexibility beyond the standard defined in this specification
-----------------------------------------------------------------------------------------------------------------------------

5.5 Data Object

Corresponds to the Data Object in the request, with the value filled
in. The Data Object is to be used for all miscellaneous elements of
the native unit such as Brand Name, Ratings, Review Count, Stars,
Downloads, Price count etc. It is also generic for future native
elements not contemplated at the time of the writing of this document.

-----------------------------------------------------------------------------------------------------------------------------
> **Field Scope Type Default Description
-----------------------------------------------------------------------------------------------------------------------------
> label optional string - The optional formatted string name of the data type to be displayed.

> value **required** string - The formatted string of data to
>
> be displayed. Can contain a
>
> formatted value such as “5 stars”
>
> or “\$10” or “3.4 stars out of 5”.

> ext optional object - This object is a placeholder that
>
> may contain custom JSON agreed to by the parties to support flexibility beyond the standard defined in this specification
-----------------------------------------------------------------------------------------------------------------------------

5.6 Video Object

Corresponds to the Video Object in the request, yet containing a value
of a conforming VAST

tag as a value.

> **Field**   > **Scope**      > **Type**   > **Default**   > **Description
------------- ---------------- ------------ --------------- -------------------
> vasttag     > **required**   > string     > -             > vast xml.

5.7 Link Object

Used for ‘call to action’ assets, or other links from the Native ad.
This Object should be associated to its peer object in the parent
Asset Object or as the master link in the top level Native Ad response
object. When that peer object is activated (clicked) the action should
take the user to the location of the link.

-----------------------------------------------------------------------------------------------------------------------------
> **Field Scope Type Default Description
-----------------------------------------------------------------------------------------------------------------------------
> url **required** string - Landing URL of the clickable link.

> clicktrackers optional array of - List of third-party tracker URLs to
>
> strings be fired on click of the URL.

> fallback optional string - Fallback URL for deeplink. To be
>
> (URL) used if the URL given in url is not supported by the device.

> ext optional object - This object is a placeholder that
>
> may contain custom JSON agreed to by the parties to support flexibility beyond the standard defined in this specification
-----------------------------------------------------------------------------------------------------------------------------

6 Bid Request/Response Samples

Note: for purposes of readability, these examples are written as
JSON objects directly, even though they may or may not be
string-encoded in the actual message. Also note that only the native
portion of the request/response is illustrated. For full examples,
please see the OpenRTB 2.4 parent document.

6.1 Social Context, Clickout Response

The ad might look like -

Bid Request

"native":{ "ver":”1.1”, "context":2, "contextsubtype":20,
"plcmttype":11, "plcmtcnt":1, "assets":\[

{

"id":123, "required":1, "title":{

"len":140

}

},

{

"id":128, "required":0, "img":{

"wmin":836,

"hmin":627, "type":3

}

},

{

"id":124, "required":1, "img":{

"wmin":50, "hmin":50,

"type":1

}

},

{

"id":126, "required":1, "data":{

"type":1,

"len":25

}

},

{

"id":127, "required":1, "data":{

"type":2,

"len":140

}

}

\]

}

Bid Response

"native": { "link": {

"url": "http: //i.am.a/URL"

}, "assets": \[

{

"id": 123, "required": 1, "title": {

"text": "Learn about this awesome thing"

}

},

{

"id": 124, "required": 1, "img": {

"url":["http://www.myads.com/thumbnail1.png](http://www.myads.com/thumbnail1.png)"

}

},

{

"id": 128, "required": 1, "img": {

"url":["http://www.myads.com/largethumb1.png](http://www.myads.com/largethumb1.png)"

}

},

{

"id": 126, "required": 1, "data": {

"value": "My Brand"

}

},

{

"id": 127, "required": 1, "data": {

my product."





}

alue": "Learn all about this awesome story of someone using



6.2 Content Context, Video Response

The ad might look like -

Bid Request

"native":{ "ver":”1.1”, "context":1, "contextsubtype":10,
"plcmttype":11, "plcmtcnt":1, "assets":\[

{

"id": 4, "video": {

"linearity": 1,

"minduration": 15, "maxduration": 30, "protocols": \[

2,3

\],

“mimes”: \[ “video/mp4”

\]

}

},

{

"id":123, "required":1, "title":{

"len":140

}

},

{

"id":128, "required":0, "img":{

"wmin":836, "hmin":627,

"type":3

}

},

{

"id":124, "required":1,

"img":{ "wmin":50, "hmin":50,

"type":1

}

},

{

"id":126, "required":1, "data":{

"type":1,

"len":25

}

},

{

"id":127, "required":1, "data":{

"type":2,

"len":140

}

}

\]

}

Bid Response

"native": { "link": {

"url": "http: //i.am.a/URL"

}, "assets": \[

{

"id": 4, "video": {

"vasttag": "&lt;VAST version=’2.0’&gt;&lt;/VAST&gt;"

}

},

{

"id": 123, "required": 1, "title": {

"text": "Watch this awesome thing"

}

},

{

"id": 124, "required": 1, "img": {

"url":["http://www.myads.com/thumbnail1.png](http://www.myads.com/thumbnail1.png)"

}

},

{

"id": 128, "required": 1, "img": {

"url":["http://www.myads.com/largethumb1.png](http://www.myads.com/largethumb1.png)"

}

},

{

"id": 126, "required": 1, "data": {

"value": "My Brand"

}

my product."





d": 127, "required": 1, "data": {

"value": "Watch all about this awesome story of someone using

}

}

\]

}

7 Reference Lists/Enumerations

7.1 Native Layout IDs - To Be Deprecated

Layout ID is to be deprecated in a future version and is not suggested
for new implementations.

Below is a list of the core layouts described in the introduction
above.

An implementing exchange may not support all asset variants or
introduce new ones unique to that system.

------------------------------------------------
> **Layout ID Description
------------------------------------------------
> 1 Content Wall

> 2 App Wall

> 3 News Feed

> 4 Chat List

> 5 Carousel

> 6 Content Stream
>
> 7 Grid adjoining the content

> 500+ Reserved for Exchange specific layouts.
------------------------------------------------

7.2 Native Ad Unit IDs - To Be Deprecated

Ad Unit ID is to be deprecated in a future version and is not
suggested for new implementations.

Below is a list of the core ad unit ids described by IAB here
[*http://www.iab.net/media/file/IABNativeAdvertisingPlaybook120413.pdf*](http://www.iab.net/media/file/IABNativeAdvertisingPlaybook120413.pdf)

In feed unit is essentially a layout, it has been removed from the
list. The in feed units can be identified via the layout parameter on
the request.

An implementing exchange may not support all asset variants or
introduce new ones unique to that system.

----------------------------------------------------
> **Ad Unit ID Description
----------------------------------------------------
> 1 Paid Search Units

> 2 Recommendation Widgets

> 3 Promoted Listings

> 4 In-Ad (IAB Standard) with Native Element Units
>
> 5 Custom /”Can’t Be Contained”
>
> 500+ Reserved for Exchange specific formats.
----------------------------------------------------

7.3 Context Type IDs

The context in which the ad appears - what type of content is
surrounding the ad on the page at a high level. This maps directly to
the new [*Deep Dive on In-Feed Ad
Units*.](http://www.iab.net/media/file/IAB_Deep_Dive_on_InFeed_Ad_Units.pdf)
This denotes the primary context, but does not imply other content may
not exist on the page - for example it's expected that most content
platforms have some social components, etc.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
> **Context Type ID Description
----------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------
                                    

> 1                                 > Content-centric context such as newsfeed, article, image gallery, video gallery, or similar.
                                    >
                                    > Social-centric context such as social network feed, email, chat, or similar. Product context such as product listings, details, recommendations,
                                    >
                                    > reviews, or similar.
                                    >
                                    > To be defined by the exchange.

> 2                                 

> 3                                 

> 500+                              
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

7.4 Context Sub Type IDs

Next-level context in which the ad appears. Again this reflects the
primary context, and does not imply no presence of other elements. For
example, an article is likely to contain images but is still first and
foremost an article. SubType should only be combined with the primary
context type as indicated (ie for a context type of 1, only context
subtypes that start with 1 are valid).

Context SubType ID Description

10 General or mixed content.

Primarily article content (which of course could include images, etc

11 as part of the article)

12 Primarily video content

13 Primarily audio content

14 Primarily image content

15 User-generated content - forums, comments, etc

20 General social content such as a general social network

21 Primarily email content

22 Primarily chat/IM content

30 Content focused on selling products, whether digital or physical

31 Application store/marketplace

32 Product reviews site primarily (which may sell product secondarily)

500+ To be defined by the exchange

7.5 Placement Type IDs

The FORMAT of the ad you are purchasing, separate from the surrounding
context

Placement Type ID Description

In the feed of content - for example as an item inside the organic

1 feed/grid/listing/carousel.

In the atomic unit of the content - IE in the article page or single
image

2 page

Outside the core content - for example in the ads section on the right

3 rail, as a banner-style placement near the content, etc.

Recommendation widget, most commonly presented below the article

4 content.

500+ To be defined by the exchange

7.6 Data Asset Types

Below is a list of common asset element types of native advertising at
the time of writing this spec. This list is non-exhaustive and
intended to be extended by the buyers and sellers as the format
evolves.

An implementing exchange may not support all asset variants or
introduce new ones unique to that system.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
> **Type**   > **Name**    > **Description**                                                                                               > **Format**                   > **Recommendations
>                                                                                                                                                                         
> **ID**                                                                                                                                                                  
------------ ------------- --------------------------------------------------------------------------------------------------------------- ------------------------------ ----------------------------------------------
> 1          > sponsored   > Sponsored By message where response should contain the brand name of the sponsor.                             > text                         > Required. Max 25 or longer.

> 2          > desc        > Descriptive text associated with the product or service being advertised. Longer length of text in response   > text                         > Recommended. Max
                           >                                                                                                                                              >
                           > may be truncated or ellipsed by the                                                                                                          > 140 or longer.
                           >                                                                                                                                              
                           > exchange.                                                                                                                                    

> 3          > rating      > Rating of the product being offered to the user. For example an app’s rating in an app store from 0-5.        > number formatted as string   > Optional. 0-5 integer formatted as string.

> 4          > likes       > Number of social ratings or “likes” of the product being offered to the user.                                 > number formatted as string   

> 5          > downloads   > Number downloads/installs of this product                                                                     > number formatted as string   
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

> 6      > price        > Price for product / app / in-app purchase. Value should include currency symbol in localised format.                                                                    > number formatted as string   
-------- -------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------ -------------------------------
> 7      > saleprice    > Sale price that can be used together with price to indicate a discounted price compared to a regular price. Value should include currency symbol in localised format.   > number formatted as string   
> 8      > phone        > Phone number                                                                                                                                                            > formatted string             
> 9      > address      > Address                                                                                                                                                                 > text                         
> 10     > desc2        > Additional descriptive text associated with the product or service being advertised                                                                                     > text                         
> 11     > displayurl   > Display URL for the text ad. To be used when sponsoring entity doesn’t own the content. IE sponsored by BRAND on SITE (where SITE is transmitted in this field).        > text                         
> 12     > ctatext      > CTA description - descriptive text describing a ‘call to action’ button for the destination URL.                                                                        > text                         > Optional. Max 15 or longer.
> 500+   > XXX          > Reserved for Exchange specific usage numbered above 500                                                                                                                 > Unknown                      

7.7 Image Asset Types

Below is a list of common image asset element types of native
advertising at the time of writing this spec. This list is
non-exhaustive and intended to be extended by the buyers and sellers
as the format evolves.

An implementing exchange may not support all asset variants or may
introduce new ones unique to that system.

In order to facilitate adoption, recommendations are made for both
minimum sizes and aspect ratios. We speak here of 'minimum maximum
height' or ‘max height of at least’, which means the SSP should
support a max height of at least this value. They are free to support
larger, but the DSP knows that if they have an image of this size it
will be

accepted. Note that SSPs will be responsible for sizing image to exact
size if min-max- height framework is used; exact size may not be
available at bid request time. Width is calculated from the 3
supported aspect ratios. Note we are merging the prior overlapping
type 1 and type 2 as just type 1 - to be used for app icon, brand
logo, or similar.

-----------------------------------------------------------------------------------
> **Type Name Description Recommendations
>
> **ID
-----------------------------------------------------------------------------------
> 1 Icon Icon image Optional.
>
> max height: at least 50 aspect ratio: 1:1

> 2 Logo Logo image for the **To be deprecated in future version
>
> brand/app. **- use type 1 Icon.

> 3 Main Large image preview for the At least one of 2 size variants ad required:

Small Variant:

> max height: at least 200 max width: at least 200,

267, or 382

aspect ratio: 1:1, 4:3, or

1.91:1

Large Variant:

> max height: at least 627 max width: at least 627,

836, or 1198

aspect ratio: 1:1, 4:3, or

1.91:1

> 500+ XXX Reserved for Exchange No recommendations specific usage numbered
>
> above 500
-----------------------------------------------------------------------------------

8 Implementation Notes

8.1 Multi Placement Bid Requests

If the bid request has a placement count (“plcmtcnt”) greater than 1,
then the implication is that the bidder is submitting bids to a
Generalized Second Price auction where multiple identical placements
are being offered in the same content feed or stream.

Example If a bid request is for 5 ad placements within a feed based
layout. The bidder can return

1-5 bids. The exchange runs a generalized second price auction across
these bids. The bidder can potentially win between 0-5 placements in
the auction.

An example bid response would look like

{

"id": "1234567890", "seatbid": \[{

"bid": \[{

"id": "1", "impid": "1", "price": 10,

["nurl":
"http://adserver.com/WinNoticeUrlThatReturnsNative1",](http://adserver.com/WinNoticeUrlThatReturnsNative1)

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
