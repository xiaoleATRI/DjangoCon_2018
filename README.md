# BDD (Behavior Driven Development) Test in Django App

### Audience Level
Beginner & Mediate (Anyone who has a little experience with Django and Django Rest Framework).

### Elevator Pitch

BDD methodology could describe expected behaviors of system in business readable and domain-specific language which could enable testers to apply tests by following BDD workflow. BDD automation test could also save testers a lot of time from doing cross-platform tests manually.

### Description

As we know, unit tests focus on class and methods without database interaction and running of whole system while the integration tests focus on the component and basic business logic coverage using the part of system environment. Both of them cannot ensure that our app will work properly in production environments. Due to which, BDD tests becomes one of optimal solutions for cross-platform and feature-focused tests.

BDD is in its prevalence now and we’d like to breakdown how we implement BDD automation tests in following questions:

1. How do we collect requirements?
2. How do we design structured and reusable test code for BDD?
3. How do we speed up the running of BDD automation tests?
4. How do we integrate BDD tests with CI/CD pipeline?
5. What are the limits of BDD test?



### Notes

#### Technical Requirements

BDD tests are required in our system to fulfill the requirements as following:
1. Page navigation is correct
2. Different components can be displayed based on operation
3. Every operation of system is well documented in audit trail
4. Data uploaded to system can be verified correctly
5. Content management is categorized by user permission
6. Error resulted from malicious input can be raised correctly

#### Background

The primary job of our testing team is to test our main Electronic Data Capture(EDC) system and report dysfunctional operations and bugs found during tests. In order to make EDC system compliant to 21 CRF part 11, HIPPA, HITECH etc, BDD tests are adopted for our end-to-end test to make sure there is no violation of regulations(ex:leak of information, malicious workflow). Meanwhile, the intactness and performance of system are guaranteed.

### Tags
BDD, Django, Python, Behave

### Bio
I'm working in Alzheimer’s Therapeutic Research Institute as a programmer analyst, MS in Computer Science. I love exploring cut-edge techniques and trying to integrate them with my current project.

I have attended a lot of meetups related to django in San Diego ([I saw one of the organizers giving the talk in last year DjangoCon](https://2017.djangocon.us/talks/stumbling-through-django-and-how-not-to/)) which inspired me a lot and enhanced my technical skills.

Apart from being a programmer, I'm also learning aikido(Japanese martial arts) and Japanese in my spare time.
