---
title: 步驟 11： 建立協調流程變數 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, variables
- message enrichment tutorial, orchestrations
ms.assetid: 3d1f792d-fe74-4373-86fa-3debda55e732
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dfe49f533989e339e6eb4318460a444ed0d8b741
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991159"
---
# <a name="step-11-create-orchestration-variables"></a>步驟 11： 建立協調流程變數
在此步驟中，您會建立訊息執行個體傳送和接收的協調流程的協調流程變數。  
  
 BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 序列化程式需要下列部分的名稱。 如果您建立多部分訊息與任何其他組件名稱時，序列化程式會拒絕訊息。 訊息部分的名稱是：  
  
- MSHSegment  
  
- BodySegments  
  
- Z 區段  
  
  以下是有關 Z 區段組件的重要資訊：  
  
- 上面所述，不論 Z 區段是否存在，所有的訊息會包含三個部分。  
  
- 您可以使用 Z 區段組件，包含訊息執行個體，它是句尾且未定義 （這也表示它未宣告） 的結構描述中的資料。  
  
- 如果沒有任何未宣告的資料，是空白的 Z 區段組件。 您看不見的 Z 區段部分檢視的中繼 XML 內 BizTalk 對應工具; 時不過，在 BizTalk 狀況與活動追蹤 (HAT) 工具中，您會看到每個訊息的三個部分。  
  
### <a name="to-create-orchestration-variables"></a>若要建立協調流程變數  
  
1. 按一下 [**協調流程檢視**索引標籤旁**方案總管] 中**下方 [方案總管] 中的索引標籤。  
  
2. 在 **協調流程檢視** 窗格中，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
3. 變更**識別碼**中的屬性**屬性**窗格，即可**DoorbellInputMessage**，然後按**Enter**。  
  
4. 在 **屬性** 窗格的下拉式清單中**訊息類型**，展開**結構描述**，然後按一下  **BTAHL7_Project.Doorbell**。  
  
5. 重複步驟 2 和 3 來建立名為另一則訊息**DoorbellOutputMessage**。  
  
6. 在 **屬性** 窗格的下拉式清單中**訊息類型**，展開**結構描述**，然後按一下  **BTAHL7Schemas.ADT_A04_22_GLO_DEF**.  
  
7. 在 **協調流程檢視**窗格中，展開**型別**節點。 以滑鼠右鍵按一下**多部分訊息類型**，然後按一下**新的多部分訊息類型**。  
  
   > [!NOTE]
   >  [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)] 建立新的訊息類型，名為**MultipartType_1**以及名為的新訊息**MessagePart_1**。  
  
8. 按一下  **MultipartType_1**，然後在**屬性**視窗中，按一下 **識別碼**，輸入新名稱**DoorbellFinalMessageType**，然後按**Enter**。  
  
   > [!NOTE]
   >  在步驟 9 至 15 中，您將建立多部分訊息的部分。 您可以在其中建立多部分訊息的部分順序很重要。 一律會建立標頭，則主體中，則 Z 區段。  
  
   > [!NOTE]
   >  一旦您已建立並命名為訊息部分，請勿重新命名它們。 如有需要，刪除舊的內文部分，並使用新的名稱建立新的內文部分。  
  
9. 中**型別** 視窗底下**多部分訊息類型**，展開**DoorbellFinalMessageType**，然後按一下**MessagePart_1**。 在 [**屬性**] 窗格中，輸入**MSHSegment**的**識別碼**，然後按**Enter**。 中的下拉式清單**型別**，展開 **.NET 類別**，然後按一下\<**從參考組件中選取\>**。  
  
10. 在 **選取成品類型**對話方塊中，在左窗格中，按一下**System.Xml**。 在右窗格中，按一下**XmlDocument**，然後按一下**確定**。  
  
11. 在 [協調流程檢視] 視窗中，以滑鼠右鍵按一下**DoorbellFinalMessageType**，然後按一下**新訊息部分**建立 MessagePart_1。  
  
12. 在 [**屬性**] 視窗中，輸入**BodySegments**的**識別碼**，然後按**Enter**。 中的下拉式清單**型別**，展開**結構描述**，然後選取**BTAHL7Schemas.ADT_A04_22_GLO_DEF**從下拉式清單。  
  
13. 設定**訊息內文部分**屬性設 **，則為 True**。  
  
14. 在 [**協調流程檢視**] 視窗中，以滑鼠右鍵按一下**DoorbellFinalMessageType**，然後按一下**新訊息部分**。  
  
15. 在 [**屬性**] 窗格中，輸入**ZSegments**的**識別碼**，然後按**Enter**。 按一下 **型別**，展開 **.NET 類別**，然後按一下**System.String**從下拉式清單。  
  
    > [!NOTE]
    >  您使用**System.String** Z 區段的訊息部分，因為 Z 區段包含不需要符合結構描述的字串資料。  
  
16. 在 **協調流程檢視** 視窗中，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
17. 在 [**屬性**] 視窗中，輸入**DoorbellFinalMessage**的**識別碼**，然後按**Enter**。 中的下拉式清單**訊息類型**，展開**多部分訊息類型**，然後按一下**BTAHL7_Project.DoorbellFinalMessageType**。  
  
18. 在 **協調流程檢視** 視窗中，以滑鼠右鍵按一下**變數**，然後按一下 **新變數**。  
  
19. 在 **屬性**窗格中，輸入**HeaderInfo**的**識別碼**，然後按**Enter**。 中的下拉式清單**型別**，按兩下\< **.NET 類別\>**。  
  
20. 在 **選取成品類型**視窗中的，在左窗格中，按一下**System.Xml**。 在右窗格中，按一下**XmlDocument**，然後按一下**確定**。  
  
21. 在 **檔案**功能表上，按一下**全部儲存**。  
  
    請繼續進行[步驟 12： 設定協調流程圖形](../../adapters-and-accelerators/accelerator-hl7/step-12-configure-orchestration-shapes.md)。  
  
## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)