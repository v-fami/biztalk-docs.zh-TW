---
title: "如何設定延遲圖形 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Delay shape [Orchestration Designer], configuring
- Delay shape [Orchestration Designer]
- Delay shape [Orchestration Designer], timeouts
- Delay shape [Orchestration Designer], about Delay shape
- configuring [Orchestration Designer], Delay shapes
ms.assetid: 727be28d-932a-41d5-af3f-3ee6f7129a17
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b76448398facd3af7f3b9712491f9895ffb406d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-delay-shape"></a><span data-ttu-id="5cfd0-102">如何設定延遲圖形</span><span class="sxs-lookup"><span data-stu-id="5cfd0-102">How to Configure the Delay Shape</span></span>
![](../core/media/ebiz-orch-delay.gif "ebiz_orch_delay")  
<span data-ttu-id="5cfd0-103">延遲圖形</span><span class="sxs-lookup"><span data-stu-id="5cfd0-103">Delay shape</span></span>  
  
 <span data-ttu-id="5cfd0-104">有兩種方式來指定的逾時**延遲**:</span><span class="sxs-lookup"><span data-stu-id="5cfd0-104">There are two ways to specify the timeout for a **Delay**:</span></span>  
  
-   <span data-ttu-id="5cfd0-105">您可以使用**System.DateTime**，因而導致協調流程暫停到指定的日期和時間為止。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-105">You can use **System.DateTime**, which causes your orchestration to pause until the specified date and time is reached.</span></span>  
  
     <span data-ttu-id="5cfd0-106">System.DateTime.UtcNow.AddSeconds(60)</span><span class="sxs-lookup"><span data-stu-id="5cfd0-106">System.DateTime.UtcNow.AddSeconds(60)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5cfd0-107">延遲必須表示以國際標準時間 (UTC) 使用時**DateTime**。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-107">Delays must be expressed in Coordinated Universal Time (UTC) when using **DateTime**.</span></span>  
  
-   <span data-ttu-id="5cfd0-108">您可以使用**System.TimeSpan**，因而導致協調流程暫停一段指定的時間。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-108">You can use **System.TimeSpan**, which causes your orchestration to pause for the specified length of time.</span></span>  
  
     <span data-ttu-id="5cfd0-109">System.TimeSpan(0, 1, 0)</span><span class="sxs-lookup"><span data-stu-id="5cfd0-109">System.TimeSpan(0, 1, 0)</span></span>  
  
 <span data-ttu-id="5cfd0-110">如果您**延遲**圖形位於**接聽**圖形，您不需要運算式的結尾加入分號。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-110">If your **Delay** shape is inside a **Listen** shape, you do not need to add a semicolon at the end of the expression.</span></span>  
  
 <span data-ttu-id="5cfd0-111">如需有關**System.DateTime**和**System.TimeSpan**，請參閱 「 DateTime 結構 」 和 「 TimeSpan 結構 」[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]組合集合。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-111">For more information about **System.DateTime** and **System.TimeSpan**, see "DateTime Structure" and "TimeSpan Structure" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Combined Collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cfd0-112">中的多電腦安裝環境其中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 SQL Server 安裝在不同的電腦，**延遲**圖形可能比預期因為時間提早結束[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]機器並同步處理。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-112">In a multiple machines installation environment where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and SQL Server are installed on separated machines, the **Delay** shape may end earlier than expected because of the times on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] machines are unsynchronized.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cfd0-113">在逾時指定在負荷條件下**延遲**圖形可能比您指定的內容。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-113">Under the stress condition, the timeout specified in the **Delay** shape may occur later than what you have specified.</span></span> <span data-ttu-id="5cfd0-114">這是因為負荷條件下的執行緒匱乏現象。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-114">This is because of the thread starvation under the stress condition.</span></span>  
  
### <a name="to-configure-a-delay-shape"></a><span data-ttu-id="5cfd0-115">若要設定延遲圖形</span><span class="sxs-lookup"><span data-stu-id="5cfd0-115">To configure a Delay shape</span></span>  
  
1.  <span data-ttu-id="5cfd0-116">如果看不到 BizTalk 運算式編輯器，以滑鼠右鍵按一下**延遲**圖形，並按一下**編輯延遲**，或在 屬性 視窗中，按一下**省略**(**...**) 按鈕**運算式**屬性。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-116">If BizTalk Expression Editor is not visible, right-click the **Delay** shape and click **Edit Delay**, or in the Properties window, click the **Ellipsis** (**...**) button for the **Expression** property.</span></span>  
  
2.  <span data-ttu-id="5cfd0-117">在 [BizTalk 運算式編輯器] 中，建立該運算式會傳回**System.DateTime**物件或**System.TimeSpan**物件。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-117">In BizTalk Expression Editor, create an expression that returns a **System.DateTime** object or a **System.TimeSpan** object.</span></span> <span data-ttu-id="5cfd0-118">如需詳細資訊，請參閱[運算式的需求與限制](../core/requirements-and-limitations-for-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="5cfd0-118">For more information, see [Requirements and Limitations for Expressions](../core/requirements-and-limitations-for-expressions.md).</span></span>