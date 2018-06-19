---
title: 在商務程序管理解決方案中處理的例外狀況 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors, tutorials
- process management solution tutorial, errors
ms.assetid: ac9fcb33-7dac-448e-88b8-04d4d439ea6a
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cd3134b8ed4e2fc6fd4a50d9b64397692ea32b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245878"
---
# <a name="exception-handling-in-the-business-process-management-solution"></a><span data-ttu-id="4edba-102">在商務程序管理解決方案中處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="4edba-102">Exception Handling in the Business Process Management Solution</span></span>
<span data-ttu-id="4edba-103">商務程序管理解決方案會使用一個特殊的例外狀況處理協調流程，以及標準的 BizTalk Server 例外狀況處理，來處理配接器、管線、對應及路由失敗，這是一個新的錯誤報告功能。</span><span class="sxs-lookup"><span data-stu-id="4edba-103">The business process management solution uses a special exception handling orchestration, as well as the standard BizTalk Server exception handling, and for adapter, pipeline, mapping, and routing failures, the new error reporting feature.</span></span> <span data-ttu-id="4edba-104">這個自訂的系統建基於**ExceptionHandler**協調流程。</span><span class="sxs-lookup"><span data-stu-id="4edba-104">This customized system is built around the **ExceptionHandler** orchestration.</span></span> <span data-ttu-id="4edba-105">解決方案會使用**ExceptionHandler**重試作業或重試在暫時問題過後可能會成功呼叫的協調流程。</span><span class="sxs-lookup"><span data-stu-id="4edba-105">The solution uses the **ExceptionHandler** orchestration to retry an operation or to retry a call that might succeed after a transient problem.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4edba-106">您可以重新使用程式碼從協調流程，例如**Activate**，使用**ExceptionHandler**協調流程。</span><span class="sxs-lookup"><span data-stu-id="4edba-106">You can re-use code from orchestrations, such as **Activate**, that use the **ExceptionHandler** orchestration.</span></span> <span data-ttu-id="4edba-107">所有這些協調流程包含標題為範圍**CallingCode**附加**例外狀況**區塊。</span><span class="sxs-lookup"><span data-stu-id="4edba-107">All of these orchestrations include a scope titled **CallingCode** with an attached **Exception** block.</span></span> <span data-ttu-id="4edba-108">中的程式碼取代**CallingCode**範圍與您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4edba-108">Replace the code in the **CallingCode** scope with your code.</span></span> <span data-ttu-id="4edba-109">**例外狀況**區塊會定義所有變數需要呼叫**ExceptionHandler**協調流程。</span><span class="sxs-lookup"><span data-stu-id="4edba-109">The **Exception** block defines all of the variables need to call the **ExceptionHandler** orchestration.</span></span> <span data-ttu-id="4edba-110">編輯指派給變數的值。</span><span class="sxs-lookup"><span data-stu-id="4edba-110">Edit the values assigned to the variables.</span></span>  
  
 <span data-ttu-id="4edba-111">解決方案會使用自訂的例外狀況及數個預先定義的 BizTalk 例外狀況，以在無法復原的錯誤時使用，例如遇到格式錯誤的訂單訊息時。</span><span class="sxs-lookup"><span data-stu-id="4edba-111">The solution uses custom exceptions, and a couple pre-defined BizTalk exceptions, for cases where the error is unrecoverable such as a malformed order message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4edba-112">解決方案會使用自訂的配接器來處理某些連接埠上的失敗。</span><span class="sxs-lookup"><span data-stu-id="4edba-112">The solution uses a custom adapter for handling failures on some ports.</span></span> <span data-ttu-id="4edba-113">如需配接器的詳細資訊，請參閱[Ops 配接器](../core/the-ops-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="4edba-113">For more information about the adapter, see [The Ops Adapter](../core/the-ops-adapter.md).</span></span>  
  
 <span data-ttu-id="4edba-114">本章節描述**ExceptionHandler**協調流程和自訂的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4edba-114">This section describes the **ExceptionHandler** orchestration and the custom exceptions.</span></span> <span data-ttu-id="4edba-115">本節也會簡短討論解決方案如何利用錯誤報告產品的功能。</span><span class="sxs-lookup"><span data-stu-id="4edba-115">It also discusses, briefly, how the solution employs the error reporting product feature.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4edba-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="4edba-116">In This Section</span></span>  
  
-   [<span data-ttu-id="4edba-117">ExceptionHandler 協調流程</span><span class="sxs-lookup"><span data-stu-id="4edba-117">The ExceptionHandler Orchestration</span></span>](../core/the-exceptionhandler-orchestration.md)  
  
-   [<span data-ttu-id="4edba-118">自訂例外狀況</span><span class="sxs-lookup"><span data-stu-id="4edba-118">Custom Exceptions</span></span>](../core/custom-exceptions.md)