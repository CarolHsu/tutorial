# 安裝 Django

> 部分章節是來自怪咖女孩 Carrots (http://django.carrots.pl/)

> 部分章節是來自 [django-marcador
tutorial](http://django-marcador.keimlink.de/) licensed under Creative Commons
Attribution-ShareAlike 4.0 International License. The django-marcador tutorial
is copyrighted by Markus Zapke-Gründemann et al.


## 虛擬環境

在我們安裝 Django 之前，我們會讓妳安裝一個超有用的工具，這可以讓你電腦中的 coding 環境保持乾淨。也可以跳過這個步驟，但是我們高度建議你不要 - 用最好的安裝方式起手可以節省你未來碰到許多麻煩的時間！

所以我們來創建一個 **虛擬環境(virtual environment)** 吧（也拼做 *virtualenv*）。這會將你的 Python/Django 獨立為一個專案形態，表示你在一個網站專案所做的任何改變都不會影響到你同時在進行的其他網站專案，超乾淨的對吧！

你所需要做的事就是找到一個目錄去創建 這個 `virtualenv`；舉例而言，你的家目錄 (`/home`)，在 Windows 環境下會是 `C:\Users\Name\` （`Name` 會是你目前登入的使用者名稱）。

在這個教程中我們會在你的家目錄下使用一個新目錄 `djangogirls` ：

    mkdir djangogirls
    cd djangogirls

我們會將會創建一個虛擬環境叫做 `myvenv`。這個指令基本的格式如下：

    python -m venv myvenv


### Windows

創建一個新的 `virtualenv`，你需要打開終端機（我們已經在前面一些章節中告訴過你了 - 記得嗎？），並且執行 `C:\Python\python -m venv venv`。這會看起來像這樣

    C:\Users\Name\djangogirls> C:\Python34\python -m venv myvenv

`C:\Python34\python` 是你之前安裝 Python 的路徑，而 `myvenv` 則是你的 `virtualenv` 的名稱。你可以取自己喜歡的名稱，不過必須要是小寫並且沒有其他空白。保持名稱簡短是好主意 - 因為你將會常常提起它！


### Linux and OS X

在 Linux 與 Mac 系統創建一個 `virtualenv` 就是很簡單的執行一下 `python3 -m venv myvenv`。看起來像這樣：

    ~/djangogirls$ python3 -m venv myvenv

`myvenv` 則你的 `virtualenv` 名稱。你可以取自己喜歡的名稱，不過必須要是小寫並且沒有其他空白。保持名稱簡短是好主意 - 因為你將會常常提起它！

> __小提示:__ 在 Ubuntu 14.04 下初始化虛擬環境目前會給你以下的錯誤訊息：

>     Error: Command '['/home/eddie/Slask/tmp/venv/bin/python3', '-Im', 'ensurepip', '--upgrade', '--default-pip']' returned non-zero exit status 1

> 將指令改為 `virtualenv` 可以避免掉這個問題

>     ~/djangogirls$ sudo apt-get install python-virtualenv
>     ~/djangogirls$ virtualenv myvenv


## 在虛擬環境下工作

以上的指令會創建一個叫做 `myvenv` 的目錄（或是你自己決定的任何名稱），裡面就是我們的虛擬環境。我們現在想要做的就是把這個虛擬環境執行起來：

    C:\Users\Name\djangogirls> myvenv\Scripts\activate

在 Windows 上, 或者:

    ~/djangogirls$ source myvenv/bin/activate

在 OS X 與 Linux 上.

記得，如果你取了自己喜歡的名稱，就把指令中的 `myvenv` 代換掉！

> __小提示:__ 有時候你系統中或許不支援 `source` 指令，在這個狀況下你可以使用以下方式：

>     ~/djangogirls$ . myvenv/bin/activate


當你看到你的終端機的命令提示字元看起來像是下面這樣的時候，你就知道你現在是在 `virtualenv` 中：

    (myvenv) C:\Users\Name\djangogirls>

或這樣:

    (myvenv) ~/djangogirls$


`(myvenv)` 總是會出現！

當你在虛擬環境下工作時， `python` 會自動切換到目前所使用的版本，所以你就可以用 `python` 而不需要再輸入 `python3`。

好了，我們已經有了所有相關的套件了，我們終於可以安裝 Django 了！


## 安裝 Django

現在你應該已經啟動了你的 `virtualenv`，你可以用 `pip` 來安裝 Django。在終端機底下，執行 `pip install django==1.6.6` （注意噢，我們是使用雙等號： `==`）。

    (myvenv) ~$ pip install django==1.6.6
    Downloading/unpacking django==1.6.6
    Installing collected packages: django
    Successfully installed django
    Cleaning up...

> 如果當你在 Ubuntu 12.04 下呼叫 `pip` 時出現錯誤訊息，請執行 `python -m pip install -U --force-reinstall pip` 去修復這個 pip 在 virtualenv 下的安裝問題。

這就是全部了！你現在（終於）準備好去創建一個 Django 應用程式！但在這之前，你需要一個好的軟體讓你可以好好寫程式...
