---
title: "如何將資料複製到訊息內容做為屬性欄位 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fdfe475-d9b4-4cf9-898f-dbd7e719c27c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18242f30f32974cc32ab5d39a4a9c63650f27ffa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-data-to-the-message-context-as-property-fields"></a><span data-ttu-id="d1106-102">如何將資料複製到訊息內容做為屬性欄位</span><span class="sxs-lookup"><span data-stu-id="d1106-102">How to Copy Data to the Message Context as Property Fields</span></span>
<span data-ttu-id="d1106-103">您可以升級為屬性**屬性欄位**很多相同方式將屬性升級為**辨別欄位**，而且您也可以使用**快速升級**功能簡化程序。</span><span class="sxs-lookup"><span data-stu-id="d1106-103">You can promote a property as a **Property Field** in much the same way as promoting a property as a **Distinguished Field**, and you can also use the **Quick Promotion** feature to streamline the process.</span></span>  
  
 <span data-ttu-id="d1106-104">您可能會選擇**屬性欄位**升級，而不**辨別欄位**升級，原因如下：</span><span class="sxs-lookup"><span data-stu-id="d1106-104">You might choose **Property Field** promotion over **Distinguished Field** promotion for the following reasons:</span></span>  
  
-   <span data-ttu-id="d1106-105">您想要升級的值是少於 255 個字元限制適用於**屬性欄位**。</span><span class="sxs-lookup"><span data-stu-id="d1106-105">The values you want to promote are shorter than the 255 character limitation that applies to **Property Fields**.</span></span>  
  
-   <span data-ttu-id="d1106-106">您需要在協調流程外部可存取所升級的值，像是在管線或連接埠中。</span><span class="sxs-lookup"><span data-stu-id="d1106-106">You need the values that you promote to be accessible outside of orchestrations, such as within pipelines or ports.</span></span>  
  
 <span data-ttu-id="d1106-107">本主題提供逐步指示將屬性升級為**屬性欄位**中這兩種方式。</span><span class="sxs-lookup"><span data-stu-id="d1106-107">This topic provides step-by-step instructions for promoting a property as a **Property Field** in both of these ways.</span></span>  
  
### <a name="to-promote-a-property-as-a-property-field-using-the-promote-properties-dialog-box"></a><span data-ttu-id="d1106-108">使用 [升級屬性] 對話方塊將屬性升級為 [屬性欄位]</span><span class="sxs-lookup"><span data-stu-id="d1106-108">To promote a property as a Property Field using the Promote Properties dialog box</span></span>  
  
