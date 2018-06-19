---
title: 如何建立使用其他結構描述的結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff0bcd9a-6c66-4c3b-bd41-64047a7c8392
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f427e5cd8e3f82e57dc8926c6e00889e1c97afe9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249414"
---
# <a name="how-to-create-schemas-that-use-other-schemas"></a>如何建立使用其他結構描述的結構描述
XML 結構描述定義 (XSD) 語言提供三個不同但相關的機制，以便在某個結構描述中使用另一個結構描述。 這些機制為匯入結構描述、包含結構描述以及重新定義結構描述。 這些機制及其有何差異的簡短摘要，請參閱[使用其他結構描述的](../core/schemas-that-use-other-schemas.md)。 如需詳細資訊，請參閱[在網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)取得 XSD 入門與規格的連結。  
  
 本主題描述在進行開發的結構描述中匯入、包含及重新定義其他結構描述所需的步驟。  
  
### <a name="to-import-include-or-redefine-one-schema-within-another-schema"></a>在某個結構描述中匯入、包含或重新定義另一個結構描述  
  
1.  在 BizTalk 編輯器中，開啟要匯入、包含或重新定義某個結構描述的另一個結構描述。 您可以在 [方案總管] 中按兩下結構描述以開啟它。  
  
2.  選取**結構描述**節點在結構描述樹狀檢視的頂端。  
  
3.  如有需要，請按 F4，開啟 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 屬性] 視窗。  
  
4.  在 [屬性] 視窗中**進階**類別目錄中的值部分**匯入**屬性中，按一下省略符號 (**...**) 按鈕。  
  
5.  在**匯入**對話方塊中，於**匯入新結構描述為**清單中，選取**XSD 匯入**， **XSD Include**，或**XSD重新定義**，適當地，然後按一下**新增**。  
  
6.  在**BizTalk 型別選擇器**對話方塊方塊中，展開 **結構描述**節點在專案樹狀目錄中，選取您想要匯入、 包括或重新定義，然後按一下 結構描述**確定**。  
  
7.  在**匯入**對話方塊中，按一下 **確定**。  
  
     適當 XSD 指示詞，來實作匯入、 包含或重新定義作業加入至**結構描述**在 XSD 檢視中，包括新的項目**匯入**，**包含**，或**重新定義**項目，視需要。  
  
> [!IMPORTANT]
>  請確定您瞭解這三種機制的不同目的，例如它們在命名空間需求方面的差異。 您可以隨時刪除先前已匯入、 包含或重新定義結構描述，然後使用其中一個其他兩個機制，但根據您如何廣泛地參考該結構描述，您可能需要重新據以處理您的結構描述。  
  
> [!IMPORTANT]
>  在某個結構描述中匯入、包含和重新定義另一個結構描述的 XSD 機制是藉由參考至已匯入、已包含或已重新定義的結構描述來運作。 這表示若您對已匯入、已包含或已重新定義的結構描述進行變更，該變更將會反映在包含匯入、包含或重新定義參考的結構描述中。  
  
## <a name="see-also"></a>另請參閱  
 [管理專案中的結構描述](../core/managing-schemas-within-projects.md)   
 [如何建立其他節點或類型的參考](../core/how-to-create-references-to-another-node-or-type.md)