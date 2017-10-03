---
title: "執行個體使用屬性升級處理訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 753571b8-4609-4ac4-a974-8bd6dfecb077
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 288657d43443582c5a05df5dd6e67059eca572e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="instance-message-processing-using-property-promotion"></a><span data-ttu-id="cab38-102">使用屬性升級處理執行個體訊息</span><span class="sxs-lookup"><span data-stu-id="cab38-102">Instance Message Processing Using Property Promotion</span></span>
<span data-ttu-id="cab38-103">使用升級屬性**屬性欄位**方法需要建立屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="cab38-103">Promoting properties by using the **Property Field** method requires the creation of a property schema.</span></span> <span data-ttu-id="cab38-104">如需有關如何建立屬性結構描述的詳細資訊，請參閱[如何建立屬性結構描述](../core/how-to-create-property-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="cab38-104">For more information about creating a property schema, see [How to Create Property Schemas](../core/how-to-create-property-schemas.md).</span></span> <span data-ttu-id="cab38-105">當您使用所有屬性升級，**升級屬性**對話方塊中，以存取使用**升級屬性**屬性**結構描述**中的節點訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="cab38-105">As with all property promotion, you use the **Promote Properties** dialog box, which is accessible by using the **Promote Properties** property of the **Schema** node in message schemas.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cab38-106">您必須選擇可升級屬性的管線，才能存取和使用升級屬性。</span><span class="sxs-lookup"><span data-stu-id="cab38-106">You must choose a pipeline that promotes properties in order to access and use the promote properties.</span></span> <span data-ttu-id="cab38-107">例如，如果您使用 PassthruReceive 管線，則不會升級任何屬性，因此以內容為基礎的路由和其他功能將不會如預期運作。</span><span class="sxs-lookup"><span data-stu-id="cab38-107">For example, if you use the PassthruReceive pipeline, no properties will be promoted; as a result, content-based routing and other functionality will not work as expected.</span></span>  
  
 <span data-ttu-id="cab38-108">在**升級屬性**對話方塊方塊中，請確定**屬性欄位**選取在對話方塊右邊索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cab38-108">In the **Promote Properties** dialog box, make sure the **Property Fields** tab is selected in the right side of the dialog box.</span></span> <span data-ttu-id="cab38-109">接下來，確定適當的屬性結構描述清單中有包含屬性結構描述頂端**屬性欄位** 索引標籤。如有必要，使用 資料夾 按鈕來選取適當的屬性結構描述使用**BizTalk 型別選擇器** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cab38-109">Next, ensure the appropriate property schema is included in the Property Schemas List at the top of the **Property Fields** tab. If necessary, use the folder button to select the appropriate property schema by using the **BizTalk Type Picker** dialog box.</span></span> <span data-ttu-id="cab38-110">接下來，展開 節點在結構描述樹狀目錄中，尋找並選取對話方塊左側**欄位項目**節點或**欄位屬性**您想要升級為屬性欄位，然後按一下 的節點**新增**。</span><span class="sxs-lookup"><span data-stu-id="cab38-110">Next, expand the nodes in the schema tree on the left side of the dialog box to find and select the **Field Element** node or **Field Attribute** node that you want to promote as a property field, and then click **Add**.</span></span> <span data-ttu-id="cab38-111">最後，使用下拉式清單中的**屬性**資料行**屬性-欄位字典**要選取的資料表**欄位項目**要與屬性結構描述中的節點升級的屬性相關聯。</span><span class="sxs-lookup"><span data-stu-id="cab38-111">Finally, use the drop-down list in the **Property** column of the **Property-Fields dictionary** table to select a **Field Element** node in a property schema with which to associate the promoted property.</span></span> <span data-ttu-id="cab38-112">如需升級為屬性欄位使用的逐步指示**升級屬性**對話方塊，請參閱[如何將資料複製到訊息內容做為屬性欄位](../core/how-to-copy-data-to-the-message-context-as-property-fields.md)。</span><span class="sxs-lookup"><span data-stu-id="cab38-112">For step-by-step instructions about promoting properties to property fields using the **Promote Properties** dialog ox, see [How to Copy Data to the Message Context as Property Fields](../core/how-to-copy-data-to-the-message-context-as-property-fields.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cab38-113">您也可以升級**記錄**節點**欄位項目**屬性結構描述，但是只有在節點**內容類型**屬性**記錄**節點設定為**SimpleContent**。</span><span class="sxs-lookup"><span data-stu-id="cab38-113">You can also promote a **Record** node to a **Field Element** node in the property schema, but only if the **Content Type** property of the **Record** node is set to **SimpleContent**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cab38-114">相同的屬性可以在一個結構描述中多次升級，只要這些升級皆在不同的根節點執行即可。</span><span class="sxs-lookup"><span data-stu-id="cab38-114">The same property can be promoted multiple times within a schema as long as all of these promotions are performed under different root nodes.</span></span> <span data-ttu-id="cab38-115">這是因為會針對單一根節點驗證訊息，且只有在該根節點之下升級的屬性才能在執行階段評估。</span><span class="sxs-lookup"><span data-stu-id="cab38-115">This is because the message is validated against a single root node and only properties promoted under that root node are evaluated at run time.</span></span>  
  
 <span data-ttu-id="cab38-116">若要移除**欄位項目**節點或**欄位屬性**節點從一組屬性會升級為屬性欄位，選取 升級的屬性**屬性-欄位字典**資料表**屬性欄位**索引標籤，然後再按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="cab38-116">To remove a **Field Element** node or **Field Attribute** node from the set of properties being promoted as property fields, select the promoted property in the **Property-Fields dictionary** table on the **Property Fields** tab, and then click **Remove**.</span></span>  
  
 <span data-ttu-id="cab38-117">**節點路徑**中的資料行**屬性-欄位字典**資料表顯示對應到已升級屬性的結構描述節點的 XPath。</span><span class="sxs-lookup"><span data-stu-id="cab38-117">The **Node Path** column in the **Property-Fields dictionary** table shows the XPath to the schema node corresponding to the promoted property.</span></span> <span data-ttu-id="cab38-118">您可以編輯這個值是直接使用**編輯執行個體 XPath**  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cab38-118">You can edit this value directly by using the **Edit Instance XPath** dialog box.</span></span> <span data-ttu-id="cab38-119">您可以開啟此對話方塊中，依序按一下省略符號 (**...**) 當您選取該資料格時，會出現在對應的資料格的右端的按鈕。</span><span class="sxs-lookup"><span data-stu-id="cab38-119">You can open this dialog box by clicking the ellipsis (**...**) button that appears at the right end of the corresponding cell when you select that cell.</span></span> <span data-ttu-id="cab38-120">當您直接編輯 XPath 值時要非常謹慎，因為無法由「BizTalk 編輯器」解析的 XPath 會阻止進行適當的驗證作業。</span><span class="sxs-lookup"><span data-stu-id="cab38-120">Care must be taken when editing XPath values directly because XPaths that cannot be resolved by BizTalk Editor will prevent proper validation operations.</span></span>  
  
 <span data-ttu-id="cab38-121">BizTalk 編輯器也會提供簡化的命令以升級使用的屬性**屬性欄位**機制。</span><span class="sxs-lookup"><span data-stu-id="cab38-121">BizTalk Editor also provides a streamlined command for promoting properties using the **Property Field** mechanism.</span></span> <span data-ttu-id="cab38-122">此命令稱為快速升級，而且可以透過**升階 &#124;快速升級**BizTalk 與快速鍵功能表命令。</span><span class="sxs-lookup"><span data-stu-id="cab38-122">This command is called Quick Promotion, and it is available using the **Promote &#124; Quick Promotion** command on the BizTalk and shortcut menus.</span></span> <span data-ttu-id="cab38-123">此命令會升級所選**欄位**節點 (或**記錄**節點) 會自動建立所指定的屬性結構描述中為屬性欄位**預設屬性結構描述名稱**屬性**屬性頁**包含結構描述 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cab38-123">This command promotes the selected **Field** node (or **Record** node) to a property field that is automatically created in the property schema specified by the **Default Property Schema Name** property in the **Property Pages** dialog box for the containing schema.</span></span> <span data-ttu-id="cab38-124">如需升級為屬性欄位，使用 [快速升級] 命令的逐步指示，請參閱[如何將資料複製到訊息內容做為屬性欄位](../core/how-to-copy-data-to-the-message-context-as-property-fields.md)。</span><span class="sxs-lookup"><span data-stu-id="cab38-124">For step-by-step instructions about promoting properties to property fields using the Quick Promotion command, see [How to Copy Data to the Message Context as Property Fields](../core/how-to-copy-data-to-the-message-context-as-property-fields.md).</span></span>  
  
 <span data-ttu-id="cab38-125">當您使用屬性欄位機制升級屬性時，會新增兩個 XML 結構描述定義 (XSD) 語言片段至訊息結構描述的 XSD 表示法。</span><span class="sxs-lookup"><span data-stu-id="cab38-125">When you promote a property by using the property field mechanism, two XML Schema definition (XSD) language fragments are added to the XSD representation of the message schema.</span></span> <span data-ttu-id="cab38-126">第一個 XSD 片段是與相關聯的註解片段**結構描述**項目會識別對應的屬性結構描述，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="cab38-126">The first XSD fragment is an annotation fragment associated with the **schema** element that identifies the corresponding property schema, as in the following example:</span></span>  
  
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
  
 <span data-ttu-id="cab38-127">第二個 XSD 片段是與相關聯的註解片段**根**項目 （不論是否它已重新命名），識別**欄位項目**節點或**欄位屬性**已使用屬性升級的節點值欄位的機制，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="cab38-127">The second XSD fragment is an annotation fragment associated with the **Root** element (regardless of whether it has been renamed) that identifies the **Field Element** node or **Field Attribute** node values that have been promoted by using the property field mechanism, as in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cab38-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cab38-128">See Also</span></span>  
 <span data-ttu-id="cab38-129">[使用訊息內容控制訊息處理方式](../core/ways-to-use-message-content-to-control-message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="cab38-129">[Ways to Use Message Content to Control Message Processing](../core/ways-to-use-message-content-to-control-message-processing.md) </span></span>  
 [<span data-ttu-id="cab38-130">如何將資料複製到訊息內容做為屬性欄位</span><span class="sxs-lookup"><span data-stu-id="cab38-130">How to Copy Data to the Message Context as Property Fields</span></span>](../core/how-to-copy-data-to-the-message-context-as-property-fields.md)