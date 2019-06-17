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

<img src="./lib/images/pigeon_racer.jpeg" width="25%" style="margin-top:0px;"><!-- .element: class="fragment fade-in" --> 
<p style="font-size: 0.3em; margin-top:0px;">Photo Illustration by Emil Lend of/The Daily Beast</p><!-- .element: class="fragment fade-in" --> 

#### VS.

<img src="https://media.giphy.com/media/FOOwKn00mZyjVjX7pk/giphy.gif" width="25%"><!-- .element: class="fragment fade-in" --> 

Note:

- we want to send an awesome video to a coworker accross town—which will be faster 
  - (a) save the video to a stick drive, tie the stick drive to a pigeon, and send it on over
  - (b) send it over the internet

- 120Km in South Africa

---

 ![](lib/images/pigeon-vs-broadband.png)

 Note:
 - reminder: efficiency of an algorithm => we can think about this in terms of **time** and **space**
 - we spend a lot of time thinking about **time** in comparison to **space** because **space** is cheaper now 
 - Both are in terms of input

 - we can assume the pigeons fly at a constant average rate and along the same route each time
 

---

`O(1)` vs. `O(n)` where `n = filesize`

---

<ul style="float:left">
    <li class="fragment fade-in">
        Constant
    </li>
    <li class="fragment fade-in">
        Logarithmic
    </li>
    <li class="fragment fade-in">
        Square Root
    </li>
    <li class="fragment fade-in">
        Linear
    </li>
    <li class="fragment fade-in">  
        Log-Linear
    </li>
    <li class="fragment fade-in">
        Quadratic
    </li>
    <li class="fragment fade-in">
        Polynomial
    </li>
    <li class="fragment fade-in">
        Exponential
    </li>
    <li class="fragment fade-in">
        Factorial
    </li>
</ul>

<img src="https://s3.amazonaws.com/lectures-ckane/Screen+Shot+2018-10-22+at+8.10.45+PM.png" style="float:right; width:70%;"/>
<div style="clear:both;">&nbsp;</div>

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

Note: 
- in terms of time, each step is +1 unless it is in relation to our input 
- each adjacent step is addition
- does the number of steps depend on our input size?

---

O(1)

---

```ruby
def example2(n)
  n.times do |i| 
    print i 
  end
end
```
Note: 
- loops usually signify some kind of operation in terms of n

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
  print t
end
```

Note:
- loop within a loop => higher order
- two levels of loops => 2nd power 

---

O(n<sup>2</sup>)

---

```ruby
def example4(n)
  t = 0
  (1..n).each do |i|
    i.times do  
      t += 1
    end
  end
  print t
end
```

---

O(n<sup>2</sup>) 

---

- Typical pattern. 
- The number of things to do each time is not always n 

Note:
On the first iteration, the inner loop iterates once.
"" for second iteration
last loop is n
on average 

If you count it all out, we are adding up from `1..n`. This results in `n(n+1)/2`, which is still `n^2` after removing constants .

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

- Typical of logarithmic time complexity. Reducing the data set by a factor each time. Remember MergeSort?

---

```ruby
def example5_5(arr1, arr2)
    arr1.each do |a1|
     arr2.each do |a2|
      print a1, a2
     end
    end
end
```

---

    O(n * m), where n = arr1 and m = arr2

---

- both `arr1` and `arr2` have an impact on the overall complexity of this function
- we want to consider their individual impact on the number of steps required and express that in terms of Big O
- in this case, `m` steps are nested in each of the `n` steps => `O(n * m)` or `O(nm)`

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
Best Case: Constant

_*Worst Case:*_ Linear

---

```ruby
def example8(n)
  return 1 if n == 0
  example8(n-1) * example8(n-1)
end
```

---

O(2<sup>n</sup>)

---

This is a branching recursive tree. Since each call results in two more calls, we multiply by two for each level of the tree.

If we input 5, the total number of calls is `2^(n+1) - 1` => `O(2^n)`

---

```ruby
def example9(n)
  return 1 if n == 0
  n.times { print n } if n.odd?
  example9(n-1) * example9(n-1)
end
```

---

O(n * 2<sup>n</sup>)

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
      t.to_s.split('').each do |el| 
        print el 
      end
      t += 1
    end
  end
  print t
end
```

---

O(n<sup>2</sup> * logn)

---

- The key question here is: What is contained in the double loop?

- For each iteration we do extra work equal to the number of digits of the current number. Do you see that?

- The number of digits is roughly equal to `log10(n)`

---

- If we count everything up we get


Sum from i=1 to n<sup>2</sup> of log10(i)



- This should give us a Time Complexity of around `O(n^2 * log10(n^2))`; once we normalize the base of the logarithm and discard the constant factor this is `O(n^2 * logn)`.

- For `n=100` the total number of prints is 38,890;

---

```ruby
def example11(n)
  print n
  n.times do
    example11(n-1)
  end
end
```

---

- Factorial: `n=5` results in 4 more calls, each of which results in 3 more calls...etc.

---


<h3>General Approach</h3>
<ul>
  <li>
    Identify n (or necessary variables)
  </li>
  <li>
    Walk through algorithm tracking step/space in terms of n &mdash; add adjacent steps; multiply blocks within 
  </li><li>
    blocks; etc. 
  </li>
  <li>
    Consider recursion 
  </li>
  <li>
    Eliminate all but highest order term
  </li>
  <li>
    Eliminate coefficients 
  </li>
</ul>