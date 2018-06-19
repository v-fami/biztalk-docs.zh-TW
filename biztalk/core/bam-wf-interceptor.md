---
title: BAM WF 攔截器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e459084-cb72-4a75-9f5f-f1fd5fd80d17
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de770da5ee0f5d3270b0ee649b6bda61dc6d156e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231366"
---
# <a name="bam-wf-interceptor"></a><span data-ttu-id="33c10-102">BAM WF 攔截器</span><span class="sxs-lookup"><span data-stu-id="33c10-102">BAM WF Interceptor</span></span>
<span data-ttu-id="33c10-103">BAM WF 攔截器提供了在 WF 應用程式內追蹤資料的完整支援。</span><span class="sxs-lookup"><span data-stu-id="33c10-103">The BAM WF interceptor provides comprehensive support for tracking data within your WF application.</span></span>  
  
 <span data-ttu-id="33c10-104">您可以使用 BAM WF 攔截器執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="33c10-104">You can use the BAM WF interceptor to:</span></span>  
  
-   <span data-ttu-id="33c10-105">直接將工作流程應用程式資料傳送到 BAM，而不需要重新編譯您的 WF 應用程式。</span><span class="sxs-lookup"><span data-stu-id="33c10-105">Transparently deliver workflow application data to BAM without having to recompile your WF application.</span></span>  
  
-   <span data-ttu-id="33c10-106">鎖定工作流程內的特定活動，以選擇性地將工作流程應用程式資料傳送到 BAM。</span><span class="sxs-lookup"><span data-stu-id="33c10-106">Target specific activities within a workflow to selectively deliver workflow application data to BAM.</span></span>  
  
-   <span data-ttu-id="33c10-107">接受工作流程的交易語意。</span><span class="sxs-lookup"><span data-stu-id="33c10-107">Honor the transactional semantics of the workflow.</span></span> <span data-ttu-id="33c10-108">只有在主控交易認可時，才會將資料傳送到 BAM。</span><span class="sxs-lookup"><span data-stu-id="33c10-108">Data will be delivered to BAM only if the owning transaction commits.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="33c10-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="33c10-109">In This Section</span></span>  
  
-   [<span data-ttu-id="33c10-110">如何設定用於攔截的 Workflow Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="33c10-110">How to Configure a Workflow Foundation Application for Interception</span></span>](../core/how-to-configure-a-workflow-foundation-application-for-interception.md)  
  
-   [<span data-ttu-id="33c10-111">Windows Workflow Foundation 結構描述</span><span class="sxs-lookup"><span data-stu-id="33c10-111">Windows Workflow Foundation Schema</span></span>](../core/windows-workflow-foundation-schema.md)  
  
-   [<span data-ttu-id="33c10-112">通用事件篩選模式</span><span class="sxs-lookup"><span data-stu-id="33c10-112">Common Event Filter Patterns</span></span>](../core/common-event-filter-patterns.md)  
  
-   [<span data-ttu-id="33c10-113">Windows Workflow Foundation 中的作業</span><span class="sxs-lookup"><span data-stu-id="33c10-113">Operations in Windows Workflow Foundation</span></span>](../core/operations-in-windows-workflow-foundation.md)