你好

在本地端電腦產生SSH的key
ssh-keygen -t rsa -b 4096 -C "email"

輸入指令後會問以下問題

    輸入儲存位置
    輸入密碼，可為空
    再次輸入密碼，可為空

建立 SSH key 後要將其加入代理，好讓之後可以使用

確認 ssh-agent 是否正常運行
eval "$(ssh-agent -s)"

將密鑰加入 ssh-agent 內
ssh-add ~/.ssh/id_rsa


顯示剛剛生成的key
cat ~/.ssh/id_rsa.pub

最後將KEY貼到github裡
Github 點頭像-> Settings -> Personal settings -> SSH and GPG keys

測試ssh是否成功
ssh -T git@github.com

設定遠端儲存庫
git remote add origin （庫的SSH地址）      例如 git remote add origin git@github.com:Lyciih/test.git 
（origin是後面地址的別名，這樣以後究不用打很長。也不一定要取origin，可以隨自己喜好）

---
本地端 新資料夾

初始化
git init

有任何修改及新增檔案都要 git add .  或 git add 檔名

查詢目前狀態 git status

將修改正式保存 git commit -m "本次資訊（隨便打或是說明這次做了什麼）"
---

第一次push
git push -u origin main （-u 是當成功時，把後面的地址跟分支名記錄下來，下次就不用再打）

之後只要
git push 

若要強制就加 -f

查詢現有分支 git branch

刪除遠端分支
git push origin --delete 分支名
刪除本地分支
git branch -d 分支名

本地分支改名
git branch -m 舊名 新名

將本地檔案更新成跟github上一樣
git pull (可加 origin 分支名)

git pull --rebase    參數表示「內容抓下來之後請使用 Rebase 方式合併。

如果你在github上新建一個倉庫並且含有Readme，然後在本地新開一個資料夾並且 git init，那你要先git pull才能push，但是因為兩邊歷史紀錄不同，不能直接pull，所以在pull時要加上參數
--allow-unrelated-histories
以下是範例
git pull origin main --allow-unrelated-histories

https://meet.google.com/dyt-rymb-wuj
