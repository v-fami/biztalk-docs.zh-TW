---
title: SMTP 配接器效能計數器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c7aa7dd-1674-4bbb-b22f-92204d55c4b8
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3503b5a37a7b2ab48be2478879cc61187895029
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973388"
---
# <a name="smtp-adapter-performance-counters"></a><span data-ttu-id="5707a-102">SMTP 配接器效能計數器</span><span class="sxs-lookup"><span data-stu-id="5707a-102">SMTP Adapter Performance Counters</span></span>
<span data-ttu-id="5707a-103">效能計數器可讓您監視網站或系統上，服務所執行之工作的特定層面。</span><span class="sxs-lookup"><span data-stu-id="5707a-103">Performance counters allow you to monitor specific aspects of work performed on the site or system by service.</span></span> <span data-ttu-id="5707a-104">效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。</span><span class="sxs-lookup"><span data-stu-id="5707a-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span>  
  
 <span data-ttu-id="5707a-105">下列效能計數器會在每個主控件執行個體可存取**biztalk: Smtp 傳送配接器**效能物件類別：</span><span class="sxs-lookup"><span data-stu-id="5707a-105">The following performance counters are accessible for each host instance under the **BizTalk:SMTP Send Adapter** performance object category:</span></span>  
  
|<span data-ttu-id="5707a-106">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="5707a-106">**Category**</span></span>|<span data-ttu-id="5707a-107">**計數器**</span><span class="sxs-lookup"><span data-stu-id="5707a-107">**Counter**</span></span>|<span data-ttu-id="5707a-108">**說明**</span><span class="sxs-lookup"><span data-stu-id="5707a-108">**Description**</span></span>|  
|------------------|-----------------|---------------------|  
|<span data-ttu-id="5707a-109">BizTalk:SMTP 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="5707a-109">BizTalk:SMTP Send Adapter</span></span>|<span data-ttu-id="5707a-110">Messages sent</span><span class="sxs-lookup"><span data-stu-id="5707a-110">Messages sent</span></span>|<span data-ttu-id="5707a-111">SMTP 配接器傳送的訊息總數。</span><span class="sxs-lookup"><span data-stu-id="5707a-111">Total number of messages sent by the SMTP adapter.</span></span> <span data-ttu-id="5707a-112">此計數器只會在訊息已傳送到 SMTP 伺服器後遞增。</span><span class="sxs-lookup"><span data-stu-id="5707a-112">The counter is incremented only for messages that have been transmitted to the SMTP server.</span></span>|  
||<span data-ttu-id="5707a-113">Messages sent/Sec</span><span class="sxs-lookup"><span data-stu-id="5707a-113">Messages sent/Sec</span></span>|<span data-ttu-id="5707a-114">SMTP 配接器每秒傳送的訊息數。</span><span class="sxs-lookup"><span data-stu-id="5707a-114">Number of messages sent by the SMTP adapter per second.</span></span> <span data-ttu-id="5707a-115">此計數器只適用於已經傳輸至 SMTP 伺服器的訊息。</span><span class="sxs-lookup"><span data-stu-id="5707a-115">The counter applies only to messages that have been transmitted to the SMTP server.</span></span>|  
  
## <a name="to-access-performance-counters"></a><span data-ttu-id="5707a-116">存取效能計數器</span><span class="sxs-lookup"><span data-stu-id="5707a-116">To access performance counters</span></span>  
 <span data-ttu-id="5707a-117">使用下列步驟來存取效能計數器。</span><span class="sxs-lookup"><span data-stu-id="5707a-117">Use the following steps to access the performance counters.</span></span>  
  
#### <a name="if-you-are-using-windows-2008"></a><span data-ttu-id="5707a-118">若是使用 Windows 2008</span><span class="sxs-lookup"><span data-stu-id="5707a-118">If you are using Windows 2008</span></span>  
  
1.  <span data-ttu-id="5707a-119">按一下**啟動**，指向 **系統管理工具**，然後按一下 **效能監視器**。</span><span class="sxs-lookup"><span data-stu-id="5707a-119">Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.</span></span>  
  
2.  <span data-ttu-id="5707a-120">在**效能監視器**對話方塊方塊中，展開 **監視工具**，選取**效能監視器**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="5707a-120">In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="5707a-121">在**新增計數器**對話方塊中，從**可用的計數器**清單中，展開**biztalk: Smtp 傳送配接器**效能計數器物件，然後選取要計數器監視</span><span class="sxs-lookup"><span data-stu-id="5707a-121">In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:SMTP Send Adapter**performance counter object and select the counters to be monitored</span></span>  
  
4.  <span data-ttu-id="5707a-122">在**選取執行個體的物件**清單中，選取要監視針對所選取計數器，然後按一下 特定的執行個體**新增**。</span><span class="sxs-lookup"><span data-stu-id="5707a-122">In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.</span></span>  <span data-ttu-id="5707a-123">若要選取所有可用的計數器執行個體，請選取\<**所有執行個體**\>。</span><span class="sxs-lookup"><span data-stu-id="5707a-123">To select all available counter instances, select \<**All instances**\>.</span></span>  
  
5.  <span data-ttu-id="5707a-124">新增計數器後, 按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="5707a-124">After adding the counters, click **OK**.</span></span>  
  
     <span data-ttu-id="5707a-125">選取的效能計數器隨即出現在**效能監視器**螢幕。</span><span class="sxs-lookup"><span data-stu-id="5707a-125">The selected performance counters appear on the **Performance Monitor** screen.</span></span>