# Searching with the Search Tester<a name="search-tester"></a>

The search tester in the Amazon CloudSearch console enables you to submit sample search requests using any of the supported query parsers: simple, structured, lucene, or dismax\. By default, requests are processed with the simple query parser\. You can specify options for the selected parser, filter and sort the results, and browse the configured facets\. The search hits are automatically highlighted in the search results\. For information about how this is done, see [Highlighting Search Hits in Amazon CloudSearch](highlighting.md)\. You can also select a suggester to get suggestions as you enter terms in the **Search** field\. \(You must configure a suggester before you can get suggestions\. For more information see [Getting Autocomplete Suggestions in Amazon CloudSearch](getting-suggestions.md)\.\)

By default, results are sorted according to an automatically\-generated relevance score, * \_score*\. For information about customizing how results are ranked, see [Sorting Results in Amazon CloudSearch](sorting-results.md)\.



**To search your domain**

1. Go to the Amazon CloudSearch console at [https://console\.aws\.amazon\.com/cloudsearch/home](https://console.aws.amazon.com/cloudsearch/home)\.

1. In the left navigation panel, choose the name of your domain to open its configuration\.

1. Choose **Run a test search**\.

1. To perform a simple text search, enter a search query and choose **Run**\. By default, all `text` and `text-array` fields are searched\. 

To search particular fields, expand **Options** and enter a comma\-separated list of the fields you want to search in the **Search fields** field\. You can append a weight to each field with a caret \(^\) to control the relative importance of each field in the search results\. For example, specifying `title^5, description` weights hits in the `title` field five times more than hits in the `description` field when calculating relevance scores for each matching document\.

To use the structured query syntax, select **Structured** from the **Query parser** menu\. Once you've selected the structured query parser, enter your structured query in the **Search** field and choose **Run**\. For example, to find all of the movies with *star* in the title that were released in the year 2000 or earlier, you could enter: `(and title:'star' year:{,2000])`\. For more information, see [Constructing Compound Queries](searching-compound-queries.md)\. To submit Lucene or DisMax queries, select the appropriate query parser\.

You can specify additional options for the selected query parser to configure the default operator and control which operators can be used in a query\. For more information, see [Search Request Parameters](search-api.md#search-request-parameters)\.

You can copy and paste the request URL to submit the request and view the response from a Web browser\. Requests can be sent via HTTP or HTTPS\.