# Tagging Amazon CloudSearch Domains<a name="tagging-cloudsearch-domains"></a>

Use Amazon CloudSearch tags to attach metadata to your search domains\. AWS does not apply any semantic meaning to your tags; tags are interpreted strictly as character strings\. All tags contain the following elements\.


****  

| Tag Element | Description | 
| --- | --- | 
| Tag key | The tag key is the required name of the tag\. Tag keys must be unique for the domain to which they are attached\. For a list of basic restrictions on tag keys and values, see [Tag Restrictions](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/allocation-tag-restrictions.html)\. | 
| Tag value | The tag value is an optional string value of the tag\. Tag values can be null and do not have to be unique in a tag set\. For example, you can have a key\-value pair in a tag set of project/Trinity and cost\-center/Trinity\. For a list of basic restrictions on tag keys and values, see [Tag Restrictions](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/allocation-tag-restrictions.html)\. | 

Each Amazon CloudSearch domain has a tag set, which contains all the tags that are assigned to that domain\. AWS does not automatically set any tags on Amazon CloudSearch domains\. A tag set can contain as many as ten tags, or it can be empty\. If you add a tag to an Amazon CloudSearch domain that has the same key as an existing tag for a resource, the new value overwrites the old value\. 

You can use a tag key to define a category, and the tag value can be a item in that category\. For example, you could define a tag key of `project` and a tag value of `Salix` indicating that the domain is assigned to the Salix project\. You could also use tags to designate domains for test or production environments by using keys such as `environment=test` and `environment=production`\. We recommend that you use a consistent set of tag keys to make it easier to track metadata associated with your search domains\. 

You also can use tags to organize your AWS bill to reflect your own cost structure and to track costs by grouping expenses for similarly tagged resources\. To do this, sign up to get your AWS account bill with tag key values included\. Then, organize your billing information according to resources with the same tag key values to see the cost of combined resources\. For example, you can tag several Amazon CloudSearch domains with key\-value pairs, and then organize your billing information to see the total cost for each domain across several services\. For more information, see [Cost Allocation and Tagging](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-alloc-tags.html) in the *AWS Billing and Cost Management* documentation\.

**Note**  
Tags are cached for authorization purposes\. Because of this, additions and updates to tags on Amazon CloudSearch domains might take several minutes before they are available\.

## Working with Tags \(Console\)<a name="es-managedomains-awsresourcetagging-console"></a>

Use the following procedure to create a resource tag with the Amazon CloudSearch console\.

**To create a tag**

1. Go to [https://aws\.amazon\.com](https://aws.amazon.com) and choose **Sign In to the Console**\.

1. Under **Application Services**, choose **CloudSearch**\.

1. On the navigation pane, choose your domain\.

1. On the navigation pane, choose **Manage tags**\.

1. In the **Key** column, enter a tag key\.

1. \(Optional\) In the **Value** column, enter a tag value\.

1. Choose **Submit**\.

**To delete a tag**

1. Go to [https://aws\.amazon\.com](https://aws.amazon.com) and choose **Sign In to the Console**\.

1. Under **Application Services**, choose **CloudSearch**\.

1. On the navigation pane, choose your domain\.

1. On the navigation pane, choose **Manage tags**\.

1. Next to the tag that you want to delete, choose **Remove tag**\.

1. Choose **Submit**\.

For more information about using the console to work with tags, see [Working with the Tag Editor](https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/tag-editor.html) in the *AWS Management Console Getting Started Guide*\.

## Working with Tags \(AWS CLI\)<a name="es-managedomains-awsresourcetagging-cli"></a>

You can create resource tags for your Amazon CloudSearch domains using the AWS CLI with the add\-tags command\. 


****  

| Parameter | Description | 
| --- | --- | 
| \-\-arn | Amazon resource name for the domain to which the tag is attached\. | 
| \-\-tag\-list | Set of space\-separated key\-value pairs in the following format: Key=<key>,Value=<value> | 

**Example**

The following example creates two tags for the `logs` domain:

```
aws cloudsearch add-tags --arn arn:aws:cs:us-east-1:1:379931976431:domain/logs --tag-list Key=service,Value=CloudSearch Key=instances,Value=m3.2xlarge
```

You can remove tags from a domain using the remove\-tags command\. 

** Syntax **

`RemoveTags --arn=<domain_arn> --tag-keys Key=<key>,Value=<value>`


****  

| Parameter | Description | 
| --- | --- | 
| \-\-arn | Amazon Resource Name \(ARN\) for the domain to which the tag is attached\. | 
| \-\-tag\-keys | Set of space\-separated tag keys that you want to remove from the domain\. | 

**Example**

The following example removes two tags from the `logs` domain that were created in the preceding example:

```
aws cloudsearch remove-tags --arn arn:aws:cs:us-east-1:379931976431:domain/logs --tag-keys service instances
```

You can view the existing tags for a domain with the list\-tags command:

**Syntax**

`list-tags --arn=<domain_arn>`


****  

| Parameter | Description | 
| --- | --- | 
| \-\-arn | Amazon Resource Name \(ARN\) for the domain to which the tags are attached\. | 

**Example**

The following example lists all resource tags for the `logs` domain:

```
aws cloudsearch list-tags --arn arn:aws:cs:us-east-1:379931976431:domain/logs
```

## Working with Tags \(AWS SDKs\)<a name="es-managedomains-awsresourcetagging-sdk"></a>

The AWS SDKs \(except the Android and iOS SDKs\) support all of the actions defined in the [Amazon CloudSearch Configuration API Reference](configuration-api.md), including the `AddTags`, `ListTags` and `RemoveTags` commands\. For more information about installing and using the AWS SDKs, see [AWS Software Development Kits](http://aws.amazon.com/code)\. 