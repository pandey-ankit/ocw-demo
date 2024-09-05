# Modernise with WebLogic, Helidon and Coherence 

## Introduction

The very purpose of writing microservices is to do a small piece of job efficiently and reuse it multiple times in different applications. Helidon MP enables us to write one such microservice for this demo. **BestBank**, a hypothetical bank has an application. As part of that application, the bank’s credit division wants to build a simple UI which showcases the details of the top 15 customers with their SSN and IBAN numbers. The team wants to have a microservice which provides the credit score of the customer as output taking the user details like IBAN/SSNs as input. The IT developers create a CreditScore Microservice in Helidon and consume it in the current UI application listing the top 15 customers.

### Implementation Details and Assumptions

* The sample application UI is built to showcase JSF and CDI using XHTML
* The user data is not coming from the database
* The Helidon Microservice written in the lab can be deployed on Docker/Kubernetes, but for this demo, we only run it from the JVM locally

[](videohub:1_o3hf75h1)
Estimated Time: 10 minutes


### Objectives

In this lab, you will:

* Verify Basic Bank Application working
* Show Modernise Best Bank application working
* Clean up

### Prerequisites

* Access to noVNC Remote Desktop created in lab 1.


## Task 1: Verify Basic Best Bank Application working

1. In firefox, open a new tab and click first bookmark **Old App**.
 ![old app](images/old-app.png)

2. This is a traditional application Best Bank application running on WebLogic Server.


## Task 2: Show Modernise Best Bank application working

This is an extended version of the application, where we have created a CreditScore Microservice in **Helidon MP**. We are also using **Coherence Cache** for storing customer credit scores. So for any customer, when you click the **View** button first time, our code generates a random credit score and stores it in the  Coherence Cache. Now, when you again click the **View** button for the same customer, It provides the credit score from the coherence cache.

1. In firefox, open a new tab and click the second bookmark **New App**.
 ![new app](images/new-app.png)

2. Go back to the terminal and Open the **Helidon-Server** named tab and Press **enter** multiple times, so you can easily see new log lines.
 ![helidon logs](images/helidon-logs.png)

3. Now select any bank customer and click **View**. You will see the **Account Owner Info** window with Customer details. Click the **Cross** icon to close it.
 ![select customer](images/select-customer.png)
 ![customer details](images/customer-details.png)


4. Go back to the terminal Open the **Helidon-Server** named tab and view the invocation of the Helidon Application. As we are accessing the details for this customer first time, the Helidon application generates the credit score.
 ![generate credit](images/generate-credit.png)

    > Press **enter** multiple times, so you can easily see new log lines. 


5. Go back to the browser and again select the same customer and click the **View** button. You can see, it is the same credit score, which we saw last time as well. Click the **Cross** icon to close this.  Now Go back to the **Helidon Server** tab in the terminal, and you can see the logs, **Credit score from cache**.
 ![same customer](images/same-customer.png)
 ![browser cache](images/browser-cache.png)
 ![terminal cache](images/terminal-cache.png)

    > Press **enter** multiple times, so you can easily see new log lines.

## Task 3: Clean up

1. Close the tab, where you have the **New App** (bestbank-2) running.

## Acknowledgements

* **Author** -  Ankit Pandey
* **Contributors** - Sid Joshi, Maciej Gruszka 
* **Last Updated By/Date** - Ankit Pandey, September 2024