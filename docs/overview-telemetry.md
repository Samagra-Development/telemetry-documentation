## Overview 

Telemetry is an user behavior analytics tool that helps you understand how different users interact with your application. To start using Telemetry, you just need to configure the telemetry code in your application front-end. After the code is set up, Telemetry will start capturing and analyzing the user activity on your application.

Telemetry keeps track of the user data by capturing “Events” performed by the user. These events can be anything such as clicking on a button, mouse movements, searches, sharing links, how much time they spend on your application etc. 

Telemetry can help organizations optimize the way visitors use their applications and help retain visitors on these applications. It can help organizations build effective and user friendly applications.

## Why we need Telemetry?

The objective of telemetry is to assist in product, application or service development, modification or security. It works as a framework. Telemetry enables automatic collection of data from real-world, real-time use.

Typically, there are four levels of telemetry:

* Security

* Basic

* Enhanced

* Full


The level of data collected is a discrete decision of an organization or business. Analysis of this data offers insights into product and user behaviour and usage patterns, driving business decisions and research outcomes. You can program your telemetry analytics to suit your requirements.

Sunbird’s telemetry service has Full level telemetry.

## Use cases of saving telemetry data

## 1. e-Samwad App

e-Samwad is a flagship program of the Department of Education, Himachal Pradesh to involve parents in child's education by providing them regular updates about child's progress. Through e-samwad, parents receive regular SMS on their mobile phones about student's attendance, examination dates, examination scores, holidays, homework completion and parent teacher meeting on.

