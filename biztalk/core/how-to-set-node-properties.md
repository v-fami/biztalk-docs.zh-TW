---
title: 如何設定節點屬性 |Microsoft 文件
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
ms.openlocfilehash: 13dc0f13814808a69c4c4b9c3976e9047acde5b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255446"
---
# <a name="how-to-set-node-properties"></a>如何設定節點屬性
將節點插入 BizTalk 結構描述後，您通常需要變更該節點屬性的預設值。 每種類型的節點都有不同的屬性集，在這些其中一個屬性集中，一個屬性的設定可影響其他屬性的可用性。 例如，才能設定**預設換行字元**屬性**結構描述** 節點，您必須設定**Default Wrap Character Type**任一屬性**字元**或**十六進位**，藉此建立要代表先前屬性的格式。 此外，這些屬性可供使用，都是整個**剖析**屬性類別目錄所屬，除非**一般檔案延伸模組**啟用利用**結構描述編輯器擴充功能**屬性。  

 節點屬性相當廣泛而且可以很複雜，就如同它們所支援的 XML 結構描述定義 (XSD) 語言一樣。 本主題僅簡單描述與檢查和設定節點屬性相關的一般步驟。 如需這些屬性的詳細資訊，包括，比方說，其預設值的相關資訊以及允許的值，請參閱**結構描述屬性參考**。 如更詳細的 XSD 概念和構成這些節點屬性的項目相關資訊，請直接參考資訊有關[在網站上的 XSD](../core/xsd-resources-on-the-web.md)。  

這些屬性和結構描述屬性參考上的進一歩[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。

  
## <a name="examine-a-node-property-value"></a>檢查節點屬性值  
  
1.  在 [BizTalk 編輯器] 中，開啟包含要檢查之屬性的結構描述，然後選取包含該屬性的節點。  
  
2.  如有需要，請按 F4，開啟 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 屬性] 視窗。  
  
3.  如有需要，請捲動 [屬性] 視窗捲動，尋找您感興趣的屬性，並注意其值。  
  
     您可使用 [屬性] 視窗上方的按鈕變更屬性排序的方式，可依照字母順序在其類別中排序，或不考慮 (或不顯示) 其類別而依字母順序排序。  
  
## <a name="set-a-node-property-value"></a>設定節點屬性值  
  
1.  在 [BizTalk 編輯器] 中，開啟包含要設定之屬性的結構描述，然後選取包含該屬性的節點。  
  
2.  如有需要，請按 F4，開啟 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 屬性] 視窗。  
  
3.  如有需要，請捲動 [屬性] 視窗，尋找您感興趣的屬性。  
  
     您可使用 [屬性] 視窗上方的按鈕變更屬性排序的方式，可依照字母順序在其類別中排序，或不考慮 (或不顯示) 其類別而依字母順序排序。  
  
4.  在值欄位 (在屬性名稱的右邊) 中設定屬性值。 根據屬性類型的不同，您可以輸入值，或從選取值欄位時所顯示的下拉式清單中選擇值。 某些屬性同時允許這兩種方式。 某些屬性會顯示省略符號 (**...**) 按鈕，按下後會開啟對話方塊，在其中更複雜的值，例如，集合、 可以設定。  
  
5.  輸入屬性的新值後，請按 ENTER 來完成。  
  
##  <a name="clear-a-node-property-value"></a>清除節點屬性值  
  
1.  選取包含您感興趣之屬性的節點。  
  
2.  在 [屬性] 視窗中，連按兩下您想要清除，屬性值，以滑鼠右鍵按一下，然後按一下屬性值**刪除**。  
  
## <a name="restore-a-node-property-to-its-default-value"></a>節點屬性還原為其預設值  
  
1.  選取包含您感興趣之屬性的節點。  
  
2.  在 [屬性] 視窗中，以滑鼠右鍵按一下您想要重設為其預設值，然後按一下屬性名稱**重設**。  
  
## <a name="see-also"></a>另請參閱  
 [使用現有的節點](../core/working-with-existing-nodes.md)