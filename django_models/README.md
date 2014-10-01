# Django models

我們現在想要新建立的東西，將可以儲存我們部落格中的所有發文。為了這個目的我們需要講一點點小東西，這個東西被稱為 `物件(object)` 。

## 物件 (Objects)

有一個被程序員們稱為 `物件導向程式設計 (Object-oriented programming)` 的概念。這個想法是說，無論是什麼東西，即便只是一個程式敘述無趣至極的序列，我們都可以把它模型化，並且定義它如何與其他東西互動。

所以什麼是物件？就是一個把性質與行為量化的東西。這聽起來很詭異，我們用一個例子來解釋。

如果我們要模擬一隻貓，我們就會建立一個叫做 `Cat` 的物件，並且這個 `Cat` 會有一些屬性。例如說， `毛色` 、 `貓齡` 、 `心情` (像是「好心情」、「壞心情」、「昏昏欲睡」等等)， `飼主` (這或許就是一個 `Person` 物件，如果是一隻走失的貓咪，這個屬性應該就是空的)。

然後這隻貓會有一些行為： `發出呼嚕聲` 、 `磨蹭` 或者 `被餵食` (這時我們會給貓咪一些 `貓食` ，當然這個貓食也應該要被獨立成另外一個擁有自己的屬性的物件，像是 `口味`)。

    Cat（貓咪）
    --------
    color （毛色）
    age （貓齡）
    mood （心情）
    owner （飼主）
    purr() （發出呼嚕聲()）
    scratch() （磨蹭()）
    feed(cat_food) （被餵食(貓食)）


    CatFood （貓食）
    --------
    taste （口味）

所以說基本上這個想法可以在程式碼中描述真實的物品，藉由一些屬性（稱為 `物件屬性 object properties`） 與行為（稱為 `方法 methods` ）。

那我們如何去把部落格中的文章模型化？我們想要建立一個部落格對吧？

我們需要先思索一個問題：什麼是網誌？它擁有哪些屬性？

嗯，可以確定的是我們的網誌一定會有一些文字，像是內容與標題，對吧？能知道這篇網誌是誰寫的也是一個好主意 - 所以我們還需要作者。最後，我們想要知道何時新增與發表了這篇網誌。

    Post
    --------
    title
    text
    author
    created_date
    published_date

那網誌又可以做什麼樣的事情呢？如果可以有一些 `method` 來發佈網誌就太好了對吧！

所以我們也需要 `publish (發佈)` 方法。

既然我們已經知道有哪些需要做的事情，我們就可以開始用 Django 模擬它了！


## Django model

了解了何謂物件，我們就來做一個我們的網誌的 Django model 吧。

Model 在 Django 中是一種特別類型的物件 - 它被儲存在 `資料庫 database` 中。一個資料庫就是一堆資料的集合。這裡你可以儲存使用者的資訊、你的網誌等等。我們將使用 SQLite 資料庫來儲存我們的資料。這是 Django 內建的資料庫連接器 -- 這夠我們用了。

你可以將一個 model 想像成在資料庫裡面的一個有行(rows - 一筆資料)與列(columns - 欄位)的電子表格。

### 創建一個應用程序

為了保持一切整潔乾淨，我們會將一個獨立的應用程序創建在我們的專案中。如果可以從一開始就讓一切井然有序最好了。我們可以在終端機中執行以下指令來新建一個應用程式（在有 `manage.py` 檔的 `djangogirls` 資料夾下）：

    (myvenv) ~/djangogirls$ python manage.py startapp blog

你會發現多了一個新建的 `blog` 資料夾，裡面有一些檔案。我們在這個專案下的的整個資料目錄就變成這樣子了：

    djangogirls
    ├── mysite
    |       __init__.py
    |       settings.py
    |       urls.py
    |       wsgi.py
    ├── manage.py
    └── blog
            __init__.py
            admin.py
            models.py
            tests.py
            views.py

