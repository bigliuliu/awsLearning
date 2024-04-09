# Fundamental

## 概念

* EC2 is one of the most of popular of AWS's offering
* EC2 =  Elastic [弹性] Compute Cloud = Infrastructure as a Service
* It mainly consists in the capability [能力]of :
1. Renting virtual machines (EC2)
2. Storing data on virtual drives (EBS)
3. Distributing load across machine [在机器上分配负载] (ELB)
4. Scaling the services using an auto-scaling group [使用自动缩放组缩放服务](ASG)
* Knowing EC2 is fundamental to understand how the Cloud works
## EC2 sizing & configuration options

* Operating System:Linux, Windows or Mac OS
* How much compute power & cores [核心](CPU)
* How much random-access memory (RAM) [随机存取存储器]
* How much storage space :
1. Network-attached [网络附加] （EBS & EFS）
2. hardware ( EC2 Instance [实例] Store)
* NetWork card : speed of the card , public IP address
* Firewall rules : security group
* Bootstrap [引导] script (configure at first launch [启动]) : EC2 User Data
## *EC2 User Data

* it is possible to bootstrap our instance using an EC2 User data script
* bootstrapping means launch commands when a machine starts [引导意味着机器启动时启动命令]
* that script is only run once at the instance first start
* EC2 user data is used to automate boot [启动] tasks such as :
1. installing updates
2. installing software
3. downloading common files from the internet
4. anything you can think of
* the EC2 User Data Script runs with the root user
### EC2 instance 在停止后再重新启动，aws会分配新的ip地址

## *EC2 instance type

* use different type of EC2 instances that are optimised [优化] for different use cases([https://aws.amazon.com/ec2/instance-types/](https://aws.amazon.com/ec2/instance-types/))
* aws has the following naming convention [习惯]
**etc ：m5.2xlarge**

* m: instance class
* 5: generation  (AWS improves them over time)
* 2xlarge : size within the instance class
### general purpose [通用的用途]

* great for a diversity of workloads such as web servers or code repositiories [非常适合各种工作负载，例如 Web 服务器或代码存储库]
* balance between:
1. compute
2. memory
3. networking
### compute optimized [优化]

* great for compute-intensive tasks [计算密集型任务] that require high performance processors:
1. batch processing workloads [批处理工作负载]
2. media transcoding
3. high performance [高性能] web servers
4. high performance computing (HPC)
5. scientific modeling & machine learning
6. dedicated [专用的] gaming servers
### memory optimized

* fast performance for workloads that process large data sets in memory[处理内存中大型数据集的工作负载具有快速性能]
* use cases :
1. high performace, relational / non-relational databases
2. distributed web scale cache stores
3. in-memory databases optimized for BI (business intelligence)
4. application performing real-time processing of big unstructured data
### storage optimized

* great for storage-intensive tasks that require high ,sequential[顺序] read and write access to large data sets on local storage.
* use cases:
1.  high frequency online transaction processing(OLTP) systems
2. relational & NoSQL databases
3. cache for in-memory database(for example, redis)
4. data warehousing [仓储] applications
5. distributed file systems 
## Security Groups

* security groups are the fundamental of network security in AWS
* they control how traffic is allowed into or out of our EC2 instance
* security groups only contain allow rules
* security groups rules can reference [参考] by ip or by security group
### Deeper Dive [深层次的理解]

* security groups are acting as a "firewall" on EC2 instance
* they regulate [监察]:
1. access to ports
2. authorised [授权] IP ranges - IPV4 and IPV6
3. control of inbound [入] network (from other to the instance)
4. control of outbound [出] network (from the instance to other)
### security group good to know

* can be attached [附加] to multiple instances
* locked down to a region / VPC combination [锁定到区域/VPC 组合]
* does live "outside" the EC2 - if traffic is blocked the EC2 instance won't see it [确实存在于 EC2“外部” - 如果流量被阻止，EC2 实例将看不到它]
* it's good to maintain [维护] on separate security group for SSH access [ 最好在单独的安全组上维护以进行 SSH 访问]
* if your application is not accessible (time out), then it's a security group issue
* if your application gives a "connection refused" error, then it's an application error or it's not launched
* all inbound traffic is blocked by default [默认情况下阻止所有入站流量]
* all outbound traffic is authorised by default [默认情况下授权所有出站流量]
### reference other security group [引入其他的安全组]

## Ports to Know

* 22 = SSH (secure shell) - log into a Linux instance
* 21 = FTP (File Transfer Protocol) - upload files into a file share
* 22 = SFTP (Secure File Transfer Protocol) - upload files using SSH
* 80 = HTTP - access unsecured websites
* 443 = HTTPS - accuess secured websites
* 3389 =RDP (Remote Desktop Protocol) - log into a Windows instance
## SSH Summary Table

*  SSH 连接到EC2  
```c++
ssh -i .\EC2 Tutorial.pem ec2-user@18.183.50.65
```
* EC2 instance connect  :
1. 连接到IAM 需要给EC2 instance 添加 IAM Roles
2. 添加完成后，执行：aws iam list-users
## *which purchasing [购买] option is right for me ?

#### On demand [按需]

* coming and staying in resort  [度假村，类比ec2]whenever we like, we pay the full price [来度假村只要我们愿意，我们就支付全价]
#### Reserved [预定]

* like planning ahead and if we plan to stay for a long time ,we may get a good discount [像提前计划，如果我们计划长期停留，我们可能会得到很好的折扣]
* EC2 Reserved Instances can be reserved for 1 or 3 years only.
#### Savings Plans [储蓄计划]

* pay a certain amount per hour for certain period and stay in any room type (e.g .king, suite,sea view) [在一定时间内每小时支付一定金额并入住任何房型]
#### Spot instances [现货实例]

* the hotel allows people to bid [出价] for the empty rooms and the highset bidder keeps the rooms. you can get kicked [踢] out at any time [酒店允许人们对空房间出价，出价最高的人保留房间。你随时都可能被踢出去]
#### Dedicated Hosts [专用主机]

* we book an entire building of the resort [我们预订了度假村的整栋建筑]
* Dedicated Hosts are good for companies with strong compliance needs or for software that have complicated licensing models. 
* This is the most expensive EC2 Purchasing Option available.
#### Capacity Reservations [容量预留]

* you book a room for a period with full price even you don't stay in it [即使您不住在其中，您也可以全价预订一段时间的房间]





