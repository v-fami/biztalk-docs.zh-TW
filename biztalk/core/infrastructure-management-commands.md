---
title: "基礎結構管理命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f1a88c-19fc-4384-b6bb-f95962a32921
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae58ea03f394b0fe8b7223bdd810dbc72ccb2472
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="infrastructure-management-commands"></a>基礎結構管理命令
BAM 管理 (BM) 公用程式組態命令可讓您取得及更新 BAM 組態。  
  
-   取得組態： 取得 BAM 組態檔。  
  
-   更新設定： 更新 BAM 組態。  
  
-   取得變更： 列出 BAM 基礎結構的變更。  
  
-   get defxml： 取得包含 BAM 主要匯入資料庫中的所有成品的檔案。  
  
> [!NOTE]
>  您可以藉由啟用任何 BM 公用程式命令的追蹤**-追蹤： 在 &#124; 關閉**切換參數。 使用追蹤參數會覆寫組態檔中的追蹤設定。 此參數可以搭配任何一般 BM 命令使用。  
  
> [!NOTE]
>  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="get-config-command"></a>get-config 命令  
 **使用方式**  
  
 **bm.exe get-config-FileName:\<輸出檔 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|檔案名稱：\<輸出檔 >|組態檔的儲存路徑和名稱。|  
|伺服器：\<伺服器 >|選擇性： 取得設定的伺服器名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 取得設定的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 擷取 BAM 組態 XML，並將它儲存在指定的檔案中。 **Get-config**命令不會覆寫現有的檔案。  
  
 **範例**  
  
```  
bm.exe get-config -FileName:MyConfig.xml  
bm.exe get-config -FileName:BAMConfiguration.xml -Server:OrdersServer  
```  
  
## <a name="update-config-command"></a>update-config 命令  
 **使用方式**  
  
 **bm.exe 更新-config-FileName:\<組態檔 >**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|檔案名稱：\<組態檔 >|用於更新 BAM 基礎結構的組態檔所在路徑和名稱。|  
  
 從含有 BAM 組態 XML 的檔案來更新本機電腦上的組態。 您可以加入目前組態中不存在的伺服器和資料庫名稱。 變更已部署動態基礎結構的伺服器或資料庫名稱會發生錯誤，且 bm.exe 將報告錯誤。  
  
 如果您修改檔案所傳遞之警示的檔案放置位置， 就必須重新啟動 SQL Notifications Services。 如果 NS 服務未重新啟動，將會繼續傳遞警示至原始檔案放置位置。  
  
 在 BAM 組態檔中修改底下這一行即可變更檔案放置位置。  
  
 \<屬性名稱 ="FileDropUNC">\\\\< 電腦名稱\>\alerts\</Property >  
  
 如需更新參照的適當步驟，請參閱[備份和還原 BizTalk Server](../core/backing-up-and-restoring-biztalk-server.md)。  
  
> [!IMPORTANT]
>  如果您已設定 BAM 警示，而在執行 update-database 命令時使用了不含 alerts 區段的 BAM 組態檔，則因 bm.exe 會覆寫組態，以致警示將不再發生作用。  
  
 **範例**  
  
```  
bm.exe update-config -FileName:MyConfig.xml  
```  
  
## <a name="get-changes-command"></a>get-changes 命令  
 **使用方式**  
  
 **bm.exe get 變更 [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|伺服器：\<伺服器 >|選擇性： 在 BAM 主要匯入資料庫所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 如果未指定的名稱，bm.exe 會使用預設名稱 BamPrimaryImport。|  
  
 取得 BAM 主要匯入資料庫套用的變更清單。 使用此命令可以稽核 BAM 基礎結構所做的變更。 此命令會傳回下列資訊：  
  
 從事變更的命令類型，以及套用變更所依據的檔案。  
  
 套用變更的使用者。  
  
 已變更的活動。  
  
 已變更的檢視。  
  
 **範例**  
  
```  
bm.exe get-changes  
```  
  
 命令的輸出  
  
 \#1： 部署 c:\bam\ordermanagement.xml  
  
 By domain\user at 12/30/2005 8:17:08 PM (v3.5.1536.0).  
  
 活動: [ordermgmt]  
  
 檢視： SalesManager  
  
## <a name="get-defxml-command"></a>get-defxml 命令  
 **使用方式**  
  
 **bm.exe get defxml-FileName:\<輸出檔 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|檔案名稱：\<輸出檔 >|用來儲存定義的檔案所在路徑和名稱。|  
|伺服器：\<伺服器 >|選擇性： 定義取得來源的伺服器名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 定義取得來源的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 從 BAM 主要匯入資料庫擷取所有成品，然後另存為 XML 檔案。 此命令不會覆寫現有的檔案。  
  
 **範例**  
  
```  
bm.exe get-defxml -FileName:BAMDefinition.xml  
bm.exe get-defxml -FileName:MyDef.xml -Server:MyServer -Database:MyPI  
```  
  
## <a name="see-also"></a>另請參閱  
 [BAM 管理公用程式](../core/bam-management-utility.md)