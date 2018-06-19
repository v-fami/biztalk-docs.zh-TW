---
title: POP3 配接器效能計數器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f799175e-e9e7-4937-93bd-aaec1c43b75a
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c53bd0a487924a50155f388b6a657541ebe8fd3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971404"
---
# <a name="pop3-adapter-performance-counters"></a><span data-ttu-id="e628b-102">POP3 配接器效能計數器</span><span class="sxs-lookup"><span data-stu-id="e628b-102">POP3 Adapter Performance Counters</span></span>
<span data-ttu-id="e628b-103">效能計數器可讓您監視網站或系統上，服務所執行之工作的特定層面。</span><span class="sxs-lookup"><span data-stu-id="e628b-103">Performance counters allow you to monitor specific aspects of work performed on the site or system by service.</span></span> <span data-ttu-id="e628b-104">效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。</span><span class="sxs-lookup"><span data-stu-id="e628b-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span>  
  
 <span data-ttu-id="e628b-105">下列效能計數器會在每個主控件執行個體可存取**biztalk: Pop3 接收配接器**效能物件類別：</span><span class="sxs-lookup"><span data-stu-id="e628b-105">The following performance counters are accessible for each host instance under the **BizTalk:POP3 Receive Adapter** performance object category:</span></span>  
  
|<span data-ttu-id="e628b-106">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="e628b-106">**Category**</span></span>|<span data-ttu-id="e628b-107">**計數器**</span><span class="sxs-lookup"><span data-stu-id="e628b-107">**Counter**</span></span>|<span data-ttu-id="e628b-108">**說明**</span><span class="sxs-lookup"><span data-stu-id="e628b-108">**Description**</span></span>|  
|------------------|-----------------|---------------------|  
|<span data-ttu-id="e628b-109">BizTalk:POP3 接收配接器</span><span class="sxs-lookup"><span data-stu-id="e628b-109">BizTalk:POP3 Receive Adapter</span></span>|<span data-ttu-id="e628b-110">作用中的工作階段</span><span class="sxs-lookup"><span data-stu-id="e628b-110">Active sessions</span></span>|<span data-ttu-id="e628b-111">POP3 配接器一次管理的 POP3 開啟連線數。</span><span class="sxs-lookup"><span data-stu-id="e628b-111">Number of open POP3 connections the POP3 adapter is managing at a time.</span></span>|  
||<span data-ttu-id="e628b-112">接收位元組數</span><span class="sxs-lookup"><span data-stu-id="e628b-112">Bytes received</span></span>|<span data-ttu-id="e628b-113">POP3 配接器從郵件伺服器下載的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="e628b-113">Total number of bytes downloaded by the POP3 adapter from a mail server.</span></span>|  
||<span data-ttu-id="e628b-114">接收位元組數/秒</span><span class="sxs-lookup"><span data-stu-id="e628b-114">Bytes receive/Sec</span></span>|<span data-ttu-id="e628b-115">POP3 配接器每秒從郵件伺服器下載的位元組數。</span><span class="sxs-lookup"><span data-stu-id="e628b-115">Number of bytes downloaded by the POP3 adapter from a mail server per second.</span></span>|  
||<span data-ttu-id="e628b-116">接收訊息數</span><span class="sxs-lookup"><span data-stu-id="e628b-116">Messages received</span></span>|<span data-ttu-id="e628b-117">POP3 配接器從郵件伺服器下載的電子郵件訊息總數。</span><span class="sxs-lookup"><span data-stu-id="e628b-117">Total number of email messages downloaded by the POP3 adapter from a mail server.</span></span>|  
||<span data-ttu-id="e628b-118">接收訊息數/秒</span><span class="sxs-lookup"><span data-stu-id="e628b-118">Messages received/Sec</span></span>|<span data-ttu-id="e628b-119">POP3 配接器每秒從郵件伺服器下載的電子郵件訊息數。</span><span class="sxs-lookup"><span data-stu-id="e628b-119">Number of email messages downloaded by the POP3 adapter from mail server per second.</span></span>|  
  
## <a name="to-access-performance-counters"></a><span data-ttu-id="e628b-120">存取效能計數器</span><span class="sxs-lookup"><span data-stu-id="e628b-120">To access performance counters</span></span>  
 <span data-ttu-id="e628b-121">請遵照下列步驟來存取 POP3 配接器的效能計數器：</span><span class="sxs-lookup"><span data-stu-id="e628b-121">Follow these steps to access performance counters for the POP3 adapter:</span></span>  
  
#### <a name="if-you-are-using-windows-2008"></a><span data-ttu-id="e628b-122">若是使用 Windows 2008</span><span class="sxs-lookup"><span data-stu-id="e628b-122">If you are using Windows 2008</span></span>  
  
1.  <span data-ttu-id="e628b-123">按一下**啟動**，指向 **系統管理工具**，然後按一下 **效能監視器**。</span><span class="sxs-lookup"><span data-stu-id="e628b-123">Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.</span></span>  
  
2.  <span data-ttu-id="e628b-124">在**效能監視器**對話方塊方塊中，展開 **監視工具**，選取**效能監視器**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="e628b-124">In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="e628b-125">在**新增計數器**對話方塊中，從**可用的計數器**清單中，展開**biztalk: Pop3 接收配接器**效能計數器物件，然後選取要計數器監視</span><span class="sxs-lookup"><span data-stu-id="e628b-125">In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:POP3 Receive Adapter** performance counter object and select the counters to be monitored</span></span>  
  
4.  <span data-ttu-id="e628b-126">在**選取執行個體的物件**清單中，選取要監視針對所選取計數器，然後按一下 特定的執行個體**新增**。</span><span class="sxs-lookup"><span data-stu-id="e628b-126">In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.</span></span>  <span data-ttu-id="e628b-127">若要選取所有可用的計數器執行個體，請選取\<**所有執行個體**\>。</span><span class="sxs-lookup"><span data-stu-id="e628b-127">To select all available counter instances, select \<**All instances**\>.</span></span>  
  
5.  <span data-ttu-id="e628b-128">新增計數器後, 按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="e628b-128">After adding the counters, click **OK**.</span></span>  
  
     <span data-ttu-id="e628b-129">選取的效能計數器隨即出現在**效能監視器**螢幕。</span><span class="sxs-lookup"><span data-stu-id="e628b-129">The selected performance counters appear on the **Performance Monitor** screen.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e628b-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="e628b-130">See Also</span></span>  
 [<span data-ttu-id="e628b-131">監視 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e628b-131">Monitoring BizTalk Server</span></span>](../core/monitoring-biztalk-server.md)  
 <span data-ttu-id="e628b-132">[處理多部分訊息，POP3 配接器](../core/processing-multi-part-messages-with-the-pop3-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="e628b-132">[Processing Multi Part Messages with the POP3 Adapter](../core/processing-multi-part-messages-with-the-pop3-adapter.md) </span></span>  
 [<span data-ttu-id="e628b-133">在叢集主控件中執行配接器處理常式的考量</span><span class="sxs-lookup"><span data-stu-id="e628b-133">Considerations for Running Adapter Handlers within a Clustered Host</span></span>](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)