
# Common Data Clean Up Operations


## Introduction
Eventually you're going to want to be able to import a csv file or scrape web pages and then automate the cleaning of your data by looping over all of the information and cleaning it up automatically. However, there are a lot of new concepts required to get to that point, so let's work on them one at a time.

In this lesson we're just going to focus on taking an individual variable and cleaning it up and/or changing its data type.

## Objectives
You will be able to:
* Perform simple data clean up operations on individual variables

### String to Integer
You've seen this one before, but let's take a run at it. We want to add two "numbers" but they are both stored as strings. Modify the code in the next cell to get the addition to work and return the value you'd expect. Remember - `shift-enter` to run the code in a cell.


```python
chase_bank_balace = "145000"
capital_one_bank_balance = "27000"
credit_card_balance = "1400"
assets = chase_bank_balace + capital_one_bank_balance - credit_card_balance
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-38-793a63b097b4> in <module>()
          2 capital_one_bank_balance = "27000"
          3 credit_card_balance = "1400"
    ----> 4 assets = chase_bank_balace + capital_one_bank_balance - credit_card_balance
    

    TypeError: unsupported operand type(s) for -: 'str' and 'str'


### Fixing Capitalization
When you are comparing text in a programming language, the code is often case sensitive (so "Ben", "ben" and "BEN" would be considered to be three different names. Try running the code below, and then just go in, change the value of name_1 to be all lower case and re-run the code.


```python
name_1 = "Ben"
name_2 = "ben"
if name_1 == name_2:
    print("The names match!")
else:
    print("Oops - problems with capitalization!")
```

    Oops - problems with capitalization!


So, consistent capitalization helps to make data both easier to read and easier to process.

There are a few methods (small pieces of pre-written software) built right into the Python programming language to make it easy to fix capitalization. 

`.upper()` capitalizes all of the letters
`.lower()` downcases all of the letters
`.capitalize()` makes the first letter of a string capital and downcases the other characters.

See them in action below:


```python
name = "SAlLY JonES"
print(name.lower())
print(name.upper())
print(name.capitalize())
```

    sally jones
    SALLY JONES
    Sally jones


One thing to look out for though. Some methods mutate (change) a variable. Others just return a new value, leaving the original variable as it is. Note below that the original name hasn't changed:


```python
name = "SAlLY JonES"
print(name.lower())
print(name.upper())
print(name.capitalize())
print(name)
```

    sally jones
    SALLY JONES
    Sally jones
    SAlLY JonES


So, if you want to change a variable, you have to write your code slightly differently:


```python
name = "SAlLY JonES"
name = name.capitalize()
print(name)
```

    Sally jones


Remember that if your code *looks* right but the values of your variables aren't changing!

### Creating Booleans from Strings
Often as a pre-processing stage, you want to take a string and based on it's value, set a boolean for that record. Lets say we want to easily find people who are living in Texas vs elsewhere and we want to take the `State` field from their address and use it to create a boolean called `lives_in_texas`. The core code might look something like this:


```python
state = "TX"
if state == "TX":
    lives_in_texas = True
else:
    lives_in_texas = False

print(lives_in_texas)
```

    True


Try pulling together the last two ideas. Here is some starter code. Can you change the code so it doesn't matter what the capitalization of the state name is?

*Note that the lines starting with a # are comments in Python, so they're notes to you, but aren't processed by the Python interpreter.*


```python
state = "Tx"
# Do something to the state variable here
# state = . . . . 
if state == "TX":
    lives_in_texas = True
else:
    lives_in_texas = False

print(lives_in_texas)
```

    False


### Creating Booleans from Numbers

Try something similar with this code. In this case lets say we're investigating a bunch of day laborers and lets assume that if they have more than (say) $5,000 in the bank we consider them to be suspicious *(hey, they could just be lucky or thrifty, but it's worth investigating further)*.

As you can see, if you run the code below, it doesn't work because we're trying to compare a string with a number. Can you add a line to the code to turn the bank balance into a number as well to get this to work?



```python
bank_balance = "7000"
# Do something to the bank_balance variable here
# bank_balance = . . .
if bank_balance > 5000:
    suspicious_assets = True
else:
    suspicious_assets = False
print(suspicious_assets)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-42-ea0acb22df8d> in <module>()
          2 # Do something to the bank_balance variable here
          3 # bank_balance = . . .
    ----> 4 if bank_balance > 5000:
          5     suspicious_assets = True
          6 else:


    TypeError: '>' not supported between instances of 'str' and 'int'


### Extracting Numbers from Strings

We've seen how to take a simple representation of a number which is stored as a string and to turn that into a number. But what happens if there are additional characters. See what happens when you run the code below (hint, it won't work!!!)


```python
salary="$36,000"
print(salary)
if salary > 46000:
    livable_wage = True
else:
    livable_wage = False
print(livable_wage)
```

    $36,000



    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-43-7b73487f6f7b> in <module>()
          1 salary="$36,000"
          2 print(salary)
    ----> 3 if salary > 46000:
          4     livable_wage = True
          5 else:


    TypeError: '>' not supported between instances of 'str' and 'int'


There are a lot of ways of solving this problem. Here is one solution. 


```python
salary="$36,000"
salary = int(''.join(filter(str.isdigit, salary)))
print(salary)
if salary > 46000:
    livable_wage = True
else:
    livable_wage = False
print(livable_wage)
```

## Summary
As you saw above, some problems are easy to solve in Python (turn "12" into 12). Some are quite a bit more complex (turn "$12" into 12). Figuring out which is which is not always obvious, so don't get surprised if sometimes there is something you think should be easy but ends up being hard - that happens to programmers all the time. Also, Google is your friend. Generally the hardest part of solving most small programming challenges is finding the right keywords to Google to find a good blog post or stack overflow thread that will give you the code that you need!

Now that you've had a little experience with cleaning up data, lets set you up with a lab where you can get more practice (of coding and of Googling)!


