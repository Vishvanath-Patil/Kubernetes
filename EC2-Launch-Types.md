# EC2 Launch Types (Purchasing Options)
## 1. On Demand 
## 2. Reserved Instance
## 3. Spot Instance
## 4. Dedicated Host
## 5. Dedicated Instance

## Overview of Instance types
**On Demand:** Stay and leave whenever you want. (Hotel)
**Reserved:** Plan to stay for long time and get discounts
**Spot instances:** Stay for the night in cheap price, but can be thrown out when someone pays more than you.
**Dedicated Host:** Book entire Building
**Dedicated Instance:** Book a Room


## 1. On-Demand
1. Pay for Compute capacity by the second with no long-term commitments.
2. You decides when to launch, stop, hibernate,start, reboot or terminate it.
## Use cases: 
short-term, irregular workloads that cannot be interrupted
-----------------Senario-------------------
## Example:

Imagine a startup company that is in the early stages of developing and testing a new mobile application. The company is uncertain about the potential popularity of the app and is not ready to commit to long-term infrastructure plans.

## Use Case:

## Scenario with On-Demand Instances:

**Variable Workload:** The startup's application experiences varying levels of traffic, especially during testing phases and promotional events.

**No Upfront Commitment:** Given the uncertainty about future demand and usage patterns, the startup opts for On-Demand Instances.

**Flexibility:** On-Demand Instances provide the flexibility to scale up or down based on current requirements. If the app gains sudden popularity, the startup can quickly add more instances to handle increased traffic.

**Pay-as-You-Go Pricing:** The startup pays only for the compute capacity used without any upfront costs or long-term commitments. This aligns with the company's agile and cost-conscious approach in the early stages.

## Benefits of On-Demand Instances:

**Flexibility:** On-Demand Instances are ideal for workloads with variable demand, providing the ability to scale resources up or down as needed.

**No Upfront Costs:** There are no upfront payments or commitments, making it suitable for projects with uncertain or changing requirements.

**Quick Provisioning:** Instances can be provisioned rapidly, allowing the startup to respond promptly to changing business needs.

**Cost-Efficient for Short-Term Projects:** On-Demand Instances are cost-effective for short-term projects, development, and testing where long-term commitments may not be appropriate.
While On-Demand Instances offer flexibility, they may not be the most cost-effective option for long-term, stable workloads. In such cases, companies may explore other purchasing options like Reserved Instances for potential cost savings over time. The key is to choose the pricing model that aligns with the specific characteristics and goals of the workload.

## 2. Reserved Instance
1. Provide Significant Discount (up to 72%) Compared to On-demand.
2. Tenure: 1 or 3 years
3. Payment: All upfront, partial upfront, No-upfront
4. Best Stable predictable workloads with long-term commitments
### 5. Types of Reserved Instances
  ### 1. Standard
  ### 2. Convirtible (can convert instance type)
  ### 3. Scheduled (can scheduled instance launch & termination)
----------Senario----------

## Example:

Let's consider a company that runs a web application on AWS and has a relatively stable and predictable workload. 
The company consistently uses a certain number of instances to handle the incoming traffic, and they expect this demand to continue for the next three years.

# Use Case:

## Scenario without Reserved Instances:

Without RIs, the company would rely on on-demand instances for their infrastructure needs. On-demand instances are flexible but come at a higher cost compared to RIs.
The company may end up paying a higher price over time, especially if the demand remains stable.

## Scenario with Reserved Instances:
The company analyzes its usage patterns and estimates the number of instances it needs for the next three years.
They decide to purchase Reserved Instances for a portion or all of their expected usage.
By committing to a one- or three-year term, the company receives a substantial discount compared to on-demand pricing.
This results in significant cost savings for the company over the reserved term.

## Benefits of Reserved Instances:
**Cost Savings:** RIs offer a cost-effective solution, providing savings of up to 75% compared to on-demand instances.

**Predictability:** For workloads with predictable usage, RIs allow companies to plan and budget more effectively.

**Capacity Assurance:** RIs provide assurance that the reserved capacity will be available, even during peak times.

