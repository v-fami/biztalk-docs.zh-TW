---
title: "如何新增 Catch 例外狀況 Block1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, adding Catch Exception block
- Catch Exception blocks, adding
- exception handling, Catch Exception blocks
ms.assetid: 8e4b264b-b3b0-4d83-81df-a14dc2ddeea2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7922a1527e0f6359427be992c4cc9963f8c7d93e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-catch-exception-block"></a><span data-ttu-id="5ab6a-102">如何新增 Catch 例外狀況區塊</span><span class="sxs-lookup"><span data-stu-id="5ab6a-102">How to Add a Catch Exception Block</span></span>
<span data-ttu-id="5ab6a-103">**Catch 例外狀況**區塊代表例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="5ab6a-103">The **Catch Exception** block represents an exception handler.</span></span> <span data-ttu-id="5ab6a-104">**攔截例外狀況**區塊會附加至結尾**範圍**協調流程設計師中的圖形。</span><span class="sxs-lookup"><span data-stu-id="5ab6a-104">**Catch Exception** blocks are attached to the end of a **Scope** shape in Orchestration Designer.</span></span> <span data-ttu-id="5ab6a-105">您可以附加多個**Catch 例外狀況**視需要會封鎖。</span><span class="sxs-lookup"><span data-stu-id="5ab6a-105">You can attach as many **Catch Exception** blocks as you need.</span></span>  
  
 <span data-ttu-id="5ab6a-106">您可以設定例外狀況處理常式，處理不同類型的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5ab6a-106">You can set up exception handlers to handle different kinds of exceptions.</span></span> <span data-ttu-id="5ab6a-107">對於每個例外狀況處理常式，您必須指定本身為例外狀況或衍生自 `System` 類別之物件的例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="5ab6a-107">On each exception handler, you specify an exception type, which must be either an exception or an object derived from the class `System`.</span></span> <span data-ttu-id="5ab6a-108">如果擲回的例外狀況符合例外狀況處理常式中指定的類型，便會呼叫例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="5ab6a-108">If an exception is thrown that matches the specified type in an exception handler, that exception handler will be called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ab6a-109">若要加入**Catch 例外狀況**封鎖**範圍**圖形，交易類型屬性的**範圍**圖形必須設定為**無**或**長時間執行的**。</span><span class="sxs-lookup"><span data-stu-id="5ab6a-109">To add a **Catch Exception** block to a **Scope** shape, the Transaction Type property of the **Scope** shape must be set to **None** or **Long Running**.</span></span>  
  
### <a name="to-add-and-populate-a-catch-exception-block"></a><span data-ttu-id="5ab6a-110">若要新增和填入 Catch 例外狀況區塊</span><span class="sxs-lookup"><span data-stu-id="5ab6a-110">To add and populate a Catch Exception block</span></span>  
  
1.  <span data-ttu-id="5ab6a-111">以滑鼠右鍵按一下**範圍**您要新增的圖形**Catch 例外狀況**區塊，並再按**新例外狀況處理常式**。</span><span class="sxs-lookup"><span data-stu-id="5ab6a-111">Right-click the **Scope** shape to which you want to add a **Catch Exception** block, and then click **New Exception Handler**.</span></span>  
  
     <span data-ttu-id="5ab6a-112">A **Catch 例外狀況**區塊便會加入至協調流程緊接相關聯**範圍**圖形。</span><span class="sxs-lookup"><span data-stu-id="5ab6a-112">A **Catch Exception** block is added to the orchestration immediately following the associated **Scope** shape.</span></span>  
  
2.  <span data-ttu-id="5ab6a-113">在**屬性**視窗中，指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="5ab6a-113">In the **Properties** window, specify the properties.</span></span>  
  
     <span data-ttu-id="5ab6a-114">最重要的屬性是 [例外狀況物件類型]，因為這是將會攔截的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="5ab6a-114">The most important property is the Exception Object Type; this is the type of message it will catch.</span></span>  
  
    |<span data-ttu-id="5ab6a-115">屬性</span><span class="sxs-lookup"><span data-stu-id="5ab6a-115">Property</span></span>|<span data-ttu-id="5ab6a-116">Description</span><span class="sxs-lookup"><span data-stu-id="5ab6a-116">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="5ab6a-117">例外狀況物件名稱</span><span class="sxs-lookup"><span data-stu-id="5ab6a-117">Exception Object Name</span></span>|<span data-ttu-id="5ab6a-118">指定例外狀況處理常式所攔截的例外狀況物件名稱。</span><span class="sxs-lookup"><span data-stu-id="5ab6a-118">Assigns a name to the exception object caught by the exception handler.</span></span>|  
    |<span data-ttu-id="5ab6a-119">例外狀況物件類型</span><span class="sxs-lookup"><span data-stu-id="5ab6a-119">Exception Object Type</span></span>|<span data-ttu-id="5ab6a-120">決定此例外狀況處理常式將會攔截的物件類型 (衍生自 System.Exception)。</span><span class="sxs-lookup"><span data-stu-id="5ab6a-120">Determines the object type (derived from System.Exception) that this exception handler will catch.</span></span>|  
  
3.  <span data-ttu-id="5ab6a-121">在**屬性**視窗，請在**例外狀況物件類型**清單中，選取**一般例外狀況**。</span><span class="sxs-lookup"><span data-stu-id="5ab6a-121">In the **Properties** window, in the **Exception Object Type** list, select the **General Exception**.</span></span>  
  
4.  <span data-ttu-id="5ab6a-122">內部**Catch 例外狀況**封鎖，新增圖形以建立處理的例外狀況的處理序。</span><span class="sxs-lookup"><span data-stu-id="5ab6a-122">Inside the **Catch Exception** block, add shapes to create the process for handling the exception.</span></span>  
  
5.  <span data-ttu-id="5ab6a-123">以滑鼠右鍵按一下下面的**Catch 例外狀況**封鎖，並指向**插入圖形**，，然後選取 **建構訊息**。</span><span class="sxs-lookup"><span data-stu-id="5ab6a-123">Right-click below the **Catch Exception** block, point to **Insert Shape**, and then select **Construct Message**.</span></span>  
  
6.  <span data-ttu-id="5ab6a-124">[] 內按兩下**MessageAssignment**啟動 「 文字編輯器，並輸入 「 訊息指派。</span><span class="sxs-lookup"><span data-stu-id="5ab6a-124">Double-click inside **MessageAssignment** to activate the Text Editor and enter the Message assignment.</span></span>  
  
     <span data-ttu-id="5ab6a-125">例如，輸入 `Message_3 = Test`。</span><span class="sxs-lookup"><span data-stu-id="5ab6a-125">For example, type `Message_3 = Test`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ab6a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ab6a-126">See Also</span></span>  
 <span data-ttu-id="5ab6a-127">[完成例外狀況訊息](../core/completing-the-exception-message5.md) </span><span class="sxs-lookup"><span data-stu-id="5ab6a-127">[Completing the Exception Message](../core/completing-the-exception-message5.md) </span></span>  
 <span data-ttu-id="5ab6a-128">[如何新增範圍圖形](../core/how-to-add-a-scope-shape2.md) </span><span class="sxs-lookup"><span data-stu-id="5ab6a-128">[How to Add a Scope Shape](../core/how-to-add-a-scope-shape2.md) </span></span>  
 [<span data-ttu-id="5ab6a-129">使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="5ab6a-129">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling3.md)