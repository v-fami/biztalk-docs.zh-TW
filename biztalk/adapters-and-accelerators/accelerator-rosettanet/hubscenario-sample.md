---
title: "HubScenario 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb6990ec-aea2-4362-8573-7f737a4fc7f1
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b9b2770f1d14d716149025ac44cb3cdffbbb23b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="hubscenario-sample"></a>HubScenario 範例
HubScenario 範例示範如何在集線器實例中管理訊息傳輸。 它會將傳送到中繼集線器的訊息轉換成要傳送給最後收件者的訊息。  
  
 HubScenario 會從服務內容擷取最後收件者的 DUNS 編號， 並管理簽章和加密憑證以及目的地 URL， 為最後收件者產生新的訊息。  
  
 本範例處理 3A4 要求和回應訊息以及 0C1 要求訊息。 當您針對某個目的使用 HubScenario 建立應用程式時，必須為每個訊息交易夥伴介面程序 (PIP) 產生常式。  
  
 HubScenario 範例包含 HubHelper.cs 和 HubScenario.odx 專案。  
  
 HubScenario 範例也包含繫結檔案，您可使用此檔案匯入接收埠 (MessagesToLOB_Receive_Port) 與接收位置 (MessagesToLOB_Receive_Location) 的繫結，搭配 HubScenario.odx 協調流程使用。 此繫結檔案 (HubScenarioBinding.xml) 位於*\<磁碟機 >*: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Microsoft BizTalk\<版本 > Accelerator for RosettaNet \SDK\HubScenario。 請使用 BTSTask 命令匯入繫結。 如需詳細資訊，請參閱「[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] 說明」中的＜ImportBindings 命令＞主題。  
  
### <a name="to-build-and-initialize-this-sample"></a>若要建置並初始化這個範例  
  
1.  在 Visual Studio 中開啟\<磁碟機 >: \Program Files\Microsoft Microsoft BizTalk\<版本 > Accelerator for RosettaNet\SDK\HubScenario\HubScenario.btproj。 在 [方案總管] 中，以滑鼠右鍵按一下 HubScenario 專案，然後按一下 [屬性]。 在 HubScenario 專案的 [屬性] 頁面中，於 [簽署] 索引標籤選取**簽署組件**核取方塊，然後選取**HubScenario.snk**中**選擇強式名稱金鑰檔**按一下**確定**。  
  
2.  在 [方案總管] 中，以滑鼠右鍵按一下 HubHelper 專案，然後按一下 [屬性]。 在 HubHelper 專案的 [屬性] 頁面中，核取 [簽署] 索引標籤中的 [簽署組件] 核取方塊。 在 [選擇強式名稱金鑰檔] 欄位中選取新的型別**HubHelper.snk**做為金鑰檔名稱，然後按一下**確定**。  
  
    > [!NOTE]
    >  如果您沒有在 HubScenario 和 HubHelper 專案中以手動方式輸入組件金鑰檔，這些組件將不會部署。  
  
3.  在命令提示字元中，移至*\<磁碟機 >*: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Microsoft BizTalk\<版本 > Accelerator for RosettaNet\SDK\HubScenario 資料夾。 執行 Setup.bat 檔案 (若在 64 位元電腦上，請執行 Setupx64.bat)。  
  
## <a name="demonstrates"></a>示範  
 HubScenario.ods 協調流程示範如何執行下列工作：  
  
1.  從商務營運系統應用程式接收訊息。  
  
2.  從服務內容中移除 `CDATA` 項目，傳回 XML 字串。  
  
3.  擷取最後訊息的目的合作對象、PIPCode、PIPInstanceID 和 PIPVersion。  
  
4.  擷取最後收件者的 DUNS 編號。  
  
5.  決定訊息的類別，並將包含適當結構描述之參考的 DOCTYPE 項目新增至服務內容。  
  
6.  使用新的目的合作對象、DUNS 編號、PIP 代碼資訊即服務內容建構訊息。  
  
7.  提交訊息，供 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 處理。 這是 `SubmitRNIF.SubmitMessage` 的呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [範例中樞架構實例](../../adapters-and-accelerators/accelerator-rosettanet/sample-hub-based-scenario.md)   
 [協調流程範例](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)