## Setup Omni-Channel in Saleforce Lightning

### Step 1: Enable

To enable Omni-Channel navigate to the Setup menu in Salesforce. 
- Search for **Omni** and click **Omni-Channel Settings**. 
- Click to check the Enable Omni-Channel checkbox. 
- **Save**

![](https://raw.githubusercontent.com/supertopoz/salesforce_omni_channel/main/1.png)

### Step 2: Create Service Channels

- Navigate to Service Channels and click New. 
- Name the Service Channel **Sendbird_Chat**
- Choose the Salesforce Object as **Case**. 
- **Save**



![alt error](https://raw.githubusercontent.com/supertopoz/salesforce_omni_channel/main/2.png)

### Step 3: Create Omni-Channel Presence Status

- These are the statuses that will be available for agents to select when they login to Salesforce Omni-Channel. 
- Navigate to **Presence Status**.
- Create a new presence. 
- Set agent to be online. 
- Add the channel created in Step 2.
- **Save**

Note: Step 8 shows how to allow presence status for different user profiles.

![](https://raw.githubusercontent.com/supertopoz/salesforce_omni_channel/main/3.png)


### Step 4: Create Routing and Presence Configurations

Here we describe how to route from the **Sendbird_Chat** Service Channel to Omni-Channel and how Omni-Channel processes **Cases** in the **Sendbird_chat** channel. 

- Navigate to Routing Configurations. 
- Create a new route. 
- Call the route **High_Priority**
- Don't care about the overflow user in this set up. 
- Set Routing Priority to **1**. 
- Set Routing Modal to **Most Available**
- Push Time-Out to **30**
- Units of Capacity to **1.00**
- **Save**

![](https://raw.githubusercontent.com/supertopoz/salesforce_omni_channel/main/4.png)

### Step 5: Create a Queue and assign a routing configuration

- Navigate to Queues into the quick find.
- Click **New**. 
- Name and label your queue **Sendbird_tickets**
- Add **Case** as a Supported Object
- Assign the Routing Configuration **High_Priority**, created in Step 4. 
- Add Queue users or roles.
- **Save**

![](https://raw.githubusercontent.com/supertopoz/salesforce_omni_channel/main/5a.png)

### Step 6: Route Cases into the Sendbird_tickets Queue

- Navigate to **Case Assignment Rules**.
- Click **New**
- Name the rule **Sendbird Case Assignment**
- Check *Active*
- **Save**

![](https://raw.githubusercontent.com/supertopoz/salesforce_omni_channel/main/5.png) 


- Click the newly created rules name after a saving the above rule. 
- Under **Rules Entries**, click **New**
- Sort Order **1**
- Run this rule if the **criteria are met**
- In field select **Case: Status**
- Operator **equals** 
- Value **New**
- In select the user or queue to assign the case to, choose **Queue** and select **Sendbird_tickets** (label of the Queue created in Step 6).
- **Save**

![](https://raw.githubusercontent.com/supertopoz/salesforce_omni_channel/main/6a.png) 

### Step 7: Add Omni-Channel to the Utility Bar

- Navigate to **App Manager**
- Under **Service Console** click down arrow on the far right. 
- Click **edit**

![](https://raw.githubusercontent.com/supertopoz/salesforce_omni_channel/main/7a.png) 

- In the window that opens 
- Select **Utility Items (Desktop Only)
- Click **Add Utility Item**
- Select **Omni-Channel**
- **Save**

![](https://raw.githubusercontent.com/supertopoz/salesforce_omni_channel/main/7b.png) 

### Step 8: Allow profiles access to Omni-Channel

- Navigate to Profiles
- In the second page select the **Standard User** profile name
- In the **Profile Standard User** header section, mouse over **Enabled Service Presence Status Access** 
- Click **Edit**


![](https://raw.githubusercontent.com/supertopoz/salesforce_omni_channel/main/8.png) 

- Add the allowed presence set in **Step 3**
- **Save**


![](https://raw.githubusercontent.com/supertopoz/salesforce_omni_channel/main/8b.png) 

