---
title: "如何將資料複製到訊息內容，做為辨別欄位 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 004a13ca-a162-4a5e-9f72-8a5c55bbb7a6
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ea68bc0b83c5a8f886416107e1dc98ea8ad8d30
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-data-to-the-message-context-as-distinguished-fields"></a><span data-ttu-id="f5bb0-102">如何將資料複製到訊息內容做為辨別欄位</span><span class="sxs-lookup"><span data-stu-id="f5bb0-102">How to Copy Data to the Message Context as Distinguished Fields</span></span>
<span data-ttu-id="f5bb0-103">本主題提供逐步指示將屬性升級為**辨別欄位**。</span><span class="sxs-lookup"><span data-stu-id="f5bb0-103">This topic provides step-by-step instructions for promoting a property as a **Distinguished Field**.</span></span>  
  
 <span data-ttu-id="f5bb0-104">您可能會選擇**辨別欄位**升級，而不**屬性欄位**升級，原因如下：</span><span class="sxs-lookup"><span data-stu-id="f5bb0-104">You might choose **Distinguished Field** promotion over **Property Field** promotion for the following reasons:</span></span>  
  
-   <span data-ttu-id="f5bb0-105">**屬性欄位**值的限制為 255 個字元的長度。</span><span class="sxs-lookup"><span data-stu-id="f5bb0-105">**Property Field** values are limited to 255 characters in length.</span></span>  
  
-   <span data-ttu-id="f5bb0-106">**屬性欄位**值會儲存在資料庫中，，因此需要更多成本負擔比**辨別欄位**。</span><span class="sxs-lookup"><span data-stu-id="f5bb0-106">**Property Field** values are stored in a database, and therefore have more overhead than **Distinguished Fields**.</span></span> <span data-ttu-id="f5bb0-107">**辨別欄位**不需要任何額外的存放裝置; 它們是基本上別名**XPath**，因此能讓協調流程可以更輕鬆地從訊息中直接存取相關的值。</span><span class="sxs-lookup"><span data-stu-id="f5bb0-107">**Distinguished Fields** do not require any additional storage; they are essentially an alias for an **XPath**, thereby allowing orchestrations to more easily access the relevant values directly from the message.</span></span>  
  
### <a name="to-promote-a-property-as-a-distinguished-field"></a><span data-ttu-id="f5bb0-108">升級做為辨別欄位的屬性</span><span class="sxs-lookup"><span data-stu-id="f5bb0-108">To promote a property as a Distinguished Field</span></span>  
  
1.  <span data-ttu-id="f5bb0-109">在 [BizTalk 編輯器] 中，開啟您要升級一或多個屬性的結構描述，然後選取 （第一個）**欄位項目**，**欄位屬性**，或**記錄**節點您想要升級作為**辨別欄位**。</span><span class="sxs-lookup"><span data-stu-id="f5bb0-109">In BizTalk Editor, open the schema for which you want to promote one or more properties, and then select the (first) **Field Element**, **Field Attribute**, or **Record** node that you want to promote as a **Distinguished Field**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f5bb0-110">記錄節點永遠不會升級為**辨別欄位**，不論它們包含的內容類型。</span><span class="sxs-lookup"><span data-stu-id="f5bb0-110">Record nodes can never be promoted as **Distinguished Fields**, regardless of the type of content they contain.</span></span>  
  
2.  <span data-ttu-id="f5bb0-111">以滑鼠右鍵按一下選取的節點中，按一下**升階**，然後按一下 **顯示升級**。</span><span class="sxs-lookup"><span data-stu-id="f5bb0-111">Right-click the selected node, click **Promote**, and then click **Show Promotions**.</span></span>  
  
     <span data-ttu-id="f5bb0-112">**升級屬性**對話方塊隨即開啟與選取的節點顯示為已選取對話方塊左側的結構描述樹狀目錄中的工作。</span><span class="sxs-lookup"><span data-stu-id="f5bb0-112">The **Promote Properties** dialog box opens with the selected node showing as selected in the schema tree on the left side of the dialog box.</span></span>  
  
3.  <span data-ttu-id="f5bb0-113">在**升級屬性**對話方塊中，選取**辨別欄位** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f5bb0-113">In the **Promote Properties** dialog box, select the **Distinguished Fields** tab.</span></span>  
  
4.  <span data-ttu-id="f5bb0-114">與要升級仍左邊的結構描述樹狀目錄中選取節點**升級屬性**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="f5bb0-114">With the node to be promoted still selected in the schema tree on the left side of the **Promote Properties** dialog box, click **Add**.</span></span>  
  
     <span data-ttu-id="f5bb0-115">如果允許，選取的節點加入至清單上**辨別欄位** 索引標籤。若不允許，則訊息方塊會提供解釋。</span><span class="sxs-lookup"><span data-stu-id="f5bb0-115">If allowed, the selected node is added to the list on the **Distinguished Fields** tab. If not allowed, a message box provides an explanation.</span></span>  
  
5.  <span data-ttu-id="f5bb0-116">您可以在對話方塊中按一下左邊的結構描述樹狀目錄中選取用於升級的其他節點**新增**之後每個選取項目。</span><span class="sxs-lookup"><span data-stu-id="f5bb0-116">You can select additional nodes for promotion in the schema tree on the left side of the dialog box, clicking **Add** after each selection.</span></span>  
  
6.  <span data-ttu-id="f5bb0-117">完成後，按**確定**。</span><span class="sxs-lookup"><span data-stu-id="f5bb0-117">When complete, click **OK**.</span></span>  
  
     <span data-ttu-id="f5bb0-118">您已選取要升級的節點現在都會**辨別欄位**。</span><span class="sxs-lookup"><span data-stu-id="f5bb0-118">The nodes that you selected to promote are now **Distinguished Fields**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5bb0-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5bb0-119">See Also</span></span>  
 <span data-ttu-id="f5bb0-120">[升級屬性](../core/promoting-properties.md) </span><span class="sxs-lookup"><span data-stu-id="f5bb0-120">[Promoting Properties](../core/promoting-properties.md) </span></span>  
 <span data-ttu-id="f5bb0-121">[如何建立屬性結構描述](../core/how-to-create-property-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="f5bb0-121">[How to Create Property Schemas](../core/how-to-create-property-schemas.md) </span></span>  
 [<span data-ttu-id="f5bb0-122">使用訊息內容控制訊息處理方式</span><span class="sxs-lookup"><span data-stu-id="f5bb0-122">Ways to Use Message Content to Control Message Processing</span></span>](../core/ways-to-use-message-content-to-control-message-processing.md)