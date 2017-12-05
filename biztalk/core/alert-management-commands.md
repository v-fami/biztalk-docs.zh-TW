---
title: "警示管理命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a96d8de7-a918-4737-aa35-4e1abf6bb08f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f419e7a0019287383080c319961b8a3831d27bb4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="alert-management-commands"></a>警示管理命令
BAM 管理公用程式的警示管理命令可讓您使用已部署的警示。  
  
-   取得警示： 取得已部署的警示清單。  
  
-   移除警示： 移除警示。  
  
-   啟用警示： 可讓檢視上的警示。  
  
-   停用警示： 停用檢視上的警示。  
  
> [!NOTE]
>  您可以藉由啟用任何 BM 公用程式命令的追蹤**-追蹤： 在 &#124; 關閉**切換參數。 使用追蹤參數會覆寫組態檔中的追蹤設定。 此參數可以搭配任何一般 BM 命令使用。  
  
> [!NOTE]
>  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="get-alerts-command"></a>get-alerts 命令  
 **使用方式**  
  
 **bm.exe get 警示 [-檢視：\<檢視名稱\>] [-Server:\<伺服器\>] [-Database:\<資料庫\>]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|檢視：\<檢視表名稱\>|警示清單取得來源的檢視名稱。|  
|伺服器：\<伺服器\>|選擇性： 檢視所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫\>|選擇性： 檢視所在的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 列出執行此命令的電腦上已定義的警示。  
  
 **範例**  
  
```  
bm.exe get-alerts -View:ManagerView  
bm.exe get-alerts -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="remove-alerts-command"></a>remove-alerts 命令  
 **使用方式**  
  
 **bm.exe 移除警示的檢視：\<檢視名稱\>[-Server:\<伺服器\>] [-資料庫：\<資料庫\>]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|檢視：\<檢視表名稱\>|要移除警示的檢視名稱。|  
|伺服器：\<伺服器\>|選擇性： 檢視所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫\>|選擇性： 檢視所在的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 移除指定之檢視上的所有警示。  
  
 **範例**  
  
```  
bm.exe remove-alerts -View:SalesManagerView  
bm.exe remove-alerts -View:Shipments -Server:Ship1  
```  
  
## <a name="enable-alerts-command"></a>enable-alerts 命令  
 **使用方式**  
  
 **bm.exe 啟用警示的檢視：\<檢視名稱\>[-Server:\<伺服器\>] [-資料庫：\<資料庫\>]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|檢視：\<檢視表名稱\>|要啟用警示的檢視名稱。|  
|伺服器：\<伺服器\>|選擇性： 檢視所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫\>|選擇性： 檢視所在的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 啟用指定之檢視上的警示。  
  
 **範例**  
  
```  
bm.exe enable-alerts -View:SalesManagerView  
bm.exe enable-alerts -View:SalesManagerView -Server:s1 -Database:db2  
```  
  
## <a name="disable-alerts-command"></a>disable-alerts 命令  
 **使用方式**  
  
 **bm.exe 停用警示的檢視：\<檢視名稱\>[-Server:\<伺服器\>] [-資料庫：\<資料庫\>]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|檢視：\<檢視表名稱\>|要停用警示的檢視名稱。|  
|伺服器：\<伺服器\>|選擇性： 檢視所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫\>|選擇性： 檢視所在的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 停用指定之檢視上的警示。  
  
 **範例**  
  
```  
bm.exe disable-alerts -View:SalesManagerView  
bm.exe disable-alerts -View:SalesManagerView -Server:s1 -Database:db2  
```  
  
## <a name="see-also"></a>請參閱  
 [BAM 管理公用程式](../core/bam-management-utility.md)