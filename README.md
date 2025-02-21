
```markdown
# Android SearchView in Java

## 1. Add SearchView in Toolbar

Update your `menu.xml` file:

```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">
    <item
        android:id="@+id/action_search"
        android:title="Search"
        android:icon="@android:drawable/ic_menu_search"
        app:showAsAction="ifRoom|collapseActionView"
        app:actionViewClass="androidx.appcompat.widget.SearchView"/>
</menu>
```

## 2. Handle SearchView in Activity

In your `MainActivity.java`:

```java
@Override
public boolean onCreateOptionsMenu(Menu menu) {
    getMenuInflater().inflate(R.menu.menu, menu);

    MenuItem searchItem = menu.findItem(R.id.action_search);
    SearchView searchView = (SearchView) searchItem.getActionView();

    searchView.setOnQueryTextListener(new SearchView.OnQueryTextListener() {
        @Override
        public boolean onQueryTextSubmit(String query) {
            // Handle search query submission
            return false;
        }

        @Override
        public boolean onQueryTextChange(String newText) {
            // Handle text change
            return false;
        }
    });

    return true;
}
```

## 3. Notes

- Ensure you are using `androidx.appcompat.widget.SearchView` for compatibility.
- The `onQueryTextChange` method is useful for filtering lists dynamically.

```
