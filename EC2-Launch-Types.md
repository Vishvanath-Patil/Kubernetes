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
