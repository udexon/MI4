# MI4 Tutorial T002: Phos Textarea Box

## A. Introduction

In this tutorial, we demonstrate the following using Phoscript:

1. Create a Textarea box to enter Phos commands.

2. Execute Phos commands in Phos Textarea box.


## B. Instructions

1. Navigate to the following web page:

- https://handsontable.com/examples?manual-resize&manual-move&conditional-formatting&context-menu&filters&dropdown-menu&headers

<img src="https://github.com/udexon/MI4/blob/master/img/handsontable_demo.png" width=600>

2. Press F12 to bring out the browser console:

<img src="https://github.com/udexon/MI4/blob/master/img/function_Phos.png" width=450>

3. Copy paste the code from the following file into the browser console as shown above.

- https://github.com/udexon/MI4/blob/master/src/libphos.js

4. Copy paste the following code into the browser console:

```js
m = new Phos()
S = m.S
F = m.F
FGL = m.FGL
F("box:")
```

<img src="https://github.com/udexon/MI4/blob/master/img/T002_box_cmd.png" width=450>

This creates a textarea box for entering commands or chat messages as shown below:

<img src="https://github.com/udexon/MI4/blob/master/img/T002_Phos_box.png" width=600>

ΦΩΣ is the original Greek word for Phos, meaning "light".

5. Copy paste the following code into the Phos textarea box:

```js
4 5 +
```

<img src="https://github.com/udexon/MI4/blob/master/img/T002_4_5_add.png" width=600>

Then press 'ΦΩΣ'.

<img src="https://github.com/udexon/MI4/blob/master/img/T002_Phos_box.png" width=600>

An `alert()` window will pop up, showing the result `9` as the top of stack item (last item in the list).

- Explanation

a. `m = new Phos()` creates a JavaScript object `m` from the `function Phos()` code that we just entered via the browser console.

b. `m.F()` calls a series of `Phos()` functions:

`gex:` this Phos _word_ (Forth / Phos term for function name) maps to the following JavaScript code, and extracts the table concerned using XPATH:
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

The extracted row is again pushed on to the stack `m.S`. The result can be viewed as `m.S[0].innerHTML` as shown above.


5. Next we extract cells with indices 3, 4, 5 from the row above.

Copy paste the following code into the browser console:

```
m.F('/html/body/section/div/div[2]/div[1]/div[1]/div[1]/div/div/div/table gex: 4 row: cells: oe: 3 6 slice:')
```

As you can see, the front portion of the code is the same as previous step. 

The additional comands are:
- `cells:` convert HTML row into `cells` object
- `oe:` calls `Object.entities()` to convert `cells` object into an array
- `3 6 slice:` extracts cells with indices 3,4,5

The results can be viewed by inspecting the variable `m.S` as shown in below:

<img src="https://github.com/udexon/MI4/blob/master/img/mi4_row_cells.png" width=450>

The JavaScript code concerned is shown below:
```js
    function f_oe() {
        S.push(Object.entries(S.pop()));
    }
    function f_cells() {
        S.push(S.pop().cells);
    }
    function f_slice() {
        var j = S.pop();
        var i = S.pop();
        var A = S.pop()
        S.push(A.slice(i, j));
    }
```
