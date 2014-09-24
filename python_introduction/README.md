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

Dictionary 和 List 有點像，差別在於，你可以用鍵值(key)而非索引值(index)來取得在 Dictionary 中的值(value)。一個 key 可以是字串或數字。你可以使用兩個大括號來宣告一個 dictionary：

    >>> {}
    {}

這樣就創建了一個空字典，喲齁！

現在，試著輸入下面指令（你也可以試著輸入你自己的資訊）：

    >>> participant = {'name' : 'Ola', 'country' : 'Poland', 'favorite_numbers' : [7, 42, 92]}

使用這個指令，你就等於是宣告了一個叫做 `participant` 的 key-value 結對變數：

- `name` 這個 key 對應到 `'Ola'` 這個 value (一個 `字串(string)` 物件),
- `country` 對應到 `'Poland'` (另一個 `字串(string)`),
- 還有 `favorite_numbers` 對應到 `[7, 42, 92]` (一個包含了三個數字在內的 `串列(list)` ).

你可以指定特殊的 key 來檢查內容，語法如下：

    >>> print(participant['name'])
    Ola

你看，和 List 有點像。不過你就不需要再記住索引值(index)了 - 就變成一個好記的名稱。

如果你向 Python 要一個不存在的 key 所對應的 value 的話會發生什麼事呢？我們試試看吧！

    >>> participant['age']
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    KeyError: 'age'

看到了吧，又是一個錯誤訊息，這次是 **KeyError** 。Python 會讓你知道這個 `'age'` key 事實上是不存在目前的 dictionary 中的。

什麼時候要用 List，什麼時候又要用 Dictionary 呢？嗯，這個問題值得深思。再看看下面內容前先把這個問題放在心裡吧。

- 你是不是只是需要一個有序的序列呢？就使用 List 吧。
- 你需要有 key 值的 value，好讓你可以更有效率地找到特定值嗎？那就使用 Dictionary 吧。

Dictionary 也像 "List" 一樣，可以默默地把它裡面的東西做點改變，你可以加入一對新的 key/value 值像這樣：

    >>> participant['favorite_language'] = 'Python'

如同 List，Dictionary 也可以使用 `len()` ，回傳 Dictionary 總共有幾對 key-value 值吧，輸入下面指令：

    >>> len(participant)
    4

我希望目前為止對你來說都還可以了解。 :) 準備好玩玩更多有趣的 Dictionary 了嗎？跳到下一行看看一些很酷的事情吧。

你可以使用 `del` 指令來刪除 Dictionary 中的項目。使用它，如果你想要刪掉一個叫做 `'favorite_numbers'` 的 key，就輸入下面指令：

    >>> del participant['favorite_numbers']
    >>> participant
    {'country': 'Poland', 'favorite_language': 'Python', 'name': 'Ola'}

輸出結果如你所見，符合 'favorite_numbers' 的 key-value 數對已經被刪除了。

除此之外，你也可以改變已經建立的 Dictionary 中的特定值，輸入：

    >>> participant['country'] = 'Germany'
    >>> participant
    {'country': 'Germany', 'favorite_language': 'Python', 'name': 'Ola'}

一樣如同你所看見的，一個 key 值為 `'country'` 的值從 `'Poland'` 變成了 `'Germany'`。 :) 興奮嗎？喲齁！你剛剛學到更多超棒的知識了！


### 總結

太完美了！你現在了解更多程式設計的知識了。在上面你學到了：

- __錯誤訊息__ - 當 Python 看不懂你給的指令時，你現在知道怎麼去閱讀並且了解錯誤訊息的意思了
- __變數__ - 這是物件的名字，讓你可以更輕鬆的寫程式，也讓你的程式更具可讀性
- __串列__ - 可以用特定順序來儲存多個物件的清單

人生要進階了，興奮嗎？ XDDDD


## 比對(compare)

程式中有很大一部份都在比對東西。什麼是最容易被比對的東西呢？當然是數字。我們來看看這裡怎麼做的：

    >>> 5 > 2
    True
    >>> 3 < 1
    False
    >>> 5 > 2 * 2
    True
    >>> 1 == 1
    True

我們給 Python 幾個數字去互相比對。如同你看見的，Python 不僅可以比對數字，甚至可以比對不同方法產生的結果，酷斃了對吧？

你說不定也會好奇為什麼我們寫了兩個等號 `==` 就可以比對兩個數字是不是相等，我們用單一個等號 `=` 去給變數賦值。如果你想要知道兩個東西是不是相等，你通常， __通常__ 需要放兩個 `==` 在兩個東西之間。

給 Python 更多工作：

    >>> 6 >= 12 / 2
    True
    >>> 3 <= 2
    False

