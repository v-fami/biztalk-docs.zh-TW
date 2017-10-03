---
title: "例外狀況的原因 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, errors
- errors, orchestrations
- errors, causes
ms.assetid: b0422382-d034-4c58-87c6-fc269dbbfe43
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9006234d71751078269e5a88559839fdadd91e91
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="causes-of-exceptions"></a><span data-ttu-id="4c818-102">造成例外狀況的原因</span><span class="sxs-lookup"><span data-stu-id="4c818-102">Causes of Exceptions</span></span>
<span data-ttu-id="4c818-103">可透過下列方式在協調流程中產生例外狀況：</span><span class="sxs-lookup"><span data-stu-id="4c818-103">Exceptions can be generated within an orchestration in the following ways:</span></span>  
  
-   <span data-ttu-id="4c818-104">由**擲回的例外狀況**圖形，立即且無條件地擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4c818-104">By a **Throw Exception** shape, which throws an exception immediately and unconditionally.</span></span> <span data-ttu-id="4c818-105">控制權會傳遞從**擲回的例外狀況**圖形直接以適當的例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="4c818-105">Control passes from the **Throw Exception** shape directly to the appropriate exception handler.</span></span>  
  
-   <span data-ttu-id="4c818-106">透過在長時間執行之交易中過期的逾時。</span><span class="sxs-lookup"><span data-stu-id="4c818-106">By a time-out expiring in a long-running transaction.</span></span> <span data-ttu-id="4c818-107">預先定義的系統例外狀況：**Microsoft.XLANG.BaseTypes.TimeOutException**— 在此情況下會擲回。</span><span class="sxs-lookup"><span data-stu-id="4c818-107">A predefined system exception—**Microsoft.XLANG.BaseTypes.TimeOutException**—is thrown in this case.</span></span>  
  
-   <span data-ttu-id="4c818-108">透過某個其他的交易失敗。</span><span class="sxs-lookup"><span data-stu-id="4c818-108">By some other transaction failure.</span></span> <span data-ttu-id="4c818-109">執行階段引擎會針對這些失敗擲回系統定義的訊息，例如 Microsoft.XLANG.BaseTypes.PersistenceException。</span><span class="sxs-lookup"><span data-stu-id="4c818-109">The runtime engine throws a system-defined message such as Microsoft.XLANG.BaseTypes.PersistenceException for these failures.</span></span>  
  
-   <span data-ttu-id="4c818-110">透過使用者程式碼例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4c818-110">By a user code exception.</span></span> <span data-ttu-id="4c818-111">在協調流程內進行外部使用者程式碼的呼叫時，所呼叫的 Common Language Runtime 類別可擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4c818-111">When calls to external user code are made within an orchestration, common language runtime classes that are called can throw exceptions.</span></span> <span data-ttu-id="4c818-112">如果使用者程式碼中未處理這些例外狀況，這些例外狀況最後會往上傳播到呼叫使用者程式碼的範圍。</span><span class="sxs-lookup"><span data-stu-id="4c818-112">If these exceptions are not handled in the user code, they eventually propagate up into the scope in which the call to the user code is made.</span></span>  
  
-   <span data-ttu-id="4c818-113">透過某個其他系統例外狀況 (例如，持續性失敗、類似型別載入器例外狀況的另一個 .NET 或系統例外狀況，或是資料轉換錯誤)。</span><span class="sxs-lookup"><span data-stu-id="4c818-113">By some other system exception (for example, a persistence failure, another .NET or system exception such as type loader exception, or a data conversion error).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c818-114">擲回型別載入器例外狀況時，可能不在攔截例外狀況**Catch 例外狀況**封鎖在相同**範圍**圖形。</span><span class="sxs-lookup"><span data-stu-id="4c818-114">When a type loader exception is thrown, the exception may not be caught in the **Catch Exception** block in the same **Scope** shape.</span></span> <span data-ttu-id="4c818-115">這是因為此例外狀況是來自於型別載入器，而不是來自於 BizTalk 協調流程處理。</span><span class="sxs-lookup"><span data-stu-id="4c818-115">This is because of that the exception is from the type loader, not from the BizTalk orchestration process.</span></span> <span data-ttu-id="4c818-116">因此，它不會遵循 BizTalk 控制流程規則。</span><span class="sxs-lookup"><span data-stu-id="4c818-116">Therefore, it does not follow the BizTalk rules of control flow.</span></span>  
  
-   <span data-ttu-id="4c818-117">根據周圍範圍終止執行中的同層級分支。</span><span class="sxs-lookup"><span data-stu-id="4c818-117">By a sibling branch in a surrounding scope halting execution.</span></span> <span data-ttu-id="4c818-118">在此情況下，會將 Microsoft.XLANG.BaseTypes.ForcedTerminationException 擲回給每一個分支，而且您可能會想要對每一個分支加入例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="4c818-118">Microsoft.XLANG.BaseTypes.ForcedTerminationException is thrown to each branch in this case, and you might want to add an exception handler to each.</span></span> <span data-ttu-id="4c818-119">這類例外狀況處理常式無法重新擲回其例外狀況，也不應該嘗試擲回任何其他類型的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4c818-119">Such an exception handler cannot re-throw its exception, nor should it attempt to throw any other type of exception.</span></span>  
  
-   <span data-ttu-id="4c818-120">透過接收指示錯誤的外部訊息。</span><span class="sxs-lookup"><span data-stu-id="4c818-120">By receipt of an external message that indicates a fault.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c818-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c818-121">See Also</span></span>  
 <span data-ttu-id="4c818-122">[錯誤訊息](../core/fault-messages.md) </span><span class="sxs-lookup"><span data-stu-id="4c818-122">[Fault Messages](../core/fault-messages.md) </span></span>  
 [<span data-ttu-id="4c818-123">例外狀況</span><span class="sxs-lookup"><span data-stu-id="4c818-123">Exceptions</span></span>](../core/exceptions.md)