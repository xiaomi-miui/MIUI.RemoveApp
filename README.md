# MIUI.RemoveApp

MIUI8で使わなそうなAppを削除する

## 稼働環境
MIUI8端末  
以下の端末で動作確認済み

* MiMax 32GB
* Redmi Note 3 Pro

Bootloaderアンロックをして、カスタムリカバリTWRPを導入しておく

## 削除するApp
削除するAppは独断と偏見による

* Contacts  
/system/priv-app/Contacts/Contacts.apk  
ContactsX Freeを使ってます
* Browser  
/system/priv-app/Browser/Browser.apk  
Chrome Betaでいいでしょう
* Gallery  
/system/priv-app/MiuiGallery/MiuiGallery.apk  
Google Photosでいいでしょう
* Mail  
/system/app/Email/Email.apk  
K-9 Mailでいいでしょう
* Explorer  
/system/app/FileExplorer/FileExplorer.apk  
X-plore File Managerでいいでしょう
* Notes  
/system/app/Notes/Notes.apk  
Quipでいいでしょう

## updater-script
updater-scriptはこんな感じ

```
ui_print("");ui_print("Delete Apps ...");show_progress(1.0,0);ui_print("Mounting system...");run_program("/sbin/mount", "/system");set_progress(0.1);ui_print("Deleting priv-app ...");ui_print("Deleting Contacts ...");delete("/system/priv-app/Contacts/Contacts.apk");ui_print("Deleting Browser ...");delete("/system/priv-app/Browser/Browser.apk");ui_print("Deleting Gallery ...");delete("/system/priv-app/MiuiGallery/MiuiGallery.apk");ui_print("Deleting app ...");ui_print("Deleting Mail ...");delete("/system/app/Email/Email.apk");ui_print("Deleting Explorer ...");delete("/system/app/FileExplorer/FileExplorer.apk");ui_print("Deleting Notes ...");delete("/system/app/Notes/Notes.apk");set_progress(0.9);ui_print("Unmounting system...");run_program("/sbin/umount", "/system");set_progress(1.00);ui_print("Complete!");
```