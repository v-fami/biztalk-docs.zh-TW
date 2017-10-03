---
title: "如何建立新對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43b36cd8-f28e-4349-87d5-c94b7d8761bf
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 910d79782f4332ae1d706e12a8c5dda8c399a41b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-new-maps"></a>如何建立新的對應

## <a name="overview"></a>概觀
若要建置新的 BizTalk 對應，請執行三個高階步驟：  
  
1.  在 BizTalk 專案內建立新對應。  
  
2.  將來源與目的結構描述加入至對應。  
  
3.  建置連結集或可能需要建置中繼運算質以指定來源結構描述對應到目的結構描述的方式。  
  
 在目前的內容中，這三個步驟中的前兩個被視為「建立」對應。 第三步驟則被視為「建置」對應。 如需的許多建置對應程序的相關工作的逐步指示，請參閱[更加建立複雜的對應使用運算質](../core/using-functoids-to-create-more-complex-mappings.md)。  
  
## <a name="create-a-new-map"></a>建立新的對應 
  
1.  以滑鼠右鍵按一下 BizTalk 專案，在 [方案總管] 中，選取**新增**，然後選取**新項目**。  
  
2.  在**加入新項目**對話方塊中，於**範本**區域中，選取**對應**。  
  
3.  選取的文字中**名稱**方塊，輸入對應的名稱，然後選取**新增**。  
  
     BizTalk 對應工具會開啟在 Microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]編輯視窗中，顯示三個不同的窗格，來並行。 由左至右，三個窗格依次顯示來源結構描述、格線 (可能有多頁) 和目的結構描述。  
  
    > [!IMPORTANT]
    >  以下名稱不能作為對應："XmlContent"、"SourceSchemas"、"TargetSchemas" 或 "XsltArgumentListContent"。 不能使用這些名稱的原因是編譯到 .NET 組件時會因為產生 C# 碼而發生命名限制。  
  
4.  在 BizTalk 對應工具的左窗格中，選取**開啟來源結構描述**。  
  
5.  在**BizTalk 型別選擇器**對話方塊方塊中，展開 [**結構描述**] 節點，選取適當的來源結構描述，然後選取**確定**。  

    > [!TIP] 
    > **從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** ，您可以調整 [型別選擇器] 視窗，請參閱您的結構描述的完整名稱。
  
     如果只存在來源結構描述中的單一根節點或根節點，已建立的結構描述使用**根參考**屬性**結構描述** 節點，在左的窗格中，而且您開啟來源結構描述可以繼續進行步驟 7。  
  
6.  如果來源結構描述有多個根節點，並沒有根節點，已建立的來源結構描述使用**結構描述**節點的**根參考**屬性，請在**來源根節點結構描述**對話方塊中，選取適當的根節點，然後選取**確定**。  
  
    > [!IMPORTANT]
    >  如果您在 BizTalk 對應工具中選擇的根節點的結構描述，然後稍後變更**根參考**屬性結構描述，下次您在 BizTalk 對應工具中開啟結構描述中的根節點不會更新來設定新的根參考在 [BizTalk 編輯器]。  
  
7.  在 BizTalk 對應工具中，在右窗格中，選取**開啟目的結構描述**。  
  
8.  在**BizTalk 型別選擇器**對話方塊方塊中，展開 **結構描述**節點在樹狀目錄中，如果有必要，選取適當的目的地結構描述，然後選取**確定**。  
  
     如果只有單一根節點存在於目的結構描述，或根節點，已建立的目的地結構描述使用**根參考**屬性**結構描述**] 節點，開啟 [目的結構描述在右窗格中，且您不需要執行步驟 9。  
  
9. 如果目的地結構描述有多個根節點，並沒有根節點，已建立的目的地結構描述使用**根參考**屬性**結構描述**節點，請在**根節點目標結構描述的**對話方塊中，選取適當的根節點，然後選取**確定**。  
  
     目的結構描述在右窗格中開啟。  
  
## <a name="see-also"></a>另請參閱  
 [管理專案中的對應](../core/managing-maps-within-projects.md)