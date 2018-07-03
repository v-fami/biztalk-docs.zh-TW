---
title: 如何取代結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 104e60d3-1303-4e56-b13a-c10ab14ba383
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8aaca705c54866ec6323d7c26a5fe7b731129e7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022524"
---
# <a name="how-to-replace-schemas"></a>如何取代結構描述
您有時候可能想要取代現有對應中的來源或目的結構描述，例如當您收到來自交易夥伴的已更新結構描述時。  
  
> [!NOTE]
>  「BizTalk 對應工具」會嘗試維護已保留結構描述和已取代結構描述之間的所有現有連結。  
  
## <a name="replace-a-source-or-destination-schema"></a>取代來源或目的結構描述  
  
1. 以滑鼠右鍵按一下來源或目的結構描述樹狀檢視，然後按**取代結構描述**。  
  
   > [!NOTE]
   >  或者，您也可以按下鍵盤的 CTRL+M、CTRL+S。 如需對應工具鍵盤快速鍵的完整清單，請參閱 < [BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。  
  
2. 在  **BizTalk 型別選擇器**對話方塊方塊中，展開**結構描述**節點在樹狀目錄中，選取適當的結構描述，然後選取**確定**。  
  
    ![選取的結構描述](../core/media/biztalk-typepicker.gif "BizTalk_TypePicker")  

   > [!TIP]
   > **開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** ，您可以調整大小的型別選擇器視窗，以查看您的結構描述的完整名稱。
      
    如果只有單一根節點存在於取代結構描述，或已建立取代結構描述使用根節點**根參考**屬性**結構描述**] 節點，開啟 [取代結構描述在相關窗格中，您將不需要執行步驟 3。  
  
3. 如果多個根節點存在於目的地結構描述，並已建立目的地結構描述使用沒有根節點**根參考**屬性**結構描述**節點，請在**根節點\<*來源/目標*\>結構描述** 對話方塊中，選取適當的根節點，然後按**確定**。  
  
    取代結構描述會在相關窗格中開啟。  
  
   > [!NOTE]
   >  如果取代結構描述時找不到相關的記錄/欄位，某些連結可能會遺失。 只有當您選取時，會取代結構描述**是**上**確認** 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [管理專案中的對應](../core/managing-maps-within-projects.md)