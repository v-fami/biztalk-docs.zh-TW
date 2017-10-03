---
title: "步驟 3A： 新增 FILE 接收位置為 FileAct 存放與轉寄實例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67ecbf4a-a2b4-4534-8ca1-3bfbb6a697bf
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e02f636500ed21d4442a43078bcd407c91d69d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3a-add-a-file-receive-location-for-the-fileact-store-and-forward-scenario"></a><span data-ttu-id="85617-102">步驟 3A： 新增 FILE 接收位置為 FileAct 存放與轉寄的實例</span><span class="sxs-lookup"><span data-stu-id="85617-102">Step 3A: Add a FILE Receive Location for the FileAct Store and Forward Scenario</span></span>
<span data-ttu-id="85617-103">在開始此步驟之前，必須先完成[步驟 2： 新增 SWIFTNet 組態為 FileAct 存放與轉寄實例 Paramfile](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-fileact-store-and-forward.md)。</span><span class="sxs-lookup"><span data-stu-id="85617-103">Before you begin this step, you must complete [Step 2: Add SWIFTNet Configuration to the Paramfile for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-fileact-store-and-forward.md).</span></span>  
  
### <a name="to-add-a-file-receive-location"></a><span data-ttu-id="85617-104">若要新增 FILE 接收位置</span><span class="sxs-lookup"><span data-stu-id="85617-104">To add a FILE receive location</span></span>  
  
1.  <span data-ttu-id="85617-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="85617-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="85617-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立接收埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="85617-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a receive port.</span></span>  
  
3.  <span data-ttu-id="85617-107">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠。**</span><span class="sxs-lookup"><span data-stu-id="85617-107">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
4.  <span data-ttu-id="85617-108">在**接收埠屬性**視窗中，接收埠，Tutorial_FA_InputRequest_SnF。</span><span class="sxs-lookup"><span data-stu-id="85617-108">In the **Receive Port Properties** window, name the receive port, Tutorial_FA_InputRequest_SnF.</span></span>  
  
5.  <span data-ttu-id="85617-109">在**接收埠屬性**視窗，請在**接收位置**索引標籤上，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="85617-109">In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.</span></span>  
  
6.  <span data-ttu-id="85617-110">在**接收位置屬性**視窗，請在**一般**索引標籤上，從**傳輸類型**下拉式清單中，選取**檔案**，和然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="85617-110">In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="85617-111">在**FILE 傳輸屬性**對話方塊中，於**接收資料夾**方塊、 輸入 C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="85617-111">In the **FILE Transport Properties** dialog box, in the **Receive folder** box, type C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="85617-112">在**接收位置屬性**視窗，請在**一般**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="85617-112">In the **Receive Location Properties** window, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="85617-113">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="85617-113">**Use this**</span></span>|<span data-ttu-id="85617-114">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="85617-114">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="85617-115">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="85617-115">**Receive handler**</span></span>|<span data-ttu-id="85617-116">從下拉式清單選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="85617-116">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="85617-117">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="85617-117">**Receive pipeline**</span></span>|<span data-ttu-id="85617-118">從下拉式清單選取**XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="85617-118">From the drop-down list, select **XMLReceive**.</span></span>|  
  
9. <span data-ttu-id="85617-119">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="85617-119">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85617-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85617-120">See Also</span></span>  
 <span data-ttu-id="85617-121">[步驟 3： 建立傳送埠和接收埠為 FileAct 存放與轉寄的實例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="85617-121">[Step 3: Create Send Ports and Receive Ports for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md) </span></span>  
 <span data-ttu-id="85617-122">[步驟 3B： 新增 FILEACT 接收位置 FileAct 存放與轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="85617-122">[Step 3B: Add a FILEACT Receive Location for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-fileact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="85617-123">[步驟 3c： 加入擷取 FileAct 存放與轉寄案例的 Sw:HandleFileRequest 和 Sw:HandleSnFRequest 訊息的 FILE 傳送埠](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlefilerequest-and-sw-handlesnfrequest.md) </span><span class="sxs-lookup"><span data-stu-id="85617-123">[Step 3C: Add a FILE Send Port to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlefilerequest-and-sw-handlesnfrequest.md) </span></span>  
 [<span data-ttu-id="85617-124">步驟 3D： 新增為 FileAct 存放與轉寄實例 FILEACT 傳送埠</span><span class="sxs-lookup"><span data-stu-id="85617-124">Step 3D: Add a FILEACT Send Port for the FileAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-store-and-forward-scenario.md)