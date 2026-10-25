# EGCL support

The `egcl` branch preserves TEST-TYPE's two return values by recognizing terminal TYPEP forms outside MAPHASH callbacks. This avoids EGCL's current loss of secondary values across a callback's nonlocal RETURN-FROM (Evergreen bliss-4fwnc).

EGCL does not reliably signal invalid type specifiers. ALL-COMPOUND-TYPES therefore retains the requested type without probing successively longer argument lists. Reverse inference still derives predicate equivalents, but does not enumerate abbreviated compound types. This conservative restriction avoids unbounded invalid-type inference (bliss-s1uu1).

`egcl-tests.lisp` checks direct and predicate inference including the success value, plus reverse integer inference. Run with dependencies registered in ASDF: `egcl --no-init --load egcl-tests.lisp`. Full upstream tests have not been run.
