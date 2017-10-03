---
title: "建立 FRR 用於接收來自 SWIFT 接收位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, creating
- creating, receive locations
- FRR, creating receive locations
ms.assetid: e10857f4-21cb-4c09-8eed-cb6e9b0a0aa9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e43ac2ac0fab9b2a29a44784032f9d3369833ae2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-the-frr-receive-location-for-receiving-from-swift"></a><span data-ttu-id="08483-102">建立 FRR 用於接收來自 SWIFT 接收位置</span><span class="sxs-lookup"><span data-stu-id="08483-102">Creating the FRR Receive Location for Receiving from SWIFT</span></span>
<span data-ttu-id="08483-103">若要執行 FIN 回應重新調整，您需要建立成 A4SWIFT SWIFT 網路接收的訊息的接收位置。</span><span class="sxs-lookup"><span data-stu-id="08483-103">To perform FIN Response Reconciliation, you need to create a receive location that receives a message from the SWIFT Network into A4SWIFT.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08483-104">建議您設定兩個接收位置接收訊息從 SAA： 一個用於接收取景位置調整/Nan，另一個收到的其他所有訊息。</span><span class="sxs-lookup"><span data-stu-id="08483-104">It is advisable to set up two receive locations for receiving messages from SAA: one to receive PAN/NANs and one to receive all other messages.</span></span> <span data-ttu-id="08483-105">若要設定兩個接收位置，您必須從 SAA 在兩個 MQSeries 佇列接收訊息： 一個用於取景位置調整/Nan，一個用於所有其他訊息類型。</span><span class="sxs-lookup"><span data-stu-id="08483-105">To set up the two receive locations, you must receive messages from two MQSeries queues at SAA: one for PAN/NANs and one for all other message types.</span></span>  
  
 <span data-ttu-id="08483-106">**摘要**</span><span class="sxs-lookup"><span data-stu-id="08483-106">**Summary**</span></span>  
  
 <span data-ttu-id="08483-107">建立具有下列屬性和元件的接收位置：</span><span class="sxs-lookup"><span data-stu-id="08483-107">Create a receive location with the following properties and components:</span></span>  
  
|<span data-ttu-id="08483-108">屬性/元件</span><span class="sxs-lookup"><span data-stu-id="08483-108">Property/Component</span></span>|<span data-ttu-id="08483-109">設定</span><span class="sxs-lookup"><span data-stu-id="08483-109">Setting</span></span>|  
|-------------------------|-------------|  
|<span data-ttu-id="08483-110">接收埠</span><span class="sxs-lookup"><span data-stu-id="08483-110">Receive port</span></span>|<span data-ttu-id="08483-111">單向連接埠</span><span class="sxs-lookup"><span data-stu-id="08483-111">One-way port</span></span>|  
|<span data-ttu-id="08483-112">傳輸類型</span><span class="sxs-lookup"><span data-stu-id="08483-112">Transport type</span></span>|<span data-ttu-id="08483-113">MQSeries</span><span class="sxs-lookup"><span data-stu-id="08483-113">MQSeries</span></span>|  
|<span data-ttu-id="08483-114">佇列定義 (MQSeries)</span><span class="sxs-lookup"><span data-stu-id="08483-114">Queue Definition (MQSeries)</span></span>|<span data-ttu-id="08483-115">MQSeries server</span><span class="sxs-lookup"><span data-stu-id="08483-115">MQSeries server</span></span><br /><span data-ttu-id="08483-116">佇列管理員</span><span class="sxs-lookup"><span data-stu-id="08483-116">Queue manager</span></span><br /><span data-ttu-id="08483-117">佇列</span><span class="sxs-lookup"><span data-stu-id="08483-117">Queue</span></span>|  
|<span data-ttu-id="08483-118">接收處理常式</span><span class="sxs-lookup"><span data-stu-id="08483-118">Receive handler</span></span>|<span data-ttu-id="08483-119">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="08483-119">BizTalkServerApplication</span></span>|  
|<span data-ttu-id="08483-120">接收管線</span><span class="sxs-lookup"><span data-stu-id="08483-120">Receive pipeline</span></span>|<span data-ttu-id="08483-121">A4SWIFT 接收管線所建立的 FRR</span><span class="sxs-lookup"><span data-stu-id="08483-121">The A4SWIFT receive pipeline that you created for FRR</span></span>|  
  
### <a name="to-add-an-frr-receive-location-for-receiving-from-swift"></a><span data-ttu-id="08483-122">新增 FRR 接收位置接收來自 SWIFT</span><span class="sxs-lookup"><span data-stu-id="08483-122">To add an FRR receive location for receiving from SWIFT</span></span>  
  
