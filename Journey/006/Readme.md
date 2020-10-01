<!-- This template removes the micro tutorial for a quicker post and removes images for a full template check out the 000-DAY-ARTICLE-LONG-TEMPLATE.MD-->

![placeholder image](https://storage.googleapis.com/gweb-uniblog-publish-prod/images/infrastructure-3.max-1000x1000.png)

# GCP Network Fundamentals

## Introduction

This is going to be a continued focus on learning the fundamentals of GCP for the next few days, leveraging content from YouTube and mostly Pluralsight video training. The focus is going to be more based on Compute and Storage as I have never been a great fan of networking (because it has never really sunk in, maybe another 100 days should be spent on that) this session or update will focus on the network fundamentals with GCP 

## Use Case

Google Cloud Platform Fundamentals
by Howard Dierking [Course Link](https://app.pluralsight.com/library/courses/google-cloud-platform-fundamentals/table-of-contents)

## Cloud Research

As much as I have mentioned about not being a fan of networking, this is down to my lack of understanding but this would be remiss of me not to at least walk through and note down the fundamentals and fundamental differences between GCP networking and other public cloud providers. 

And it is what enables the other areas around Compute and Storage to work together. 

What Makes Google's Network Special? 

- Size & Scale - around a million servers dealing with data globally being moved around the global network 
- Agility - designed to adapt to any change 
- Performance - throughput and latency the amount and speed 

You can see from the image at the top of the page that another advantage is that this is GCPs own cabling effort through Sea and Land and operated as a single WAN. 

- B4 network - Data center network (2013)
- Peering network - Edge Points of Presence (PoPs)
- Google global cache nodes - Edge caching nodes - remotely managed by Google but hosted in external DCs to GCP

Software Defined Networking (SDN)

- B4 (2013)
- Andromeda (2014) 
- Jupiter (2015)
- Espresso (2017)

these are the design basis to the SDN and GCP networking, likely we would not need to understand these. 

- Virtual Private Cloud 
  - Private network space - Subnets routes etc. 
    - VPCs 
  - metadata-driven approach to policy 
  - Shared VPCs for large and federated systems 

- Cloud Load Balancing 
  - Single, Load balanced IP Address 
  - Uses anycast IP addresses

- Cloud Armor & Telemtry 
  - Protection against DDoS attacks 
  - Applies policy on top of cloud load balancer 
  - telemetry provides detailed inspection of all VPC ingress and egress 

- Content Delivery Network 
  - Extends caching beyond peering edge
  - caches content on google global cache nodes 

- Cloud DNS 
  - Fasted DNS for many years 
  - leverages existing google DNS infrastructure 
  - Flexible DNS configuration management
  
- Cloud Interconnect 
  - connects existing network infrastrutre to google network 
  - includes both VPN and peering connections
  - supports direct and partner mediated connections 
  - I think this would be classed the same as Direct Connect and ExpressRoute from AWS and Microsoft Azure? 

- Network Service Tiers 
  - Base level and premium tiers 
  - difference based on how long traffic stays in google's network 

## Social Proof

[Tweet](https://twitter.com/MichaelCade1/status/1311662278907891714?s=20)