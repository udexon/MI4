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

<img src="https://github.com/udexon/MI4/blob/master/img/T002_alert.png" width=600>

An `alert()` window will pop up, showing the result `9` as the top of stack item (last item in the list).

## C. Explanations

1. In line 44 of `libphos.js`:

- https://github.com/udexon/MI4/blob/master/src/libphos.js

```js
S[3].onclick=function(){ F(S[1].value); alert( S );} 
```

`S[1]` is defined by line 20 of `libphos.js`:

```js
S.push(document.createElement('textarea'))
```

Hence `S[1].value` returns whatever contents in `textarea`.

The contents are then fed to `F()`, which is defined at line 241 of `libphos.js`.

2. The commands entered are `4 5 +`.

`4` and `5` are data (non-function) _words_ (Phoscript or Forth terminology) or tokens. As such, they will be _pushed on to the stack_ `S`.

`+` is a function word (token). It is mapped to code starting at line 457 in `libphos.js`. It pops the top two items of the stack (`4` and `5`), adds them (result is `9`) and pushes the result on to the stack.

3. `alert( S )` in line 44 of `libphos.js` then pops up the `alert` window.

The result `9` is displayed at the end of the output, as the top item of the stack.

