# Git 常用指令


<!--more-->
## 設定
### Git 全局設置
設置使用者，Email 
<!-- {{< admonition example >}} -->
<!-- {{< /admonition >}} -->
```git
git config --global user.name "your gitlab username"
git config –global user.email "your email"
```

### 新建代碼庫
```git
git init
```

## 拉回 (PULL)
### 複製既有遠端代碼庫
```git
git clone <url>
```
{{< admonition example >}}
$ git clone https://192.168.1.100/xxx_group/abc.git 

{{< /admonition >}}

## 提交 (PUSH)
### 將本地已有項目提交

```git
git add .
git commit -m "My first commit"
git remote add origin <url>       **(首次新建)**
git push origin master            **(後續使用此提交即可)**
```
## 確認、查看

### 確認add狀態
```git
git status
```

### 確認提交紀錄
```git
git log
```

### 查看修改檔案差異
```git
git diff
```

## 分支 (Branch)
### 建立分支
```git
git branch 分支名稱
```

### 查看分支清單
* 加上 **-r**  =>  顯示遠端分支
* 加上 **-a**  =>  顯示遠端與本地端分支
```git
git branch
git branch -r
git branch -a
```

### 切換分支
```git
git checkout 分支名稱
```

### 刪除分支
```git
git branch -d 分支名稱
```

### 修改分支名稱
```git
git branch -m 舊分支名稱 新分支名稱
```

### 合併分支
```git
git merge 分支名稱       **(將分支名稱與"當前"分支合併)**
```

## 回復版本
**git checkout**
```git
git checkout f9977272       **(將版本"移動"至此commitID)**
```

**git reset**
* 加上 -soft  =>  工作目錄跟暫存區的檔案不會被丟掉
* 加上 -hard  =>  工作目錄及暫存區的檔案都會丟掉
```git
git reset f9977272       **(將版本回復至此commitID)**
git reset -soft f9977272
git reset -hard f9977272
```

{{< admonition tip >}}
**如何把丟掉檔案找回?**

Ans:下git reflog指令查找id，再reset
```git
git reflog
git reset commitID
```

* **查找功能使用checkout**

* **返回並且清除紀錄使用reset**
{{< /admonition >}}

## 推薦Git學習網站
1. [連猴子都能懂的Git入門指南](https://backlog.com/git-tutorial/tw/)     <深入淺出，圖文並茂>
