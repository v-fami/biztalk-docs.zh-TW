---
title: "如何新增 Catch 例外狀況 Block6 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exception handling, Catch Exception block
- Catch Exception blocks
- exceptions, Catch Exception block
ms.assetid: 404312dd-773b-44fe-8b65-7de3d0af2f79
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4be60ddbe45ef4b4f293d7959dc774254e7cd3c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-catch-exception-block"></a><span data-ttu-id="5c467-102">如何新增 Catch 例外狀況區塊</span><span class="sxs-lookup"><span data-stu-id="5c467-102">How to Add a Catch Exception Block</span></span>
<span data-ttu-id="5c467-103">**Catch 例外狀況**區塊代表例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="5c467-103">The **Catch Exception** block represents an exception handler.</span></span> <span data-ttu-id="5c467-104">**攔截例外狀況**區塊會附加至結尾**範圍**協調流程設計師中的圖形。</span><span class="sxs-lookup"><span data-stu-id="5c467-104">**Catch Exception** blocks are attached to the end of a **Scope** shape in Orchestration Designer.</span></span> <span data-ttu-id="5c467-105">在 BizTalk Server 中，您可以附加多個**Catch 例外狀況**視需要會封鎖。</span><span class="sxs-lookup"><span data-stu-id="5c467-105">In BizTalk Server, you can attach as many **Catch Exception** blocks as you need.</span></span>  
  
 <span data-ttu-id="5c467-106">您可以設定例外狀況處理常式，處理不同類型的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5c467-106">You can set up exception handlers to handle different kinds of exceptions.</span></span> <span data-ttu-id="5c467-107">對於每個例外狀況處理常式，您必須指定本身為錯誤訊息或衍生自 `System.Exception` 類別之物件的例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="5c467-107">On each exception handler, you specify an exception type, which must be either a fault message or an object derived from the class `System.Exception`.</span></span> <span data-ttu-id="5c467-108">如果未指定例外狀況類型，例外狀況區塊會被視為一般例外狀況處理常式，而且可以攔截非衍生自 `System.Exception` 的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5c467-108">If you do not specify an exception type, the exception block is treated as a general exception handler, and can catch exceptions that do not derive from `System.Exception`.</span></span>  
  
 <span data-ttu-id="5c467-109">若擲回的例外狀況符合例外狀況處理常式中指定的類型，便會呼叫該例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="5c467-109">If an exception is thrown that matches the specified type in an exception handler, that exception handler is called.</span></span> <span data-ttu-id="5c467-110">其他例外狀況則交由預設的例外狀況處理常式處理。</span><span class="sxs-lookup"><span data-stu-id="5c467-110">If some other exception is thrown, it is handled by the default exception handler.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c467-111">若要加入**Catch 例外狀況**封鎖**範圍**圖形，**交易類型**屬性**範圍**圖形必須設定為 None 或長在執行中。</span><span class="sxs-lookup"><span data-stu-id="5c467-111">To add a **Catch Exception** block to a **Scope** shape, the **Transaction Type** property of the **Scope** shape must be set to None or Long Running.</span></span>  
  
## <a name="adding-and-populating-a-catch-exception-block"></a><span data-ttu-id="5c467-112">新增和填入 Catch 例外狀況區塊</span><span class="sxs-lookup"><span data-stu-id="5c467-112">Adding and Populating a Catch Exception Block</span></span>  
  
#### <a name="to-add-and-populate-a-catch-exception-block"></a><span data-ttu-id="5c467-113">新增和填入 Catch 例外狀況區塊</span><span class="sxs-lookup"><span data-stu-id="5c467-113">To add and populate a catch exception block</span></span>  
  
1.  <span data-ttu-id="5c467-114">以滑鼠右鍵按一下**範圍**您想要新增的圖形**Catch 例外狀況**區塊，然後按一下 **新例外狀況處理常式**。</span><span class="sxs-lookup"><span data-stu-id="5c467-114">Right-click the **Scope** shape that you want to add a **Catch Exception** block to, and then click **New Exception Handler**.</span></span>  
  
     <span data-ttu-id="5c467-115">A **Catch 例外狀況**區塊便會加入至協調流程緊接相關聯**範圍**圖形。</span><span class="sxs-lookup"><span data-stu-id="5c467-115">A **Catch Exception** block is added to the orchestration immediately following the associated **Scope** shape.</span></span>  
  
