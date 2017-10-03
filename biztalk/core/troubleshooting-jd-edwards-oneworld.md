---
title: "疑難排解 JD Edwards OneWorld |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards OneWorld adapters, troubleshooting
- troubleshooting [JD Edwards OneWorld adapters]
ms.assetid: 15d73c2a-c6ee-46bf-8837-9c6ae3b098d2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b79e1bab85b52f816788b4e5e3550a5fa8059a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-jd-edwards-oneworld"></a><span data-ttu-id="78225-102">疑難排解 JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="78225-102">Troubleshooting JD Edwards OneWorld</span></span>
<span data-ttu-id="78225-103">本節說明您可能會在 BizTalk Adapter for JD Edwards OneWorld 中遇到的常見問題與錯誤訊息，並提供可能的解決方式。</span><span class="sxs-lookup"><span data-stu-id="78225-103">This section describes common issues and error messages that you might encounter in BizTalk Adapter for JD Edwards OneWorld, and provides possible corrections.</span></span> <span data-ttu-id="78225-104">此外，還會討論 Windows 事件追蹤的用法。</span><span class="sxs-lookup"><span data-stu-id="78225-104">In addition, it discusses the use of Event Tracing for Windows.</span></span>  
  
 <span data-ttu-id="78225-105">您可以使用下列偵錯/追蹤工具來進行此配接器的疑難排解：</span><span class="sxs-lookup"><span data-stu-id="78225-105">You can use the following debugging/tracing tools to troubleshoot the adapter:</span></span>  
  
-   <span data-ttu-id="78225-106">原生 BizTalk Server 偵錯 (例如，您連接埠上的「追蹤類型」或「協調流程偵錯工具」)。</span><span class="sxs-lookup"><span data-stu-id="78225-106">Native BizTalk Server debugging (for example, the Tracking Type on your port or the Orchestration Debugger).</span></span>  
  
-   <span data-ttu-id="78225-107">提交至事件日誌的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="78225-107">Error messages submitted to the Event Log.</span></span>  
  
-   <span data-ttu-id="78225-108">透過 BTAJDEOneWorldTrace.cmd 來擷取傳輸器、接收器與管理訊息，以及可轉換 .etl 檔案的工具 (例如，tracerpt.exe 或 tracedmp.exe)。</span><span class="sxs-lookup"><span data-stu-id="78225-108">The capture of transmitter, receiver, and management messages through BTAJDEOneWorldTrace.cmd and a tool that converts the .etl files, such as tracerpt.exe or tracedmp.exe.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="78225-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="78225-109">In This Section</span></span>  
  
-   [<span data-ttu-id="78225-110">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="78225-110">Error Messages</span></span>](../core/error-messages2.md)  
  
-   [<span data-ttu-id="78225-111">使用 Windows 事件追蹤</span><span class="sxs-lookup"><span data-stu-id="78225-111">Using Event Tracing for Windows</span></span>](../core/using-event-tracing-for-windows2.md)  
  
-   [<span data-ttu-id="78225-112">配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="78225-112">Troubleshooting the Adapter</span></span>](../core/troubleshooting-the-adapter3.md)