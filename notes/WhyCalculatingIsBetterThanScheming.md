
# Why calculating is better Than Scheming By P. Wadler

- Haskell definition of sum:
```haskell
sum [] = 0
sum (x:xs) = x + sum xs
```

- Lisp definition of sum:
```scheme
(define (sum xs) 
  (if (null? xs)
  0
  (+ (car xs) (sum (cdr xs)))))
```

the Lisp program obscures the symmetry between the two cases. The nil case is tested for explicitly, and the cons case is assumed otherwise. 
The symmetry can be recovered though by writing:
```scheme
(define (sum xs)
  (cond ((nu1l? xs) 0)
        ((pair? xs) ( + (car xs) (surn4cdr xs))))))
```

- In Miranda one can prove by structural induction that a definition of append is associative 
- the lesson from the section comparing miranda style proof and lisp style proof for append if wanted to do them is that pattern-matching notation 
  greatly simplifies the mechanics of the proof, and just in general any algebraic manipulation is easier in an infix notation such as used in Miranda.
 
- Some people may wish to dismiss these issues as being just syntax. But it is also true that a good choice of notation can greatly aid learning and thought, 
  and a poor choice can hinder it. In particular, pattern-matching seems to aid thought about case analysis, making it easier to construct programs and to prove 
  their properties by structural induction. 



