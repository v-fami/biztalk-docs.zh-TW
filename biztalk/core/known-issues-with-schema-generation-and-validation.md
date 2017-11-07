---
title: "結構描述產生和驗證的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df1eaa6c-0d3e-4aec-9de0-8b9817b7bb97
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a462ab04aad857bf87b189cafce14bb9c3747e8
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="known-issues-with-schema-generation-and-validation"></a>結構描述的產生和驗證的已知的問題
本主題提供產生和驗證結構描述的已知問題相關資訊。  
  
## <a name="an-instance-message-generated-for-a-positional-record-with-tags-could-be-incorrect"></a>為具有標記的位置記錄產生的執行個體訊息有可能不正確  
 就位置記錄而言，標記可以在欄位之中或是跨越欄位之間。 不論哪一種情況，產生的執行個體將無效，而且可能在剖析階段期間的「剖析引擎」中導致失敗。  
  
 若標記不屬於任何子系 (子記錄或子欄位) 的一部分，就不會發生此問題。  
  
 若要解決此問題，請在結構描述中包含標記的實際值做為預設。 在一般檔案延伸 BizTalk 編輯器中，您可以設定**固定值**或**預設值**屬性的適當位置欄位標籤的值。  
  
## <a name="an-instance-message-generated-for-a-field-with-some-restrictions-may-not-pass-validation"></a>為具有某些限制的欄位所產生的執行個體訊息可能無法通過驗證  
 當您從包含一或多個結構描述產生執行個體訊息時**欄位項目**和**欄位屬性**具有使用限制機制，例如衍生的資料類型的節點當**模式**屬性時，產生這類欄位的範例資料可能不符合需求的限制，因此可以防止使用相同的結構描述，從該執行個體訊息的驗證成功它所產生。  
  
## <a name="an-instance-message-generated-for-a-schema-that-contains-an-infinite-loop-may-not-be-valid"></a>為包含無限迴圈的結構描述所產生的執行個體訊息可能無效。  
 包含節點的循環參考時，您的結構描述可以包含無限迴圈**Min Occurs**大於或等於一，本質上會防止終止條件的屬性值。 您需要人工終止產生執行個體訊息，才能完成產生作業，但是產生的執行個體訊息也因此不符合產生它的結構描述。 這樣的結構描述通常是有問題的。  
  
## <a name="validation-of-xml-instance-fails-for-document-schema-which-has-the-target-namespacehttpwwww3orgxml1998namespace"></a>文件結構描述的 XML 執行個體驗證失敗，其 target namespace="http://www.w3.org/XML/1998/namespace"  
 超連結"http://www.w3.org/XML/1998/namespace"是保留的命名空間，其前置詞應該為"XML"。 您可以手動將前置詞編輯為 "XML"。

## <a name="see-also"></a>另請參閱
這些屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