在創建了一個應用程序後我們也需要告訴 Django 說這個應用程序要用上它。我們在 `mysite/settings.py` 這個檔案中設定。我們需要找到 `INSTALLED_APPS` 然後在 `(` 內加上一行 `'blog',` 。所以最終產物就會長得像這樣。

    INSTALLED_APPS = (
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        'blog',
    )


### 建立一個網誌 model

我們定義所有叫做 `Model` 的物件在 `blog/models.py` 檔中 - 這禮我們可以定義我們的網誌。

讓我們打開 `blog/models.py` ，移除裡面所有的東西，並寫下這樣的程式碼：

    from django.db import models
    from django.utils import timezone
    from django.contrib.auth.models import User

    class Post(models.Model):
        author = models.ForeignKey(User)
        title = models.CharField(max_length=200)
        text = models.TextField()
        created_date = models.DateTimeField(
                default=timezone.now)
        published_date = models.DateTimeField(
                blank=True, null=True)

        def publish(self):
            self.published_date = timezone.now()
            self.save()

        def __str__(self):
            return self.title

看起來豪可怕啊對嗎？但別擔心，我們會一行一行的解釋給你聽！

所有行首是 `from` 或 `import` 的程式碼就是引進其他檔案的程式。所以除了複製貼上一堆一樣的程式碼以外，我們也可以用 `from... import...` 來把檔案內容載入進來。


`class Post(models.Model):` - 這行定義了我們的 model (它就是一個 `object` )
- `class` 是由我們定義的一個物件，是一個保留字。
- `Post` 是這個 model 的名稱，我們可以給各種不同的名字（但必須避免特殊自元與空白）。這裡的字首永遠大寫。
- `models.Model` 這意指 Post 是一個 Django Model, 這樣 Django 就會知道要這個東西要存進資料庫。

現在我們定義我們剛才提到的各種性質： `title` 、 `text` 、 `created_date` 、 `published_date` 與 `author` 。為了做這件事我們必須要定義資料形態（它是文字嗎？還是數字？是個日期嗎？是個關聯性物件嗎，像是 User 這類的？）

- `models.CharField` - 這裏你可以定義這個資料是一個有上限的字元。
- `models.TextField` - 這裏你可以定義這個資料是一個有無上限的字串。這適合被部落格網誌的內容所用，對吧？
- `models.DateTimeField` - 這是是日期與時間。
- `models.ForeignKey` - 這是與其他 model 的關聯。

我們不解釋所有的程式碼，因為會花上太多時間。你應該看一下 Django 的文件 (https://docs.djangoproject.com/en/1.6/ref/models/fields/#field-types)，如果你想知道更多關於 Model fields 的事情，或是如何定義其他在此處提到的東西。


那 `def publish(self):` 又是啥？它事實上就是我們之前所提到的 `publish` 方法。 `def` 表示這是一個 函數/方法 `publish` 就是這個方法的名稱。如果你喜歡，你可以改變它。在此處我們用小寫與底線（取代空白）來作為它的命名規則（就是說如果你想要有一個可以計算平均價錢的方法你可以將名稱取為 `calculate_average_price` ）。

方法通常會 `return(回傳)` 一些東西。這裡有個在 `__str__` 方法中的範例。在這個情境下，當我們呼叫 `__str__()` 我們將得到關於網誌標題的一組文字 (**string**)。

如果對於 model 還有什麼不清楚的，馬上問你的教練！我們知道這滿複雜的，特別是你同時學了物件與函數。但希望這個東西現在開始可以讓你擁有神奇魔法！

### 在資料庫中創建與 model 相關的 table

最後一步是把我們的新 model 加進我們的資料庫 (database)。這很輕鬆，就輸入 `python manage.py syncdb` 即可，看起來會像這樣：

    (myvenv) ~/djangogirls$ python manage.py syncdb
    Creating tables ...
    Creating table blog_post
    Installing custom SQL ...
    Installing indexes ...
    Installed 0 object(s) from 0 fixture(s)

看到這個 Post model 的感覺真好啊對吧？進入下一個章節看看你的網誌長怎樣吧！
