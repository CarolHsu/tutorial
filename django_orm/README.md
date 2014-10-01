# Django ORM 與 QuerySets

在這個章節你將了解 Django 如何連接到資料庫，並且把資料儲存進入。來吧！

## 什麼是 QuerySet?

一個 QuerySet，大體上來說，是一個充滿了 Model 物件的清單。QuerySet 允許你從資料庫中讀取資料，也可以對資料做篩選或排序。

從做中學最簡單明瞭了。現在就來試試看好嗎 :)


## Django shell

打開你的終端機輸入以下指令：

    > $ python manage.py shell

結果會像下面這樣：

    (InteractiveConsole)
    >>>

你現在就在 Django 的互動式介面裡了。它就像一般單純的 Python 命令提示字元，但是多了 Django 魔法 :)
當然囉，你可以使用所有的 Python 指令。

### 所有物件

首先我們來試試展示所有我們的網誌。你可以輸入下面指令：

    >>> Post.objects.all()
    Traceback (most recent call last):
          File "<console>", line 1, in <module>
    NameError: name 'Post' is not defined

噢喔！出現一個錯誤了。它抱怨說沒有 Post 啊。沒錯 -- 我們忘記先把 Post 載入進來了。

    >>> from blog.models import Post

這是一個範例：我們從 `blog.models` 載入了 model `Post` 。我們重新來試試秀出所有的網誌吧：

    >>> Post.objects.all()
    []

看起來是個空的 list。這沒錯吧？我們確實還沒有新增任何的網誌！讓我們增加一下。


### 創造物件

下面示範了你可以怎麼做來增加一個 Post 物件在資料庫裡：

    >>> Post.objects.create(author=user, title='Sample title', text='Test')

但我們好像少了一個要件： `user`。我們需要傳入一個 `User` Model 實體來作為文章作者。怎麼做呢？

先來載入一個 User model：

    >>> from django.contrib.auth.models import User

我們資料庫裡面有哪些 users 呢？試試這個吧：

    >>> User.objects.all()
    [<User: ola>]

酷斃了！我們獲得一個 user 實體了：

    user = User.objects.get(username='ola')

如你所見，我們知道 `get` 一個 `User` 的 `username` 會是 `ola`。乾淨俐落！當然了，你必須將它改為你的使用者名稱。

現在我們終於可以創一個我們的第一個 post 了：

    >>> Post.objects.create(author = user, title = 'Sample title', text = 'Test')

萬歲！想要看看有沒有成功嗎？

    >>> Post.objects.all()
    [<Post: Sample title>]

### 新增更多 posts

你了解到，新增一些 post 然後看看它有沒有成功就可以從中獲得一點小確幸。立馬新增兩三個或更多個吧！

### 篩選 objects

QuerySet 很大一部份的能力是篩選資料。這麼說吧，我們想要找到所有由使用者 ola 新增的 post。我們將會使用 `filter` 而不是在 `Post.objects.all()` 的 `all`。在括號中我們可以放入很多條件，而找到的資料必須符合我們的查詢條件。在這個例子中 `author` 等於 `user`。用 Django 寫起來就是 `author=user`。現在我們這段 code 就會像這樣：

    >>> Post.objects.filter(author=user)
    [<Post: Sample title>, <Post: Post number 2>, <Post: My 3rd post!>, <Post: 4th title of post>]

或是也許我們想要看看所有 `title` 有 `title` 這個字的網誌呢？

    >>> Post.objects.filter(title__contains='title')
    [<Post: Sample title>, <Post: 4th title of post>]

你也可以獲得所有已發佈的網誌。我們會用 `published_date` 來篩選出來：

    >>> Post.objects.filter(published_date__isnull=False)
    []

不幸的是，目前沒有半篇網誌是已經發佈的。我們可以改變這個情形！首先取得所有我們想要發佈的網誌：

    >>> post = Post.objects.get(id=1)

然後用我們的 `publish` 方法發佈它！

    >>> post.publish()

現在試試得到一個已發佈網誌清單吧（按 3 次上方向鍵然後按下 Enter）：

    >>> Post.objects.filter(published_date__isnull=False)
    [<Post: Sample title>]


### 對 objects 排序


QuerySets 也允許你對物件清單排序。我們來試試用 `created_date` 這個欄位去排序它：

    >>> Post.objects.order_by('created_date')
    [<Post: Sample title>, <Post: Post number 2>, <Post: My 3rd post!>, <Post: 4th title of post>]

我們也可以在開頭加上 `-` 反排：

    >>> Post.objects.order_by('-created_date')
    [<Post: 4th title of post>,  <Post: My 3rd post!>, <Post: Post number 2>, <Post: Sample title>]

酷斃了！你現在已經對下一個階段蓄勢待發了！輸入下面指令關掉終端機：

    >>> exit()
    $
