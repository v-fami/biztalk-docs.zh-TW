---
title: "執行個體訊息使用辨別欄位處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b8f3f77-5385-4294-b441-bcb28bdc51b4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4dca22ff1b09a0d1cfb261a9d5726da8b1b17b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="instance-message-processing-using-distinguished-fields"></a><span data-ttu-id="0ac07-102">使用辨別欄位處理執行個體訊息</span><span class="sxs-lookup"><span data-stu-id="0ac07-102">Instance Message Processing Using Distinguished Fields</span></span>
<span data-ttu-id="0ac07-103">使用升級屬性**辨別欄位**機制不需要建立屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="0ac07-103">Promoting properties by using the **Distinguished Field** mechanism does not require the creation of a property schema.</span></span> <span data-ttu-id="0ac07-104">當您使用所有屬性升級，**升級屬性**對話方塊中，以存取使用**升級屬性**屬性**結構描述**中的節點訊息結構描述，或使用**升階 &#124;顯示升級**命令**BizTalk**或捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="0ac07-104">As with all property promotion, you use the **Promote Properties** dialog box, which is accessible by using the **Promote Properties** property of the **Schema** node in message schemas, or by using the **Promote &#124; Show Promotions** command on the **BizTalk** or shortcut menus.</span></span>  
  
 <span data-ttu-id="0ac07-105">在**升級屬性**對話方塊方塊中，確認**辨別欄位**選取在對話方塊右邊索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0ac07-105">In the **Promote Properties** dialog box, ensure the **Distinguished Fields** tab is selected in the right side of the dialog box.</span></span> <span data-ttu-id="0ac07-106">然後展開的節點在結構描述樹狀目錄中，尋找並選取對話方塊左側**欄位項目**節點或**欄位屬性**您想要升級為辨別欄位的節點，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="0ac07-106">Then you expand the nodes in the schema tree on the left side of the dialog box to find and select the **Field Element** node or **Field Attribute** node that you want to promote as a distinguished field, and then click **Add**.</span></span> <span data-ttu-id="0ac07-107">如需升級屬性的逐步指示**辨別欄位**使用**升級屬性** 對話方塊中，請參閱[複製資料至訊息內容做 Distinguished欄位](../core/how-to-copy-data-to-the-message-context-as-distinguished-fields.md)。</span><span class="sxs-lookup"><span data-stu-id="0ac07-107">For step-by-step instructions about promoting properties to **Distinguished Fields** using the **Promote Properties** dialog, see [Copying Data to the Message Context as Distinguished Fields](../core/how-to-copy-data-to-the-message-context-as-distinguished-fields.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ac07-108">您也可以升級**記錄**節點至欄位項目中的節點屬性結構描述，但是只有**內容類型**屬性**記錄**節點設定為**SimpleContent**。</span><span class="sxs-lookup"><span data-stu-id="0ac07-108">You can also promote a **Record** node to a Field Element node in the property schema, but only if the **Content Type** property of the **Record** node is set to **SimpleContent**.</span></span>  
  
 <span data-ttu-id="0ac07-109">若要移除的一組要升級為辨別欄位屬性節點，選取 升級的屬性上**辨別欄位**索引標籤，然後按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="0ac07-109">To remove a node from the set of properties being promoted as distinguished fields, select the promoted property on the **Distinguished Fields** tab, and click **Remove**.</span></span>  
  
 <span data-ttu-id="0ac07-110">當您使用辨別欄位機制升級屬性時，會在根項目的註解子項目中新增 XML 結構描述定義 (XSD) 語言片段。</span><span class="sxs-lookup"><span data-stu-id="0ac07-110">When you promote properties by using the distinguished field mechanism, an XML Schema definition (XSD) language fragment is added within the annotation subelement of the root element.</span></span> <span data-ttu-id="0ac07-111">在下列範例中，片段顯示使用辨別欄位機制升級的兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="0ac07-111">In the following example, the fragment shows two properties promoted by using the distinguished field mechanism.</span></span>  
  
```  
<b:properties>  
    <b:property distinguished="true"  
        xpath="/*[local-name()='Record' and namespace-  
         uri()='http://BizTalk_Server_Project1.Schema11']/*[local-  
         name()='test']/*[local-name()='Field1']" />  
    <b:property distinguished="true"  
        xpath="/*[local-name()='Record' and namespace-  
         uri()='http://BizTalk_Server_Project1.Schema11']/*[local-  
         name()='test']/*[local-name()='Field5' and position()='1']" />  
</b:properties>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ac07-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ac07-112">See Also</span></span>  
 <span data-ttu-id="0ac07-113">[使用訊息內容控制訊息處理方式](../core/ways-to-use-message-content-to-control-message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="0ac07-113">[Ways to Use Message Content to Control Message Processing](../core/ways-to-use-message-content-to-control-message-processing.md) </span></span>  
 [<span data-ttu-id="0ac07-114">如何將資料複製到訊息內容做為辨別欄位</span><span class="sxs-lookup"><span data-stu-id="0ac07-114">How to Copy Data to the Message Context as Distinguished Fields</span></span>](../core/how-to-copy-data-to-the-message-context-as-distinguished-fields.md)