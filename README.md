# OnRecruit Trackingcodes

Track all the events and pages visisted of your candidates and correlate them to each job, channel and candidate.

## Usage
Track actions like pageveiws, jobviews, apply starts, conversions and so on. These actions actions can be used by OnRecruit to give hiring funnel insights, candidate journeys, retarget candidates, find new candidates, track conversions and attribute the channels leading up to a conversions.

The trackingcode comes with standard events that you scan use on your website. Next to that you can ask your OnRecruit accountmanager to register custom events. This way you can track custom events that happen on your website such as: newsletter signup and saved job.

## Implementation

Below you can find the the snippet which you have to add before the ending *</head>* tag in the page's HTML:
```html
<!-- OnRecruit Analytics Code -->
<script>
!function(o,r,e,v,n,t,s){if(o.orq)return;n=o.orq=function(){n.callMethod?
n.callMethod.apply(n,arguments):n.queue.push(arguments)};if(!o._orq)o._orq=n;
n.push=n;n.loaded=!0;n.version='3.0';n.queue=[];t=r.createElement(e);t.async=!0;
t.src=v;s=r.getElementsByTagName(e)[0];s.parentNode.insertBefore(t,s)}(window,
document,'script','//analytics.onrecruit.net/static/scripts/v3/analytics.js?v=' + Math.random());

// in case of different subdomains
orq('init', '<ONRECRUIT_ID>', '<CUSTOMER_NAME>', {domain: "example.com"});
// in regular case
orq('init', '<ONRECRUIT_ID>', '<CUSTOMER_NAME>');
orq('track', 'jobview');
</script>
<!-- End OnRecruit Analytics Code -->
```

OnRecruit will supply you with the correct `<ONRECRUIT_ID>` and `<CUSTOMER_NAME>`. As you can see `orq('track', 'jobview');` refers to a view on the job page. Next to that other events are also possible:

|Event|Command|Explanation|
|-----|-------|-----------|
|Job view|`orq('track','jobview');`|This code needs to be placed on the job detail page and tracks a job view.|
|Page view|`orq('track', 'pageview');`|This code needs to be placed on other pages than job detail pages and tracks a page view.|
|Conversion|`orq('track', 'conversion');`|This code needs to be placed on the thank you for applying page.|
|Apply start|`orq('track', 'apply-start');`|This code tracks an apply start and could be attached to an apply button. Below we'll cover how to do this.|
|Custom event|`orq('track', '<custom_event>');`|A `<custom event>` can be registered via your OnRecruit accountmanager so that you can track other events. Your accountmanager will tell what should come in the place of `<custom_event>`.

## Attaching the event tracking to a click on your website
OnRecruit events, except job views and page views, are also attachable to clicks HTML elements in your website, for example apply button or Newsletter signup button.

The way you can manually implement this is as follows:
```html
<!-- Somewhere there is an apply button -->
<a id="apply-btn" class="apply-now">Apply now!</a>

<script type="text/javascript">
// It is important however that the snippet above is present just 
// before the closing </head> tag in the HTML.
//
// Add 'apply-start' event to click on apply button
//
// After 'track' and 'apply-start', the element can be given as 3rd argument. As 4th argument 
// you can specify which text it should contain.
orq('track', 'apply-start', 'a', 'Apply now');

// An other way of attaching to this button is by making use of the javascript query selector:
orq('track', 'apply-start', 'a[id="apply-btn"]');
// or
orq('track', 'apply-start', 'a#apply-btn');
// or
orq('track', 'apply-start', 'a[class="apply-now"]');
// or
orq('track', 'apply-start', 'a.apply-now');
</script>
```

# Thank you for applying pages
If you don't have access to your thank you for applying page, there are 2 options:
1. OnRecruit will send you a `<img>`-snippet so that you can place the trackingpixel. Some ATS-es only accept trackingpixels instead of javascript codes.
2. You can attach the `orq('track', 'conversion');` code to an apply button via the above snippet.


# Questions?
If you have any questions feel free to contact your OnRecruit Customer Success Manager!
