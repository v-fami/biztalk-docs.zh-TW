---
title: 教學課程： 使用 TIBCO EMS 訊息內容屬性 |Microsoft 文件
description: 若要針對 BizTalk Server 使用 TIBCO Enterprise Message Service 訊息描述元欄位，在協調流程中的逐步指南
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e52593b-5001-4740-89fb-e003e12d8e69
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fafde77ad1e6edcae71d2c33a722ac63ab8e75b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973996"
---
# <a name="tutorial-use-tibco-ems-message-descriptors"></a><span data-ttu-id="a0c54-103">教學課程： 使用 TIBCO EMS 訊息描述元</span><span class="sxs-lookup"><span data-stu-id="a0c54-103">Tutorial: Use TIBCO EMS message descriptors</span></span>

## <a name="overview"></a><span data-ttu-id="a0c54-104">概觀</span><span class="sxs-lookup"><span data-stu-id="a0c54-104">Overview</span></span>
<span data-ttu-id="a0c54-105">本教學課程將示範如何使用 BizTalk Server 內容屬性，以設定協調流程中的 TIBCO Enterprise Message Service (EMS) 訊息描述元欄位。</span><span class="sxs-lookup"><span data-stu-id="a0c54-105">This tutorial demonstrates how to use BizTalk Server context properties to set TIBCO Enterprise Message Service (EMS) message descriptor fields in your orchestration.</span></span> <span data-ttu-id="a0c54-106">本教學課程是假設您的協調流程可以接收來自接收埠的訊息，而且可將訊息送至已繫結到 Microsoft BizTalk Adapter for TIBCO Enterprise Message Service 的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="a0c54-106">The tutorial assumes that you have an orchestration that receives a message from a receive port and sends the message to a send port bound to Microsoft BizTalk Adapter for TIBCO Enterprise Message Service.</span></span>  
  
 <span data-ttu-id="a0c54-107">下列程序將示範如何透過變更 TibcoEMS.Priority 內容屬性的值，變更 TIBCO EMS 訊息的優先順序。</span><span class="sxs-lookup"><span data-stu-id="a0c54-107">The following procedure demonstrates how to change the priority of the TIBCO EMS message by changing the value of the TibcoEMS.Priority context property.</span></span> <span data-ttu-id="a0c54-108">在 BizTalk Server 中，訊息都是永遠不變的。</span><span class="sxs-lookup"><span data-stu-id="a0c54-108">In BizTalk Server, messages are immutable.</span></span> <span data-ttu-id="a0c54-109">因此，若要變更屬性值，您必須建立新訊息並加以修改。</span><span class="sxs-lookup"><span data-stu-id="a0c54-109">Therefore, to change a property value, you must create and modify a new message.</span></span> <span data-ttu-id="a0c54-110">在接收和傳送圖形之間插入訊息指派圖形，就可以建立新訊息和加以修改。</span><span class="sxs-lookup"><span data-stu-id="a0c54-110">You create and modify the new message by inserting a message assignment shape between the Receive and Send shapes.</span></span> <span data-ttu-id="a0c54-111">但首先您必須先參考結構描述 DLL，才能取得 TIBCO EMS 屬性的存取權。</span><span class="sxs-lookup"><span data-stu-id="a0c54-111">First, however, you must reference the schema DLL to gain access to the TIBCO EMS properties.</span></span>  
  
## <a name="reference-the-schema-dll"></a><span data-ttu-id="a0c54-112">參考結構描述 DLL</span><span class="sxs-lookup"><span data-stu-id="a0c54-112">Reference the schema DLL</span></span>  
  
1.  <span data-ttu-id="a0c54-113">在 Visual Studio 中，開啟您的 BizTalk Server 專案，並開啟**方案總管 中**。</span><span class="sxs-lookup"><span data-stu-id="a0c54-113">In Visual Studio, open your BizTalk Server project, and open **Solution Explorer** .</span></span>  
  
2.  <span data-ttu-id="a0c54-114">以滑鼠右鍵按一下**參考**，然後選取**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="a0c54-114">Right-click **References**, and select **Add Reference**.</span></span>  
  
     <span data-ttu-id="a0c54-115">[新增參考] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="a0c54-115">The **Add Reference** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="a0c54-116">按一下**瀏覽** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a0c54-116">Click the **Browse** tab.</span></span>  
  
     <span data-ttu-id="a0c54-117">**選取元件** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="a0c54-117">The **Select Component** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="a0c54-118">找出 **\<TIBCO EMS_Adapter_installation_directory\>\bin**，然後選取**Microsoft.Adapters.TibcoEMSProperties.dll**。</span><span class="sxs-lookup"><span data-stu-id="a0c54-118">Locate **\<TIBCO EMS_Adapter_installation_directory\>\bin**, and then select **Microsoft.Adapters.TibcoEMSProperties.dll**.</span></span>  
  
5.  <span data-ttu-id="a0c54-119">按一下 **[開啟]**。</span><span class="sxs-lookup"><span data-stu-id="a0c54-119">Click **Open**.</span></span>  
  
     <span data-ttu-id="a0c54-120">DLL 會出現在**選取的元件**中**加入參考** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a0c54-120">The DLL appears in the **Selected Components** in the **Add Reference** dialog box.</span></span>  
  
6.  <span data-ttu-id="a0c54-121">按一下**確定**，然後按兩下您的協調流程存取協調流程設計工具。</span><span class="sxs-lookup"><span data-stu-id="a0c54-121">Click **OK** and then double-click your orchestration to access the Orchestration Designer.</span></span>  
  
