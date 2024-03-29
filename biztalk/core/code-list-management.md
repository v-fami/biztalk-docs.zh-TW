---
title: 程式碼清單管理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a924c814-d077-4aea-bacb-bf2e8a3dee01
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a28126d7acdb7e5d97b6aaa9924cea455c5fad1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010727"
---
# <a name="code-list-management"></a>程式碼清單管理

## <a name="overview"></a>概觀
您可以使用 XSD 指定對項目或屬性有效的一組特定值。 這項功能是可透過**列舉型別**項目。 當您衍生的資料類型**欄位項目**或是**欄位屬性**由限制，其中會變成可供您在 [屬性] 節點**限制**類別是**列舉型別**屬性。 使用這個屬性，您可以開啟**列舉型別編輯器**對話方塊中，您可以在其中輸入應該被視為有效的相對應的項目或執行個體訊息中的屬性的值。  

 Microsoft BizTalk Server 提供一種替代且更有效率的方式，來管理您結構描述中的列舉，稱之為程式碼清單。 程式碼清單使用 Microsoft Access 資料庫儲存您各種列舉的選擇，可讓您以更集中的方式管理它們。 此外，如果您要使用的列舉值包含非直覺式數值代碼，必須在該表單使用輸入**列舉型別**屬性中，您在程式碼清單使用 Access 資料庫中建立的資料表功能包括這些數值的文字描述。 文字描述會用於**CodeList**  對話方塊中，而不是與其等同的模糊數值項目。  

## <a name="use-the-code-list"></a>使用程式碼清單  
 若要使用程式碼清單功能，您必須執行數個不同的步驟，包括：  

- 您必須建立含有適當具名資料表 (含有所需的資料行) 的 Access 資料庫，並且在其中填入值。  

  - 資料表的名稱是組成**標準**並**標準版本**的屬性**結構描述**節點，以底線 (_) 字元分隔。 比方說，如果您已設定**標準**屬性**結構描述**節點，以 XML 和**標準版本**屬性設為 MyVersion1，所指定的 Access 資料庫**程式碼清單資料庫**屬性必須具有名為 XML_MyVersion1 的資料表。  

    這些屬性的更多有關[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。

  - 此資料表必須有三個資料行，一般命名為 [Code]、[Value] 及 [Desc]。第一個資料行可以識別彼此相關，提供可能對應至所選的資料允許的列舉型別選擇每個這類的資料列的資料列**欄位項目**或**欄位屬性**節點。 第一個資料行中值相同的所有資料列會構成一個群組。 這些值通常是整數，但也可以是不含空格的任意字串。  

     資料表中每個資料列的第二和第三個資料行，必須分別設為包含每個可能之列舉值的對應值和文字表示法。  

     例如，下列要和 [程式碼清單] 功能搭配使用的 Access 資料庫資料表表示法，包含兩組三個相關的列舉值。 第一個資料行中的特定值是任意值，並用來和相關資料列建立關聯。  


    | 程式碼 | ReplTest1 |  Desc  |
    |------|-------|--------|
    |  @shouldalert   |  13   |  紅色   |
    |  @shouldalert   |  16   | 綠色  |
    |  @shouldalert   |  19   |  藍色  |
    |  2   |   @shouldalert   | Small  |
    |  2   |   2   | 中 |
    |  2   |   3   | Large  |


- 您必須正確設定的三個屬性**結構描述**節點：  

  -   **程式碼清單資料庫**屬性必須設定為您建立之 Access 資料庫的名稱。  

  -   **標準**並**標準版本**必須設定屬性，使它們以分隔的底線 (_) 字元結合，形成內指定適當的資料表名稱Access 資料庫。  

- 若要真正進行的 Access 資料庫中的值用於選取特定**欄位項目**或**Field 屬性** 節點，您必須設定其兩個屬性：  

  -   您必須設定其**Derived By**屬性設**限制**。 若要設定，您需要的其他屬性**CodeList**，直到您執行此步驟會啟用。  

  -   您必須輸入新的值**CodeList**對應至第一個資料行中值的屬性 (**程式碼**資料行) 的一或多個指定的 Access 資料庫中的資料列。 此動作會識別您要對應至所選的列舉值的集合**欄位項目**或是**Field 屬性**節點。  

       然後您必須按一下省略符號 (**...**) 按鈕位於右邊**CodeList**屬性值欄位，以開啟**CodeList**  對話方塊。 使用核取方塊，在此對話方塊中，選取您想要允許做為合法值對應至所選的執行個體訊息資料的值**欄位項目**或是**Field 屬性**節點。 您只能選取可用值的子集。 例如，以前述資料表為例，如果您輸入值 1 **CodeList**屬性，**程式碼清單**對話方塊將包含紅色、 綠色及藍色的選項。 如果您選取紅色和綠色的核取方塊，並請勿選取核取方塊，藍色，只有前兩個色彩會在 XSD 中顯示為有效的值，為所選**欄位項目**或是**Field 屬性**節點。  

> [!NOTE]
>  **CodeList**並**程式碼清單資料庫**屬性只能在設計階段使用和保存在 XSD 做為對應的設定，如**列舉型別**屬性。 在執行階段，針對驗證所有的值**列舉型別**只顯示屬性。  

> [!CAUTION]
>  針對給定**欄位項目**或**欄位屬性**節點，兩者都使用**列舉型別**屬性和**CodeList**屬性。 使用後一種屬性可能導致以前一種屬性輸入的值遭到覆寫。  

## <a name="see-also"></a>另請參閱  
 [建立結構描述時的考量](../core/considerations-when-creating-schemas.md)