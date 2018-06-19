---
title: 如何設定延遲圖形 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Delay shape [Orchestration Designer], configuring
- Delay shape [Orchestration Designer]
- Delay shape [Orchestration Designer], timeouts
- Delay shape [Orchestration Designer], about Delay shape
- configuring [Orchestration Designer], Delay shapes
ms.assetid: 727be28d-932a-41d5-af3f-3ee6f7129a17
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b76448398facd3af7f3b9712491f9895ffb406d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "22248334"
---
# <a name="how-to-configure-the-delay-shape"></a><span data-ttu-id="18a90-102">如何設定延遲圖形</span><span class="sxs-lookup"><span data-stu-id="18a90-102">How to Configure the Delay Shape</span></span>
<span data-ttu-id="18a90-103">![](../core/media/ebiz-orch-delay.gif "ebiz_orch_delay")</span><span class="sxs-lookup"><span data-stu-id="18a90-103">![](../core/media/ebiz-orch-delay.gif "ebiz_orch_delay")</span></span>  
<span data-ttu-id="18a90-104">延遲圖形</span><span class="sxs-lookup"><span data-stu-id="18a90-104">Delay shape</span></span>  
  
 <span data-ttu-id="18a90-105">有兩種方式來指定的逾時 **延遲**:</span><span class="sxs-lookup"><span data-stu-id="18a90-105">There are two ways to specify the timeout for a **Delay**:</span></span>  
  
-   <span data-ttu-id="18a90-106">您可以使用 **System.DateTime**, ，而導致您的協調流程暫停，直到指定的日期和時間為止。</span><span class="sxs-lookup"><span data-stu-id="18a90-106">You can use **System.DateTime**, which causes your orchestration to pause until the specified date and time is reached.</span></span>  
  
     <span data-ttu-id="18a90-107">System.DateTime.UtcNow.AddSeconds(60)</span><span class="sxs-lookup"><span data-stu-id="18a90-107">System.DateTime.UtcNow.AddSeconds(60)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="18a90-108">延遲必須以表示在國際標準時間 (UTC) 使用時 **DateTime**。</span><span class="sxs-lookup"><span data-stu-id="18a90-108">Delays must be expressed in Coordinated Universal Time (UTC) when using **DateTime**.</span></span>  
  
-   <span data-ttu-id="18a90-109">您可以使用 **System.TimeSpan**, ，而導致您的協調流程暫停指定的時間長度。</span><span class="sxs-lookup"><span data-stu-id="18a90-109">You can use **System.TimeSpan**, which causes your orchestration to pause for the specified length of time.</span></span>  
  
     <span data-ttu-id="18a90-110">System.TimeSpan(0, 1, 0)</span><span class="sxs-lookup"><span data-stu-id="18a90-110">System.TimeSpan(0, 1, 0)</span></span>  
  
 <span data-ttu-id="18a90-111">如果您 **延遲** 圖形位於 **接聽** 圖形，您不需要在運算式結尾處加上分號。</span><span class="sxs-lookup"><span data-stu-id="18a90-111">If your **Delay** shape is inside a **Listen** shape, you do not need to add a semicolon at the end of the expression.</span></span>  
  
 <span data-ttu-id="18a90-112">如需詳細資訊 **System.DateTime** 和 **System.TimeSpan**, ，請參閱 「 DateTime 結構 」 和 「 TimeSpan 結構 」 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 結合的集合。</span><span class="sxs-lookup"><span data-stu-id="18a90-112">For more information about **System.DateTime** and **System.TimeSpan**, see "DateTime Structure" and "TimeSpan Structure" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Combined Collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18a90-113">中的多電腦安裝環境其中 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 SQL Server 安裝在不同的電腦， **延遲** 圖形可能比預期時間因為提早結束 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 機器不同步。</span><span class="sxs-lookup"><span data-stu-id="18a90-113">In a multiple machines installation environment where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and SQL Server are installed on separated machines, the **Delay** shape may end earlier than expected because of the times on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] machines are unsynchronized.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18a90-114">在逾時指定在負荷條件下 **延遲** 圖形可能會發生晚於您指定的內容。</span><span class="sxs-lookup"><span data-stu-id="18a90-114">Under the stress condition, the timeout specified in the **Delay** shape may occur later than what you have specified.</span></span> <span data-ttu-id="18a90-115">這是因為負荷條件下的執行緒匱乏現象。</span><span class="sxs-lookup"><span data-stu-id="18a90-115">This is because of the thread starvation under the stress condition.</span></span>  
  
### <a name="to-configure-a-delay-shape"></a><span data-ttu-id="18a90-116">若要設定延遲圖形</span><span class="sxs-lookup"><span data-stu-id="18a90-116">To configure a Delay shape</span></span>  
  
1.  <span data-ttu-id="18a90-117">如果看不到 BizTalk 運算式編輯器，以滑鼠右鍵按一下 **延遲** 圖形，並按一下 **編輯延遲**, ，或在 屬性 視窗中，按一下  **省略** (**...**) 按鈕 **運算式** 屬性。</span><span class="sxs-lookup"><span data-stu-id="18a90-117">If BizTalk Expression Editor is not visible, right-click the **Delay** shape and click **Edit Delay**, or in the Properties window, click the **Ellipsis** (**...**) button for the **Expression** property.</span></span>  
  
2.  <span data-ttu-id="18a90-118">在 [BizTalk 運算式編輯器] 中，建立一個運算式會傳回 **System.DateTime** 物件或 **System.TimeSpan** 物件。</span><span class="sxs-lookup"><span data-stu-id="18a90-118">In BizTalk Expression Editor, create an expression that returns a **System.DateTime** object or a **System.TimeSpan** object.</span></span> <span data-ttu-id="18a90-119">如需詳細資訊，請參閱[運算式的需求與限制](../core/requirements-and-limitations-for-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="18a90-119">For more information, see [Requirements and Limitations for Expressions](../core/requirements-and-limitations-for-expressions.md).</span></span>