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
The quote symbol reads the contents of the parenthesis as a list and is not evaluated. Even if the starting symbol is a `+` operator, the value is returned as a list.

Correction: the first `'` is not counted in the evaluation. Thus the entire function is evaluated resulting into 7. It has a kind of integer and a function as its operator.

## P02
''(+ 1 2) quotes the list instead of evaluating it. The result is (+ 1 2), with length 3.

## P03
`nil` is a special case in Lisp since it can mean multiple things. It can represent an empty list, and an empty value. Additionally, it is also used to represent `false` in the language. It is for this reason that the length of a nil value is 0 and not none. 

## P04
't returns the symbol T, representing true. Symbols have no sequence length.

## P05
`symbolp` checks the next element in the list if it is a symbol and returns `T` or `nil` representing `true` and `false` respectively. In this case, `nil` is considered as a self-evaluating symbol and would thus pass `symbolp`'s check.

Correction: Despite LISP documentation changing every non-string into uppercase, the problem set requires a different syntax. Thus `T` is instead supposed to be `t`. Additionally, `symbolp` despite being able to be considered as a branching type of operator, is considered as a function rather than a special-operator.

## P06
(car '()) gets the first element of an empty list. The result is NIL, with length 0.

## P07
The `cons` function takes the value of the first argument, appends it to the start of the second argument and returns the longer list.

## P08
(null '()) returns T, so the if expression returns EMPTY. The result is a symbol.

## P09
`and` is the logical and of the LISP language. It takes any number of arguments and checks its truth value. If any argument is read as `nil` then the function returns `nil` as its false value.

Correction: and is a special operator since and is invoked before all the values are finished being evaluated to allow it to perform short-circuiting. 

## P10
progn executes each form sequentially. The dynamic binding changes *ps3-rate* to 10, so (ps3-scale 3) returns 30.

## P11
`defun` it is a macro that defines a function. Additionally, it does not have a return value unless it is invoked.

Correction: the `defun` macro returns the name of the function.

## P12
labels defines a recursive function that counts down from 3. The result is (3 2 1), with length 3.

## P13
`mapcar` is used when the program wants to run the function for all the elements of a list. In the example, it runs the function `length` for all elements of `mapcar`'s second element list.

## P14
mapcar applies the lambda function to square each number. The result is (1 4 9), with length 3.

## P15
`lambda` does not have a return value since it defines a one-time function. 

Correction: `lambda` returns a function object when it is declared.

## P16
The function f captures the lexical value of factor, which is 2. Therefore, (funcall f 3) returns 6.

## Corrections:
P03, P04, P05, P06, P08, P09, P11 - Should be in lowercase. The grader writes symbols in
lower case.

P02 - Value should be separated by commas. The head is quote, so operator shopuld be special-operator
P15 - The grader writes any function object as `#<function>`. I also wrote the wrong
operator: `lambda` is a macro, so the cell reads `macro`.