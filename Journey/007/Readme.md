<!-- This template removes the micro tutorial for a quicker post and removes images for a full template check out the 000-DAY-ARTICLE-LONG-TEMPLATE.MD-->

![placeholder image](https://miro.medium.com/max/11436/1*_t_eIOzvoMiYEZb33YIanA.png)

# GCP - Cloud 3.0, Security, Management & Tools

## Introduction

This is going to be a continued focus on learning the fundamentals of GCP for the next few days, leveraging content from YouTube and mostly Pluralsight video training. The focus is going to be more based on Compute and Storage as I have never been a great fan of networking (because it has never really sunk in, maybe another 100 days should be spent on that) this session or update will focus on 

- Enabling Cloud 3.0 
- Security 
- Tools 
- Building for Cloud 3.0 

I am excited for this one because I have not I don't believe stumbled across the term Cloud 3.0 as a term but if I was going to take a guess now before starting the course we are going to be talking about Cloud Native architectures where the focus is on Applications and Functions vs Infrastructure and Virtual Machines. I would likely also add that Infrastructure as code has to play a part in this to a degree to deploy the platform but we shall see. 

## Use Case

Google Cloud Platform Fundamentals
by Howard Dierking [Course Link](https://app.pluralsight.com/library/courses/google-cloud-platform-fundamentals/table-of-contents)

## Cloud Research

Enabling Cloud 3.0 

- Applications and functions, not Virtual Machines 
- Storage disaggregation, not disks 
- SLAs, not load balancing and scehduling 
- Intelligence, not data processing 
- Policy, not "middle boxes" 

these are 5 areas that I really need to understand and get deeper into especially around Data, Compute and Storage and how this world will evolve over time to cloud 3.0. 

Security 

    Infrastructure Security 
        - Data Center - limited access and permissions to physical locations and all sorts of high end physical security measures to prevent external interference 
        - Hardware 
        - Software 
        - Employees - 2FA on all and making sure employees have access to what they absolutely need and nothing more. 

    Data Storage Security
        - Application - Level encryption 
        - Device Protection 
        - Hardware lifecycle management is extremely strict for data removal and migration 

    Data Flow Security 
        - Most environments concentrate on security on the perimiter rather than the middle (Squishy middle) remember that GCP runs on the same infrastructure that me and you can use. 
        - Explicit Identity 
        - Policy Enforcement 
        - Secure Communication 
        - All traffic between Data Centers is encrypted 
        - user data protection 

    Internet Traffic Security 
        - Network Segmentation - external and internal networks are seperated (GFE was mentioned here)
        - TLS termination 
        - Public IP and DNS hosting 
        - DoS protection - Google Machine learning and AI learnings which has helped the dynamic approach to this protection. 

    Compliance Certifications 
        - cloud.google.com/security/compliance 
  
    Security Configuration 
        - Service Accounts - bring your own key or use the GCP key management rotation 
        - IAM - least privelege mentality, you define your access management 

Management

    Resource Hierarachy 
    normally you would only see Org and folders if you are a complete GSuite user / customer but with Cloud Indentity this is now visible and possible to use, modify and create. 
        - Organisation - top level site or organisation  
        - Folder - demarkation of business units / groups 
        - Project - logical grouping of a set of resources 
        - Resources 
    
    Best Practices 
    - Mirror resource heirarchy to organisation structure 
    - Projects form a trust boundary 
    - Use inheritance wherever possible 
    - Follow principle of least privilege 
    - Grant roles to groups over users 
    - Audit Everything! 

    Logging and MOnitoring 
        - Provided by Stackdriver 
        - unified view of logs 
        - detailed monitoring service available

    Billing 
        - Billing accounts mapped to projects - can be managed however you want 
        - budgets and alerts 
        - detailed transaction view 

Tools
    Everything in GCP is based on an API which opens the tooling to literally achieve anything. 

    Management tools 
        - Web Console - Console.cloud.google.com 
        - SDK - can be installed on all major OS
        - Cloud Shell through web console which allows for SDK if you cannot install on your machine. 
        - API Explorer 

    Development tools 
        - Programming language support 
        - IDE Support (visual studio)

    Lifecycle Tools and Services 
        - Local service emulators 
        - Source Code Repositories similar to GitHub and others you can actually mirror between GitHub or other services. 
        - Build Service - began as container build service, now expanded scope 

Summary 

- Google Cloud Platform leverages years of research and investment in security at google 

- Resource hierarchy simplifies org and mgmt of resources 

- Comprehensive development tooling 

Building for Cloud 3.0 

- Evolving the monolithic applications 
- Big Data 
- Machine Learning 

Cloud 2.0 
    
    where are we coming from?
    - On Demand Computing resources 
    - Projection of On-Premises architecture 
    - App Server contains all services > storage layer > logs all run on the same infrastructure. Operator is responsible for app and infrastructure. This is the challenge of taking a monolith application to more cloud native. 

Cloud 3.0 

I have already said this but repeating for knowledge. 
- Applications and functions, not Virtual Machines 
- Storage disaggregation, not disks 
- SLAs, not load balancing and scehduling 
- Intelligence, not data processing 
- Policy, not "middle boxes" 

Many of us are not starting here but we are evolving too

worry less about because of cloud 3.0 
  
    - managed logging and monitoring 
    - declartive network policy 
    - task automation 

Benefits of container orchestration 
  - Technical: Increase density 
  - Architecture: Decomposition (break down the app server into services)
  - Organisational: End to end teams 

Processing events 
  - Cloud PubSub 
    - Fully managed, message broker 
    - Folows the publis / subscribe messageaging pattern 
    - "at least once" message delivery
    - Push and Pull 
    - Ordering is not guarenteed 
    - optimised for throughput 
  - Cloud DataFlow 
    - Unified data processing platform for batch and streaming workloads 
    - Programming model is Apache Beam (open source)

Towards a new Architecture 
- at this point i am pretty lost and need to go over this again. 
  - releated terms: event sourcing, CQRS, Kappa
  - System is a single state machine 
  - State machine is implemented using PubSub topics and subscriptions 
    - Submitted > Withdrawn
    - Withdrawn > Submitted 
    - Submitted > Approved 

## Social Proof

[Tweet](https://twitter.com/MichaelCade1/status/1311999918333194243?s=20)