`>` 及 `<` 很直觀，不過 `>=` 和 `<=` 是什麼意思? 其實事情是這樣的：

- x `>` y 表示: x 大於 y
- x `<` y 表示: x 小於 y
- x `<=` y 表示: x 小於等於 y
- x `>=` y 表示: x 大於等於 y

很棒吧！想知道更多嗎？試試這些：

    >>> 6 > 2 and 2 < 3
    True
    >>> 3 > 2 and 2 < 1
    False
    >>> 3 > 2 or 2 < 1
    True

你儘可以給 Python 所有你想比對的數字，它都會給你答案！非常聰明對吧？

- __and__ - 如果你使用 `and` 運算子，會回傳給你一個交集（所有結果都必須為 `true` 才是 `true）
- __or__ - 如果你使用 `or` 運算子，會回傳給你一個聯集（只要其中一個結果都必須為 `true` 就是 `true）


不知道你有沒有聽過一個諺語「牛頭不對馬嘴」（按：原文為 "comparing apples to oranges"）呢? 讓我們來試試下面的等式吧！：

    >>> 1 > 'django'
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: unorderable types: int() > str()

在此你看到在這個表達式中，Python 無法用數字 (`int`) 來與字串 (`str`) 做比較。
此外，它給了一個 **TypeError** 並告訴我們這兩種型態無法放在一起比較。


## 布林值(Boolean)

很快的，你學到了一個新的 Python 物件型別。這稱為 __布林值(Boolean)__ -- 這或許是一種最簡單的型別。

這裡是兩個 Boolean 物件
- True
- False

為了讓 Python 知道那是布林值，你必須把它寫成像這樣 True（字首大寫，其餘小寫）。__true, TRUE, tRUE 都不會有作用 -- 只有 True 是正確的。__ （當然囉，False 亦同）

Boolean 也值可以存成變數！像這樣：

    >>> a = True
    >>> a
    True

你也可以這麼做：

    >>> a = 2 > 5
    >>> a
    False

玩一玩練習一下 Boolean 值，運行下面的指令：

- `True and True`
- `False and True`
- `True or 1 == 1`
- `1 != 2`

恭喜！你現在要進入到程式設計裡面最主要的一個段落了：


## If...elif...else

在程式運行時，很多時候就只是在判斷一些設定條件是不是符合而已。這就是為什麼 Python 中有個東西叫做 __if 判斷式__ 。

試一下：

    >>> if 3 > 2:
    ...

目前為止，除了本來應該是 `>>>` 的地方出現了點點點 `...` 以外，Python 毫無反應。Python 預期我們會給出更多的說明來讓它執行一個 if 的 `3 > 2` 成立的條件式。我們來讓 Python 印出 "It works!"：

    >>> if 3 > 2:
    ... print('It works!')
      File "<stdin>", line 2
        print('It works')
            ^
    IndentationError: expected an indented block

呃... 這裡出了一些錯！Python 需要知道這些說明是不是接續在 `if` 敘述之後，或者這是另外一個與條件式無關的段落。我們必須縮排這行 code 讓它可以運行：

    >>> if 3 > 2:
    ...     print('It works!')
    ...
    It works!

然後你又有一行在 `...` 後面的空白了。為了避免雜亂無章，多數的 Python 程序員習慣使用 4 個空白作為縮排。

所有在 `if` 判斷式後面的程式碼都縮排了，在條件符合的狀況下都會被執行。看吧：

    >>> if 3 > 2:
    ...     print('It works!')
    ...     print('Another command')
    ...
    It works!
    Another command

### 如果我們不想要這樣呢？

在前一個範例中，這些程式碼只會在條件是成立的時候被執行。但 Python 還有 `elif` 與 `else` 判斷式：

    >>> if 5 > 2:
    ...     print('5 is indeed greater than 2')
    ... else:
    ...     print('5 is not greater than 2')
    ...
    5 is indeed greater than 2

如果 2 大於 5，那第二段指令就會被執行。很簡單吧？我們看看 `elif` 如何運作：

    >>> name = 'Sonja'
    >>> if name == 'Ola':
    ...     print('Hey Ola!')
    ... elif name == 'Sonja':
    ...     print('Hey Sonja!')
    ... else:
    ...     print('Hey anonymous!')
    ...
    Sonja!

看看會發生什麼事吧？


### 總結

在剛剛的三個練習中，你已經學到：

- __比對__ - 在 Python 中你可以用 `>`, `>=`, `==`, `<=`, `<` 和 `and`, `or` 來比對東西
- __Boolean__ - 一種只有兩種值的物件型別： `True` 或 `False`
- __if...elif...else__ - 判斷式讓你可以在條件符合的狀況下執行相應的程式碼

