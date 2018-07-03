---
title: 如何設定延遲圖形 |Microsoft Docs
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
ms.openlocfilehash: 7c00e002418dac53295828a4cbed632a6de0c235
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993647"
---
# <a name="how-to-configure-the-delay-shape"></a><span data-ttu-id="1c684-102">如何設定延遲圖形</span><span class="sxs-lookup"><span data-stu-id="1c684-102">How to Configure the Delay Shape</span></span>
<span data-ttu-id="1c684-103">![](../core/media/ebiz-orch-delay.gif "ebiz_orch_delay")</span><span class="sxs-lookup"><span data-stu-id="1c684-103">![](../core/media/ebiz-orch-delay.gif "ebiz_orch_delay")</span></span>  
<span data-ttu-id="1c684-104">延遲圖形</span><span class="sxs-lookup"><span data-stu-id="1c684-104">Delay shape</span></span>  
  
 <span data-ttu-id="1c684-105">有兩種方式來指定的逾時**延遲**:</span><span class="sxs-lookup"><span data-stu-id="1c684-105">There are two ways to specify the timeout for a **Delay**:</span></span>  
  
- <span data-ttu-id="1c684-106">您可以使用**System.DateTime**，因而導致協調流程暫停到指定的日期和時間為止。</span><span class="sxs-lookup"><span data-stu-id="1c684-106">You can use **System.DateTime**, which causes your orchestration to pause until the specified date and time is reached.</span></span>  
  
   <span data-ttu-id="1c684-107">System.DateTime.UtcNow.AddSeconds(60)</span><span class="sxs-lookup"><span data-stu-id="1c684-107">System.DateTime.UtcNow.AddSeconds(60)</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="1c684-108">延遲必須以表示以 Coordinated Universal Time (UTC) 使用時**DateTime**。</span><span class="sxs-lookup"><span data-stu-id="1c684-108">Delays must be expressed in Coordinated Universal Time (UTC) when using **DateTime**.</span></span>  
  
- <span data-ttu-id="1c684-109">您可以使用**System.TimeSpan**，這樣會使您的協調流程暫停指定的時間長度。</span><span class="sxs-lookup"><span data-stu-id="1c684-109">You can use **System.TimeSpan**, which causes your orchestration to pause for the specified length of time.</span></span>  
  
   <span data-ttu-id="1c684-110">System.TimeSpan(0, 1, 0)</span><span class="sxs-lookup"><span data-stu-id="1c684-110">System.TimeSpan(0, 1, 0)</span></span>  
  
  <span data-ttu-id="1c684-111">如果您**延遲**圖形位於**接聽**圖形，您不需要在運算式結尾加上分號。</span><span class="sxs-lookup"><span data-stu-id="1c684-111">If your **Delay** shape is inside a **Listen** shape, you do not need to add a semicolon at the end of the expression.</span></span>  
  
  <span data-ttu-id="1c684-112">如需詳細資訊**System.DateTime**並**System.TimeSpan**，請參閱中的 < DateTime 結構 > 和 < TimeSpan 結構 >[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]組合集合。</span><span class="sxs-lookup"><span data-stu-id="1c684-112">For more information about **System.DateTime** and **System.TimeSpan**, see "DateTime Structure" and "TimeSpan Structure" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Combined Collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c684-113">中的多電腦安裝環境所在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 SQL Server 安裝在不同的電腦**延遲**圖形可能比預期時間因為提早結束[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]機器是未同步處理。</span><span class="sxs-lookup"><span data-stu-id="1c684-113">In a multiple machines installation environment where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and SQL Server are installed on separated machines, the **Delay** shape may end earlier than expected because of the times on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] machines are unsynchronized.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="1c684-114">在負荷條件下指定中的逾時**延遲**圖形可能比您指定的內容。</span><span class="sxs-lookup"><span data-stu-id="1c684-114">Under the stress condition, the timeout specified in the **Delay** shape may occur later than what you have specified.</span></span> <span data-ttu-id="1c684-115">這是因為負荷條件下的執行緒匱乏現象。</span><span class="sxs-lookup"><span data-stu-id="1c684-115">This is because of the thread starvation under the stress condition.</span></span>  
  
### <a name="to-configure-a-delay-shape"></a><span data-ttu-id="1c684-116">若要設定延遲圖形</span><span class="sxs-lookup"><span data-stu-id="1c684-116">To configure a Delay shape</span></span>  
  
1.  <span data-ttu-id="1c684-117">如果看不到 BizTalk 運算式編輯器，以滑鼠右鍵按一下**延遲**圖形，然後按一下**編輯延遲**，或在 屬性 視窗中，按一下 **省略符號**(**...**) 按鈕**運算式**屬性。</span><span class="sxs-lookup"><span data-stu-id="1c684-117">If BizTalk Expression Editor is not visible, right-click the **Delay** shape and click **Edit Delay**, or in the Properties window, click the **Ellipsis** (**...**) button for the **Expression** property.</span></span>  
  
2.  <span data-ttu-id="1c684-118">在 [BizTalk 運算式編輯器] 中，建立該運算式會傳回**System.DateTime**物件或**System.TimeSpan**物件。</span><span class="sxs-lookup"><span data-stu-id="1c684-118">In BizTalk Expression Editor, create an expression that returns a **System.DateTime** object or a **System.TimeSpan** object.</span></span> <span data-ttu-id="1c684-119">如需詳細資訊，請參閱 <<c0> [ 運算式的需求和限制](../core/requirements-and-limitations-for-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="1c684-119">For more information, see [Requirements and Limitations for Expressions](../core/requirements-and-limitations-for-expressions.md).</span></span>