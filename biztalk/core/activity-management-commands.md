---
title: "活動管理命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34db54f3-4116-49de-880b-c9891a38d2e7
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d90c5f394ed32b68f4f9b747c580fac02e22a8ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="activity-management-commands"></a>活動管理命令
BAM 管理公用程式活動管理命令可讓您使用已部署的活動。  
  
-   取得活動： 取得已部署的活動清單。  
  
-   移除活動： 將活動中移除。  
  
-   get activitywindow： 取得活動的持續時間。  
  
-   設定 activitywindow： 設定活動的活動持續時間。  
  
-   取得索引： 取得索引的清單。  
  
-   建立索引： 建立新的索引。  
  
-   刪除索引： 刪除索引。  
  
-   get 封存： 取得封存 」 活動的行為。  
  
-   設定封存： 設定封存 」 活動的行為。  
  
> [!NOTE]
>  您可以藉由啟用任何 BAM 公用程式命令的追蹤**-追蹤： 在 &#124; 關閉**切換參數。 使用追蹤參數會覆寫組態檔中的追蹤設定。 此參數可以搭配任何一般 BAM 命令使用。  
  
> [!NOTE]
>  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="get-activities-command"></a>get-activities 命令  
 **使用方式**  
  
 **bm.exe get 活動 [-檢視：\<檢視名稱 >] [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|名稱：\<活動名稱 >|要移除的活動名稱。|  
|伺服器：\<伺服器 >|選擇性： 要從其中取得活動清單的伺服器名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 要從中取得活動清單的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 列出在執行此命令之電腦上部署的活動。  
  
 **範例**  
  
```  
bm.exe get-activities -View:SalesManagerView  
bm.exe get-activities -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="remove-activity-command"></a>remove-activity 命令  
 **使用方式**  
  
 **bm.exe 移除活動的名稱：\<活動名稱 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|名稱：\<活動名稱 >|要移除的活動名稱。|  
|伺服器：\<伺服器 >|選擇性： 要移除之活動的來源伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 要從中移除活動的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 從 BAM 主要匯入資料庫移除指定的活動。 如果活動有相依檢視，命令將會失敗並報告錯誤。 請先使用 remove-view 命令移除所有相依檢視，然後再度執行 remove-activity 命令。  
  
 **範例**  
  
```  
bm.exe remove-activity -Name:PurchaseOrder  
bm.exe remove-activity -Name:PO -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="get-activitywindow-command"></a>get-activitywindow 命令  
 **使用方式**  
  
 **bm.exe get activitywindow-活動：\<活動名稱 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|活動：\<活動名稱 >|活動的名稱。|  
|伺服器：\<伺服器 >|選擇性： 活動所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 活動所在資料庫的名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 顯示指定活動的持續時間。 這個命令會傳回持續時間的長度以及測量持續時間所用的單位。  
  
 **範例**  
  
```  
bm.exe get-activitywindow -Activity:PurchaseOrder  
bm.exe get-activitywindow -Activity:PO -Server:Ship -Database:ShipDatabase  
```  
  
## <a name="set-activitywindow-command"></a>set-activitywindow 命令  
 **使用方式**  
  
 **bm.exe 組 activitywindow-活動：\<活動名稱 >-TimeLength:\<整數數字 >-TimeUnit： 月份 &#124; 天 &#124;小時 &#124;分鐘 [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|活動：\<活動名稱 >|活動的名稱。|  
|TimeLength:\<整數數字 >|活動的持續時間。|  
|TimeUnit:Month &#124; 天 &#124;小時 &#124;分鐘|持續時間的計量單位。|  
|伺服器：\<伺服器 >|選擇性： 活動所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 活動所在資料庫的名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 設定指定活動的持續時間。  
  
 **範例**  
  
```  
bm.exe set-activitywindow -Activity:PurchaseOrder -TimeLength:6 -TimeUnit:Day  
bm.exe set-activitywindow -Activity:PurchaseOrder -TimeLength:1 -TimeUnit:Month  
```  
  
## <a name="get-index-command"></a>get-index 命令  
 **使用方式**  
  
 **bm.exe get 索引的活動：\<活動名稱 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|活動：\<活動名稱 >|活動的名稱。|  
|伺服器：\<伺服器 >|選擇性： 活動所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 活動所在資料庫的名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 列出已針對指定之活動建立的所有索引。  
  
 **範例**  
  
```  
bm.exe get-index -Activity:PurchaseOrder  
bm.exe get-index -Activity:PurchaseOrder -Server:Ship -Database:ShipDatabase  
```  
  
## <a name="create-index-command"></a>create-index 命令  
 **使用方式**  
  
 **bm.exe 建立-IndexName:\<索引名稱 >-活動：\<活動名稱 >-檢查點：\<checkpoint1 > [，\<checkpoint2 >...][-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|IndexName:\<索引名稱 >|新索引的名稱。|  
|活動：\<活動名稱 >|建立索引的活動名稱。|  
|檢查點：\<checkpoint1 > [，\<checkpoint2 >...]|索引的檢查點清單 (以逗號分隔)。|  
|伺服器：\<伺服器 >|選擇性： 活動所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 活動所在資料庫的名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 使用指定的檢查點，為指定的活動建立索引。  
  
 **範例**  
  
```  
bm.exe create-index -IndexName:Idx1 -Activity:PO -Checkpoint:State,City  
bm.exe create-index -IndexName:Idx2 -Activity:PO -Checkpoint:Amount -Server:S1  
```  
  
## <a name="delete-index-command"></a>delete-index 命令  
 **使用方式**  
  
 **bm.exe delete-IndexName:\<索引名稱 >-活動：\<活動名稱 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|IndexName:\<索引名稱 >|要刪除之索引的名稱。|  
|活動：\<活動名稱 >|要刪除索引之活動的名稱。|  
|伺服器：\<伺服器 >|選擇性： 活動所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 活動所在資料庫的名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 從指定的活動刪除具有指定名稱的指定索引。  
  
 **範例**  
  
```  
bm.exe delete-index -IndexName:Idx1 -Activity:PO  
bm.exe delete-index -IndexName:Idx2 -Activity:PO -Server:S1 -Database:BamPI1  
```  
  
## <a name="set-archive-command"></a>set-archive 命令  
 **使用方式**  
  
 **bm.exe get 封存-活動：\<活動 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|活動：\<活動名稱 >|活動的行為是要顯示的名稱。|  
|伺服器：\<伺服器 >|選擇性： 活動所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 活動所在資料庫的名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 取得指定的活動，封存套件的行為是否封存的封裝將會封存 orpurge 活動資料。  
  
 **範例**  
  
```  
bm.exe get-archive -Activity:PurchaseOrder  
```  
  
## <a name="set-archive-command"></a>set-archive 命令  
 **使用方式**  
  
 **bm.exe 組封存-活動：\<活動 >-ShouldArchive:，則為 True [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|活動：\<活動名稱 >|活動的行為是要顯示的名稱。|  
|ShouldArchive: True|如果設為 True，該活動移到封存資料庫。 如果設定為 False，活動會清除。|  
|伺服器：\<伺服器 >|選擇性： 活動所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 活動所在資料庫的名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 設定封存封裝，因此活動資料會移到封存資料庫 」 活動的行為。 根據預設，此行為是設定新部署的活動。  
  
 **範例**  
  
 若要清除的 BAM 活動資料，執行下列作業：  
  
```  
bm.exe set-archive -Activity:PurchaseOrder -ShouldArchive:False  
```  
  
 若要將 BAM 活動資料移到 BAMArchive 資料庫，執行下列作業：  
  
```  
bm.exe set-archive -Activity:PurchaseOrder -ShouldArchive:True  
```  
  
## <a name="see-also"></a>另請參閱  
 [BAM 管理公用程式](../core/bam-management-utility.md)