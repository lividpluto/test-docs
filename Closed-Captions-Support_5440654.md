1.  [aanchal doc changes](index.html)
2.  [Aanchal Doc changes](Aanchal-Doc-changes_5439532.html)

aanchal doc changes : Closed Captions Support {#title-heading .pagetitle}
=============================================

Created by Aanchal Gupta, last modified by Tom Charles on Dec 06, 2017

The Roku platform supports the following closed caption formats:

-   SMPTE-TT
-   EIA-608/708
-   WebVTT

Overview {#ClosedCaptionsSupport-Overview}
--------

SMPTE-TT uses TTML formatted data either in an external file or embedded
into the video stream to carry the caption text, timing, and format
information. With EIA-608/708, caption information can only be embedded
into the video stream. Adding support for either of these formats to
your BrightScript channel is straightforward. SMPTE-TT and EIA-608
caption formats are not supported on legacy Roku platforms where the
device is running firmware version 3.1. These platforms are limited to
the use of SRT subtitles.

 

Closed Caption tracks specification {#ClosedCaptionsSupport-ClosedCaptiontracksspecification}
-----------------------------------

Use the Content-Meta-Data property SubtitleTracks that specify language,
description and track name for each subtitle track. The SubtitleConfig
property should not be used – unless overriding the caption track that
is automatically selected based on user caption language preference.
When specifying a track in SubtitleConfig – be sure to also specify it
in SubtitleTracks so that the language and description are clear.
Omitting the description will cause the UI to display the language in
the closed caption menu. A description should at least contain the
language.

The Video Node has additional fields related to closed captioning.

Certification Requirements {#ClosedCaptionsSupport-CertificationRequirements}
--------------------------

### Packaged Control Settings {#ClosedCaptionsSupport-PackagedControlSettings}

In accordance with our certification requirements, Roku’s Video node
automatically handles:

-   closed captioning, 
-   language selection, and 
-   instant replay.

![](attachments/5440654/5440648.png)

 

Unless the channel overrides it, all Roku players will launch
an **Options overlay menu** when
the ![](attachments/5440654/5440649.png) key is pressed during playback
of full-screen videos.

However, this only works if the channel does not have
its [OnKeyEvent()](https://sdkdocs.roku.com/pages/viewpage.action?pageId=1608547) handler
fired, and the **[Video
node](https://sdkdocs.roku.com/display/sdkdoc/Video)** is playing full
screen and setFocus is enabled i.e., the Video node is in focus, as
displayed in the following code example:

+--------------------------------------------------------------------------+
| sub init()\                                                              |
| m.top.setFocus(true)\                                                    |
| setVideo()\                                                              |
| end sub                                                                  |
+--------------------------------------------------------------------------+

 \

\

**Note:** When a full-screen video is playing, the user will expect the
\* key to work as expected. The channel must not override it in cases
where there are no other UI elements showing with associated actions for
the \* key.

### Custom Control Settings {#ClosedCaptionsSupport-CustomControlSettings}

#### Recommendations {#ClosedCaptionsSupport-Recommendations}

Note that Captions have following three values:

-   “on,”
-   “on-replay,” and
-   “off.”

The following is a list of recommendations and items to be aware of:

-   Starting from Roku OS 8, it is no longer necessary for a channel to
    partake in the Closed Caption track selection, apart from adding any
    available tracks to the list of available tracks. The firmware now
    selects a Closed Caption track based on the preferred caption
    language selection in the system preferences. When the selected
    language is not available, it defaults to the system's UI language.
-   The global **closedCaptionMode** method of
    the [videoNode](https://sdkdocs.roku.com/display/sdkdoc/Video) object
    is how you turn on and off closed captioning of the current playing
    video. The global settings can be read and set in
    the [rodeviceinfo](https://sdkdocs.roku.com/display/sdkdoc/ifDeviceInfo) object. These
    affect the same system setting. Whenever the user switches on/off
    closed caption, it is expected that the global setting will be
    adjusted accordingly. Therefore setting the global setting every
    time you adjust a local setting is required.
-   The **audio track** and the **subtitle track** (for Multilanguage
    subtitles) can be
    set using the **VideoNode.audioTrack** and **VideoNode.subtitleTrack** respectively.
    The available tracks can be found
    with **VideoNode.availableAudioTracks** and **VideoNode.availableSubtitleTracks**.
    Another useful item is **rodeviceinfo.GetCurrentLocale**.
-   If you are using the **roVideoScreen** or **roVideoPlayer**, you
    should be rewriting your application
    in **[SceneGraph](https://sdkdocs.roku.com/display/sdkdoc/SceneGraph+Core+Concepts)** as the older
    technologies are being dropped from the firmware.

### Star Button {#ClosedCaptionsSupport-StarButton}

**Important notes about
the ![](attachments/5440654/5440649.png) Button:**

![](attachments/5440654/5440648.png)

 

-   All Roku devices (express, premier, premier+, premier Ultra)  plus
    all TVs handle the ![](attachments/5440654/5440649.png)button.
-   Beginning with Roku OS 8, the Options overlay slides in whenever
    the ![](attachments/5440654/5440649.png) button is pressed, the
    Video node is in focus, and the OnKeyEvent() handler is fired. When
    the Video node is not in focus, the Options overlay does not slide
    in and the OnKeyEvent() handler is fired. \
-   If you are running the Video Node on older Roku devices,
    then the ![](attachments/5440654/5440649.png)button can only be
    detected at the channel level. As a result, you will not be able to
    disable the default UI on any of the older Roku devices. 

### Instant Replay Button {#ClosedCaptionsSupport-InstantReplayButton}

Similarly, to closed captioning, Roku recommends that you allow us to
handle use of the instant replay
button ![](attachments/5440654/5440650.png) in our firmware. However, if
you decide to override our built-in functionality, then your channel
must offer equal levels of functionality.

![](attachments/5440654/5440651.png)

While playing video, pressing ![](attachments/5440654/5440650.png) will
move the play head back 20 seconds and resume playing. If the closed
caption setting is set to “On-replay,” then closed captioning will
appear for the duration of time until playback reaches the position
where the user presses ![](attachments/5440654/5440650.png) .

The instant replay button events can be received like any
other [events](https://sdkdocs.roku.com/display/sdkdoc/Event+Loops).

Beginning with Roku OS 8, the firmware will automatically enable the
closed captions during the replay interval.

Pressing ![](attachments/5440654/5440650.png) multiple times should move
the play head and changes the demarcation point accordingly i.e., only
the most recent replay applies. Also, if you are live streaming you can
stop seeking back if the play head hit the end of the live window.

 

\
\

### Additional Considerations {#ClosedCaptionsSupport-AdditionalConsiderations}

Although **Closed Captioning** and **Subtitles** are two different
things and server separate functions, both functions reside within
the [Video node](https://sdkdocs.roku.com/display/sdkdoc/Video).

One important consideration with the rules outlined above is that
the [Roku Ad
Framework](https://blog.roku.com/developer/2016/02/10/roku-ad-framework/) (RAF)
will turn off **trickplay** and the **instant replay** for the duration
of an ad. If you are using server-stitched, it is up to the channel to
disable this with **videoplayer.enableUI**.

![](attachments/5440654/5440652.png)

 

Finally, note that the **fast forward**, **rewind**, and
the **left** & **right** arrows on the direction pad should move the
play head. 

\
Use **videoplayer.notificationInterval** events to simplify the channel
logic around this.

 

 

**Related Topics**

-   Video
    node: [sdkdocs.roku.com/display/sdkdoc/Video](https://sdkdocs.roku.com/display/sdkdoc/Video)
-   idDeviceInfo: [sdkdocs.roku.com/display/sdkdoc/ifDeviceInfo](https://sdkdocs.roku.com/display/sdkdoc/ifDeviceInfo)
-   Event
    loops: [sdkdocs.roku.com/display/sdkdoc/Event+Loops](https://sdkdocs.roku.com/display/sdkdoc/Event+Loops)
-   RAF
    overview: [blog.roku.com/developer/2016/02/10/roku-ad-framework/](https://blog.roku.com/developer/2016/02/10/roku-ad-framework/)\
    \

\
 {#ClosedCaptionsSupport-}
-

Non-Legacy Platforms {#ClosedCaptionsSupport-Non-LegacyPlatforms}
--------------------

\

The non-legacy Roku platforms also include a closed captions setting
menu (under the Settings menu option) which allows Roku users to control
how closed captions are rendered on the device. These settings let users
turn closed captions on and off, and to customize various caption
properties such as font size, color, etc. These settings are available
to developers via APIs defined on the roDeviceInfo component. It is not
necessary for channels to implement their own closed caption settings
UI, as the state of the global settings can be queried using these new
API functions. Details of the global closed caption settings APIs can be
found here.

Roku SMPTE-TT Support Details {#ClosedCaptionsSupport-RokuSMPTE-TTSupportDetails}
-----------------------------

Roku has partially implemented the SMPTE-TT TTML spec that can be
referenced
here: [http://www.w3.org/TR/ttaf1-dfxp/](http://www.w3.org/TR/ttaf1-dfxp/). Roku
makes no claim of even minimal compliance. The link to the TTML spec is
provided only for discussion on features we have implemented. Roku's
TTML parser will recognize regions, styles, and spans. The captions are
recognized as "p" paragraph elements with a "begin" and "end" time.
Roku's TTML does not recognize the "duration" attribute for captions.

Roku's Caption rendering will always use a build in Gotham font
regardless of any font specified in the TTML. Likewise, font styles
(like italics or Bold) are also ignored. However, the Roku Caption
rendering will make the best guess effort at choosing the corresponding
font size in the system Gotham font using the specified font size in the
TTML.

Roku's TTML parser recognizes sufficient stylings to render colors,
positions, and alignments either on an absolute or percentage offset.
Namespaces do not cause a problem for the parser, but they are not
validated either.

The Roku TTML parser recognizes the following elements from Section 7 of
the TTML spec that specify the structure and principal content aspects
of a document instance:

-   [**7.1.1
    tt**](http://www.w3.org/TR/ttaf1-dfxp/#document-structure-vocabulary-tt)

-   [**7.1.2
    head**](http://www.w3.org/TR/ttaf1-dfxp/#document-structure-vocabulary-head)

-   [**7.1.3
    body**](http://www.w3.org/TR/ttaf1-dfxp/#document-structure-vocabulary-body)

-   [**7.1.4
    div**](http://www.w3.org/TR/ttaf1-dfxp/#content-vocabulary-div)

-   **[7.1.5 p](http://www.w3.org/TR/ttaf1-dfxp/#content-vocabulary-p)**

-   **[7.1.6
    span](http://www.w3.org/TR/ttaf1-dfxp/#content-vocabulary-span)**

The Roku TTML parser recognizes the following elements from Section 8 of
the TTML spec that specify the structure and principal styling aspects
of a document instance:

-   [**8.1.1
    styling**](http://www.w3.org/TR/ttaf1-dfxp/#styling-vocabulary-styling)

-   [**8.1.2
    style**](http://www.w3.org/TR/ttaf1-dfxp/#styling-vocabulary-style)

The Roku TTML parser recognizes the following styling elements from
Section 8.2 of the TTML spec:

-   [**8.2.2
    backgroundColor**](http://www.w3.org/TR/ttaf1-dfxp/#style-attribute-backgroundColor)

-   [**8.2.3
    color**](http://www.w3.org/TR/ttaf1-dfxp/#style-attribute-color)

-   [**8.2.6
    displayAlign**](http://www.w3.org/TR/ttaf1-dfxp/#style-attribute-displayAlign)

-   [**8.2.7
    extent**](http://www.w3.org/TR/ttaf1-dfxp/#style-attribute-extent)

-   [**8.2.9
    fontSize**](http://www.w3.org/TR/ttaf1-dfxp/#style-attribute-fontSize)

-   [**8.2.14
    origin**](http://www.w3.org/TR/ttaf1-dfxp/#style-attribute-origin)

-   **[8.2.18
    textAlign](http://www.w3.org/TR/ttaf1-dfxp/#style-attribute-textAlign)**

The Roku TTML parser recognizes the following layout elements from
Section 9 of the TTML spec:

-   [**9.1.1
    layout**](http://www.w3.org/TR/ttaf1-dfxp/#layout-vocabulary-layout)

-   [**9.1.2
    region**](http://www.w3.org/TR/ttaf1-dfxp/#layout-vocabulary-region)

The Roku TTML parser recognizes the following basic timing attributes
for use with timed elements:

-   [**10.2.1
    begin**](http://www.w3.org/TR/ttaf1-dfxp/#timing-attribute-begin)

-   **[10.2.2
    end](http://www.w3.org/TR/ttaf1-dfxp/#timing-attribute-end)**

EIA-608 {#ClosedCaptionsSupport-EIA-608}
-------

Roku supports EIA-608 closed caption data (analog TV format)
encapsulated within a EIA-708 container (digital TV) in an H.264
elementary stream. EIA-608 captions are delivered as part of the video
stream itself. One benefit of this caption format is that there can be
multiple “channels” of captions within the stream. These separate
channels could be used for different languages, for example, English
captions on one channel, Spanish on another, and so forth.

To render EIA-608 captions from within BrightScript, simply set the
TrackName attribute of the SubtitleConfig content metadata parameter to
“eia608/n” where n is the caption channel. Also, add it to
SubtitleTracks to specify the correct language.

WebVTT {#ClosedCaptionsSupport-WebVTT}
------

Roku supports WebVTT captions if embedded in HLS streams or manifests.
As with the other closed caption formats, a channel specifies WebVTT
captions in the SubtitleTracks metadata. The **TrackName** property is
set to "webvtt/track" where **track** specifies the index of the caption
track to render.

Closed Caption Support Summary {#ClosedCaptionsSupport-ClosedCaptionSupportSummary}
------------------------------

Below is a summary of the closed caption formats supported by the
various video streaming technologies on Roku devices.

 

SMPTE-TT

EIA-608

WebVTT

MP4 VOD

Yes (external file only)

Yes (in stream only for all manifests containing AVC streams)

No

HLS VOD

Yes (external file only)

Yes (in stream only for all manifests containing AVC streams)

Yes (In a separate stream described in the manifest ( playlist for hls))

HLS Live

No

Yes (in stream only for all manifests containing AVC streams)

Yes  (In a separate stream described in the manifest ( playlist for
hls))

Smooth VOD

Yes (in stream or external file)

Yes (in stream only for all manifests containing AVC streams)

No

Smooth Live

Yes (in stream only)

Yes (in stream only for all manifests containing AVC streams)

No

DASH VOD

Yes (external file only)

Yes (in stream only for all manifests containing AVC streams)

No

Attachments: {#attachments .pageSectionTitle}
------------

![](images/icons/bullet_blue.gif)
[Roku-remote-control-star-button.png](attachments/5440654/5440648.png)
(image/png) \
 ![](images/icons/bullet_blue.gif) [image2017-7-13
8:40:18.png](attachments/5440654/5440649.png) (image/png) \
 ![](images/icons/bullet_blue.gif) [image2017-7-13
10:42:14.png](attachments/5440654/5440650.png) (image/png) \
 ![](images/icons/bullet_blue.gif)
[Roku-remote-control-replay-button.png](attachments/5440654/5440651.png)
(image/png) \
 ![](images/icons/bullet_blue.gif)
[Roku-remote-control-4-button.png](attachments/5440654/5440652.png)
(image/png) \
 ![](images/icons/bullet_blue.gif)
[caption\_dialog.png](attachments/5440654/5440653.png)
(application/octet-stream) \

Document generated by Confluence on Jan 23, 2018 17:12

[Atlassian](http://www.atlassian.com/)
