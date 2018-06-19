---
title: 使用者管理命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: feb12226-a4da-4fc5-93a1-aced239f60a9
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16527acda7432b2eea35f0c87bb9d89fff632430
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974076"
---
# <a name="user-management-commands"></a>使用者管理命令
BAM 管理公用程式的警示使用者管理命令可讓您取得、新增及移除使用者。  
  
-   取得帳戶： 取得所有使用者和群組可以存取指定的檢視的清單。  
  
-   新增帳戶： 授與存取指定的使用者或群組的權限，以指定的檢視。  
  
-   移除帳戶： 移除存取權限的使用者或群組，從指定的檢視。  
  
> [!NOTE]
>  您可以藉由啟用任何 BM 公用程式命令的追蹤 **-追蹤： 在 &#124; 關閉**切換參數。 使用追蹤參數會覆寫組態檔中的追蹤設定。 此參數可以搭配任何一般 BM 命令使用。  
  
> [!NOTE]
>  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="get-accounts-command"></a>get-accounts 命令  
 **使用方式**  
  
 **bm.exe get 帳戶-檢視：\<檢視名稱\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|檢視：\<檢視表名稱\>|要列出其帳戶的檢視名稱。|  
|伺服器：\<伺服器\>|選擇性： 要從中擷取帳戶的伺服器名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫\>|選擇性： 要從中擷取帳戶的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 列出可存取特定檢視的所有使用者和群組。  
  
 **範例**  
  
 `bm.exe get-accounts -View:PurchaseOrder`  
  
 `bm.exe get-accounts -View:ShipmentOrder -Server:Ship -Database:ShipDatabase`  
  
## <a name="add-account-command"></a>add-account 命令  
 **使用方式**  
  
 **bm.exe 新增帳戶-AccountName:\<帳戶名稱\>-檢視：\<檢視名稱\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|AccountName:<帳戶名稱|要對其授與權限的帳戶名稱。|  
|檢視：\<檢視表名稱\>|要對其授與權限的檢視名稱。|  
|伺服器：\<伺服器\>|選擇性： 檢視所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫\>|選擇性： 檢視所在的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 授與指定的使用者或群組存取特定檢視的權限。  
  
> [!IMPORTANT]
>  如果您使用即時彙總 (Rta)，使用者會新增與**新增帳戶**命令不會自動授予 SQL Server 登入權限。 如果您使用 RTA，請考慮建立一個 Windows 使用者群組，並在該群組中加入所有需要查看 RTA 檢視的使用者。 然後，授與該群組對裝載 BAM 主要匯入資料庫的 SQL 伺服器擁有明確的 SQL Server 登入權限。  
  
 **範例**  
  
```  
bm.exe add-account -AccountName:john -View:PurchaseOrder  
bm.exe add-account -AccountName:Agents -View:PO -Server:Srv1 -Database:Db2  
```  
  
## <a name="remove-account-command"></a>remove-account 命令  
 **使用方式**  
  
 **bm.exe 移除帳戶-AccountName:\<帳戶名稱\>-檢視：\<檢視名稱\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|AccountName:\<帳戶名稱\>|要移除其檢視存取權限的帳戶名稱。|  
|檢視：\<檢視表名稱\>|要對其移除權限的檢視名稱。|  
|伺服器：\<伺服器\>|選擇性： 檢視所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫\>|選擇性： 檢視所在的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 移除使用者或群組對特定檢視的存取權。 從檢視移除帳戶會從指定檢視所定義的警示移除該帳戶及其所有成員。 如果該帳戶是特定警示的唯一擁有者，則目前的使用者 (admin) 將成為這些警示的新擁有者。  
  
 **範例**  
  
```  
bm.exe remove-account -AccountName:john -View:PurchaseOrder  
bm.exe remove-account -AccountName:Agents -View:PO -Server:Srv1 -Database:Db2  
```  
  
## <a name="see-also"></a>請參閱  
 [BAM 管理公用程式](../core/bam-management-utility.md)