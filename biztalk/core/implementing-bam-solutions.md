---
title: 實作 BAM 解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18a5bc04-1b0a-4242-b599-760e696f5c06
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a167f2991250c446bedcb6bb235739f5414454e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257166"
---
# <a name="implementing-bam-solutions"></a><span data-ttu-id="41f72-102">實作 BAM 解決方案</span><span class="sxs-lookup"><span data-stu-id="41f72-102">Implementing BAM Solutions</span></span>
<span data-ttu-id="41f72-103">本節說明實作 BAM 解決方案的方法，包括擷取感興趣的資料、傳送資料至 BAM，以及基於變更商務需要而修改傳送至 BAM 的資料。</span><span class="sxs-lookup"><span data-stu-id="41f72-103">This section describes ways to implement your BAM solution, including capturing data of interest, sending data to BAM, and modifying the data you send to BAM as a result of changing business requirements.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="41f72-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="41f72-104">In This Section</span></span>  
  
-   [<span data-ttu-id="41f72-105">安裝 Bam-eventing 軟體</span><span class="sxs-lookup"><span data-stu-id="41f72-105">Installing the BAM-Eventing Software</span></span>](../core/installing-the-bam-eventing-software.md)  
  
-   [<span data-ttu-id="41f72-106">追蹤設定檔編輯器</span><span class="sxs-lookup"><span data-stu-id="41f72-106">Tracking Profile Editor</span></span>](../core/tracking-profile-editor.md)  
  
-   [<span data-ttu-id="41f72-107">使用事件資料流實作 BAM 活動</span><span class="sxs-lookup"><span data-stu-id="41f72-107">Implementing BAM Activities with Event Streams</span></span>](../core/implementing-bam-activities-with-event-streams.md)  
  
-   [<span data-ttu-id="41f72-108">何謂 BAM 攔截器？</span><span class="sxs-lookup"><span data-stu-id="41f72-108">What Is the BAM Interceptor?</span></span>](../core/what-is-the-bam-interceptor.md)  
  
-   [<span data-ttu-id="41f72-109">如何建立自訂的分析工作</span><span class="sxs-lookup"><span data-stu-id="41f72-109">How to Create a Custom Analysis Task</span></span>](../core/how-to-create-a-custom-analysis-task.md)  
  
-   [<span data-ttu-id="41f72-110">BAM 事件發佈的效能考量</span><span class="sxs-lookup"><span data-stu-id="41f72-110">Performance Considerations for BAM Event Publishing</span></span>](../core/performance-considerations-for-bam-event-publishing.md)  
  
-   [<span data-ttu-id="41f72-111">BAM 程式碼維護的考量</span><span class="sxs-lookup"><span data-stu-id="41f72-111">Considerations for BAM Code Maintenance</span></span>](../core/considerations-for-bam-code-maintenance.md)  
  
-   [<span data-ttu-id="41f72-112">使用 BAM Api 的考量事項</span><span class="sxs-lookup"><span data-stu-id="41f72-112">Considerations for Working with BAM APIs</span></span>](../core/considerations-for-working-with-bam-apis.md)  
  
-   [<span data-ttu-id="41f72-113">如何修飾 BAM 資料使用查閱</span><span class="sxs-lookup"><span data-stu-id="41f72-113">How to Enrich BAM Data Using Lookups</span></span>](../core/how-to-enrich-bam-data-using-lookups.md)  
  
-   [<span data-ttu-id="41f72-114">部署當地語系化的 BAM XML 檔案</span><span class="sxs-lookup"><span data-stu-id="41f72-114">Deploying Localized BAM XML Files</span></span>](../core/deploying-localized-bam-xml-files.md)  
  
-   [<span data-ttu-id="41f72-115">使用 BAM WCF 和 WF 攔截器</span><span class="sxs-lookup"><span data-stu-id="41f72-115">Using the BAM WCF and WF Interceptors</span></span>](../core/using-the-bam-wcf-and-wf-interceptors.md)