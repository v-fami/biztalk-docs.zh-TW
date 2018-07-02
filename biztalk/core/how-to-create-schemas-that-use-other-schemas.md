---
title: 如何建立使用其他結構描述的結構描述 |Microsoft Docs
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
ms.openlocfilehash: 51fdc5e7601eebca7cc8193757cc909784ab828f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987807"
---
# <a name="how-to-create-schemas-that-use-other-schemas"></a>如何建立使用其他結構描述的結構描述
XML 結構描述定義 (XSD) 語言提供三個不同但相關的機制，以便在某個結構描述中使用另一個結構描述。 這些機制為匯入結構描述、包含結構描述以及重新定義結構描述。 這些機制，以及它們之間的差異的簡短摘要，請參閱 <<c0> [ 使用其他結構描述的](../core/schemas-that-use-other-schemas.md)。 如需詳細資訊，請參閱 <<c0> [ 網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)以 XSD 入門與規格的連結。  
  
 本主題描述在進行開發的結構描述中匯入、包含及重新定義其他結構描述所需的步驟。  
  
### <a name="to-import-include-or-redefine-one-schema-within-another-schema"></a>在某個結構描述中匯入、包含或重新定義另一個結構描述  
  
1. 在 BizTalk 編輯器中，開啟要匯入、包含或重新定義某個結構描述的另一個結構描述。 您可以在 [方案總管] 中按兩下結構描述以開啟它。  
  
2. 選取 **結構描述**在結構描述樹狀檢視頂端的節點。  
  
3. 如有需要，請按 F4，開啟 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 屬性] 視窗。  
  
4. 在 屬性 視窗中，在**進階**類別目錄中的值部分**匯入**屬性中，按一下省略符號 (**...**) 按鈕。  
  
5. 在 **匯入**對話方塊中，於**匯入新結構描述為**清單中，選取**XSD 匯入**， **XSD 包含**，或**XSD重新定義**適當地，然後按一下 **新增**。  
  
6. 在  **BizTalk 型別選擇器**對話方塊方塊中，展開**結構描述**節點，在專案樹狀結構中，選取您想要匯入、 包括或重新定義，然後按一下 結構描述**確定**。  
  
7. 在 [**匯入**] 對話方塊中，按一下**確定**。  
  
    適當 XSD 指示詞，來實作匯入、 包含或重新定義作業新增至**結構描述**在 XSD 檢視中，包括新的項目**匯入**，**包括**，或**redefine**項目，視需要。  
  
> [!IMPORTANT]
>  請確定您瞭解這三種機制的不同目的，例如它們在命名空間需求方面的差異。 您可以隨時將其刪除先前已匯入、 包含或重新定義結構描述，，然後使用其中一個其他兩個機制，但根據如何廣泛您已參考該結構描述，您可能需要據此修改您的結構描述。  
  
> [!IMPORTANT]
>  在某個結構描述中匯入、包含和重新定義另一個結構描述的 XSD 機制是藉由參考至已匯入、已包含或已重新定義的結構描述來運作。 這表示若您對已匯入、已包含或已重新定義的結構描述進行變更，該變更將會反映在包含匯入、包含或重新定義參考的結構描述中。  
  
## <a name="see-also"></a>另請參閱  
 [管理專案中的結構描述](../core/managing-schemas-within-projects.md)   
 [如何建立另一個節點或類型的參考](../core/how-to-create-references-to-another-node-or-type.md)