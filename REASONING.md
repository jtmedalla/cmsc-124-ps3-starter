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
According to the required reading, `quote` is a special operator that reads the list and returns its contents as is, even if the head of the list is a function or special operator. Therefore, the result of P02 is a list containg +, 1, and 2.

## P03
`nil` is a special case in Lisp since it can mean multiple things. It can represent an empty list, and an empty value. Additionally, it is also used to represent `false` in the language. It is for this reason that the length of a nil value is 0 and not none. 

## P04
A lone symbol `t` is interpreted by LISP as a symbol. Since a symbol is atomic, it has neither a length or an operator. The value that LISP would return is just the symbol itself thus `t`.

## P05
`symbolp` checks the next element in the list if it is a symbol and returns `T` or `nil` representing `true` and `false` respectively. In this case, `nil` is considered as a self-evaluating symbol and would thus pass `symbolp`'s check.

Correction: Despite LISP documentation changing every non-string into uppercase, the problem set requires a different syntax. Thus `T` is instead supposed to be `t`. Additionally, `symbolp` despite being able to be considered as a branching type of operator, is considered as a function rather than a special-operator.

## P06
`car` function takes the first element of the list in its atomic form. In the case of an empty list, its first value would be `nil`.

## P07
The `cons` function takes the value of the first argument, appends it to the start of the second argument and returns the longer list.

## P08
`null` is used to test for an empty list. It returns `T` if yes and `nil` if no. Then the `if` special-operator checks for the truth value of its first argument, returning its second argument if `true` and its third argument if `false`.

## P09
`and` is the logical and of the LISP language. It takes any number of arguments and checks its truth value. If any argument is read as `nil` then the function returns `nil` as its false value.

Correction: and is a special operator since and is invoked before all the values are finished being evaluated to allow it to perform short-circuiting. 

## P10
`progn` is a special operator used to evaluate 0 or more forms. It can be used to group similar sections but only returns *all* the values in the last form. `defvar` is used to define a global variables. \*ps3-rate\* is a global variable in the context of the small subprogram. `defun` is used to define functions in LISP. 
LISP has shadowing rules, in the case of the small subprogram, the variable inside the let binds tighter than the global variable. This causes the value used by the function to change into the one defined by the let.

## P11
`defun` it is a macro that defines a function. Additionally, it does not have a return value unless it is invoked.

Correction: the `defun` macro returns the name of the function.

## P12
`labels` is used to group defining functions. One special feature of the special-operator is it allows recursion. The example creates a list that counts down to 0.

## P13
`mapcar` is used when the program wants to run the function for all the elements of a list. In the example, it runs the function `length` for all elements of `mapcar`'s second element list.

## P14
Since `mapcar` requries that its first argument is a function, lambda can be used as a shortcut instead of defining the function separately.

## P15
`lambda` does not have a return value since it defines a one-time function. 

Correction: `lambda` returns a function object when it is declared.

## P16
When `lambda` is defined, it captures the first declaration of factor, which is `2`. By the time `f` is called through `funcall`, it calls the function with the factor being the value of `2`.
