# Web Development Project Planning Guide
## Overview

This is a guide for how to break down web development projects in to small, meaningful, and easy to understand steps.
It focuses on which questions the project planning should ask and answer before starting on the project.  

In this guide we'll use the Drumeo cancellation process revamp project in the examples.  
Docs: [https://docs.google.com/document/d/1WzHSzpMyBlRv6SDVZWI28CWs_3ZDfRcgUuetKrCWVEI/edit#](https://docs.google.com/document/d/1WzHSzpMyBlRv6SDVZWI28CWs_3ZDfRcgUuetKrCWVEI/edit#)

## Questions

### Which **technologies** and **developers** are required?

Most teams have developers who specialise in different technologies. It's important to plan out who will be 
needed to complete the project and make sure they are aware of the project and schedule.  

Here is a basic list of options to choose from:

- PHP/Laravel
- Blade/HTML
- CSS/SASS
- Basic JS
- VueJS
- Any third party APIs

**Example:**

Our drumeo cancellation revamp project will need:

- PHP/Laravel - yes, from a BE dev
- Blade/HTML - yes, basic implementation from a BE dev
- CSS/SASS - yes, from a FE dev
- Basic JS - yes, for the modals, from a FE dev
- VueJS - none required, there are no complex or dynamic UI elements in the design
- Any third party APIs - none required

We'll need at least 1 BE dev and one FE dev to complete this project.  


### Which **requests** are required?

HTTPS requests and responses are the lowest level element of any web or app project. Planning from the request level and
working upward is typically the best way to start planning. The core questions to answer are:

- What requests need to be sent?
- What information do the responses to those requests need to contain? 
- What requests and responses need to be sent to third party APIs?

**Example:**

- 'Account Details' page load GET request
The response will need to return the view itself and all the data about the users  
subscription necessary to render the different use cases outlined in the project documentation and design. 
Specifically we'll need to send the 'state' of the users membership, along with the renewal date, price, etc.  
  
- Main cancellation page load GET request
When a user decides to go through with the cancellation, past the initial modal, we bring them to a new blank white page 
with only the cancellation form as per the design. This should be its own page, not a giant full screen 
modal like the design suggests. It should return the view, no special info is required, everyone sees the same options.

- Main cancellation form submit POST request
When the user submits the main cancellation page form we need to redirect them depending on the option chosen. See docs
for which page to send them to.

- Other
Each of the other cancellation win back pages need requests to render them. 
There are also some other POST endpoints required for upgrading, delaying billing, etc. Planning those is outside the 
scope of this guide.

### How much and what kind of **automated testing** should be used?

Some projects need lots of layers of automated testing, others only 1. Deciding this is a bit subjective based on 
how important the project is and what other priorities are ahead. There are also business implication to consider
when planning how much time to spend on automated testing. Here are the core testing options:

- Unit testing (individual class methods)
- Functional/integration testing (endpoints/controller methods)
- Acceptance testing (browser emulation)

**Example:**
For this cancellation project I recommend only functional testing. Unit testing doesn't seem necessary since 
there is no complex logic or mathematics. Acceptance testing would be nice, but it will take too long, and we have other
projects to move on to.


### How will this project be deployed to the live production server?

It's useful to understand how complex the deployment process will be for pushing the project to production. Some 
questions to answer are:

- What data migrations need to be run before the project will function?
- Do any of the websites or systems need to be taken offline or put in to maintenance mode?
- What is the expected downtime?

**Example:**
There shouldn't be any special deployments steps request for the cancellation project. A regular deployment should do 
it!

### Send It