1.  <span data-ttu-id="d1106-109">如有必要，建立適當的屬性結構描述，您可以在其中升級屬性。</span><span class="sxs-lookup"><span data-stu-id="d1106-109">If necessary, create an appropriate property schema into which you will promote a property.</span></span> <span data-ttu-id="d1106-110">如需建立屬性結構描述的逐步指示，請參閱[建立屬性結構描述](../core/how-to-create-property-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="d1106-110">For step-by-step instructions for creating property schemas, see [Creating Property Schemas](../core/how-to-create-property-schemas.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d1106-111">此步驟可能不是必要，如果您已經建立屬性結構描述並插入適當**欄位項目**做為子節點的節點**結構描述**節點。</span><span class="sxs-lookup"><span data-stu-id="d1106-111">This step might not be necessary if you have already created a property schema and inserted the appropriate **Field Element** nodes as child nodes of the **Schema** node.</span></span>  
  
2.  <span data-ttu-id="d1106-112">在 [BizTalk 編輯器] 中，開啟您要升級一或多個屬性的結構描述，然後選取 （第一個）**欄位項目**，**欄位屬性**，或**記錄**節點您想要升級作為**屬性欄位**。</span><span class="sxs-lookup"><span data-stu-id="d1106-112">In BizTalk Editor, open the schema for which you want to promote one or more properties, and then select the (first) **Field Element**, **Field Attribute**, or **Record** node that you want to promote as a **Property Field**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d1106-113">您可以只升級**記錄**節點，如果在設定為只包含簡單內容有其**內容型別**屬性設定為**SimpleContent**。</span><span class="sxs-lookup"><span data-stu-id="d1106-113">You can only promote **Record** nodes if they are configured to contain only simple content by having its **Content Type** property set to **SimpleContent**.</span></span>  
  
3.  <span data-ttu-id="d1106-114">以滑鼠右鍵按一下選取的節點中，按一下**升階**，然後按一下 **顯示升級**。</span><span class="sxs-lookup"><span data-stu-id="d1106-114">Right-click the selected node, click **Promote**, and then click **Show Promotions**.</span></span>  
  
     <span data-ttu-id="d1106-115">**升級屬性**對話方塊隨即開啟與選取的節點顯示為已選取對話方塊左側的結構描述樹狀目錄中的工作。</span><span class="sxs-lookup"><span data-stu-id="d1106-115">The **Promote Properties** dialog box opens with the selected node showing as selected in the schema tree on the left side of the dialog box.</span></span>  
  
4.  <span data-ttu-id="d1106-116">在**升級屬性**對話方塊中，選取**屬性欄位** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d1106-116">In the **Promote Properties** dialog box, select the **Property Fields** tab.</span></span>  
  
5.  <span data-ttu-id="d1106-117">確認要升級屬性的屬性結構描述存在於**屬性結構描述清單**屬性欄位 索引標籤中。若已顯示，請跳至步驟 8。</span><span class="sxs-lookup"><span data-stu-id="d1106-117">Confirm that the property schema into which you want to promote a property is present in the **Property Schemas List** in the Property Fields tab. If it is present, skip to step 8.</span></span>  
  
6.  <span data-ttu-id="d1106-118">在**屬性結構描述清單**區段中，按一下**資料夾**圖示。</span><span class="sxs-lookup"><span data-stu-id="d1106-118">In the **Property Schemas List** section, click the **Folder** icon.</span></span> <span data-ttu-id="d1106-119">**BizTalk 型別選擇器** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d1106-119">The **BizTalk Type Picker** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="d1106-120">在**BizTalk 型別選擇器**對話方塊方塊中，瀏覽至適當的屬性結構描述 （您可能已在步驟 1 中建立），選取該結構描述，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d1106-120">In the **BizTalk Type Picker** dialog box, navigate to the appropriate property schema (that you may have created in step 1), select that schema, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d1106-121">（選擇性） 您可以變更藉由變更中適當的字串相關聯的屬性結構描述的命名空間前置詞**前置詞**資料行 欄位。</span><span class="sxs-lookup"><span data-stu-id="d1106-121">Optionally, you can change the namespace prefix associated with the property schema by changing the string in the appropriate **Prefix** column field.</span></span>  
  
8.  <span data-ttu-id="d1106-122">與要升級仍左邊的結構描述樹狀目錄中選取節點**升級屬性**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="d1106-122">With the node to be promoted still selected in the schema tree on the left side of the **Promote Properties** dialog box, click **Add**.</span></span>  
  
     <span data-ttu-id="d1106-123">如果允許，選取的節點會加入至結尾**屬性欄位清單**上**屬性欄位** 索引標籤。若不允許，則訊息方塊會提供解釋。</span><span class="sxs-lookup"><span data-stu-id="d1106-123">If allowed, the selected node is added to the end of the **Property Fields List** on the **Property Fields** tab. If not allowed, a message box provides an explanation.</span></span> <span data-ttu-id="d1106-124">如果不允許，**新增**按鈕未啟用。</span><span class="sxs-lookup"><span data-stu-id="d1106-124">If not allowed, the **Add** button is not enabled.</span></span>  
  
9. <span data-ttu-id="d1106-125">按兩下**屬性**剛加入的資料列的資料行儲存格**屬性欄位清單**，然後在下拉式清單中，選取**屬性結構描述**和對應**欄位項目**您要升級所選取的節點的節點。</span><span class="sxs-lookup"><span data-stu-id="d1106-125">Double-click **Property** column cell for the row you just added to the **Property Fields List**, and then in the drop-down list, select the **Property Schema** and corresponding **Field Element** node into which you want to promote the selected node.</span></span> <span data-ttu-id="d1106-126">下拉式清單值有格式為 X:Y，其中 X 是中的屬性結構描述的命名空間前置詞**屬性結構描述清單**，而 Y 是節點名稱的**欄位項目**該屬性結構描述中的節點。</span><span class="sxs-lookup"><span data-stu-id="d1106-126">Drop-down list values have the form X:Y, where X is the namespace prefix of a property schema in the **Property Schemas List**, and Y is the node name of a **Field Element** node in that property schema.</span></span>  
  
     <span data-ttu-id="d1106-127">下拉式清單中的預設值是第一個屬性結構描述**（欄位項目）**具有不尚未升級的節點會依字母順序排序跨所有相關的屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="d1106-127">The default value in the drop-down list is the first property schema **(Field Element)** node that has not yet been promoted, sorted alphabetically across all relevant property schemas.</span></span> <span data-ttu-id="d1106-128">這很少會是您想要在其中升級指定的結構描述節點之屬性結構描述節點。</span><span class="sxs-lookup"><span data-stu-id="d1106-128">This will rarely be the property schema node into which you intend to promote a given schema node.</span></span>  
  
10. <span data-ttu-id="d1106-129">您可以在對話方塊中按一下左邊的結構描述樹狀目錄中選取用於升級的其他節點**新增**然後執行步驟 9 之後每個選取項目。</span><span class="sxs-lookup"><span data-stu-id="d1106-129">You can select additional nodes for promotion in the schema tree on the left side of the dialog box, clicking **Add** and then performing step 9 after each selection.</span></span>  
  
11. <span data-ttu-id="d1106-130">完成後，按**確定**。</span><span class="sxs-lookup"><span data-stu-id="d1106-130">When complete, click **OK**.</span></span>  
  
     <span data-ttu-id="d1106-131">您已選取要升級的節點現在都會**屬性欄位**和相關聯的特定**欄位項目**屬性結構描述中的節點。</span><span class="sxs-lookup"><span data-stu-id="d1106-131">The nodes that you selected to promote are now **Property Fields** and are associated with a particular **Field Element** node in a property schema.</span></span>  
  
### <a name="to-promote-a-property-as-a-property-field-using-the-quick-promotion-command"></a><span data-ttu-id="d1106-132">使用 [快速升級] 命令將屬性升級為 [屬性欄位]</span><span class="sxs-lookup"><span data-stu-id="d1106-132">To promote a property as a Property Field using the Quick Promotion command</span></span>  
  
1.  <span data-ttu-id="d1106-133">在 [BizTalk 編輯器] 中，開啟您要升級一或多個屬性的結構描述，然後選取 （第一個）**欄位項目**，**欄位屬性**，或**記錄**節點您想要升級作為**屬性欄位**。</span><span class="sxs-lookup"><span data-stu-id="d1106-133">In BizTalk Editor, open the schema for which you want to promote one or more properties, and then select the (first) **Field Element**, **Field Attribute**, or **Record** node that you want to promote as a **Property Field**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d1106-134">您可以只升級**記錄**節點，如果在設定為只包含簡單內容有其**內容型別**屬性設定為**SimpleContent**。</span><span class="sxs-lookup"><span data-stu-id="d1106-134">You can only promote **Record** nodes if they are configured to contain only simple content by having its **Content Type** property set to **SimpleContent**.</span></span>  
  
2.  <span data-ttu-id="d1106-135">以滑鼠右鍵按一下選取的節點中，按一下**升階**，然後按一下 **快速升級**。</span><span class="sxs-lookup"><span data-stu-id="d1106-135">Right-click the selected node, click **Promote**, and then click **Quick Promotion**.</span></span>  
  
     <span data-ttu-id="d1106-136">如果預設屬性結構描述，由**預設屬性結構描述名稱**屬性**屬性頁**相關的結構描述不存在，您必須按一下**確定**在確認對話方塊中建立預設屬性結構描述，並加以設定以適當**欄位項目**適應屬性升級的節點。</span><span class="sxs-lookup"><span data-stu-id="d1106-136">If the default property schema, as defined by the **Default Property Schema Name** property on the **Property Pages** for the relevant schema, does not exist, you must click **OK** in the confirmation dialog to create the default property schema and configure it with an appropriate **Field Element** node to accommodate your property promotion.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1106-137">您可以檢視和管理使用提升的屬性**快速升級**功能開啟**升級屬性**] 對話方塊，然後按一下 [**屬性欄位**索引標籤。如需逐步指示，開啟**升級屬性**對話方塊中，請參閱[開啟升級屬性對話方塊](../core/how-to-open-the-promote-properties-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="d1106-137">You can view and manage properties promoted using the **Quick Promotions** feature by opening the **Promote Properties** dialog box and then clicking the **Property Fields** tab. For step-by-step instructions for opening the **Promote Properties** dialog box, see [Opening the Promote Properties Dialog Box](../core/how-to-open-the-promote-properties-dialog-box.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1106-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1106-138">See Also</span></span>  
 <span data-ttu-id="d1106-139">[升級屬性](../core/promoting-properties.md) </span><span class="sxs-lookup"><span data-stu-id="d1106-139">[Promoting Properties](../core/promoting-properties.md) </span></span>  
 <span data-ttu-id="d1106-140">[如何建立屬性結構描述](../core/how-to-create-property-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="d1106-140">[How to Create Property Schemas](../core/how-to-create-property-schemas.md) </span></span>  
 [<span data-ttu-id="d1106-141">使用訊息內容控制訊息處理方式</span><span class="sxs-lookup"><span data-stu-id="d1106-141">Ways to Use Message Content to Control Message Processing</span></span>](../core/ways-to-use-message-content-to-control-message-processing.md)