+++
date = "2017-04-05T21:42:05+02:00"
title = "E-commerce Tracking With Google Analytics and Google Tag Manager"
Categories = ["Online Marketing","Google Analytics"]
Tags = ["Online Marketing","Google Analytics"]
Description = ""

+++

In order to setup ecommerce tracking we assume that you successfully implemented Google Analytics with Google Tag Manager.  

Ecommerce tracking enables the tracking of sales data on the thank you page (confirmation or checkout page). This includes all information about your shopping basket like number of sales, products, revenues, value per order, etc.

In other words, the confirmation page features a data layer with all information about the transaction, which we can extract with the Google Tag Manager and Google Analytics implementation.

There are two main types of ecommerce implementation methods:

**Standard ecommerce** reports in Google Analytics allow you to analyze purchase activity on your site or app. You can see product and transaction information, average order value, ecommerce conversion rate, time to purchase, and other data.

**Enhanced ecommerce** adds functionality by allowing you to see when customers have added items to their shopping carts, when they have started the checkout process, and when they have completed a purchase. You can also use Enhanced Ecommerce to identify segments of customers who are falling out of the shopping funnel.

Both methods of ecommerce tracking can be implemented with Google Tag Manager. In this section we will focus on **standard ecommerce tracking**.

Before we start with the implementation of the standard ecommerce tracking, there is a really useful Youtube video that is worth watching and might clarify further questions you have upfront the implementation: <https://youtu.be/ZKjlIhFJMCU>

The setup of the standard ecommerce tracking is split into three steps:

1. Installation of the data layer
2. Testing the data layer
3. Configuration of the Google Tag Manager

1. Installation of the data layer object on the thank you page.

Here is an example of the data layer object:

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
It is possible to integrate the data layer with java script manually, however we recommend to use the build-in feature of your ecommerce framework to push the data layer on the order confirmation page. Woo Commerce, Shopify, Magento or any common ecommerce framework feature plugins that integrate the data layer on the confirmation page.

3. Test the data layer object

We want to test if the data layer is working correctly. Therefore best practice is to make a test order in your online shop system and inspect the order confirmation page with the developer tools of the web browser.

On the confirmation page of the order, open the inspection tool of the web browser and click on console. You will find the data layer object as in the example above. If everything works correctly the data layer object contains the product information of your test order. Among other things there is an element which is called **event**. Copy and save the value of the event parameter. We will use it for the following configuration of the Google Tag Manager.

![Testing the data layer object](/blog/images/gtm3_small.png)

2. Configuration of Google Tag Manager

After the implementation of the data layer we can create a tag for the transaction.

1. Go to Google Tag Manager and create a Tag: "Google Analytics Transaction"
2. Choose product: Google Analytics
3. Choose tag type: Universal Analytics
4. Configure Tag: Use GA Tracking ID: "UA-**********"" and set track type to: "Transaction"
5. Fire On: Click More --> Create new Trigger: Call it "Transaction", Choose Event: "Custom Event", Fire On: Event and add the event value you saved from data layer object previously. Save Trigger

Now you finished the implementation of the Ecommerce Tracking and future transactions will appear in Google Analytics.
