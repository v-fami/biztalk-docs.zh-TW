---
title: 子順序考量 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4f7aa81-5c08-4932-9e28-31e22e037999
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef7e2783bea6c67301c704319035ee0617296eed
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977159"
---
# <a name="child-order-considerations"></a>子順序考量

## <a name="requirements-for-header-in-a-flat-file"></a>一般檔案中的標頭需求
有兩個相關的特殊考量適用於設定時的分隔式一般檔案的案例**子系順序**屬性。 第一個實例是與一般檔案文件具有標頭、內文及結尾 (選擇性) 的情況相關。 在這些實例中，您必須遵守下列需求：  

- 您必須設定**子系順序**屬性的 （分隔） 根記錄要的標頭**後置**。  

- 若有結尾，您必須設定**子系順序**屬性的內文的 （分隔） 根記錄**後置**。  

- 如果沒有結尾，您可以設定**子系順序**的內文的 （分隔） 根記錄的屬性**前置詞**， **InFix**，或**後置詞**.  

- 若有結尾，您可以設定**子系順序**屬性以該結尾的 （分隔） 根記錄**前置詞**，**中置**，或**後置詞**.  

- 您可以設定**子系順序**屬性的標頭、 內文和結尾中的，以分隔附屬記錄**前置詞**，**中置**，或**後置**.  

  第二個相關的案例分隔式一般檔案和**子系順序**屬性是根據針對節點預期的執行階段元件，必須設定這個屬性。 正確的設定，如**子系順序**屬性可能不明顯的根節點和群組節點，如下所示：  

- **根節點。** 假設有一個典型的一般檔案，其結構是由記錄後面加上 CR/LF 的組合所構成。 分隔符號會分隔檔案中的記錄，且順序通常是記錄、分隔符號、記錄、分隔符號等等。 在此情況下，分隔符號一律會跟資料，其對應至**子系順序**屬性設定**後置**。  

- **群組節點。** 顯示在 BizTalk Server 和結構描述之 XSD 表示法中的群組節點不會明確出現在執行個體訊息的一般檔案表示法中。 假設有一筆訂單 (PO) 包含每個明細項目記錄之集合，而這些記錄會重複多次來表示單一 PO 中的多個明細項目。 這類訊息的結構描述可能會包含名為 LineItems 做為重複組 （有時是概念性的） 容器的節點： 在執行個體訊息的一般檔案表示法，LineItems 容器是在本質上，由概念資料和分隔符號，適當的順序在執行個體訊息的 XML 表示法，LineItems 容器是明確的形式出現**LineItems** XML 中的項目。  

  假設有一個訊息包含根節點並僅含有一個群組節點。 我們可以很容易看出，輸入資料流的最後一個分隔符號會屬於根節點。 因此，概念性迴圈中的資料/分隔符號順序，就只不過是一或多筆明細項目記錄。 只有在超過一筆明細項目記錄的情況下，才會有分隔符號來分隔它們。 因此，分隔符號的數目會比被分隔的項目組少一，且分隔符號會位於被分隔的項目之間，此結構稱為 [中置]。  

## <a name="see-also"></a>另請參閱  
- [分隔記錄考量](../core/delimited-record-considerations.md)   
- **子系順序 （一般檔案結構描述中的節點屬性）** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
