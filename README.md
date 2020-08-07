
# The Challenge

Imagine we have a list of jobs, each represented by a character. Because certain jobs must be done before others, a job may have a dependency on another job.

For example,  `a`  may depend on  `b`, meaning the final sequence of jobs should place  `b`  before  `a`.

If  `a`  has no dependency, the position of  `a`  in the final sequence does not matter.

-   Given you’re passed an empty string (no jobs), the result should be an empty sequence.
    
-   Given the following job structure:  `a =>`  The result should be a sequence consisting of a single job  `a`.
    
-   Given the following job structure:
    
    ```
    a =>
    b =>
    c =>
    
    ```
    
    The result should be a sequence containing all three jobs  `abc`  in no significant order.
    
-   Given the following job structure:
    
    ```
    a =>  
    b => c  
    c =>
    
    ```
    
    The result should be a sequence that positions  `c`  before  `b`, containing all three jobs  `abc`.
    
-   Given the following job structure:
    
    ```
    a =>  
    b => c  
    c => f  
    d => a  
    e => b  
    f =>
    
    ```
    
    The result should be a sequence that positions  `f`  before  `c`,  `c`  before  `b`,  `b`  before  `e`  and  `a`  before  `d`  containing all six jobs  `abcdef`.
    
-   Given the following job structure:
    
    ```
    a =>  
    b =>  
    c => c
    
    ```
    
    The result should be an error stating that jobs can’t depend on themselves.
    
-   Given the following job structure:
    
    ```
    a =>
    b => c
    c => f
    d => a
    e =>
    f => b
    
    ```
    
    The result should be an error stating that jobs can’t have circular dependencies.
    
# Implementation Details
The challenge should be completed in C# targeting .NET core 3.1. You may use a test framework of your choice, e.g xUnit/NUnit/MSTest to verify the functionality. The rule set above must be verified by a suite of tests, as your approach to testing is as much a part of the challenge as the implementation itself. It is not necessary to parse any input text files. The tests may drive the implementation directly with input data.

# Examples  
Below are some examples of inputs and expected outputs. Note that this is not an exhaustive list and your tests should cover the whole rule set defined above.
  ```
a =>  
b =>  
c =>
should equal 'abc'
```

```
a => b  
b =>  
c => a
should equal `bac`
```
```
a => c  
b => a  
c => 
should equal `cab`
```

```
a => b  
b => c  
c => a
should throw an error (jobs cannot have a circular dependency)
```
```
a =>  
b =>  
c => c
should throw an error (jobs cannot have dependency on themselves)
```
