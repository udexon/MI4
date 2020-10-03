# MI4 Tutorial T001: Extract Row and Cells from HTML Table

## A. Introduction

In this tutorial, we demonstrate the following using Phoscript:

1. Extract one row from a HTML table.

2. Extract a range of cells from a row.


## B. Instructions

1. Navigate to the following web page:

- https://handsontable.com/examples?manual-resize&manual-move&conditional-formatting&context-menu&filters&dropdown-menu&headers

<img src="https://github.com/udexon/MI4/blob/master/img/handsontable_demo.png" width=600>

2. Press F12 to bring out the browser console:

<img src="https://github.com/udexon/MI4/blob/master/img/function_Phos.png" width=450>

3. Copy paste the code from the following file into the browser console as shown above.

- https://github.com/udexon/MI4/blob/master/src/libphos.js

4. Copy paste the following code into the browser console:

```
m = new Phos()

m.F('/html/body/section/div/div[2]/div[1]/div[1]/div[1]/div/div/div/table 
gex: 4 row:')
```

<img src="https://github.com/udexon/MI4/blob/master/img/mi4_row.png" width=450>

5. Copy paste the following code into the browser console:

```
m.F('/html/body/section/div/div[2]/div[1]/div[1]/div[1]/div/div/div/table 
gex: 4 row: cells: oe: 3 6 slice:')
```

<img src="https://github.com/udexon/MI4/blob/master/img/mi4_row_cells.png" width=450>
