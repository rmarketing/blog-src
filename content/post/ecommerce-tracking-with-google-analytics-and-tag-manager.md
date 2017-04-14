+++
date = "2017-04-05T21:42:05+02:00"
title = "E-commerce Tracking With Google Analytics and Google Tag Manager"
Categories = ["Online Marketing","Google Analytics"]
Tags = ["Online Marketing","Google Analytics"]
Description = "Detailed guideline to set up and configure e-commerce tracking with Google Analytics."

+++

At this point, we assume that you have successfully added Google Analytics using Google Tag Manager to your website (If not, check the previous posts). In this post we will explain how to add e-commerce tracking to the mix. E-commerce tracking means tracking sales data at checkout (that is, through the thank you or confirmation page of a shop). Such a confirmation page should include all information about a visitor's shopping basket: amount of goods, products, product related revenues, value per order, taxes etc. In other words, the confirmation page features a data layer which is should be pretty relevant to online shop owners. An yup, our combo of Google Tag Manager and Google Analytics can extract this information with ease. This post explains in greater detail how a such a data layer works and how it can be exploited using Google's e-commerce tracking.

<!-- more -->

In Analytics, there are two main types of e-commerce tracking methods:

**Standard e-commerce** reports in Google Analytics allow you to analyze purchase activity on your site or app. You can see product and transaction information, average order value, e-commerce conversion rate, time to purchase, and other data.

**Enhanced e-commerce** adds functionality allowing you to see when customers have added items to their shopping carts, when they have started the checkout process, and when they have completed a purchase. You can also use Enhanced E-commerce to identify segments of customers who are falling out of the shopping funnel.

Both methods of e-commerce tracking can be implemented using Google Tag Manager. In this post we will focus on **standard e-commerce tracking**. Before we start with the implementation of the standard e-commerce tracking, let's have a look at a really useful video that might clarify further questions upfront.

{{< youtube ZKjlIhFJMCU >}}

The setup of standard e-commerce tracking is split into three steps:

  1. Installation of the data layer
  2. Testing the data layer
  3. Configuration of Google Tag Manager

1. Embed data layer object on the thank you page.

Here is what a data layer could look like:

```
{   
   'event': 'gtm4wp.orderCompleted',
   'transactionId': '1234',
   'transactionAffiliation': 'Acme Clothing',
   'transactionTotal': 38.26,
   'transactionTax': 1.29,
   'transactionShipping': 5,
   'transactionProducts': [{
       'sku': 'DD44',
       'name': 'T-Shirt',
       'category': 'Apparel',
       'price': 11.99,
       'quantity': 1
   },{
       'sku': 'AA1243544',
       'name': 'Socks',
       'category': 'Apparel',
       'price': 9.99,
       'quantity': 2
   }]
}
```

It is possible to integrate the data layer manually using javascript. However, we recommend to use the build-in feature of your e-commerce framework to add the data layer to the order confirmation page. Woo Commerce, Shopify, Magento and many common e-commerce frameworks sport plugins to integrate a data layer on the confirmation page.

3. Test the data layer object

Now, let's see whether the data layer is working correctly: Best practice is to make a test order in your online shop system and inspect the order confirmation page with the developer tools in your web browser. On the confirmation page, open the inspection tool of the web browser and click on console. You will find the data layer object as in the example above. If everything works correctly the data layer object contains the product information of your test order. Among other things there is an element which is called **event**. Copy and save the value of the event parameter. We will use it for the following configuration of the Google Tag Manager.

![Testing the data layer object](/blog/images/gtm3_small.png)

2. Configuration of Google Tag Manager

After adding the data layer we can create a tag for the transaction.

1. Go to Google Tag Manager and create a Tag: "Google Analytics Transaction"
2. Choose product: Google Analytics
3. Choose tag type: Universal Analytics
4. Configure Tag: Use GA Tracking ID: "UA-**********"" and set track type to: "Transaction"
5. Fire On: Click More --> Create new Trigger: Call it "Transaction", Choose Event: "Custom Event", Fire On: Event and add the event value you previously saved from data layer object. Save Trigger.

Congrats, you're done adding e-commerce tracking and future transactions will appear in Google Analytics.