Listed in the following excel file are some of the use cases where Telemetry was used to capture user data for the e-Samwad android app. To view it, click [here](https://docs.google.com/spreadsheets/d/1HvryrR95cHRshST3Zg7AsWW4LXQ0h2G2j-3KmaFdcBE/edit#gid=0)

   ### Why do we want to Capture data?
   
   e-Samwad is a mobile app currently used by over 100K+ people all around the world. With so many active users on the app, it becomes important that we maintain the user-friendliness and quality of the app. 
   
   The data captured by Telemetry in the form of “events' ' helps the e-Samwad team to consistently make changes to the app that helps increase the quality of the app and provide a smooth user experience to its user base. By analyzing this data, the e-Samwad team removes any roadblock users might face while surfing the android application.


   ### What data do we want to capture

   Essentially, we want to capture every action a visitor makes on the e-Samwad app from the moment he visits it and to the time he leaves. These actions can be anything such as:

   - A Teacher submitting attendance
   - Total time spent on each module
   - How many students are actually able to submit assignments
   - Tracking how much resources are being shared by the teachers and if there arises any problem while sharing these resources
   - Student opening a chapter selection screen
   - Teacher/Student logging into the app
   - Viewing Subject selection screen
   - Clicking on a button

  ### How are we capturing this Data?
  
  In order to configure Telemetry to capture the user data on the e-Samwad application, we first have to define what events we specifically have to capture and make excel sheet detailing each event.
  
  The excel sheet should be planned with the developer, who will help the application capture all the “events” every user performs on the e-Samwad app. Everything from what a user clicks to how much time a user spends on various sections of the app will be captured and stored for analysis.

 Example for how we are defining the telemetry data for the e-Samwad android app:

<p align="middle">
<img src="telemetry-images/excel-image.png" width="700"/> 
</p>

<p align="middle">
<img src="https://user-images.githubusercontent.com/77961530/183051228-fef2ace8-4306-4cdf-9d15-58d3767598e2.png" width="700"/> 
</p>

  Following code example shows how a button click event in e-Sawad is captured:

  ```json
  {
    "id": "01826424-c368-0002-e6f9-c8802a6ce088",
    "timestamp": "2022-08-03T14:38:13.742000+00:00",
    "event": "esamwad-nipunhp-click",
    "distinct_id": "110",
    "properties": {
        "$app_build": "1200711",
        "$app_name": "e-Samwad",
        "$app_namespace": "com.himachal.android.eSamwad",
        "$app_version": "7.1.1",
        "$device_id": "9d28979226f439a7",
        "$device_manufacturer": "OnePlus",
        "$device_model": "ONEPLUS A6000",
        "$device_name": "OnePlus6",
        "$ip": "10.10.10.6",
        "$lib": "posthog-android",
        "$lib_version": "1.1.2",
        "$locale": "en-US",
        "$network_bluetooth": false,
        "$network_carrier": "Vodafone IN",
        "$network_cellular": false,
        "$network_wifi": true,
        "$os_name": "Android",
        "$os_version": "11",
        "$plugins_deferred": [],
        "$plugins_failed": [],
        "$plugins_succeeded": [
            "GeoIP (3)",
            "Property Flattener Plugin (4)"
        ],
        "$screen_density": 2.625,
        "$screen_height": 2201,
        "$screen_width": 1080,
        "$timezone": "Asia/Kolkata",
        "$user_agent": "Dalvik/2.1.0 (Linux; U; Android 11; ONEPLUS A6000 Build/RKQ1.201217.002)",
        "actor": {
            "id": "6fe47da6-b538-4f7e-b25f-111b5cfaad5e",
            "type": "school"
        },
        "actor.id": "6fe47da6-b538-4f7e-b25f-111b5cfaad5e",
        "actor.type": "school",
        "context": {
            "pdata": {
                "id": "com.himachal.esamwad",
                "pid": "esamwadapp-home-screen"
            },
            "channel": "eSamwad-android-app",
            "cdata": [
                {
                    "id": "110",
                    "type": "udise"
                }
            ]
        },
        "context.cdata.0.id": "110",
        "context.cdata.0.type": "udise",
        "context.channel": "eSamwad-android-app",
        "context.pdata.id": "com.himachal.esamwad",
        "context.pdata.pid": "esamwadapp-home-screen",
        "eData": {
            "pageId": "home-screen",
            "type": "click"
        },
        "eData.pageId": "home-screen",
        "eData.type": "click",
        "eid": "INTERACT",
        "eventType": "User Action",
        "identifier": "6fe47da6-b538-4f7e-b25f-111b5cfaad5e",
        "object": {
            "id": "nipunhp-practice-button",
            "type": "ui-element"
        },
        "object.id": "nipunhp-practice-button",
        "object.type": "ui-element",
        "page": "esamwadapp-home-screen",
        "product": "e-Samwad"
    },
    "elements_chain": ""
}
  ```
## Posthog - Analytics Tool We Use for Telemetry

PostHog is an open-source product analytics suite, built for engineers that can automatically track every event on your website or app. Based on these events, it can help you understand your users and how to improve your product.

Posthog is used as an Analytic tool for Telemetry samagra.  PostHog is designed to give you every tool you need to understand user behavior, create hypothesis and release changes to make your product more successful. To know more about Posthog and how to set it up and integrate it with your application, check out their documentation [here](https://posthog.com/docs/integrate).

## Specifications Followed by Telemetry Samagra:

Even if we don't follow the Sunbird Telemetry specifications for defining application events, Posthog as an analytics tool is capable enough to analyze these events without the Telemetry specifications. We can normally define the events in an excel sheet and give it to the developer and even without the specifications, Posthog will store and perform analysis on the events captured without any problem.

Currently the Telemetry samagra follows some specifications for their events. These specifications state that all events follow a common data structure, though the event data structure (“edata”) may differ for each event.
Below listed are some of the event specifications. You can view all of them in more detail [here](https://telemetry.sunbird.org/learn/specification). 

- Start - This method initializes capture of telemetric data associated to the start of user action
- Impression - This method is used to capture telemetry for user visits to a specific page.
- Interact - This method is used to capture user interactions on a page. For example, search, click, preview, move, resize, configure
- Feedback - This method is used to capture user feedback

### How the Analytics is Done on Posthog 
 
 PostHog can be deployed on your own infrastructure and provides a large set of tools to help improve your product, such as session recording, heatmaps, and feature flags, that are unique to PostHog in the product analytics space. To integrate Posthog with your application backend and enable Analytics services, follow these [steps](https://posthog.com/docs/integrate).

 Following example shows the e-Samwad Posthog analytics dashboard: 

<p align="middle">
<img src="https://user-images.githubusercontent.com/77961530/183069921-f2ad1069-b73b-4b67-9140-b9c0d2482c49.png" width="700"/> 
</p>





