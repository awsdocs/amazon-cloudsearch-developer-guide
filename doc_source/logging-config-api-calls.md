# Logging Amazon CloudSearch Configuration Service Calls Using AWS CloudTrail<a name="logging-config-api-calls"></a>

Amazon CloudSearch is integrated with CloudTrail, a service that logs all AWS API calls made by, or on behalf of, your AWS account\. The log files are delivered to the Amazon S3 bucket that you specify\. CloudTrail captures all Amazon CloudSearch configuration service API calls, including those submitted by the Amazon CloudSearch console\. 

You can use the information collected by CloudTrail to monitor activity for your search domains\. You can determine what request was made to Amazon CloudSearch, the source IP address from which the request was made, who made the request, when it was made, and so on\. To learn more about CloudTrail, including how to configure and enable it, see the [http://docs.aws.amazon.com/awscloudtrail/latest/userguide/](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\.

## Amazon CloudSearch Information in CloudTrail<a name="cloudsearch-info-in-cloudtrail"></a>

When CloudTrail logging is enabled in your AWS account, API calls made to Amazon CloudSearch actions are tracked in log files\. Amazon CloudSearch records are written together with other AWS service records in a log file\. CloudTrail determines when to create and write to a new file based on a time period and file size\.

All Amazon CloudSearch configuration service actions are logged\. For example, calls to `CreateDomain`, `DescribeDomains`, and `UpdateServiceAccessPolicies` generate entries in the CloudTrail log files\. For the complete list of actions, see [Actions](API_Operations.md)\. 

Every log entry contains information about who generated the request\. The user identity information in the log helps you determine whether the request was made with root or IAM user credentials, with temporary security credentials for a role or federated user, or by another AWS service\. For more information, see the `userIdentity` field in the [CloudTrail Event Reference](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/event_reference_top_level.html)\.

You can store your log files in your bucket for as long as you want, but you can also define Amazon S3 lifecycle rules to archive or delete log files automatically\. By default, your log files are encrypted by using Amazon S3 server\-side encryption \(SSE\)\.

You can choose to have CloudTrail publish Amazon SNS notifications when new log files are delivered if you want to take quick action upon log file delivery\. For more information, see [Configuring Amazon SNS Notifications](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/getting_notifications_top_level.html)\.

You can also aggregate Amazon CloudSearch log files from multiple AWS regions and multiple AWS accounts into a single Amazon S3 bucket\. For more information, see [Aggregating CloudTrail Log Files to a Single Amazon S3 Bucket](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/aggregating_logs_top_level.html)\.

## Understanding Amazon CloudSearch Log File Entries<a name="understanding-cloudsearch-event-entries"></a>

CloudTrail log files contain one or more log entries where each entry is made up of multiple JSON\-formatted events\. A log entry represents a single request from any source and includes information about the requested action, any parameters, the date and time of the action, and so on\. The log entries are not guaranteed to be in any particular order—they are not an ordered stack trace of the public API calls\.

CloudTrail log files include events for all AWS API calls for your AWS account, not just calls to the Amazon CloudSearch configuration service API\. However, you can read the log files and scan for the `eventSource` `cloudsearch.amazonaws.com`\. The `eventName` element contains the name of the configuration service action that was called\.

The following example shows a CloudTrail log for a user who created a search domain and then configured an index field for the domain\. The corresponding API calls \(`CreateDomain` and `DefineIndexField`\) are shown in the `eventName` element for each record\. Information about the user \(Alice\) is shown in the `userIdentity` element:

```
{
  "Records": [
    {
      "eventVersion": "1.01",
      "userIdentity": {
        "type": "IAMUser",
        "principalId": "AIDAI2JXM4FBZZEXAMPLE",
        "arn": "arn:aws:iam::123456789012:user/Alice",
        "accountId": "123456789012",
        "accessKeyId": "AKIAIOSFODNN7EXAMPLE"
      },
      "eventTime": "2014-09-12T19:47:32Z",
      "eventSource": "cloudsearch.amazonaws.com",
      "eventName": "CreateDomain",
      "awsRegion": "us-east-1",
      "sourceIPAddress": "198.51.100.0",
      "requestParameters": {
        "domainName": "imdb-movies"
      },
      "responseElements": {
        "domainStatus": {
          "created": true,
          "searchService": {
            
          },
          "processing": false,
          "docService": {
            
          },
          "domainName": "imdb-movies",
          "domainId": "123456789012\/imdb-movies",
          "requiresIndexDocuments": false,
          "searchPartitionCount": 0,
          "deleted": false,
          "arn": "arn:aws:cloudsearch:us-east-1:123456789012:domain\/imdb-movies",
          "searchInstanceCount": 0
        }
      },
    {
      "eventVersion": "1.01",
      "userIdentity": {
        "type": "IAMUser",
        "principalId": "AIDAI2JXM4FBZZEXAMPLE",
        "arn": "arn:aws:iam::123456789012:user/Alice",
        "accountId": "123456789012",
        "accessKeyId": "AKIAIOSFODNN7EXAMPLE"
      },
      "eventTime": "2014-09-12T19:47:34Z",
      "eventSource": "cloudsearch.amazonaws.com",
      "eventName": "DefineIndexField",
      "awsRegion": "us-east-1",
      "sourceIPAddress": "198.51.100.0",
      "requestParameters": {
        "domainName": "imdb-movies",
        "indexField": {
          "indexFieldType": "text",
          "indexFieldName": "plot",
          "textOptions": {
            "highlightEnabled": true,
            "returnEnabled": true,
            "analysisScheme": "_en_default_",
            "sortEnabled": true
          }
        }
      },
      "responseElements": {
        "indexField": {
          "options": {
            "indexFieldType": "text",
            "indexFieldName": "plot",
            "textOptions": {
              "highlightEnabled": true,
              "returnEnabled": true,
              "analysisScheme": "_en_default_",
              "sortEnabled": true
            }
          },
          "status": {
            "pendingDeletion": false,
            "state": "RequiresIndexDocuments",
            "updateDate": "Sep 12, 2014 12:47:33 PM",
            "creationDate": "Sep 12, 2014 12:47:33 PM",
            "updateVersion": 5
          }
        }
      },
      "requestID": "98c6c9f4-7e0f-4982-ae43-67a183e74968",
      "eventID": "3a7fe907-b482-46de-9f25-0ac035e84d1d"
    }   
  ]
}
```