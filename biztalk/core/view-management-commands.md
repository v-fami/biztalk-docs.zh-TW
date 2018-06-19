---
title: 檢視管理命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52f25ee3-9bb3-4682-a9ff-cac8c25f58c3
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ced7a9ac58fa0375e3eaefa49832e6c23ba1a73
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975172"
---
# <a name="view-management-commands"></a>檢視管理命令
[BAM 管理] 公用程式檢視管理命令可讓您使用已部署的檢視。  
  
-   取得檢視表： 列出所有已部署的檢視。  
  
-   移除檢視： 移除已部署的檢視。  
  
-   get rtawindow： 在檢視上取得的持續時間。  
  
-   設定 rtawindow： 在檢視上設定的持續時間。  
  
> [!NOTE]
>  您可以藉由啟用任何 BM 公用程式命令的追蹤 **-追蹤： 在 &#124; 關閉**切換參數。 使用追蹤參數會覆寫組態檔中的追蹤設定。 此參數可以搭配任何一般 BM 命令使用。  
  
> [!NOTE]
>  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="get-views-command"></a>get-views 命令  
 **使用方式**  
  
 **bm.exe get 檢視 [-活動：\<活動名稱\>] [-Server:\<伺服器\>] [-Database:\<資料庫\>]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|活動：\<活動名稱\>|要列出其檢視的活動名稱。|  
|伺服器：\<伺服器\>|選擇性： 取得檢視的清單的伺服器名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫\>|選擇性： 取得的檢視清單之資料庫的名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 列出在執行此命令的電腦上部署的檢視。  
  
 **範例**  
  
```  
bm.exe get-views -Activity:PO1  
bm.exe get-views -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="remove-view-command"></a>remove-view 命令  
 **使用方式**  
  
 **bm.exe 移除檢視-名稱：\<檢視名稱\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|名稱：\<檢視表名稱\>|要移除的檢視名稱。|  
|伺服器：\<伺服器\>|選擇性： 要移除其檢視的來源伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫\>|選擇性： 要從中移除其檢視的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 從 BAM 主要匯入資料庫移除指定的檢視。 如果檢視有相依警示，就會一併移除這些警示。  
  
 **範例**  
  
```  
bm.exe remove-view -Name:POView  
bm.exe remove-view -Name:MyView -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="get-rtawindow-command"></a>get-rtawindow 命令  
 **使用方式**  
  
 **bm.exe get rtawindow-檢視：\<檢視名稱\>-活動：\<活動名稱\>Rta:\<RTA 名稱\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|檢視：\<檢視表名稱\>|檢視名稱。|  
|活動：\<活動名稱\>|活動名稱。|  
|Rta:\<RTA 名稱\>|即時彙總名稱。|  
|伺服器：\<伺服器\>|選擇性： 活動所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫\>|選擇性： 活動所在資料庫的名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 顯示指定之即時彙總的持續時間。 這個命令會傳回持續時間的長度以及測量持續時間所用的單位。  
  
 **範例**  
  
```  
bm.exe get-rtawindow -View:ManagerView -Activity:PO -Rta:Rta1  
bm.exe get-rtawindow -View:V1 -Activity:A2 -Rta:R3 -Server:S1 -Database:BamPI  
```  
  
## <a name="set-rtawindow-command"></a>set-rtawindow 命令  
 **使用方式**  
  
 **bm.exe 組 rtawindow-檢視：\<檢視名稱\>-活動：\<活動名稱\>-Name:\<RTA 名稱\>-TimeLength:\<整數數字\>-TimeUnit:Day &#124;小時 &#124;分鐘 [-Server:\<伺服器\>] [-Database:\<資料庫\>]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|檢視：\<檢視表名稱\>|檢視名稱。|  
|活動：\<活動名稱\>|活動名稱。|  
|名稱：\<RTA 名稱\>|即時彙總名稱。|  
|TimeLength:\<整數數字\>|即時彙總的持續時間。|  
|TimeUnit:Month &#124; 天 &#124;小時 &#124;分鐘|視窗持續時間的計量單位。|  
|伺服器：\<伺服器\>|選擇性： 活動所在的伺服器的名稱。 伺服器必須位在相同的網域執行 bm.exe 的電腦。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫\>|選擇性： 活動所在資料庫的名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 設定指定之即時彙總的持續時間。  
  
 **範例**  
  
```  
bm.exe set-rtawindow -View:V -Activity:A -Name:R -TimeLength:5 -TimeUnit:Minute  
bm.exe set-rtawindow -View:V -Activity:A -Name:R -TimeLength:1 -TimeUnit:Hour  
```  
  
## <a name="see-also"></a>請參閱  
 [BAM 管理公用程式](../core/bam-management-utility.md)