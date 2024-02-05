# EC2 Launch Types (Purchasing Options)
## 1. On Demand 
## 2. Reserved Instance
## 3. Spot Instance
## 4. Dedicated Host
## 5. Dedicated Instance

## 1. On-Demand
1. Pay for Compute capacity by the second with no long-term commitments.
2. You decides when to launch, stop, hibernate,start, reboot or terminate it.
## Use cases: 
short-term, irregular workloads that cannot be interrupted
-----------------Senario-------------------
Example:

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

Example:

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
