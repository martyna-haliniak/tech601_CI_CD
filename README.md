# CI/CD

- [CI/CD](#cicd)
  - [CI: Continuous Integration](#ci-continuous-integration)
    - [How it works:](#how-it-works)
    - [Benefits:](#benefits)
  - [CD: Continuous Delivery / Continuous Deployment](#cd-continuous-delivery--continuous-deployment)
    - [Continuous Delivery (CD)](#continuous-delivery-cd)
    - [Continuous Deployment (CDE)](#continuous-deployment-cde)
    - [Difference between CD (Delivery) and CDE (Deployment)](#difference-between-cd-delivery-and-cde-deployment)
  - [Jenkins](#jenkins)
    - [What is Jenkins](#what-is-jenkins)
    - [Why use Jenkins?](#why-use-jenkins)
      - [Benefits](#benefits-1)
      - [Disadvantages](#disadvantages)
    - [Stages in a Jenskins CI/CD Pipeline](#stages-in-a-jenskins-cicd-pipeline)
      - [What is an artifact](#what-is-an-artifact)
    - [Alternative](#alternative)


## CI: Continuous Integration
**Continuous Integration** is the practice of frequently merging small code changes into a shared repository. 

### How it works:

* Developers push code changes often 
* Automated tests run 
* Integration issues found early


### Benefits:

* Faster development
* Reduce merge conflicts
* Higher code quality
* Catch bugs early
* Confidence that the app still works after each change



## CD: Continuous Delivery / Continuous Deployment
**CD** is what happens *after* **CI**.

### Continuous Delivery (CD)

* Code changes are automatically tested and packaged
* Ready to deploy at any time
* BUT deployment still requires a manual approval


### Continuous Deployment (CDE)
* Every change that passes CI is automatically deployed to production 
* No human approval needed

### Difference between CD (Delivery) and CDE (Deployment)

| Term | Trigger | Goes to Prod? | Automation Level |
| ----------- | ----------- | ---------- | ---------- |
| CD / Continuous Delivery | Manual approve only | Optional | High |
| CDE / Continuous Deployment | Automatic | Yes | Very High |

Delivery - prepared but not released

Deployment - automatically released








## Jenkins

### What is Jenkins

Jenkins is an open-source **automation server** used for CI/CD pipelines.

**What it does:**

* Automates building, testing, deploying
* Runs pipelines defined by you 
* Integrates with GitHub
* Uses "jobs" and "pipelines"



### Why use Jenkins?

#### Benefits

* **Open source & free**
* **Highly customisable**
* **Huge plugin ecosystem** (Docker, AWS, Git, Terraform, etc.)
* **Scalable** with master → agents
* **Cross-platform** (Windows, Linux, Mac)
* **Integrates with anything**


#### Disadvantages

* High maintenance (plugins break, updates needed)
* Old-fashioned UI
* Can be slow
* Requires managing your own server (unlike GitHub Actions)




### Stages in a Jenskins CI/CD Pipeline

1. **SCM (Source Code Management)** \
    Pull code from GitHub, GitLab, Bitbucket etc.
2. **Build** \ 
    Create the executable/app (artifact*) \
    Example: `npm build`, `docker build`
    
3. **Test** \
    Unit tests, integration tests

4. **Package** \
    Bundle application into a deployable format

5. **Deploy/Deliver**\
    Send artifact to an environment (dev/test/prod)

6. **Monitor**\
    Health checks, logging, alerts


#### What is an artifact



### Alternative

* GitHub Actions (most popular)
* GitLab Cl
* Azure Devops Pipelines