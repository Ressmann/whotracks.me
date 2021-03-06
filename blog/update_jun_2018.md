title: June Update - Do you consent?
subtitle: The rushed, rough and rogue UX of services getting you to opt-in.
author: privacy team
type: article
publish: True
date: 2018-06-07
tags: blog, update
header_img: blog/update_jun18/june_update18.png
+++

_This post is one of our regular monthly blogs accompanying an update to the data
displayed on WhoTracks.Me. In these posts we introduce what data has been added as well
as point out interesting trends and case-studies we found in the last month. Previous
month's posts can be found here: [May 2018](./update_may_2018.html), [April 2018](./update_apr_2018.html)._

This month the site has been updated with tracker data from 370 million page loads during May
2018. We've expanded the number of trackers shown further to over 1,000, and we now show information
for the top 1,750 websites. We also have published regional versions of the data for the US, France
and Germany, allowing regional disparities to be investigated. This regional data is not yet visible
on the site - regional stats are planned for an upcoming design update.

As we mentioned [last month](./update_may_2018.html), the [GDPR](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation)
has now come into force, which is expected to have an effect on how the data collected via online
tracking is handled. So far, the main observation is that sites have deployed complex consent
dialogs, trying to get users to consent to being tracked on their sites. We can already observe
the rise of third parties offering the services behind these consent dialogs.

Despite the changes in regulation, we see no evidence of a reduction in the number of third parties
loaded on websites this month (also when doing a week-by-week analysis). The average number of
third-parties loaded on popular websites remained at 8.5, which is the same as in April.

## Consent as a service

One observable result of the GDPR is a rise in the user of Consent Management Platforms (CMPs) by
websites. These services manage the cookie consent notices shown. Now that GDPR is in
place, European users should be informed of all services collecting data on the site, and be able to
opt-out of certain practices and data collection. This means that these CMPs have become much more
prominent, providing deeper controls, and propagating user consent to the third-party services.

The WhoTracks.Me data has tracked the rise of several CMPs appearing this month, as well as
existing providers increasing their presence. With our data we can detect where they are present
and then compare their approaches to asking for user consent, and we present a short survey of
these here:

### TrustArc

