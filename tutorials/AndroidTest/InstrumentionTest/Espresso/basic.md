# Espresso Tests

### Testing is done from following methods

* `onView()`—A `ViewInteraction` for a given view. Takes the `hamcrest
  ViewMatchers` instance(s) as a parameter. You can pass one or more
  of these to the `onView()` method to **locate a view**, based on view
  properties, within the current view hierarchy. We use `Espresso.onData` for recyclerview.
* `onData()`—A `DataInteraction` for a data object (e.g., a ListView).
  Takes as a parameter a `hamcrest matcher` that matches the data
  object represented by the **single item** in the list.
* `pressBack()`—A press on the back button. **Throws PerformException**
  if the currently displayed activity is a root activity, since pressing the
  back button would result in the application closing.
* `closeSoftKeyboard()`—Closes the **soft keyboard** if it’s open.
* `openContextualActionModeOverflowMenu()`—Opens the **overflow
  menu** displayed in the contextual options of an `ActionMode`.
* `openActionBarOverflowOrOptionsMenu()`—Opens the **overflow
  menu** displayed within an ActionBar.
  
### Espresso ViewMatchers

View matchers form a collection of hamcrest Java matchers that match views

* `isAssignableFrom()` —Matches a view based on an instance or
subclass of the provided class. Normally used in combination with
other ViewMatchers. Commonly used.
* `withClassName()`⎯Returns a matcher that matches views with class
name matching the given matcher.
* `isDisplayed()`⎯Returns a matcher that matches views that are
currently displayed on the screen to the user. Commonly used.

>**Note** `isDisplayed()` will select views that are partially displayed (e.g.,
 the full height/width of the view is greater than the height/width of the
 visible rectangle). If you want to ensure the entire rectangle is displayed, use
 isCompletelyDisplayed().
>
* isCompletelyDisplayed()⎯Returns a matcher that only accepts
a view whose height and width fit perfectly within the currently
displayed region of this view.
>**Note** There exist views (such as ScrollViews) whose height and width
 are larger than the physical device screen by design. Such views will never be
 completely displayed.

* `isDisplayingAtLeast()`⎯Returns a matcher that accepts a view so
long as a given percentage of that view’s area is not obscured by any
parent view and is thus visible to the user.
* `isEnabled()`⎯Returns a matcher that matches view(s) that are
enabled. Commonly used.
* `isFocusable()`⎯Returns a matcher that matches view(s) that are
focusable.
* `hasFocus()`⎯Returns a matcher that matches view(s) that currently
have focus.
* `isSelected()`⎯Returns a matcher that matches view(s) that are
selected.
* `hasSibling()`⎯Returns a matcher that matches view(s) based on
their siblings. This may be particularly useful when a view cannot be
uniquely selected on properties such as text or view ID. For example,
a call button is repeated several times in a contact layout and the only
way to differentiate the call button view is by what appears next to it
(e.g., the unique name of the contact).
* `withContentDescription()`⎯Returns a matcher that matches view(s)
based on the content description property value. Commonly used.
* `withId()`⎯Returns a matcher that matches view(s) based on content
description’s id. Commonly used.

>**Note** Android resource IDs are not guaranteed to be unique. You may have to pair
 this matcher with another one to guarantee a unique view selection

* `withResourceName()`⎯Returns a matcher that matches view(s) based
on resource ID names, (for instance, channel_avatar).
* `withTagKey()`⎯Returns a matcher that matches view(s) based on tag
keys.
* `withTagValue()`⎯Returns a matcher that matches view(s) based on
tag property values.
withText()⎯Returns a matcher that matches view(s) based on its text
property value.
* `withHint()`⎯Returns a matcher that matches view(s) based on its hint
property value.
* `isChecked()`⎯Returns a matcher that accepts it only if the view is a
CompoundButton (or a subtype of ) and is in checked state. Commonly
used.
* `isNotChecked()`⎯Returns a matcher that accepts it only if the view
is a CompoundButton (or subtype of ) and is not in the checked state.
Commonly used.
* `hasContentDescription()`⎯Returns a matcher that matches view(s)
with any content description.
* `hasDescendant()`⎯Returns a matcher that matches view(s) based on
the presence of a descendant in its view hierarchy.
* `isClickable()`⎯Returns a matcher that matches view(s) that are
clickable.
* `isDescendantOfA()`⎯Returns a matcher that matches view(s) based
on the given ancestor type.
* `withEffectiveVisibility()`⎯Returns a matcher that matches
view(s) that have “effective” visibility set to the given value.
* `withAlpha()`⎯Matches view(s) with the specified alpha value. Alpha
is a view property value from 0 to 1, where 0 means the view is
completely transparent and 1 means the view is completely opaque.
withParent()⎯A matcher that accepts a view only if the view’s parent
is accepted by the provided matcher.
* `withChild()`⎯Matches view(s) whose child is accepted by the
provided matcher.
* `hasChildCount()`⎯Matches a ViewGroup (e.g., a ListView) if it has
exactly the specified number of children.
* `hasMinimumChildCount()`⎯Matches a ViewGroup (e.g., a ListView) if it
has at least the specified number of children.
isRoot()⎯Returns a matcher that matches the root view.
* `hasImeAction()`⎯Returns a matcher that matches views that support
input methods.
* `hasLinks()`⎯Returns a matcher that matches TextView(s) that have links.
* `withSpinnerText()`⎯Returns a matcher that matches a descendant of
a spinner that is displaying the string of the selected item associated
with the given resource ID.
* `isJavascriptEnabled()`⎯Returns a matcher that matches web
view(s) if they are evaluating JavaScript.
* `hasErrorText()`⎯Returns a matcher that matches EditText based on
the edit text error string value.
* `withInputType()`⎯Returns a matcher that matches android.text.
InputType.
* `withParentIndex()`⎯Returns a matcher that matches the child index
inside the ViewParent.

**Example `withText()`**
This example means we are searching for view that has text "item 1" in it. 
```java
onView(withText("item 1"));
```

**Example `withId()`**
Locate menu filter using Resource ID
```java
onView(withId(R.id.menu_filter));
```

### ViewMatchers grouping in following sections

* User properties
* UI properties
* Object matchers
* Hierarchy
* Input
* Class
* Root matchers

![ViewMatchers](./images/Viewmatchers.jpg)

*  `ActivityTestRule` We pass false for automatic launch because this activity will be launched by intent. 

```java
    @Rule
    public ActivityTestRule<RecipeActivity> activityRule =
        new ActivityTestRule<>(RecipeActivity.class,
        true, // initial Touch mode
        false); // Automatic launch launchActivity
```

* Launching Activity Without Intent ID. 

```java
    @Test
    public void recipeNotFound(){
        activityRule.launchActivity(null);
        onView(withId(R.id.description)).check(matches(withText(R.string.recipe_not_found)));
    }
```