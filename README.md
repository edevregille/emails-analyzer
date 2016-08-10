Emails Analyzer with Watson NLC
====================================

### Emails Analyzer in BlueMix with Watson NLC

This repository is an example Node-RED application to analyze emails with Watson that can be deployed into Bluemix with only a couple clicks. Try it out for yourself right now by clicking:

[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/edevregille/emails-analyzer.git)

It provides you with a flow to:
- an automatic analysis of all incoming emails with Watson NLC to detect the user intention.
- a classification of analyzed emails: either to be answered by the agent or by the center.
- a rerouting of emails: if email is to be answered by the center, then the email is resent to another email box.
- a reporting UI interface

LIMITATIONS: the incoming mail box need to be Gmail because of the classification.

![node-red flow](/public/images/node-flow.png?raw=true "Flow Node-Red")

![Reporting](/public/images/reporting.png?raw=true "Reporting UI")


### How does this work?

When you click the button 'Deploy to Bluemix', you are taken to Bluemix where you get to pick a name
for your application at which point the platform takes over, grabs the code from
this repository and gets it deployed.

It will automatically create an instance of the Cloudant service and Watson NLC and bind all those services to your app.

### Set-up of the flow

**Client Input node**
You need to set the Input Client node Gmail by entering credentials of the gmail box to listen to. You also need to create on your gmail box two labels: one for the center and one for the agent.

**NLC node**
You have to create and train a NLC classifier by uploading the nlc-training-bank.csv file on the Watson NLC service.
Don't forget to update the NLC node with the new classifierID and credentials.

**Classification node**
Classification node uses IMAP Gmail extension to move mails to the right folder. Indicate here the names of the labels you have created in the gmail incoming box.

**Output email**
This node is just to send the email to another mailbox if the email needs to be answered by the center. 

