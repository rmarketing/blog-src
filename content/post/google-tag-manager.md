+++
Categories = ["Online Marketing","Google Analytics"]
date = "2017-03-25T11:09:05+01:00"
title = "Set Up Google Tag Manager in 3 Steps"
Tags = ["Online Marketing","Google Analytics"]
Description = ""

+++

As discussed at the end of the previous post,
we recommend **Google Tag Manager (GTM)** as an umbrella for all your tracking
tokens and code snippets. Even if Google Analytics is the only service you use,
**GTM** remains a simple and expandable option.

The big advantage of **GTM** is that you only have to add a single code
snippet from Google Tag Manager to your website instead of including multiple
tracking snippets from services like Google Analytics, AdWords,
AdWords Remarketing, Facebook, etc. Through **GTM**'s web interface, you can
manage all these tracking snippets. That way you are flexible to make changes
or extend your tracking implementation in the future without touching the
code of your website.

### Setup Google Tag Manager (GTM)

#### 1. Create GTM Account

To get started managing your tags using Tag Manager:

1. Go to <https://www.google.com/analytics/tag-manager/> and create a Tag Manager account (you can use your existing Google account).
2. Create a container for your site or app.

![Creating an account in Google Tag Manager](/blog/images/gtm1_small.png)


#### 2. Add the Google Tag Manager container to your website

Assuming you created the Google Tag Manager container in the previous step, you automatically will get directed to the page with the code snippet for the Tag Manager container. Copy the code and add it to all your pages – it’s recommended to add the code right after the opening <body> tag on all your pages. If you’re using a Content Management System like Wordpress, Shopify, Magento or anything alike you should insert it in the template that serves all pages.

If you are using Google Analytics tracking without Google Tag Manager already, it is now time to replace all existing Google Analytics code snippets with the Google Tag Manager code snippet.

For web pages: Add the container snippet to your site while removing any existing tags.
For mobile apps: Implementation of Tag Manager for mobile apps is done in conjunction with the Firebase SDK. See the Google Android or Apple iOS documentation for more information.

#### 3. Create the Google Analytics tag

Now we can create the tag for Google Analytics within Google Tag Manager.

In your Google Tag Manager Account proceed with the following steps:

1. Create Tag
2. Choose product: "Google Analytics"
3. Choose Tag Type: "Universal Analytics"
3. Configure Tag: Paste the "UA-**********" Tracking ID from Google Analytics. (You will find the Google Analytics Tracking ID in the settings of your Google Analytics Account under Property > Tracking Info.) Set track type to "Page View".
4. Fire On: All Pages
5. Create Tag

![Creating an Google Analytics tag in GTM](/blog/images/gtm2_small.png)

Now you have created the Google Analytics tag. Moreover you can watch this Youtube video that summarizes step 1. - 5:

{{< youtube irNpwlEn1ZM >}}

#### 4. Publish and test the tag.

Now it’s time to preview the site, make sure the tracking works as expected and the tag is firing correctly.

From the Tags page, click Create Version. A page appears that summarizes all the tags, rules, and macros in the container. Click Save and Preview. When your website appears properly in the preview mode, you can go back and click Publish.

Google provides a really useful browser extension for Google Chrome that allows you to test if the Google Tag Manager container and the Google Analytics tag is working properly.
In the Google Chrome Browser go to Settings > Extension and add the **Google Tag Assistant** extension. Now visit your website and click on the Google Tag Assistant icon in top right of the Chrome browser window. The Google Tag Assistant shows green light for the Tag Manager container and the Google Analytics tag.
