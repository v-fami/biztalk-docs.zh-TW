---
title: 如何新增 Catch 例外狀況 Block2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Catch Exception blocks
- exceptions, Catch Exception blocks
ms.assetid: 7c8b6024-e8dc-4417-83f9-bf4032644b91
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e48ce1e6f0646acdf63ed33582f382f1baed797
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246838"
---
# <a name="how-to-add-a-catch-exception-block"></a><span data-ttu-id="1df77-102">如何新增 Catch 例外狀況區塊</span><span class="sxs-lookup"><span data-stu-id="1df77-102">How to Add a Catch Exception Block</span></span>
<span data-ttu-id="1df77-103">**Catch 例外狀況**區塊代表例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="1df77-103">The **Catch Exception** block represents an exception handler.</span></span> <span data-ttu-id="1df77-104">**攔截例外狀況**區塊會附加至結尾**範圍**協調流程設計師中的圖形。</span><span class="sxs-lookup"><span data-stu-id="1df77-104">**Catch Exception** blocks are attached to the end of a **Scope** shape in Orchestration Designer.</span></span> <span data-ttu-id="1df77-105">您可以附加多個**Catch 例外狀況**視需要會封鎖。</span><span class="sxs-lookup"><span data-stu-id="1df77-105">You can attach as many **Catch Exception** blocks as you need.</span></span>  
  
 <span data-ttu-id="1df77-106">您可以設定例外狀況處理常式，處理不同類型的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1df77-106">You can set up exception handlers to handle different kinds of exceptions.</span></span> <span data-ttu-id="1df77-107">對於每個例外狀況處理常式，您必須指定例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="1df77-107">On each exception handler, you specify an exception type.</span></span> <span data-ttu-id="1df77-108">這必須是例外狀況或衍生自類別 `System` 的物件。</span><span class="sxs-lookup"><span data-stu-id="1df77-108">This must be either an exception or an object derived from the class `System`.</span></span> <span data-ttu-id="1df77-109">如果擲回的例外狀況符合例外狀況處理常式中指定的類型，便會呼叫例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="1df77-109">If an exception is thrown that matches the specified type in an exception handler, that exception handler will be called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1df77-110">若要加入 Catch 例外狀況區塊至 「 範圍 」 圖形，「 範圍 」 圖形的交易類型屬性必須設定為**無**或**長時間執行**。</span><span class="sxs-lookup"><span data-stu-id="1df77-110">To add a Catch Exception block to a Scope shape, the Transaction Type property of the Scope shape must be set to **None** or **Long Running**.</span></span>  
  
### <a name="to-add-and-populate-a-catch-exception-block"></a><span data-ttu-id="1df77-111">若要新增和填入 Catch 例外狀況區塊</span><span class="sxs-lookup"><span data-stu-id="1df77-111">To add and populate a Catch Exception block</span></span>  
  
1.  <span data-ttu-id="1df77-112">以滑鼠右鍵按一下**範圍**您要新增的圖形**Catch 例外狀況**區塊，並再按**新例外狀況處理常式**。</span><span class="sxs-lookup"><span data-stu-id="1df77-112">Right-click the **Scope** shape to which you want to add a **Catch Exception** block, and then click **New Exception Handler**.</span></span>  
  
     <span data-ttu-id="1df77-113">A **Catch 例外狀況**區塊便會加入至協調流程緊接相關聯**範圍**圖形。</span><span class="sxs-lookup"><span data-stu-id="1df77-113">A **Catch Exception** block is added to the orchestration immediately following the associated **Scope** shape.</span></span>  
  
2.  <span data-ttu-id="1df77-114">在**屬性**視窗中，指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="1df77-114">In the **Properties** window, specify the properties.</span></span>  
  
     <span data-ttu-id="1df77-115">最重要的屬性是**例外狀況物件類型**; 這是將要 catch 的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="1df77-115">The most important property is the **Exception Object Type**; this is the type of message it will catch.</span></span>  
  
3.  <span data-ttu-id="1df77-116">在**屬性**windows，請在**例外狀況物件類型**清單中，選取**一般例外狀況**。</span><span class="sxs-lookup"><span data-stu-id="1df77-116">In the **Properties** windows, in the **Exception Object Type** list, select  **General Exception**.</span></span>  
  
    |<span data-ttu-id="1df77-117">屬性</span><span class="sxs-lookup"><span data-stu-id="1df77-117">Property</span></span>|<span data-ttu-id="1df77-118">Description</span><span class="sxs-lookup"><span data-stu-id="1df77-118">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="1df77-119">**例外狀況物件名稱**</span><span class="sxs-lookup"><span data-stu-id="1df77-119">**Exception Object Name**</span></span>|<span data-ttu-id="1df77-120">指定例外狀況處理常式所攔截的例外狀況物件名稱。</span><span class="sxs-lookup"><span data-stu-id="1df77-120">Assigns a name to the exception object caught by the exception handler.</span></span>|  
    |<span data-ttu-id="1df77-121">**例外狀況物件類型**</span><span class="sxs-lookup"><span data-stu-id="1df77-121">**Exception Object Type**</span></span>|<span data-ttu-id="1df77-122">決定此例外狀況處理常式將會攔截的物件類型 (衍生自 System.Exception)。</span><span class="sxs-lookup"><span data-stu-id="1df77-122">Determines the object type (derived from System.Exception) that this exception handler will catch.</span></span>|  
  
4.  <span data-ttu-id="1df77-123">在 [Catch 例外狀況] 區塊內新增圖形，建立例外狀況的處理程序。</span><span class="sxs-lookup"><span data-stu-id="1df77-123">Inside the Catch Exception block, add shapes to create the process for handling the exception.</span></span>  
  
    1.  <span data-ttu-id="1df77-124">以滑鼠右鍵按一下下面的**CatchException** ，指向 **插入圖形**，然後選取**建構訊息**。</span><span class="sxs-lookup"><span data-stu-id="1df77-124">Right-click below the **CatchException** and point to **Insert Shape**, and then select **Construct Message**.</span></span>  
  
    2.  <span data-ttu-id="1df77-125">[] 內按兩下**MessageAssignment**開啟文字編輯器，然後輸入 「 訊息指派。</span><span class="sxs-lookup"><span data-stu-id="1df77-125">Double-click inside **MessageAssignment** to open the Text Editor and enter the Message assignment.</span></span>  
  
         <span data-ttu-id="1df77-126">例如，輸入 `Message_3 = Test`。</span><span class="sxs-lookup"><span data-stu-id="1df77-126">For example, type `Message_3 = Test`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1df77-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1df77-127">See Also</span></span>  
 <span data-ttu-id="1df77-128">[完成例外狀況訊息](../core/completing-the-exception-message4.md) </span><span class="sxs-lookup"><span data-stu-id="1df77-128">[Completing the Exception Message](../core/completing-the-exception-message4.md) </span></span>  
 <span data-ttu-id="1df77-129">[如何新增範圍圖形](../core/how-to-add-a-scope-shape4.md) </span><span class="sxs-lookup"><span data-stu-id="1df77-129">[How to Add a Scope Shape](../core/how-to-add-a-scope-shape4.md) </span></span>  
 [<span data-ttu-id="1df77-130">使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="1df77-130">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling4.md)