# yascm

Yet Another Scheme Interpreter.

## Building

```
make
```

## Example

- Recursion

```
$ ./yascm
welcome
> (define (sum x)
  (if (= 0 x) 0 (+ x (sum (+ x -1)))))
; ok
> (sum 10000)
50005000
>
```

- Closure

```
$ ./yascm
welcome
> (define (add a)
 (lambda (b) (+ a b)))
; ok
> (define add3 (add 3))
; ok
> (add3 4)
7
> (define my-counter
    ((lambda (count)
       (lambda ()
         (set! count (+ count 1))
         count))
     0)
  )
; ok
> (my-counter)
1
> (my-counter)
2
> (my-counter)
3
>
```

- [man or boy test](https://en.wikipedia.org/?title=Man_or_boy_test):

```
$ ./yascm
welcome
> (define (A k x1 x2 x3 x4 x5)
    (define (B)
      (set! k (+ k -1))
      (A k B x1 x2 x3 x4))
    (if (> 1 k)
        (+ (x4) (x5))
        (B)))
; ok
> (A 10 (lambda () 1) (lambda () -1) (lambda () -1) (lambda () 1) (lambda () 0))
-67
> 
```

## Author

hmgle <dustgle@gmail.com>

## LICENSE

GPL Version 3, see the COPYING file included in the source distribution.
