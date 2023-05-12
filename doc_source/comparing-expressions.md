# Comparing Expressions in Amazon CloudSearch<a name="comparing-expressions"></a>

 You can use the Amazon CloudSearch console to compare expressions and see how changes to the expression and field weights affect how Amazon CloudSearch sorts search results\.

**To compare expressions**

1. Open the Amazon CloudSearch console at [https://console\.aws\.amazon\.com/cloudsearch/home](https://console.aws.amazon.com/cloudsearch/home)\.

1. In the left navigation pane, choose **Domains**\.

1. Choose the name of the domain to open its configuration\.

1. Choose **Actions**, **Compare expressions**\.

1. In the **Search** box, enter the terms you want to search for\. Amazon CloudSearch ranks the search results using the specified expressions and weights\. It refreshes the results whenever you make changes to the expressions or weights\.

1. In each expression editor, specify the rank expressions to compare\. You can add new expressions or select an existing expression from the **Saved expressions** menu\. Amazon CloudSearch evaluates new expressions when you submit a search request\.

1. Specify the field weights to use for each expression\. You can also edit the field weights directly in the expression\. Field weights must be in the range 0\.0 to 10\.0, inclusive\. By default, the weight for all fields is set to 1\.0\. You can set individual field weights to control how much matches in particular text or literal fields affect a document's relevance \_score\. You can also change the default weight\.
**Note**  
Adjusting field weights only affects result ranking if the expression references the `_score` value\. You can modify the expression to change how the weight relevance `_score` contributes to a document's overall ranking\. For more information, see [Using Relative Field Weighting to Customize Text Relevance](weighting-fields.md)\.

1. Choose **Run**\.

1. The search results for the two expressions are shown side\-by\-side\. \(If the expression is empty, the results are sorted according to the default relevance `_score`\.\) Four icons highlight the differences:  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/images/cloudsearch-console-green-up-arrow.png) Green up arrow  
 The document is ranked higher in the search results using the second expression\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/images/cloudsearch-console-red-down-arrow.png) Red down arrow  
 The document is ranked lower in the search results using the second expression\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/images/cloudsearch-console-yellow-plus.png) Yellow plus  
 The document is included in the search results using the second expression, but was omitted from the search results using the first expression\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/images/cloudsearch-console-red-minus.png) Red minus  
 The document was omitted from the search results using the second expression, but was included in the search results using the first expression\. 

**Note**  
You can save expressions to your domain configuration directly from the **Compare expressions** pane\. To save either expression, choose **Save expression**\.