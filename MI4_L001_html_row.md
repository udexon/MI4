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

m.F('/html/body/section/div/div[2]/div[1]/div[1]/div[1]/div/div/div/table gex: 4 row:')
```

<img src="https://github.com/udexon/MI4/blob/master/img/mi4_row.png" width=450>

Entering `m.S[0].innerHTML` in the browser console shows the HTML code of the row extracted:

<img src="https://github.com/udexon/MI4/blob/master/img/mi4_row_innerHTML.png" width=450>

- Explanation

a. `m = new Phos()` creates a JavaScript object `m` from the `function Phos()` code that we just entered via the browser console.

b. `m.F()` calls a series of `Phos()` functions:

`gex:` this Phos _word_ (Forth / Phos term for function name) maps to the following JavaScript code, and extract the table concerned using XPATH:
```js
    function getElementByXpath(path) {
        return document.evaluate(path, document, null, XPathResult.FIRST_ORDERED_NODE_TYPE, null).singleNodeValue;
    }
    function fgl_gex() {
        S.push(getElementByXpath(S.pop()));
    }
```

The XPATH of the table is:
`/html/body/section/div/div[2]/div[1]/div[1]/div[1]/div/div/div/table`

It was entered BEFORE `gex:` as Phoscript uses the Reverse Polish Notation, i.e. data words are entered first, before function word is executed.

The results of `gex:` is _pushed on to the stack_, `m.S` (JavaScript array).

Next, the result on top of the stack is further processed by `4 row:` which extracts row index 4 of the HTML table, by calling the following JavaScript function:

```js
    function f_row() {
        var R = S.pop();
        var T = S.pop();
        S.push(T.rows[R]);
    }
```


5. Copy paste the following code into the browser console:

```
m.F('/html/body/section/div/div[2]/div[1]/div[1]/div[1]/div/div/div/table gex: 4 row: cells: oe: 3 6 slice:')
```

<img src="https://github.com/udexon/MI4/blob/master/img/mi4_row_cells.png" width=450>
