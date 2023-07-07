<h1 style="text-align: center;">Virtual Private Cloud</h1>

* Intro and research
* VPC Set up
  * Internet Gateway
  * Subnets
  * Route table
  * VPC
* App and DB set up

### Intro and research
VPCs (Virtual Private Cloud):

- What: A VPC is a virtual network environment provided by cloud computing platforms, allowing users to create a logically isolated section of the cloud where they can launch resources like virtual machines, databases, and load balancers. It provides network isolation and control, giving users the ability to define and manage their own virtual network topology.

- Why: VPCs offer several benefits, such as enhanced security, scalability, and flexibility. They provide isolation from other users in the cloud, allowing organizations to build secure and private networks. VPCs also enable businesses to scale their infrastructure as needed, launching and managing resources in a controlled environment. They provide the flexibility to configure IP addressing, subnets, routing, and connectivity options.

- Business Benefits: VPCs help businesses by providing a secure and private network environment. They allow organizations to isolate their resources, control network traffic, and apply security measures. VPCs also facilitate hybrid cloud deployments by providing connectivity options to on-premises networks. The scalability of VPCs enables businesses to handle growing workloads and fluctuating traffic demands effectively.

- DevOps Benefits: VPCs are highly beneficial for DevOps teams as they provide a controlled and flexible environment for deploying and managing infrastructure. DevOps teams can define and automate network configurations, leverage security groups and access controls, and integrate VPCs with other cloud services. VPCs also enable the creation of isolated development and testing environments, facilitating continuous integration and deployment workflows.

- Introduction of VPCs by AWS: AWS introduced VPCs to address the need for more granular control and security in cloud environments. Prior to VPCs, AWS used EC2-Classic, where instances were launched in a shared, flat network. VPCs were introduced to provide users with dedicated and isolated virtual networks, allowing fine-grained control over IP addressing, subnets, routing, and security. VPCs offer enhanced security features and greater flexibility, making them a preferred choice for deploying resources.

### VPC Set Up