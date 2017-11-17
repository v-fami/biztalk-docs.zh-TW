---
title: "收集例外狀況並將訊息路由修復和重新提交 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a61658a-0bac-4802-b506-02e61a3d2a9b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6a9123526dd35f788c86a610ee51ed8e90c1bc5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="collecting-exceptions-and-routing-messages-for-repair-and-resubmit"></a><span data-ttu-id="eb7e0-102">收集例外狀況並將訊息路由修復和重新提交</span><span class="sxs-lookup"><span data-stu-id="eb7e0-102">Collecting Exceptions and Routing Messages for Repair and Resubmit</span></span>
<span data-ttu-id="eb7e0-103">在此使用情況下，自訂例外狀況處理常式收到透過 Web 服務所收到的錯誤訊息，且將其路由傳送到磁碟檔案中隨附的 InfoPath 範本相容的格式[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="eb7e0-103">In this use case, a custom exception handler picks up a fault message received through a Web service and routes it to a disk file in a format compatible with an InfoPath template included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="eb7e0-104">使用者可以使用 Microsoft InfoPath 開啟檔案、 編輯訊息內容，並重新提交訊息以進行處理，如圖 1 所示。</span><span class="sxs-lookup"><span data-stu-id="eb7e0-104">The user can open the file using Microsoft InfoPath, edit the message contents, and resubmit the message for processing, as illustrated in Figure 1.</span></span>  
  
 <span data-ttu-id="eb7e0-105">![收集例外狀況修復](../esb-toolkit/media/ch3-collectingexceptionsrepair.gif "Ch3 CollectingExceptionsRepair")</span><span class="sxs-lookup"><span data-stu-id="eb7e0-105">![Collecting Exceptions Repair](../esb-toolkit/media/ch3-collectingexceptionsrepair.gif "Ch3-CollectingExceptionsRepair")</span></span>  
  
 <span data-ttu-id="eb7e0-106">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="eb7e0-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="eb7e0-107">**修復和重新提交的訊息路由傳送**</span><span class="sxs-lookup"><span data-stu-id="eb7e0-107">**Routing a message for repair and resubmission**</span></span>  
  
 <span data-ttu-id="eb7e0-108">「 修復和重新提交的自訂例外狀況處理常式 」 範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。</span><span class="sxs-lookup"><span data-stu-id="eb7e0-108">The Repair and Resubmit Custom Exception Handler sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="eb7e0-109">當協調流程中的處理序會遇到錯誤，例外狀況處理常式，協調流程會產生和發佈 ESB 錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="eb7e0-109">When a process in an orchestration encounters an error, the exception handler in that orchestration generates and publishes an ESB fault message.</span></span> <span data-ttu-id="eb7e0-110">此錯誤訊息包括，在承載中，訊息 (包括其內容屬性與相關的[!INCLUDE[prague](../includes/prague-md.md)]) 的 「 在途中 」 時，發生例外狀況，而且目前的例外狀況攔截 BizTalk 協調流程引擎。</span><span class="sxs-lookup"><span data-stu-id="eb7e0-110">This fault message includes, in its payload, the messages (including their context properties that are related to [!INCLUDE[prague](../includes/prague-md.md)]) that were "in flight" when the exception occurred, and the current exception caught by the BizTalk Orchestration engine.</span></span> <span data-ttu-id="eb7e0-111">ESB 錯誤訊息會發佈後，就是要訂閱的協調流程 （自訂例外狀況處理常式），擷取和會檢查傳遞訊息，以及系統例外狀況物件，並將訊息路由傳送至檔案的資料夾中，從中取消佇列使用者可以編輯使用 InfoPath 的訊息，並在其重新提交到 BizTalk Server 進行處理。</span><span class="sxs-lookup"><span data-stu-id="eb7e0-111">After an ESB fault message is published, it is de-queued to a subscribing orchestration (a custom exception handler) that extracts and inspects the in-flight messages and the system exception object, and routes the in-flight messages to a file folder, from which a user can edit the message using InfoPath and resubmit it to BizTalk Server for processing.</span></span>  
  
 <span data-ttu-id="eb7e0-112">如需詳細資訊，請參閱[執行修復並重新提交自訂例外狀況處理常式範例](../esb-toolkit/running-the-repair-and-resubmit-custom-exception-handler-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb7e0-112">For more information, see [Running the Repair and Resubmit Custom Exception Handler Sample](../esb-toolkit/running-the-repair-and-resubmit-custom-exception-handler-sample.md).</span></span>