1.  <span data-ttu-id="08483-123">在 BizTalk Server 管理主控台中，展開**BizTalk Server 管理**， **BizTalk 群組**，**應用程式**，和**BizTalk 應用程式1**節點。</span><span class="sxs-lookup"><span data-stu-id="08483-123">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and  **BizTalk Application 1** nodes.</span></span>  
  
2.  <span data-ttu-id="08483-124">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="08483-124">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
3.  <span data-ttu-id="08483-125">在 [接收埠屬性] 對話方塊中**名稱**方塊中，輸入接收埠，例如 FRRSWIFTReceivePort 的名稱。</span><span class="sxs-lookup"><span data-stu-id="08483-125">In the Receive Port Properties dialog box, in the **Name** box, type a name for the receive port, such as FRRSWIFTReceivePort.</span></span>  
  
4.  <span data-ttu-id="08483-126">按一下**套用**來繫結連接埠，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="08483-126">Click **Apply** to bind the port, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="08483-127">在管理主控台中，以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下 **單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="08483-127">In the Administration Console, right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
6.  <span data-ttu-id="08483-128">在 [選取接收埠] 對話方塊中，選取您剛才的接收埠建立，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="08483-128">In the Select a Receive Port dialog box, select the receive port that you just created, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="08483-129">在 [接收位置屬性] 對話方塊中**名稱**方塊中，輸入接收位置，例如 FRRSWIFTReceiveLocation 的名稱。</span><span class="sxs-lookup"><span data-stu-id="08483-129">In the Receive Location Properties dialog box, in the **Name** box, type a name for the receive location, such as FRRSWIFTReceiveLocation.</span></span>  
  
8.  <span data-ttu-id="08483-130">在**傳輸** 區段中，針對**類型**文字方塊中，選取**MQSeries**。</span><span class="sxs-lookup"><span data-stu-id="08483-130">In the **Transport** section, for the **Type** text box, select **MQSeries**.</span></span>  
  
9. <span data-ttu-id="08483-131">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="08483-131">Click **Configure**.</span></span>  
  
10. <span data-ttu-id="08483-132">在 [MQSeries 傳輸屬性] 對話方塊中，按一下**佇列定義**，然後按一下省略符號 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="08483-132">In the MQSeries Transport Properties dialog box, click **Queue Definition**, and then click the ellipsis (**…**) button.</span></span>  
  
11. <span data-ttu-id="08483-133">在**佇列定義**對話方塊中，輸入 MQSeries server 佇列管理員，並加入佇列。</span><span class="sxs-lookup"><span data-stu-id="08483-133">In the **Queue Definition** dialog box, enter the MQSeries server, queue manager, and queue.</span></span> <span data-ttu-id="08483-134">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="08483-134">Click **OK**.</span></span>  
  
12. <span data-ttu-id="08483-135">在**MQSeries 傳輸屬性**對話方塊方塊中，確認內容會視需要。</span><span class="sxs-lookup"><span data-stu-id="08483-135">In the **MQSeries Transport Properties** dialog box, verify that the properties are as needed.</span></span> <span data-ttu-id="08483-136">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="08483-136">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="08483-137">如需 MQSeries 傳輸屬性的詳細資訊，請參閱 MQSeries 文件。</span><span class="sxs-lookup"><span data-stu-id="08483-137">For more information about MQSeries transport properties, see the MQSeries documentation.</span></span>  
  
13. <span data-ttu-id="08483-138">在 [接收位置屬性] 對話方塊的**接收處理常式**，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="08483-138">In the Receive Location Properties dialog box, for **Receive Handler**, select **BizTalkServerApplication**.</span></span>  
  
14. <span data-ttu-id="08483-139">如**接收管線** 區段中，選取 A4SWIFT 接收管線 FRR 所建立。</span><span class="sxs-lookup"><span data-stu-id="08483-139">For **Receive Pipeline** section, select the A4SWIFT receive pipeline that you created for FRR.</span></span>  
  
15. <span data-ttu-id="08483-140">按一下**套用**，然後按一下  **確定**</span><span class="sxs-lookup"><span data-stu-id="08483-140">Click **Apply**, and then click **OK**</span></span>  
  
16. <span data-ttu-id="08483-141">在 [BizTalk 總管] 中，以滑鼠右鍵按一下您剛才的接收位置建立，，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="08483-141">In BizTalk Explorer, right-click the receive location that you just created, and then click **Enable**.</span></span>