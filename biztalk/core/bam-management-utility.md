---
title: "BAM 管理公用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c55aabe2-f38b-4917-863c-b408a4eef98e
caps.latest.revision: "50"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5374ba63ba8eb4193c3ef4990e8c169646a3528b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="bam-management-utility"></a>BAM 管理公用程式
商務活動監控 (BAM) 定義的管理員可使用 BAM 管理公用程式，來管理和維護 BAM 基礎結構的所有層面。  
  
 您可以使用 BAM 公用程式執行下列工作：  
  
-   使用 BAM 定義以及 BAM 組態 XML 做為輸入項。 BAM 定義 XML 或 XLS 檔案定義所要追蹤和彙總的資料，以及追蹤資料的商務使用者檢視。 BAM 組態 XML 則指定部署基礎結構的地點，例如伺服器名稱、資料庫名稱和資料庫的其他設定。  
  
-   在伺服器上部署執行階段基礎結構，包括 BAM 主要匯入資料庫、BAM 星狀結構描述資料庫、BAM 分析資料庫以及對應的 Data Transformation Services (DTS) 封裝。 執行此步驟時會建立下列項目：  
  
    -   BAM 主要匯入資料庫  
  
    -   BAM 星狀結構描述資料庫  
  
    -   BAM 封存資料庫  
  
    -   BAM 分析資料庫  
  
> [!NOTE]
>  執行 BAM 管理公用程式的電腦，其地區設定必須與建立 BAM 定義以進行部署所使用的地區設定相同，BAM 命令才能正常運作。 例如，如果您執行**get 檢視**命令設定的電腦上採用英文地區設定比對資料庫使用法文地區設定的電腦上您將無法使用傳回的檢視名稱，除非您重設您電腦為法文的地區設定。  
  
 您可以使用 BAM 管理公用程式在伺服器上產生並部署追蹤組態。 BAM 管理公用程式是命令列工具位於\<*安裝路徑*\>\Program Files\Microsoft BizTalk Server\<版本\>\Tracking\BM.exe。  
  
> [!IMPORTANT]
>  若要執行 BAM 管理公用程式，您必須是成員**db_owner** BAM 主要匯入、 BAM 星狀結構描述和 BAM 封存資料庫中的 SQL Server 資料庫角色。 您也必須擁有 BAM 警示資料庫上 sysadmin 權限，如果進行與 BAM 警示相關的任何更新。  
  
> [!NOTE]
>  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。 若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。  
  
## <a name="bam-management-utility-commands"></a>BAM 管理公用程式命令  
 此命令描述使用下列慣例：  
  
-   方括弧 ([]) 代表選擇性參數。  
  
-   角括弧 (<>) 代表必要參數。  
  
-   大括弧 ({}) 代表應從列舉清單中選取的項目。  
  
-   安全性帳戶可能是 NT 群組或個別的 NT 使用者帳戶。  
  
-   BAM 定義檔案可能是 XML 檔案或 BAM Excel 活頁簿檔案 (.xls)。  
  
-   如果沒有提供 BAM 組態檔，則預設為目前資料夾中的 BamConfiguration.xml。  
  
 下列主題包含個別命令的說明：  
  
-   [資料庫命令](../core/database-commands.md)  
  
-   [BAM 定義的部署 (觀察模型) 命令](../core/deployment-of-bam-definition-observation-model-commands.md)  
  
-   [基礎結構管理命令](../core/infrastructure-management-commands.md)  
  
-   [活動管理命令](../core/activity-management-commands.md)  
  
-   [檢視管理命令](../core/view-management-commands.md)  
  
-   [警示管理命令](../core/alert-management-commands.md)  
  
-   [使用者管理命令](../core/user-management-commands.md)  
  
-   [警示訂閱管理命令](../core/alert-subscription-management-commands.md)  
  
-   [攔截器管理命令](../core/interceptor-management-commands.md)  
  
## <a name="displaying-the-bam-management-utility-help"></a>顯示 BAM 管理公用程式說明  
 您使用**/？** 或**協助 BAM 管理公用程式**命令，以顯示 BAM 管理公用程式的說明檔。  
  
#### <a name="to-display-the-help-file-for-the-bam-management-utility"></a>若要顯示 BAM 管理公用程式的說明檔  
  
1.  從命令提示字元，瀏覽至下列目錄： C:\Program Files\Microsoft BizTalk Server\<版本\>\Tracking\\。  
  
2.  型別**bm**或**bm 說明**。  
  
3.  按 ENTER 鍵。