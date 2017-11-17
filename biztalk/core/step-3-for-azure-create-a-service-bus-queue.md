---
title: "（適用於 Azure) 的步驟 3： 建立服務匯流排佇列 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7192c3c-4ebf-49c4-b8ce-46a6e9fb5f4a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d55b3222798edb245000cdde8de52565c39758a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-for-azure-create-a-service-bus-queue"></a><span data-ttu-id="6b48f-102">（適用於 Azure) 的步驟 3： 建立服務匯流排佇列</span><span class="sxs-lookup"><span data-stu-id="6b48f-102">Step 3 (For Azure): Create a Service Bus Queue</span></span>
<span data-ttu-id="6b48f-103">在本主題中，您可以建立服務匯流排佇列的 X12 銷售訂單傳送它的後面處理和轉換使用 EDI 協議。</span><span class="sxs-lookup"><span data-stu-id="6b48f-103">In this topic, you create a Service Bus Queue to which the X12 sales order is sent after it is processed and transformed using the EDI agreement.</span></span>  
  
### <a name="to-create-a-service-bus-queue"></a><span data-ttu-id="6b48f-104">若要建立服務匯流排佇列</span><span class="sxs-lookup"><span data-stu-id="6b48f-104">To create a Service Bus Queue</span></span>  
  
1.  <span data-ttu-id="6b48f-105">登入[Windows Azure CTP Management Portal](http://go.microsoft.com/fwlink/p/?LinkId=202886)使用您的 Microsoft 帳戶。</span><span class="sxs-lookup"><span data-stu-id="6b48f-105">Log in to the [Windows Azure CTP Management Portal](http://go.microsoft.com/fwlink/p/?LinkId=202886) using your Microsoft account.</span></span>  
  
2.  <span data-ttu-id="6b48f-106">在較低的頁面左側，按一下  **AppFabric**。</span><span class="sxs-lookup"><span data-stu-id="6b48f-106">On the lower left-hand side of the page, click **AppFabric**.</span></span>  
  
3.  <span data-ttu-id="6b48f-107">在左側樹狀目錄中展開 服務、 展開您的訂閱，然後按一下命名空間中，您必須已經建立。</span><span class="sxs-lookup"><span data-stu-id="6b48f-107">Expand Services in the tree on the left-hand side, expand your subscription, and click a namespace that you must have already created.</span></span> <span data-ttu-id="6b48f-108">如果您還沒有命名空間，請參閱[How to： 建立或修改 Windows Azure CTP 服務命名空間](http://msdn.microsoft.com/library/windowsazure/hh697699.aspx)。</span><span class="sxs-lookup"><span data-stu-id="6b48f-108">If you don’t have a namespace already, see [How to: Create or Modify a Windows Azure CTP Service Namespace](http://msdn.microsoft.com/library/windowsazure/hh697699.aspx).</span></span>  
  
4.  <span data-ttu-id="6b48f-109">若要建立佇列按一下**新佇列**從**管理實體**從工具列則位於頁面頂端的類別。</span><span class="sxs-lookup"><span data-stu-id="6b48f-109">To create a Queue click **New Queue** from the **Manage Entities** category from the toolbar at the top of the page.</span></span>  
  
5.  <span data-ttu-id="6b48f-110">在**新佇列**對話方塊方塊中，輸入佇列的名稱。</span><span class="sxs-lookup"><span data-stu-id="6b48f-110">In the **New Queue** dialog box, enter a name for the Queue.</span></span> <span data-ttu-id="6b48f-111">此教學課程中，輸入相同的名稱。 `queueordersedi`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6b48f-111">For this tutorial, enter the name as `queueordersedi`, and then click **OK**.</span></span> <span data-ttu-id="6b48f-112">您指定這個名稱做為您在建立 EDI 協議的一部分[(Azure) 的步驟 2： 建立 EDI 協議](../core/step-2-for-azure-create-an-edi-agreement.md)。</span><span class="sxs-lookup"><span data-stu-id="6b48f-112">You specified this name as part of the EDI agreement you created in [Step 2 (For Azure): Create an EDI Agreement](../core/step-2-for-azure-create-an-edi-agreement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b48f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b48f-113">See Also</span></span>  
 [<span data-ttu-id="6b48f-114">教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式</span><span class="sxs-lookup"><span data-stu-id="6b48f-114">Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013</span></span>](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)