---
title: "使用其他結構描述的結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02954d46-48ce-4cdf-a012-74c212ce8b6d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 563260031e545b5223697d49992c1ae85bae3891
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="schemas-that-use-other-schemas"></a>使用其他結構描述的結構描述

## <a name="overview"></a>概觀
當您的結構描述變得又大又複雜，或是代表您不同類型之執行個體訊息的結構描述有部分相同時，將較小的結構描述結合成最終定義您計劃與交易夥伴交換之執行個體訊息的結構描述，是很有用的。 例如，您可能會有多個訊息類型，內含需要快遞的送貨地址。 您可以在單一結構描述中定義送貨地址的結構，然後在其他定義如「訂單」、「發票」及「送貨單」等訊息結構描述的其他結構描述中，使用該結構描述。  

## <a name="import-include-and-redefine"></a>匯入、 包含及重新定義  
 XML 結構描述定義 (XSD) 語言提供了三種相關機制，來使用多個 BizTalk 編輯器支援的結構描述。 下表摘要描述這些機制 (由 XSD 所定義) 的特性。  
  
|多重結構描述機制|使用實例|  
|---------------------------|--------------------|  
|匯入|-存取和使用匯入結構描述中定義的類型。<br />-必須使用中，匯入結構描述型別，或從中; 衍生新的類型不能修改類型。<br />-提供一種機制，使用其他命名空間中定義的型別。 事實上，已匯入之結構描述的目標命名空間必須與正在匯入的結構描述不同。<br />-使用**匯入**項目和其**命名空間**和**schemaLocation**屬性，來參照其他的結構描述。|  
|包含|-存取和使用包含結構描述中定義的類型。<br />-必須使用中，包含結構描述型別，或從中; 衍生新的類型不能修改類型。<br />-包含結構描述必須位於相同的目標命名空間包含的結構描述，或包含的結構描述的目標命名空間必須為空白。<br />-使用**包含**項目和其**schemaLocation**屬性，來參照其他的結構描述。|  
|重新定義|-存取和使用已重新定義結構描述中定義的類型。<br />-可以使用已重新定義結構描述中的型別，衍生的新類型，或指定對其的修改。<br />-已重新定義結構描述必須位於相同的目標命名空間重新定義結構描述，或重新定義結構描述的目標命名空間必須為空白。<br />-使用**重新定義**項目和其**schemaLocation**屬性，來參照其他的結構描述。 任何類型的重新定義所指定的**重新定義**項目。 **注意：**使用重新定義機制是進階的 XSD 概念，應該只用於之後您有充分瞭解如何及何時應該使用。|  
  
> [!NOTE]
>  完整的差異和相似性之間匯入的詳細資訊，包括和重新定義機制，請參閱中所列的參照[在網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)。  

## <a name="important-details"></a>重要的詳細資料  
 若要在一個結構描述 (結構描述 2) 內使用在另一個結構描述 (結構描述 1) 中所定義的類型，您必須在結構描述 2 中提供結構描述 1 的參考。 若要這樣做，請使用**匯入**屬性**結構描述**2 中的節點。 當您按一下省略符號 (**...**) 按鈕**匯入**屬性欄位中，**匯入**對話方塊隨即開啟。 在**匯入新結構描述為**下拉式清單中，選取**XSD 匯入**， **XSD Include**，或**XSD Redefine**。 然後按一下 [**新增**開啟**BizTalk 型別選擇器**] 對話方塊，並瀏覽以選取您的 BizTalk 專案內**Schema1**。  
  
 如需這些步驟的詳細指示，請參閱[建立使用其他結構描述的](../core/how-to-create-schemas-that-use-other-schemas.md)。  
  
 當您使用**匯入**對話方塊來匯入、 包含或重新定義另一個結構描述、 一個或多個 XSD 項目**匯入**，**包含**，和**重新定義**加入至您的結構描述，包括適當的屬性和屬性值之 XSD 表示法。 此外，如果是**匯入**元素會加入另一個結構描述的命名空間前置詞宣告**結構描述**項目。  
  
 所有全域型別 (例如**ComplexTypes**， **SimpleTypes**，項目群組、 屬性群組) 匯入/包含/重新定義結構描述中會自動可供所在之結構描述內的使用先前的結構描述匯入、 包含，或重新定義。 例如，全域**ComplexTypes**匯入/包含/重新定義結構描述中定義加入到下拉式清單**資料結構型別**屬性的所有**記錄**匯入、 包含或重新定義結構描述中的節點。 這個屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="see-also"></a>另請參閱  
 [關於結構描述](../core/about-schemas.md)   
 [建立使用其他結構描述的結構描述](../core/how-to-create-schemas-that-use-other-schemas.md)   
 [建立另一個節點或類型的參考](../core/how-to-create-references-to-another-node-or-type.md)