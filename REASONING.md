# Reasoning for the Predictions Table

Write one entry under every heading below, then commit this file together with
`predictions.tsv`, before you run a case or open `tests/expected.tsv`.

Each entry names the rule that produces the four predicted fields for that
case. One to three sentences is enough. The grader checks structure only. It
does not judge quality, and it sets no word minimum.

After you run the cases, add a short correction under each case you predicted
wrongly. Say what you predicted, what CLISP printed, and which rule you
misread. Those entries belong in the correction commits.

## P01
(+ 1 (* 2 3)) evaluates (* 2 3) first, giving 6, then adds 1 to get 7. The result is an integer, so its length is none.

## P02
''(+ 1 2) quotes the list instead of evaluating it. The result is (+ 1 2), with length 3.

## P03
'nil returns NIL, representing the empty list. Its length is 0.

## P04
't returns the symbol T, representing true. Symbols have no sequence length.

## P05
symbolp checks whether its argument is a symbol. NIL is a symbol, so the result is T.

## P06
(car '()) gets the first element of an empty list. The result is NIL, with length 0.

## P07
cons adds 1 to the beginning of (2 3). The result is (1 2 3), with length 3.

## P08
(null '()) returns T, so the if expression returns EMPTY. The result is a symbol.

## P09
and stops evaluating when it encounters NIL. Therefore, the result is NIL, with length 0.

## P10
progn executes each form sequentially. The dynamic binding changes *ps3-rate* to 10, so (ps3-scale 3) returns 30.

## P11
defun defines the function PS3-TWICE. It returns the function name as a symbol, not the function's calculated result.

## P12
labels defines a recursive function that counts down from 3. The result is (3 2 1), with length 3.

## P13
mapcar applies length to each nested list. Their lengths produce (2 0 1), with length 3.

## P14
mapcar applies the lambda function to square each number. The result is (1 4 9), with length 3.

## P15
lambda creates an anonymous function that doubles its argument. It returns a function object, so its length is none.

## P16
The function f captures the lexical value of factor, which is 2. Therefore, (funcall f 3) returns 6.

## Corrections:
P03, P04, P05, P06, P08, P09, P11 - Should be in lowercase. The grader writes symbols in
lower case.

P02 - Value should be separated by commas. The head is quote, so operator shopuld be special-operator
P15 - The grader writes any function object as `#<function>`. I also wrote the wrong
operator: `lambda` is a macro, so the cell reads `macro`.