2.  <span data-ttu-id="5c467-116">在**屬性**視窗中，指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="5c467-116">In the **Properties** window, specify the properties.</span></span> <span data-ttu-id="5c467-117">最重要的屬性是**例外狀況物件類型**因為這是將要 catch 的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="5c467-117">The most important property is the **Exception Object Type** because this is the type of message it will catch.</span></span>  
  
    |<span data-ttu-id="5c467-118">屬性</span><span class="sxs-lookup"><span data-stu-id="5c467-118">Property</span></span>|<span data-ttu-id="5c467-119">Description</span><span class="sxs-lookup"><span data-stu-id="5c467-119">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="5c467-120">例外狀況物件名稱</span><span class="sxs-lookup"><span data-stu-id="5c467-120">Exception Object Name</span></span>|<span data-ttu-id="5c467-121">指定例外狀況處理常式所攔截的例外狀況物件名稱。</span><span class="sxs-lookup"><span data-stu-id="5c467-121">Assigns a name to the exception object caught by the exception handler.</span></span>|  
    |<span data-ttu-id="5c467-122">例外狀況物件類型</span><span class="sxs-lookup"><span data-stu-id="5c467-122">Exception Object Type</span></span>|<span data-ttu-id="5c467-123">決定此例外狀況處理常式將會攔截的物件類型 (衍生自 System.Exception)。</span><span class="sxs-lookup"><span data-stu-id="5c467-123">Determines the object type (derived from System.Exception) that this exception handler will catch.</span></span>|  
  
3.  <span data-ttu-id="5c467-124">在**屬性**視窗中，按一下 **例外狀況物件類型**清單。</span><span class="sxs-lookup"><span data-stu-id="5c467-124">In the **Properties** window, click the **Exception Object Type** list.</span></span> <span data-ttu-id="5c467-125">此清單包含配接器擲回的一般例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5c467-125">This list contains the general exception that is thrown by the adapter.</span></span>  
  
     <span data-ttu-id="5c467-126">名稱會出現為您在後端系統的連接埠中設定的錯誤，例如 PS.SQLExecute.Fault。</span><span class="sxs-lookup"><span data-stu-id="5c467-126">The name appears as the fault you set in the port to the back-end system, for example, PS.SQLExecute.Fault.</span></span>  
  
4.  <span data-ttu-id="5c467-127">加入名稱**例外狀況物件名稱**，例如 Test。</span><span class="sxs-lookup"><span data-stu-id="5c467-127">Add a name for the **Exception Object Name**, for example, Test.</span></span>  
  
     <span data-ttu-id="5c467-128">內部**Catch 例外狀況**封鎖，新增圖形以建立處理的例外狀況的處理序。</span><span class="sxs-lookup"><span data-stu-id="5c467-128">Inside the **Catch Exception** block, add shapes to create the process for handling the exception.</span></span>  
  
    1.  <span data-ttu-id="5c467-129">以滑鼠右鍵按一下下面的**Catch 例外狀況**，指向**插入圖形**，然後選取**建構訊息**。</span><span class="sxs-lookup"><span data-stu-id="5c467-129">Right-click below the **Catch Exception**, point to **Insert Shape**, and select **Construct Message**.</span></span>  
  
         ![](../core/media/siebeladapter-20-exceptionhandling-constructmessage.gif "SiebelAdapter_20_ExceptionHandling_ConstructMessage")  
  
    2.  <span data-ttu-id="5c467-130">[] 內按兩下**MessageAssignment**開啟文字編輯器，然後輸入 「 訊息指派。</span><span class="sxs-lookup"><span data-stu-id="5c467-130">Double-click inside **MessageAssignment** to open the Text Editor and enter the Message assignment.</span></span>  
  
         <span data-ttu-id="5c467-131">輸入您在設定的名稱**例外狀況物件名稱**從**Catch 例外狀況**，以及您建立之錯誤的新訊息。</span><span class="sxs-lookup"><span data-stu-id="5c467-131">Enter the name that you set in the **Exception Object Name** from the **Catch Exception**, and the new message you created for the fault.</span></span>  
  
         <span data-ttu-id="5c467-132">例如，輸入 `Message_3 = Test`。</span><span class="sxs-lookup"><span data-stu-id="5c467-132">For example, type `Message_3 = Test`.</span></span>  
  
         ![](../core/media/siebeladapter-21-exceptionhandling-message3test.gif "SiebelAdapter_21_ExceptionHandling_Message3Test")  
  
## <a name="see-also"></a><span data-ttu-id="5c467-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c467-133">See Also</span></span>  
 <span data-ttu-id="5c467-134">[如何新增範圍圖形](../core/how-to-add-a-scope-shape1.md) </span><span class="sxs-lookup"><span data-stu-id="5c467-134">[How to Add a Scope Shape](../core/how-to-add-a-scope-shape1.md) </span></span>  
 <span data-ttu-id="5c467-135">[完成例外狀況訊息](../core/completing-the-exception-message3.md) </span><span class="sxs-lookup"><span data-stu-id="5c467-135">[Completing the Exception Message](../core/completing-the-exception-message3.md) </span></span>  
 [<span data-ttu-id="5c467-136">使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="5c467-136">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling2.md)