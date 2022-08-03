## Telemetry Basics (with example)

As discussed in the overview, there are a lot of user behaviour data that is generated on any web app pr mobile apps, when a user comes on the home page and navigates through the app. These events are captured in the background without explicitly informing the user. Telemetry provide inputs to understand user behaviour patterns on any website or app.

Let's take an example of [this](http://docs.sunbird.org/latest/developer-docs/telemetry/overview/) documentation site and try to understand what telementry we can capture and how to go about different steps in the process.

- [Event Specifications for Telemetry events](http://docs.sunbird.org/latest/developer-docs/telemetry/specification/#events-specs)

     Step 1: Identify the telemetry events you want to capture.
     Events we can capture for this documentation site.

    - Average time spent by the user in a session - This will help understand how much time a user typically takes to read and understand about telemtry

    - Time spent on a particular section - This will help understand, which sections are more useful or requires more clarificaiton

    - Links clicked - This will help keep track of which hyperlinks are most sought after, so we can focus on making that section more relevant

    Step 2: Define each page on the website, and create events sheet for each page and events on the page that you want to capture.
      Defining events for the documentaion page:

   - Define page names: Here we have defined all the pages and sub-pages of Telemetry documentation
      <p align="center">
      <img src = "https://user-images.githubusercontent.com/77961530/182592879-61abae8f-a984-4b7e-a2d8-c60b79dd97db.png" width="800"/>
      </p>

    - Define events for each page: Define events for each page and the possible events that are going to be captured on that page



    - The following sheet defines some sample events for the Telemetry documentation site. Click [here](https://docs.google.com/spreadsheets/d/1PcWibGk6fK25lTGAJB-irr8OsNpHhCa0o4gB4UycWN4/edit#gid=187433592) to view.

     
- [Sending Telemetry](http://docs.sunbird.org/latest/developer-docs/telemetry/sending_telemetry/)

- [Consuming Telemetry data](http://docs.sunbird.org/latest/developer-docs/telemetry/consuming_telemetry/)
