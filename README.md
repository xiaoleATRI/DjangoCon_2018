# BDD (Behavior Driven Development) Test in Django App

### Audience Level
Beginner & Mediate (Anyone who has a little experience with Django and Django Rest Framework).

### Elevator Pitch

The beauty of Behaviour-Driven Development (BDD) methodology is that it builds a tunnel between testers and business analyzers. In which, the expected behaviors of system are described in business readable and domain-specific language. 

Accordingly, testers are capable to apply tests based on the semantic of business requirements directly without translation. 

In the end, it is very easy for business analyzers to understand the results of tests.

### Description

As we know, unit tests focus on class and methods without database interaction and running of whole system while the integration tests focus on the component and basic business logic coverage using the part of system environment. Both of them cannot ensure that our app will work properly in production environments. Due to which, BDD tests becomes one of optimal solutions for cross-platform and feature-focused tests.

BDD is in its prevalence now and we’d like to breakdown how we implement BDD automation tests.


### Notes

#### How do we collect requirements?
1. The Table of Requirements Hierarchy

    | Feature | Story | Scenario | Step |
    | :-------: |:-----:| :--------:|:----:|
    | The summary of function we need to test on | The abstract of behaviours user is performing | The user cases under specific story |The exact behavior decription|

2. Summary Template of Scenario
    |   | User | Privilege | Modal Verb | Action |
    |:---:|:----:|:---------:|:----------:|:-------:|
    | Ex| Any | Registration | Can | Attend Djangocon|

3. Template of Step
    | | Condition Word | Subject | Modal Verb | Action | in | Page Pattern | of | App Name |
    |:---:|:----:|:---------:|:----------:|:-------:|:------:|:------:|:--:|:-----:|
    | Ex| Given | I | Can | register | in | land page | of | DjangoCon Website|
    ***
    The reason why we designed such Gherkin style description step is that we have many apps in one project and it can be very hard for us to maintain the test if we have all the step implementations in one single action file. 
    
    Therefore, we categorize the behaviors by apps and each app will have its own action file to contain implementations of involved steps. 
    
    In the meantime, we apply the “Page Objects” pattern in our code structure so that we only locate elements in page file. The big takeaway is that the step description is the metadata we use to identify page objects and action files which should be loaded for test.                                                        
#### How do we design structured and reusable test code for BDD?
1. The List of Files in Feature
    
    * Feature
        
        1. Action(Step)
            * Action files contain the implementation of each step.
        2. Page Objects
            * Page files contain the location of elements of page.
        3. Fixtures
            * Fixture files contain the data which need to be loaded before test.

2. The Relationship between Action and Page Objects

    * Since the Page Objects are only for return elements found on page while Action is responsible for performing behaviors on specific elements, the mapping between Action and Page objects would be Many-to-Many.
    * Since we seprated elements location from test operation, the elements in one page can be reused in different test cases. In the meantime, it would be easy for us to maintain the test if the interface of page is changed without changing the operation logic of web app.
    
    * ||Action|Page Objects|
      |:--:|:----:|:-----:|
      |EX|LoginAction|LandPage/LoginPage|
      |  |NavigationAction|LoginPage/MenuPage/|

3. Test Implementation Process

    1. Environment

        * Set up Browser Web Driver
        * Open browser at feature level
    2. Page Objects
        * Navigate to correct page
        * Locate and return elements on page
    3. Action
        * Perform behaviors and selected elements
        * Validate test assertion
#### How do we speed up the running of tests?

Massive interface interactions could slow down the execution of BDD tests since page navigation could be very time-consuming.

Instead of using headless browser mode to run test (we do want to see the test steps visually), we choose to refine our test logic from very beginning. 

Except for fixtures simplification to reduce fixture loading time, we apply the idea that using RESTful APIClient from `rest_framework.test` to perform pre-steps internally and swap to web driver by storing cookies from APIClient.

1. APIClient
    
    * Send HTTP request to Django RESTful API to obtain user authorization
    * Process data exchange with API

2. Web Driver
    * Open the browser and visit land page of app
    * Store cookies from API client
3. Selenium
    * Navigate to selected page
    * Perform user behaviors on this page

#### How do we run BDD tests in CI/CD?

1. Branch Structure

For those static files (configuration files), we put them in a separated branch named as “environment branch”. 

The feature branch of BDD is forked from master branch which contains the implementation of steps. 

We update the settings of those feature branches by sending them pull requests from environment branch so that we don’t have to worry about that updates in settings will affect the execution of BDD. 

Therefore, the developer branch forked from feature branch will also be up-to-date.

2. CI Structure

The CI platform we are using is Travis CI. During CI process, we treat BDD test as a plugin in which specified project branch will be pulled out and merged with BDD test branch on Travis CI so that we can execute BDD test. 

When it comes to production release, we merge the BDD test feature branches into version branch the name of which is as same as the project version branch name so that we can pull out the project version branch to execute BDD test by name convention. 

Thanks to stages of Travis CI, now we can run parallel tests in different jobs and each job will be specified with a browser

#### What are the limits of BDD test?
1.	The Gherkin syntax attempts to make tests human-readable and ends up as a constraint human language. For which, it may not able to capture nuance and intention.

2.	Since the execution sequence is from top to bottom of feature file, there would be no space for conditional situation. In other words, we are not able to use “if-else” to cover alternate user cases. Then we have to replicate scenario and change steps to tackle this problem which will result in code redundancy.
