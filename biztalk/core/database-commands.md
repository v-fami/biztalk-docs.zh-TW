---
title: "資料庫命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60c54131-0793-45a9-822a-554cd4fc05a2
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7ec623c49c90fc0fddcbab7b6ee9b4e7ea0ef58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="database-commands"></a>資料庫命令
BAM 管理公用程式資料庫命令可讓您使用 BAM 資料庫：  
  
-   安裝程式資料庫： 建立 BAM 專屬資料庫。  
  
-   移轉 sql： 移轉您的 BAM 資料庫：  
  
    -   Microsoft SQL server 2008 的 Microsoft SQL Server 2000  
  
    -   Microsoft SQL server 2008 的 Microsoft SQL Server 2005  
  
-   啟用參考： 啟用分散式 BAM 主要匯入資料庫的參考。  
  
-   取得參考： 取得一份分散式 BAM 主要匯入資料庫的參考。  
  
-   停用參考： 停用 BAM 主要匯入資料庫的參考。  
  
> [!NOTE]
>  您可以藉由啟用任何 BM 公用程式命令的追蹤**-追蹤： 在 &#124; 關閉**切換參數。 使用追蹤參數會覆寫組態檔中的追蹤設定。 此參數可以搭配任何一般 BM 命令使用。  
  
> [!NOTE]
>  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="setup-databases-command"></a>setup-databases 命令  
 **使用方式**  
  
 **bm.exe 安裝程式資料庫 ConfigFile:\<組態檔 > [-NSUser:\<通知服務使用者名稱 >] [-NSUserPassword:\<通知服務使用者密碼 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|ConfigFile:\<組態檔 >|建立資料庫所依據的 BAM 組態檔。|  
|NSUser:\<通知服務使用者名稱 >|選擇性： 具有建立資料庫的權限之通知服務使用者的使用者識別碼。|  
|NSUserPassword|選擇性： 指定之通知服務使用者的密碼。|  
  
 如果組態檔中描述的資料庫 (BAM 主要匯入、BAM 星狀結構描述、BAM 封存、BAM 分析和警示) 不存在，會建立所有資料庫。 資料庫建立之後，命令即建立關聯的 BAM 中繼資料資料表和預存程序。  
  
 如果設定 BAM 警示，則 NSUser 和 NSUserPassword 皆為必要參數。 如果沒有在命令列指定 NSUserPassword，bm.exe 會提示您輸入密碼。  
  
> [!NOTE]
>  命令完成之後，追蹤記錄中可能會有來自 AlertModule 的例外狀況：  
>   
>  「指定的帳戶是資料庫擁有者。 資料庫擁有者永遠可以存取檢視，而且無法加入檢視或從檢視移除。」  
>   
>  此外，您可能還會看到 NotificationServices #19001 事件提出的警告。  
>   
>  如果命令執行期間沒有回報錯誤，您就可以放心地忽略這些通知事項。  
  
> [!IMPORTANT]
>  如果您已設定 BAM 警示，而在執行 setup-database 命令時使用了不含 alerts 區段的 BAM 組態檔，則因 bm.exe 會覆寫組態，以致警示將不再發生作用。  
  
 若要安裝 BAM 資料庫，您必須對裝載 BAMPrimaryImport、BAMStarSchema 和 BAMArchive 資料庫的 Microsoft SQL Server 擁有系統管理員權限。 若要安裝 SQL Notification Services 資料庫，您必須擁有系統管理員權限，並且隸屬於本機系統管理員群組及任何其他已設定的系統管理員群組 (例如 BTS Admins 群組)。  
  
 **範例**  
  
```  
bm.exe setup-databases -ConfigFile:BamConfiguration.xml  
bm.exe setup-databases -ConfigFile:cfg.xml -NSUser:domain\user1  
```  
  
## <a name="migrate-sql-command"></a>migrate-sql 命令  
 **使用方式**  
  
 **bm.exe 移轉 sql-從： sql2000-至： sql2008 [-NSUser:\<通知服務使用者名稱 >] [-NSUserPassword:\<通知服務使用者密碼 >] [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 \-或者-  
  
 **bm.exe 移轉 sql-從： sql2005-至： sql2008 [-NSUser:\<通知服務使用者名稱 >] [-NSUserPassword:\<通知服務使用者密碼 >] [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|從： sql2000|指定從 Microsoft SQL Server 2000 資料庫進行轉換。|  
|若要： sql2008|指定轉換到 Microsoft SQL Server 2008 資料庫。|  
|從： sql2005|指定您想要從 Microsoft SQL Server 2005 資料庫進行轉換。|  
|若要： sql2008|指定轉換到 Microsoft SQL Server 2008 資料庫。|  
|NSUser:\<通知服務使用者名稱 >|選擇性： 有建立資料庫的權限之通知服務使用者的使用者識別碼。|  
|NSUserPassword|選擇性： 指定通知服務使用者的密碼。|  
|伺服器：\<伺服器 >|選擇性： 將轉換的資料庫所在的伺服器名稱。 伺服器和裝載 Microsoft SQL Server 2008 資料庫的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 然後命名的轉換的資料庫。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 將 BAM 基礎結構從 Microsoft SQL Server 2000 或 Microsoft SQL Server 2005 移轉至 Microsoft SQL Server 2008。 從 Microsoft SQL Server 2000 或 Microsoft SQL Server 2005 中將您的資料庫伺服器和 Analysis server 升級至 Microsoft SQL Server 2008 之後，請使用此命令。  
  
 如果設定 BAM 警示，則 NSUser 和 NSUserPassword 皆為必要參數。 如果沒有在命令列指定 NSUserPassword，bm.exe 會提示您輸入密碼。  
  
 若要移轉 SQL Server Notification Services 資料庫，您必須擁有系統管理員權限，並且隸屬於本機系統管理員群組及任何其他已設定的系統管理員群組 (例如 BTS Admins 群組)。  
  
> [!NOTE]
>  如果您收到錯誤訊息 「 錯誤： 無法在電腦上啟動服務 NS$ BAMAlerts '\<電腦名稱 >'。 服務並未及時回應啟動或控制要求」，請嘗試手動重新啟動服務。 如果 SQL Server 在移轉期間非常忙碌，可能無法重新啟動服務。  
  
> [!NOTE]
>  若要在有安裝 Notification Services 的電腦上執行 migrate-sql 命令，您必須隸屬於該電腦上的本機系統管理員群組。  
  
 **範例**  
  
```  
bm.exe migrate-sql -From:sql2000 -To:sql2008 -NSUser:domain\user1  
bm.exe migrate-sql -From:sql2000 -To:sql2008 -Server:MyServer -Database:db1  
```  
  
```  
bm.exe migrate-sql -From:sql2005 -To:sql2008 -NSUser:domain\user1  
bm.exe migrate-sql -From:sql2005 -To:sql2008 -Server:MyServer -Database:db1  
```  
  
## <a name="enable-reference-command"></a>enable-reference 命令  
 **使用方式**  
  
 **bm.exe 啟用參考 TargetServer:\<目標伺服器 >-TargetDatabase:\<目標資料庫 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|TargetServer:\<目標伺服器 >|啟用參考的對象伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。|  
|TargetDatabase:\<目標資料庫 >|啟用參考的對象資料庫的名稱。|  
|伺服器：\<伺服器 >|選擇性： 目標伺服器和資料庫啟用參考的伺服器名稱。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 目標伺服器和資料庫啟用參考的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 啟用其他分散式 BAM 主要匯入資料庫的參考。 這可讓您從目前的資料庫訂閱目標 BAM 主要匯入資料庫上的檢視和活動中繼資料。 藉此即可瀏覽分散式活動。  
  
 您可以將目標伺服器指定為 SQL Server 的執行個體，例如 'mymachine2\myinstance'。  
  
 **範例**  
  
```  
bm.exe enable-reference -TargetServer:MySrv -TargetDatabase:BamPrimaryImport  
bm.exe enable-reference -TargetServer:s2 -TargetDatabase:db1 -Server:s1  
```  
  
## <a name="get-references-command"></a>get-references 命令  
 **使用方式**  
  
 **bm.exe get 參考 [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|伺服器：\<伺服器 >|選擇性： 若要取得的參考清單所在的伺服器名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 要取得的參考清單上的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 列出執行此命令的電腦已啟用的參考。  
  
 **範例**  
  
```  
bm.exe get-references  
bm.exe get-references -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="disable-reference-command"></a>disable-reference 命令  
 **使用方式**  
  
 **bm.exe 停用參考 TargetServer:\<目標伺服器 >-TargetDatabase:\<目標資料庫 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|TargetServer:\<目標伺服器 >|停用參考的對象伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。|  
|TargetDatabase:\<目標資料庫 >|停用參考的對象資料庫的名稱。|  
|伺服器：\<伺服器 >|選擇性： 在它會參考到目標伺服器和資料庫要停用伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 在它會參考到目標伺服器和資料庫要停用資料庫的名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 停用目標伺服器上其他分散式 BAM 主要匯入資料庫的參考。  
  
 您可以將目標伺服器指定為 SQL Server 的執行個體，例如 'mymachine2\myinstance'。  
  
 **範例**  
  
```  
bm.exe disable-reference -TargetServer:MySrv -TargetDatabase:BamPI  
bm.exe disable-reference -TargetServer:s2 -TargetDatabase:db1 -Server:s1  
```  
  
## <a name="see-also"></a>另請參閱  
 [BAM 管理公用程式](../core/bam-management-utility.md)