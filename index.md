# _Lab:_ Creating alert conditions with guided mode

**Objective:** Use New Relic’s guided mode to create two alert conditions: 

- One that will open a critical incident if production APM services have a response time greater than 500 ms for at least 5 minutes; and

- Another that will open a critical incident if the page load time for a browser application is greater than 2 seconds for at least 5 minutes. 

## Step 1: Log into the training account

In a private browser window, use the following credentials to log into New Relic: 

- URL: [https://one.newrelic.com/](https://one.newrelic.com/)
- Email: learn@newrelicuniversity.com
- The instructor will provide the password

## Step 2
From New Relic’s main menu, select _Alerts_ > _Alert Conditions_, then click _+ New alert condition_ in the upper-right.

## Step 3
Select _Use guided mode_. Your first alert condition will monitor APM services, so select _Services - APM_ and click _Next_.

## Step 4
On the next page, use _Filter by name or tags_ to filter the list of services to those containing a value of “Production” in the “Environment” tag. Select the matching services.

## Step 5
Scroll down to _Select a metric to monitor_. From the list of golden metrics, select _Response time (ms)_. Note the automatically-generated NRQL query, then click _Next_.

## Step 6
On the next page, under _Set condition thresholds_, configure a static threshold to open an incident of critical severity when a query returns a value above 500 (ms) for at least 5 minutes. Note that you may optionally add a second threshold to create an incident of warning severity. Click _Next_.

## Step 7
On the final page, give your alert condition a descriptive name, such as “[Your initials] Production services response time > 500 ms”. 

## Step 8
Under _Connect this condition to a policy_, select _New policy_ and create a new alert policy to contain your conditions. Give it a name you will recognize as yours, such as “[Your initials] Alert policy”. Accept the defaults for all other options.

## Step 9
Click _Save & set up notifications_. When prompted to create a workflow, select _Cancel_.

## Step 10
Repeat the above steps to create a second alert condition: Open a critical incident if the New Relic Pet Clinic browser application has a page load time greater than 2 seconds for at least 5 minutes. Add the condition to the policy you just created.

---

# _Lab:_ Creating alert conditions with custom NRQL queries

**Objective:** In the previous lab, you used New Relic’s guided mode to automatically generate NRQL queries for alert conditions. In this lab, you will create an alert condition by writing your own query.

## Step 1
From New Relic’s main menu, select _Alerts_ > _Alert Conditions_, then click _+ New alert condition_ in the upper-right.

## Step 2
Select _Write your own query_. **Challenge:** See if you can write a query that returns the average CPU usage for any host running the New Relic Pet Clinic APM service. (Try asking AI and seeing how it does.) When you have a working query, click _Next_.

## Step 3
On the next page, under _Set condition thresholds_, configure a static threshold to open an incident of critical severity when a query returns a value above 50 (%) for at least 3 minutes. If you wish, create a second threshold to open an incident of warning severity when a query returns a value above 20 (%) for at least 2 minutes. Click _Next_.

## Step 4
Add the new condition to the alert policy you created in the previous lab.

---
# _Lab:_ Using the New Relic Logs UI

**Objective:** Practice using the New Relic Logs UI to search and analyze log data.

## Step 1
From New Relic’s main menu, select _Logs_. Select the **NRU Demotron v4** account, and set the time picker to the past 60 minutes.

## Step 2
Filter the list to show only logs with a level of ERROR. How many logs are there?

## Step 3
Add a column to the results table to display the log level and entity.name of each log. How can you change your filter query to show only logs that contain a value for entity.name?

## Step 4
How could you save this view to quickly recall it later? How could you share this data with a colleague? What if they don’t have access to your New Relic account?

## Step 5
How could you create an alert condition based on this log search?

---

# _Lab:_ Searching logs based on custom attributes

**Objective:** Find logs containing custom attributes recorded with automatic logs in context.

## Step 1
In a web browser, visit [https://foodme.nru.to/](https://foodme.nru.to/). Enter a customer name and address you will search for later. Select a restaurant and add some menu items to your cart, then complete your order. (_Tip:_ Try changing the item quantity to a very large value.) 

## Step 2
From New Relic’s main menu, select _Logs_. Select the **NRU Training** account.

## Step 3
Using the filter bar at the top of the page, try to find the order you just placed.

## Step 4
Select a matching log entry and notice the custom attributes that were recorded.

## Additional resources
- [New Relic Logs UI documentation](https://docs.newrelic.com/docs/logs/ui-data/use-logs-ui/)
- [APM Logs in Context documentation](https://docs.newrelic.com/docs/logs/logs-context/get-started-logs-context/)

---

# _Lab:_ Collecting custom attributes

**Objective:** Add New Relic to a sample APM service and collect custom business metrics.

---

# _Lab_: Using New Relic APM to troubleshoot a database performance problem

**Objective:** Use the features of New Relic APM, such as the _Databases_ page and transaction traces, to identify the cause of slow database performance.

## Step 1
Under _Services - APM_ in the New Relic UI, select **Ad Service** in the **NRU Demotron v4** account. Set the time window to the last 60 minutes.

## Step 2
Notice that there are several response-time spikes during the past hour. Based on the colors on the _Web transactions time_ chart, where is most of the time being spent?

## Step 3
Select the _Databases_ menu to the left of the _Summary_ page. Which database query is taking the most time? 

## Step 4
Select the most time-consuming database query from the list. Why do you think it is taking so much time? Are there any slow query traces? If not, why not?

## Step 5
Go back to the _Summary_ page and scroll down to the list of Transactions. Select the slowest transaction. Do you notice anything on that page that might explain why database queries are taking a long time?

## Step 6
Scroll further down the transaction detail page and select a transaction trace with a duration greater than 60,000 ms. Looking at the trace, what do you think caused the transaction to take so long?

## Additional resources
- [APM Databases page documentation](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time/)
- [APM Transactions page documentation](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/transactions-page-find-specific-performance-problems/)
- [Tutorial: Troubleshoot slow application performance](https://docs.newrelic.com/docs/tutorial-improve-app-performance/root-causes/)

---

_Lab:_ Using integrated APM and Infrastructure to troubleshoot a performance problem

**Objective:** The New Relic Pet Clinic application experienced a sudden increase in response time. Use integrated APM and Infrastructure to investigate the problem.

## Step 1
Select the **New Relic Pet Clinic** application in the **NRU Training** account. Set the time picker to 24 hours, and locate a response-time spike (there should be one daily between 06:10 and 06:50 UTC). 

![](/images/new-relic-pet-clinic-apm-overview.png)

## Step 2
Use integrated APM and Infrastructure to answer the following questions: 

- Were there any application deployments around the time of the incident?

- Was there an increase in application throughput that might explain the increased 
response time?

- Did response time increase across all hosts (containers), or only certain ones?

- Select an affected container and view the data for the associated host (_Hint:_ _Related entities_ > _See full map_). Do you notice anything unusual about that host’s data?

---

_Lab:_ Creating Synthetics monitors

**Objective**: Understand the various types of Synthetics monitors and practice creating Availability, Page load performance, and Step builder monitors.

## Step 1
You want to monitor whether your website is online and responding to requests. Which Synthetics monitor type should you use? What if you also want to monitor page load performance, does that change your answer?

## Step 2
In your personal New Relic account, create an Availability (Ping) monitor to check the URL of your choice from 3 locations.

## Step 3
Create a page load performance (Simple browser) monitor for the same URL. What differences do you notice in configuration options compared to the Ping monitor from Step 1?

## Step 4
Wait a few minutes, then compare the results of the Ping monitor with those of the Simple browser. How are they similar? How are they different?

## Step 5
Create a Step builder monitor that performs the following steps: 

1. **Navigate** to http://webportal.telco.nrdemo.com/

2. **Click Element** `Login`

3. **Type Text** in element `input[name="username"]`, your user name

4. **Type Text** in element `input[name="password"]`, any password

5. **Click Element** `input.btn-primary`

6. **Assert Element** `//a[text()="<your user name>"]` **is visible**

Click the _Validate_ button to confirm that your monitor runs successfully.

---

_Lab:_ Using cloud integrations