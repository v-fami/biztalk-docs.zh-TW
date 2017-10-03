---
title: "如何使用多部分訊息類型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multi-part message types, parts
- multi-part message types, creating
- multi-part message types, type modifiers
- messages
- multi-part message types, deleting
- orchestrations, messages
- deleting, multi-part messages
- multi-part message types, about multi-part message types
- orchestrations, type modifier
- messages, multi-parts
- creating, multi-part messages
- messages, about messages
ms.assetid: 009a39bd-cfc4-42d9-918c-88ac24bfc370
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f87f210c4b0d2969edc9ddfa27b1d8494310eb6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-multi-part-message-types"></a>如何使用多部分訊息類型
每個訊息都有多部分訊息類型，即是由零或多個訊息部分所組成的訊息的結構描述。 這些部分是由 XML 結構描述定義 (XSD) 語言結構描述或 .NET 類別所定義。 您可以定義自己的多部分訊息類型，也可以使用現有的 .NET 類別和結構描述。  
  
 您可以直接在協調流程內存取或指派訊息部分，也可以使用公開為辨別欄位或屬性欄位的個別訊息部分項目。 如需詳細資訊，請參閱[使用辨別欄位和訊息屬性](../core/using-distinguished-fields-and-property-fields.md)。  
  
> [!NOTE]
>  多部分訊息類型不一定要包含多個部分。  
  
> [!NOTE]
>  可以.NET 類型所定義的訊息部分**XmlDocument**、 可用來包含任意的 XML 文件、 任何的 XML 序列化，.NET 型別或任何.NET 類型支援自訂序列化。  
  
## <a name="add-a-multi-part-message-type"></a>新增多部分訊息類型  
  
1.  在**協調流程檢視**視窗中，展開 **類型**節點。  
  
2.  以滑鼠右鍵按一下**多部分訊息類型**，然後按一下 **新多部分訊息類型**。  
  
     **多部分訊息類型**資料夾，則會展開摺疊，並具有一個預設訊息部分加入新的多部分訊息類型。  
  
3.  命名多部分訊息類型和提供的訊息部分。  
  
     如果您的多部分訊息類型需要一個以上的訊息部分，您可以新增其他部分將名稱指派給\<新增 > 訊息部分。  
  
4.  將每個訊息部分與類型 (例如，.NET 類別或結構描述) 建立關聯。  
  
## <a name="remove-a-multi-part-message-type"></a>移除多部分訊息類型  
  
-   在**協調流程檢視**視窗中，以滑鼠右鍵按一下的多部分訊息的類型，您想要移除，然後按一下 **刪除**。  
  
    > [!NOTE]
    >  從協調流程移除多部分訊息類型，也會從用到它的訊息中移除類型資訊。  
  
    > [!NOTE]
    >  顯示為唯讀的項目定義在另一個協調流程中。  
  
## <a name="remove-a-part-from-a-multi-part-message-type"></a>移除多部分訊息類型的組件  
  
-   在**協調流程檢視**視窗中，以滑鼠右鍵按一下您想要移除，然後按一下組的件**刪除**。  
  
    > [!NOTE]
    >  如果您無法刪除訊息類型的訊息部分**訊息內文部分**屬性設定為 true。 您必須先設定**訊息內文部分**屬性設為 True 的訊息類型的組件的另一個。  
  
## <a name="set-the-type-modifier-for-a-multi-part-message-type"></a>設定多部分訊息類型的型別修飾詞  
  
-   在**屬性**視窗中，設定下列屬性：  
  
    |屬性|Description|  
    |--------------|-----------------|  
    |**型別修飾詞**|決定多部分訊息類型的範圍：<br /><br /> -   **私用 —**存取此多部分訊息類型僅限於包含的模組。<br />-   **公用 —**存取此多部分訊息類型不受任何限制。<br />-   **內部 —**存取此多部分訊息類型限於相同專案中的模組。|  
  
## <a name="add-parts-to-an-existing-multi-part-message"></a>將組件加入至現有的多部分訊息  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可讓您將部分新增至多部分 XLANG 訊息，並且透過大於原始宣告的部分數目的索引來參考訊息部分 (如果有該部分存在的話)。 傳送或接收夾帶數目不定之附件的 SMTP 訊息時，此功能可能會很有用。 實作此功能的方法如下：  
  
-   從您的專案，將參考加入**Microsoft.XLANGs.BaseTypes**。  
  
-   建立的變數 (例如*xlangPart*) 型別的**Microsoft.XLANGs.BaseTypes.XLANGMessage**。  
  
-   呼叫*xlangPart***。AddPart(...)**使用適當的引數，從 「 運算式 」 圖形。  
  
    > [!NOTE]
    >  新增的部分為型別的**XmlDocument**因此您無法加入自訂格式化的訊息部分使用**addpart （)**方法。  
  
> [!NOTE]
>  如果收到包含大於宣告的部分數目的多部分訊息時，有多少部分是在訊息中的協調流程引擎讀取然後建構適當的部分類型符合的組件中宣告的訊息數目的組件類型，然後建構**XmlDocument**組件的其餘部分。  
  
## <a name="see-also"></a>另請參閱  
 **IBaseMessage.AddPart 方法 (COM)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]  
 [在網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)   
 [使用辨別的欄位和屬性欄位](../core/using-distinguished-fields-and-property-fields.md)   
 [協調流程中使用訊息](../core/using-messages-in-orchestrations.md)