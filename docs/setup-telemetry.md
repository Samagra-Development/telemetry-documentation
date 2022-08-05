## Setup Telemetry For Your Application

If you are looking to integrate Telemetry with your application, you should follow these steps:

### 1. Define Events for your Application

1. The first step is to plan out the Events you are going to be capturing for your application. These events can be anything such as Clicking on a button, Sharing a link on your web app, Search, Total amount of time spent on an application etc.

2. Plan with your engineer on how to integrate these events in the organization applications. Provide the engineer with the excel sheet and the related information

3. Setup Posthog for your organization application. Posthog is where all these Events will be stored and analyzed in order to improve the application quality and the user experience

### 2. Include Events in Your Code

#### 1. Mobile Applications:

Following Example shows how events code is integrated into e-Samwad android to capture the user data:

In order to use posthog, we need to integrate the Posthog library into Android Studio. Paste the following code into your android studio 'build.gradle" file:

```
api 'com.posthog.android:posthog:1.1.2'
```

Following code sample defines a function called as sendSelectionsSubmittedEvent() which captures an event for submitting Student details on a button click:

```java
private void sendSelectionsSubmittedEvent() {
        ArrayList<Cdata> cDataList = new ArrayList<>();
        cDataList.add(new Cdata("grade", "" + classAdapter.getSelectedItem().getValue()));
        cDataList.add(new Cdata("subject", subAdapter.getSelectedSubject().getTag()));
        cDataList.add(new Cdata("s_id", "" + selectedStudent.getId()));
        Properties properties = PostHogManager.INSTANCE.createProperties("esamwadapp-nipunhp-selectdetails", PostHogEventKt.EVENT_TYPE_USER_ACTION,
                PostHogEventKt.EID_INTERACT, PostHogManager.INSTANCE.createContext("com.himachal.esamwad", "esamwadapp-nipun-practice", cDataList), new Edata("esamwadapp-nipunhp-selectdetails", "click"), new Object.Builder().type("ui-element").id("nipunhp-submitdetails-next-button").build());
        PostHogManager.INSTANCE.capture(this, "esamwad-nipunhp-studentdetailssubmit-click", properties);
    }
```

Include the following code in your application backend and modify the values according to your app's custom parameters. 

The following line invokes the Posthog manager class and actually captures the event performed in your application user interface:
```java
Properties properties = PostHogManager.INSTANCE.createProperties("esamwadapp-nipunhp-selectdetails", PostHogEventKt.EVENT_TYPE_USER_ACTION,
                PostHogEventKt.EID_INTERACT, PostHogManager.INSTANCE.createContext("com.himachal.esamwad", "esamwadapp-nipun-practice", cDataList), new Edata("esamwadapp-nipunhp-selectdetails", "click"), new Object.Builder().type("ui-element").id("nipunhp-submitdetails-next-button").build());
        PostHogManager.INSTANCE.capture(this, "esamwad-nipunhp-studentdetailssubmit-click", properties);
```

#### 2. Web Applications:


