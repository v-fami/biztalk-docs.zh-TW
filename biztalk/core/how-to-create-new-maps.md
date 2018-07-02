---
title: 如何建立新對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 43b36cd8-f28e-4349-87d5-c94b7d8761bf
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03de6f3dc8445afa2171b6ca17099de85302692a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984375"
---
# <a name="how-to-create-new-maps"></a>如何建立新的對應

## <a name="overview"></a>概觀
若要建置新的 BizTalk 對應，請執行三個高階步驟：  
  
1. 在 BizTalk 專案內建立新對應。  
  
2. 加入對應的來源和目的地結構描述。  
  
3. 建置連結集或可能需要建置中繼運算質以指定來源結構描述對應到目的結構描述的方式。  
  
   在目前的內容中，這三個步驟中的前兩個被視為「建立」對應。 第三步驟則被視為「建置」對應。 如需許多建置對應的程序的相關工作的逐步指示，請參閱[更加建立複雜的對應使用運算質](../core/using-functoids-to-create-more-complex-mappings.md)。  
  
## <a name="create-a-new-map"></a>建立新的對應 
  
1. 以滑鼠右鍵按一下 BizTalk 專案，在 [方案總管] 中，選取**新增**，然後選取**新項目**。  
  
2. 在 **加入新項目**對話方塊中，於**範本**區域中，選取**對應**。  
  
3. 選取中的文字**名稱**方塊中，輸入對應的名稱，然後選取**新增**。  
  
    BizTalk 對應工具會開啟 microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]編輯視窗中，顯示三個不同的窗格並排顯示。 由左至右，三個窗格依次顯示來源結構描述、格線 (可能有多頁) 和目的結構描述。  
  
   > [!IMPORTANT]
   >  以下名稱不能作為對應："XmlContent"、"SourceSchemas"、"TargetSchemas" 或 "XsltArgumentListContent"。 不能使用這些名稱的原因是編譯到 .NET 組件時會因為產生 C# 碼而發生命名限制。  
  
4. 在 BizTalk 對應工具中，在左窗格中，選取**開啟來源結構描述**。  
  
5. 在  **BizTalk 型別選擇器**對話方塊方塊中，展開**結構描述**節點中，選取適當的來源結構描述，然後選取**確定**。  

   > [!TIP]
   > **開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** ，您可以調整大小的型別選擇器視窗，以查看您的結構描述的完整名稱。
  
    如果只有單一根節點存在於來源結構描述，或已建立結構描述使用根節點**根參考**屬性**結構描述** 節點，在左的窗格中，而您開啟來源結構描述可以繼續進行步驟 7。  
  
6. 如果來源結構描述有多個根節點，並已建立來源結構描述使用沒有根節點**結構描述**節點的**根參考**屬性，請在**來源的根節點結構描述** 對話方塊中，選取適當的根節點，然後選取**確定**。  
  
   > [!IMPORTANT]
   >  如果您選擇在 BizTalk 對應工具中的結構描述的根節點，然後稍後變更**根參考**屬性結構描述，下次您在 BizTalk 對應工具中開啟結構描述中的根節點將不會更新來設定新的根參考在 [BizTalk 編輯器] 中。  
  
7. 在 BizTalk 對應工具中，在右窗格中，選取**開啟目的結構描述**。  
  
8. 在  **BizTalk 型別選擇器**對話方塊方塊中，展開**結構描述**節點樹狀目錄中，如果有必要，選取適當的目的地結構描述，然後選取**確定**。  
  
    如果只有單一根節點存在於目的地結構描述，或已建立目的地結構描述使用根節點**根參考**屬性**結構描述**] 節點，開啟 [目的結構描述在右窗格中，您將不需要執行步驟 9。  
  
9. 如果目的結構描述有多個根節點，並已建立目的地結構描述使用沒有根節點**根參考**屬性**結構描述**節點，請在**根節點目標結構描述** 對話方塊中，選取適當的根節點，然後選取**確定**。  
  
     目的結構描述在右窗格中開啟。  
  
## <a name="see-also"></a>另請參閱  
 [管理專案中的對應](../core/managing-maps-within-projects.md)