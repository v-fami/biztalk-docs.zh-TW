---
title: FTP 配接器效能計數器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ca5cbe67-9aa3-4194-816e-fab4eb551c07
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5dad67f24f37f661e26f4cb56895c6bcad6b0782
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969436"
---
# <a name="ftp-adapter-performance-counters"></a><span data-ttu-id="cf4f5-102">FTP 配接器效能計數器</span><span class="sxs-lookup"><span data-stu-id="cf4f5-102">FTP Adapter Performance Counters</span></span>
<span data-ttu-id="cf4f5-103">效能計數器可讓您監視網站或系統上，服務所執行之工作的特定層面。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-103">Performance counters allow you to monitor specific aspects of work performed on the site or system by service.</span></span> <span data-ttu-id="cf4f5-104">效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span>  
  
 <span data-ttu-id="cf4f5-105">下列效能計數器會在每個主控件執行個體可存取**biztalk: Ftp 接收配接器**和**biztalk: Ftp 傳送配接器**效能物件類別：</span><span class="sxs-lookup"><span data-stu-id="cf4f5-105">The following performance counters are accessible for each host instance under the **BizTalk:FTP Receive Adapter** and the **BizTalk:FTP Send Adapter** performance object categories:</span></span>  
  
|<span data-ttu-id="cf4f5-106">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="cf4f5-106">**Category**</span></span>|<span data-ttu-id="cf4f5-107">**計數器**</span><span class="sxs-lookup"><span data-stu-id="cf4f5-107">**Counter**</span></span>|<span data-ttu-id="cf4f5-108">**說明**</span><span class="sxs-lookup"><span data-stu-id="cf4f5-108">**Description**</span></span>|  
|------------------|-----------------|---------------------|  
|<span data-ttu-id="cf4f5-109">BizTalk:FTP 接收配接器</span><span class="sxs-lookup"><span data-stu-id="cf4f5-109">BizTalk:FTP Receive Adapter</span></span>|<span data-ttu-id="cf4f5-110">接收位元組數</span><span class="sxs-lookup"><span data-stu-id="cf4f5-110">Bytes received</span></span>|<span data-ttu-id="cf4f5-111">FTP 接收配接器接收的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-111">Total number of bytes received by the FTP receive adapter.</span></span> <span data-ttu-id="cf4f5-112">此計數器會在 FTP 接收配接器從 FTP 伺服器完整讀取訊息後遞增。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-112">The counter is incremented after a message is completely read by the FTP receive adapter from the FTP server.</span></span>|  
||<span data-ttu-id="cf4f5-113">接收位元組數/秒</span><span class="sxs-lookup"><span data-stu-id="cf4f5-113">Bytes received/Sec</span></span>|<span data-ttu-id="cf4f5-114">FTP 接收配接器每秒收到的位元組數。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-114">Number of bytes received by the FTP receive adapter per second.</span></span> <span data-ttu-id="cf4f5-115">此計數器只適用於 FTP 接收配接器從 FTP 伺服器完整讀取的訊息。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-115">The counter applies only to messages that have been completely read by the FTP receive adapter from the FTP server.</span></span>|  
||<span data-ttu-id="cf4f5-116">接收訊息數</span><span class="sxs-lookup"><span data-stu-id="cf4f5-116">Messages received</span></span>|<span data-ttu-id="cf4f5-117">FTP 接收配接器接收的訊息總數。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-117">Total number of messages received by the FTP receive adapter.</span></span> <span data-ttu-id="cf4f5-118">此計數器會在 FTP 接收配接器從 FTP 伺服器完整讀取訊息後遞增。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-118">The counter is incremented after a message is completely read by the FTP receive adapter from the FTP server.</span></span>|  
||<span data-ttu-id="cf4f5-119">接收訊息數/秒</span><span class="sxs-lookup"><span data-stu-id="cf4f5-119">Messages received/Sec</span></span>|<span data-ttu-id="cf4f5-120">FTP 接收配接器每秒收到的訊息數。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-120">Number of messages received by the FTP receive adapter per second.</span></span> <span data-ttu-id="cf4f5-121">此計數器只適用於 FTP 接收配接器從 FTP 伺服器完整讀取的訊息。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-121">The counter applies only to messages that have been completely read by the FTP receive adapter from the FTP server.</span></span>|  
|<span data-ttu-id="cf4f5-122">BizTalk:FTP 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="cf4f5-122">BizTalk:FTP Send Adapter</span></span>|<span data-ttu-id="cf4f5-123">傳送位元組數</span><span class="sxs-lookup"><span data-stu-id="cf4f5-123">Bytes sent</span></span>|<span data-ttu-id="cf4f5-124">FTP 傳送配接器傳送的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-124">Total number of bytes sent by the FTP send adapter.</span></span> <span data-ttu-id="cf4f5-125">此計數器只會在訊息已寫入目的地 FTP 伺服器後遞增。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-125">The counter is incremented only for messages that have been written to the destination FTP server.</span></span>|  
||<span data-ttu-id="cf4f5-126">傳送位元組數/秒</span><span class="sxs-lookup"><span data-stu-id="cf4f5-126">Bytes sent/Sec</span></span>|<span data-ttu-id="cf4f5-127">FTP 傳送配接器每秒傳送的位元組數。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-127">Number of bytes sent by the FTP send adapter per second.</span></span> <span data-ttu-id="cf4f5-128">此計數器只適用於已寫入目的地 FTP 伺服器的訊息。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-128">The counter applies only to messages that have been written to the destination FTP server.</span></span>|  
||<span data-ttu-id="cf4f5-129">Messages sent</span><span class="sxs-lookup"><span data-stu-id="cf4f5-129">Messages sent</span></span>|<span data-ttu-id="cf4f5-130">FTP 傳送配接器傳送的訊息總數。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-130">Total number of messages sent by the FTP send adapter.</span></span> <span data-ttu-id="cf4f5-131">此計數器只會在訊息已寫入目的地 FTP 伺服器後遞增。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-131">The counter is incremented only for messages that have been written to the destination FTP server.</span></span>|  
||<span data-ttu-id="cf4f5-132">Messages sent/Sec</span><span class="sxs-lookup"><span data-stu-id="cf4f5-132">Messages sent/Sec</span></span>|<span data-ttu-id="cf4f5-133">FTP 傳送配接器每秒傳送的訊息數。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-133">Number of messages sent by the FTP send adapter per second.</span></span> <span data-ttu-id="cf4f5-134">此計數器只適用於已寫入目的地 FTP 伺服器的訊息。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-134">The counter applies only to messages that have been written to destination FTP server.</span></span>|  
  
