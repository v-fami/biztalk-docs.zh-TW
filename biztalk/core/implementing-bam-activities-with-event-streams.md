---
title: 實作 BAM 活動與事件資料流 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- activities [BAM], about activities
- activities [BAM]
- BAM, activities
ms.assetid: 94e6d9dd-93c3-4ab0-9de7-a860dd1e3406
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63594b956affc0f5b94f26ccdcb10d904ef171cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257342"
---
# <a name="implementing-bam-activities-with-event-streams"></a><span data-ttu-id="620c7-102">使用事件資料流實作 BAM 活動</span><span class="sxs-lookup"><span data-stu-id="620c7-102">Implementing BAM Activities with Event Streams</span></span>
<span data-ttu-id="620c7-103">BAM 活動代表商務中的工作單位，例如訂單或貸款申請。</span><span class="sxs-lookup"><span data-stu-id="620c7-103">A BAM activity represents a unit of work in the business, such as purchase order or loan application.</span></span> <span data-ttu-id="620c7-104">活動會對商務使用者或資訊工作者顯示，有關此工作單位的歷程記錄 (里程碑) 和資料。</span><span class="sxs-lookup"><span data-stu-id="620c7-104">The activity shows the history (milestones) and data about this unit of work to the business end user, or information worker.</span></span> <span data-ttu-id="620c7-105">例如，貸款申請活動可能包含如「已核准貸款」的里程碑，以及如「申請者名稱」和「貸款金額」等資料。</span><span class="sxs-lookup"><span data-stu-id="620c7-105">For example, a loan application activity might contain milestones such as “Loan approved” and data such as “Applicant name” and “Loan amount.”</span></span> <span data-ttu-id="620c7-106">BAM 活動通常會直接對應到商務程序，但是在高階抽象概念中，活動與您 IT 基礎結構的實際實作無關。</span><span class="sxs-lookup"><span data-stu-id="620c7-106">BAM activities often map directly to a business process, although as a high-level abstraction an activity is independent of the actual implementation of your IT infrastructure.</span></span>  
  
 <span data-ttu-id="620c7-107">身為開發人員的工作，就是只從特定活動內容中的實作公開相關的里程碑和資料。</span><span class="sxs-lookup"><span data-stu-id="620c7-107">Your job as a developer is to maintain this abstraction by exposing only the relevant milestones and data from the implementation in the context of a specific activity.</span></span> <span data-ttu-id="620c7-108">如需示範如何使用活動的程式碼範例，請參閱[BAM API （BizTalk Server 範例）](../core/bam-api-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="620c7-108">For a code sample that demonstrates the use of an activity, see [BAM API (BizTalk Server Sample)](../core/bam-api-biztalk-server-sample.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="620c7-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="620c7-109">In This Section</span></span>  
  
-   [<span data-ttu-id="620c7-110">為何為 BAM 撰寫程式碼？</span><span class="sxs-lookup"><span data-stu-id="620c7-110">Why Write Code For BAM?</span></span>](../core/why-write-code-for-bam.md)  
  
-   [<span data-ttu-id="620c7-111">開發人員適用的 BAM 概念</span><span class="sxs-lookup"><span data-stu-id="620c7-111">BAM Concepts for the Developer</span></span>](../core/bam-concepts-for-the-developer.md)  
  
-   [<span data-ttu-id="620c7-112">BAM 開發程序的概觀</span><span class="sxs-lookup"><span data-stu-id="620c7-112">Overview of the BAM Development Process</span></span>](../core/overview-of-the-bam-development-process.md)  
  
-   [<span data-ttu-id="620c7-113">EventStream 類別</span><span class="sxs-lookup"><span data-stu-id="620c7-113">EventStream Classes</span></span>](../core/eventstream-classes.md)  
  
-   [<span data-ttu-id="620c7-114">使用活動</span><span class="sxs-lookup"><span data-stu-id="620c7-114">Using an Activity</span></span>](../core/using-an-activity.md)  
  
-   [<span data-ttu-id="620c7-115">活動關係</span><span class="sxs-lookup"><span data-stu-id="620c7-115">Activity Relationships</span></span>](../core/activity-relationships.md)  
  
-   [<span data-ttu-id="620c7-116">活動接續</span><span class="sxs-lookup"><span data-stu-id="620c7-116">Activity Continuation</span></span>](../core/activity-continuation.md)  
  
-   [<span data-ttu-id="620c7-117">迴圈活動</span><span class="sxs-lookup"><span data-stu-id="620c7-117">Looping Activities</span></span>](../core/looping-activities.md)  
  
-   [<span data-ttu-id="620c7-118">檢測解決方案： 逐步 API 使用方式</span><span class="sxs-lookup"><span data-stu-id="620c7-118">Instrumenting a Solution: Step-by-Step API Usage</span></span>](../core/instrumenting-a-solution-step-by-step-api-usage.md)