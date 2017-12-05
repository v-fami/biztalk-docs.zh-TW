---
title: "步驟 11： 建立協調流程變數 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, variables
- message enrichment tutorial, orchestrations
ms.assetid: 3d1f792d-fe74-4373-86fa-3debda55e732
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a640b938628ebe3dcd6757e3f6fdfd7b1108880d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-11-create-orchestration-variables"></a>步驟 11： 建立協調流程變數
在此步驟中，您會建立訊息執行個體傳送和接收的協調流程的協調流程變數。  
  
 BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 序列化程式需要下列部分的名稱。 如果您使用其他部分的名稱建立多部分訊息，序列化程式將會拒絕訊息。 訊息部分的名稱是：  
  
-   MSHSegment  
  
-   BodySegments  
  
-   Z 區段  
  
 以下是有關 Z 區段組件的重要資訊：  
  
-   所有訊息都包含三個部分 （如上所述），不論 Z 區段是否已存在。  
  
-   您可以使用 Z 區段組件，包含訊息執行個體，且結尾 （這也表示未宣告） 的結構描述中未定義的資料。  
  
-   如果沒有未宣告的資料，Z 區段部分是空白的。 看不到 Z 區段組件時檢視的中繼 XML 內 BizTalk 對應工具。不過，在 BizTalk 狀況與活動追蹤 (HAT) 工具中，您會看到每個訊息的三個部分。  
  
### <a name="to-create-orchestration-variables"></a>若要建立協調流程變數  
  
1.  按一下**協調流程檢視**索引標籤旁**方案總管 中** 索引標籤下方的 方案總管 中。  
  
2.  在**協調流程檢視**] 窗格中，以滑鼠右鍵按一下**訊息**，然後按一下 [**新訊息**。  
  
3.  變更**識別碼**屬性**屬性**窗格**DoorbellInputMessage**，然後按下**Enter**。  
  
4.  在**屬性**窗格的下拉式清單中**訊息類型**，依序展開**結構描述**，然後按一下  **BTAHL7_Project.Doorbell**。  
  
5.  重複步驟 2 和 3 來建立名為另一個訊息**DoorbellOutputMessage**。  
  
6.  在**屬性**窗格的下拉式清單中**訊息類型**，依序展開**結構描述**，然後按一下  **BTAHL7Schemas.ADT_A04_22_GLO_DEF**.  
  
7.  在**協調流程檢視**] 窗格中，展開 [**類型**節點。 以滑鼠右鍵按一下**多部分訊息類型**，然後按一下 **新多部分訊息類型**。  
  
    > [!NOTE]
    >  [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]建立新的訊息類型，名為**MultipartType_1**以及一個名為的新訊息**MessagePart_1**。  
  
8.  按一下**MultipartType_1**，然後在**屬性**視窗中，按一下 **識別碼**，輸入新名稱**DoorbellFinalMessageType**，然後按下**Enter**。  
  
    > [!NOTE]
    >  在步驟 9 至 15，您將建立多部分訊息的部分。 您可以在其中建立多部分訊息部分的順序很重要。 請務必建立標頭，然後本文，然後再 Z 區段。  
  
    > [!NOTE]
    >  一旦您建立並命名為訊息部分，請勿重新命名它們。 如有必要，刪除舊的內文部分，並以新名稱建立新的內文部分。  
  
9. 在**類型**視窗底下**多部分訊息類型**，依序展開**DoorbellFinalMessageType**，然後按一下  **MessagePart_1**。 在**屬性** 窗格中，輸入**MSHSegment**如**識別碼**，然後按下**Enter**。 在下拉式清單中**類型**，依序展開**.NET 類別**，然後按一下  \<**從參考的組件中選取\>**。  
  
10. 在**選取成品類型**] 對話方塊的左窗格中，按一下 [ **System.Xml**。 在右窗格中，按一下  **XmlDocument**，然後按一下 **確定**。  
  
11. 在協調流程檢視] 視窗中，以滑鼠右鍵按一下**DoorbellFinalMessageType**，然後按一下 [**新訊息部分**建立 MessagePart_1。  
  
12. 在**屬性**視窗中，輸入**BodySegments**如**識別碼**，然後按下**Enter**。 在下拉式清單中**類型**，依序展開**結構描述**，然後選取**BTAHL7Schemas.ADT_A04_22_GLO_DEF**從下拉式清單。  
  
13. 設定**訊息內文部分**屬性**True**。  
  
14. 在**協調流程檢視**視窗中，以滑鼠右鍵按一下**DoorbellFinalMessageType**，然後按一下 **新訊息部分**。  
  
15. 在**屬性** 窗格中，輸入**ZSegments**如**識別碼**，然後按下**Enter**。 按一下**類型**，依序展開**.NET 類別**，然後按一下  **System.String**從下拉式清單。  
  
    > [!NOTE]
    >  您使用**System.String** Z 區段訊息部分，因為 Z 區段包含不需要符合結構描述的字串資料。  
  
16. 在**協調流程檢視**視窗中，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
17. 在**屬性**視窗中，輸入**DoorbellFinalMessage**如**識別碼**，然後按下**Enter**。 在下拉式清單中**訊息類型**，依序展開**多部分訊息類型**，然後按一下  **BTAHL7_Project.DoorbellFinalMessageType**。  
  
18. 在**協調流程檢視**視窗中，以滑鼠右鍵按一下**變數**，然後按一下 **新變數**。  
  
19. 在**屬性** 窗格中，輸入**HeaderInfo**如**識別碼**，然後按下**Enter**。 在下拉式清單中**類型**，連按兩下\< **.NET 類別\>**。  
  
20. 在**選取成品類型**視窗中的，在左窗格中，按一下  **System.Xml**。 在右窗格中，按一下  **XmlDocument**，然後按一下 **確定**。  
  
21. 在**檔案**功能表上，按一下 **全部儲存**。  
  
 若要繼續[步驟 12： 設定協調流程圖形](../../adapters-and-accelerators/accelerator-hl7/step-12-configure-orchestration-shapes.md)。  
  
## <a name="see-also"></a>請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)