## <a name="to-access-performance-counters"></a><span data-ttu-id="cf4f5-135">存取效能計數器</span><span class="sxs-lookup"><span data-stu-id="cf4f5-135">To access performance counters</span></span>  
 <span data-ttu-id="cf4f5-136">使用下列步驟來存取效能計數器。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-136">Use the following steps to access the performance counters.</span></span>  
  
#### <a name="if-you-are-using-windows-2008"></a><span data-ttu-id="cf4f5-137">若是使用 Windows 2008</span><span class="sxs-lookup"><span data-stu-id="cf4f5-137">If you are using Windows 2008</span></span>  
  
1.  <span data-ttu-id="cf4f5-138">按一下**啟動**，指向 **系統管理工具**，然後按一下 **效能監視器**。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-138">Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.</span></span>  
  
2.  <span data-ttu-id="cf4f5-139">在**效能監視器**對話方塊方塊中，展開 **監視工具**，選取**效能監視器**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-139">In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="cf4f5-140">在**新增計數器**對話方塊中，從**可用的計數器**清單中，展開**biztalk: Ftp**效能計數器物件，然後選取要監視的計數器</span><span class="sxs-lookup"><span data-stu-id="cf4f5-140">In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:FTP** performance counter object and select the counters to be monitored</span></span>  
  
4.  <span data-ttu-id="cf4f5-141">在**選取執行個體的物件**清單中，選取要監視針對所選取計數器，然後按一下 特定的執行個體**新增**。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-141">In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.</span></span>  <span data-ttu-id="cf4f5-142">若要選取所有可用的計數器執行個體，請選取\<**所有執行個體**\>。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-142">To select all available counter instances, select \<**All instances**\>.</span></span>  
  
5.  <span data-ttu-id="cf4f5-143">新增計數器後, 按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-143">After adding the counters, click **OK**.</span></span>  
  
     <span data-ttu-id="cf4f5-144">選取的效能計數器隨即出現在**效能監視器**螢幕。</span><span class="sxs-lookup"><span data-stu-id="cf4f5-144">The selected performance counters appear on the **Performance Monitor** screen.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf4f5-145">請參閱</span><span class="sxs-lookup"><span data-stu-id="cf4f5-145">See Also</span></span>  
 <span data-ttu-id="cf4f5-146">[監控 BizTalk Server](../core/monitoring-biztalk-server.md) [執行叢集主控件中的配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)</span><span class="sxs-lookup"><span data-stu-id="cf4f5-146">[Monitoring BizTalk Server](../core/monitoring-biztalk-server.md) [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)</span></span>