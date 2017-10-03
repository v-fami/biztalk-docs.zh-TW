---
title: "如何建立接收埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, receive
- receive ports
- creating receive ports
ms.assetid: d390320e-12f1-4ead-b608-60bc1e273477
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1ca5727422fd7519443cc290d35d0c2e24d499f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-receive-ports"></a><span data-ttu-id="50eee-102">如何建立接收埠</span><span class="sxs-lookup"><span data-stu-id="50eee-102">How to Create Receive Ports</span></span>
<span data-ttu-id="50eee-103">請遵循下列步驟，使用 Visual Studio 建立接收埠。</span><span class="sxs-lookup"><span data-stu-id="50eee-103">Follow these steps to create a receive port using Visual Studio.</span></span>  
  
### <a name="to-create-a-receive-port"></a><span data-ttu-id="50eee-104">建立接收埠</span><span class="sxs-lookup"><span data-stu-id="50eee-104">To create a receive port</span></span>  
  
1.  <span data-ttu-id="50eee-105">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。</span><span class="sxs-lookup"><span data-stu-id="50eee-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="50eee-106">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="50eee-106">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Ports**.</span></span>  
  
3.  <span data-ttu-id="50eee-107">在**接收埠屬性**視窗，請在**一般**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="50eee-107">In the **Receive Port Properties** window, on the **General** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="50eee-108">在**名稱**欄位中，輸入`ReceiveFromTIBCORV`。</span><span class="sxs-lookup"><span data-stu-id="50eee-108">In the **Name** field, type `ReceiveFromTIBCORV`.</span></span>  
  
    2.  <span data-ttu-id="50eee-109">在**驗證**群組方塊中，指定使用驗證時，如何處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="50eee-109">In the **Authentication** group box, specify how messages are handled when using authentication.</span></span>  
  
    3.  <span data-ttu-id="50eee-110">選取**啟用的路由失敗訊息**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="50eee-110">Select the **Enable routing for failed messages** checkbox.</span></span>  
  
4.  <span data-ttu-id="50eee-111">在**接收位置**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="50eee-111">On the **Receive Locations** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="50eee-112">按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="50eee-112">Click **New**.</span></span>  
  
    2.  <span data-ttu-id="50eee-113">在**接收位置**視窗，請在**一般**頁面上，輸入**名稱**接收位置。</span><span class="sxs-lookup"><span data-stu-id="50eee-113">In the **Receive Locations** window, on the **General** page, type the **Name** of the receive location.</span></span>  
  
    3.  <span data-ttu-id="50eee-114">從**類型**下拉式清單中，選取傳輸類型，以及從**接收處理常式**下拉式清單中，選取傳輸位址。</span><span class="sxs-lookup"><span data-stu-id="50eee-114">From the **Type** drop-down list, select the transport type, and from the **Receive handler** drop-down list, select the transport address.</span></span>  
  
    4.  <span data-ttu-id="50eee-115">從**接收管線**下拉式清單中，選取接收管線。</span><span class="sxs-lookup"><span data-stu-id="50eee-115">From the **Receive pipeline** drop-down list, select the receive pipeline.</span></span>  
  
    5.  <span data-ttu-id="50eee-116">在**排程**頁面上，選取**開始日期**和**結束日期**限制接收文件。</span><span class="sxs-lookup"><span data-stu-id="50eee-116">On the **Schedule** page, select the **Start date** and the **End date** to restrict receiving documents.</span></span>  
  
    6.  <span data-ttu-id="50eee-117">選取**啟用服務窗口**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="50eee-117">Select the **Enable service window** checkbox.</span></span>  
  
    7.  <span data-ttu-id="50eee-118">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="50eee-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="50eee-119">在**輸入對應**頁面上，選取輸入的對應轉換文件上選取的連接埠。</span><span class="sxs-lookup"><span data-stu-id="50eee-119">On the **Inbound Maps** page, select the inbound maps for transforming documents on the selected port.</span></span>  
  
6.  <span data-ttu-id="50eee-120">在**追蹤**頁面上，選取所需的追蹤訊息內文和追蹤訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="50eee-120">On the **Tracking** page, select the desired tracking message bodies and tracking message properties.</span></span>  
  
7.  <span data-ttu-id="50eee-121">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="50eee-121">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50eee-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50eee-122">See Also</span></span>  
 [<span data-ttu-id="50eee-123">建立 TIBCO Rendezvous 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="50eee-123">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)