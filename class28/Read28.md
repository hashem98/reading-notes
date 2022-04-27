# Create dynamic lists with RecyclerView


* RecyclerView it's a library makes it easy to efficiently display large sets of data
* RecyclerView improves performance, improving your app's responsiveness and reducing power consumption.

### Key classes
* `RecyclerView` is the `ViewGroup` that contains the views corresponding to your data
* define the view holder by extending `RecyclerView.ViewHolder`
* define the adapter by extending `RecyclerView.Adapter`
* use `LayoutManager` to arranges the individual elements in your list

## Steps for implementing your RecyclerView
1. decide what the list or grid is going to look like
2. Design how each element in the list is going to look and behave
3. extend the `ViewHolder` class
4. Define the `Adapter` that associates your data with the `ViewHolder` views.

## Plan your layout

* `LinearLayoutManager `arranges the items in a one-dimensional list.

* `GridLayoutManager` arranges all items in a two-dimensional grid

* `StaggeredGridLayoutManager` 

## Implementing your adapter and view holder

to define how your data is displayed we need to implement `Adapter ` and `ViewHolder` and to define the adapter we need to override three key methods:

 `onCreateViewHolder()`,`onBindViewHolder()`,and `getItemCount()`


[Create dynamic lists with RecyclerView](https://developer.android.com/guide/topics/ui/layout/recyclerview#java)