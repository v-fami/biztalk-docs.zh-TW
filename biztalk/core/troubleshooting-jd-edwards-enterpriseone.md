---
title: "疑難排解 JD Edwards EnterpriseOne 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b3e68fa-b81d-4767-ab62-3200ce89d81c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d46fd3375f49f9fabd6ce8028cc226bce5885db
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="troubleshooting-jd-edwards-enterpriseone"></a><span data-ttu-id="17179-102">對 JD Edwards EnterpriseOne 進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="17179-102">Troubleshooting JD Edwards EnterpriseOne</span></span>

## <a name="overview"></a><span data-ttu-id="17179-103">概觀</span><span class="sxs-lookup"><span data-stu-id="17179-103">Overview</span></span>
<span data-ttu-id="17179-104">本節描述您可能在 BizTalk Adapter for JD Edwards EnterpriseOne 中遇到的常見問題與錯誤訊息，並提供可能的更正方式。</span><span class="sxs-lookup"><span data-stu-id="17179-104">This section describes common issues and error messages you might encounter in BizTalk Adapter for JD Edwards EnterpriseOne and provides possible corrections for them.</span></span> <span data-ttu-id="17179-105">此外，還會討論 Windows 事件追蹤的用法。</span><span class="sxs-lookup"><span data-stu-id="17179-105">In addition, it discusses the use of Event Tracing for Windows.</span></span>  
  
 <span data-ttu-id="17179-106">您可以使用下列偵錯/追蹤工具來進行此配接器的疑難排解：</span><span class="sxs-lookup"><span data-stu-id="17179-106">You can use the following debugging/tracing tools to troubleshoot the adapter:</span></span>  
  
-   <span data-ttu-id="17179-107">原生 BizTalk Server 偵錯 (例如，您連接埠上的「追蹤類型」或「協調流程偵錯工具」)。</span><span class="sxs-lookup"><span data-stu-id="17179-107">Native BizTalk Server debugging (for example, the Tracking Type on your port or the Orchestration Debugger).</span></span>  
  
-   <span data-ttu-id="17179-108">提交至事件日誌的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="17179-108">Error messages submitted to the Event Log.</span></span>  
  
-   <span data-ttu-id="17179-109">透過 BTAJDEEnterpriseOneTrace.cmd 擷取的傳輸器、接收器和管理訊息，以及可轉換 .etl 檔的工具 (如 tracerpt.exe 或 tracedmp.exe)。</span><span class="sxs-lookup"><span data-stu-id="17179-109">The capture of transmitter, receiver, and management messages through BTAJDEEnterpriseOneTrace.cmd and a tool that converts.etl files, such as tracerpt.exe or tracedmp.exe.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="17179-110">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="17179-110">Next steps</span></span>
  
-   [<span data-ttu-id="17179-111">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="17179-111">Error Messages</span></span>](../core/error-messages1.md)  
  
-   [<span data-ttu-id="17179-112">使用 Windows 事件追蹤</span><span class="sxs-lookup"><span data-stu-id="17179-112">Using Event Tracing for Windows</span></span>](../core/using-event-tracing-for-windows4.md)  
  
-   [<span data-ttu-id="17179-113">配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="17179-113">Troubleshooting the Adapter</span></span>](../core/troubleshooting-the-adapter1.md)