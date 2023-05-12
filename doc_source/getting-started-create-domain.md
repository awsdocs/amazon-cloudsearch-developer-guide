# Step 1: Create an Amazon CloudSearch Domain<a name="getting-started-create-domain"></a>

An Amazon CloudSearch domain encapsulates a collection of data you want to search, the search instances that process your search requests, and a configuration that controls how your data is indexed and searched\. You create a separate search domain for each collection of data you want to make searchable\. For each domain, you configure indexing options that describe the fields you want to include in your index and how you want to use them, analysis schemes that specify language\-specific text processing options for individual fields, expressions that you can use to customize how search results are ranked, and access policies that control access to the domain's document and search endpoints\. 

You interact with a search domain to:
+ Configure index and search options
+ Submit data for indexing
+ Perform searches

Each domain has a unique endpoint through which you submit search requests to the domain\. For example, the endpoint for a domain called *movies* created in the US East \(N\. Virginia\) region might be:

**Example**  

```
search-movies-mtshfsu2rje7ywr66uit3dei4m.us-east-1.cloudsearch.amazonaws.com
```

When creating a search domain, you specify a unique name for the domain\. Domain names must start with a letter or number and be at least 3 and no more than 28 characters long\. The allowed characters are: a\-z, 0\-9, and hyphen \(\-\)\. By default, new domains are created in the US East \(N\. Virginia\) region\. To create a domain in another region, you must explicitly specify the region when creating the domain\.

To configure the new domain, you must specify:
+ Indexing options for the data you want to search\. 
+ Access policies for the domain's document service and search service endpoints\. 

This tutorial shows you how to create and interact with a domain using the Amazon CloudSearch console\. To learn more, see [Creating a Search Domain](creating-domains.md)\.

**Important**  
The domain you're about to create will be live and you will incur the standard Amazon CloudSearch usage fees for the domain until you delete it\. For more information about Amazon CloudSearch usage rates, go to the [Amazon CloudSearch detail page](http://aws.amazon.com/cloudsearch/)\.

**To create your movies domain**

1. Go to the Amazon CloudSearch console at [https://console\.aws\.amazon\.com/cloudsearch/home](https://console.aws.amazon.com/cloudsearch/home)\.

1. Choose **Create domain**\.

1. Enter a name for your new domain\. Domain names must start with a letter or number and be at least 3 and no more than 28 characters\. Domain names can contain the following characters: a\-z \(lower case\), 0\-9, and \- \(hyphen\)\. Upper case letters and underscores are not allowed\.

1. Leave the other settings as their defaults and choose **Next**\.

1. Select **Sample data** and choose **IMDb movies \(demo\)** from the dropdown\. You can also automatically configure a search domain by analyzing a sample of your data\.

1. Choose **Next**\.

1. Review the index fields being configured\. Eleven fields are configured automatically for the imdb\-movie data: actors, directors, genres, image\_url, plot, rank, rating, release\_date, running\_time\_secs, title, and year\. 
**Note**  
By default, all options are enabled for each field\. While this is convenient for development and testing, fine\-tuning the options configured for each field according to how you use those fields can reduce the size of your index\. If your domain uses more than a single small search instance, tuning can help minimize the cost of running your domain\. 

   When you finish reviewing the indexing options, choose **Next**\.

1. For simplicity in this tutorial, use an open access domain\. Choose **Allow open access to the domain** and choose **Next**\.

1. Review the domain configuration and click **Create** to create your domain\. 

Amazon CloudSearch initializes resources for the domain, which can take about ten minutes\. During this initialization process, the status of the domain is **Processing**\. Once the status changes to **Active**, you can upload your data and start searching\.