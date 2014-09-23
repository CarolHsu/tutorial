# 初試 Python

> 部分章節是來自怪咖女孩 Carrots (http://django.carrots.pl/)

我們來寫些程式碼吧！


## Python 的命令提示字元

開始玩 Python 之前，我們需要在電腦上打開命令行視窗（就是終端機）。你應該已經知道那是什麼了 -- 你已經學過了 [命令行簡介](/intro_to_command_line/README.html) 一節。

一旦你準備好了，就按著下面的步驟來吧。

現在，我們想打開 Python 自己的主控台(console)，讓我們輸入 `python3` 然後按下 Enter。

    $ python3
    Python 3.4.1 (...)
    Type "copyright", "credits" or "license" for more information.
    >>>


## 你的第一個 Python 指令!

在運行了 Python 指令後，命令提示字元就改變成 `>>>` 了。對我們來說這是代表現在我們只能在這裡使用 Python 語言的指令。你不需要輸入 `>>>` - Python 本身已經幫你輸入好了。

如果你隨時想要離開 Python 主控台的話，就輸入 `exit()` 或是在 Windows 環境下按下熱鍵 `Ctrl + Z`，在 Mac/Linux 環境下按下熱鍵 `Ctrl + D` ，然後你就不會再看見 `>>>` 了。

但現在，我們還不想離開 Python 主控台，我們想要學習更多關於它的事。讓我們從最簡單的開始，舉例來說，試著輸入一點數學，像是`2 + 3` 然後按下 Enter。

    >>> 2 + 3
    5

幹得好！現在看看視窗跳出什麼來了？Python 懂數學耶！你可以嘗試其他指令像是：
- `4 * 5`
- `5 - 1`
- `40 / 2`


放輕鬆隨意玩會兒，待會再回來學習新進展 :)

如你所見，Python 是很棒的計算機。如果你還好奇你還可以拿它來做些什麼...


## 字串

那輸入你的名字呢？你可以像下面這樣試試看：

    >>> "Ola"
    'Ola'

你現在已經創造了你的第一個字串！這是一個可以被電腦運用的字元集合。字串通常會存在以一個同樣的字元來起頭和結束，或許是一個單引號 (`'`) 或者雙引號 (`"`) - 這會讓 Python 知道引號中的東西是一個字串。

字串們也可以被串在一起，試試看這招：

    >>> "Hi there " + "Ola"
    'Hi there Ola'

你也可以用一個數字來把字串乘起來：

    >>> "Ola" * 3
    'OlaOlaOla'

還有，如果你想要放一個單引號在你的字串裡面，你有兩種方式可以達成這個目標。

使用雙引號來宣告字串：

    >>> "Runnin' down the hill"
    "Runnin' down the hill"
    
