---
title: A4SWIFT 清理工具 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- A4SWIFT Cleanup tool
ms.assetid: e694f824-6097-4d60-bc7b-b4f1a40acea0
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b2d0e251bf5e8a4169ff0d86cc6635944ca12e1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="a4swift-cleanup-tool"></a>A4SWIFT 清理工具
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]清理工具可讓您準備伺服器具有[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]在其上安裝適用於新安裝的[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]。 此工具會移除 A4SWIFT 的成品，例如合約、 部門和商務規則引擎 (BRE) 原則，並解除部署組件。 執行此工具可讓您避免手動移除許多 A4SWIFT 成品，以及解決問題的可能參考其他組件中解除部署組件。  
  
 當您執行 「 清除 」 工具時，您可以選擇離開 A4SWIFT 的電腦 （預設值） 或解除安裝 A4SWIFT 安裝之後移除成品。 您應該執行此工具，然後再解除 A4SWIFT 安裝。  
  
> [!CAUTION]
>  請勿在生產環境中使用 A4SWIFT 清理工具。 此工具是用於在單一伺服器開發環境中，不能在多伺服器部署。  
  
> [!NOTE]
>  根據預設，「 清理 」 工具不適用於英文的任何其他語言。 不過，使 「 清理 」 工具可當地語系化的電腦上，您可以修改環境。 範本文件庫，例如，當地語系化的字串與 t 參數執行 FormPublish 工具**t:VorLagen**德文的環境中。 您接著可以當地語系化的環境中執行清理工具。  
  
 下列條件必須為要執行清除工具，則為 true:  
  
-   您必須是成員[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。  
  
-   [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]必須安裝在執行此工具的伺服器上。  
  
-   MrsrConfiguration.dll、 Shared.dll，RuleEngineExtension.dll 必須部署和執行此工具的伺服器上。  
  
## <a name="what-the-cleanup-tool-does"></a>[清理] 工具的用途  
 A4SWIFT 清理工具會執行下列作業：  
  
-   執行**BM 解除部署**ForActivities.xml 和 MRSRBAM.xml  
  
-   FrrActivities_ConnectionStrings.xml 和 MRSRActivities_ConnectionStrings.xml 檔案移除，如果有的話  
  
-   如果存在的話，移除 A4SWIFT 2.1 (如果您已升級伺服器[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]，但安裝程式已離開 A4SWIFT 2.1 安裝)，並刪除 A4SWIFT 2.1 資料夾  
  
-   解除部署所有 A4SWIFT 組件  
  
-   刪除 A4SWIFT 系統管理員群組和 A4SWIFT Users 群組  
  
-   刪除 A4SWIFT 資料庫  
  
-   刪除 A4SWIFT 虛擬目錄  
  
-   執行完整無訊息解除安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]並刪除[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]資料夾 （如果已選取）  
  
 因為它會移除成品，並解除部署組件，清理工具也會執行下列作業：  
  
-   啟動 Internet Information Services (IIS) 管理服務，才能執行  
  
-   停止並重新啟動 MSSQLSERVER、 SQLSERVERAGENT、 BizTalk 和企業單一登入服務  
  
#### <a name="to-run-the-a4swift-cleanup-tool"></a>若要執行 A4SWIFT 清理工具  
  
1.  在之前執行 A4SWIFT 清理工具，解除部署任何 A4SWIFT 預設組件是指任何專案。  
  
2.  開啟命令提示字元並移至\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools。  
  
3.  型別**A4SWIFTCleanupTool.exe** ，然後按**ENTER**。  
  
    > [!NOTE]
    >  當您一開始執行 A4SWIFTCleanupTool.exe 時，此工具會顯示說明畫面，並會提示您輸入的參數。 在您輸入的參數之前，不會執行此工具。  
  
4.  您希望該工具来採取的動作而定，按下列機碼，然後再按**ENTER**:  
  
    -   **0**的任何動作 （預設值）  
  
    -   **1**移除所有本機 A4SWIFT 電腦上的資源，包括虛擬目錄和登錄設定  
  
    -   **2**移除所有 BizTalk Server 群組，包括 Sharepoint Web 資料夾、 FIN 訊息範本、 BRE 原則和詞彙、 BizTalk 成品和 A4SWIFT 資料庫上的共用的 A4SWIFT 資源  
  
    -   **3**移除所有本機和共用資源  
  
    -   **4**來移除所有本機和共用資源和解除安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]產品。  
  
## <a name="see-also"></a>請參閱  
 [工具](../../adapters-and-accelerators/accelerator-swift/tools.md)