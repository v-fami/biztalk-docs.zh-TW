---
title: 步驟 2A： 新增檔案接收位置的互動存放區和轉送 （提取） 案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdc30e1-d80c-40bf-864d-bf136c77a2b8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 195480b616437eea7b1cfafa703d4ec5d0bd2b54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225270"
---
# <a name="step-2a-add-file-receive-locations-for-the-interact-store-and-forward-pull-scenario"></a><span data-ttu-id="77a9e-102">步驟 2A： 新增檔案接收位置的互動存放區和轉送 （提取） 案例</span><span class="sxs-lookup"><span data-stu-id="77a9e-102">Step 2A: Add FILE Receive Locations for the InterAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="77a9e-103">在開始此步驟之前，必須先完成[步驟 2： 新增 SWIFTNet 組態為互動存放與轉寄實例 Paramfile](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-store-and-forward.md)。</span><span class="sxs-lookup"><span data-stu-id="77a9e-103">Before you begin this step, you must complete [Step 2: Add SWIFTNet Configuration to the Paramfile for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-store-and-forward.md).</span></span>  
  
### <a name="to-add-a-file-receive-location"></a><span data-ttu-id="77a9e-104">若要新增 FILE 接收位置</span><span class="sxs-lookup"><span data-stu-id="77a9e-104">To add a FILE Receive location</span></span>  
  
1.  <span data-ttu-id="77a9e-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="77a9e-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="77a9e-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立接收埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="77a9e-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a receive port.</span></span>  
  
3.  <span data-ttu-id="77a9e-107">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠。**</span><span class="sxs-lookup"><span data-stu-id="77a9e-107">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
4.  <span data-ttu-id="77a9e-108">在**接收埠屬性**視窗中，接收埠， **Tutorial_IA_InputRequest_SnF**。</span><span class="sxs-lookup"><span data-stu-id="77a9e-108">In the **Receive Port Properties** window, name the receive port, **Tutorial_IA_InputRequest_SnF**.</span></span>  
  
5.  <span data-ttu-id="77a9e-109">在**接收埠屬性**視窗，請在**接收位置**索引標籤上，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="77a9e-109">In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.</span></span>  
  
6.  <span data-ttu-id="77a9e-110">在**接收位置屬性**視窗，請在**一般**索引標籤上，從**傳輸類型**下拉式清單中，選取**檔案**，和然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="77a9e-110">In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="77a9e-111">在**FILE 傳輸屬性**] 對話方塊中，輸入**C:\SWIFTAdapterTutorial\Interact\InputRequest_SnF**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="77a9e-111">In the **FILE Transport Properties** dialog box, type **C:\SWIFTAdapterTutorial\Interact\InputRequest_SnF**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="77a9e-112">在**接收位置屬性**視窗，請在**一般**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="77a9e-112">In the **Receive Location Properties** window, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="77a9e-113">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="77a9e-113">**Use this**</span></span>|<span data-ttu-id="77a9e-114">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="77a9e-114">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="77a9e-115">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="77a9e-115">**Receive handler**</span></span>|<span data-ttu-id="77a9e-116">從下拉式清單選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="77a9e-116">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="77a9e-117">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="77a9e-117">**Receive pipeline**</span></span>|<span data-ttu-id="77a9e-118">從下拉式清單選取**XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="77a9e-118">From the drop-down list, select **XMLReceive**.</span></span>|  
  
9. <span data-ttu-id="77a9e-119">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="77a9e-119">Click **OK**.</span></span>  
  
10. <span data-ttu-id="77a9e-120">重複步驟 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="77a9e-120">Repeat steps 1 and 2.</span></span>  
  
11. <span data-ttu-id="77a9e-121">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠。**</span><span class="sxs-lookup"><span data-stu-id="77a9e-121">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
12. <span data-ttu-id="77a9e-122">在**接收埠屬性**視窗中，接收埠， **Tutorial_IA_InputRequest_PullMode**。</span><span class="sxs-lookup"><span data-stu-id="77a9e-122">In the **Receive Port Properties** window, name the receive port, **Tutorial_IA_InputRequest_PullMode**.</span></span>  
  
13. <span data-ttu-id="77a9e-123">在**接收埠屬性**視窗，請在**接收位置**索引標籤上，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="77a9e-123">In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.</span></span>  
  
14. <span data-ttu-id="77a9e-124">在**接收位置屬性**視窗，請在**一般**索引標籤上，從**傳輸類型**下拉式清單中，選取**檔案**，和然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="77a9e-124">In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
15. <span data-ttu-id="77a9e-125">在**FILE 傳輸屬性**] 對話方塊中，輸入**C:\SWIFTAdapterTutorial\Interact\PullRequest**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="77a9e-125">In the **FILE Transport Properties** dialog box, type **C:\SWIFTAdapterTutorial\Interact\PullRequest**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="77a9e-126">在**接收位置屬性**視窗，請在**一般**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="77a9e-126">In the **Receive Location Properties** window, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="77a9e-127">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="77a9e-127">**Use this**</span></span>|<span data-ttu-id="77a9e-128">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="77a9e-128">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="77a9e-129">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="77a9e-129">**Receive handler**</span></span>|<span data-ttu-id="77a9e-130">從下拉式清單選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="77a9e-130">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="77a9e-131">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="77a9e-131">**Receive pipeline**</span></span>|<span data-ttu-id="77a9e-132">從下拉式清單選取**XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="77a9e-132">From the drop-down list, select **XMLReceive**.</span></span>|  
  
17. <span data-ttu-id="77a9e-133">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="77a9e-133">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77a9e-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77a9e-134">See Also</span></span>  
 <span data-ttu-id="77a9e-135">[步驟 2B： 將檔案傳送埠，以擷取 Sw:HandleRequest 訊息互動存放區和轉送 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports-to-get-sw-handlerequest-message-for-interact.md) </span><span class="sxs-lookup"><span data-stu-id="77a9e-135">[Step 2B: Add FILE Send Ports to Capture the Sw:HandleRequest Message for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports-to-get-sw-handlerequest-message-for-interact.md) </span></span>  
 [<span data-ttu-id="77a9e-136">步驟 2c: 互動存放區和轉送 （提取） 案例中加入互動的傳送埠</span><span class="sxs-lookup"><span data-stu-id="77a9e-136">Step 2C: Add an INTERACT Send Port for the InterAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-2c-add-interact-send-port-for-interact-store-and-forward-pull-scenario.md)