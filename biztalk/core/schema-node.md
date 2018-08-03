---
title: 結構描述節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7ea02c2a-ee00-4f44-9086-83d7ac4a8832
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd892e825194afea880d3bde153f472051ce9102
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25972228"
---
# <a name="schema-node"></a>結構描述節點

## <a name="overview"></a>概觀
在 [BizTalk 編輯器] 中，結構描述階層的頂層永遠是**結構描述**節點，無法重新命名。 **結構描述**節點對應至**結構描述**結構描述的 XML 結構描述定義 (XSD) 語言表示法中的項目。  
  
> [!NOTE]
>  在 [BizTalk 編輯器] 中，**結構描述**節點以字串表示\<結構描述\>結構描述樹狀結構檢視中。  
  
 一般而言，屬性**結構描述**節點對應屬性的**結構描述**結構描述之 XSD 表示法中的項目。 如需節點屬性的一般資訊，請參閱[節點屬性](../core/node-properties.md)。 如需屬性的參考資訊**結構描述** 節點，請參閱**結構描述節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
 當您在 「 BizTalk 編輯器 」 中，建立新的 XML 結構描述**結構描述**節點和一個**根**節點會自動建立。  
  
## <a name="xsd-representation"></a>XSD 表示法  
 下列範例所示，以粗體類型，對應至結構描述之 XSD 表示法中的線條**\<結構描述\>** 的結構描述樹狀檢視中的節點。  
  
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
  
## <a name="see-also"></a>請參閱  
 [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
 [節點屬性](../core/node-properties.md)   
 [設定節點屬性](../core/how-to-set-node-properties.md)