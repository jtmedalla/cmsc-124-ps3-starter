# Environments and the Toy Evaluator

## Analysis

I traced the scope-discrimination form through our eval-expr: a let binds x to 2, a second let binds f to (lambda (y) (+ x y)), a third let rebinds x to 100, then (f 1) runs. 

## point to the line that captures the defining environment
Capture happens in the branch of eval-expr: (make-closure (cadr expr) (caddr expr) env). Because eval-let evaluates the initializer for f before binding f env holds only ((x. 2)) At that moment. make-closure stores it unchanged as (:closure (y) (+ x y) ((x. 2))). The later binding of x to 100 builds a list in front of it and the saved list never sees it.


## say what would change if application joined the arguments to the caller's environment instead
apply-closure evaluates the body in (extend-env params args env) where env is the one saved inside the closure. (F1) returns 3. If it extended the callers environment instead that environment would be ((x. 100) (F. Closure) (x. 2)). The first match, for x would be 100. The result would be 101. The language would then be dynamically scoped. A free variable would resolve by whoever calls the function. A free variable would resolve by whoever calls the function. The closure’s saved env would go unused.


## explain why the host CLISP needs `funcall` where the toy language doesn't.
There are two namespaces that are present in CLISP. The function namespace, where function names are stored, and the variable namespace, where variable names are stored. CLISP always checks the first item in the function namespace which is why it is able to evaluate lists with operators or functions as the first element. This allows the language to name variables as functions without conflict between the two. However, when the function is contained in a variable, then funcall is needed to find a function call within the variable namespace instead since keywords within the function namespace takes precedence. Since the toy language stores everything in a single global namespace, then this conflict does not occur. 

