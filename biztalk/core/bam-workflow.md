---
title: BAM 工作流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- monitoring business activities [BAM], collecting business data
- XML files
- orchestrations, XML files
- business activities, business data
- infrastructure, managing [BAM]
- business activities, monitoring
- monitoring business activities [BAM], monitoring flow
- managing [BAM], infrastructure
- monitoring business activities [BAM], viewing business data
- managing [orchestrations], mapping XML to orchestrations
ms.assetid: 8b4ae145-3e16-4bb8-bfba-09b9f666218d
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19356d6191963ec441f0b85c0e987c8515dcf1f4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232038"
---
# <a name="bam-workflow"></a>BAM 工作流程
下圖顯示四個與「商務活動監控」共同工作的使用者角色，以及其所使用的工具。  
  
 ![](../core/media/ebiz-tut-bamworkflow.gif "ebiz_tut_bamworkflow")  
BAM 角色  
  
 下列步驟針對如何使用「商務活動監控」，提供其工作流程的高階概觀。  
  
## <a name="specifying-the-business-data-to-collect"></a>指定要收集的商務資料  
 商務資料會以下列方式收集：  
  
-   商務分析師使用「BAM 活動精靈」來指定所有商務使用者所要收集的資料。  
  
-   商務分析師使用「BAM 檢視精靈」來定義每個商務使用者類別的檢視。  
  
-   完成定義後，他會在名為「BAM 定義活頁簿」的 Microsoft® Excel 活頁簿中儲存活動和檢視。  
  
-   商務分析師可以將「BAM 定義活頁簿」匯出為 XML。  
  
-   系統管理員和開發人員則使用 XML 來執行各自的角色。  
  
-   使用 「 BAM 定義活頁簿的指示都位於[定義商務活動和在 Excel 中的檢視](../core/defining-business-activities-and-views-in-excel.md)。  
  
## <a name="managing-the-bam-infrastructure"></a>管理 BAM 基礎結構  
 商務分析師定義過所需的 BAM 檢視後，系統管理員會使用命令列工具「BAM 管理公用程式」(BM.EXE)，從「BAM 定義活頁簿」或由活頁簿所匯出的 XML 中部署 BAM 基礎結構。  
  
 BAM 管理公用程式會動態建立支援 BAM 檢視所需的資料表、觸發程序、DTS 封裝和 OLAP Cube。  
  
 每當商務分析師定義不同的 BAM 檢視，或變更現有的 BAM 檢視時，系統管理員都必須重新部署 BAM 定義活頁簿。  
  
## <a name="mapping-the-xml-to-an-orchestration"></a>對應 XML 至協調流程  
 商務分析師將「BAM 定義活頁簿」匯出為 XML 後，開發人員會將 XML 檔案匯入至「追蹤設定檔編輯器」。 開發人員則實作商務分析師的資訊需求，將 XML 對應到協調流程。  
  
 使用「追蹤設定檔編輯器」時，開發人員可以執行下列步驟，將 XML 對應到協調流程：  
  
-   將儲存在 BizTalk 管理資料庫 (也稱為組態資料庫) 中的部署組件載入。 部署的組件包含一或多個協調流程，對應至商務分析師在上述「步驟 1」指定的需求。  
  
-   定義要從協調流程中擷取的資料。 若要這麼做，您可以將項目從訊息結構描述和協調流程圖形放置在適當的商務里程碑 (事件) 和資料項目資料夾中。  
  
-   完成後，他會在存放資料庫 (如 Visual SourceSafe) 中，將設定檔儲存為 BizTalk® Server 追蹤 (.btt) 檔案。  
  
 開發人員再將 .btt 檔案部署到測試資料庫，並透過整合測試確認結果。  
  
## <a name="deploying-the-tracking-profile"></a>部署追蹤設定檔  
 使用「追蹤設定檔編輯器」時，系統管理員可以將設定檔部署到一或多個 BizTalk 管理資料庫。  
  
 每當開發人員變更協調流程，或商務使用者需求變更而要追蹤更多資料時，系統管理員都必須使用命令列公用程式 bttdeploy.exe 來重新部署追蹤設定檔。  
  
## <a name="viewing-the-business-data"></a>檢視商務資料  
 商務使用者使用由 BM.exe 公用程式產生的 _LiveData 活頁簿。 每當商務使用者開啟 _LiveData 活頁簿時，都會收到最新版的即時資料，這些資料是收集用來監控商務程序的特定層面。  
  
-   若要檢視定義為即時彙總的資料，商務使用者只需按一下**重新整理**要檢視資料的活頁簿中。  
  
-   如果彙總資料不是即時的，商務使用者可以檢視排程 DTS 封裝在執行時所攝取的商務資料快照集。  
  
-   如果您的組織有協同作業的需求，商務使用者可以從 BAS Web 網站存取即時資料。  
  
## <a name="see-also"></a>另請參閱  
 [在 Excel 中定義商務活動和檢視](../core/defining-business-activities-and-views-in-excel.md)   
 [使用 BAM 監控商務活動](../core/monitoring-business-activities-with-bam.md)