---
title: 步驟 1： 設定檔案接收位置 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: df591263-964a-4ad8-bc3a-a553de8dae4f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78f8bccc187bf310b8426fc3d5fee36add44a9f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278254"
---
# <a name="step-1-configure-a-file-receive-location"></a><span data-ttu-id="0ea4c-102">步驟 1： 設定檔案接收位置</span><span class="sxs-lookup"><span data-stu-id="0ea4c-102">Step 1: Configure a FILE Receive Location</span></span>
<span data-ttu-id="0ea4c-103">本主題中，您可以設定讓檔案接收位置使用拖放到檔案資料夾，即可叫用傳送埠的虛擬要求訊息。</span><span class="sxs-lookup"><span data-stu-id="0ea4c-103">In this topic, you configure a FILE receive location that consumes the dummy request message that you drop to a file folder to invoke the send port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ea4c-104">在本教學課程的步驟假設您使用預設的應用程式 (**BizTalk Application 1**) 若要建立方案。</span><span class="sxs-lookup"><span data-stu-id="0ea4c-104">The steps in this tutorial assume that you use the default application (**BizTalk Application 1**) to create the solution.</span></span> <span data-ttu-id="0ea4c-105">您也可以建立另一個應用程式，並在任何該應用程式執行相同的步驟。</span><span class="sxs-lookup"><span data-stu-id="0ea4c-105">You can also create another application and perform the same steps in any that application.</span></span>  
  
### <a name="to-configure-a-file-receive-location"></a><span data-ttu-id="0ea4c-106">若要設定 FILE 接收位置</span><span class="sxs-lookup"><span data-stu-id="0ea4c-106">To configure a FILE receive location</span></span>  
  
1.  <span data-ttu-id="0ea4c-107">從 BizTalk Server 管理主控台，在**BizTalk Application 1** ] 節點，以滑鼠右鍵按一下**接收埠**，指向**新增**，然後按一下 [ **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="0ea4c-107">From BizTalk Server Administration Console, under the **BizTalk Application 1** node, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
2.  <span data-ttu-id="0ea4c-108">在 [一般] 索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0ea4c-108">On the General tab, do the following:</span></span>  
  
    |<span data-ttu-id="0ea4c-109">使用</span><span class="sxs-lookup"><span data-stu-id="0ea4c-109">Use this</span></span>|<span data-ttu-id="0ea4c-110">動作</span><span class="sxs-lookup"><span data-stu-id="0ea4c-110">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="0ea4c-111">**名稱**</span><span class="sxs-lookup"><span data-stu-id="0ea4c-111">**Name**</span></span>|<span data-ttu-id="0ea4c-112">型別**ReceivePortRestAzureMarketPlace**。</span><span class="sxs-lookup"><span data-stu-id="0ea4c-112">Type **ReceivePortRestAzureMarketPlace**.</span></span>|  
    |<span data-ttu-id="0ea4c-113">**啟用失敗訊息的路由**</span><span class="sxs-lookup"><span data-stu-id="0ea4c-113">**Enable routing for failed messages**</span></span>|<span data-ttu-id="0ea4c-114">(清除)</span><span class="sxs-lookup"><span data-stu-id="0ea4c-114">(clear)</span></span>|  
  
3.  <span data-ttu-id="0ea4c-115">按一下**接收位置**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="0ea4c-115">Click **Receive Locations**, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="0ea4c-116">從 [Receive Location1 - 接收位置屬性] 中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0ea4c-116">From Receive Location1 – Receive Location Properties, do the following:</span></span>  
  
    |<span data-ttu-id="0ea4c-117">使用</span><span class="sxs-lookup"><span data-stu-id="0ea4c-117">Use this</span></span>|<span data-ttu-id="0ea4c-118">動作</span><span class="sxs-lookup"><span data-stu-id="0ea4c-118">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="0ea4c-119">**名稱**</span><span class="sxs-lookup"><span data-stu-id="0ea4c-119">**Name**</span></span>|<span data-ttu-id="0ea4c-120">型別**ReceiveLocationAzureMarketPlace**。</span><span class="sxs-lookup"><span data-stu-id="0ea4c-120">Type **ReceiveLocationAzureMarketPlace**.</span></span>|  
    |<span data-ttu-id="0ea4c-121">**型別**</span><span class="sxs-lookup"><span data-stu-id="0ea4c-121">**Type**</span></span>|<span data-ttu-id="0ea4c-122">選取**檔案**。</span><span class="sxs-lookup"><span data-stu-id="0ea4c-122">Select **FILE**.</span></span>|  
    |<span data-ttu-id="0ea4c-123">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="0ea4c-123">**Receive handler**</span></span>|<span data-ttu-id="0ea4c-124">選取 **[BizTalkServerApplication]**。</span><span class="sxs-lookup"><span data-stu-id="0ea4c-124">Select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="0ea4c-125">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="0ea4c-125">**Receive pipeline**</span></span>|<span data-ttu-id="0ea4c-126">選取**PassThruReceive**。</span><span class="sxs-lookup"><span data-stu-id="0ea4c-126">Select **PassThruReceive**.</span></span>|  
  
5.  <span data-ttu-id="0ea4c-127">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="0ea4c-127">Click **Configure**.</span></span>  
  
6.  <span data-ttu-id="0ea4c-128">從 [檔案傳輸屬性] 中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0ea4c-128">From File Transport Properties, do the following:</span></span>  
  
    |<span data-ttu-id="0ea4c-129">使用</span><span class="sxs-lookup"><span data-stu-id="0ea4c-129">Use this</span></span>|<span data-ttu-id="0ea4c-130">動作</span><span class="sxs-lookup"><span data-stu-id="0ea4c-130">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="0ea4c-131">**接收資料夾**</span><span class="sxs-lookup"><span data-stu-id="0ea4c-131">**Receive folder**</span></span>|<span data-ttu-id="0ea4c-132">輸入您將放置虛擬要求訊息的位置。</span><span class="sxs-lookup"><span data-stu-id="0ea4c-132">Type a location where you will drop the dummy request message.</span></span>|  
    |<span data-ttu-id="0ea4c-133">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="0ea4c-133">**File name**</span></span>|<span data-ttu-id="0ea4c-134">保留`*.xml`</span><span class="sxs-lookup"><span data-stu-id="0ea4c-134">Retain `*.xml`</span></span>|  
  
7.  <span data-ttu-id="0ea4c-135">按一下**確定**直到結束所有對話方塊為止。</span><span class="sxs-lookup"><span data-stu-id="0ea4c-135">Click **OK** until you exit all the dialog boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ea4c-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ea4c-136">See Also</span></span>  
 [<span data-ttu-id="0ea4c-137">教學課程 5： 叫用 REST 介面使用 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="0ea4c-137">Tutorial 5: Invoking a REST Interface Using BizTalk Server</span></span>](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)