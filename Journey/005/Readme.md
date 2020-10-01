<!-- This template removes the micro tutorial for a quicker post and removes images for a full template check out the 000-DAY-ARTICLE-LONG-TEMPLATE.MD-->

![placeholder image](https://miro.medium.com/max/1200/1*uAxoEkgJPmD_TUbcObfKeA.png)

# GCP Storage Fundamentals

## Introduction

This is going to be a continued focus on learning the fundamentals of GCP for the next few days, leveraging content from YouTube and mostly Pluralsight video training. The focus is going to be more based on Compute and Storage as I have never been a great fan of networking (because it has never really sunk in, maybe another 100 days should be spent on that) this session or update will focus on the storage fundamentals with GCP 

## Use Case

Google Cloud Platform Fundamentals
by Howard Dierking [Course Link](https://app.pluralsight.com/library/courses/google-cloud-platform-fundamentals/table-of-contents)

## Cloud Research

- Cloud SQL 
  - Managed Postgres & MySQL 
  - Scalable for most OLTP workloads
  - Benefits from compute engine cost optimisations
  - Runtime and management configuration 
  - Data encrypted in transit and at rest 


- Cloud Storage 
  - Global Blob Storage 
    - Similar to Microsoft Azure Blob Storage / AWS S3 
    - Object Storage 
    - Automatic Edge Caching - No requirement for CDN (I think this is different to the other public clouds?)
    - Different storage classes for different data types 
      - Multi Regional for frequently accessed public data for example a website 
      - regional for localy scoped 
      - nearline data that is accessed no more than once a month 
      - coldline infrequently 
      - Data can be moved between these storage classes 
      - Cost vs Performance as with all storage offerings in the cloud 
    - Object Lifecycle management 
      - Conversion 
      - rules 
      - automate between storage classes - this is the interesting one we will look to deep diver into 

- Persistant Disk - Compute Engine 
  - Block storage for use with compute VMs 
  - Independant of VMs 
  - 128 persistant disks limit (what would need that limit?)
  - Highly configurable 
    - Standard Disk or SSD 
    - region or zone 
    - data encryption 
    - resize at any time  
    - regional persistance disks? 
  -   Managed & Optimised infrastructure

- Cloud FileStore
  - Managed Network Attached Storage 
  - Shared block storage compute VMs or containers (This is a note from something that was said in the training module but i think this is just saying that storage is shared via network its not a block based protocol being used?)
  - Low latency, low maintenance 
  - I have another question here that I will dive deeper into later about what other services can offer more performance around NAS for example NetApp have their Cloud Volumes Service within GCP is there a big difference between CVS and GCP Cloud FileStore I expect so as this is a difference in Microsoft Azure also. 
  
- Cloud Bigtable
  - High performance at scale (PB scale)
    - GMAIL built on 
  - Managed infrastructure 
  - Libary support for multiple languages (much the same as other public cloud offerings)
  - All entity information modelled as a row with a single index 
  - No transactional guarrantees beyond a row operation 
  - optimsed for sparsely populated rows. 

- Cloud Spanner
  - Horizontally-Scalable managemd Relational Database 
  - Distributed transaction support 
  - "Spanner is Google's highly available global SQL database, It manages replicated data at great scale, both in terms of of size of data and volume of transactions. It assigns globally consistent real-time timestamps to every datum written to it, and clients can do globally consistent reads across the entire database without locking."
  - TrueTime is also mentioned here. 
  - Built for Google's own applications 
  - Scales like a NoSQL database 

- Cloud Datastore (Firestore)
  - To begin has to enable an App Engine Compute configuration 
  - Used for managing structured data 
  - Same question here vs something for example as NetApp Cloud Volumes Service offerings? 
  - Limited transaction support 
  - Scales based on size of the query results 
  - rebranded to Cloud FireStore from an acquisition 
    - brings together cloud datastore and the firebase real-time database 
    - changes the data model and storage model 
    - full transaction support 
    - 3 modes for transition from Cloud Datastore 
      - Cloud Datastore - standard cloud datastore database (see above) production SLA
      - Cloud Firestore - in cloud firestore in datastore mode the benefits of the storage but without the next option (transactional gaurantees) server app tolerate beta 
      - Cloud FireStore Native mode - mobile web app 
        - offline support and all other new features mentioned above for Firestore 

- Cloud Memorystore
  - In-Memory database 
  - Ideal for caching 
  - Supports Redis application protocol 
  - Managed Infrastructure 

I thought the flow chart was also very useful that i have used at the top of the page. My learning would be much more focused around Cloud Storage and Cloud Filestore. 


## Social Proof

[Tweet](https://twitter.com/MichaelCade1/status/1311656487404531713?s=20)
