---
title: "疑難排解 JD Edwards EnterpriseOne |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting [JD Edwards EnterpriseOne adapters]
- JD Edwards EnterpriseOne adapters, troubleshooting
- adapters [JD Edwards EnterpriseOne adapters], troubleshooting
ms.assetid: 7b3e68fa-b81d-4767-ab62-3200ce89d81c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d32a4db56dc60d3a57d6e43985cc30a2868098bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-jd-edwards-enterpriseone"></a><span data-ttu-id="c5f60-102">對 JD Edwards EnterpriseOne 進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="c5f60-102">Troubleshooting JD Edwards EnterpriseOne</span></span>
<span data-ttu-id="c5f60-103">本節描述您可能在 BizTalk Adapter for JD Edwards EnterpriseOne 中遇到的常見問題與錯誤訊息，並提供可能的更正方式。</span><span class="sxs-lookup"><span data-stu-id="c5f60-103">This section describes common issues and error messages you might encounter in BizTalk Adapter for JD Edwards EnterpriseOne and provides possible corrections for them.</span></span> <span data-ttu-id="c5f60-104">此外，還會討論 Windows 事件追蹤的用法。</span><span class="sxs-lookup"><span data-stu-id="c5f60-104">In addition, it discusses the use of Event Tracing for Windows.</span></span>  
  
 <span data-ttu-id="c5f60-105">您可以使用下列偵錯/追蹤工具來進行此配接器的疑難排解：</span><span class="sxs-lookup"><span data-stu-id="c5f60-105">You can use the following debugging/tracing tools to troubleshoot the adapter:</span></span>  
  
-   <span data-ttu-id="c5f60-106">原生 BizTalk Server 偵錯 (例如，您連接埠上的「追蹤類型」或「協調流程偵錯工具」)。</span><span class="sxs-lookup"><span data-stu-id="c5f60-106">Native BizTalk Server debugging (for example, the Tracking Type on your port or the Orchestration Debugger).</span></span>  
  
-   <span data-ttu-id="c5f60-107">提交至事件日誌的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c5f60-107">Error messages submitted to the Event Log.</span></span>  
  
-   <span data-ttu-id="c5f60-108">透過 BTAJDEEnterpriseOneTrace.cmd 擷取的傳輸器、接收器和管理訊息，以及可轉換 .etl 檔的工具 (如 tracerpt.exe 或 tracedmp.exe)。</span><span class="sxs-lookup"><span data-stu-id="c5f60-108">The capture of transmitter, receiver, and management messages through BTAJDEEnterpriseOneTrace.cmd and a tool that converts.etl files, such as tracerpt.exe or tracedmp.exe.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c5f60-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="c5f60-109">In This Section</span></span>  
  
-   [<span data-ttu-id="c5f60-110">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="c5f60-110">Error Messages</span></span>](../core/error-messages1.md)  
  
-   [<span data-ttu-id="c5f60-111">使用 Windows 事件追蹤</span><span class="sxs-lookup"><span data-stu-id="c5f60-111">Using Event Tracing for Windows</span></span>](../core/using-event-tracing-for-windows4.md)  
  
-   [<span data-ttu-id="c5f60-112">配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="c5f60-112">Troubleshooting the Adapter</span></span>](../core/troubleshooting-the-adapter1.md)