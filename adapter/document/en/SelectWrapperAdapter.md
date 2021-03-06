## SelectWrapperAdapter.

> It's for the user who wants to manually choose some things.

We support three different choice-mode.

* Single-choice
* Multi-choice
* Range-choice

#### Example classes:

* [SelectSampleActivity](https://raw.githubusercontent.com/momodae/RecyclerViewLibrary2/master/app/src/main/java/com/cz/widget/recyclerview/sample/adapter/SelectSampleActivity.kt)

#### Image
![select_adapter](https://github.com/momodae/LibraryResources/blob/master/RecyclerViewLibrary/image/adapter/select_adapter.gif?raw=true)

### Usage

```
val adapter = SimpleSelectAdapter(this, list)
val wrapperAdapter= SelectWrapperAdapter(adapter)
recyclerView.layoutManager = LinearLayoutManager(this)
recyclerView.adapter=wrapperAdapter

//The different select mode.
wrapperAdapter.setSelectMode(SelectWrapperAdapter.CLICK)
wrapperAdapter.setSelectMode(SelectWrapperAdapter.SINGLE_SELECT)
wrapperAdapter.setSelectMode(SelectWrapperAdapter.MULTI_SELECT)
wrapperAdapter.setSelectMode(SelectWrapperAdapter.RECTANGLE_SELECT)
```


### Functions.

#### For single-choice

```
//This listener will receive all the single-choice events.
wrapperAdapter.setOnSingleSelectListener { v, newPosition, oldPosition ->
    //The selected position has changed.
}

//Choice a position programmatically
wrapperAdapter.setSingleSelectPosition(0)
```


#### For a multi-choice

```
//The maximum number we could have.
//wrapperAdapter.setSelectMaxCount(5)
//Handle the select events.
wrapperAdapter.setOnMultiSelectListener { v, selectPositions, lastSelectCount, maxCount ->
//The selected position has changed.
}
//Choice a list programmatically
wrapperAdapter.setMultiSelectItems(listOf(1,2,3))
```

#### For a range-choice

```
wrapperAdapter.setOnRectangleSelectListener { startPosition, endPosition ->
    //Just do something.
}
```

By extend from HeaderWrapperAdapter. You could add extra layouts.

```
wrapperAdapter.addHeaderView(headerView)
wrapperAdapter.addFooterView(footerView)
```