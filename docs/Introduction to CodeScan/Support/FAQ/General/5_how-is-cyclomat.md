## Metadata_Start
## title: How is Cyclomatic Complexity calculated?
## original-url : https://knowledgebase.autorabit.com/docs/how-is-cyclomatic-complexity-calculated
## article-id : 3cc3aabb-0764-4ebf-8ea6-8c070a77d710
## seo-title : How is Cyclomatic Complexity calculated - CodeScan
## description : Cyclomatic complexity in CodeScan is calculated by the number of decision points in a method. This is the average complexity between all methods in that class 
## Metadata_End
Cyclomatic complexity in [CodeScan](https://www.codescan.io/){target="_blank"} is calculated by the number of decision points in a method.  

For example, the below method would have a cyclomatic complexity of **5**.

```
public void newMethod() {
     for(Integer i = 0; i < 100; i++){
      if (a == b && b == c){
        doStuff();
      } else if(a != b) {
        doOtherStuff();
      }
     }
   }
```

This counts:

* The entry to the method
* The entry to the ***for*** loop
* The ***if*** statement and the first conditional
* The second conditional in the ***if*** statement
* The ***elseif*** statement

This does not include:

* ***else*** statements
* ***when else*** in switch statements

The cyclomatic complexity for a class will be the average complexity between all methods in that class.
