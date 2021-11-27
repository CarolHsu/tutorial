# 你的第一個 Django 專案！

> 部分章節是來自怪咖女孩 Carrots (http://django.carrots.pl/)

> 部分章節是來自 [django-marcador
tutorial](http://django-marcador.keimlink.de/) licensed under Creative Commons
Attribution-ShareAlike 4.0 International License. The django-marcador tutorial
is copyrighted by Markus Zapke-Gründemann et al.

我們要開始來做一個簡單的 blog 了！

要新增一個 Django 專案的第一步。基本上，這代表我們將會運行由 Django 提供的某些腳本，它會幫我們建立一個 Django 專案的基本架構：一堆我們待會會用上的檔案夾和檔案。

這些檔案夾和檔案們的命名對 Django 來說是非常重要的。你不應該重新命名這些我們剛剛弄出來的檔案。將這些檔案移動到別的地方也不是好主意。為了可以容易找到重要的事物，Django 必須保持這些檔案結構。

在終端機下你應該執行（應該記得吧，你不需要再輸入 `(myvenv) ~/djangogirls$` 囉）：

> 記得要在虛擬環境裡執行所有動作。如果你的終端機命令列沒有看到前綴 `(myvenv)` 時，你就需要重新喚起你的虛擬環境。我們已經在 _安裝 Django__ 這章的 __在虛擬環境下工作__ 中解釋過如何做囉。

在 Windows 下執行：

    (myvenv) ~/djangogirls$ python myvenv\Scripts\django-admin.py startproject mysite .

或者在 Linux 或 Mac OS 下執行：

    (myvenv) ~/djangogirls$ django-admin.py startproject mysite .

`django-admin.py` 是一個可以替你創建資料夾與檔案的腳本(script)。你現在應該有像是下面這樣的資料目錄了：

    djangogirls
    ├───manage.py
    └───mysite
            settings.py
            urls.py
            wsgi.py
            __init__.py

`manage.py` 是個協助管理這個網站的腳本。有了它我們將可以在我們的電腦上叫起一個 web server，不需安裝其他的東西。

至於 `settings.py` 則包含了你的網站中的各種配置。

記得當我們談過一個郵差如何檢查信要送到哪裡嗎？ `urls.py` 就是一個有很多範例的清單，被 `urlresolver` 所用。

現在讓我們先忽略其他檔案 - 我們不會改變那些。唯一需要記得的一件事就是不要不小心刪了它們 XD


## 改變設定

我們來在 `mysite/settings.py` 中做點改變。用你早先安裝的程式碼編輯器打開這個檔案。

如果我們網站中有正確的時間是件好事。到 http://en.wikipedia.org/wiki/List_of_tz_database_time_zones 這個維基頁面去複製你所在時區吧（TZ - time zone）。（例如這裡是 `Asia/Taipei` ）

你應該可以找到幾行包含了 `USE_TZ` 與 `TIME_ZONE`，像這樣修改它，代入你的時區的資料來源 `Asia/Taipei` ：

    USE_TZ = False
    TIME_ZONE = 'Asia/Taipei'

## 設定資料庫

這裡有好幾種不同的資料庫可以為你的網站儲存資料。我們將使用內定的那個， `sqlite3`。

這已經在你的 `mysite/settings.py` 檔案中設定好了：

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.sqlite3',
            'NAME': BASE_DIR / 'db.sqlite3',
        }
    }

要為我們的部落格創建一個資料庫，我們要在終端機下執行這個： `python manage.py migrate` (我們需要在已經建好了 `manage.py` 檔的 `djangogirls` 目錄下)。如果一切順利，你應該可以看到像這樣的東西：

    (myvenv) ~/djangogirls$ python manage.py migrate
    Creating tables ...
    Creating table django_admin_log
    Creating table auth_permission
    Creating table auth_group_permissions
    Creating table auth_group
    Creating table auth_user_groups
    Creating table auth_user_user_permissions
    Creating table auth_user
    Creating table django_content_type
    Creating table django_session

    You just installed Django's auth system, which means you don't have any superusers defined.
    Would you like to create one now? (yes/no): yes
    Username (leave blank to use 'Name'):
    Email address: admin@example.com
    Password:
    Password (again):
    Superuser created successfully.
    Installing custom SQL ...
    Installing indexes ...
    Installed 0 object(s) from 0 fixture(s)

它會問你想不想創建一個 *超級使用者(superuser)* - 就是一個可以控制這個網站上所有功能的使用者。輸入 `yes` ，按下 Enter 並且輸入你的使用者名稱（小寫無空白），email 帳號以及密碼（必填）。記住這組帳密！我們稍後會用到。

這樣我們就完成了！現在是時候叫起 web server 然後看看我們的網站怎麼樣！

你一樣需要在這個包含了 `manage.py` 檔案的 `djangogirls` 目錄下。在終端機下，我們可以開始用 `python manage.py runserver` 來叫起我們的 web server 了：

    (myvenv) ~/djangogirls$ python manage.py runserver

至此，你需要做的就是檢查你的網站是不是有運作起來 - 打開你的瀏覽器（火狐，Crhome, Safari 甚至是 IE 或是任何你有在用的）然後輸入這個網址：

    http://127.0.0.1:8000/

你可以再次停掉這個 web server 了（就是說在命令提示字元下輸入其他指令），藉由按下 CTRL+C - Control 和 C 鍵一起按下去。

恭喜恭喜！你剛剛就建好了你的第一個網站，並且用 web server 運作起來了！好 Django 不學嗎？


![It worked!](images/it_worked2.png)

準備好進入下一階段了嗎？是時候加入一些內容了！
