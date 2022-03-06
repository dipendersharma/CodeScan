## Metadata_Start
## title: Ignoring violations
## original-url : https://knowledgebase.autorabit.com/docs/ignoring-violations
## article-id : ab0d11b0-336d-4562-ac4b-0cf719dad5f3
## seo-title : 
## description : 
## Metadata_End
There are multiple ways to ignore false positives or avoid unwanted violations in CodeScan.

## Using Mark as False Positive
When viewing your violations inline, **SonarQube™** allows you to mark **False Positives** to prevent further alerts about certain issues in your code. This will block that violation from appearing until it is unblocked.

This feature will not carry the false positive between projects. 
**For example**, if you mark an issue as a false positive in ProjectOne and create ProjectTwo from the same code source, the issue will still be present in ProjectTwo until it is marked otherwise.

## Using suppressUnitTestViolations
For each rule we have provided the parameter **suppressUnitTestViolations**. This stops any violations of this rule being reported in test methods. 
**For example**, setting **suppressUnitTestViolations** to true for the rule **AvoidSoqlInLoops** would ignore the violation below:
```
@IsTest
class newClass {
   void method1(){
     for (int i = 0; i < 10; i++){
       insert new Account(name = ‘Name ’ + i);
     }
   }
}
```
 
## Using @SuppressWarnings
**SonarQube™** allows you to mark **False Positives** to prevent further alerts about certain issues in your code but these changes wont be remembered if you have multiple environments that aren’t linked together.

Using the **@SuppressWarnings** annotation allows you to block rule violations for certain classes and methods.

The following will ignore all rule violations for the **class Test1**:
```
@SuppressWarnings(‘all’)
class newClass {
   void method1(){
     for (int i = 0; i < 10; i++){
       insert new Account(name = ‘Name ’ + i);
     }
   }
}
```

Whereas this would ignore only the rules given to **@SuppressWarnings** as parameters within **method1**:

```
class newClass {
  @SuppressWarnings(‘cs.AvoidSoqlInLoops’)
   void method1(){
     for (int i = 0; i < 10; i++){
       insert new Account(name = ‘Name ’ + i);
     }
   }
}
```

The same method can also be used for **fields**:
```
class newClass {
  @SuppressWarnings(‘sf:UnusedPrivateField’)
  integer x;
}
```

#### The names of the rules can be found in:

* **SonarQube™/CodeScan Cloud**, by clicking on a specific rule in the Rules menu.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28293%29.png){height="" width=""}
 
* **IntelliJ**, next to the rule violations themselves when a violation is selected.
CodeScan Rules found in IntelliJ
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28294%29.png){height="" width=""}

#### The syntax is as follows:

* Use ***@SuppressWarnings(‘cs.RULENAME’)*** for a specific rule name

* ***@SuppressWarnings(‘sf:RULENAME’)*** is also allowed

* Use ***@SuppressWarnings(‘cs.RULENAME, cs.OTHERULE’)*** to specify multiple rules, separating each new rule with a comma

* Use ***@SuppressWarnings(‘all’)*** to ignore all rules

## Using //NOSONAR
This can be used to ignore all rules on a single line:
```
class newClass {
   void method1(){
     for (int i = 0; i < 10; i++){
       insert new Account(name = ‘Name ’ + i); //NOSONAR
     }
   }
}
```
