# Overview


Establishing performance benchmarks among different headless CMS frameworks is crucial for several reasons. Firstly, it allows developers to identify which CMS platforms can deliver fast and responsive content delivery, ensuring a smooth user experience. Performance-based comparisons help developers choose frameworks that can handle high traffic loads efficiently, preventing slow page load times or API response delays. Additionally, benchmarking performance enables developers to optimize their application's performance by selecting a CMS that aligns with their specific requirements. It helps in identifying bottlenecks, improving caching strategies, and implementing performance enhancements. By establishing performance standards, developers can make informed decisions and build applications that deliver optimal performance, enhancing user satisfaction and engagement.

# Dataset

A moderately sized dataset with a very simple schema was used for this initial round of benchmarking.

| Entity      | Record Count| 
| ----------- | ----------- | 
| Customer      | 250,000       |
| Products   | 500,000       |
| Orders   | 500,000       | 
| Order Details   | 1,000,000       | 

## Entity Relationships:

Each Customer has:
- 5 Products
- 3 Orders
- 3 Order Details

Note: I realize that these entity relationships don't make sense in the real world. I had trouble getting Strapi to work the way that I had hoped when I went to pull the customer and nested data from the API so I ended up with this more flat structure.

# Test Details
1. Get a random page of 25 results (gets a list of 25 customers and their related data)
1. Get a single customer record and their related data
1. Repeat steps 1 & 2 for 10 seconds

We'll perform the same test against all 3 platforms in order to establish an initial baseline.

The K6 Repository used to run the tests can be found here:
https://github.com/lane711/sonicjs-performance-k6

# Strapi
Server setup: AWS EC2 t3.xlarge
| Instance      | vCPU| Mem (GiB) | Storage | Network Performance (Gbps)***
| ----------- | ----------- | ---- |  ---- |  ---- | 
| t3.xlarge | 4 | 16 | EBS | Up tp 5 |



## K6 Results
![Strapi K6](/img/strapi-k6.png)



# Introduction

Lorem ipsum

