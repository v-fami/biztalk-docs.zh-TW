---
title: "疑難排解 JD Edwards OneWorld |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 15d73c2a-c6ee-46bf-8837-9c6ae3b098d2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85c4b1099814c4cf7489f18ae5cd921f46f180bc
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="troubleshooting-jd-edwards-oneworld"></a><span data-ttu-id="869a1-102">疑難排解 JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="869a1-102">Troubleshooting JD Edwards OneWorld</span></span>

## <a name="overview"></a><span data-ttu-id="869a1-103">概觀</span><span class="sxs-lookup"><span data-stu-id="869a1-103">Overview</span></span>
<span data-ttu-id="869a1-104">本節說明您可能會在 BizTalk Adapter for JD Edwards OneWorld 中遇到的常見問題與錯誤訊息，並提供可能的解決方式。</span><span class="sxs-lookup"><span data-stu-id="869a1-104">This section describes common issues and error messages that you might encounter in BizTalk Adapter for JD Edwards OneWorld, and provides possible corrections.</span></span> <span data-ttu-id="869a1-105">此外，還會討論 Windows 事件追蹤的用法。</span><span class="sxs-lookup"><span data-stu-id="869a1-105">In addition, it discusses the use of Event Tracing for Windows.</span></span>  
  
 <span data-ttu-id="869a1-106">您可以使用下列偵錯/追蹤工具來進行此配接器的疑難排解：</span><span class="sxs-lookup"><span data-stu-id="869a1-106">You can use the following debugging/tracing tools to troubleshoot the adapter:</span></span>  
  
-   <span data-ttu-id="869a1-107">原生 BizTalk Server 偵錯 (例如，您連接埠上的「追蹤類型」或「協調流程偵錯工具」)。</span><span class="sxs-lookup"><span data-stu-id="869a1-107">Native BizTalk Server debugging (for example, the Tracking Type on your port or the Orchestration Debugger).</span></span>  
  
-   <span data-ttu-id="869a1-108">提交至事件日誌的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="869a1-108">Error messages submitted to the Event Log.</span></span>  
  
-   <span data-ttu-id="869a1-109">透過 BTAJDEOneWorldTrace.cmd 來擷取傳輸器、接收器與管理訊息，以及可轉換 .etl 檔案的工具 (例如，tracerpt.exe 或 tracedmp.exe)。</span><span class="sxs-lookup"><span data-stu-id="869a1-109">The capture of transmitter, receiver, and management messages through BTAJDEOneWorldTrace.cmd and a tool that converts the .etl files, such as tracerpt.exe or tracedmp.exe.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="869a1-110">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="869a1-110">Next steps</span></span>
  
-   [<span data-ttu-id="869a1-111">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="869a1-111">Error Messages</span></span>](../core/error-messages2.md)  
  
-   [<span data-ttu-id="869a1-112">使用 Windows 事件追蹤</span><span class="sxs-lookup"><span data-stu-id="869a1-112">Using Event Tracing for Windows</span></span>](../core/using-event-tracing-for-windows2.md)  
  
-   [<span data-ttu-id="869a1-113">配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="869a1-113">Troubleshooting the Adapter</span></span>](../core/troubleshooting-the-adapter3.md)