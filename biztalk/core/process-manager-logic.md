---
title: "程序管理員邏輯 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, processing
- processing, processing logic
ms.assetid: 6b69fc71-0f01-4513-9361-d7787d0cde6d
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e562362fec8e13589f1860e74024ffe70dad1c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="process-manager-logic"></a><span data-ttu-id="7f220-102">程序管理員邏輯</span><span class="sxs-lookup"><span data-stu-id="7f220-102">Process Manager Logic</span></span>
<span data-ttu-id="7f220-103">本章節描述如何處理序管理員， **OrderManager**協調流程、 處理訂單。</span><span class="sxs-lookup"><span data-stu-id="7f220-103">This section describes how the process manager, the **OrderManager** orchestration, processes orders.</span></span> <span data-ttu-id="7f220-104">它描述不同訂單訊息中的索引鍵欄位，並在整個協調流程中追蹤新訂單和更新的訂單。</span><span class="sxs-lookup"><span data-stu-id="7f220-104">It describes key fields in the various order messages and follows new and updated orders through the orchestration.</span></span>  
  
 <span data-ttu-id="7f220-105">**OrderManager**協調流程會協調附屬協調流程以處理訂單。</span><span class="sxs-lookup"><span data-stu-id="7f220-105">The **OrderManager** orchestration coordinates subordinate orchestrations to process the order.</span></span> <span data-ttu-id="7f220-106">您可以新增、 刪除或修改這些階段，而不必變更**OrderManager**。</span><span class="sxs-lookup"><span data-stu-id="7f220-106">You can add, delete, or modify these stages without having to change the **OrderManager**.</span></span> <span data-ttu-id="7f220-107">**OrderManager**執行大部分的協調，透過.NET 類別定義的自訂訊息。</span><span class="sxs-lookup"><span data-stu-id="7f220-107">The **OrderManager** does much of the coordination through custom messages defined by .NET classes.</span></span> <span data-ttu-id="7f220-108">如需解決方案中的所有訊息的清單，請參閱[商務程序管理解決方案的訊息參考](../core/message-reference-for-the-business-process-management-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="7f220-108">For a list of all messages in the solution, see [Message Reference for the Business Process Management Solution](../core/message-reference-for-the-business-process-management-solution.md).</span></span> <span data-ttu-id="7f220-109">定義訊息類型與.NET 類別的相關資訊，請參閱[使用者程式碼中的 建構訊息](../core/constructing-messages-in-user-code.md)。</span><span class="sxs-lookup"><span data-stu-id="7f220-109">For information about defining message types with .NET classes, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f220-110">由於大小和範圍**OrderManager**，您可能想要閱讀這些章節，特別是第二個，與 Microsoft Visual Studio 中開啟協調流程。</span><span class="sxs-lookup"><span data-stu-id="7f220-110">Because of the size and scope of **OrderManager**, you may want to read these sections, especially the second, with the orchestration open in Microsoft Visual Studio.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7f220-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="7f220-111">In This Section</span></span>  
  
-   [<span data-ttu-id="7f220-112">關鍵訊息和欄位</span><span class="sxs-lookup"><span data-stu-id="7f220-112">Key Messages and Fields</span></span>](../core/key-messages-and-fields.md)  
  
-   [<span data-ttu-id="7f220-113">透過處理序管理員的訂單流程</span><span class="sxs-lookup"><span data-stu-id="7f220-113">Order Flow through the Process Manager</span></span>](../core/order-flow-through-the-process-manager.md)