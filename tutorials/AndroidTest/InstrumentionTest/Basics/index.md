# Intrumention Test

Tests that require android context and runs on Android device. We use [Espresso](https://developer.android.com/training/testing/espresso/setup) to test it.

## Context

We have 2 options to get context.

1. `getContext` method is used to get context of Test class.
```java
Context context = InstrumentationRegistry.getInstrumentation().getContext();
```
2. `getTargetContext` method is used to get context of Target Appp.
```java
Context context = InstrumentationRegistry.getInstrumentation().getTargetContext();
```

We can use [Junit](/tutorials/AndroidTest/Junit/basic/basic.md) Tests at first 