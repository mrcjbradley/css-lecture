# Big O(h boy!) and You

### learn it &bull; live it &bull; love it

<!-- .slide: data-transition="zoom" -->


---

# What is big o?
* Big-O notation is a relative representation of the complexity of an algorithm. ([from stackoverflow](https://stackoverflow.com/questions/487258/what-is-a-plain-english-explanation-of-big-o-notation)) 
<!-- .element: class="fragment fade-up" --> 

* Big O notation is the language we use for talking about ***how long*** [and ***how much space***] an algorithm takes to run. It's how we compare the efficiency of different approaches to a problem. ([from interviewcake.com](https://www.interviewcake.com/article/ruby/big-o-notation-time-and-space-complexity))
<!-- .element: class="fragment fade-up" --> 

Note: 
question for class: what is big O? 


---

## Who will win?

![](data:image/jpeg;base64,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)<!-- .element: class="fragment fade-in" --> 

#### VS.


<img src="https://media.giphy.com/media/FOOwKn00mZyjVjX7pk/giphy.gif" width="25%"><!-- .element: class="fragment fade-in" --> 

---

 ![](lib/images/pigeon-vs-broadband.png)


---

* Constant
* Logarithmic
* Square Root
* Linear
* Log-Linear
* Quadratic
* Polynomial
* Exponential
* Factorial

---

![](https://s3.amazonaws.com/lectures-ckane/Screen+Shot+2018-10-22+at+8.10.45+PM.png)

---

It's all a matter of counting!

---

```ruby
def example1(n)
  n = 3n + 2
  n += 40n
  n**5
end
```

---

O(1)

---

```ruby
def example2(n)
  n.times { |i| p i }
end
```

---

O(n)

---

```ruby
def example3(n)
  t = 0
  n.times do
    n.times do  
      t += 1
    end
  end
  p t
end
```

---

O(n^2)

---

```ruby
def example4(n)
  t = 0
  (1..n).each do |i|
    i.times do  
      t += 1
    end
  end
  p t
end
```

---

O(n^2) 

---

Typical pattern. The number of things to do each time is not always n, so it is less than `n^2` in total, right? Sort of...

If you count it all out, we are adding up from `1..n`. This results in `n(n+1)/2`, which is still `n^2`.

---

```ruby
def example5(n)
  while n > 0
    n /= 2
  end
end
```

---

O(logn)

---

Typical of logarithmic time complexity. Reducing the data set by a factor each time. Remember MergeSort?

---

```ruby
def example5_5(arr1, arr2)
    arr1.each do |a1|
     arr2.each do |a2|
      p a1, a2
     end
    end
end
```

---

    O(n * m)

---

explanation goes here

---


```ruby
def example6(n)
  return 1 if n == 0
  example6(n-1)
end
```

---

O(n) Time and Space

---

```ruby
def example7(n)
  return 1 if n.even? || n < 0
  example7(n-2)
end
```

---

O(n)

note:
Best Case: Constant,

Worst Case: Linear

---

```ruby
def example8(n)
  return 1 if n == 0
  example8(n-1) * example8(n-1)
end
```

note: 
ask the audience 

---

O(2^n)

---

This is a branching recursive tree. Since each call results in two more calls, we multiply by two for each level of the tree.

If we input 5, the total number of calls is `2^(n+1) - 1` => `O(2^n)`

---

```ruby
def example9(n)
  return 1 if n == 0
  n.times { p n } if n.odd?
  example9(n-1) * example9(n-1)
end
```
note: turn and talk

---

O(n * 2^n)

---

- Example 9 is a branching tree which gives us a lower bound of `O(2^n)`
- However, there is extra stuff going on. Sometimes we do extra stuff that depends on `n`.
- If there were `n` things going on for each recursive call, then our time complexity would be `O(n*2^n)`. This is the upper bound
- Counting up exactly how much stuff is going on, given that only odd numbers result in extra work, is outside the scope of what you should expect to be able to do in an interview. It is a fun math challenge to try though!

---

```ruby
def example10(n)
  t = 0
  n.times do
    n.times do  
      t.to_s.split('').each { |el| p el }
      t += 1
    end
  end
  p t
end
```

---

O(n^2 * logn)

---

The key question here is: What is contained in the double loop?

For each iteration we do extra work equal to the number of digits of the current number. Do you see that?

The number of digits is roughly equal to `log10(n)`

---

If we count everything up we get

```
Sum from i=1 to n^2 of:
log10(i)
```

This should give us a Time Complexity of around `O(n^2 * log10(n^2))`; once we normalize the base of the logarithm and discard the constant factor this is `O(n^2 * logn)`.

For `n=100` the total number of prints is 38,890;

---

```ruby
def example11(n)
  p n
  n.times do
    example11(n-1)
  end
end
```

---

Factorial: `n=5` results in 4 more calls, each of which results in 3 more calls...etc.

---


# General Approach 
* Identify n (or necessary variables)
* Walk through algorithm tracking step/space in terms of n — add adjacent steps; multiply blocks within blocks; etc. 
* Consider recursion 
* Eliminate all but highest order term
* Eliminate coefficients 

---