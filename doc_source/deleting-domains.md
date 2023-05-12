# Deleting an Amazon CloudSearch Domain<a name="deleting-domains"></a>

If you are no longer using a search domain, you must delete it to avoid incurring additional usage fees\. You will still be charged for a domain even if it does not contain any documents—deleting all documents does not delete the domain\. Deleting a domain deletes the index associated with the domain and takes the domain's document and search endpoints offline permanently\. It can take some time to completely remove a domain and decommission all of its resources\. Small domains are typically deleted in a short amount of time, while especially large domains may require an extended amount of time to be deleted\. During this process, the domain status is `Being Deleted` and your account is not charged\. 

You can delete a domain from the Amazon CloudSearch console, using the `aws cloudsearch delete-domain` command, or using the AWS SDKs\.

**Topics**
+ [Amazon CloudSearch console](#deleting-domains-console)
+ [Deleting a Domain Using the AWS CLI](#deleting-domains-clt)
+ [DeleteDomain](#deleting-domains-sdk)

## Deleting a Domain Using the Amazon CloudSearch Console<a name="deleting-domains-console"></a>

You can easily delete a domain from the domain dashboard in the Amazon CloudSearch console\. 

**To delete a domain**

1. Open the Amazon CloudSearch console at [https://console\.aws\.amazon\.com/cloudsearch/home](https://console.aws.amazon.com/cloudsearch/home)\.

1. In left **Navigation** pane, choose **Domains**\.

1. Select the checkbox next to the domain that you want to delete, then choose **Delete** and confirm deletion\.

## Deleting a Domain Using the AWS CLI<a name="deleting-domains-clt"></a>

Run the `aws cloudsearch delete-domain` command and specify the name of the domain you want to delete\. For example, to delete the *movies* domain, you specify `--domain-name movies`\.

```
aws cloudsearch delete-domain --domain-name movies  
```

 For information about installing and setting up the AWS CLI, see the [AWS Command Line Interface User Guide](https://docs.aws.amazon.com/cli/latest/userguide/)\. 

## Deleting Amazon CloudSearch Domains Using the AWS SDKs<a name="deleting-domains-sdk"></a>

The AWS SDKs \(except the Android and iOS SDKs\) support all of the Amazon CloudSearch actions defined in the Amazon CloudSearch Configuration API, including `DeleteDomain`\. For more information about installing and using the AWS SDKs, see [AWS Software Development Kits](http://aws.amazon.com/code)\.