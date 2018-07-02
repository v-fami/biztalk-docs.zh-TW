---
title: A4SWIFT 清理工具 |Microsoft Docs
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
ms.openlocfilehash: db6e9f6f6ec25762abc4416bc18f0955055b7e70
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983615"
---
# <a name="a4swift-cleanup-tool"></a>A4SWIFT 清理工具
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]清理工具可讓您準備具有 Microsoft 的伺服器[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]新安裝在其上安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]。 此工具會移除 A4SWIFT 成品，例如合約、 部門及商務規則引擎 (BRE) 原則，並解除部署組件。 執行此工具可讓您避免以手動方式移除許多 A4SWIFT 成品，並解決可能與其他組件參考的解除部署組件的問題。  
  
 當您執行清理工具時，您可以選擇離開 A4SWIFT 安裝在電腦 （預設值） 或解除安裝 A4SWIFT 之後移除成品。 您應該執行此工具，然後再解除 A4SWIFT 安裝。  
  
> [!CAUTION]
>  請勿在生產環境中使用 A4SWIFT 清理工具。 此工具是用於在單一伺服器的開發環境中，不會在多伺服器部署。  
  
> [!NOTE]
>  根據預設，清理工具不適用於其他任何語言比英文。 使清理工具可當地語系化的電腦上，不過，可以修改環境。 範本文件庫，例如，當地語系化的字串與 t 參數執行 FormPublish 工具**t:VorLagen**德文的環境中。 您接著可以在當地語系化的環境中執行清理工具。  
  
 下列條件必須為要執行清除工具，則為 true:  
  
- 您必須是成員[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。  
  
- [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] 必須安裝在您用來執行此工具的伺服器上。  
  
- MrsrConfiguration.dll、 Shared.dll 和 RuleEngineExtension.dll 必須部署在您用來執行此工具的伺服器上。  
  
## <a name="what-the-cleanup-tool-does"></a>清理工具的用途  
 A4SWIFT 清理工具會執行下列作業：  
  
- 回合**BM 解除部署**ForActivities.xml 和 MRSRBAM.xml  
  
- 如果有的話，移除 FrrActivities_ConnectionStrings.xml 和 MRSRActivities_ConnectionStrings.xml 檔案，  
  
- 若有的話，移除 A4SWIFT 2.1 (如果您已升級伺服器[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]，但安裝程式已離開 A4SWIFT 2.1 安裝)，並刪除 A4SWIFT 2.1 資料夾  
  
- 解除部署 A4SWIFT 的所有組件  
  
- 刪除 A4SWIFT 系統管理員群組和 A4SWIFT 使用者群組  
  
- 刪除 A4SWIFT 資料庫  
  
- 刪除 A4SWIFT 虛擬目錄  
  
- 執行的完整無訊息解除安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]，並刪除[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]資料夾 （如果已選取）  
  
  因為它會移除成品，並解除部署組件，清理工具也會執行下列作業：  
  
- 若要執行的啟動 Internet Information Services (IIS) 管理員服務  
  
- 會停止，然後重新啟動 MSSQLSERVER、 SQLSERVERAGENT、 BizTalk、 和企業單一登入服務  
  
#### <a name="to-run-the-a4swift-cleanup-tool"></a>若要執行 A4SWIFT 清理工具  
  
1. 然後再執行 A4SWIFT 清理工具，解除部署是指任何 A4SWIFT 預設組件的任何專案。  
  
2. 開啟命令提示字元並移至\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools。  
  
3. 型別**A4SWIFTCleanupTool.exe** ，然後按**ENTER**。  
  
   > [!NOTE]
   >  當您一開始執行 A4SWIFTCleanupTool.exe 時，此工具會顯示 [說明] 畫面中，並會提示您輸入的參數。 您輸入的參數之前，不會執行此工具。  
  
4. 根據您希望該工具，要採取的動作，請按下列索引鍵，其中，然後按**ENTER**:  
  
   - **0**的 （預設） 沒有動作  
  
   - **1**移除所有本機 A4SWIFT 電腦上的資源，包括虛擬目錄和登錄設定  
  
   - **2**移除所有的 BizTalk Server 群組，包括 Sharepoint Web 資料夾、 FIN 訊息範本，BRE 原則和詞彙、 BizTalk 成品和 A4SWIFT 資料庫上的共用的 A4SWIFT 資源  
  
   - **3**移除所有本機和共用資源  
  
   - **4**來移除所有本機和共用資源和解除安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]產品。  
  
## <a name="see-also"></a>另請參閱  
 [工具](../../adapters-and-accelerators/accelerator-swift/tools.md)