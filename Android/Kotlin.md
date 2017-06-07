# Best practices for using Kotlin at NRK

## Named parameters

Use named parameters when input to a function can be ambiguous. Use named parameters and default parameter values over a Java-style Builder pattern. 

## val getters

Do not use custom getters for vals. 

Don't:
```
class Person(val birthDay: DateTime) {  
  val age: Int
    get() = yearsBetween(birthDay, DateTime.now())
}
```

Use a function instead: 

``` 
class Person(val birthDay: DateTime) {  
  fun age(): Int = yearsBetween(birthDay, DateTime.now())
}
```