# Basic Syntax

## Assert

* `AssertNotEquals` is used to check is the Object is of same type as on right side. 

```java
 assertNotEquals(recipe, Recipe.class);
```

* `AssertEquals` is used to check the value of object with the value that we expect it to have. 

```java
 assertEquals("water", recipe.id);
```
* `assertNotNull` is used to check not Null;
```
 RecipeStore store = new RecipeStore(context, null);
 assertNotNull(store);
```


