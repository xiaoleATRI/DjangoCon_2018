# BDD (Behavior Driven Development) Testing for Django Apps

### Audience Level
Beginner & Intermediate  (Anyone who has a little experience with Django and Django Rest Framework).

### Elevator Pitch

BDD leverages a simple domain-specific language to enhance the effectiveness of testing within SDLC. With a BDD workflow, tester is able to accelerate development, speed up execution of cross-platform tests, facilitate CI/CD, standardize validation and enhance the readability of test documentation.

### Description

Unit tests focus on classes and methods while integration tests focus on components and basic business logic. However, neither of these is executed against the full system environment nor take account of the system's behaviors as a whole. Therefore, our app will not be assured to work properly in production environments if we limit our testing approach to only two types of tests. Incorporating BDD testing into our app's testing plan addresses these limitations.

BDD is experiencing increasing industry adoption but can still prove daunting to implement from scratch. Our talk will describe how we implement a BDD framework stack by answering following questions:

1. How do we design structured and reusable test code for BDD?
2. How do we integrate BDD tests with our CI/CD pipeline? 
3. How do we speed up the execution of BDD automated tests?
4. How do we set up our BDD framework?
5. What are the limits of BDD testing?




### Notes

#### Technical Requirements

BDD tests help our team ensure that our app fulfills system requirements as follows:

1. Page navigation is correct
2. Different components can be displayed based on an operation
3. Every operation of the system is well documented in an audit trail
4. Data uploaded to the system can be verified correctly
5. Content management is categorized by user permission
6. Errors resulting from malicious input can be raised correctly


#### Background

The primary job of our testing team is to test applications used to collect and manage medical research data and report dysfunctional operations and bugs found during tests. These systems are subject to multiple regulatory requirements (e.g. 21 CRF part 11) and we have adopted BDD testing to implement our end-to-end testing and ensure that all requirements are met on a continuous basis.

### Tags
BDD, Django, Python, Behave

### Bio

I work at the Alzheimer’s Therapeutic Research Institute, University of Southern California, as a programmer analyst, MS in Computer Science. I love exploring cut-edge techniques and trying to integrate them with my current project.

I have attended a lot of meetups related to django in San Diego ([I saw one of the organizers giving the talk in last year DjangoCon](https://2017.djangocon.us/talks/stumbling-through-django-and-how-not-to/)) which inspired me a lot and enhanced my technical skills.

Apart from being a programmer, I'm also learning aikido (Japanese martial arts) and Japanese in my spare time.
