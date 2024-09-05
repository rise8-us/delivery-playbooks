# Continuous Integration/Continuous Deplyment

## What is it?

CI/CD stands for Continuous Integration and Continuous Delivery/Deployment. It's a set of practices and tools that help software developers work together to create, test, and release software more efficiently and quickly. Here's a straightforward breakdown:

![process](../assets/cicd.png)

### Continuous Integration (CI)

Imagine you're building a giant puzzle with a team. Each person works on a different piece of the puzzle. But if everyone waits until the end to put their pieces together, it might not fit well, and you'll have a lot of fixing to do. Continuous Integration means everyone frequently adds their puzzle pieces (code) to the main puzzle (main codebase). This way, you can quickly spot any problems and fix them before they become bigger issues. 

*  **Frequent Code Updates**: Developers share their code changes frequently, usually multiple times a day.

* **Automated Testing**: Each time someone adds their code, automated tests run to ensure the software is secure and is working as intended..

*  **Immediate Feedback**: If something breaks, the team knows right away and can fix it quickly.

### Continuous Delivery (CD)

Now, let's say once your puzzle (software) is complete, you need to show it to people (users). Instead of waiting until the entire puzzle is done, you show them small sections as you complete them. Continuous Delivery means that the code is always ready to be delivered to users. Every change is tested and can be safely released at any time.

*  **Ready for Release**: The software is always in a state that can be released to users.

*  **Frequent Updates**: You can release updates often, the highest performing teams do this multiple times every day.

*  **User Feedback**: Users can see new features or fixes sooner, and you can get their feedback quickly.

*  **Automatic Release**: No manual steps are needed to release the software to users.

*  **Speed**: Changes go live very quickly, sometimes within minutes.

*  **Reliability**: Because everything is automated, there's less room for human error.

### The CI/CD Pipeline

We recommend using external software to manage CI and CD for projects. There are many of these software solutions in the marketplace and they are often referred to as “CI/CD pipelines.” They are called pipelines because you can imagine your software release starting at one side and passing through a series of automated gate checks to ensure quality and security of the release before coming out the other end, deployed to production and in the hands of the end-user. There may be a gate for doing an automated security vulnerability scan, a gate to ensure all services within the application are integrating properly, and a gate to run unit tests against the software to ensure business logic is functioning as expected. If any one step in the pipeline fails, it will alert the team and halt that release from going any further, ensuring that release never makes it into production.

## Why do it?

CI/CD is crucial because it makes developing and delivering software faster, more reliable, and more efficient. By continuously integrating code changes and automatically testing them, teams can catch and fix problems early, ensuring higher quality software. This process also allows teams to release updates and new features more frequently, so users get improvements faster and more regularly. This continuous improvement cycle not only helps developers work together more effectively but also keeps users satisfied with quick and reliable updates. Ultimately, CI/CD helps create better software in less time, benefiting both the creators and the users.

## Relevant Links / Books

* [What is CI/CD?](https://www.redhat.com/en/topics/devops/what-is-ci-cd) \- Red Hat  
* [Continuous integration vs. delivery vs. deployment](https://www.atlassian.com/continuous-delivery/principles/continuous-integration-vs-delivery-vs-deployment) \- Atlassian  
* [An Introduction to Continuous Integration, Delivery, and Deployment](https://www.digitalocean.com/community/tutorials/an-introduction-to-continuous-integration-delivery-and-deployment) \- DigitalOcean  
* [Continuous Integration: Improving Software Quality and Reducing Risk](https://www.amazon.com/Continuous-Delivery-Deployment-Automation-Addison-Wesley/dp/0321601912) \- Martin Fowler  
* [Accelerate: The Science of Lean Software and DevOps](https://www.amazon.com/Accelerate-Software-Performing-Technology-Organizations/dp/1942788339) \- Dr. Nicole Forsgren, Jez Humble, and Gene Kim
