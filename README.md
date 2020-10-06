# Sales Engineer Take-Home Exercise
v2.0

Thank you for being interested in a position at Cockroach Labs!  As a part of our interview process, we like to have candidates get their hands dirty with the product.  This allows you to get a feel for what it’s like to work with our platform, and it gives us an opportunity to determine where best you will fit in the organization.

You can spend as much time as you’d like working on this exercise, but if you haven’t been able to get through the core portion of it in 2-4 hours please let us know.  The extra credit is just that, EXTRA, so don’t feel like you need to do any or all of it.  But successful Roachers tend to go above and beyond in at least one area. Don’t feel like it needs to be one of our suggestions though - be creative!

## High-Level Goals 

### Core:

- Demonstrate a fundamental understanding of how to launch and initialize the database
- Monitor the database during certain common scenarios as described below
- Take one of the code examples from our website and get it working against your local environment
- Present your findings back to the team

### Extra Credit (examples):

- Demonstrate a complex failure scenario and how the database manages resilience (K8s, multi-cloud, multi-dc, etc)
- Integrate a 3rd party application of your choice (a BI dashboard, an ETL tool, Monitoring etc) 
- Build an app in the language of your choice that uses CRDB as the backend (particularly one not covered by our docs)
- Anything else you think would highlight your unique skill-set
- Other ideas for extra credit are included in-line below

## Prerequisites

- Machine with at least 4 cores and 8 GB of RAM
- If running on Windows, you may want to start with a Linux VM with the same specs

If you don’t have a machine that meets these minimum requirements, please let us know and we will spin up a cloud instance on your behalf

It might also be worth going through at least some of our online tutorials before getting started with this exercise.

## Core Exercise

### Launch and Initialize CRDB

- Follow the instructions on our website to start a local cluster of 3 nodes (https://www.cockroachlabs.com/docs/stable/start-a-local-cluster.html). 
  - *Extra Credit* Launch the cluster in Docker or Kubernetes
-Connect to the Admin UI on port 8080 and verify that you can see all 3 nodes
- Set up load balancing in front of the cluster for HA (our default is HAProxy but you can use anything you’d like)

### Generate a load against the cluster

- Generate some load against the cluster - easiest way to do this is using the cockroach workload command (https://www.cockroachlabs.com/docs/stable/cockroach-workload.html)
  - You’ll want to route this through the load balancer for a later part of the exercise
  - *Extra Credit* generate some load some other way against the cluster
- Set your load generator to run for at least 60 minutes to give you time to run through some common scenarios listed below

### Scaling and Failing

#### While loading data into the cluster:
- Attach a 4th node and see how the system behaves (watch for 5 minutes)
- Gracefully remove a node from the cluster and see how the system behaves (watch for 5 minutes)
- Forcibly remove a node from the cluster (think kill -9) and see how the system behaves (watch for 5 minutes)
- Remove all nodes but one from the cluster

#### Questions to answer:
- As you were adding and removing nodes from the cluster, how did that impact performance?  What kinds of metrics were you tracking to identify that impact?
- What other kinds of behavior did you witness as you were changing the cluster topology?  How did the system handle the hard node failure differently than the graceful shutdown?
- When you killed all of the nodes but one, what happened to the database?
- Did the platform behave differently than you would expect in any of the above scenarios?  If so please describe.

### Executing a Code Example

- Shut down the load generator
- Scale the database back to at least 3 nodes and execute one of the code examples in the language of your choice (https://www.cockroachlabs.com/docs/stable/hello-world-example-apps.html).
  - *Extra Credit* Enhance the example to do more than what is demonstrated

### Present Your Findings

At a minimum, please cover the following topics:
- Describe the experience of installing and monitoring CRDB and the pros/cons to the approach you took
- Describe your understanding of the pros and cons of CRDB’s distributed architecture
- Scaling and Failing - present your answers to the questions above and any other notes on your experience
- Demonstrate your working code example
- Present any extra credit activities that highlight your unique skills

The format of the presentation should be in alignment with the role for which you’re interviewing.  That may be some form of a live demo, a presentation, or something completely different.  This is your chance to differentiate yourself.


## Appendix
### Useful Links

- Documentation - https://www.cockroachlabs.com/docs/stable/
- Tutorials - https://www.cockroachlabs.com/docs/stable/training/
- GitHub - https://github.com/cockroachdb
- Cockroach University: https://university.cockroachlabs.com/
