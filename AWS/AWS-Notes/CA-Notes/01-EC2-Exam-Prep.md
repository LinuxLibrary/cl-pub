# EC2 Exam Preperation

* **AMIs and Instance Types**:
    - AMIs are digital templates of pre-configured EC2 Instances allowing you to quickly launch a new instance
    - You have the choice of AWS Managed, custom, market place and community AMIs

* **Instance Types**:
    - Instance types are defined ny different parameters and their values such as amount of memory, network performance, storage etc.
    - As your instance size gets bigger, the parameter values (vCPU, network performance, storage) also increases
    - Some instances only support EBS and do not support for ephermal storage
    - General purpose instances gives a good balance of compute, memory and network resources, so its great for lots of different use cases
    - Compute optimized instances are designed for compute intensive workloads requiring high performance processors
    - Memory optimized instances help you deliver super fast performance for processing data sets in memory
    - Accelerated computing instance types use hardware accelerators which are great for graphics and data pattern matching
    - Storage optimzed instances maintain low latency IOPS and sequential read and write access to massive data sets locally

* **EC2 Purchase Options**:
    * **On-Demand Instances**:
        - Can be launched at any time
        - Provisioned and available within minutes
        - No duration limit
        - A flat cost rate paid by the second
        - Suitable for short time workloads
        - Used for irregular an interruptible workloads
        - Stop paying when the resource is stopped or terminated
    * **Spot Instances**:
        - Bid for unused EC2 compute resources
        - Huge cost saving can be achieved
        - There is no assurance that you will have spot instances for a fixed period of time
        - The instance is purchased when your bid price is higher than the fluctuating spot price
        - Spot price fluctuates depending on the supply and demand of the unused resources
        - If your bid price drops below spot price a two minute warning is issued before the instance automatically terminates
        - Useful for workloads that can be suddenly interrupted
    * **Reserved Instances**:
        - Purchase instances at a discounted rate over a 1 or 3 year period
        - Savings can be as much as 75% compared to on-demand instances
        - All upfront payment allows you to pay the entire resource for a single or three year period, and provides the biggest discount
        - Partial upfront payment allows you to pay a partial upfront and then a discount is applied to any hours used by the instance
        - No upront payment gives the smallest discount of the 3 options
        - Used for long term predictable workloads
    * **Scheduled Instances**:
        - Pay for the reservation of an instance on a recurring schedule, either daily, weelky or monthly
        - You are charged for the instance even if you don't use it
        - Used to run scheduled workloads that are not running continuously
    * **Capacity Reservations**:
        - Reserve capacity for EC2 instances based on attributes such as instance type, platform and tenancy etc.
        - Reserved within particular availibility zone for a period of time
        - Ensures you have capacity when its required
        - Can also be used in conjunction with your reserved instances discount providing you additional savings