It's important to note that Reserved Instances are best suited for predictable workloads with long-term commitments. 
If the workload is variable or if there are uncertainties in usage, other purchasing options like on-demand or spot instances might be more appropriate. 
The key is to align the purchasing strategy with the specific characteristics of the application's demand patterns and the organization's financial considerations.

## 3. Spot Instances 
Imagine an e-commerce website that regularly processes a high volume of web traffic. The website's traffic patterns are somewhat predictable during regular business hours, but there are occasional bursts of traffic due to flash sales, promotions, or unexpected events.

## Use Case:

## Scenario with Spot Instances:

**Variable Workload with Cost Sensitivity:** The e-commerce website typically experiences high traffic during certain periods but also has periods of lower demand.


**Cost Optimization:** To optimize costs during periods of lower demand, the website utilizes Spot Instances, which allow them to access spare EC2 capacity at a significantly lower price compared to On-Demand Instances.


**Flexible Scaling:** Spot Instances enable the website to quickly scale up resources during peak traffic periods and scale down during quieter times, taking advantage of available spare capacity.


**Cost Savings for Non-Critical Workloads:** Spot Instances are suitable for non-critical or fault-tolerant workloads where interruptions or terminations are acceptable and can be managed gracefully.

## Benefits of Spot Instances:

**Cost-Efficiency:** Spot Instances offer substantial cost savings, often providing compute capacity at a fraction of the On-Demand price.


**High Availability:** While Spot Instances can be interrupted if the capacity is needed by On-Demand or Reserved Instances, they are suitable for applications designed to handle interruptions gracefully.


**Scaling Opportunities:** Ideal for applications that can benefit from rapid scaling based on available spare capacity, such as batch processing, data analysis, and rendering tasks.

**Optimized for Bursty Workloads:** Spot Instances are well-suited for workloads with variable demand, making them cost-effective for bursty or intermittent processing requirements.

It's important to note that Spot Instances are not suitable for every workload, especially for applications that require continuous, uninterrupted availability. However, for scenarios where flexibility and cost optimization are key considerations, Spot Instances can be a valuable resource.

## 3. Dedicated Host
1. Dedicated Host is a physical server fully dedicated for your use.
2. User for Strong Regulatory compliance requirements.
3. Allow you to reduce cost by using your own Exiting License (BYOL)
4. Expensive.

## Example:

Consider a financial institution that is subject to strict regulatory compliance requirements. The institution hosts a variety of applications, including sensitive financial databases and transaction processing systems, in the cloud.

## Use Case:

### Scenario with Dedicated Hosts:

**Regulatory Compliance:** The financial institution must adhere to regulatory requirements that mandate physical isolation of their computing resources to ensure data security and compliance.


**Dedicated Hardware:** To meet regulatory standards, the institution utilizes Dedicated Hosts on AWS, which provide physical servers dedicated exclusively to their use. This ensures that their workloads do not share the same physical hardware with other AWS customers.


**Isolation and Security:** Dedicated Hosts offer a higher level of isolation and security by providing control over the placement of instances on the physical servers, reducing the risk of noisy neighbor issues.


**License Compliance:** The financial institution may have specific software licensing requirements that are tied to physical servers. Dedicated Hosts allow them to bring their existing licenses to the cloud while maintaining compliance.

## Benefits of Dedicated Hosts:

**Regulatory Compliance:** Ideal for industries with stringent regulatory requirements, such as finance, healthcare, or government, where physical isolation is necessary for compliance.


**Isolation and Security:** Provides enhanced isolation and security by dedicating physical servers to a single customer, minimizing the risk of unauthorized access or interference from other tenants.


**Control over Placement:** Offers control over the placement of instances on specific physical servers, allowing organizations to meet specific performance, security, and compliance requirements.


**License Flexibility:** Useful for workloads that have licensing dependencies tied to physical servers, allowing organizations to bring their own licenses to the cloud.

While Dedicated Hosts offer strong isolation and control, they might not be necessary for all workloads. They are typically chosen in scenarios where regulatory compliance or specific licensing requirements necessitate the use of dedicated physical hardware.

## Dedicated Instances
1. Hardware that is Dedicated to launch only your instances
2. You cannot control it like you do in Dedicated Host
   Use case will be same as Dedicated Host.









