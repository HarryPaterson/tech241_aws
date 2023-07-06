<h1 style="text-align: center;">Autoscaling groups</h1>

### Contents
* Intro
* Launch template
* Autoscaling groups

### Intro
 An autoscaling group (ASG) is a feature provided by cloud computing platforms, such as Amazon Web Services (AWS) that allows you to automatically scale the number of instances in a group based on defined conditions. When CPU usage of a VM is high it can lead to a crash. We can scale upwards and increase the capacity of the vm or we can scale sideways where we employ more VMs so if one crashes the application will still be running on another. We set up our configuration for this to have a minimum of 2 machines (in case one fails), a desired number of 2 (to avoid excess and increased cost) and a maximum number of 3 (created when dealing with two). The cpu usage is considered high above 50%.

### Launch template
For our ASG we will require a launch template which will instruct the ASG on what kind of instance we will run. This uses our previously made AMIs but provides all the additional information we need to run the application on the instance.
### Autoscaling group

Our autoscaling group will then work on our set configuration mentioned earlier.
Autoscaling groups often work in conjunction with load balancers. The load balancer distributes incoming traffic across multiple instances within the group, ensuring that the workload is evenly distributed and improving the overall availability and responsiveness of the application.

Note: Pictures needed on next set up