# RM_CRM

Project Title:
    Roofmaster CRM management streamlines the entry of contract information.

Motivation:
    The entry of contract information includes some redundant processes this web app intends to automate into a single process.

Build Structure:
    Using Node.js, the web app is built around the web server chosen to be AWS Lambda. From this controller, there will be a script that calls Monday.com to seek (every 15 minutes) if data is updated from Monday.com. If it is, then it returns this data and sends it to Hubspot. 

API References:
    Monday: https://api.developer.monday.com/docs
    Hubspot: https://developers.hubspot.com/docs/api/overview


Contribution Framework:
    
    Ryan builds the trigger Monday script with getdata loop or an EventBridge scheduled event or etc. If the result is true that a user collection has been updated on Monday (in specified boards where new entries are inputted), then it approves the model updating and returns the updated collection in a static data file or cache. This process will then call a module to continue with the next step to update Hubspot.
    
    Stu builds the server to Hubspot interaction made to be called as a module given the Monday script returns any updates. The client sends a hyperlink request or auth form to the controller and receives confirmation and a view of the updated information uploaded onto Hubspot transfered from the static data file or cache. 
