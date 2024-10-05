[Skip to main content](#hcfe-content)

# \[GA4\] Enhanced measurement events

Discover how to enable and disable enhanced measurement events and learn more about which parameters are collected for each event.

Enhanced measurement lets you measure interactions with your content by enabling options (events) in the Google Analytics interface. No code changes are required. When you enable these options for a web data stream, your Google Analytics tag starts sending events right away.

Before turning on the enhanced measurement feature, be sure you understand each option and what enhanced data will be collected. You can also turn off specific measurement options in settings.

You're required to ensure that no [personally identifiable information](/analytics/answer/7686480) is collected.

## Enable or disable enhanced measurement events

1. In [Admin](/analytics/answer/6132368), under _Data collection and modification_, click [**Data streams**](https://analytics.google.com/analytics/web/#/?pagename=admin-streams&utm_source=gahc&utm_medium=dlinks).




**Note**: The previous link opens to the last Analytics property you accessed. You can [change the property](/analytics/answer/12813202) using the property selector. You must be an [Editor or above](/analytics/answer/9305587) at the property level to enable or disable enhanced measurement events.

2. Click the name of your data stream.
3. Under _Enhanced measurement_, slide the switch **On** to enable all options.


    Click ![Settings](https://support.google.com/lh3.googleusercontent.com/PzFeiQQaPASuntRuvWiXoqZjQqUj0s0q0w_jI4Nx9vL6x7rGmmS9f-xQr1Kj9S91WMlm=h36) to edit individual options as needed.

![Enable enhanced measurement slider](https://support.google.com/storage.googleapis.com/support-kms-prod/jSN8lyeZNXQYjaxLguisELX1ojlvMmO3iDEJ)

If you use [the Google tag](/analytics/answer/11994839) on your website, you also need to make sure that each event is enabled for automatic event detection for your Google tag. By default, all event types are enabled. [Learn more about your Google tag settings](/analytics/answer/12131703#Event&zippy=%2Cmanage-automatic-event-detection)

## Events measurement and parameters

The following table explains when events are triggered, and which parameters are collected for each event. You can find enhanced data about each triggered event in the Events report within [the Engagement topic](/analytics/answer/10999789). Click the event name in the report for more information on the event.

To understand each event parameter listed below and how each parameter updates a dimension or metric in Google Analytics, see [Google Analytics event parameters](/analytics/table/13594742).

| Measurement option / event | Triggered... | Parameters |
| --- | --- | --- |
| Page views<br>page\_view | each time the page loads or the browser history state is changed by the active site<br>This event is collected automatically. You cannot turn off collection.<br>An advanced setting on this option controls whether the event is sent based on browser-history events. This measurement option listens for pushState, popState, and replaceState.<br>The event populates the [_Views_](/analytics/answer/9143382#page-screen-metrics) metric. The parameters populate the following dimensions:<br>- [_Page location_](/analytics/answer/9143382#page-screen) (from page\_location)<br>- [_Page referrer_](/analytics/answer/9143382#page-screen) (from page\_referrer) | page\_location (page URL), page\_referrer (previous page URL) |
| Scrolls<br>scroll | the first time a user reaches the bottom of each page (i.e., when a 90% vertical depth becomes visible)<br>The event populates the [_Percent scrolled_](/analytics/answer/9143382#general) dimension. | engagement\_time\_msec |
| Outbound clicks<br>click | each time a user clicks a link that leads away from the current domain<br>By default, outbound click events will occur for all links leading away from the current domain. Links to domains configured for [cross-domain measurement](/analytics/answer/10071811) will not trigger outbound click events.<br>The parameters populate the following dimensions:<br>- [_Link classes_](/analytics/answer/9143382#link) (from link\_classes)<br>- [_Link domain_](/analytics/answer/9143382#link) (from link\_domain)<br>- [_Link ID_](/analytics/answer/9143382#link) (from link\_id)<br>- [_Link URL_](/analytics/answer/9143382#link) (from link\_url)<br>- [_Outbound_](/analytics/answer/9143382#link) (from outbound) | link\_classes, link\_domain, link\_id, link\_url, outbound (boolean) |
| Site search<br>view\_search\_results | each time a user is presented with a search results page, as indicated by the presence of a URL query parameter<br> By default, the event is triggered based on the presence of one of the following 5 query parameters in the URL:<br> <br>- q<br>- s<br>- search<br>- query<br>- keyword<br>You can optionally configure this event to look for other URL query parameters.<br>The search\_term parameter populates the [_Search term_](/analytics/answer/9143382#general) dimension. | search\_term, optionally ‘q\_<additional key="">’ (where <additional key=""> matches an additional query parameter you specify to be collected under advanced settings).<br>Note: This event only sends the unique\_search\_term parameter when it has a value of 1 (i.e. when the string is unique to that session). |
| Video engagement<br>video\_start<br>video\_progress<br>video\_complete | For YouTube embedded videos that have [JS API support](https://developers.google.com/youtube/player_parameters#enablejsapi) enabled, the following events are triggered:<br> <br>- video\_start: when the video starts playing<br>- video\_progress: when the video progresses past 10%, 25%, 50%, and 75% duration time<br>- video\_complete: when the video ends<br>The parameters populate the following dimensions:<br>- [_Video provider_](/analytics/answer/9143382#video) (from video\_provider)<br>- [_Video title_](/analytics/answer/9143382#video) (from video\_title)<br>- [_Video URL_](/analytics/answer/9143382#video) (from video\_url)<br>- [_Visible_](/analytics/answer/9143382#general) (from visible) | video\_current\_time, video\_duration, video\_percent, video\_provider, video\_title, video\_url, visible (boolean) |
| File downloads<br>file\_download | when a user clicks a link leading to a file (with a common file extension) of the following types:<br> <br>- document<br>- text<br>- executable<br>- presentation<br>- compressed file<br>- video<br>- audio<br>File extensions that match the following regex will trigger the event:<br>pdf\|xlsx?\|docx?\|txt\|rtf\|csv\|exe\|key\|pp(s\|t\|tx)\|<br>7z\|pkg\|rar\|gz\|zip\|avi\|mov\|mp4\|mpe?g\|wmv\|midi?\|mp3\|wav\|wma<br>The parameters populate the following dimensions:<br>- [_File extension_](/analytics/answer/9143382#general) (from file\_extension)<br>- [_File name_](/analytics/answer/9143382#general) (from file\_name)<br>- [_Link classes_](/analytics/answer/9143382#link) (from link\_classes)<br>- [_Link ID_](/analytics/answer/9143382#link) (from link\_id)<br>- [_Link text_](/analytics/answer/9143382#link) (from link\_text)<br>- [_Link URL_](/analytics/answer/9143382#link) (from link\_url) | file\_extension, file\_name, link\_classes, link\_id, link\_text, link\_url |
| Form interactions<br>form\_start<br>form\_submit | 'form\_start': the first time a user interacts with a form in a session<br>'form\_submit': when the user submits a form<br>You can use these two events to see how many users started to fill out a form and compare the information to users who submitted the form.<br>Note: You can only use the parameters in your reports if you [create custom dimensions](/analytics/answer/10075209) for them. | form\_start<br>- form\_id: HTML id attribute of the <form> DOM element<br>- form\_name: HTML name attribute of the <form> DOM element<br>- form\_destination: URL to which the form is being submitted<br>form\_submit<br>- form\_id: HTML id attribute of the <form> DOM element<br>- form\_name: HTML name attribute of the <form> DOM element<br>- form\_destination: URL to which the form is being submitted<br>- form\_submit\_text: text of the submit button, if present |

Give feedback about this article

Choose a section to give feedback on

## Was this helpful?

How can we improve it?

YesNo

Submit

## Need more help?

### Try these next steps:

[Post to the help community  Get answers from community members](/analytics/community?hl=en&help_center_link=[9216061,%22[GA4]%20Enhanced%20measurement%20events%22]) [Contact usTell us more and we’ll help you get there](/analytics/gethelp)

true

313829339104995266

true

Search

Clear search

Close search

Main menu

Google apps

Search Help Center

true

true

true

[Google Help](/)

[Help Center](/analytics/?hl=en)

[Get started with Analytics](/analytics/topic/14090456?hl=en&ref_topic=3544742,2986333,) [Collect and manage data](/analytics/topic/14132937?hl=en&ref_topic=3544742,2986333,) [Report and explore](/analytics/topic/9228654?hl=en&ref_topic=3544742,2986333,) [Advertising and attribution](/analytics/topic/10595744?hl=en&ref_topic=3544742,2986333,) [Audiences and remarketing](/analytics/topic/9303474?hl=en&ref_topic=3544742,2986333,) [Manage accounts, properties, and users](/analytics/topic/9303569?hl=en&ref_topic=3544742,2986333,) [Google Analytics 360](/analytics/topic/10985992?hl=en&ref_topic=3544742,2986333,) [Migrate from UA to GA4 \[Legacy\]](/analytics/topic/10737980?hl=en&ref_topic=3544742,2986333,) [Policies and data privacy](/analytics/topic/1008008?hl=en&ref_topic=3544742,2986333,)

[Community](/analytics/community?hl=en&help_center_link=[9216061,%22[GA4]%20Enhanced%20measurement%20events%22]) [Analytics](//www.google.com/analytics/)

[Privacy Policy](//www.google.com/intl/en/privacy.html) [Terms of Service](https://www.google.com/accounts/TOS) [Submit feedback](about:invalid#zjslayoutz)

[Introduction to Analytics](/analytics/topic/14089939?hl=en&ref_topic=14090456,3544742,2986333,) [Set up Analytics](/analytics/topic/14088998?hl=en&ref_topic=14090456,3544742,2986333,) [Guides and videos](/analytics/topic/14089317?hl=en&ref_topic=14090456,3544742,2986333,) [Troubleshoot](/analytics/topic/13614110?hl=en&ref_topic=14090456,3544742,2986333,) [Glossary](/analytics/topic/9355633?hl=en&ref_topic=14090456,3544742,2986333,)

[Events and key events](/analytics/topic/14710097?hl=en&ref_topic=14132937,3544742,2986333,) [Import data from external systems](/analytics/topic/10054560?hl=en&ref_topic=14132937,3544742,2986333,) [Integrations](/analytics/topic/9306488?hl=en&ref_topic=14132937,3544742,2986333,) [Measure ecommerce](/analytics/topic/12270146?hl=en&ref_topic=14132937,3544742,2986333,) [Measure lead generation](/analytics/topic/12943241?hl=en&ref_topic=14132937,3544742,2986333,) [\[GA4\] First-party data](/analytics/topic/14272008?hl=en&ref_topic=14132937,3544742,2986333,)

[Reports](/analytics/topic/13818299?hl=en&ref_topic=9228654,3544742,2986333,) [Explorations](/analytics/topic/9266525?hl=en&ref_topic=9228654,3544742,2986333,) [Dimensions and metrics](/analytics/topic/11151952?hl=en&ref_topic=9228654,3544742,2986333,) [Analytics Intelligence](/analytics/topic/10333392?hl=en&ref_topic=9228654,3544742,2986333,) [The Analytics app](/analytics/topic/12677004?hl=en&ref_topic=9228654,3544742,2986333,) [How data is stored and displayed](/analytics/topic/13987797?hl=en&ref_topic=9228654,3544742,2986333,) [Regular expressions \[Legacy\]](/analytics/topic/1034375?hl=en&ref_topic=9228654,3544742,2986333,) [\[GA4\] Mini guides: Reporting](/analytics/topic/13137724?hl=en&ref_topic=9228654,3544742,2986333,) [\[GA4\] Mini guides: Explorations](/analytics/topic/13138758?hl=en&ref_topic=9228654,3544742,2986333,)

[Understand advertising](/analytics/topic/10604827?hl=en&ref_topic=10595744,3544742,2986333,) [Understand attribution](/analytics/topic/10597959?hl=en&ref_topic=10595744,3544742,2986333,) [Manage and configure attribution](/analytics/topic/10595462?hl=en&ref_topic=10595744,3544742,2986333,) [iOS conversion measurement](/analytics/topic/13165701?hl=en&ref_topic=10595744,3544742,2986333,)

[\[GA4\] Set up audiences](/analytics/topic/14272803?hl=en&ref_topic=9303474,3544742,2986333,) [\[GA4\] Use audiences for advertising and remarketing](/analytics/topic/14277381?hl=en&ref_topic=9303474,3544742,2986333,) [\[GA4\] Audiences for common marketing objectives](/analytics/topic/13286687?hl=en&ref_topic=9303474,3544742,2986333,) [\[GA4\] Troubleshoot audiences](/analytics/topic/14277483?hl=en&ref_topic=9303474,3544742,2986333,)

[\[GA4\] Subproperties](/analytics/topic/11525653?hl=en&ref_topic=9303569,3544742,2986333,) [\[GA4\] Roll-up properties](/analytics/topic/11525654?hl=en&ref_topic=9303569,3544742,2986333,)

[\[GA4\] Subproperties](/analytics/topic/11525653?hl=en&ref_topic=10985992,3544742,2986333,) [\[GA4\] Roll-up properties](/analytics/topic/11525654?hl=en&ref_topic=10985992,3544742,2986333,) [How data is stored and displayed](/analytics/topic/13987797?hl=en&ref_topic=10985992,3544742,2986333,)

[Data privacy and security](/analytics/topic/2919631?hl=en&ref_topic=1008008,3544742,2986333,)

true

true

69256

true

## What is the issue with this selection?

Inaccurate - doesn't match what I see in the product

Hard to understand - unclear or translation is wrong

Missing info - relevant but not comprehensive

Irrelevant - doesn’t match the title and / or my expectations

Minor errors - formatting issues, typos, and / or broken links

Other suggestions - ideas to improve the content

## Share additional info or suggestions

​

​

Do not share any personal info

Cancel

Submit

By continuing, you agree Google uses your answers, account & system info to improve services, per our [Privacy](https://myaccount.google.com/privacypolicy?hl=en) & [Terms](https://policies.google.com/terms?hl=en).

false