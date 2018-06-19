---
title: 將要求對應至私用程序中回應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, maps
- private processes, mapping requests
- private processes, customizing
- orchestrations, adding maps
- maps, adding to orchestrations
- maps, creating
- customizing private processes
- requests, mapping
- requests, private processes
ms.assetid: 5452c0a2-3a9b-43e7-bfa7-713eef0eab3b
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 966ad6ad752c36be36b4013743eaba3af5434d0a
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008367"
---
# <a name="mapping-a-request-to-a-response-in-a-private-process"></a>將要求對應至私用程序中回應時間
本主題描述如何將私用回應者程序所接收的要求訊息對應 — 從[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]公用回應者程序，來回應訊息傳送給[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]公用回應者程序。  
  
 當回應者收到要求訊息時，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會藉由從公開程序協調流程到私用程序協調流程的方式，路由這個要求訊息至商務營運系統 (LOB) 程式。 這個回應者需要從 LOB 程式取得回應服務內容，並產生 RosettaNet 回應訊息傳回給啟動者。 回應訊息中的許多項目都是使用要求訊息的值加以填入。 因此，您可以在回應者私用程序協調流程中整合出一套對應方式，幫助 LOB 程式以所需的格式產生回應服務內容訊息。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 包含下列範例，讓您可以在將對應加入回應者私用程序時加以使用：  
  
-   [3A2 要求至 3A2 回應的對應範例](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md)  
  
-   [3A4 要求至 3A4 回應的對應範例](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md)  
  
-   [雙向動作 PIPAutomation 協調流程](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md)  
  
-   [使用商務規則的 3A4 私用回應者協調流程](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)  
  
### <a name="to-create-the-map"></a>若要建立對應  
  
1.  啟動**Microsoft Visual Studio 2012**。  
  
2.  在**檔案**功能表上，指向**開啟**，然後按一下 **專案**。  
  
3.  找到含有 BizTalk 專案的資料夾，這個資料夾需包含要將對應加入至其中的私用程序協調流程。  
  
4.  在方案總管中，以滑鼠右鍵按一下專案，指向 [加入]，然後按一下 [新增項目]。  
  
5.  在 [加入新項目] 視窗中**類別**] 窗格中，按一下 [**對應檔**。 在 [範本] 窗格中，按一下**對應**。 在**名稱**方塊、 輸入對應的名稱，然後按一下**開啟**。  
  
6.  在 [來源結構描述] 窗格中，按一下**開啟來源結構描述**。  
  
7.  在 BizTalk 型別選擇器 視窗中，依序展開**結構描述**，選取您想要從，對應，然後按一下 要求訊息的 PIP 結構描述**確定**。  
  
8.  在 [目的結構描述] 窗格中，按一下**開啟目的結構描述**。  
  
9. 在 [BizTalk 型別選擇器] 視窗中，依序展開**參考**，依序展開**Microsoft.Solutions.BTARN.Schemas.RNPIPs**，依序展開**結構描述**，選取的 PIP 結構描述您想要對應，然後按一下的回應訊息**確定**。  
  
10. 以滑鼠右鍵按一下\<*結構描述*\>節點來源結構描述，然後再按一下**展開樹狀結構節點**。  
  
11. 重複步驟 10，完成目的結構描述的部分。  
  
12. 在 [來源結構描述] 窗格中，在您要與目的結構描述之欄位進行對應的欄位上按住不放。 然後將該欄位拖曳至 [目的結構描述] 窗格中對應的節點。  
  
13. 重複步驟 12，將全部您要進行對應的欄位完成對應的動作。  
  
14. 驗證並測試對應。 如需詳細資訊，請參閱 BizTalk Server 說明中的 「 編譯與測試對應 」 主題。  
  
### <a name="to-add-the-map-to-the-orchestration"></a>將對應加入協調流程  
  
1.  在 [方案總管] 中，按兩下私用程序協調流程。  
  
    > [!NOTE]
    >  請確認協調流程含有包括這個結構描述之組件的參考。  
  
2.  在工具箱中，按一下 **轉換**圖形，並將它拖曳至協調流程，您不必將要求訊息轉換成回應訊息中的點。  
  
    > [!NOTE]
    >  如需範例的位置的**轉換**圖形，請參閱 PIP3A4PrivateResponder.odx 協調流程。 它位於\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\PipAutomation\3A4\PR。 這個範例會將放**轉換**立即圖形下**IsActivityDoubleAction**圖形。 如需詳細資訊，請參閱[3A4 私用回應者協調流程使用商務規則](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)。  
  
    > [!NOTE]
    >  如需如何將多個對應合併多個 Pip 的範例，請參閱[雙向動作 PIPAutomation 協調流程](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md)。  
  
3.  協調流程設計介面上，按一下  **ConstructMessage1**。 在 [屬性] 視窗中，輸入這個圖形的名稱，以及所要建構的訊息名稱。  
  
4.  協調流程設計介面上，按一下 **轉換**。 在 屬性 視窗中，按一下 省略符號按鈕 (**...**) 旁邊**對應名稱**。  
  
5.  在 轉換組態 視窗中，按一下 **現有對應**，然後在**完整格式對應名稱**，按一下您剛才建立的對應。  
  
6.  在下**轉換**，按一下 **來源**。 按一下變數下方的空白方塊，並從下拉式清單中選取要求訊息的名稱。  
  
7.  在下**轉換**，按一下 **目的地**。 按一下變數下方的空白方塊，並從下拉式清單中選取回應訊息的名稱。  
  
8.  按一下 **[確定]**。  
  
## <a name="see-also"></a>請參閱  
 [程式設計指南](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)