或者，在想要加入的單引號前面給他一個反斜線 (`\`):

    >>> 'Runnin\' down the hill'
    "Runnin' down the hill"

不賴吧？去看看如何把你的名字全部換成大寫，簡單的輸入這個：

    >>> "Ola".upper()
    'OLA'

你只需要用 `upper` 這個 __函數(function)__ 在你的字串後面就可以了！一個函數（像是 `upper()`）就是一個指令集，讓 Python 可以在這個 (`"Ola"`) 物件(object)中展現你呼叫這個函數的效果。

如果你想要知道你的名字總共有幾個字元，也有相對應的函數可以叫用！

    >>> len("Ola")
    3

你應該很好奇，為什麼有時候你會在字串結尾用 `.` 來叫用一個函數（例如 `"Ola".upper()`），但有時你會先呼叫函數，然後把字串放在括號中？嗯，在某些狀況下，函數屬於某個物件，像是 `upper()` ，這個函數就只能表現在字串上。在這個狀況下，我們可以稱呼這類型函數為 __方法(method)__。其他時候，函數不屬於任何特定的類型或物件，可為各種不同類型或物件所用，像是 `len()`。這是為什麼我們可以在 `len()` 這個函數中放入一個 `"Ola"` 字串作為參數。


### 總結

好了，說夠了字串。目前為止你學到了：

- __命令提示字元(prompt)__ - 在 Python 的命令提示字元下輸入指令（程式碼）來得到結果
- __數字(number)及字串(string)__ - 在 Python 中數字可計算，而字串表示一個文字物件
- __運算子(operator)__ - 像是 + 與 *, 可結合兩個數值進行運算產生一個新的值
- __函數(function)__ - 像是 upper() 與 len(), 讓物件展現出某種行為

你剛剛學到的是所有程式語言的基礎。準備好接受更多挑戰了嗎？來吧！

## 錯誤訊息

我們來試試新的東西。看看我們能不能使用找到我們名字長度的那個函數，來得到某個數字的長度呢？輸入 `len(304023)` 按下 Enter:

    >>> len(304023)
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: object of type 'int' has no len()

恭喜！我們得到了我們的第一個錯誤訊息！它抱怨說這個物件的類型是 "int" (integer, 整數) 所以根本沒有長度這件事。所以我們現在應該怎麼辦呢？或許我們可以把我們這個數字寫成一個字串看看如何？字串就有長度啦，對吧？

    >>> len(str(304023))
    6

看起來成功了！我們在 `len` 函數中使用了 `str` 這個函數去把任何物件轉成字串。

- `str` 函數可將物件轉為 __字串__
- `int` 函數可將物件轉為 __整數__

> 重要：我們可以轉數字為字串，但我們不必然能把文字轉為數字 - 想想看要是 `int('hello')` 會有怎樣的結果？


## 變數

一個重要的程式觀念叫做變數(variables)。一個變數其實沒什麼，就是一個你稍後可以叫用的一個名字。程序員使用這些變數去儲存資料，讓他們的程式碼有更高的可讀性，這樣他們就不必一直記得那些資料是什麼。

所以我們就說好吧，現在我們做了一個新的變數叫做 `name`:

    >>> name = "Ola"

你看吧？就這麼簡單！其實只代表一件事情：這個叫做 name 的變數等於 "Ola" 這個字串。

如同你所注意到的，你的程式沒有回傳任何你宣告的東西。所以我們如何得知我們所宣告的變數確實存在呢？簡單的輸入 `name` 然後按下 Enter:

    >>> name
    'Ola'

呀比！你的第一個變數啊啊啊 :)！你可以隨時改變它的值像這樣：

    >>> name = "Sonja"
    >>> name
    'Sonja'

你也可以在函數中使用它：

    >>> len(name)
    5

太完美了，對吧？當然，變數可以是任何東西，數字亦然！試試看這個：

    >>> a = 4
    >>> b = 6
    >>> a * b
    24

但是萬一我們叫錯變數了呢？你可以猜到會發生什麼事情嗎？讓我們試試看吧！

    >>> name = "Maria"
    >>> names
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    NameError: name 'names' is not defined

又是一個錯誤訊息！如同你所見，Python 有各式各樣的錯誤訊息，這個就叫做一個 **NameError**。Python 會在你試圖使用一個從未宣告的變數時給你這個錯誤訊息。如果你得到像這樣的錯誤，就回頭看看你的程式碼裡面是不是有什麼變數的名字是打錯的。

玩一會兒吧，看看你還能做什麼！


## Print（印出） 函數

試試這招：

    >>> name = 'Maria'
    >>> name
    'Maria'
    >>> print(name)
    Maria

當你只是輸入 `name`，Python 直譯器會馬上回應你變數 `name` 所代表的字串，就是個用單引號包起來的 M-a-r-i-a 字母們。當你說 `print(name)` ，Python 就會在螢幕上「印出」這個變數的乾淨內容，沒有引號。

就像是我們稍後會看到的， 當我們想要印出某些東西時，或是想要印出一個有很多行的東西時，`print()` 就是個超有用的函數。


## 串列(List)

除了字串和整數，Python 還有一堆不同形態的物件。現在我們要介紹的稱為 __串列(list)__。List 就是你想的那樣：它是一個列出一堆物件的物件 XD

開始建立一個 List 吧：

    >>> []
    []

對沒錯，這就是一個空的 List。看起來沒什麼用啊... 我們來建立一組包含樂透彩數字的 List 吧。我們不想每次都重覆輸入這個長的 List，所以我們就把它存進一個變數裡吧：

    >>> lottery = [3, 42, 12, 19, 30, 59]

好了，我們有一個 List 了！我們可以拿它來幹嘛？來看看這個 List 的長度吧。你想到可以用什麼函數了嗎？沒錯就是它！

    >>> len(lottery)
    6

賓果！ `len()` 可以告訴你這個 List 有多長。真是太神奇了傑克！或許我們還可以幫這個 List 排序：

    >>> lottery.sort()

這不會回傳任何值，只是默默的的改變了 List 中數字們的順序。我們把它印出來看看發生了什麼事吧：

    >>> print(lottery)
    [3, 12, 19, 30, 42, 59]

如你所見，這串 List 數字已經從小到大排序了。恭喜囉！

那如果我們想要反排序呢？試試看吧！

    >>> lottery.reverse()
    >>> print(lottery)
    [59, 42, 30, 19, 12, 3]

很簡單對吧？如果你還想替 List 新加一點東西，可以輸入這個指令：

    >>> lottery.append(199)
    >>> print(lottery)
    [59, 42, 30, 19, 12, 3, 199]

如果你只想要秀某一個數字，你可以使用 __索引(index)__ 來指定。索引就是一個指出 List 某個物件位置的數字，電腦宅們喜歡讓索引從 0 開始，所以你的 List 中的第一個物件的索引就是 0，下一個物件則是 1，以此類推，試試看這些：

    >>> print(lottery[0])
    59
    >>> print(lottery[1])
    42

如你所見，你可以呼叫 List 變數的名字並指定索引值，並將索引值放在中括號 `[]` 中，來取得 List 裡不同的物件。

還有更多好玩的，試試看這些索引值： 6, 7, 1000, -1, -6 or -1000。看看你能不能在輸入指令前就預測到結果，這些結果合理嗎？

你可以在這個 Python 文件章節中，找到所有支援 List 物件的方法(method)：https://docs.python.org/3/tutorial/datastructures.html


## 字典(Dictionaries)


A dictionary is similar to a list, but you access values by looking up a key instead of an index. A key can be any string or number. The syntax to define an empty dictionary is:

    >>> {}
    {}

This shows that you just created an empty dictionary. Hurray!

Now, try writing the following command (try replacing your own information too):

    >>> participant = {'name' : 'Ola', 'country' : 'Poland', 'favorite_numbers' : [7, 42, 92]}

With this command, you just created a variable named `participant` with three key-value pairs:

- The key `name` points to the value `'Ola'` (a `string` object),
- `country` points to `'Poland'` (another `string`),
- and `favorite_numbers` points to `[7, 42, 92]` (a `list` with three numbers in it).

You can check the content of individual keys with this syntax:

    >>> print(participant['name'])
    Ola

See, it's similar to a list. But you don't need to remember the index - just the name.

What happens if we ask Python the value of a key that doesn't exist? Can you guess? Let's try it and see!

    >>> participant['age']
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    KeyError: 'age'

Look, another error! This one is a **KeyError**. Python is helpful and tells you that the key `'age'` doesn't exist in this dictionary.

When to use a dictionary or a list? Well, a good point to ponder on. Just have a solution in mind before looking at the answer in the next line.

- Do you just need an ordered sequence of items? Go for a list.
- Do you need to associate values with keys, so you can look them up efficiently (by key) later on? Use a dictionary.

Dictionaries are mutable like "lists" meaning that they can be changed after they are created. You can add new key/value pairs to the dictionary after it is created, like:

    >>> participant['favorite_language'] = 'Python'

Like the lists, using `len()` method on the dictionaries, returns the number of key-value pairs in the dictionary. Go ahead and type in the command:

    >>> len(participant)
    4

I hope it makes sense uptil now. :) Ready for some more fun with dictionaries? Hop on the next line for some amazing things.

You can use the `del` command to delete an item in the dictionary. Say, if you want to delete the entry corresponding to the key `'favorite_numbers'`, just type in the following command:

    >>> del participant['favorite_numbers']
    >>> participant
    {'country': 'Poland', 'favorite_language': 'Python', 'name': 'Ola'}

As you can see from the output, the key-value pair corresponding to 'favorite_numbers' key has been deleted.

Apart from this, you can also change a value associated with an already created key in the dictionary. Type:

    >>> participant['country'] = 'Germany'
    >>> participant
    {'country': 'Germany', 'favorite_language': 'Python', 'name': 'Ola'}

As you can see, the value of the key `'country'` has been altered from `'Poland'` to `'Germany'`. :) Exciting? Hurrah! You just learnt another amazing thing.

### Summary

Awesome! You know a lot about programming now. In this last part you learned about:

- __errors__ - you now know how to read and understand errors that show up if Python doesn't understand a command you've given it
- __variables__ - names for objects that allow you to code more easily and to make your code more readable
- __lists__ - lists of objects stored in a particular order.

Excited for the next part? :)

## Compare things

A big part of programming includes comparing things. What's the easiest thing to compare? Numbers, of course. Let's see how that works:

    >>> 5 > 2
    True
    >>> 3 < 1
    False
    >>> 5 > 2 * 2
    True
    >>> 1 == 1
    True

We gave Python some numbers to compare. As you can see, Python can compare not only numbers, but it can also compare method results. Nice, huh?

Do you wonder why we put two equal signs `==` next to each other to compare if numbers are equal? We use a single `=` for assigning values to variables. You always, __always__ need to put two `==` if you want to check if things are equal to each other.

Give Python two more tasks:

    >>> 6 >= 12 / 2
    True
    >>> 3 <= 2
    False

`>` and `<` are easy, but what do `>=` and `<=` mean? Read them like this:

- x `>` y means: x is greater than y
- x `<` y means: x is smaller than y
- x `<=` y means: x is smaller or equal to y
- x `>=` y means: x is greater or equal to y

Awesome! Wanna do one more? Try this:

    >>> 6 > 2 and 2 < 3
    True
    >>> 3 > 2 and 2 < 1
    False
    >>> 3 > 2 or 2 < 1
    True

You can give Python as many numbers to compare as you want, and it will give you an answer! Pretty smart, right?

- __and__ - if you use the `and` operator, both comparisons have to be True in order for the whole command to be True
- __or__ - if you use the `or` operator, only one of the comparisons has to be True in order for the whole command to be True

Have you heard of the expression "comparing apples to oranges"? Let's try the Python equivalent:

    >>> 1 > 'django'
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: unorderable types: int() > str()

Here you see that just like in the expression, Python is not able to compare a number (`int`) and a string (`str`).
Instead, it shows a **TypeError** and tells us the two types can't be compared together.

## Boolean

Accidently, you just learned about a new type of object in Python. It's called a __Boolean__ -- and it probably is the easiest type there is.

There are only two Boolean objects:
- True
- False

But for Python to understand this, you need to always write it as True (first letter uppercased, with the rest of the letter lowercased). __true, TRUE, tRUE won't work -- only True is correct.__ (The same applies to False as well, of course.)

Booleans can be variables, too! See here:

    >>> a = True
    >>> a
    True

You can also do it this way:

    >>> a = 2 > 5
    >>> a
    False

Practice and have fun with Booleans by trying to run the following commands:

- `True and True`
- `False and True`
- `True or 1 == 1`
- `1 != 2`

Congrats! You can now move on to an essential tool in programming:

## If...elif...else

Lots of things in code should only be executed when given conditions are met. That's why Python has something called __if statements__.

Try this:

    >>> if 3 > 2:
    ...

So far nothing has happened, as evidenced by the dots `...` instead of incentives `>>>` which we saw so far. Python expects us to give further instructions to it which are supposed to be executed if the condition `3 > 2` turns out to be true (or `True` for that matter). Let’s try to make Python print “It works!”:

    >>> if 3 > 2:
    ... print('It works!')
      File "<stdin>", line 2
        print('It works')
            ^
    IndentationError: expected an indented block

Well... something went wrong here! Python needs to know whether the instruction we have written is a continuation of `if` or a next instruction not covered by the condition. We need to indent our code to make it work:

    >>> if 3 > 2:
    ...     print('It works!')
    ...
    It works!

All you need is one space after `...`. To avoid chaos, most Python programmers use four spaces for each level of indentation.

Everything that is indented after the `if` statement will be executed if the condition is met. See:

    >>> if 3 > 2:
    ...     print('It works!')
    ...     print('Another command')
    ...
    It works!
    Another command

### What if not?

In previous examples, code was executed only when the conditions were True. But Python also has `elif` and `else` statements:

    >>> if 5 > 2:
    ...     print('5 is indeed greater than 2')
    ... else:
    ...     print('5 is not greater than 2')
    ...
    5 is indeed greater than 2

If 2 were a greater number than 5, then the second command would be executed. Easy, right? Let's see how `elif` works:

    >>> name = 'Sonja'
    >>> if name == 'Ola':
    ...     print('Hey Ola!')
    ... elif name == 'Sonja':
    ...     print('Hey Sonja!')
    ... else:
    ...     print('Hey anonymous!')
    ...
    Sonja!

See what happened there?

### Summary

In the last three exercises you learned about:

- __comparing things__ - in Python you can compare things by using `>`, `>=`, `==`, `<=`, `<` and the `and`, `or` operators
- __Boolean__ - a type of object that can only have one of two values: `True` or `False`
- __if...elif...else__ - statements that allow you to execute code only when certain conditions are met.

Time for the last part of this chapter!

## Your own functions!

Remember functions like `len()` that you can execute in Python? Well, good news, you will learn how to write your own functions now!

A function is a set of instructions that Python should execute. Each function in Python starts with the keyword `def`, is given a name and can have some parameters. Let's start with an easy one:

    >>> def hi():
    ...

As you can see, there are those dots again! This means that nothing has really happened yet... and yes, we need to press the `Space` key before giving our instructions:

    >>> def hi():
    ...     print('Hi there!')
    ...     print('How are you?')
    ...

OK, our first function is ready! Press Enter to get back to the Python prompt again. Now let's execute our function:

    >>> hi()
    Hi there!
    How are you?

Great! You're now a programmer, congratulate yourself :)!

That was easy! Let's build our first function with parameters. We will use the previous example - a function that says 'hi' to the person running it - with a name:

    >>> def hi(name):
    ...

As you can see, we now gave our function a parameter that we called `name`:

    >>> def hi(name):
    ...     if name == 'Ola':
    ...         print('Hi Ola!')
    ...     elif name == 'Sonja':
    ...         print('Hi Sonja!')
    ...     else:
    ...         print('Hi anonymous!')
    ...

As you can see, we needed to put two spaces before the `print` function, because `if` needs to know what should happen when the condition is met. Let's see how it works now:

    >>> hi()
        Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: hi() missing 1 required positional argument: 'name'

Oops, an error. Luckily, Python gives us a pretty useful error message.
It tells us that the function `hi()` (the one we defined) has one required argument (called `name`) and that we forgot to pass it when calling the function.
Let's fix it then:

    >>> hi("Ola")
    Hi Ola!
    >>> hi("Sonja")
    Hi Sonja!
    >>> hi("Anja")
    Hi anonymous!

Awesome, right? This way you don't have to repeat yourself every time you want to change the name of the person the function is supposed to greet. And that's exactly why we need functions - you never want to repeat your code!

Let's do something smarter -- there is more names than two, and writing a condition for each would be hard, right?

    >>> def hi(name):
    ...     print('Hi ' + name + '!')
    ...

Let's call the function now:

    >>> hi("Rachel")
    Hi Rachel!

Congratulations! You just learned how to write functions :)!

## Loops

That's the last part already. That was quick, right? :)

As we mentioned, programmers are lazy, they don't like to repeat themselves. Programming is all about automating things, so we don't want to greet every person by their name manually, right? That's where loops come in handy.

Still remember lists? Let's do a list of girls:

    >>> girls = ['Rachel', 'Monica', 'Phoebe', 'Ola', 'You']

We want to greet all of them by their name. We have the `hi` function to do that, so let's use it in a loop:

    >>> for name in girls:
    ...

Dots again! Remember what goes after the dots? Yes, a space :)

    >>> for name in girls:
    ...     hi(name)
    ...     print('Next girl')
    ...
    Hi Rachel!
    Next girl
    Hi Monica!
    Next girl
    Hi Phoebe!
    Next girl
    Hi Ola!
    Next girl
    Hi You!
    Next girl

As you can see, everything you will put inside a `for` statement with space will be repeated for every element of the list `girls`.

You can also use `for` on numbers using the `range` method:

    >>> for i in range(1, 6):
    ...     print(i)
    ...
    1
    2
    3
    4
    5

`range` is a function that creates a list of numbers following one after the other (these numbers are provided by you as parameters).

Note that the second of these two numbers is not included in the list that is output by Python (meaning `range(1, 6)` counts from 1 to 5, but does not include the number 6).

## Exiting Python

You can exit Python and return to the command line using `exit()`.

## Summary

That's it. __You totally rock!__ This really wasn't so easy, so you should feel proud of yourself. We're definitely proud of you for making it to here!

Grab yourself a cupcake and go to the next chapter :)

![Cupcake](images/cupcake.png)
