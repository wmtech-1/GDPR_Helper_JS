# Helper JavaScript
Publishers who do not want a CMP (Consent Management Provider) UI to appear as a pop-up on their site still need the ability to pass a "consent" signal downstream to process bid requests appropriately. Such publishers need a way to operationalize their understanding that they have consent from their users while satisfying the technical need to pass on consent objects.

The PubMatic Helper JavaScript code generates a consent object for every bid request. Consent is provided for all the vendors listed in the IAB EU Transparency & Consent Framework Global Vendor List.

 
## The Helper JavaScript:

+ Implements all functions, such as getConsentData and getVendorConsents, which are detailed in the IAB Consent Management Provider JavaScript API.
+ Relies on IAB's vendor list to construct the consent string.
+ Requires that publishers install it on every page.
+ Works with any client (e.g., PubMatic's OpenWrap) that integrates with IAB's Consent Management Framework.

## Important Notes
+ By using the Helper JavaScript, you confirm that you have obtained required consents from end users.
+ This code was forked from https://github.com/appnexus/cmp

## Download Script

+ [`./build/cmp.complete.bundle.js`](https://raw.githubusercontent.com/wmtech-1/GDPR_Helper_JS/master/build/cmp.complete.bundle.js) - Helper Script to include on your site

## How to Include on Web Page
```html
<!-- 
	Publishers will need to add following script tag on their web-pages.
	This tag needs to be placed above any other ad tag that needs to pass consent info.
-->
<script src="<<HTTP_PATH_TO_HOSTED_cmp.complete.bundle.js>>"></script>
```

### Sample Web Page
```html
<!DOCTYPE html>
<html>
    
    <head>
        <!-- 
        Publishers will need to add following script tag on their web-pages.
	This tag needs to be placed above any other ad tag that needs to pass consent info.

        -->
        <script src="<<HTTP_PATH_TO_HOSTED_cmp.complete.bundle.js>>"></script>
    </head>
    
    <body>
        <h3>
            Demo
        </h3>
        <!-- 
	Following is just an example that simulates the calls an ad tag would make if it's ready to integrate with
	IAB's Consent Framework JS 1.1
        Publishers do not need to put following code on their web-page. 
        -->
        <script>
            setTimeout(function() {
                window.__cmp('getVendorConsents', null, function(result) {
                    console.log('getVendorConsents callback result:\n' + JSON.stringify(result, null, 2));
                });

                window.__cmp('getConsentData', null, function(result) {
                    console.log(result);
                });
            }, 3000);
        </script>
    </body>

</html>
```
