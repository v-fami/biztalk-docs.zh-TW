---
title: 執行個體使用屬性升級處理訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 753571b8-4609-4ac4-a974-8bd6dfecb077
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 288657d43443582c5a05df5dd6e67059eca572e9
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="instance-message-processing-using-property-promotion"></a>使用屬性升級處理執行個體訊息
使用 升級屬性 **屬性欄位** 方法需要建立屬性結構描述。 如需有關如何建立屬性結構描述的詳細資訊，請參閱[如何建立屬性結構描述](../core/how-to-create-property-schemas.md)。 當您使用所有的屬性升級 **升級屬性** 對話方塊中，以存取使用 **升級屬性** 屬性 **結構描述** 訊息結構描述中的節點。  
  
> [!NOTE]
>  您必須選擇可升級屬性的管線，才能存取和使用升級屬性。 例如，如果您使用 PassthruReceive 管線，則不會升級任何屬性，因此以內容為基礎的路由和其他功能將不會如預期運作。  
  
 在 **升級屬性** 對話方塊方塊中，請確定 **屬性欄位** 在對話方塊的右邊選取索引標籤。 接下來，請確定適當的屬性結構描述包含在屬性結構描述清單頂端的 **屬性欄位**  索引標籤。如有必要，使用 資料夾 按鈕來選取適當的屬性結構描述使用**BizTalk 型別選擇器** 對話方塊。 接下來，依序展開的節點在結構描述樹狀目錄中，尋找並選取對話方塊左側 **欄位項目** 節點或 **欄位屬性** 節點，您想要升級為屬性欄位，然後按一下  **新增**。 最後，使用下拉式清單中的 **屬性** 資料行的 **屬性-欄位字典** 要選取的資料表 **欄位項目** 要升級的屬性與相關聯的屬性結構描述中的節點。 如需升級為屬性欄位使用的逐步指示**升級屬性**對話方塊，請參閱[如何將資料複製到訊息內容做為屬性欄位](../core/how-to-copy-data-to-the-message-context-as-property-fields.md)。  
  
> [!NOTE]
>  您也可以升級 **記錄** 節點 **欄位項目** 屬性結構描述，但是只有在節點 **內容類型** 屬性 **記錄** 節點設定為 **SimpleContent**。  
  
> [!NOTE]
>  相同的屬性可以在一個結構描述中多次升級，只要這些升級皆在不同的根節點執行即可。 這是因為會針對單一根節點驗證訊息，且只有在該根節點之下升級的屬性才能在執行階段評估。  
  
 若要移除 **欄位項目** 節點或 **欄位屬性** 節點從一組屬性升級 「 屬性欄位，選取 升級的屬性 **屬性-欄位字典** 資料表上 **屬性欄位** 索引標籤，然後再按一下 **移除**。  
  
 **節點路徑** 中的資料行 **屬性-欄位字典** 資料表顯示對應到已升級屬性的結構描述節點的 XPath。 您可以使用來直接編輯這個值 **編輯執行個體 XPath** 對話方塊。 您可以開啟此對話方塊中，依序按一下省略符號 (**...**) 時選取該儲存格會顯示在對應的資料格右邊的按鈕。 當您直接編輯 XPath 值時要非常謹慎，因為無法由「BizTalk 編輯器」解析的 XPath 會阻止進行適當的驗證作業。  
  
 BizTalk 編輯器也提供有效率的命令來升級屬性使用 **屬性欄位** 機制。 此命令稱為 快速升級，而且可供使用 **升階 & #124;快速升級** BizTalk 與快速鍵功能表命令。 此命令會升級所選 **欄位** 節點 (或 **記錄** 節點) 的屬性欄位，會自動建立所指定的屬性結構描述中 **預設屬性結構描述名稱** 屬性 **屬性頁** 包含結構描述 對話方塊。 如需升級為屬性欄位，使用 [快速升級] 命令的逐步指示，請參閱[如何將資料複製到訊息內容做為屬性欄位](../core/how-to-copy-data-to-the-message-context-as-property-fields.md)。  
  
 當您使用屬性欄位機制升級屬性時，會新增兩個 XML 結構描述定義 (XSD) 語言片段至訊息結構描述的 XSD 表示法。 第一個 XSD 片段是與相關聯的註解片段 **結構描述** 項目會識別對應屬性結構描述，如下列範例所示︰  
  
```  
<xs:annotation>  
    <xs:appinfo>  
        <b:imports>  
            <b:namespace prefix="ns0"  
                uri="http://BizTalk_Server_Project1.PropertySchema1"  
                location=".\propertyschema1.xsd" />  
        </b:imports>  
    </xs:appinfo>  
</xs:annotation>  
```  
  
 第二個 XSD 片段是與相關聯的註解片段 **根** 項目 （不論是否它已重新命名），識別 **欄位項目** 節點或 **欄位屬性** 已使用屬性升級的節點值欄位機制，如下列範例所示︰  
  
```  
<xs:annotation>  
    <xs:appinfo>  
        <b:properties>  
            <b:property name="ns0:PromProp1"  
                xpath="/*[local-name()='Root' and namespace-  
                 uri()='http://BizTalk_Server_Project1.Schema2']/  
                 *[local-name()='MyRec1']/@*[local-  
                 name()='Field_x0020_1']" />  
            <b:property name="ns0:PromProp2"  
                xpath="/*[local-name()='Root' and namespace-  
                 uri()='http://BizTalk_Server_Project1.Schema2']/  
                 *[local-name()='MyRec1']/*[local-  
                 name()='ProgramManager']/*[local-name()='Name']" />  
        </b:properties>  
    </xs:appinfo>  
</xs:annotation>  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用訊息內容控制訊息處理方式](../core/ways-to-use-message-content-to-control-message-processing.md)   
 [如何將資料複製到訊息內容做為屬性欄位](../core/how-to-copy-data-to-the-message-context-as-property-fields.md)