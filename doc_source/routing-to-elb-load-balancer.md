# Routing Traffic to an ELB Load Balancer<a name="routing-to-elb-load-balancer"></a>

If you host a website on multiple Amazon EC2 instances, you can distribute traffic to your website across the instances by using an Elastic Load Balancing \(ELB\) load balancer\. The ELB service automatically scales the load balancer as traffic to your website changes over time\. The load balancer also can monitor the health of its registered instances and route domain traffic only to healthy instances\. 

To route domain traffic to an ELB load balancer, use Amazon Route 53 to create an [alias record](http://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resource-record-sets-choosing-alias-non-alias.html) that points to your load balancer\. An alias record is a Route 53 extension to DNS\. It's similar to a CNAME record, but you can create an alias record both for the root domain, such as example\.com, and for subdomains, such as www\.example\.com\. \(You can create CNAME records only for subdomains\.\) 

**Note**  
Route 53 doesn't charge for alias queries to ELB load balancers or other AWS resources\.

## Prerequisites<a name="routing-to-elb-load-balancer-prereqs"></a>

Before you get started, you need the following:

+ An ELB load balancer\. You can use an ELB Classic, Application, or Network Load Balancer\. For information about creating a load balancer, see [Getting Started with Elastic Load Balancing](http://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/load-balancer-getting-started.html) in the *Elastic Load Balancing User Guide*\.

  Give the load balancer a name that will help you remember what it's for later\. The name that you specify when you create a load balancer is the name that you'll choose when you create an alias record in the Route 53 console\.

+ A registered domain name\. You can use Route 53 as your domain registrar, or you can use a different registrar\.

+ Route 53 as the DNS service for the domain\. If you register your domain name by using Route 53, we automatically configure Route 53 as the DNS service for the domain\. 

  For information about migrating DNS service to Route 53, see [Using Amazon Route 53 as the DNS Service for Subdomains Without Migrating the Parent Domain](creating-migrating.md)\.

## Configuring Amazon Route 53 to Route Traffic to an ELB Load Balancer<a name="routing-to-elb-load-balancer-configuring"></a>

To configure Amazon Route 53 to route traffic to an ELB load balancer, perform the following procedure\.

**To route traffic to an ELB load balancer**

1. Sign in to the AWS Management Console and open the Route 53 console at [https://console\.aws\.amazon\.com/route53/](https://console.aws.amazon.com/route53/)\.

1. In the navigation pane, choose **Hosted Zones**\.

1. Choose the name of the hosted zone that has the domain name that you want to use to route traffic to your load balancer\.

1. Choose **Create Record Set**\.

1. Specify the following values:  
**Name**  
Type the domain name that you want to use to route traffic to your ELB load balancer\. The default value is the name of the hosted zone\.  
For example, if the name of the hosted zone is example\.com and you want to use acme\.example\.com to route traffic to your load balancer, type **acme**\.  
**Type**  
Choose **A – IPv4 address**\.  
**Alias**  
Choose **Yes**\.  
**Alias Target**  
Find the applicable category in the list \(**ELB Application Load Balancers**, **ELB Classic Load Balancers**, or **ELB Network Load Balancers**\), and then choose the name that you assigned to the load balancer when you created it\.  
**Routing Policy**  
Accept the default value of **Simple**\.  
**Evaluate Target Health**  
If you want Route 53 to route traffic based on the health of your resources, choose **Yes**\. For more information about checking the health of your resources, see [Creating Amazon Route 53 Health Checks and Configuring DNS Failover](dns-failover.md)\.

1. Choose **Create**\.

   Changes generally propagate to all Route 53 servers within 60 seconds\. When propagation is done, you'll be able to route traffic to your load balancer by using the name of the alias record that you created in this procedure\. 