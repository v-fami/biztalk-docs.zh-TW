---
title: "如何建構 Web 訊息部分的結構描述型別從 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, Web messages
- Web messages, schema types
- Web messages, creating
- Transform shape [Orchestration Designer]
- Web messages, Transform shape [Orchestration Designer]
ms.assetid: 4452ade6-b10f-4564-bffc-18114896aeeb
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da57e32f2ba4d4d5feb60a6f44cc7d92195852c9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-construct-a-web-message-part-from-a-schema-type"></a><span data-ttu-id="7cbc4-102">如何從結構描述類型建構 Web 訊息部分</span><span class="sxs-lookup"><span data-stu-id="7cbc4-102">How to Construct a Web Message Part from a Schema Type</span></span>
<span data-ttu-id="7cbc4-103">從結構描述類型建立 Web 訊息部分使用**轉換**圖形。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-103">You create a Web message part from a schema type by using a **Transform** shape.</span></span> <span data-ttu-id="7cbc4-104">或者，您也可以使用 .NET Helper 類別來設定部分，以從結構描述類型建立 Web 訊息部分。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-104">Alternatively, you can create a Web message part from a schema type by using a .NET helper class to set the parts.</span></span> <span data-ttu-id="7cbc4-105">如需有關使用.NET 類別建立訊息類型的詳細資訊，請參閱[使用者程式碼中的 建構訊息](../core/constructing-messages-in-user-code.md)。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-105">For more information on creating message types by using a .NET class, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).</span></span>  
  
### <a name="to-construct-a-web-message-part-from-a-schema-type"></a><span data-ttu-id="7cbc4-106">若要從結構描述類型建構 Web 訊息部分</span><span class="sxs-lookup"><span data-stu-id="7cbc4-106">To construct a Web message part from a schema type</span></span>  
  
1.  <span data-ttu-id="7cbc4-107">新增對應。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-107">Add a new map.</span></span> <span data-ttu-id="7cbc4-108">如需建立對應資訊，請參閱[如何建立新的對應](../core/how-to-create-new-maps.md)。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-108">For information about creating maps, see [How to Create New Maps](../core/how-to-create-new-maps.md).</span></span>  
  
2.  <span data-ttu-id="7cbc4-109">在 BizTalk 對應工具中，按一下 **開啟目的結構描述**中**目的結構描述**窗格中的對應，然後在**BizTalk 型別選擇器**對話方塊方塊中，展開  **結構描述** 節點，選取 加入 Web 參考的結構描述，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-109">In BizTalk Mapper, click **Open Destination Schema** in the **Destination Schema** pane of the map and in the **BizTalk Type Picker** dialog box, expand the **Schemas** node, select the schema for the added Web reference, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7cbc4-110">Web 參考結構描述的格式是**\<專案預設命名空間\>。\<Web 參考名稱\>。參考**。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-110">The format of the Web reference schema is **\<project default namespace\>.\<Web reference name\>.Reference**.</span></span>  
  
3.  <span data-ttu-id="7cbc4-111">在**目標結構描述的根節點**對話方塊中，選取 目的結構描述的根節點，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-111">In the **Root Node for Target Schema** dialog box, select a root node for the destination schema, and then click **OK**.</span></span> <span data-ttu-id="7cbc4-112">如需如何判斷 Web 訊息部分類型的根節點的詳細資訊，請參閱[如何判斷 Web 訊息部分類型](../core/how-to-determine-a-web-message-part-type.md)。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-112">For more information about how to determine a root node for a Web message part type, see [How to Determine a Web Message Part Type](../core/how-to-determine-a-web-message-part-type.md).</span></span>  
  
4.  <span data-ttu-id="7cbc4-113">按一下**開啟來源結構描述**中**來源結構描述**窗格中的對應，然後在**BizTalk 型別選擇器**對話方塊方塊中，展開 **結構描述**節點、 選取要對應資料，來源結構描述，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-113">Click **Open Source Schema** in the **Source Schema** pane of the map and in the **BizTalk Type Picker** dialog box, expand the **Schemas** node, select the source schema to map data from, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="7cbc4-114">在 [BizTalk 對應工具] 中，建立來源結構描述和目標結構描述之間的連結。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-114">In the BizTalk Mapper, create links between the source schema and target schema.</span></span>  
  
6.  <span data-ttu-id="7cbc4-115">開啟現有的協調流程 （或建立新的協調流程），開啟**工具箱**，然後按一下**BizTalk 協調流程** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-115">Open an existing orchestration (or create a new orchestration), open the **Toolbox**, and click the **BizTalk Orchestrations** tab.</span></span>  
  
7.  <span data-ttu-id="7cbc4-116">拖曳**建構訊息**圖形至協調流程。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-116">Drag a **Construct Message** shape to the orchestration.</span></span>  
  
8.  <span data-ttu-id="7cbc4-117">編輯**建構訊息**yo 建立 Web 訊息類型的屬性設定為包含訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-117">Edit the **Message Constructed** property to include the message instance that yo created for the Web message type.</span></span>  
  
9. <span data-ttu-id="7cbc4-118">拖曳**轉換**圖形拖曳到**建構訊息**圖形，然後按兩下以開啟**轉換組態** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-118">Drag a **Transform** shape onto the **Construct Message** shape and double-click to open the **Transform Configuration** dialog box.</span></span>  
  
10. <span data-ttu-id="7cbc4-119">按一下**現有對應**按鈕，然後選取您在步驟一中建立的對應**完整格式對應名稱**清單方塊。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-119">Click the **Existing Map** button and select the map that you created in step one in the **Fully Qualified Map Name** list box.</span></span>  
  
11. <span data-ttu-id="7cbc4-120">在**轉換**窗格中，選取**來源**。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-120">In the **Transform** pane, select **Source**.</span></span> <span data-ttu-id="7cbc4-121">在**來源轉換**窗格中，選取有效的訊息執行個體從清單方塊。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-121">In the **Source Transform** pane, select a valid message instance from the list box.</span></span>  
  
12. <span data-ttu-id="7cbc4-122">在**轉換**窗格中，選取**目的地**。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-122">In the **Transform** pane, select **Destination**.</span></span> <span data-ttu-id="7cbc4-123">在**目的轉換**窗格中，選取 Web 訊息執行個體從清單方塊中，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-123">In the **Destination Transform** pane, select the Web message instance from the list box, and then click **OK**.</span></span>  
  
 <span data-ttu-id="7cbc4-124">如需有關使用**轉換組態**對話方塊中，請參閱[如何設定 「 轉換 」 圖形](../core/how-to-configure-the-transform-shape.md)。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-124">For more information about using the **Transform Configuration** dialog box, see [How to Configure the Transform Shape](../core/how-to-configure-the-transform-shape.md).</span></span>  
  
 <span data-ttu-id="7cbc4-125">您也可以使用這個程序，將 Web 方法回應訊息執行個體對應到其他 Web 訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="7cbc4-125">You can also use this procedure to map the Web method response message instance to another Web message instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cbc4-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="7cbc4-126">See Also</span></span>  
 [<span data-ttu-id="7cbc4-127">建構 Web 訊息</span><span class="sxs-lookup"><span data-stu-id="7cbc4-127">Constructing Web Messages</span></span>](../core/constructing-web-messages.md)