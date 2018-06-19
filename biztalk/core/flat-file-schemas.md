---
title: 一般檔案結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8009fba7-85f0-4795-9284-5b4e94b3fc72
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 674a862b3966088bb1d75dd17ceacd47c30bdda1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246046"
---
# <a name="flat-file-schemas"></a>一般檔案結構描述

## <a name="purpose-of-flat-file-schemas"></a>一般檔案結構描述的目的
一般檔案結構描述有兩個用途。 定義所有相同記錄與欄位特性 (包含結構) 為 XML 結構描述，並且提供定義轉譯一般檔案執行個體訊息為對等的 XML 執行個體訊息 (反之亦然) 所需的所有一般檔案特性之機制。 在「BizTalk 對應工具」中使用一般檔案結構描述，以定義轉換符合的一般檔案執行個體訊息為不同的目的結構時，前一個用途最為有用。 由「BizTalk 對應工具」中的目的結構描述所定義的目的結構，可能由一般檔案訊息結構描述 (可能為 XML 結構描述) 決定，也可能無法由一般檔案訊息結構描述決定。  
  
 後一個用途，在文件的一般檔案格式及其對等的 XML 格式之間轉譯，使用利用其註解語法新增至 XML 結構描述定義 (XSD) 語言結構描述的延伸資訊組。 以 XSD 觀點，根據它在依決定其結構的結構描述以驗證 XML 執行個體訊息時的可用性而言，此項資訊是不必要的。 不過，XSD 註解語法提供一個方便的機制來儲存內各種不同的範圍，範圍從整個結構描述的資訊儲存為中的註解XSD結構描述內的一般檔案結構資訊**結構描述**項目，為特定的特定記錄或欄位中，儲存為中對應的註解的資訊**元素**或**屬性**項目。  
  
 一般檔案結構描述與其 XML 相應項目相異的另一個特性是執行個體訊息不能與以其內容為基礎決定的結構描述比對。 而是必須指定一組靜態結構描述，以供一般檔案解譯器在執行階段使用。  
  
 若要查看與一般檔案特性相關的其他節點屬性，您需要指定**一般檔案延伸模組**使用**Schema Editor Extensions**屬性**結構描述**節點。 依照預設，它們不會顯示。  
  
 如需專屬於一般檔案結構描述的節點屬性的詳細資訊，請參閱**一般檔案結構描述的增補節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="see-also"></a>另請參閱  
 [不同類型的 BizTalk 結構描述](../core/different-types-of-biztalk-schemas.md)