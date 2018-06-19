---
title: Ops 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters, Ops adapters
- Ops adapters, about Ops adapters
- Ops adapters
- process management solution tutorial, Ops adapters
- process management solution tutorial, errors
ms.assetid: 7f747a5f-14af-4e4c-bc29-f083f8f00bd0
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67463adf4e1e960ab6608e67595a679804aa223e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279374"
---
# <a name="the-ops-adapter"></a><span data-ttu-id="21f39-102">Ops 配接器</span><span class="sxs-lookup"><span data-stu-id="21f39-102">The Ops Adapter</span></span>
<span data-ttu-id="21f39-103">解決方案的設計是儘可能將有問題的訊息和錯誤傳送到決策作業系統，以決定要修正錯誤或終止訂單。</span><span class="sxs-lookup"><span data-stu-id="21f39-103">The design of the solution is to pass, where possible, problematic messages and errors to operations systems that make a decision about fixing the error or terminating the order.</span></span> <span data-ttu-id="21f39-104">結合新錯誤報告功能的 Ops 配接器可處理許多這類情況。</span><span class="sxs-lookup"><span data-stu-id="21f39-104">The Ops adapter, combined with the new error reporting feature, handles many of these cases.</span></span>  
  
 <span data-ttu-id="21f39-105">解決方案可在設定為使用新錯誤報告功能的連接埠上使用配接器。</span><span class="sxs-lookup"><span data-stu-id="21f39-105">The solution uses the adapter on a port configured to use the new error reporting feature.</span></span> <span data-ttu-id="21f39-106">當它收到錯誤時，配接器會呼叫兩個方法：**初始化**和**Execute**，在指定的組件中的類別。</span><span class="sxs-lookup"><span data-stu-id="21f39-106">When it receives an error, the adapter calls two methods, **Initialize** and **Execute**, on a class in a specified assembly.</span></span> <span data-ttu-id="21f39-107">在解決方案中，這些方法會將錯誤傳送到正確的作業群組。</span><span class="sxs-lookup"><span data-stu-id="21f39-107">In the solution, these methods send the error to the correct operations group.</span></span>  
  
 <span data-ttu-id="21f39-108">解決方案包括一個範例處理常式，但您可以輕鬆的撰寫自己的處理常式，並使用其他解決方案中的配接器。</span><span class="sxs-lookup"><span data-stu-id="21f39-108">The solution includes a sample handler, although you can easily write your own and use the adapter in other solutions.</span></span> <span data-ttu-id="21f39-109">如需新的錯誤報告功能的一般資訊，請參閱[使用失敗訊息路由](../core/using-failed-message-routing.md)。</span><span class="sxs-lookup"><span data-stu-id="21f39-109">For general information about the new error reporting feature, see [Using Failed Message Routing](../core/using-failed-message-routing.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21f39-110">Ops 配接器是使用「配接器架構」建置。</span><span class="sxs-lookup"><span data-stu-id="21f39-110">The Ops adapter is built using the Adapter Framework.</span></span> <span data-ttu-id="21f39-111">建置配接器架構的相關資訊，請參閱[開發自訂配接器](../core/developing-custom-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="21f39-111">For information about building adapters with the framework, see [Developing Custom Adapters](../core/developing-custom-adapters.md).</span></span>  
  
 <span data-ttu-id="21f39-112">本節描述配接器的運作方式和設定方式，同時提供有關錯誤處理常式組件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="21f39-112">This section describes how the adapter works and how to configure it, and provides details about the error handler assemblies.</span></span> <span data-ttu-id="21f39-113">此節以非常有用的實作詳細資料做為結束，協助使用者修改配接器或在其他應用程式中使用配接器。</span><span class="sxs-lookup"><span data-stu-id="21f39-113">The section concludes with implementation details that would be helpful to users who wish to modify the adapter or use it in other applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="21f39-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="21f39-114">In This Section</span></span>  
  
-   [<span data-ttu-id="21f39-115">使用 Ops 配接器</span><span class="sxs-lookup"><span data-stu-id="21f39-115">Using the Ops Adapter</span></span>](../core/using-the-ops-adapter.md)  
  
-   [<span data-ttu-id="21f39-116">範例作業錯誤處理常式</span><span class="sxs-lookup"><span data-stu-id="21f39-116">The Sample Operations Error Handler</span></span>](../core/the-sample-operations-error-handler.md)  
  
-   [<span data-ttu-id="21f39-117">Ops 配接器實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="21f39-117">Ops Adapter Implementation Details</span></span>](../core/ops-adapter-implementation-details.md)