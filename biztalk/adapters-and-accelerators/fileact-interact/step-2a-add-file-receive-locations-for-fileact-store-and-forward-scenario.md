---
title: 步驟 2A-新增檔案接收位置 |Microsoft 文件
description: 步驟 2A-新增檔案在 BizTalk Server 接收位置的 FileAct 存放與轉寄 （提取） 案例
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 13720ebb-fbe4-4fe1-a095-9ae14c62def1
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e297a85f309445c3caf569d2d752be58997e9754
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224070"
---
# <a name="step-2a-add-file-receive-locations-for-the-fileact-store-and-forward-pull-scenario"></a><span data-ttu-id="68d69-103">步驟 2A： 新增檔案接收位置的 FileAct 存放與轉寄 （提取） 案例</span><span class="sxs-lookup"><span data-stu-id="68d69-103">Step 2A: Add FILE Receive Locations for the FileAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="68d69-104">在開始此步驟之前，必須先完成[步驟 1： 將 SWIFT 介面卡 FileAct 存放與轉寄 （提取） 案例](step-1-configure-the-swift-adapter-for-fileact-store-and-forward-pull-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="68d69-104">Before you begin this step, you must complete [Step 1: Configure the SWIFT Adapter for the FileAct Store and Forward (Pull) Scenario](step-1-configure-the-swift-adapter-for-fileact-store-and-forward-pull-scenario.md).</span></span>  
  
## <a name="add-a-file-receive-location"></a><span data-ttu-id="68d69-105">新增檔案接收位置</span><span class="sxs-lookup"><span data-stu-id="68d69-105">Add a FILE Receive location</span></span>  
  
1.  <span data-ttu-id="68d69-106">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="68d69-106">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="68d69-107">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立接收埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="68d69-107">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a receive port.</span></span>  
  
3.  <span data-ttu-id="68d69-108">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠。**</span><span class="sxs-lookup"><span data-stu-id="68d69-108">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
4.  <span data-ttu-id="68d69-109">在**接收埠屬性**視窗中，接收埠， **Tutorial_FA_InputRequest_SnF**。</span><span class="sxs-lookup"><span data-stu-id="68d69-109">In the **Receive Port Properties** window, name the receive port, **Tutorial_FA_InputRequest_SnF**.</span></span>  
  
5.  <span data-ttu-id="68d69-110">在**接收埠屬性**視窗，請在**接收位置**索引標籤上，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="68d69-110">In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.</span></span>  
  
6.  <span data-ttu-id="68d69-111">在**接收位置屬性**視窗，請在**一般**索引標籤上，從**傳輸類型**下拉式清單中，選取**檔案**，和然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="68d69-111">In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="68d69-112">在**FILE 傳輸屬性**] 對話方塊中，輸入**C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="68d69-112">In the **FILE Transport Properties** dialog box, type **C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="68d69-113">在**接收位置屬性**視窗，請在**一般**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="68d69-113">In the **Receive Location Properties** window, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="68d69-114">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="68d69-114">**Use this**</span></span>|<span data-ttu-id="68d69-115">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="68d69-115">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="68d69-116">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="68d69-116">**Receive handler**</span></span>|<span data-ttu-id="68d69-117">從下拉式清單選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="68d69-117">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="68d69-118">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="68d69-118">**Receive pipeline**</span></span>|<span data-ttu-id="68d69-119">從下拉式清單選取**XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="68d69-119">From the drop-down list, select **XMLReceive**.</span></span>|  
  
9. <span data-ttu-id="68d69-120">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="68d69-120">Click **OK**.</span></span>  
  
10. <span data-ttu-id="68d69-121">重複步驟 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="68d69-121">Repeat steps 1 and 2.</span></span>  
  
11. <span data-ttu-id="68d69-122">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠。**</span><span class="sxs-lookup"><span data-stu-id="68d69-122">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
12. <span data-ttu-id="68d69-123">在**接收埠屬性**視窗中，接收埠， **Tutorial_ FA_InputRequest_PullMode**。</span><span class="sxs-lookup"><span data-stu-id="68d69-123">In the **Receive Port Properties** window, name the receive port, **Tutorial_ FA_InputRequest_PullMode**.</span></span>  
  
13. <span data-ttu-id="68d69-124">在**接收埠屬性**視窗，請在**接收位置**索引標籤上，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="68d69-124">In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.</span></span>  
  
14. <span data-ttu-id="68d69-125">在**接收位置屬性**視窗，請在**一般**索引標籤上，從**傳輸類型**下拉式清單中，選取**檔案**，和然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="68d69-125">In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
15. <span data-ttu-id="68d69-126">在**FILE 傳輸屬性**] 對話方塊中，輸入**C:\SWIFTAdapterTutorial\Interact\PullRequest**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="68d69-126">In the **FILE Transport Properties** dialog box, type **C:\SWIFTAdapterTutorial\Interact\PullRequest**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="68d69-127">在**接收位置屬性**視窗，請在**一般**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="68d69-127">In the **Receive Location Properties** window, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="68d69-128">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="68d69-128">**Use this**</span></span>|<span data-ttu-id="68d69-129">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="68d69-129">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="68d69-130">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="68d69-130">**Receive handler**</span></span>|<span data-ttu-id="68d69-131">從下拉式清單選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="68d69-131">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="68d69-132">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="68d69-132">**Receive pipeline**</span></span>|<span data-ttu-id="68d69-133">從下拉式清單選取**XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="68d69-133">From the drop-down list, select **XMLReceive**.</span></span>|  
  
17. <span data-ttu-id="68d69-134">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="68d69-134">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="68d69-135">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="68d69-135">Next steps</span></span>
-  [<span data-ttu-id="68d69-136">步驟 2B： 將檔案傳送埠，以擷取 Sw:HandleFileRequest 和 Sw:HandleSnFRequest FileAct 存放與轉寄的訊息 （提取） 案例</span><span class="sxs-lookup"><span data-stu-id="68d69-136">Step 2B: Add FILE Send Ports to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward (Pull) Scenario</span></span>](step-2b-add-file-send-ports--get-sw-handlefilerequest-and-sw-handlesnfrequest.md)   
-  [<span data-ttu-id="68d69-137">步驟 2c： 新增為 FileAct 存放與轉寄 （提取） 實例 FILEACT 傳送埠</span><span class="sxs-lookup"><span data-stu-id="68d69-137">Step 2C: Add a FILEACT Send Port for the FileAct Store and Forward (Pull) Scenario</span></span>](step-2c-add-a-fileact-send-port-for-fileact-store-and-forward-pull-scenario.md)