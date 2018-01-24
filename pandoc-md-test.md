<div id="page">

<div id="main" class="aui-page-panel">

<div id="main-header">

<div id="breadcrumb-section">

1.  <span>[Roku SDK Documentation](index.html)</span>
2.  <span>[Roku SDK
    Documentation](Roku-SDK-Documentation_1611307.html)</span>

</div>

# <span id="title-text"> Roku SDK Documentation : Roku Search </span>

</div>

<div id="content" class="view">

<div class="page-metadata">

Created by <span class="author"> Bill Reid</span>, last modified by
<span class="editor"> Aanchal Gupta</span> on Dec 20, 2017

</div>

<div id="main-content" class="wiki-content group">

<span style="color: rgb(128,0,128);">**Table of Contents**</span>

<div class="toc-macro rbtoc1516756438815">

  - [Roku Search Algorithm](#RokuSearch-RokuSearchAlgorithm)
      - [Content Details Screen](#RokuSearch-ContentDetailsScreen)
      - [Content Provider List
        Order](#RokuSearch-ContentProviderListOrder)
      - [Content Meta-Data
        Database](#RokuSearch-ContentMeta-DataDatabase)
  - [Integrating Your VOD Channel Content Into Roku
    Search](#RokuSearch-IntegratingYourVODChannelContentIntoRokuSearch)
  - [Search Artwork](#RokuSearch-SearchArtwork)
      - [Requirements](#RokuSearch-Requirements)
      - [Search Artwork Templates](#RokuSearch-SearchArtworkTemplates)
  - [Deep Linking](#RokuSearch-DeepLinking)
  - [Testing your channel for
    search](#RokuSearch-Testingyourchannelforsearch)
      - [XML Feed Schemas](#RokuSearch-XMLFeedSchemas)
      - [Optional security](#RokuSearch-Optionalsecurity)
          - [Schemas Using the TMS
            Database](#RokuSearch-SchemasUsingtheTMSDatabase)
          - [Schemas Without the TMS
            Database](#RokuSearch-SchemasWithouttheTMSDatabase)
          - [XML Validation](#RokuSearch-XMLValidation)
  - [Search Meta-Data](#RokuSearch-SearchMeta-Data)
      - [Movie Meta-Data (TMS)](#RokuSearch-MovieMeta-Data\(TMS\))
      - [Movie Meta-Data
        (non-TMS)](#RokuSearch-MovieMeta-Data\(non-TMS\))
      - [TV Meta-Data (TMS)](#RokuSearch-TVMeta-Data\(TMS\))
      - [TV Meta-Data (non-TMS)](#RokuSearch-TVMeta-Data\(non-TMS\))
  - [Acceptable Genres](#RokuSearch-AcceptableGenres)
  - [Acceptable Parental Ratings](#RokuSearch-AcceptableParentalRatings)

</div>

-----

Roku Search provides another way to convert Roku users into customers of
your VOD channel, besides the Roku Channel Store. Roku Search is located
on the main menu of the Roku home-screen, and allows Roku users to
search for a particular movie, TV show/special, or
actor/actress/director. Roku Search then allows users to see a list of
providers and launch the provider's channel and go directly to the
selected piece of content.

By participating in the Roku Search program, all of your content that
matches any search, and your channel, is offered automatically to all
Roku users who use Roku Search and can use your channel.   (Search
results are not shown outside the country specified)

After completing a search, the user can also add the results to My Feed,
which provides updates on the content they have expressed an interest in
previously. 

<span class="confluence-embedded-file-wrapper">![](attachments/3737679/3737876.jpg)</span>

Roku Search is only available in English, and only available in the
U.S., Canada (English only), Ireland and the U.K. Roku Search only
supports full-length movies and TV series, episodes, and specials. Roku
Search does not support short-form or clip content.

## Roku Search Algorithm

The algorithm for Roku Search is:

1.  A user selects Search from the Roku home-screen main menu.
2.  The user is presented with a keypad to enter a search string and a
    panel of search results.   Initially, the user also is presented
    with a list of previous search results.   The user does have the
    option of clearing their search history.
3.  As the user enters the search string, the system suggests search
    results from the Roku Search database that match. The user can
    select any search result at any
    time.  
    <span class="confluence-embedded-file-wrapper">![](attachments/3737679/3737710.jpg)</span>
4.  After the user selects an actor or a director,  a list of content
    titles that were done by that person appear.
        
    <span class="confluence-embedded-file-wrapper confluence-embedded-manual-size">![](attachments/3737679/4259934.jpg)</span>
5.  After the user selects a title then a content details screen will
    appear.   The user can also select a title directly in step \#3.  
    This screen has a list of providers.
6.  If the title is a series then a list of seasons appears.     Once
    the user selects a season then a list of providers will
    appear.   
    <span class="confluence-embedded-file-wrapper confluence-embedded-manual-size">![](attachments/3737679/4259936.jpg)</span>
7.  Once the user selects a provider, that provider's channel is
    launched and you go directly to the selected piece of content.
8.  If the user does not have the provider's channel installed  it will
    prompt the user to install the channel.

### Content Details Screen

The content details screen includes:

  - artwork, such as DVD cover art, or TV show banners
  - content information, such title, description, rating, actors,
    director, run time, production year, genre
  - a selectable list of content provider items for the movie or TV
    show, including an option to add the movie or TV show to the
    personal My Feed of the user

Each item in the content provider list includes:

  - the logo of the content provider
  - the terms to acquire the movie or TV show
  - an indication if the movie or TV show is available in HD
  - the number of episodes available for TV shows
  - a checkmark if the user has installed the content provider VOD
    channel on their Roku Media Player

Each item, when selected by the user, will "deep link" into the content
provider channel. The link could be to a content provider movie details
screen, TV season episode list screen, or TV episode details screen, or
other screen, depending on the content selected, the content provider,
and whether the user has installed the content provider VOD
channel.

<span class="confluence-embedded-file-wrapper">![](attachments/3737679/3737711.jpg)</span>

### Content Provider List Order

Content providers are sorted on the content details screen in the
following order\*:

1.  Whether or not the channel is installed (represented by the
    checkmark icon)
2.  By price (Free, Authenticated or Subscription, Purchase/Rental
    price)

Search results for TV episodes results are ordered by:

1.  Whether or not the channel is installed (represented by the check
    mark icon)
2.  Whether the channel has the latest episode
3.  By number of episodes available

When more than one content provider meets the same criteria, the order
is randomized.

\* There are very few exceptions.

### Content Meta-Data Database

User search strings are compared to a master database of content
meta-data maintained by Roku. Content providers who participate in the
Roku Search program must supply Roku with an XML file listing their
currently-available content and content meta-data, which is then
incorporated into the Roku master database four times a day.   Currently
content is pulled at 1:00am, 7:00am, 1:00pm and 7:00pm.   The process of
reconciling all of the data sources is quite long so we ask you to give
us 24 hours for changes to propagate to production.

## Integrating Your VOD Channel Content Into Roku Search

This is what you need to do to participate in the Roku Search program:

  - Create an up-to-date XML feed of your currently available content. –
    see below
  - Create search artwork (store and list artwork) – see below
  - Create a non-certified channel with the name \<CHANNEL\>SearchBeta
    where \<CHANNEL\> is the name of your production channel.   When I
    say "name" I mean the channel name used when you upload the channel.
      Not the name in the manifest.
       
    <span class="confluence-embedded-file-wrapper confluence-embedded-manual-size">![](attachments/3737679/4260366.png)</span>  
  - Submit an up-to-date XML feed of your available content to
    Roku using the correct XML schema.   Here is the URL:
    <https://developer.roku.com/search/feed_validator>.   We do not
    accept feeds which do not pass the validator.
  - Send email
    to <span style="color: rgb(0,0,0);">dl.searchsubmit@roku</span><span style="color: rgb(0,0,0);">.com
    with your non-certified channel code, your feed URL, and your icons.
      Tell us if you think your deep linking already works.</span>
  - <span style="color: rgb(0,0,0);">We will configure your XML feed to
    your non-certified channel and then you can test deep linking.  
     Because non-certified channels publish automatically you can
    rapidly iterate to get the feature working.   </span>
  - <span style="color: rgb(0,0,0);">Once everything is working on the
    non-certified channel and any changes made have been published to
    the public channel then we can enable search on your public channel.
      There is a cert process that we do to make sure everything
    works.</span>
  - <span style="color: rgb(0,0,0);"><span style="color: rgb(0,0,0);">Make
    sure you have the infrastructure in place to keep the search feed
    up-to-date.   </span></span>

## Search Artwork

You must provide artwork to display in the Roku Search interface. There
are two formats, a small icon of your logo for your item in the content
providers list on the content details screen and a larger, square logo
used for randomized teasers in the search screen. This artwork must look
similar to the artwork used to represent your channel in the Roku
Channel Store, with your logo and brand colors.

#### **Requirements**

  - PNG format only
  - Square corners for the teaser logo
  - Rounded corners for the small logo
  - 143w x 113h pixels for the teaser logo
  - 165w x 60h pixels for the small logo 
  - Use an inner shadow effect for the teaser logo to conform to the
    default Scene Graph list item focus appearance
  - If a gradient is applied to the artwork, use a gradient with the
    light source at the top of the artwork 

#### Search Artwork Templates

The following PSD templates can be used in an illustration tool to
create the Roku Search artwork.

  - **Channel Store Teaser Artwork,
    FHD: [searchProviderTile\_FHD.psd](attachments/3737679/5440660.psd)**
  - **Content Provider List Item Artwork,
    FHD: [partnerLogo\_template\_FHD.psd](attachments/3737679/5440661.psd)**

## Deep Linking

Your channel will need to be updated to support deep linking with the
play IDs provided in your feed.    Deep linking works by sending command
line arguments, via the roAssociativeArray named "args",  your channel.
  Args should be parsed by the channel launch time and the correct
content brought up.   Just launching the channel will not pass
certification.

<div class="code panel pdl" style="border-width: 1px;">

<div class="codeHeader panelHeader pdl" style="border-bottom-width: 1px;">

**Play IDs and Deep Linking Example**

</div>

<div class="codeContent panelContent pdl">

``` brush: vb; gutter: false; theme: Confluence
Function Main(args as Dynamic) as void     
   if (args <> invalid)
        contentID    = args.contentID
        contentType  = args.mediatype
        ...    
   End Function
```

</div>

</div>

 

**A tricky item.  **In your feed, there is a tag called **PlayID** which
gets passed into the channel as** ContentID.  **

**A 2nd tricky item.  **If in search, the user selects "series", then a
"season", it will not deep link using the PlayID for the series.   It
will instead use one of the PlayIDs for one of the episodes in the
selected season.

**A 3<sup>rd</sup> tricky item**.  When the deep link comes through, it
has a contentType of “season” not a “series.” 

Here is a snippet from a working XML
feed:

<div class="code panel pdl" style="border-width: 1px;">

<div class="codeHeader panelHeader pdl" style="border-bottom-width: 1px;">

**Feed snippit**

</div>

<div class="codeContent panelContent pdl">

``` brush: java; gutter: false; theme: Confluence
<movie tmsId="MV003837380000">
    <title>The Adventures of Chris Fable</title>
    <videos>
        <video>
            <region>us</region>
            <playId>bbtv://vod/asset_id/2dd3cf6fcf644453a0792cd1a60c3be2</playId>
            <viewOptions>
                <option>
                    <quality>SD</quality>
                    <license>rental</license>
                    <price>1.99</price>
                    <currency>USD</currency>
                </option>
            </viewOptions>
        </video>
    </videos>
</movie>
```

</div>

</div>

Here is what is the "args" passed in when the piece of content above was
selected:

<div class="code panel pdl" style="border-width: 1px;">

<div class="codeHeader panelHeader pdl" style="border-bottom-width: 1px;">

**content of args**

</div>

<div class="codeContent panelContent pdl">

``` brush: java; gutter: false; theme: Confluence
splashTime: 1973
source: meta-search
contentid: bbtv://vod/asset_id/2dd3cf6fcf644453a0792cd1a60c3be2
instant_on_run_mode: foreground
mediatype: movie
action: display
lastExitOrTerminationReason: EXIT_UNKNOWN
```

</div>

</div>

This contentID means something to this channel's developer.    As far as
Roku is concerned it is just a string  however.   Some channels use
numbers, some user URLs, some use name/value pairs delimited by "|".

## Testing your channel for search

There are two ways to test.   The first one is to manually trigger the
deep link via an ECP command.    This boils down to a "curl" to the ECP
port where you specify the ContentID and the MediaType as parameters to
the URL.    See [External Control
API\#3.3ImplementingDeepLinkinginaChannel](External-Control-API_1611563.html#ExternalControlAPI-3.3ImplementingDeepLinkinginaChannel) 

The other way to test is with a live system.   We use the \<channel
name\>PrivateSearchBeta channel you created for live, end-to-end
testing.  We configure your feed to point to this channel when we test
it.   Because non-certified channels are published automatically you can
make changes, upload them, update your system, and see your changes in
production immediately.      

### <span style="line-height: 1.5;">XML Feed Schemas</span>

You must provide an up-to-date XML feed web location for your VOD
channel.

### Optional security

The only security we support for the XML feed is basic username and
password authentication in the HTTP request-header.

 

Your XML feed should contain content meta-data for each title in your
catalog, as described in [Search
Meta-Data](#RokuSearch-SearchMeta-Data). The XML files from your feed
location will be uploaded and incorporated into the Roku Search master
database four times a day. 

There are two schemas used for XML feeds to the Roku master database:

  - Schemas Using the Gracenote TMS Database
  - Schemas Without the TMS Database

The two differ in the amount of meta-data you must supply, and whether
you need to supply a TMS ID that corresponds to the deep-link playID(s)
of your content item(s).

#### Schemas Using the TMS Database

One schema incorporates meta-data from the Gracenote TMS database, a
database of movies and TV shows. To use this database, you must supply
the minimal data required to allow Roku users to purchase and play your
content items, such as playID, pricing, and so forth. You must also
identify the TMS ID for the corresponding content item(s) you make
available to Roku users.

The TMS ID is a 14-character scheme used to uniquely identify movie and
TV show content (for example, MV123456780000). These IDs are used to
match titles in your currently-offered content catalog back to specific
title entries in the master Roku Search database.

The first two characters in the ID represent the unique ID domain
applied to the program record:

<div class="table-wrap">

| ID | Domain                                                   |
| -- | -------------------------------------------------------- |
| MV | Movie (theatrical, made-for-television, direct-to-video) |
| SH | TV Show                                                  |
| EP | TV Episode                                               |

</div>

The next 12 characters will be the unique numeric value within that
database. This implies that the numeric sequence could be identical
across the four ID domains.

By using the TMS IDs, Roku only needs limited information from you to
display full content meta-data. Please contact Gracenote directly about
acquiring IDs for your
content.

<div class="confluence-information-macro confluence-information-macro-note">

<span class="aui-icon aui-icon-small aui-iconfont-warning confluence-information-macro-icon"></span>

<div class="confluence-information-macro-body">

If the meta-data you provide for a title appears to match a title we
already have in our database, we will display only the TMS meta-data.

</div>

</div>

#### Schemas Without the TMS Database

The second schema requires you to provide more meta-data.  You will also
provide your own unique, immutable playID for each item instead of the
TMS-ID.

#### XML Validation

Roku cannot incorporate your XML files into the master database unless
it conforms to the correct XML schema. Refer to [Search
Meta-Data](#RokuSearch-SearchMeta-Data) for details on the required and
optional meta-data for Roku Search. The following are two sample XML
files, one that uses the TMS database, the other without the TMS
database:

  - TMS:
    [roku-parter-content-feed-example-tms-id\_2015-06-01.xml](attachments/3737679/3737768.xml)
  - Non-TMS:
    [roku-partner-content-feed-example-non-tms-id-2015-06-02.xml](attachments/3737679/3737767.xml)

Make sure to validate your XML feed against one of the two following XML
schema (`.xsd`) files before submitting it to Roku:

  - TMS:
    [partner-feed-tms-validator.xsd](attachments/3737679/4259946.xsd)
  - Non-TMS:
    [partner-feed-validator.xsd](attachments/3737679/4259947.xsd)

## Search Meta-Data

The following tables describe the required and optional meta-data fields
used in the XML feed files for Roku
Search.

<div class="confluence-information-macro confluence-information-macro-tip">

<span class="aui-icon aui-icon-small aui-iconfont-approve confluence-information-macro-icon"></span>

<div class="confluence-information-macro-body">

Although many fields are optional, the more meta-data you include, the
greater the probability your content will be returned in the user search
results. 

</div>

</div>

### Movie Meta-Data (TMS)

<div class="table-wrap">

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>movies/movie/@tmsId</p></td>
<td><p>Required</p></td>
<td><p>Gracenote TMS ID for a specific movie.</p></td>
</tr>
<tr class="even">
<td><p>... movie/title</p></td>
<td><p>Optional</p></td>
<td><p>Optional, but very helpful</p></td>
</tr>
<tr class="odd">
<td><p>… movie/videos/video</p></td>
<td><p>Required</p></td>
<td><p>The videos element lists all the video content items corresponding to the specific movie identified by the movie/@tmsId attribute. Each child video element must have a unique play ID, and provide meta-data indicating availability, pricing and other specifics about that specific video content item available on your channel.</p></td>
</tr>
<tr class="even">
<td><p>… video/playId</p></td>
<td><p>Required</p></td>
<td><p>A value you provide for each title in your XML feed that we will pass back to your channel when a user selects your service as a provider for a specific title (see <a href="#RokuSearch-PlayIDsandDeepLinking">Play IDs and Deep Linking</a>).</p></td>
</tr>
<tr class="odd">
<td><p>… video/region</p></td>
<td><p>Optional</p></td>
<td><p>Can be one of the following 2-character ISO codes (can be either uppercase or lowercase):</p>
<ul>
<li>us (default)</li>
<li>US (default)</li>
<li>gb</li>
<li>GB</li>
<li>ca</li>
<li>CA</li>
<li>ie</li>
<li>IE</li>
</ul></td>
</tr>
<tr class="even">
<td><p>… video/viewOptions/option</p></td>
<td><p>Required</p></td>
<td><p>Used to provide video viewing options.</p></td>
</tr>
<tr class="odd">
<td><p>… option/quality</p></td>
<td><p>Required</p></td>
<td><p>The resolution of the video content item. Must be one of the following (can either be uppercase or lowercase):</p>
<ul>
<li>sd</li>
<li>SD</li>
<li>hd</li>
<li>HD</li>
<li>hd+</li>
<li>HD+</li>
<li>UHD</li>
</ul></td>
</tr>
<tr class="even">
<td><p>… option/license</p></td>
<td><p>Required</p></td>
<td><p>The type of license terms for the video content item. Must be one of the following (can either be initial capitalization or all lowercase):</p>
<ul>
<li>free</li>
<li>Free</li>
<li>rental</li>
<li>Rental</li>
<li>purchase</li>
<li>Purchase</li>
<li>subscription</li>
<li>Subscription</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>… option/price</p></td>
<td><p>Required if option/license is set to purchase or rental, defaults to 0.00 if option/license is set to subscription or free</p></td>
<td><p>Price, that must include two decimal point places, such as &quot;1.90&quot;, &quot;1.99&quot;, or &quot;2.00&quot;. If the price is &quot;0.00&quot;, set option/license to &quot;subscription&quot; or &quot;free&quot; rather than setting option/price to &quot;0.00&quot;, and option/price will be set to &quot;0.00&quot; by default.</p></td>
</tr>
<tr class="even">
<td><p>… option/currency</p></td>
<td><p>Optional</p></td>
<td><p>The type of currency that denominates the price. Must be one of the following (can either be uppercase or lowercase):</p>
<ul>
<li>usd (default)</li>
<li>USD (default)</li>
<li>gbp</li>
<li>GBP</li>
<li>cad</li>
<li>CAD</li>
</ul></td>
</tr>
</tbody>
</table>

</div>

### Movie Meta-Data (non-TMS)

<div class="table-wrap">

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>movies/movie/@id</p></td>
<td><p>Required</p></td>
<td><p>Your immutable reference ID for that movie.</p>
<div class="confluence-information-macro confluence-information-macro-warning">
<span class="aui-icon aui-icon-small aui-iconfont-error confluence-information-macro-icon"></span>
<div class="confluence-information-macro-body">
Once assigned to a content item, you cannot change the reference ID or use it for another content item in the Roku Search meta-data.
</div>
</div></td>
</tr>
<tr class="even">
<td><p>... movie/titles/title</p></td>
<td><p>Required</p></td>
<td><p>Movie title. We use this value for matching. Please don’t include extra information like year, version label, and so forth.</p></td>
</tr>
<tr class="odd">
<td><p><span>… </span>title/@language</p></td>
<td><p>Optional</p></td>
<td><p>Default: en</p>
<p>(Roku Search is currently only available in English.)</p></td>
</tr>
<tr class="even">
<td><p>… movie/images/image</p></td>
<td><p>Optional</p></td>
<td><p>Although this is optional, we recommend that you include it for items where you unsure about whether we can or cannot match your content.</p></td>
</tr>
<tr class="odd">
<td><p>… image/url</p></td>
<td><p>Required</p></td>
<td><p><code>http://your_domain/your_image_path</code></p>
<p>Image dimensions must be 240 x 360 (W x H) pixels.</p></td>
</tr>
<tr class="even">
<td><p><span>… </span>image/@language</p></td>
<td><p>Optional</p></td>
<td><p>Default: en</p>
<p>(Roku Search is currently only available in English.)</p></td>
</tr>
<tr class="odd">
<td><p><span>… </span>image/@category</p></td>
<td><p>Required</p></td>
<td><p>Must one of the following:</p>
<ul>
<li>Poster Art</li>
<li>Box Art</li>
</ul></td>
</tr>
<tr class="even">
<td><p>… movie/descriptions/description</p></td>
<td><p>Required</p></td>
<td><p>You must provide a movie description that does not exceed 60 characters. You should (though are not required) to also provide longer descriptions not to exceed 500 characters (the maximum length is set by the description/@length attribute).</p></td>
</tr>
<tr class="odd">
<td><p><span>… </span>description/@language</p></td>
<td><p>Optional</p></td>
<td><p>Default: en</p>
<p>(Roku Search is currently only available in English.)</p></td>
</tr>
<tr class="even">
<td><p>… description/@length</p></td>
<td><p>Optional</p></td>
<td><p>Maximum character value for the short/long description. Must be one of the following:</p>
<ul>
<li>60 (default)</li>
<li>100</li>
<li>250</li>
<li>500</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>… movie/runTime</p></td>
<td><p>Required</p></td>
<td><p>Runtime in seconds</p></td>
</tr>
<tr class="even">
<td><p>… movie/releaseYear</p></td>
<td><p>Required</p></td>
<td><p>Year initially released or first aired</p></td>
</tr>
<tr class="odd">
<td><p>… movie/crew/person,</p>
<p>… movie/cast/person</p></td>
<td><p>Optional</p></td>
<td><p>Used to provide a list of cast and crew members.</p>
<div class="confluence-information-macro confluence-information-macro-tip">
<span class="aui-icon aui-icon-small aui-iconfont-approve confluence-information-macro-icon"></span>
<div class="confluence-information-macro-body">
We recommend that you provide this if there’s a chance that we can’t match your data.
</div>
</div></td>
</tr>
<tr class="even">
<td><p>… cast/person/role</p></td>
<td><p>Required if a cast person is provided</p></td>
<td><p>Must be one of the following:</p>
<ul>
<li>Actor</li>
<li>Anchor</li>
<li>Host</li>
<li>Narrator</li>
<li>Voice</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>… crew/person/role</p></td>
<td><p>Required if a crew person is provided</p></td>
<td><p>Must be one of the following:</p>
<ul>
<li>Director</li>
<li>Host</li>
</ul></td>
</tr>
<tr class="even">
<td><p>… person/firstName</p></td>
<td><p>Required if person provided</p></td>
<td><p>First Name or abbreviation</p></td>
</tr>
<tr class="odd">
<td><p>… person/middleName</p></td>
<td><p>Optional</p></td>
<td><p>Middle Name or abbreviation</p></td>
</tr>
<tr class="even">
<td><p>… person/lastName</p></td>
<td><p>Optional</p></td>
<td><p>Last Name</p></td>
</tr>
<tr class="odd">
<td><p>… person/birthDate</p></td>
<td><p>Optional</p></td>
<td><p><code>YYYY-mm-dd</code></p></td>
</tr>
<tr class="even">
<td><p>… person/deathDate</p></td>
<td><p>Optional</p></td>
<td><p><code>YYYY-mm-dd</code></p></td>
</tr>
<tr class="odd">
<td><p>… person/image</p></td>
<td><p>Optional</p></td>
<td><p><code>http://your_domain/your_image_path</code></p>
<p>Image dimensions must be 270 x 360 (W x H) pixels.</p></td>
</tr>
<tr class="even">
<td><p>… movie/ratings/rating</p></td>
<td><p>Optional</p></td>
<td><p>Localized parental rating of movie</p></td>
</tr>
<tr class="odd">
<td><p>… rating/rating</p></td>
<td><p>Required if rating provided</p></td>
<td><p>Must be a value found in <a href="#RokuSearch-AcceptableParentalRatings">Acceptable Parental Ratings</a></p></td>
</tr>
<tr class="even">
<td><p>… rating/source</p></td>
<td><p>Required if rating provided</p></td>
<td><p>Must be either:</p>
<ul>
<li>British Board of Film Classification</li>
<li>Canadian Home Video Rating System</li>
<li>Canadian Parental Rating</li>
<li>Motion Picture Association of America</li>
<li>UK Content Provider</li>
<li>USA Parental Rating</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>… movie/keywords/keyword</p></td>
<td><p>Optional</p></td>
<td><p>Keywords used to describe movie</p></td>
</tr>
<tr class="even">
<td><p>… keyword/type</p></td>
<td><p>Required only if keyword</p></td>
<td><p>Must be:</p>
<ul>
<li>Character</li>
<li>General</li>
<li>Mood</li>
<li>Setting</li>
<li>Subject</li>
<li>Theme</li>
<li>Time Period</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>… keyword/word</p></td>
<td><p>Optional</p></td>
<td><p>Users cannot search by keyword, however our meta-data structure supports them. For example, here are keywords for the movie <strong><em>Argo</em></strong> by keyword type:</p>
<p><strong>Mood</strong></p>
<ul>
<li>Brutal</li>
<li>Tense</li>
<li>Suspenseful</li>
</ul>
<p><strong>Theme</strong></p>
<ul>
<li>Rescue</li>
<li>Escape</li>
</ul>
<p><strong>Subject</strong></p>
<ul>
<li>Iran hostage crisis</li>
<li>On the run</li>
<li>Political intrigue</li>
<li>Schemes</li>
</ul>
<p><strong>Time Period</strong></p>
<ul>
<li>1970s</li>
</ul>
<p><strong>Setting</strong></p>
<ul>
<li>Tehran, Iran</li>
<li>CIA office</li>
<li>Canada</li>
<li>United States</li>
</ul>
<p><strong>Character</strong></p>
<ul>
<li>CIA agent</li>
<li>Specialist</li>
<li>Hostage</li>
<li>Revolutionary</li>
<li>Ambassador</li>
<li>Wife</li>
</ul></td>
</tr>
<tr class="even">
<td><p><span>… </span>keyword/@language</p></td>
<td><p>Optional</p></td>
<td><p>Default: en</p>
<p>(Roku Search is currently only available in English.)</p></td>
</tr>
<tr class="odd">
<td><p>… movie/genres/genre</p></td>
<td><p>Optional</p></td>
<td><p>Must be found in <a href="#RokuSearch-AcceptableGenres">Acceptable Genres</a>.</p></td>
</tr>
<tr class="even">
<td><p>… movie/videos/video</p></td>
<td><p>Required</p></td>
<td><p>The videos element lists all the video content items corresponding to the specific movie identified by the movie/@id attribute. Each child video element must have a unique play ID, and provide meta-data indicating availability, pricing and other specifics about that specific video content item available on your channel.</p></td>
</tr>
<tr class="odd">
<td><p>… video/playId</p></td>
<td><p>Required</p></td>
<td><p>A value you provide for each title in your XML feed that we will pass back to your channel when a user selects your service as a provider for a specific title (see <a href="#RokuSearch-PlayIDsandDeepLinking">Play IDs and Deep Linking</a>).</p></td>
</tr>
<tr class="even">
<td><p>… video/region</p></td>
<td><p>Optional</p></td>
<td><p>Can be one of the following 2-character ISO codes (can be either uppercase or lowercase):</p>
<ul>
<li>us (default)</li>
<li>US (default)</li>
<li>gb</li>
<li>GB</li>
<li>ca</li>
<li>CA</li>
<li>ie</li>
<li>IE</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>… video/viewOptions/option</p></td>
<td><p>Required</p></td>
<td><p>Used to provide video viewing options.</p></td>
</tr>
<tr class="even">
<td><p>… option/quality</p></td>
<td><p>Required</p></td>
<td><p>The resolution of the video content item. Must be one of the following (can either be uppercase or lowercase):</p>
<ul>
<li>sd</li>
<li>SD</li>
<li>hd</li>
<li>HD</li>
<li>hd+</li>
<li>HD+</li>
<li>UHD</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>… option/license</p></td>
<td><p>Required</p></td>
<td><p>The type of licensing terms for the video content item. Must be one of the following (can either be initial capitalization or all lowercase):</p>
<ul>
<li>free</li>
<li>Free</li>
<li>rental</li>
<li>Rental</li>
<li>purchase</li>
<li>Purchase</li>
<li>subscription</li>
<li>Subscription</li>
</ul></td>
</tr>
<tr class="even">
<td><p>… option/price</p></td>
<td><p>Required if option/license is set to purchase or rental, defaults to 0.00 if option/license is set to subscription or free</p></td>
<td><p>Price, that must include two decimal point places, such as &quot;1.90&quot;, &quot;1.99&quot;, or &quot;2.00&quot;. If the price is &quot;0.00&quot;, set option/license to &quot;subscription&quot; or &quot;free&quot; rather than setting option/price to &quot;0.00&quot;, and option/price will be set to &quot;0.00&quot; by default.</p></td>
</tr>
<tr class="odd">
<td><p>… option/currency</p></td>
<td><p>Optional</p></td>
<td><p>The type of currency denominated by price. Must be one of the following (can be either uppercase or lowercase):</p>
<ul>
<li>usd (default)</li>
<li>USD (default)</li>
<li>gbp</li>
<li>GBP</li>
<li>cad</li>
<li>CAD</li>
</ul></td>
</tr>
</tbody>
</table>

</div>

### TV Meta-Data (TMS)

<div class="table-wrap">

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>seriesItems/series/@tmsId</p></td>
<td><p>Required</p></td>
<td><p>Gracenote TMS ID for a specific TV series.</p></td>
</tr>
<tr class="even">
<td><p>... series/title</p></td>
<td><p>Optional</p></td>
<td><p>Optional, but very helpful</p></td>
</tr>
<tr class="odd">
<td><p>… series/episodes/episode</p></td>
<td><p>Required</p></td>
<td><p>At least one episode must be included for a series</p></td>
</tr>
<tr class="even">
<td><p>episode/@tmsId</p></td>
<td><p>Required</p></td>
<td><p>Gracenote TMS ID for a specific TV episode.</p></td>
</tr>
<tr class="odd">
<td><p>... episode/title</p></td>
<td><p>Optional</p></td>
<td><p>Optional, but very helpful</p></td>
</tr>
<tr class="even">
<td><p>… episode/videos/video</p></td>
<td><p>Required</p></td>
<td><p>The videos element lists all the video content items corresponding to the specific TV episode identified by the episode/@tmsId attribute. Each child video element must have a unique play ID, and provide meta-data indicating availability, pricing, and other specifics about that specific video content item available on your channel.</p></td>
</tr>
<tr class="odd">
<td><p>… video/playId</p></td>
<td><p>Required</p></td>
<td><p>A value you provide for each title in your XML feed that we will pass back to your channel when a user selects your service as a provider for a specific title (see <a href="#RokuSearch-PlayIDsandDeepLinking">Play IDs and Deep Linking</a>).</p></td>
</tr>
<tr class="even">
<td><p>… video/region</p></td>
<td><p>Optional</p></td>
<td><p>Can be one of the following 2-character ISO codes (can be either uppercase or lowercase):</p>
<ul>
<li>us (default)</li>
<li>US (default)</li>
<li>gb</li>
<li>GB</li>
<li>ca</li>
<li>CA</li>
<li>ie</li>
<li>IE</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>… video/viewOptions/option</p></td>
<td><p>Required</p></td>
<td><p>Used to provide video viewing options.</p></td>
</tr>
<tr class="even">
<td><p>… option/quality</p></td>
<td><p>Required</p></td>
<td><p>The resolution of the video content item. Must be one of the following (can be either uppercase or lowercase):</p>
<ul>
<li>sd</li>
<li>SD</li>
<li>hd</li>
<li>HD</li>
<li>hd+</li>
<li>HD+</li>
<li>UHD</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>… option/license</p></td>
<td><p>Required</p></td>
<td><p>The type of licensing terms for the video content item. Must be one of the following (can be either initial capitalization or all lowercase):</p>
<ul>
<li>free</li>
<li>Free</li>
<li>rental</li>
<li>Rental</li>
<li>purchase</li>
<li>Purchase</li>
<li>subscription</li>
<li>Subscription</li>
</ul></td>
</tr>
<tr class="even">
<td><p>… option/price</p></td>
<td><p>Required if option/license is set to purchase or rental, defaults to 0.00 if option/license is set to subscription or free</p></td>
<td><p>Price, that must include two decimal point places, such as &quot;1.90&quot;, &quot;1.99&quot;, or &quot;2.00&quot;. If the price is &quot;0.00&quot;, set option/license to &quot;subscription&quot; or &quot;free&quot; rather than setting option/price to &quot;0.00&quot;, and option/price will be set to &quot;0.00&quot; by default.</p></td>
</tr>
<tr class="odd">
<td><p>… option/currency</p></td>
<td><p>Optional</p></td>
<td><p>The type of currency denominated by price. Must be one of the following (can be either uppercase or lowercase):</p>
<ul>
<li>usd (default)</li>
<li>USD (default)</li>
<li>gbp</li>
<li>GBP</li>
<li>cad</li>
<li>CAD</li>
</ul></td>
</tr>
</tbody>
</table>

</div>

### TV Meta-Data (non-TMS)

<div class="table-wrap">

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>seriesItems/series/@id</p></td>
<td><p>Required</p></td>
<td><p>Your immutable reference ID for that TV series.</p>
<div class="confluence-information-macro confluence-information-macro-warning">
<span class="aui-icon aui-icon-small aui-iconfont-error confluence-information-macro-icon"></span>
<div class="confluence-information-macro-body">
Once assigned to a content item, you cannot change the reference ID or use it for another content item in the Roku <strong>Search</strong> meta-data.
</div>
</div></td>
</tr>
<tr class="even">
<td><p>… series/titles/title</p></td>
<td><p>Required</p></td>
<td><p>Used for providing titles. We use this field for matching.</p></td>
</tr>
<tr class="odd">
<td><p><span>… </span>title/@language</p></td>
<td><p>Options</p></td>
<td><p>Default: en</p>
<p>(Roku <strong>Search</strong> is currently only available in English.)</p></td>
</tr>
<tr class="even">
<td><p>… series/images/image</p></td>
<td><p>Optional</p></td>
<td><p>Used to provide images for this tv series. Optional but highly recommended if you’re not confident that we can match your data.</p></td>
</tr>
<tr class="odd">
<td><p>… image/url</p></td>
<td><p>Required</p></td>
<td><p><span class="nolink"><span style="font-family: Courier New;">http://your_domain/your_image_path</span></span></p>
<p>Image dimensions must be 360 x 270 (W x H) pixels.</p></td>
</tr>
<tr class="even">
<td><p><span>… </span>image/@language</p></td>
<td><p>Optional</p></td>
<td><p>Default: en</p>
<p>(Roku Search is currently only available in English.)</p></td>
</tr>
<tr class="odd">
<td><p>… series/descriptions/description</p></td>
<td><p>Required</p></td>
<td><p>You must provide a movie description that does not exceed 60 characters. You should (though are not required) to also provide longer descriptions not to exceed 500 characters (the maximum length is set by the description/@length attribute).</p></td>
</tr>
<tr class="even">
<td><p><span>… </span>description/@language</p></td>
<td><p>Optional</p></td>
<td><p>Default: en</p>
<p>(Roku Search is currently only available in English.)</p></td>
</tr>
<tr class="odd">
<td><p><span>… </span>description/@length</p></td>
<td><p>Optional</p></td>
<td><p>The maximum character value for the short/long description.</p>
<p>Must be one of the following:</p>
<ul>
<li>60 (default)</li>
<li>100</li>
<li>250</li>
<li>500</li>
</ul></td>
</tr>
<tr class="even">
<td><p>… series/originalAirDate</p></td>
<td><p>Optional</p></td>
<td><p>Optional but very important. We recommend that you provide this.</p></td>
</tr>
<tr class="odd">
<td><p>… series/crew/person,<br />
… series/cast/person</p></td>
<td><p>Optional</p></td>
<td><p>Used to identify cast and crew members</p></td>
</tr>
<tr class="even">
<td><p>… cast/person/role</p></td>
<td><p>Required if a cast person is provided</p></td>
<td><p>Must be one of the following::</p>
<ul>
<li>Actor</li>
<li>Anchor</li>
<li>Host</li>
<li>Narrator</li>
<li>Voice</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>… crew/person/role</p></td>
<td><p>Required if a crew person is provided</p></td>
<td><p>Must be one of the following:</p>
<ul>
<li>Director</li>
<li>Host</li>
</ul></td>
</tr>
<tr class="even">
<td><p>… person/firstName</p></td>
<td><p>Required if person provided</p></td>
<td><p>First Name or abbreviation. Used for matching.</p></td>
</tr>
<tr class="odd">
<td><p>… person/middleName</p></td>
<td><p>Optional</p></td>
<td><p>Middle Name or abbreviation</p></td>
</tr>
<tr class="even">
<td><p>… person/lastName</p></td>
<td><p>Optional</p></td>
<td><p>Last Name. Used for matching.</p></td>
</tr>
<tr class="odd">
<td><p>… person/birthDate</p></td>
<td><p>Optional</p></td>
<td><p><code>YYYY-mm-dd</code></p>
<p>Used for matching.</p></td>
</tr>
<tr class="even">
<td><p>… person/deathDate</p></td>
<td><p>Optional</p></td>
<td><p><code>YYYY-mm-dd</code></p></td>
</tr>
<tr class="odd">
<td><p>… person/image</p></td>
<td><p>Optional</p></td>
<td><p><span class="nolink"><span style="font-family: Courier New;">http://your_domain/your_image_path</span></span></p>
<p>Image dimensions must be 270 x 360 (W x H) pixels.</p></td>
</tr>
<tr class="even">
<td><p>… series/seasons/season</p></td>
<td><p>Required</p></td>
<td><p>Used to include data for seasons</p></td>
</tr>
<tr class="odd">
<td><p>… season/seasonNumber</p></td>
<td><p>Required</p></td>
<td><p>Sequential season number</p></td>
</tr>
<tr class="even">
<td><p>… season/images/image/url</p></td>
<td><p>Required</p></td>
<td><p><span class="nolink"><span style="font-family: Courier New;">http://your_domain/your_image_path</span></span></p>
<p>Image dimensions must be 360 x 270 (W x H) pixels.</p></td>
</tr>
<tr class="odd">
<td><p><span>… </span>season/images/image/@language</p></td>
<td><p>Optional</p></td>
<td><p>Default: en</p>
<p>(Roku Search is currently only available in English.)</p></td>
</tr>
<tr class="even">
<td><p>… season/episodes/episode</p></td>
<td><p>Required</p></td>
<td><p>At least one episode must be included for a series</p></td>
</tr>
<tr class="odd">
<td><p><span>… </span>episode/@id</p></td>
<td><p>Required</p></td>
<td><p>Your immutable reference ID for episode.</p>
<div class="confluence-information-macro confluence-information-macro-warning">
<span class="aui-icon aui-icon-small aui-iconfont-error confluence-information-macro-icon"></span>
<div class="confluence-information-macro-body">
Once assigned to a content item, you cannot change the reference ID or use it for another content item in the Roku Search meta-data.
</div>
</div></td>
</tr>
<tr class="even">
<td><p>… episode/episodeNumber</p></td>
<td><p>Required</p></td>
<td><p>Sequential episode number</p></td>
</tr>
<tr class="odd">
<td><p>… episode/airDate</p></td>
<td><p>Optional</p></td>
<td><p>Optional but recommended. This is helpful for matching and such.</p></td>
</tr>
<tr class="even">
<td><p>… episode/titles/title</p></td>
<td><p>Required</p></td>
<td><p>Series title</p></td>
</tr>
<tr class="odd">
<td><p>… title/@language</p></td>
<td><p>Optional</p></td>
<td><p>Default: en</p>
<p>(Roku Search is currently only available in English.)</p></td>
</tr>
<tr class="even">
<td><p>… episode/images/image</p></td>
<td><p>Optional</p></td>
<td><p>Image used for episode</p></td>
</tr>
<tr class="odd">
<td><p>… image/url</p></td>
<td><p>Required</p></td>
<td><p><code>http://your_domain/your_image_path</code></p>
<p>Image dimensions must be 360 x 270 (W x H) pixels.</p></td>
</tr>
<tr class="even">
<td><p><span>… </span>image/@language</p></td>
<td><p>Optional</p></td>
<td><p>Default: en</p>
<p>(Roku Search is currently only available in English.)</p></td>
</tr>
<tr class="odd">
<td><p>… episode/descriptions/description</p></td>
<td><p>Required</p></td>
<td><p>You must provide a movie description that does not exceed 60 characters. You should (though are not required) to also provide longer descriptions not to exceed 500 characters (the maximum length is set by the description/@length attribute).</p></td>
</tr>
<tr class="even">
<td><p><span>… </span>description/@language</p></td>
<td><p>Optional</p></td>
<td><p>Default: en</p>
<p>(Roku Search is currently only available in English.)</p></td>
</tr>
<tr class="odd">
<td><p><span>… </span>description/@length</p></td>
<td><p>Optional</p></td>
<td><p>Must be the maximum character value for the short/long description:</p>
<ul>
<li>60 (default)</li>
<li>100</li>
<li>250</li>
<li>500</li>
</ul></td>
</tr>
<tr class="even">
<td><p>… episode/crew/person,<br />
… episode/cast/person</p></td>
<td><p>Optional</p></td>
<td><p>A cast or crew member.</p>
<div class="confluence-information-macro confluence-information-macro-tip">
<span class="aui-icon aui-icon-small aui-iconfont-approve confluence-information-macro-icon"></span>
<div class="confluence-information-macro-body">
Roku recommends that you provide complete data for this if you’re not sure that we can match the episode.  
</div>
</div></td>
</tr>
<tr class="odd">
<td><p>… cast/person/role</p></td>
<td><p>Required if a cast person is provided</p></td>
<td><p>Must be one of the following:</p>
<ul>
<li>Actor</li>
<li>Anchor</li>
<li>Host</li>
<li>Narrator</li>
<li>Voice</li>
</ul></td>
</tr>
<tr class="even">
<td><p>… crew/person/role</p></td>
<td><p>Required if a crew person is provided</p></td>
<td><p>Must be one of the following:</p>
<ul>
<li>Director</li>
<li>Host</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>… person/firstName</p></td>
<td><p>Required if person provided</p></td>
<td><p>First Name or abbreviation. Used for matching.</p></td>
</tr>
<tr class="even">
<td><p>… person/middleName</p></td>
<td><p>Optional</p></td>
<td><p>Middle Name or abbreviation</p></td>
</tr>
<tr class="odd">
<td><p>… person/lastName</p></td>
<td><p>Optional</p></td>
<td><p>Last Name. Used for matching.</p></td>
</tr>
<tr class="even">
<td><p>… person/birthDate</p></td>
<td><p>Optional</p></td>
<td><p><code>YYYY-mm-dd</code></p>
<p>Used for matching.</p></td>
</tr>
<tr class="odd">
<td><p>… person/deathDate</p></td>
<td><p>Optional</p></td>
<td><p><code>YYYY-mm-dd</code></p></td>
</tr>
<tr class="even">
<td><p>… person/image</p></td>
<td><p>Optional</p></td>
<td><p><span class="nolink"><span style="font-family: Courier New;">http://your_domain/your_image_path</span></span></p>
<p>Image dimensions must be 270 x 360 (W x H) pixels.</p></td>
</tr>
<tr class="odd">
<td><p>… episode/ratings/rating</p></td>
<td><p>Optional</p></td>
<td><p>Localized parental rating of movie</p></td>
</tr>
<tr class="even">
<td><p>… rating/rating</p></td>
<td><p>Required if rating provided</p></td>
<td><p>Must be a value from <a href="#RokuSearch-AcceptableParentalRatings">Acceptable Parental Ratings</a></p></td>
</tr>
<tr class="odd">
<td><p>… rating/source</p></td>
<td><p>Required if rating provided</p></td>
<td><p>Must be either:</p>
<ul>
<li>British Board of Film Classification</li>
<li>Canadian Home Video Rating System</li>
<li>Canadian Parental Rating</li>
<li>Motion Picture Association of America</li>
<li>UK Content Provider</li>
<li>USA Parental Rating</li>
</ul></td>
</tr>
<tr class="even">
<td><p>… episode/keywords/keyword</p></td>
<td><p>Optional</p></td>
<td><p>Keywords used to describe movie</p></td>
</tr>
<tr class="odd">
<td><p>… keyword/type</p></td>
<td><p>Required only if keyword</p></td>
<td><p>Must be:</p>
<ul>
<li>Character</li>
<li>General</li>
<li>Mood</li>
<li>Setting</li>
<li>Subject</li>
<li>Theme</li>
<li>Time Period</li>
</ul></td>
</tr>
<tr class="even">
<td><p>… keyword/word</p></td>
<td><p>Optional</p></td>
<td><p>Users cannot search by Keyword, however our meta-data structure supports them. For example, here are keywords for the movie <strong><em>Argo</em></strong> by keyword type:</p>
<p><strong>Mood</strong></p>
<ul>
<li>Brutal</li>
<li>Tense</li>
<li>Suspenseful</li>
</ul>
<p><strong>Theme</strong></p>
<ul>
<li>Rescue</li>
<li>Escape</li>
</ul>
<p><strong>Subject</strong></p>
<ul>
<li>Iran hostage crisis</li>
<li>On the run</li>
<li>Political intrigue</li>
<li>Schemes</li>
</ul>
<p><strong>Time Period</strong></p>
<ul>
<li>1970s</li>
</ul>
<p><strong>Setting</strong></p>
<ul>
<li>Tehran, Iran</li>
<li>CIA office</li>
<li>Canada</li>
<li>United States</li>
</ul>
<p><strong>Character</strong></p>
<ul>
<li>CIA agent</li>
<li>Specialist</li>
<li>Hostage</li>
<li>Revolutionary</li>
<li>Ambassador</li>
<li>Wife</li>
</ul></td>
</tr>
<tr class="odd">
<td><p><span>… </span>keyword/@language</p></td>
<td><p>Optional</p></td>
<td><p>Default: en</p>
<p>(Roku Search is currently only available in English.)</p></td>
</tr>
<tr class="even">
<td><p>… episode/videos/video</p></td>
<td><p>Required</p></td>
<td><p>The videos element lists all the video content items corresponding to the specific TV episode identified by the episode/@id attribute. Each child video element must have a unique play ID, and provide meta-data indicating availability, pricing, and other specifics about that specific video content item available on your channel.</p></td>
</tr>
<tr class="odd">
<td><p>… episode/genres/genre</p></td>
<td><p>Optional</p></td>
<td><p>Must be found in <a href="#RokuSearch-AcceptableGenres">Acceptable Genres</a>.</p></td>
</tr>
<tr class="even">
<td><p>… video/playId</p></td>
<td><p>Required</p></td>
<td><p>A value you provide for each title in your XML feed that we will pass back to your channel when a user selects your service as a provider for a specific title (see <a href="#RokuSearch-PlayIDsandDeepLinking">Play IDs and Deep Linking</a>).  </p></td>
</tr>
<tr class="odd">
<td><p>… video/region</p>
<p> </p></td>
<td><p>Optional</p>
<p> </p></td>
<td><p>Must be one of the following 2-character ISO codes (can be either uppercase or lowercase):</p>
<ul>
<li>us (default)</li>
<li>US (default)</li>
<li>gb</li>
<li>GB</li>
<li>ca</li>
<li>CA</li>
<li>ie</li>
<li>IE</li>
</ul></td>
</tr>
<tr class="even">
<td><p>… video/viewOptions/option</p></td>
<td><p>Required</p></td>
<td><p>You must provide at least one option.</p></td>
</tr>
<tr class="odd">
<td><p>… option/quality</p></td>
<td><p>Required</p></td>
<td><p>The resolution of the video content item. Must be one of the following (can be either uppercase or lowercase):</p>
<ul>
<li>sd</li>
<li>SD</li>
<li>hd</li>
<li>HD</li>
<li>hd+</li>
<li>HD+</li>
<li>UHD</li>
</ul></td>
</tr>
<tr class="even">
<td><p>… option/license</p></td>
<td><p>Required</p></td>
<td><p>The type of licensing terms for the video content item. Must be one of the following (can be either initial capitalization or all lowercase):</p>
<ul>
<li>free</li>
<li>Free</li>
<li>rental</li>
<li>Rental</li>
<li>purchase</li>
<li>Purchase</li>
<li>subscription</li>
<li>Subscription</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>… option/price</p></td>
<td><p>Required if option/license is set to purchase or rental, defaults to 0.00 if option/license is set to subscription or free</p></td>
<td><p>Price, that must include two decimal point places, such as &quot;1.90&quot;, &quot;1.99&quot;, or &quot;2.00&quot;. If the price is &quot;0.00&quot;, set option/license to &quot;subscription&quot; or &quot;free&quot; rather than setting option/price to &quot;0.00&quot;, and option/price will be set to &quot;0.00&quot; by default.</p></td>
</tr>
<tr class="even">
<td><p>… option/currency</p></td>
<td><p>Optional</p></td>
<td><p>The currency that denominates price. Must be one of the following (can either be uppercase or lowercase):</p>
<ul>
<li>usd (default)</li>
<li>USD (default)</li>
<li>gbp</li>
<li>GBP</li>
<li>cad</li>
<li>CAD</li>
</ul></td>
</tr>
</tbody>
</table>

</div>

## Acceptable Genres

All acceptable genres may have either initial capitalization of the
first word or all lower-case.

<div class="sectionColumnWrapper">

<div class="sectionMacro">

<div class="sectionMacroRow">

<div class="columnMacro" style="width:25%;min-width:25%;max-width:25%;">

  - action
  - action sports
  - adventure
  - aerobics
  - agriculture
  - animals
  - animated
  - anime
  - anthology
  - archery
  - arm wrestling
  - art
  - arts/crafts
  - auction
  - auto
  - auto racing
  - aviation
  - awards
  - badminton
  - ballet
  - baseball
  - basketball
  - beach soccer
  - beach volleyball
  - biathlon
  - bicycle
  - bicycle racing
  - billiards
  - biography
  - blackjack
  - boat
  - boat racing
  - bobsled
  - bodybuilding
  - bowling
  - boxing
  - bullfighting
  - bus./financial
  - canoe
  - card games
  - cheerleading
  - children
  - children-music
  - children-special
  - children-talk
  - collectibles
  - comedy
  - comedy drama
  - community
  - computers
  - consumer
  - cooking
  - cricket
  - crime
  - crime drama
  - curling

</div>

<div class="columnMacro" style="width:25%;min-width:25%;max-width:25%;">

  - dance
  - dark comedy
  - darts
  - debate
  - diving
  - docudrama
  - documentary
  - dog racing
  - dog show
  - dog sled
  - drag racing
  - drama
  - educational
  - entertainment
  - environment
  - equestrian
  - erotic
  - event
  - exercise
  - fantasy
  - fashion
  - fencing
  - field hockey
  - figure skating
  - fishing
  - football
  - fundraiser
  - gaelic football
  - game show
  - gaming
  - gay/lesbian
  - golf
  - gymnastics
  - handball
  - health
  - historical drama
  - history
  - hockey
  - holiday
  - holiday music
  - holiday music special
  - holiday special
  - holiday-children
  - holiday-children special
  - home improvement
  - horror
  - horse
  - house/garden
  - how-to
  - hunting
  - hurling
  - hydroplane racing
  - indoor soccer
  - interview
  - intl soccer

</div>

<div class="columnMacro" style="width:25%;min-width:25%;max-width:25%;">

  - kayaking
  - lacrosse
  - law
  - luge
  - martial arts
  - medical
  - military
  - miniseries
  - mixed martial arts
  - motorcycle
  - motorcycle racing
  - motorsports
  - mountain biking
  - music
  - music special
  - music talk
  - musical
  - musical comedy
  - mystery
  - nature
  - news
  - newsmagazine
  - olympics
  - opera
  - outdoors
  - parade
  - paranormal
  - parenting
  - performing arts
  - playoff sports
  - poker
  - politics
  - polo
  - pool
  - pro wrestling
  - public affairs
  - racquet
  - reality
  - religious
  - ringuette
  - rodeo
  - roller derby
  - romance
  - romantic comedy
  - rowing
  - rugby
  - running

</div>

<div class="columnMacro" style="width:25%;min-width:25%;max-width:25%;">

  - sailing
  - science
  - science fiction
  - self improvement
  - shooting
  - shopping
  - sitcom
  - skateboarding
  - skating
  - skeleton
  - skiing
  - snooker
  - snowboarding
  - snowmobile
  - soap
  - soap special
  - soap talk
  - soccer
  - softball
  - special
  - speed skating
  - sports talk
  - squash
  - standup
  - sumo wrestling
  - surfing
  - suspense
  - swimming
  - table tennis
  - talk
  - technology
  - tennis
  - theater
  - thriller
  - track/field
  - travel
  - triathlon
  - variety
  - volleyball
  - war
  - water polo
  - water skiing
  - watersports
  - weather
  - weightlifting
  - western
  - wrestling
  - yacht racing

</div>

</div>

</div>

</div>

## Acceptable Parental Ratings

<div class="sectionColumnWrapper">

<div class="sectionMacro">

<div class="sectionMacroRow">

<div class="columnMacro" style="width:25%;min-width:25%;max-width:25%;">

  - 12
  - 12A
  - 14+
  - 14A
  - 15
  - 18
  - 18+
  - 18A

</div>

<div class="columnMacro" style="width:25%;min-width:25%;max-width:25%;">

  - A
  - AA
  - C
  - C8
  - E
  - G
  - NC-17
  - PG

</div>

<div class="columnMacro" style="width:25%;min-width:25%;max-width:25%;">

  - PG-13
  - R
  - R18
  - TV14
  - TVG
  - TVMA
  - TVPG
  - TVY

</div>

<div class="columnMacro" style="width:25%;min-width:25%;max-width:25%;">

  - TVY14
  - TVY7
  - U
  - Uc
  - UNRATED

</div>

</div>

</div>

</div>

</div>

<div class="pageSection group">

<div class="pageSectionHeader">

## Attachments:

</div>

<div class="greybox" data-align="left">

![](images/icons/bullet_blue.gif)
[searchscreen.jpg](attachments/3737679/3737678.jpg) (image/jpeg)  
![](images/icons/bullet_blue.gif)
[searchresults.jpg](attachments/3737679/3737682.jpg) (image/jpeg)  
![](images/icons/bullet_blue.gif)
[searchscreen80.jpg](attachments/3737679/3737710.jpg) (image/jpeg)  
![](images/icons/bullet_blue.gif)
[searchresults80.jpg](attachments/3737679/3737711.jpg) (image/jpeg)  
![](images/icons/bullet_blue.gif)
[searchalgo.png](attachments/3737679/3737724.png) (image/png)  
![](images/icons/bullet_blue.gif)
[searchalgo.png](attachments/3737679/3737873.png) (image/png)  
![](images/icons/bullet_blue.gif)
[roku-partner-content-feed-example-non-tms-id-2015-06-02.xml](attachments/3737679/4264873.xml)
(text/xml)  
![](images/icons/bullet_blue.gif)
[roku-parter-content-feed-example-tms-id\_2015-06-01.xml](attachments/3737679/3737768.xml)
(text/xml)  
![](images/icons/bullet_blue.gif)
[partner-feed-tms-validator.xsd](attachments/3737679/4259866.xsd)
(application/octet-stream)  
![](images/icons/bullet_blue.gif)
[partner-feed-validatornontms.xsd](attachments/3737679/4259868.xsd)
(application/octet-stream)  
![](images/icons/bullet_blue.gif)
[searchalgo.png](attachments/3737679/3737716.png) (image/png)  
![](images/icons/bullet_blue.gif)
[searchalgo.jpg](attachments/3737679/3737876.jpg) (image/jpeg)  
![](images/icons/bullet_blue.gif)
[searchlogodims.jpg](attachments/3737679/3737888.jpg) (image/jpeg)  
![](images/icons/bullet_blue.gif)
[searchProviderTile\_HD.psd](attachments/3737679/3737889.psd)
(image/photoshop)  
![](images/icons/bullet_blue.gif)
[searchProviderTile\_SD.psd](attachments/3737679/3737890.psd)
(image/photoshop)  
![](images/icons/bullet_blue.gif)
[partnerLogo\_template\_HD.psd](attachments/3737679/3737892.psd)
(image/photoshop)  
![](images/icons/bullet_blue.gif)
[partnerLogo\_template\_HD.psd](attachments/3737679/3737891.psd)
(image/photoshop)  
![](images/icons/bullet_blue.gif)
[partnerLogo\_template\_SD.psd](attachments/3737679/3737893.psd)
(image/photoshop)  
![](images/icons/bullet_blue.gif)
[partner-feed-tms-validator.xsd](attachments/3737679/3737769.xsd)
(application/octet-stream)  
![](images/icons/bullet_blue.gif)
[partner-feed-validatornontms.xsd](attachments/3737679/4259869.xsd)
(application/octet-stream)  
![](images/icons/bullet_blue.gif)
[partner-feed-validatornontms.xsd](attachments/3737679/3737770.xsd)
(application/octet-stream)  
![](images/icons/bullet_blue.gif)
[harrisonFord.jpg](attachments/3737679/4259935.jpg) (image/jpeg)  
![](images/icons/bullet_blue.gif)
[harrisonFord.jpg](attachments/3737679/4259934.jpg) (image/jpeg)  
![](images/icons/bullet_blue.gif)
[GameOThrones.jpg](attachments/3737679/4259936.jpg) (image/jpeg)  
![](images/icons/bullet_blue.gif)
[partner-feed-validator.xsd](attachments/3737679/4259943.xsd)
(application/octet-stream)  
![](images/icons/bullet_blue.gif)
[partner-feed-tms-validator.xsd](attachments/3737679/4265039.xsd)
(application/octet-stream)  
![](images/icons/bullet_blue.gif)
[partner-feed-validator.xsd](attachments/3737679/4265038.xsd)
(application/octet-stream)  
![](images/icons/bullet_blue.gif)
[Capture.PNG](attachments/3737679/4260366.png) (image/png)  
![](images/icons/bullet_blue.gif)
[roku-partner-content-feed-example-non-tms-id-2015-06-02.xml](attachments/3737679/4264884.xml)
(text/xml)  
![](images/icons/bullet_blue.gif)
[roku-partner-content-feed-example-non-tms-id-2015-06-02.xml](attachments/3737679/3737767.xml)
(text/xml)  
![](images/icons/bullet_blue.gif)
[partner-feed-validator.xsd](attachments/3737679/5440966.xsd)
(application/octet-stream)  
![](images/icons/bullet_blue.gif)
[partner-feed-tms-validator.xsd](attachments/3737679/4259946.xsd)
(application/octet-stream)  
![](images/icons/bullet_blue.gif)
[searchProviderTile\_FHD.psd](attachments/3737679/5440660.psd)
(image/vnd.adobe.photoshop)  
![](images/icons/bullet_blue.gif)
[partnerLogo\_template\_FHD.psd](attachments/3737679/5440661.psd)
(image/vnd.adobe.photoshop)  
![](images/icons/bullet_blue.gif)
[partner-feed-validator.xsd](attachments/3737679/4259947.xsd)
(application/xml)  

</div>

</div>

</div>

</div>

<div id="footer" data-role="contentinfo">

<div class="section footer-body">

Document generated by Confluence on Jan 23, 2018 17:13

<div id="footer-logo">

[Atlassian](http://www.atlassian.com/)

</div>

</div>

</div>

</div>
