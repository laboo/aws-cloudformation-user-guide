# AWS::WAF::Rule<a name="aws-resource-waf-rule"></a>

The `AWS::WAF::Rule` resource creates an AWS WAF rule that specifies a combination of `IPSet`, `ByteMatchSet`, and `SqlInjectionMatchSet` objects that identify the web requests to allow, block, or count\. To implement rules, you must associate them with a web ACL\.

For more information, see [CreateRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_CreateRule.html) in the *AWS WAF API Reference*\.


+ [Syntax](#aws-resource-waf-rule-syntax)
+ [Properties](#w3ab2c21c10e1047c11)
+ [Return Value](#w3ab2c21c10e1047c13)
+ [Example](#w3ab2c21c10e1047c15)

## Syntax<a name="aws-resource-waf-rule-syntax"></a>

To declare this entity in your AWS CloudFormation template, use the following syntax:

### JSON<a name="aws-resource-waf-rule-syntax.json"></a>

```
{
  "Type" : "AWS::WAF::Rule",
  "Properties" : {
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-waf-rule-metricname)" : String,
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-waf-rule-name)" : String,
    "[[ERROR] BAD/MISSING LINK TEXT](#cfn-waf-rule-predicates)" : [ Predicate, ... ]
  }
}
```

### YAML<a name="aws-resource-waf-rule-syntax.yaml"></a>

```
Type: "AWS::WAF::Rule"
Properties: 
  [[ERROR] BAD/MISSING LINK TEXT](#cfn-waf-rule-metricname): String
  [[ERROR] BAD/MISSING LINK TEXT](#cfn-waf-rule-name): String
  [[ERROR] BAD/MISSING LINK TEXT](#cfn-waf-rule-predicates):
    - Predicate
```

## Properties<a name="w3ab2c21c10e1047c11"></a>

`MetricName`  
A friendly name or description for the metrics of the rule\. For valid values, see the `MetricName` parameter for the [http://docs.aws.amazon.com/waf/latest/APIReference/API_CreateRule.html](http://docs.aws.amazon.com/waf/latest/APIReference/API_CreateRule.html) action in the *AWS WAF API Reference*\.  
*Required: *Yes  
*Type*: String  
*Update requires*: Replacement

`Name`  
A friendly name or description of the rule\.  
*Required: *Yes  
*Type*: String  
*Update requires*: Replacement

`Predicates`  
The `ByteMatchSet`, `IPSet`, `SizeConstraintSet`, `SqlInjectionMatchSet`, or `XssMatchSet` objects to include in a rule\. If you add more than one predicate to a rule, a request must match all conditions in order to be allowed or blocked\.  
*Required: *No  
*Type*: List of [AWS WAF Rule Predicates](aws-properties-waf-rule-predicates.md)  
*Update requires*: No interruption

## Return Value<a name="w3ab2c21c10e1047c13"></a>

### Ref<a name="w3ab2c21c10e1047c13b2"></a>

When the logical ID of this resource is provided to the `Ref` intrinsic function, `Ref` returns the resource physical ID, such as `1234a1a-a1b1-12a1-abcd-a123b123456`\.

For more information about using the `Ref` function, see Ref\.

## Example<a name="w3ab2c21c10e1047c15"></a>

### Associate an IPSet with a Web ACL Rule<a name="w3ab2c21c10e1047c15b2"></a>

The following example associates the `MyIPSetBlacklist` `IPSet` object with a web ACL rule\.

#### JSON<a name="aws-resource-waf-rule-example.json"></a>

```
"MyIPSetRule" : {
  "Type": "AWS::WAF::Rule",
  "Properties": {
    "Name": "MyIPSetRule",
    "MetricName" : "MyIPSetRule",
    "Predicates": [
      {
        "DataId" : {  "Ref" : "MyIPSetBlacklist" },
        "Negated" : false,
        "Type" : "IPMatch"
      }
    ]
  }      
}
```

#### YAML<a name="aws-resource-waf-rule-example.yaml"></a>

```
MyIPSetRule: 
  Type: "AWS::WAF::Rule"
  Properties: 
    Name: "MyIPSetRule"
    MetricName: "MyIPSetRule"
    Predicates: 
      - 
        DataId: 
          Ref: "MyIPSetBlacklist"
        Negated: false
        Type: "IPMatch"
```