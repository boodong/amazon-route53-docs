# Limits<a name="DNSLimitations"></a>

Amazon Route 53 API requests and entities are subject to the following limits\.


+ [Limits on Entities](#limits-api-entities)
+ [Limits on API Requests](#limits-api-requests)

## Limits on Entities<a name="limits-api-entities"></a>

Amazon Route 53 entities are subject to the following limits\.

For information on getting current limits, see the following Route 53 actions:

+ [GetAccountLimit](http://docs.aws.amazon.com/Route53/latest/APIReference/API_GetAccountLimit.html) – Gets limits on health checks, hosted zones, reusable delegation sets, traffic flow policies, and traffic flow policy records

+ [GetHostedZoneLimit](http://docs.aws.amazon.com/Route53/latest/APIReference/API_GetHostedZoneLimit.html) – Gets limits on records in a hosted zone and on Amazon VPCs that you can associate with a private hosted zone

+ [GetReusableDelegationSetLimit](http://docs.aws.amazon.com/Route53/latest/APIReference/API_GetReusableDelegationSetLimit.html) – Gets the limit on the number of hosted zones that you can associate with a reusable delegation set


+ [Limits on Domains](#limits-api-entities-domains)
+ [Limits on Hosted Zones](#limits-api-entities-hosted-zones)
+ [Limits on Records](#limits-api-entities-records)
+ [Limits on Health Checks](#limits-api-entities-health-checks)
+ [Limits on Query Log Configurations](#limits-api-entities-query-log-configs)
+ [Limits on Traffic Flow Policies and Policy Records](#limits-api-entities-traffic-flow)
+ [Limits on ReusableDelegationSets](#limits-api-entities-reusable-delegation-sets)
+ [Limits on Autonaming](#limits-api-entities-autonaming)

### Limits on Domains<a name="limits-api-entities-domains"></a>


****  

| Entity | Limit | 
| --- | --- | 
| Domains | 50 per AWS account [Request a higher limit](https://console.aws.amazon.com/support/home#/case/create?issueType=service-limit-increase&limitType=service-code-route53)\. | 

### Limits on Hosted Zones<a name="limits-api-entities-hosted-zones"></a>


****  

| Entity | Limit | 
| --- | --- | 
| Hosted zones | 500 per AWS account [Request a higher limit](https://console.aws.amazon.com/support/home#/case/create?issueType=service-limit-increase&limitType=service-code-route53)\. | 
| Hosted zones that can use the same reusable delegation set  | 100 [Request a higher limit](https://console.aws.amazon.com/support/home#/case/create?issueType=service-limit-increase&limitType=service-code-route53)\. | 
| Amazon VPCs that you can associate with a private hosted zone | 100 [Request a higher limit](https://console.aws.amazon.com/support/home#/case/create?issueType=service-limit-increase&limitType=service-code-route53)\. | 
| Authorizations that you can create so you can associate Amazon VPCs that were created by one account with a hosted zone that was created by another account | 100 | 

### Limits on Records<a name="limits-api-entities-records"></a>


****  

| Entity | Limit | 
| --- | --- | 
| Records | 10,000 per hosted zone [Request a higher limit](https://console.aws.amazon.com/support/home#/case/create?issueType=service-limit-increase&limitType=service-code-route53)\. For a limit greater than 10,000 records in a hosted zone, an additional charge applies\.  | 
| Values in a record | 100 per record | 
| Geolocation, geoproximity, latency, multivalue answer, and weighted records | 100 records that have the same name and type | 

### Limits on Health Checks<a name="limits-api-entities-health-checks"></a>


****  

| Entity | Limit | 
| --- | --- | 
| Health checks | 200 active health checks per AWS account [Request a higher limit](https://console.aws.amazon.com/support/home#/case/create?issueType=service-limit-increase&limitType=service-code-route53)\. | 

### Limits on Query Log Configurations<a name="limits-api-entities-query-log-configs"></a>


****  

| Entity | Limit | 
| --- | --- | 
| Query log configurations | 1 per hosted zone | 

### Limits on Traffic Flow Policies and Policy Records<a name="limits-api-entities-traffic-flow"></a>


****  

| Entity | Limit | 
| --- | --- | 
| Traffic policies For more information about Route 53 traffic flow, see [Using Traffic Flow to Route DNS Traffic](traffic-flow.md)\. | 50 per AWS account [Request a higher limit](https://console.aws.amazon.com/support/home#/case/create?issueType=service-limit-increase&limitType=service-code-route53)\. | 
| Traffic policy versions | 1000 per traffic policy | 
| Traffic policy records \(referred to as "policy instances" in the Route 53 API, AWS SDKs, AWS Command Line Interface, and AWS Tools for Windows PowerShell\) | 5 per AWS account [Request a higher limit](https://console.aws.amazon.com/support/home#/case/create?issueType=service-limit-increase&limitType=service-code-route53)\. | 

### Limits on ReusableDelegationSets<a name="limits-api-entities-reusable-delegation-sets"></a>


****  

| Entity | Limit | 
| --- | --- | 
| Reusable delegation sets | 100 per AWS account [Request a higher limit](https://console.aws.amazon.com/support/home#/case/create?issueType=service-limit-increase&limitType=service-code-route53)\. | 

### Limits on Autonaming<a name="limits-api-entities-autonaming"></a>

Each limit listed applies to each region where you create autonaming resources\. For example, each AWS account can create 50 namespaces in each region\.


****  

| Entity | Limit | 
| --- | --- | 
| Namespaces per AWS account | 50 per region [Request a higher limit](https://console.aws.amazon.com/support/home?region=us-west-2#/case/create?issueType=service-limit-increase)  | 
| Instances per namespace | 2000 per region [Request a higher limit](https://console.aws.amazon.com/support/home?region=us-west-2#/case/create?issueType=service-limit-increase)  | 
| Instances per service | 100 per region [Request a higher limit](https://console.aws.amazon.com/support/home?region=us-west-2#/case/create?issueType=service-limit-increase)  | 

## Limits on API Requests<a name="limits-api-requests"></a>

Amazon Route 53 API requests are subject to the following limits\.

### Number of Elements and Characters in `ChangeResourceRecordSets` Requests<a name="limits-api-requests-changeresourcerecordsets"></a>

**`ResourceRecord` elements**  
A request cannot contain more than 1000 `ResourceRecord` elements\. When the value of the `Action` element is `UPSERT`, each `ResourceRecord` element is counted twice\.

**Maximum number of characters**  
The sum of the number of characters \(including spaces\) in all `Value` elements in a request cannot exceed 32,000 characters\. When the value of the `Action` element is `UPSERT`, each character in a `Value` element is counted twice\.

### Frequency of Amazon Route 53 API Requests<a name="limits-api-requests-route-53"></a>

**All requests**  
Five requests per second per AWS account\. If you submit more than five requests per second, Amazon Route 53 returns an HTTP 400 error \(`Bad request`\)\. The response header also includes a `Code` element with a value of `Throttling` and a `Message` element with a value of `Rate exceeded`\.

**`ChangeResourceRecordSets` requests**  
If Route 53 can't process a request before the next request arrives, it will reject subsequent requests for the same hosted zone and return an HTTP 400 error \(`Bad request`\)\. The response header also includes a `Code` element with a value of `PriorRequestNotComplete` and a `Message` element with a value of `The request was rejected because Route 53 was still processing a prior request.`

**`CreateHealthCheck` requests**  
You can submit a maximum of 1000 `CreateHealthCheck` requests in a 24\-hour period\.