---
title: 步驟 3c： 新增 FILE 傳送埠，以取得 Sw:HandleRequest-互動存放與轉寄 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c872b4be-ef8b-4e42-b5ef-63dfd120793f
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b82c57f2f3a6e2fcfc199e56d34c44aa7667451d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225574"
---
# <a name="step-3c-add-file-send-port-to-get-swhandlerequest-interact-store-and-forward"></a><span data-ttu-id="ec30c-102">步驟 3c： 新增 FILE 傳送埠，以取得 Sw:HandleRequest-互動儲存與轉送</span><span class="sxs-lookup"><span data-stu-id="ec30c-102">Step 3C: Add FILE send port to get Sw:HandleRequest-InterAct Store and Forward</span></span>
<span data-ttu-id="ec30c-103">在開始此步驟之前，必須先完成[步驟 3B： 新增的互動接收位置為互動存放與轉寄實例](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="ec30c-103">Before you begin this step, you must complete [Step 3B: Add an INTERACT Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md).</span></span>  
  
### <a name="to-add-a-file-send-port-to-capture-the-swhandlerequest-message"></a><span data-ttu-id="ec30c-104">若要加入檔案傳送埠以擷取 Sw:HandleRequest 訊息</span><span class="sxs-lookup"><span data-stu-id="ec30c-104">To add a FILE send port to capture the Sw:HandleRequest message</span></span>  
  
1.  <span data-ttu-id="ec30c-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="ec30c-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="ec30c-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ec30c-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="ec30c-107">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠。**</span><span class="sxs-lookup"><span data-stu-id="ec30c-107">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**</span></span>  
  
4.  <span data-ttu-id="ec30c-108">在**傳送埠屬性**視窗中，傳送埠，Tutorial_IA_SendResponseToReceiver。</span><span class="sxs-lookup"><span data-stu-id="ec30c-108">In the **Send Port Properties** window, name the send port, Tutorial_IA_SendResponseToReceiver.</span></span>  
  
5.  <span data-ttu-id="ec30c-109">在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**檔案**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="ec30c-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="ec30c-110">中**FILE 傳輸屬性**對話方塊中，於**目的地資料夾**方塊、 輸入 C:\SWIFTAdapterTutorial\Interact\HandleRequest，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ec30c-110">In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type C:\SWIFTAdapterTutorial\Interact\HandleRequest, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="ec30c-111">在**傳送埠屬性**視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ec30c-111">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="ec30c-112">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="ec30c-112">**Use this**</span></span>|<span data-ttu-id="ec30c-113">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="ec30c-113">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="ec30c-114">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="ec30c-114">**Send handler**</span></span>|<span data-ttu-id="ec30c-115">從下拉式清單選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="ec30c-115">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="ec30c-116">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="ec30c-116">**Send pipeline**</span></span>|<span data-ttu-id="ec30c-117">從下拉式清單選取**XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="ec30c-117">From the drop-down list, select **XMLTransmit**.</span></span>|  
  
8.  <span data-ttu-id="ec30c-118">在**傳送埠屬性**視窗，請在**篩選**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ec30c-118">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="ec30c-119">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="ec30c-119">**Use this**</span></span>|<span data-ttu-id="ec30c-120">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="ec30c-120">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="ec30c-121">**屬性**</span><span class="sxs-lookup"><span data-stu-id="ec30c-121">**Property**</span></span>|<span data-ttu-id="ec30c-122">從下拉式清單選取**BTS。ReceivePortName**。</span><span class="sxs-lookup"><span data-stu-id="ec30c-122">From the drop-down list, select **BTS.ReceivePortName**.</span></span>|  
    |<span data-ttu-id="ec30c-123">**運算子**</span><span class="sxs-lookup"><span data-stu-id="ec30c-123">**Operator**</span></span>|<span data-ttu-id="ec30c-124">從下拉式清單選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="ec30c-124">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="ec30c-125">**值**</span><span class="sxs-lookup"><span data-stu-id="ec30c-125">**Value**</span></span>|<span data-ttu-id="ec30c-126">型別**Tutorial_IA_InputRequest_SnF**。</span><span class="sxs-lookup"><span data-stu-id="ec30c-126">Type **Tutorial_IA_InputRequest_SnF**.</span></span>|  
    |<span data-ttu-id="ec30c-127">**群組依據**</span><span class="sxs-lookup"><span data-stu-id="ec30c-127">**Group by**</span></span>|<span data-ttu-id="ec30c-128">保留預設值。</span><span class="sxs-lookup"><span data-stu-id="ec30c-128">Leave the default value.</span></span>|  
  
9. <span data-ttu-id="ec30c-129">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="ec30c-129">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec30c-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec30c-130">See Also</span></span>  
 <span data-ttu-id="ec30c-131">[步驟 3： 建立傳送埠和接收埠以進行互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ec30c-131">[Step 3: Create Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="ec30c-132">[步驟 3A： 新增 FILE 接收位置為互動存放區與正向的實例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ec30c-132">[Step 3A: Add a FILE Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="ec30c-133">[步驟 3B： 加入互動接收位置的互動存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ec30c-133">[Step 3B: Add an INTERACT Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="ec30c-134">步驟 3D: 互動存放區和轉寄的案例中加入互動的傳送埠</span><span class="sxs-lookup"><span data-stu-id="ec30c-134">Step 3D: Add an INTERACT Send Port for the InterAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3d-add-an-interact-send-port-for-the-interact-store-and-forward-scenario.md)