---
title: 根節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2161f877-835e-434d-a8d1-2426f977d60e
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d8b2746e9e1886b676e656db883579b28898e3d5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019658"
---
# <a name="root-nodes"></a>根節點
在 BizTalk 編輯器中的子節點**結構描述**稱為節點**根**節點。 **根**節點是一種特殊型別的**記錄** 節點，而且有幾個其他的屬性，但是一般**記錄**節點。 **根**節點表示結構描述所描述的文件的類型，可以重新命名視情況。 例如，您可以重新命名**根**讓它描述的結構描述表示，如 purchaseOrder、 orderAcknowledgment 或 shipNotice 的訊息類型的節點。  

 當您在 「 BizTalk 編輯器 」 中，建立新的 XML 結構描述**結構描述**節點和一個**根**節點會自動建立。 您可以建立其他**根**節點的子系**結構描述**節點; 這可讓您建立單一的 XML 結構描述定義 (XSD) 語言表示法中的結構描述的程式庫。 例如，您可以建立結構描述程式庫，以描述與傳送訂單、命名各種根節點 purchaseOrder、orderAcknowledgment 和 shipNotice 相關之訊息的各種結構描述。  

## <a name="xsd-representation"></a>XSD 表示法  
 下列範例顯示的行中對應的結構描述之 XSD 表示法**根**在樹狀檢視中的結構描述的節點。  

```  
<?xml version="1.0" encoding="utf-16" ?>  
<xs:schema xmlns="http://BizTalk_Server_Project1.Schema2"  
    xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
    targetNamespace="http://BizTalk_Server_Project1.Schema2"  
    xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name="Root">  
        <xs:complexType />   
    </xs:element>  
</xs:schema>  
```  

 **根**在 「 BizTalk 編輯器 」 中的節點代表對應的 XML 執行個體的問題中的訊息中的主要項目。 例如，如果**根**特定結構描述的節點已重新命名為 purchaseOrder，對應的 XSD 表示法會有下列的高階結構。  

```  
<?xml version="1.0" encoding="utf-16" ?>  
<xs:schema xmlns="http://BizTalk_Server_Project1.Schema2"  
    xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
    targetNamespace="http://BizTalk_Server_Project1.Schema2"  
    xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name="">  
        <xs:complexType>   
            ...  
        </xs:complexType>   
    </xs:element>  
</xs:schema>  
```  

 對應的 XML 執行個體訊息必須具有下列的基本結構。  

```  
<?xml version="1.0"?>  
<purchaseOrder ...>  
    ...  
</purchaseOrder>  
```  

> [!NOTE]
>  根節點不能有**欄位**屬性。 **欄位**屬性附加至**根**節點不會儲存與結構描述。  

## <a name="see-also"></a>另請參閱  
- [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
- [節點屬性](../core/node-properties.md)   
- **記錄節點屬性**  [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
- [如何設定節點屬性](../core/how-to-set-node-properties.md)
