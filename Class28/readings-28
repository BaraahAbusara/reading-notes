# Class-28 : RecyclerView
***

In this file I will be summarizing what I have learnt in class-28 reading notes which included the following resources : 
- [RecyclerView for displaying lists of data](https://developer.android.com/guide/topics/ui/layout/recyclerview#java).

## Create dynamic lists with RecyclerView   
***
!["RecyclerView Example"](https://tutorials.eu/wp-content/uploads/2020/07/RecycleViewApp.png)
RecyclerView recycles those individual elements. When an item scrolls off the screen, RecyclerView doesn't destroy its view. Instead, RecyclerView reuses the view for new items that have scrolled onscreen. This reuse vastly improves performance, improving your app's responsiveness and reducing power consumption.RecyclerView recycles those individual elements. When an item scrolls off the screen, RecyclerView doesn't destroy its view. Instead, RecyclerView reuses the view for new items that have scrolled onscreen. This reuse vastly improves performance, improving your app's responsiveness and reducing power consumption.
### Key classes
Several different classes work together to build your dynamic list:
- `RecyclerView`.
- define the view holder by extending `RecyclerView.ViewHolder`.
-  define the adapter by extending `RecyclerView.Adapter`.
-  define the  layout manager that is based on the library's `LayoutManager` abstract class.
You can see how all the pieces fit together in the [RecyclerView sample app (Java)](https://github.com/android/views-widgets-samples/tree/main/RecyclerView/).
### Steps for implementing your RecyclerView
1. Decide the style (layout).
2. Design elements behaviour, extend the `ViewHolder` class.
3. Define the `Adapter` that associates your data with the `ViewHolder` views.
### Plan your layout
The RecyclerView library provides three layout managers, which handle the most common layout situations:
1. `LinearLayoutManager` arranges the items in a one-dimensional list.
2. `GridLayoutManager` arranges all items in a two-dimensional grid.
3. `StaggeredGridLayoutManager`.

### Implementing your adapter and view holder
When you define your adapter, you need to override three key methods:
1. onCreateViewHolder() :
```
// Create new views (invoked by the layout manager)
    @Override
    public ViewHolder onCreateViewHolder(ViewGroup viewGroup, int viewType) {
        // Create a new view, which defines the UI of the list item
        View view = LayoutInflater.from(viewGroup.getContext())
                .inflate(R.layout.text_row_item, viewGroup, false);

        return new ViewHolder(view);
    }
```

2. onBindViewHolder()
```
   // Replace the contents of a view (invoked by the layout manager)
    @Override
    public void onBindViewHolder(ViewHolder viewHolder, final int position) {

        // Get element from your dataset at this position and replace the
        // contents of the view with that element
        viewHolder.getTextView().setText(localDataSet[position]);
    }
```
3. getItemCount() 
```
    // Return the size of your dataset (invoked by the layout manager)
    @Override
    public int getItemCount() {
        return localDataSet.length;
    }
```
### Next steps
You can [customize your implementation](https://developer.android.com/guide/topics/ui/layout/recyclerview-custom).