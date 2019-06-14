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

 example of file and birds n' shit



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

Example 9 is a branching tree which gives us a lower bound of `O(2^n)`

 However, there is extra stuff going on. Sometimes we do extra stuff that depends on `n`.

 If there were `n` things going on for each recursive call, then our time complexity would be `O(n*2^n)`. This is the upper bound

 Counting up exactly how much stuff is going on, given that only odd numbers result in extra work, is outside the scope of what you should expect to be able to do in an interview. It is a fun math challenge to try though!

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