7.  <span data-ttu-id="a0c54-122">在**檢視**功能表上，指向**其他視窗**，然後按一下 **協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="a0c54-122">On the **View** menu, point to **Other Windows**, and then click **Orchestration View**.</span></span>  
  
8.  <span data-ttu-id="a0c54-123">在協調流程檢視中，以滑鼠右鍵按一下**訊息**選取**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="a0c54-123">In the Orchestration view, right-click **Messages** and select **New Message**.</span></span>  
  
9. <span data-ttu-id="a0c54-124">編輯新訊息的屬性，並指派**訊息類型**。</span><span class="sxs-lookup"><span data-stu-id="a0c54-124">Edit your new message properties and assign a **Message Type**.</span></span>  
  
     <span data-ttu-id="a0c54-125">您要指派 Message_1 到 Message_2。</span><span class="sxs-lookup"><span data-stu-id="a0c54-125">You will assign Message_1 to Message_2.</span></span> <span data-ttu-id="a0c54-126">因此，這兩個訊息都必須指派相同的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="a0c54-126">Therefore, you must assign the same message type to both messages.</span></span>  
  
10. <span data-ttu-id="a0c54-127">在 [檢視] 功能表上，按一下 [工具箱]。</span><span class="sxs-lookup"><span data-stu-id="a0c54-127">On the **View** menu, click **Toolbox**.</span></span>  
  
11. <span data-ttu-id="a0c54-128">拖曳**訊息指派**圖形拖曳到您要建立新的訊息的協調流程。</span><span class="sxs-lookup"><span data-stu-id="a0c54-128">Drag a **Message Assignment** shape onto your orchestration where you want to create a new message.</span></span>  
  
12. <span data-ttu-id="a0c54-129">編輯外圈的 ConstructMessage_1 圖形中，並選取您新的訊息，Message_2，**建構的訊息**屬性。</span><span class="sxs-lookup"><span data-stu-id="a0c54-129">Edit the outer ConstructMessage_1 shape and select your new message, Message_2, in the **Constructed Messages** property.</span></span>  
  
13. <span data-ttu-id="a0c54-130">按兩下內圈的 MessageAssignment_1 圖形。</span><span class="sxs-lookup"><span data-stu-id="a0c54-130">Double-click the inner MessageAssignment_1 shape.</span></span>  
  
     <span data-ttu-id="a0c54-131">[BizTalk 運算式編輯器] 便會出現。</span><span class="sxs-lookup"><span data-stu-id="a0c54-131">The BizTalk Expression Editor appears.</span></span>  
  
14. <span data-ttu-id="a0c54-132">在 [BizTalk 運算式編輯器] 中，輸入您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a0c54-132">In the BizTalk Expression Editor, type your code.</span></span>  
  
15. <span data-ttu-id="a0c54-133">一開始先貼上現有的訊息，然後為訊息內容屬性指定值。</span><span class="sxs-lookup"><span data-stu-id="a0c54-133">First copy an existing message and then assign values to message context properties.</span></span>  
  
     <span data-ttu-id="a0c54-134">語法是 `Message(property) = value;`。</span><span class="sxs-lookup"><span data-stu-id="a0c54-134">The syntax is `Message(property) = value;`.</span></span> <span data-ttu-id="a0c54-135">例如：</span><span class="sxs-lookup"><span data-stu-id="a0c54-135">For example:</span></span>  
  
    ```  
    Message_2 = Message_1;  
    Message_2( TibcoEMS.Priority) = 6;  
    ```  
  
     <span data-ttu-id="a0c54-136">如需取得可用於自訂訊息之支援屬性的清單，請參閱 TIBCO EMS。</span><span class="sxs-lookup"><span data-stu-id="a0c54-136">See TIBCO EMS for a list of supported properties that you can use in your custom message.</span></span>  
  
16. <span data-ttu-id="a0c54-137">按一下**確定**以關閉 BizTalk 運算式編輯器並儲存您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a0c54-137">Click **OK** to close the BizTalk Expression Editor and save your code.</span></span>  
  
17. <span data-ttu-id="a0c54-138">按一下 [傳送] 圖形，並指派**訊息**是**Message_2**。</span><span class="sxs-lookup"><span data-stu-id="a0c54-138">Click the Send shape and assign the **Message** to be **Message_2**.</span></span>  
  
18. <span data-ttu-id="a0c54-139">確認訊息流程中的其餘圖形有在適當訊息上進行操作。</span><span class="sxs-lookup"><span data-stu-id="a0c54-139">Verify that the shapes in the rest of the message flow operate on the appropriate message.</span></span>  
  
19. <span data-ttu-id="a0c54-140">以滑鼠右鍵按一下方案總管 中的專案，然後選取**建置**。</span><span class="sxs-lookup"><span data-stu-id="a0c54-140">Right-click your project in Solution Explorer, and select **Build**.</span></span>  
  
20. <span data-ttu-id="a0c54-141">以滑鼠右鍵按一下您的專案，然後選取**部署**。</span><span class="sxs-lookup"><span data-stu-id="a0c54-141">Right-click your project and select **Deploy**.</span></span>  
  
21. <span data-ttu-id="a0c54-142">選取**繫結**，**登錄**，和**啟動**測試您的協調流程 [BizTalk 總管] 中。</span><span class="sxs-lookup"><span data-stu-id="a0c54-142">Select **Bind**, **Enlist**, and **Start** in the BizTalk Explorer to test your orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c54-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="a0c54-143">See Also</span></span>  
[<span data-ttu-id="a0c54-144">TIBCO EMS 訊息內容屬性</span><span class="sxs-lookup"><span data-stu-id="a0c54-144">TIBCO EMS message context properties</span></span>](../core/message-context-properties-in-biztalk-server.md)