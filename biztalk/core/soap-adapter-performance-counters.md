---
title: "SOAP 配接器效能計數器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40b54d4e-0a2e-483f-982a-97ab9fb59202
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 870a3333ce638200c92125f08a4f048150584b51
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="soap-adapter-performance-counters"></a><span data-ttu-id="a21d4-102">SOAP 配接器效能計數器</span><span class="sxs-lookup"><span data-stu-id="a21d4-102">SOAP Adapter Performance Counters</span></span>
<span data-ttu-id="a21d4-103">效能計數器可讓您監視網站或系統上，服務所執行之工作的特定層面。</span><span class="sxs-lookup"><span data-stu-id="a21d4-103">Performance counters allow you to monitor specific aspects of work performed on the site or system by service.</span></span> <span data-ttu-id="a21d4-104">效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。</span><span class="sxs-lookup"><span data-stu-id="a21d4-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span>  
  
 <span data-ttu-id="a21d4-105">下列效能計數器會在每個主控件執行個體可存取**biztalk: Soap 接收配接器**和**biztalk: Soap 傳送配接器**效能物件類別：</span><span class="sxs-lookup"><span data-stu-id="a21d4-105">The following performance counters are accessible for each host instance under the **BizTalk:SOAP Receive Adapter** and the **BizTalk:SOAP Send Adapter** performance object categories:</span></span>  
  
|<span data-ttu-id="a21d4-106">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="a21d4-106">**Category**</span></span>|<span data-ttu-id="a21d4-107">**計數器**</span><span class="sxs-lookup"><span data-stu-id="a21d4-107">**Counter**</span></span>|<span data-ttu-id="a21d4-108">**說明**</span><span class="sxs-lookup"><span data-stu-id="a21d4-108">**Description**</span></span>|  
|------------------|-----------------|---------------------|  
|<span data-ttu-id="a21d4-109">BizTalk:SOAP 接收配接器</span><span class="sxs-lookup"><span data-stu-id="a21d4-109">BizTalk:SOAP Receive Adapter</span></span>|<span data-ttu-id="a21d4-110">接收訊息數</span><span class="sxs-lookup"><span data-stu-id="a21d4-110">Messages received</span></span>|<span data-ttu-id="a21d4-111">SOAP 接收配接器接收的訊息總數。</span><span class="sxs-lookup"><span data-stu-id="a21d4-111">Total number of messages received by the SOAP receive adapter.</span></span> <span data-ttu-id="a21d4-112">此計數器會在配接器從 SOAP 用戶端完整讀取要求訊息後遞增。</span><span class="sxs-lookup"><span data-stu-id="a21d4-112">The counter is incremented after a request message is completely read by the adapter from the SOAP client.</span></span>|  
||<span data-ttu-id="a21d4-113">接收訊息數/秒</span><span class="sxs-lookup"><span data-stu-id="a21d4-113">Messages received/Sec</span></span>|<span data-ttu-id="a21d4-114">SOAP 接收配接器每秒收到的訊息數。</span><span class="sxs-lookup"><span data-stu-id="a21d4-114">Number of messages received by the SOAP receive adapter per second.</span></span> <span data-ttu-id="a21d4-115">此計數器只適用於配接器從 SOAP 用戶端完整讀取的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="a21d4-115">The counter applies only to request messages that have been completely read by the adapter from the SOAP client.</span></span>|  
|<span data-ttu-id="a21d4-116">BizTalk:SOAP 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="a21d4-116">BizTalk:SOAP Send Adapter</span></span>|<span data-ttu-id="a21d4-117">Messages sent</span><span class="sxs-lookup"><span data-stu-id="a21d4-117">Messages sent</span></span>|<span data-ttu-id="a21d4-118">SOAP 傳送配接器傳送的訊息總數。</span><span class="sxs-lookup"><span data-stu-id="a21d4-118">Total number of messages sent by the SOAP send adapter.</span></span> <span data-ttu-id="a21d4-119">此計數器只會在訊息已到達目的地 URL 後遞增。</span><span class="sxs-lookup"><span data-stu-id="a21d4-119">The counter is incremented only for messages that have reached the destination URL.</span></span>|  
||<span data-ttu-id="a21d4-120">Messages sent/Sec</span><span class="sxs-lookup"><span data-stu-id="a21d4-120">Messages sent/Sec</span></span>|<span data-ttu-id="a21d4-121">SOAP 傳送配接器每秒傳送的訊息數。</span><span class="sxs-lookup"><span data-stu-id="a21d4-121">Number of messages sent by the SOAP send adapter per second.</span></span> <span data-ttu-id="a21d4-122">此計數器只適用於已到達目的地 URL 的訊息。</span><span class="sxs-lookup"><span data-stu-id="a21d4-122">The counter applies only to messages that have reached the destination URL.</span></span>|  
  
## <a name="to-access-performance-counters"></a><span data-ttu-id="a21d4-123">存取效能計數器</span><span class="sxs-lookup"><span data-stu-id="a21d4-123">To access performance counters</span></span>  
 <span data-ttu-id="a21d4-124">使用下列步驟來存取效能計數器。</span><span class="sxs-lookup"><span data-stu-id="a21d4-124">Use the following steps to access the performance counters.</span></span>  
  
#### <a name="if-you-are-using-windows-server-2008"></a><span data-ttu-id="a21d4-125">若是使用 Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="a21d4-125">If you are using Windows Server 2008</span></span>  
  
1.  <span data-ttu-id="a21d4-126">按一下**啟動**，指向 **系統管理工具**，然後按一下 **效能監視器**。</span><span class="sxs-lookup"><span data-stu-id="a21d4-126">Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.</span></span>  
  
2.  <span data-ttu-id="a21d4-127">在**效能監視器**對話方塊方塊中，展開 **監視工具**，選取**效能監視器**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="a21d4-127">In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="a21d4-128">在**新增計數器**對話方塊中，從**可用的計數器**清單中，展開**biztalk: Soap**效能計數器物件，然後選取要監視的計數器</span><span class="sxs-lookup"><span data-stu-id="a21d4-128">In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:SOAP** performance counter object and select the counters to be monitored</span></span>  
  
4.  <span data-ttu-id="a21d4-129">在**選取執行個體的物件**清單中，選取要監視針對所選取計數器，然後按一下 特定的執行個體**新增**。</span><span class="sxs-lookup"><span data-stu-id="a21d4-129">In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.</span></span> <span data-ttu-id="a21d4-130">若要選取所有可用的計數器執行個體，請選取\<**所有執行個體**>。</span><span class="sxs-lookup"><span data-stu-id="a21d4-130">To select all available counter instances, select \<**All instances**>.</span></span>  
  
5.  <span data-ttu-id="a21d4-131">新增計數器後, 按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="a21d4-131">After adding the counters, click **OK**.</span></span>  
  
     <span data-ttu-id="a21d4-132">選取的效能計數器隨即出現在**效能監視器**螢幕。</span><span class="sxs-lookup"><span data-stu-id="a21d4-132">The selected performance counters appear on the **Performance Monitor** screen.</span></span>