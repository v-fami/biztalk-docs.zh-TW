---
title: 步驟 3A： 新增 FILE 接收位置為互動存放區與正向實例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5f4bae51-6869-4334-a3a1-ef7e662197ca
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d2027878771249ceb2dcb45683a71b4475a75cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224174"
---
# <a name="step-3a-add-a-file-receive-location-for-the-interact-store-and-forward-scenario"></a><span data-ttu-id="7d08f-102">步驟 3A： 新增 FILE 接收位置為互動存放區與正向的實例</span><span class="sxs-lookup"><span data-stu-id="7d08f-102">Step 3A: Add a FILE Receive Location for the InterAct Store and Forward Scenario</span></span>
<span data-ttu-id="7d08f-103">完成[步驟 2： 新增 SWIFTNet 組態為互動存放與轉寄實例 Paramfile](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-store-and-forward.md)開始此步驟之前。</span><span class="sxs-lookup"><span data-stu-id="7d08f-103">Complete [Step 2: Add SWIFTNet Configuration to the Paramfile for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-store-and-forward.md) before you begin this step.</span></span>
  
## <a name="add-a-file-receive-location"></a><span data-ttu-id="7d08f-104">新增 FILE 接收位置</span><span class="sxs-lookup"><span data-stu-id="7d08f-104">Add a FILE receive location</span></span>  
  
1.  <span data-ttu-id="7d08f-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="7d08f-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="7d08f-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立接收埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7d08f-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a receive port.</span></span>  
  
3.  <span data-ttu-id="7d08f-107">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠。**</span><span class="sxs-lookup"><span data-stu-id="7d08f-107">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
4.  <span data-ttu-id="7d08f-108">在**接收埠屬性**視窗中，接收埠，Tutorial_IA_InputRequest_SnF。</span><span class="sxs-lookup"><span data-stu-id="7d08f-108">In the **Receive Port Properties** window, name the receive port, Tutorial_IA_InputRequest_SnF.</span></span>  
  
5.  <span data-ttu-id="7d08f-109">在**接收埠屬性**視窗，請在**接收位置**索引標籤上，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="7d08f-109">In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.</span></span>  
  
6.  <span data-ttu-id="7d08f-110">在**接收位置屬性**視窗，請在**一般**索引標籤上，從**傳輸類型**下拉式清單中，選取**檔案**，和然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="7d08f-110">In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="7d08f-111">在**FILE 傳輸屬性**對話方塊中，輸入 C:\SWIFTAdapterTutorial\Interact\InputRequest_SnF，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="7d08f-111">In the **FILE Transport Properties** dialog box, type C:\SWIFTAdapterTutorial\Interact\InputRequest_SnF, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="7d08f-112">在**接收位置屬性**視窗，請在**一般**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="7d08f-112">In the **Receive Location Properties** window, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="7d08f-113">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="7d08f-113">**Use this**</span></span>|<span data-ttu-id="7d08f-114">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="7d08f-114">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="7d08f-115">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="7d08f-115">**Receive handler**</span></span>|<span data-ttu-id="7d08f-116">從下拉式清單選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="7d08f-116">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="7d08f-117">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="7d08f-117">**Receive pipeline**</span></span>|<span data-ttu-id="7d08f-118">從下拉式清單選取**XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="7d08f-118">From the drop-down list, select **XMLReceive**.</span></span>|  
  
9. <span data-ttu-id="7d08f-119">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="7d08f-119">Click **OK**.</span></span>  
  
## <a name="complete-steps"></a><span data-ttu-id="7d08f-120">完成步驟</span><span class="sxs-lookup"><span data-stu-id="7d08f-120">Complete steps</span></span>
 <span data-ttu-id="7d08f-121">[步驟 3： 建立傳送埠和接收埠以進行互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="7d08f-121">[Step 3: Create Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="7d08f-122">[步驟 3B： 加入互動接收位置的互動存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="7d08f-122">[Step 3B: Add an INTERACT Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="7d08f-123">步驟 3c： 新增檔案傳送埠，以便擷取 Sw:HandleRequest 訊息互動存放區和轉寄的案例</span><span class="sxs-lookup"><span data-stu-id="7d08f-123">Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-store-and-forward.md)  
 [<span data-ttu-id="7d08f-124">步驟 3D: 互動存放區和轉寄的案例中加入互動的傳送埠</span><span class="sxs-lookup"><span data-stu-id="7d08f-124">Step 3D: Add an INTERACT Send Port for the InterAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3d-add-an-interact-send-port-for-the-interact-store-and-forward-scenario.md)