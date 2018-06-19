---
title: 例外狀況處理的方式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors, handlers
- scopes, errors
- errors, scopes
- handlers [adapters], errors
ms.assetid: 30b88d8a-8737-4700-b856-1b49fdf6b6d0
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 004e4f29bcfc292edb33bae816a52b588a89771c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246662"
---
# <a name="how-exceptions-are-handled"></a><span data-ttu-id="b06f3-102">如何處理例外狀況</span><span class="sxs-lookup"><span data-stu-id="b06f3-102">How Exceptions Are Handled</span></span>
<span data-ttu-id="b06f3-103">當例外狀況在某個範圍內發生時，在該範圍中執行的每個邏輯執行緒都會停止。</span><span class="sxs-lookup"><span data-stu-id="b06f3-103">When an exception occurs within a scope, each logical thread of execution in the scope is stopped.</span></span> <span data-ttu-id="b06f3-104">執行階段引擎便會嘗試尋找適當例外狀況的例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="b06f3-104">The runtime engine tries to find an exception handler for the appropriate exception.</span></span>  
  
 <span data-ttu-id="b06f3-105">如果找到的例外狀況處理常式符合特定型別或是其基底型別之一，便會將控制傳遞到該處理常式並執行其程式碼。</span><span class="sxs-lookup"><span data-stu-id="b06f3-105">If the exception handler is found that matches the specific type or one of its base types, control passes to that handler and its code runs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b06f3-106">例外狀況類型必須衍生自**System.Exception**。</span><span class="sxs-lookup"><span data-stu-id="b06f3-106">The exception type must be derived from **System.Exception**.</span></span>  
  
 <span data-ttu-id="b06f3-107">例外狀況處理常式是循序的，也就是說，這些處理常式會依順序接受檢查，以決定它們是否能夠處理特定的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b06f3-107">Exception handlers are sequential; that is, they will be checked in order to see if they can handle a particular exception.</span></span> <span data-ttu-id="b06f3-108">為正常運作，例外狀況處理常式必須在放置時，讓這些處理更為特定類型的例外狀況處理常式先出現，後面則跟著處理較為一般類型的處理常式。</span><span class="sxs-lookup"><span data-stu-id="b06f3-108">To work properly, exception handlers must be placed so that those handling more specific types come first, followed by those handling more general types.</span></span> <span data-ttu-id="b06f3-109">如此您才能確定特定類型的例外狀況會由適當的處理常式所處理，而非設計用來處理基底型別的處理常式。</span><span class="sxs-lookup"><span data-stu-id="b06f3-109">This is so that you can ensure that an exception of a specific type is handled by the appropriate handler, rather than one designed to handle a base type.</span></span>  
  
 <span data-ttu-id="b06f3-110">如果例外狀況處理常式正常完成，控制便會傳遞到周圍的範圍中。</span><span class="sxs-lookup"><span data-stu-id="b06f3-110">If the exception handler completes normally, control passes to the surrounding scope.</span></span> <span data-ttu-id="b06f3-111">如果在周圍的範圍中沒有擲回例外狀況，協調流程便會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="b06f3-111">If no exception has been thrown in the surrounding scope, the orchestration continues to run.</span></span> <span data-ttu-id="b06f3-112">如果例外狀況處理常式以擲回陳述式結束，除非您指定要擲回不同的例外狀況，否則會在要對其行動的周圍範圍再度擲回原始的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b06f3-112">If the exception handler ends with a throw statement, the original exception is thrown again for the surrounding scope to act upon, unless you specify a different exception that you want to be thrown.</span></span>  
  
 <span data-ttu-id="b06f3-113">如果找不到例外狀況處理常式，便會執行預設的例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="b06f3-113">If no exception handler can be located, the default exception handler will run.</span></span> <span data-ttu-id="b06f3-114">範圍的預設例外狀況處理常式會呼叫任何巢狀交易的補償，然後再度擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b06f3-114">The default exception handler for a scope will call the compensations for any nested transactions, and then throw the exception again.</span></span> <span data-ttu-id="b06f3-115">如果您撰寫自己的例外狀況處理常式，即可選擇不要傳送例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b06f3-115">If you write your own exception handler, you can choose not to propagate the exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b06f3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b06f3-116">See Also</span></span>  
 [<span data-ttu-id="b06f3-117">例外狀況</span><span class="sxs-lookup"><span data-stu-id="b06f3-117">Exceptions</span></span>](../core/exceptions.md)