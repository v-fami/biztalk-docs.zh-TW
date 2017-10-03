---
title: "如何使用 [工具箱] |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, pipelines
- pipeline components, deleting from toolbox
- pipeline components, Pipeline Designer
- pipeline components, adding to toolbox
- Pipeline Designer, toolbox
- pipelines, creating
ms.assetid: 7a60c590-1a38-46fe-addf-0aa2c8b63cf9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3965a063aebcc932f07937fd19c3998412591ea1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-toolbox"></a>如何使用工具箱
從工具箱拖曳元件 (圖形) 至設計介面以建立管線。 「管線設計工具」藉由在建立程序中設定限制以協助您組合有效的管線。 您只能選取適用於您所建立的管線類型的工具箱元件。 例如，接收管線會將解碼器、解譯器和驗證器顯示為有效的工具箱元件，而編碼器和組合器則會停用 (變成灰色)。  
  
 此外，階段只能接受有效的元件。 例如，您無法將編碼器元件拖曳至組合階段。 當您拖曳元件接近有效的放置位置時，會出現箭頭以指示可插入元件的點。  
  
 若您將有效的元件拖曳至摺疊的階段上，請在階段上暫停滑鼠游標數秒鐘以展開它，然後將元件放置到階段中。  
  
 在「管線設計師」中新增自訂元件至工具箱的動作與標準 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 程序相似。  
  
 **開始和結束圖形**  
  
 **啟動**和**結束**圖形會顯示為在所有管線上的項目符號。 它們會出現在設計介面上，僅供視覺組織之用。 每種圖形只有一個，而且不能新增或刪除它們。 **啟動**和**結束**圖形不會出現在工具箱中。  
  
### <a name="to-add-a-pipeline-component-to-the-toolbox"></a>新增管線元件至工具箱  
  
1.  在 **[工具]** 功能表中按一下 **[選擇工具箱項目]**。  
  
     -或者-  
  
     以滑鼠右鍵按一下 工具箱，然後按一下 **選擇項目**。  
  
2.  在**自訂工具箱**對話方塊中，按一下 [ **BizTalk 管線元件**] 索引標籤。  
  
     對話方塊會顯示相容的管線元件。 您可以按一下對話方塊上方的索引標籤在類別之間巡覽。  
  
3.  選取您要新增至工具箱的元件。  
  
4.  按一下 **[確定]**。 此元件將會出現在**BizTalk 管線元件**工具箱索引標籤。  
  
### <a name="to-remove-a-pipeline-component-from-the-toolbox"></a>從工具箱移除管線元件  
  
-   開啟**自訂工具箱**對話方塊 （如同前述程序），然後清除要移除的元件。  
  
     即使元件已從工具箱移除，它仍然保持已註冊狀態。  
  
## <a name="see-also"></a>另請參閱  
 [如何建立新的管線](../core/how-to-create-a-new-pipeline.md)   
 [如何開啟管線](../core/how-to-open-a-pipeline.md)   
 [如何使用鍵盤巡覽](../core/how-to-navigate-with-the-keyboard.md)   
 [使用管線設計師建立管線](../core/creating-pipelines-with-pipeline-designer.md)