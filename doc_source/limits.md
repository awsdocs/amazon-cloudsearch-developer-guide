# Understanding Amazon CloudSearch Limits<a name="limits"></a>

This table shows naming and size restrictions within Amazon CloudSearch\. You can [submit a request](https://console.aws.amazon.com/support/home#/case/create?issueType=service-limit-increase&limitType=service-code-cloudsearch-partitions-and-instances) if you need to increase the maximum number of search instances or partitions for a search domain\. For information about increasing other limits such as the maximum number of search domains, contact Amazon CloudSearch\.

The current Amazon CloudSearch limits are summarized in the following table\. 


| Item | Limit | 
| --- | --- | 
| Batch size | The maximum batch size is 5 MB\. | 
| Data loading volume | You can load one document batch every 10 seconds \(approximately 10,000 batches every 24 hours\), with each batch size up to 5 MB\.Exceeding this limit significantly increases the latency of document updates and could result in throttling\. To mitigate this risk, you can increase your update capacity by selecting a larger instance type\. For more information, see [Creating Document Batches](preparing-data.md#creating-document-batches)\. | 
| Document size | The maximum document size is 1 MB\. | 
| Expressions | [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/limits.html)  | 
| Highlighting | [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/limits.html)  | 
| Index fields | [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/limits.html) | 
| Naming conventions | [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/limits.html)  | 
| Policy document size | The maximum size of an Amazon CloudSearch policy document is 100 KB\. | 
| Region restriction | The ap\-northeast\-2 region supports only m4 instance types\. | 
| \_score | A document's text relevance score is a positive floating point value\. | 
| Search domains | Each AWS account can create up to 100 search domains\.  | 
| Search instances | [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/limits.html) | 
| Search partitions  | A search index can be split across a maximum of 10 partitions | 
| Search requests |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/limits.html)  | 
| Suggesters |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/limits.html) | 
| Synonym dictionary size | The maximum size of a Amazon CloudSearch synonym dictionary is 100 KB\. | 