[TrustArc](https://www.trustarc.com/) (formally TRUSTe) have been providing cookie consent dialogs
since the original ePrivacy regulation introduce the concept. [Our data shows](../trackers/truste_consent.html)
that their reach has doubled in recent months as they have obviously gained customers using their
services for GDPR compliance.

Their familiar consent popup now has improved opt-out capabilities. These are however hidden behind
a _More Information_ link. This popup has not changed from the pre-GDPR options, so users may not
realise that improved opt-out options are hidden behind this button. The styling of the button as
a link also does not suggest that consent can be configured.

<img class="img-responsive" src="../static/img/blog/update_jun18/trustarc_1.png" alt="TrustArc Consent popup" />
<p class="img-caption">TrustArc: Consent popup.</p>

The _More Information_ button leads to a screen where consent can be specified for different cookie
types. On the tested site ([MyFitnessPal.com](../websites/myfitnesspal.com.html)) this view had
all types enabled by default.

<img class="img-responsive" src="../static/img/blog/update_jun18/trustarc_2.png" alt="TrustArc Consent settings" />
<p class="img-caption">TrustArc: Choosing consent settings.</p>

After submitting, we hit a processing dialog. In our testing this processing takes minutes to complete,
and blocks access to the underlying page until it completes. This poor user-experience is may
reduce the amount of users who will actually take the time to express consent settings. After
waiting minutes once, they may subsequently simply agree to all, or just abandon sites who present
this dialog.

<img class="img-responsive" src="../static/img/blog/update_jun18/trustarc_3.png" alt="TrustArc Consent submission" />
<p class="img-caption">TrustArc: Processing......</p>

Another manifestation of the TrustArc CMP, found on [Weather Underground](../websites/wunderground.com.html)
provides a more detailed popup, including details of the third-parties in each category. This
version, however, also suffers from a long processing time once consent has been expressed.

<img class="img-responsive" src="../static/img/blog/update_jun18/trustarc_4.png" alt="TrustArc detailed consent settings" />
<p class="img-caption">TrustArc: Detailed view</p>

### IAB Consent Framework

In response to the GDPR, the [IAB](https://iabtechlab.com/) proposed a framework for propagating
user consent through ad-networks. The [GDPR Transparency and Consent Framework](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/)
aims to create a standardised expression of consent which can be passed around ad networks.

In this framework, CMPs are [registered](http://advertisingconsent.eu/iab-europe-transparency-consent-framework-list-of-registered-cmps/)
and a first party cookie specifies which CMP obtained the consent on this site, and which
purposes and vendors are permitted. The CMP code and vendor list are served from a single domain,
`consensu.org`, which means we can measure that it is already in use on [0.5% of sites](../trackers/iab_consent.html).

An example of this framework can be seen on [SourceForge](../websites/sourceforge.net.html). In
this case, [Quantserve](../trackers/quantcast.html) acts as the CMP to set the IAB consent cookie.
Note this framework allows first-party and third-party consents to be specified separately for a
standardised set of purposes.

<div class="row">
  <div class="col-md-6 col-xs-12">
    <img class="img-responsive" src="../static/img/blog/update_jun18/iab_prompt.png" alt="Sourceforge Consent popup" />
  </div>
  <div class="col-md-6 col-xs-12">
    <img class="img-responsive" src="../static/img/blog/update_jun18/iab_settings.png" alt="Sourceforge Consent settings" />
  </div>
</div>
<p class="img-caption">Quantserve consent dialog, using the IAB framework</p>

Unlike the TrustArc consent, opting out in this dialog is instant. Furthermore, in testing, all
options were disabled by default, and a blanket opt out is also made easy.

### Cookiebot

A new service which appeared in our data this month is [Cookiebot](https://www.cookiebot.com/en/),
which is already present on [0.3% of websites](../trackers/cookiebot.html).
They provide a very simple clean dialog to allow quick specification of consent.

One site using this service is [Gitlab](../websites/gitlab.com.html). We note here that all options
are selected by default, and consent is assumed even if the user does not click 'OK'.

<img class="img-responsive" src="../static/img/blog/update_jun18/cookiebot_1.png" alt="Cookiebot dialog basic view" />
<p class="img-caption">Cookiebot dialog on gitlab.com.</p>

The 'Show details' button provides more detailed information about which providers and cookies
fall under each category.

<img class="img-responsive" src="../static/img/blog/update_jun18/cookiebot_2.png" alt="Cookiebot dialog detailed view" />
<p class="img-caption">Cookiebot detailed view.</p>

In this case the opt-out is also instant.

### OneTrust

Lastly, [OneTrust](https://www.onetrust.com/). This service does not appear among the top trackers
this month, however we can still see its presence on some sites.

One feature of this CMP seems to be its configurability. We find multiple different levels of
options available on different sites. Firstly, the cookie banner, shown on the bottom of the
page, may provide configurability via a 'More Information' button. For example on
[CNN](../websites/cnn.com.html):

<img class="img-responsive" src="../static/img/blog/update_jun18/onetrust_banner.png" alt="OneTrust banner on cnn.com" />
<p class="img-caption">OneTrust banner on CNN</p>

However, we also found examples where one can only accept, for example on [express.de](../websites/express.de.html):

<img class="img-responsive" src="../static/img/blog/update_jun18/onetrust_banner_noopt.png" alt="OneTrust banner on express.de" />
<p class="img-caption">OneTrust banner on express.de</p>

Secondly, the information dialog may or may not allow the user to opt-out. We can compare the
dialogs on [cnn.com](../websites/cnn.com.html) and [mailchimp.com](../websites/mailchimp.com.html).
On MailChimp, all non-essential cookie categories offer an opt-out, while on CNN the interface
only provides information about the category, with no options for the user except accept.

<div class="row">
  <div class="col-md-6 col-xs-12">
    <img class="img-responsive" src="../static/img/blog/update_jun18/onetrust_cnn.png" alt="OneTrust Privacy Preference Center on cnn.com"/>
  </div>
  <div class="col-md-6 col-xs-12">
    <img class="img-responsive" src="../static/img/blog/update_jun18/onetrust_mailchimp.png" alt="OneTrust Privacy Preference Center on MailChimp.com"/>
  </div>
</div>
<p class="img-caption">OneTrust Preference Center on cnn.com and mailchimp.com</p>

Again, opt-out (when available) is instant.

## Conclusion

Since GDPR came into force we have seen a marked increase in cookie consent, many of which block
access to the page until consent is obtained. These CMPs aim to standardise the process, making it
easier for users to quickly express their preferences. However, as we have seen in this article,
the current main CMPs differ in their approach to the problem.

As many publishers main aim from deploying a CMP will be to achieve maximum opt-in, while remaining compliant
with the law, there is a strong incentive for platforms to deceive users into consenting. Examples
such as TrustArc show some dark patterns which nudge users to accepting all. Platforms which
provide clear opt-outs, and leave options unticked by default may suffer for providing a better
user experience.

The importance of consent for publishers who rely on advertising revenue, and their willingness to
test users' goodwill in order to obtain consent can be seen from this dialog, seen when visiting [GHacks](https://www.ghacks.net/)
having opted out of data collection.

<img class="img-responsive" src="../static/img/blog/update_jun18/ghacks_opted_out.png" alt="Dialog asking for user to reconsider consent settings"/>
<p class="img-caption">Dialog on seen ghacks.net.</p>

Despite [criticism](https://martechtoday.com/pagefair-iab-consent-framework-violates-gdpr-212428)
of its method of communicating user consent, the openness of the IAB Framework is welcome, as it
opens up the possibility for standardised browser interfaces for consent. This would take control
of the consent UX out of the hands of site owners, who will be incentivised to 'cheat', and make
it neutral and consistent.