現在是時候進入到最後一章了！


## 你自己的函數!

還記得你先前在 Python 中執行過像是 `len()` 這樣的函數嗎？嗯，好消息，你將可以學習如何寫一個屬於你自己的函數囉！

一個函數就是一堆 Python 應該執行哪些行為的集合。在 Python 中每個函數都用一個關鍵字 `def` 來宣告，可以被賦予一個名稱與一些參數。我們來做一個簡單的：

    >>> def hi():
    ...

如你所見，這裡又出現點點們了！這代表你還可以繼續說些話... 以及沒錯，在做更多描述錢，我們需要按幾次空白鍵：

    >>> def hi():
    ...     print('Hi there!')
    ...     print('How are you?')
    ...

好了，我們的第一個函數完成了！按下 Enter 再次回到 Python 命令提示字元。現在我們來執行我們的函數：

    >>> hi()
    Hi there!
    How are you?

棒極了！你現在是個程序員了，恭喜一下自己吧 :)！

這真是簡單！讓我們來建立自己的第一個有參數的函數吧。我們將會使用前一個範例 - 一個會對某個人說 'hi' 的函數，並且執行它 - 並帶有一個名字：

    >>> def hi(name):
    ...

如你所見，我們現在讓這個函數帶有一個叫做 `name` 的參數：

    >>> def hi(name):
    ...     if name == 'Ola':
    ...         print('Hi Ola!')
    ...     elif name == 'Sonja':
    ...         print('Hi Sonja!')
    ...     else:
    ...         print('Hi anonymous!')
    ...

這裡你可以看到，我們需要放兩個縮排在 `print` 函數前面了，因為 `if` 需要知道接下來的條件符合的話會發生什麼事。我們來看看現在他運作得如何：

    >>> hi()
        Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: hi() missing 1 required positional argument: 'name'

喔喔，一個錯誤訊息。很幸運的，Python 給我們一個非常有用的錯誤訊息。它告訴我們這個叫做 `hi()` 的函數（就我們剛剛定義的那個）要求必須傳入一個參數（就是 `name`），只是我們叫用這個函數的時候忘記忘記傳入了。

我們把它修好吧：

    >>> hi("Ola")
    Hi Ola!
    >>> hi("Sonja")
    Hi Sonja!
    >>> hi("Anja")
    Hi anonymous!

太完美了！這下子當你需要換個人名說 hi 的時候，你就不需要一直重複做一樣的事情。這就是為什麼我們如此需要函數 - 你永遠不會想要重複你的程式碼！

我們再來做點更聰明的事 -- 如果我們有兩個以上的人名，寫兩次差不多的句子真的很累對吧？

    >>> def hi(name):
    ...     print('Hi ' + name + '!')
    ...

現在我們可以叫用這個函數了：

    >>> hi("Rachel")
    Hi Rachel!

恭喜！你剛剛學到如何寫一個函數了 :) ！


## 迴圈(Loop)

現在就是最後一步了，進展滿快的呢 :)

就像我們先前所提到的，程序員很懶，他們很討厭重複自己。程式設計應該是一件完全自動化的事情，所以我們不希望手動去對每個不同的人名說嗨，沒錯吧？所以迴圈的出現非常好用。

還記得 List 嗎？我們來做一個女孩 List:

    >>> girls = ['Rachel', 'Monica', 'Phoebe', 'Ola', 'You']

我們想要對每個人的名字說嗨。我們已經有一個 `hi` 函數可以用了，我們讓我們把這個函數放在迴圈之中：

    >>> for name in girls:
    ...

噢又是點點們！記得點點出現時要做什麼事情嗎？沒錯，縮排 :)

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

如你所見，你利用縮排將一些程式碼放在 for 判斷式之中都會重複執行，而且會逐次帶入 List 中的女孩名字。

你也可以用 for 來帶入一個數字範圍：

    >>> for i in range(1, 6):
    ...     print(i)
    ...
    1
    2
    3
    4
    5

`range` 是個可以建立兩個數字範圍中所有數字 List 的函數（這兩個數字來自由你提供的參數）

要注意的是，在 Python 中，range 會輸出第二個參數的前一個整數（就是說如果有一個函數 `range(1, 6)` 就會輸出 1 到 5，但不會包含數字 6）。


## 離開 Python 主控台

你可以用指令 `exit()` 來離開 Python 主控台。


## 總結

這就是全部了。 __你真是酷斃了！__ 這真的很不簡單，所以你可以為你自己鼓鼓掌。我們也超級為你可以走到這裡感到驕傲！

進行到下一章之前抓個杯子蛋糕來吃吧 :)

![杯子蛋糕](images/cupcake.png)
