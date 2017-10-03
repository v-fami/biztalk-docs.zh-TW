---
title: "如何新增 Catch 例外狀況 Block3 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scope shape [Orchestration Designer], Catch Exception block [Orchestration Designer]
- Catch Exception block [Orchestration Designer]
- Catch Exception block [Orchestration Designer], creating
- Catch Exception block [Orchestration Designer], exception handler
- Catch Exception block [Orchestration Designer], about Catch Exception blocks
- Orchestration Designer, errors
ms.assetid: 63ca4a60-b657-452a-86fd-78968ccf2933
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1040a27a5e1273d2ad80a722deb421878de36c12
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-catch-exception-block"></a><span data-ttu-id="835ba-102">如何新增 Catch 例外狀況區塊</span><span class="sxs-lookup"><span data-stu-id="835ba-102">How to Add a Catch Exception Block</span></span>
<span data-ttu-id="835ba-103">**Catch 例外狀況**區塊代表例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="835ba-103">The **Catch Exception** block represents an exception handler.</span></span> <span data-ttu-id="835ba-104">**攔截例外狀況**區塊會附加至結尾**範圍**協調流程設計師中的圖形。</span><span class="sxs-lookup"><span data-stu-id="835ba-104">**Catch Exception** blocks are attached to the end of a **Scope** shape in Orchestration Designer.</span></span> <span data-ttu-id="835ba-105">您可以附加多個**Catch 例外狀況**視需要會封鎖。</span><span class="sxs-lookup"><span data-stu-id="835ba-105">You can attach as many **Catch Exception** blocks as you need.</span></span>  
  
 <span data-ttu-id="835ba-106">您可以設定例外狀況處理常式，處理不同類型的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="835ba-106">You can set up exception handlers to handle different kinds of exceptions.</span></span> <span data-ttu-id="835ba-107">對於每個例外狀況處理常式中，您可以指定例外狀況類型的錯誤訊息或衍生自類別的物件必須是**System.Exception**。</span><span class="sxs-lookup"><span data-stu-id="835ba-107">On each exception handler, you specify an exception type, which must be either a fault message or an object derived from the class **System.Exception**.</span></span> <span data-ttu-id="835ba-108">如果您未指定的例外狀況類型，例外狀況區塊會被視為一般例外狀況處理常式中，而且可以攔截例外狀況不是衍生自**System.Exception**。</span><span class="sxs-lookup"><span data-stu-id="835ba-108">If you do not specify an exception type, the exception block will be treated as a general exception handler, and can catch exceptions that do not derive from **System.Exception**.</span></span>  
  
 <span data-ttu-id="835ba-109">如果擲回的例外狀況符合例外狀況處理常式中指定的類型，便會呼叫例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="835ba-109">If an exception is thrown that matches the specified type in an exception handler, that exception handler will be called.</span></span> <span data-ttu-id="835ba-110">其他例外狀況則交由預設的例外狀況處理常式處理。</span><span class="sxs-lookup"><span data-stu-id="835ba-110">If some other exception is thrown, it will be handled by the default exception handler.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="835ba-111">若要加入**Catch 例外狀況**封鎖**範圍**圖形，**交易類型**屬性**範圍**圖形必須設定為**無**或**長時間執行的**。</span><span class="sxs-lookup"><span data-stu-id="835ba-111">To add a **Catch Exception** block to a **Scope** shape, the **Transaction Type** property of the **Scope** shape must be set to **None** or **Long Running**.</span></span>  
  
### <a name="to-add-a-catch-exception-block"></a><span data-ttu-id="835ba-112">若要新增 Catch 例外狀況區塊</span><span class="sxs-lookup"><span data-stu-id="835ba-112">To add a Catch Exception block</span></span>  
  
1.  <span data-ttu-id="835ba-113">以滑鼠右鍵按一下**範圍**您要新增的圖形**Catch 例外狀況**區塊，並再按**新例外狀況處理常式**。</span><span class="sxs-lookup"><span data-stu-id="835ba-113">Right-click the **Scope** shape to which you want to add a **Catch Exception** block, and then click **New Exception Handler**.</span></span>  
  
     <span data-ttu-id="835ba-114">A **Catch 例外狀況**區塊便會加入至協調流程緊接相關聯**範圍**圖形。</span><span class="sxs-lookup"><span data-stu-id="835ba-114">A **Catch Exception** block is added to the orchestration immediately following the associated **Scope** shape.</span></span>  
  
2.  <span data-ttu-id="835ba-115">在 [屬性] 視窗中，指定以下屬性：</span><span class="sxs-lookup"><span data-stu-id="835ba-115">In the Properties window, specify the following properties:</span></span>  
  
    |<span data-ttu-id="835ba-116">屬性</span><span class="sxs-lookup"><span data-stu-id="835ba-116">Property</span></span>|<span data-ttu-id="835ba-117">Description</span><span class="sxs-lookup"><span data-stu-id="835ba-117">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="835ba-118">例外狀況物件名稱</span><span class="sxs-lookup"><span data-stu-id="835ba-118">Exception Object Name</span></span>|<span data-ttu-id="835ba-119">指定例外狀況處理常式所攔截的例外狀況物件名稱。</span><span class="sxs-lookup"><span data-stu-id="835ba-119">Assigns a name to the exception object caught by the exception handler.</span></span>|  
    |<span data-ttu-id="835ba-120">例外狀況物件類型</span><span class="sxs-lookup"><span data-stu-id="835ba-120">Exception Object Type</span></span>|<span data-ttu-id="835ba-121">決定此例外狀況處理常式將會攔截的物件類型 (衍生自 System.Exception)。</span><span class="sxs-lookup"><span data-stu-id="835ba-121">Determines the object type (derived from System.Exception) that this exception handler will catch.</span></span>|  
  
3.  <span data-ttu-id="835ba-122">內部**Catch 例外狀況**封鎖，新增圖形以建立處理的例外狀況的處理序。</span><span class="sxs-lookup"><span data-stu-id="835ba-122">Inside the **Catch Exception** block, add shapes to create the process for handling the exception.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="835ba-123">如果您指定做為一般例外狀況**例外狀況**物件類型， **Catch 例外狀況**區塊就會攔截任何例外狀況，包括非衍生自**System.Exception**.</span><span class="sxs-lookup"><span data-stu-id="835ba-123">If you specify General Exception as the **Exception** object type, the **Catch Exception** block will intercept any exception, including those that are not derived from **System.Exception**.</span></span> <span data-ttu-id="835ba-124">在此狀況下，您無法存取例外狀況物件。</span><span class="sxs-lookup"><span data-stu-id="835ba-124">In such a case, you will not have access to an exception object.</span></span> <span data-ttu-id="835ba-125">這在區塊內，如果您使用**擲回的例外狀況**圖形與一般例外狀況類型，您將能有效地重新擲回攔截的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="835ba-125">Within this block, if you use a **Throw Exception** shape with the General Exception type, you will be effectively rethrowing the caught exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="835ba-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="835ba-126">See Also</span></span>  
 [<span data-ttu-id="835ba-127">例外狀況</span><span class="sxs-lookup"><span data-stu-id="835ba-127">Exceptions</span></span>](../core/exceptions.md)