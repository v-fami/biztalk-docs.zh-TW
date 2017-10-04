---
title: "屬性結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8018bb72-a037-4eeb-bbbe-dd0cc6209aec
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2fb50536b2521e77994baf0b6457206614b7eed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="property-schemas"></a>屬性結構描述

## <a name="promoted-properties"></a>升級屬性
在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，升級的屬性可以讓各種 BizTalk Server 元件存取資料的主要項目，在此內容中即為送達執行個體訊息內的辨別欄位與屬性欄位，而不需要瞭解如何在訊息本身之中找尋這些項目。 您可以針對不同類型的訊息，決定哪些資料項目需要升級至更高的可見層級。 根據您選擇升級這類欄位的方式，您可能需要建立和定義關聯的屬性結構描述。  
  
> [!NOTE]
>  升級屬性僅限非重複項目/屬性。  
  
 辨別欄位只能在協調流程中存取，不需要建立對應的屬性結構描述。 若您只需要從協調流程中存取升級的訊息資料，可以將資料升級為一或多個辨別欄位。  
  
 屬性欄位可以從各種 BizTalk Server 元件 (包括管線和協調流程) 中存取。 屬性欄位也可用於訊息路由。 若您需要從內容而不是從協調流程存取升級的訊息資料，則必須建立一或多個屬性結構描述以描述要升級的資料。  
  
 屬性結構描述是與訊息結構描述相關聯的特殊結構描述。 它用於將執行個體訊息中的特定值升級為訊息內容。 屬性升級提供集中的機制，以提取您從執行個體訊息中定義的訊息之主要部分，並且讓處理訊息的 BizTalk Server 元件，在處理透過 BizTalk Server 傳送的訊息時更容易存取。  
  
## <a name="create-property-schema-overview"></a>建立屬性結構描述的概觀
 您可以使用 BizTalk Server 的快速升級功能自動建立預設屬性結構描述。 這是建立屬性欄位升級必要的屬性結構描述最容易的方式。 如需如何執行快速升級的詳細資訊，請參閱[如何將資料複製到訊息內容做為屬性欄位](../core/how-to-copy-data-to-the-message-context-as-property-fields.md)。  
  
 您也可以建立新的屬性結構描述。 開啟 BizTalk 專案時，選取 BizTalk 專案，以滑鼠右鍵按一下並選取**新增**，按一下 **新項目**，然後按一下 **結構描述**。  
  
> [!NOTE]
>  - 若屬性結構描述與訊息結構描述相關聯，則這兩個結構描述必須在相同的 BizTalk 專案中。 不支援將屬性結構描述與其相關的訊息結構描述分隔在不同的 BizTalk 專案中。  
>
>  - 如果您有兩個具有相同命名空間的屬性結構描述，則即使這兩個結構描述是在不同的組件中定義，它們將無法在執行階段正確解析。 您將在執行階段收到路由失敗。  

## <a name="distinguished-fields-and-property-fields"></a>辨別的欄位和屬性欄位 
 有兩個屬性升級類型：辨別欄位和屬性欄位。 後者使用屬性結構描述。 在 [BizTalk 編輯器] 中，您管理這兩種類型的屬性升級使用**升級屬性**對話方塊中，您可以使用存取**升級屬性**屬性**結構描述**節點。  
  
> [!NOTE]
>  - 您可升級的值有部分限制。 如需詳細資訊，請參閱中的資料表[升級屬性](../core/promoting-properties.md)。  
>
>  - [辨別] 欄位不會出現在篩選條件運算式。 只有屬性欄位會出現在篩選條件運算式。  
  
 與訊息結構描述比較，屬性結構描述較簡單。 在結構描述樹狀目錄中，您只允許插入**欄位項目**直屬子節點的節點**結構描述**節點，建立兩層的結構。 大部分的情況下，您可以設定的屬性**欄位項目**節點做為您用來處理**欄位項目**訊息結構描述中出現的節點。 限制您只能使用 XSD 簡單類型。  
  
> [!IMPORTANT]
>  您不能重新命名任何一個已經用於其他結構描述的結構描述。 這包含已經建立其升級的屬性結構描述。 若這麼做，所使用的結構描述將找不到其他結構描述，因為它所包含的名稱已經不正確。  
  
 **Property Schema Base**屬性是唯一**欄位項目**節點出現在屬性結構描述。 這個屬性是空白的根據預設，不過可以設定為  **MessageDataPropertyBase**或**MessageContextPropertyBase**，並產生**propSchFieldBase**屬性正在加入**fieldInfo**或其他這些值的其中一種註釋項目。  
  
 當**propSchFieldBase**屬性設為**MessageDataPropertyBase**，這表示 升級屬性的值對應至訊息，例如某些欄位的值中的資料。 當**propSchFieldBase**屬性設為**MessageContextPropertyBase**，就表示升級屬性的值可能會從信封時，例如，其他地方，或者它可能是由設定管線元件。  
  
 **欄位項目**屬性結構描述中的節點也有一個屬性呼叫**機密資訊**，而當設定為**是**，會顯示從保留的相對應的值BizTalk 總管 以及訊息事件和服務執行個體追蹤，因此能保持其機密的性質。  請參閱**機密資訊**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]如需詳細資訊。
  
 以下屬性結構描述的 XML 結構描述定義 (XSD) 語言表示法包含與識別此結構描述為屬性結構描述 (schema_type="property") 的結構描述項目相關聯的註解。 它也包含三種**欄位項目**節點之下**結構描述**節點。 第一個**欄位項目**名為 PromProp1，節點沒有值，定義其**Property Schema Base**屬性，但後面兩個**欄位項目**節點的方式屬性設定為**MessageDataPropertyBase**和**MessageContextPropertyBase**分別。  
  
```  
<?xml version="1.0" encoding="utf-16" ?>   
<xs:schema xmlns="http://BizTalk_Server_Project1.PropertySchema1"  
           xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
           targetNamespace="http://BizTalk_Server_Project1.PropertySchema1"  
           xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:annotation>  
       <xs:appinfo>  
  
        </xs:appinfo>  
    </xs:annotation>  
    <xs:element name="" type="xs:string">  
        <xs:annotation>  
            <xs:appinfo>  
  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
    <xs:element name="" type="xs:string">  
        <xs:annotation>  
            <xs:appinfo>  
  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
    <xs:element name="" type="xs:string">  
        <xs:annotation>  
            <xs:appinfo>  
  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
</xs:schema>  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [不同類型的 BizTalk 結構描述](../core/different-types-of-biztalk-schemas.md)