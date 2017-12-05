---
title: "BAM 通知的命令列指令碼服務組態檔 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aa4a460-58f9-439d-af28-0a9cb2288236
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b22607193ed7c345388a6435e2d58c16b8986370
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="bam-command-line-script-for-notification-services-configuration-files"></a>用於處理 Notification Services 組態檔的 BAM 命令列指令碼
系統管理員可使用 ProcessBamNSFiles.vbs 指令碼，以針對 BAM 警示自訂 SQL Server Notification Services 的行為。 使用這個指令碼可以取得 Notification Services 應用程式定義檔 (ADF) 及 Notification Services 組態檔。 而在修改這些檔案後，您也可以利用指令碼套用變更。  
  
 請從 Notification Services 命令提示字元執行指令碼，而不要從一般的命令提示字元執行。 若從一般的命令提示字元執行指令碼，指令碼將無法正確執行。 執行指令碼時，所有的參數皆為必要項。  
  
## <a name="get-command"></a>Get 命令  
 **使用方式**  
  
 **cscript ProcessBamNSFiles-Get\<組態檔路徑\> \<ADF 檔案路徑\>\<主要匯入伺服器\>\<主要匯入資料庫  \>**  
  
|參數|Description|  
|---------------|-----------------|  
|組態檔路徑|指定組態檔的儲存位置和名稱。|  
|ADF 檔案路徑|指定 ADF 檔案的儲存位置和名稱。|  
|主要匯入伺服器|儲存 BAM 主要匯入資料庫之電腦的名稱。|  
|主要匯入資料庫|BAM 主要匯入資料庫的名稱。|  
  
 從 BAM 主要匯入資料庫擷取 Notification Services 組態檔及應用程式定義檔，然後儲存至指定的位置。  
  
## <a name="update-command"></a>Update 命令  
 **使用方式**  
  
 **cscript ProcessBamNSFiles-Update \<configfilepath\> \<組態檔路徑\>\<primaryimport 伺服器\>\<主要匯入資料庫  \>**  
  
|參數|Description|  
|---------------|-----------------|  
|組態檔路徑|指定用於更新 Notification Services 組態資訊的檔案位置和名稱。|  
|ADF 檔案路徑|指定用於更新 ADF 資訊的檔案位置和名稱。|  
|主要匯入伺服器|儲存 BAM 主要匯入資料庫之電腦的名稱。|  
|主要匯入資料庫|BAM 主要匯入資料庫的名稱。|  
  
 呼叫 Notification Services 並將其設定更新為指定檔案中的資訊。 組態檔及 ADF 檔案均儲存於 BAM 主要匯入資料庫。  
  
## <a name="see-also"></a>請參閱  
 [BAM 命令列工具](../core/bam-command-line-tools.md)