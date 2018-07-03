---
title: 如何設定節點屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0c79eac-d9ba-45e2-a6e9-770b2bcb2067
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e70a1c6797379c81c22d1fc38a503974d8ac795
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022540"
---
# <a name="how-to-set-node-properties"></a>如何設定節點屬性
將節點插入 BizTalk 結構描述後，您通常需要變更該節點屬性的預設值。 每種類型的節點都有不同的屬性集，在這些其中一個屬性集中，一個屬性的設定可影響其他屬性的可用性。 比方說，才能設定**預設換行字元**屬性**結構描述**節點，您必須設定**Default Wrap Character Type**屬性，以其中一個**字元**或是**十六進位**，藉此建立要代表先前屬性的格式。 此外，沒有這些屬性可供使用，也不是整個**剖析**屬性類別目錄所屬，除非**一般檔案延伸模組**啟用使用**結構描述編輯器延伸模組**屬性。  

 節點屬性相當廣泛而且可以很複雜，就如同它們所支援的 XML 結構描述定義 (XSD) 語言一樣。 本主題僅簡單描述與檢查和設定節點屬性相關的一般步驟。 如需這些屬性的詳細資訊，包括，比方說，其預設值的相關資訊和允許的值，請參閱**結構描述屬性參考**。 針對更詳細的 XSD 概念和構成這些節點屬性的項目相關的資訊，請直接參考資訊的相關[網站上的 XSD](../core/xsd-resources-on-the-web.md)。  

深入了解這些屬性和結構描述屬性參考[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。

  
## <a name="examine-a-node-property-value"></a>檢查節點屬性值  
  
1. 在 [BizTalk 編輯器] 中，開啟包含要檢查之屬性的結構描述，然後選取包含該屬性的節點。  
  
2. 如有需要，請按 F4，開啟 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 屬性] 視窗。  
  
3. 如有需要，請捲動 [屬性] 視窗捲動，尋找您感興趣的屬性，並注意其值。  
  
    您可使用 [屬性] 視窗上方的按鈕變更屬性排序的方式，可依照字母順序在其類別中排序，或不考慮 (或不顯示) 其類別而依字母順序排序。  
  
## <a name="set-a-node-property-value"></a>設定節點屬性值  
  
1. 在 [BizTalk 編輯器] 中，開啟包含要設定之屬性的結構描述，然後選取包含該屬性的節點。  
  
2. 如有需要，請按 F4，開啟 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 屬性] 視窗。  
  
3. 如有需要，請捲動 [屬性] 視窗，尋找您感興趣的屬性。  
  
    您可使用 [屬性] 視窗上方的按鈕變更屬性排序的方式，可依照字母順序在其類別中排序，或不考慮 (或不顯示) 其類別而依字母順序排序。  
  
4. 在值欄位 (在屬性名稱的右邊) 中設定屬性值。 根據屬性類型的不同，您可以輸入值，或從選取值欄位時所顯示的下拉式清單中選擇值。 某些屬性同時允許這兩種方式。 某些屬性會顯示省略符號 (**...**) 按鈕，可以設定的對話方塊中的較複雜的值，例如集合的已按下 隨即開啟。  
  
5. 輸入屬性的新值後，請按 ENTER 來完成。  
  
##  <a name="clear-a-node-property-value"></a>清除節點屬性值  
  
1.  選取包含您感興趣之屬性的節點。  
  
2.  在 屬性 視窗中，連按兩下您想要清除，以滑鼠右鍵按一下 屬性值，然後按一下 屬性值**刪除**。  
  
## <a name="restore-a-node-property-to-its-default-value"></a>節點屬性還原為其預設值  
  
1.  選取包含您感興趣之屬性的節點。  
  
2.  在 屬性 視窗中，以滑鼠右鍵按一下您想要重設為其預設值，然後按一下 屬性名稱**重設**。  
  
## <a name="see-also"></a>另請參閱  
 [使用現有節點](../core/working-with-existing-nodes.md)