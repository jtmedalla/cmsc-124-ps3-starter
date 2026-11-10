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
Replace this line with the rule behind this case's four fields.

## P09
Replace this line with the rule behind this case's four fields.

## P10
Replace this line with the rule behind this case's four fields.

## P11
Replace this line with the rule behind this case's four fields.

## P12
Replace this line with the rule behind this case's four fields.

## P13
Replace this line with the rule behind this case's four fields.

## P14
Replace this line with the rule behind this case's four fields.

## P15
Replace this line with the rule behind this case's four fields.

## P16
Replace this line with the rule behind this case's four fields.
