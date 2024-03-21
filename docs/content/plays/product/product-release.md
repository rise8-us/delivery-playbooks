# Releasing a Product

## What is it?
Releasing a product is the process of delivering code to a production environment either as an initial launch or as an iteration on an existing software version.


## Why do it?
Shipping completed work is essential for providing users with new capabilities, bug fixes, and performance improvements. It is also the best way to collect metrics and quantify the impact of new features since production is more honest and indicative of user behavior compared to usability tests and interviews. 


## When to do it? 
Release cadence varies widely depending on the organization and team, with some products releasing dozens of times per day while others may only release a couple times a month. We urge you to focus on releasing as frequently as possible but we also recognize there may be some constraints. Working with your organization to push towards more frequent releases is an important part of being an influential PM, especially in the high compliance environments we work in. Here are some common ways to plan releases:

1. **As often as possible**
  * Each story is structured so that delivering that story adds value to the application in production. You can theoretically cut a release whenever you choose.

2. **As workflows are delivered**
  * Sometimes cutting a release mid-workflow could deliver incomplete usability to users. As a result, many teams will release when the minimum functionality of a feature set or epic has been built. If operating in this model, we encourage you to still scope work into the smallest increments possible and iterate from there.

3. **As dictated by the sprint/iteration**
  * Many teams release on a schedule following sprints or iterations of set lengths. This can be helpful for communicating your release plan to users and stakeholders, but it gives you a little less flexibility to move fast and learn. If using this model ensure you do not go more than 2 weeks without releasing.


## Who’s involved? 
Product Managers, Product Designers, Engineers, Platform Operators/Engineers, and in many cases Users and Stakeholders


## Tools You Might Need
* Repository for Release Notes (github, gitlab, etc)
* Backlog management tool
* Release Pipeline workflow
* Test environments (Acceptance and Production Staging)

## How to do it (Steps)
1. **Decide when to release**
    * Pick one of the cadences above and determine your batch size
    * Create a Release Marker in your backlog that demonstrates which work is associated with that release
    * Label the associated tickets with that version number or release name for bookkeeping purposes
    * Make sure the release will not disrupt any critical user operations. Check with your users if you have any doubts

2. **Test in Acceptance**
    * When all work is complete, smoke test the application in an acceptance environment to ensure everything works as expected and the team did not introduce any bugs

3. **Ensure the application can be released**
    * Check that the pipeline is green and all tests are passing
    * Determine all security controls have been met and no vulnerabilities are detected

4. **Write release notes** 
    * Choose a version number that follows your team’s agreed upon format. Most commonly teams use Major.Minor.Patch, i.e. v3.16.0
    * Include features, bug fixes, and any relevant information for platform operators and/or security, such as environment variables

5. **Trigger the release to Staging**
    * Depending on the team’s workflow this is either done by the PM or the engineers
    * May require an external Platform team to physically release the new version if working in classified environments

6. **Test in Staging**
    * This is an important step when your production environment is at a different classification level since things can often differ considerably between environments

7. **Promote to Production**
    * Smoke test again in prod
    * Notify your users of the new version (consider building a changelog into your application to show all new updates)
    * Monitor user feedback closely after the release goes live


## Relevant Links
  * [Accelerate](https://www.amazon.com/Accelerate-Software-Performing-Technology-Organizations/dp/1942788339/ref=sr_1_1?crid=YNQGHC1DCTAD&keywords=accelerate+book&qid=1650402762&sprefix=accelerate+book%2Caps%2C114&sr=8-1) by Forsgren, Humble, & Kim - A helpful resource for communicating the value of frequent, small, and stable releases
  * [DORA Metrics Overview](https://cloud.google.com/blog/products/devops-sre/using-the-four-keys-to-measure-your-devops-performance)
