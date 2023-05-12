# ScalingParameters<a name="API_ScalingParameters"></a>

## Description<a name="API_ScalingParameters_Description"></a>

The desired instance type and desired number of replicas of each index partition\.

## Contents<a name="API_ScalingParameters_Contents"></a>

 **DesiredInstanceType**   
The instance type that you want to preconfigure for your domain\. For example, `search.medium`\.  
Type: String  
Valid Values: `search.small | search.medium | search.large | search.xlarge | search.2xlarge`   
For older domains, valid values might also include `search.m1.small`, `search.m1.large`, `search.m2.xlarge`, `search.m2.2xlarge`, `search.m3.medium`, `search.m3.large`, `search.m3.xlarge`, and `search.m3.2xlarge`\.
Required: No 

 **DesiredPartitionCount**   
The number of partitions you want to preconfigure for your domain\. Only valid when you select `search.2xlarge` as the instance type\.  
Type: Integer  
Required: No 

 **DesiredReplicationCount**   
The number of replicas you want to preconfigure for each index partition\.  
Type: Integer  
Required: No 