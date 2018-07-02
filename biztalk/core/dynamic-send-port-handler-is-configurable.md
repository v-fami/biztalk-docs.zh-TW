---
title: 動態傳送埠處理常式是可設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eb8f5ef-af95-4b2e-9a43-6f1240b25855
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea7fb4a2f877baf70c0684c57b83e5f32edaa4d6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971775"
---
# <a name="dynamic-send-port-handler-is-configurable"></a><span data-ttu-id="a9449-102">可設定動態傳送埠處理常式</span><span class="sxs-lookup"><span data-stu-id="a9449-102">Dynamic Send Port Handler is Configurable</span></span>
<span data-ttu-id="a9449-103">建立動態傳送埠時，可針對「每一個」安裝的配接器設定配接器傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="a9449-103">When creating a Dynamic Send Port, an adapter Send Handler is configurable for *every* installed adapter.</span></span> <span data-ttu-id="a9449-104">請考慮下列案例：</span><span class="sxs-lookup"><span data-stu-id="a9449-104">Consider the following scenario:</span></span>  
  
 <span data-ttu-id="a9449-105">**狀況**</span><span class="sxs-lookup"><span data-stu-id="a9449-105">**Scenario**</span></span>  
  
 <span data-ttu-id="a9449-106">應用程式中有兩個 ESB 行程。</span><span class="sxs-lookup"><span data-stu-id="a9449-106">There are two ESB itineraries in an application.</span></span> <span data-ttu-id="a9449-107">Itinerary1 使用動態傳送埠將資料傳送至檔案共用。</span><span class="sxs-lookup"><span data-stu-id="a9449-107">Itinerary1 uses a Dynamic Send Port to send data to a File share.</span></span> <span data-ttu-id="a9449-108">Itinerary2 使用動態傳送埠傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="a9449-108">Itinerary2 uses a Dynamic Send Port to send e-mail.</span></span> <span data-ttu-id="a9449-109">動態傳送埠過去是在配接器的預設主控件中執行。</span><span class="sxs-lookup"><span data-stu-id="a9449-109">In the past, Dynamic send ports execute in the adapter's default host.</span></span> <span data-ttu-id="a9449-110">Itinerary1 主要是以小量 - 大型訊息大小案例為目標。</span><span class="sxs-lookup"><span data-stu-id="a9449-110">Itinerary1 is designed to target a low volume - big message size scenario.</span></span> <span data-ttu-id="a9449-111">Itinerary2 是以大量 - 小型訊息大小案例為目標。</span><span class="sxs-lookup"><span data-stu-id="a9449-111">Itinerary2 targets a high volume - small message size scenario.</span></span> <span data-ttu-id="a9449-112">因為一個配接器只有一個預設主控件，所有會使用相同的主控件來路由傳送所有訊息，因而使效能降低。</span><span class="sxs-lookup"><span data-stu-id="a9449-112">Since there is only one default host for an adapter, all messages are routed using the same host, decreasing the performance.</span></span>  
  
 <span data-ttu-id="a9449-113">**變更**</span><span class="sxs-lookup"><span data-stu-id="a9449-113">**The Change**</span></span>  
  
 <span data-ttu-id="a9449-114">若要改善動態傳送埠的效能，可以將配接器傳送處理常式設定為使用任何主控件。</span><span class="sxs-lookup"><span data-stu-id="a9449-114">To improve the performance of Dynamic Send Ports, an adapter Send Handler is configurable to use any host.</span></span> <span data-ttu-id="a9449-115">在 ESB 案例中，Itinerary1 使用 HostA 將資料傳送至檔案共用。</span><span class="sxs-lookup"><span data-stu-id="a9449-115">In the ESB scenario, Itinerary1 uses HostA to send data to a File share.</span></span> <span data-ttu-id="a9449-116">Itinerary2 使用 HostB 連接埠傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="a9449-116">Itinerary2 uses HostB Port to send e-mail.</span></span>  
  
## <a name="select-a-send-handler"></a><span data-ttu-id="a9449-117">選取 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="a9449-117">Select a Send Handler</span></span>  
 <span data-ttu-id="a9449-118">建立動態單向傳送埠或動態請求-回應傳送埠時，可針對每一個安裝的配接器設定傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="a9449-118">When creating a Dynamic One-Way Send Port or Dynamic Solicit-Response Send Port, the Send Handler is configurable for every installed adapter.</span></span> <span data-ttu-id="a9449-119">步驟：</span><span class="sxs-lookup"><span data-stu-id="a9449-119">Steps:</span></span>  
  
1. <span data-ttu-id="a9449-120">在**BizTalk Server 管理**主控台中，展開**BizTalk 群組 [*GroupName*]**，展開**應用程式**，然後展開包含傳送埠的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a9449-120">In the **BizTalk Server Administration** console, expand **BizTalk Group [*GroupName*]**, expand **Applications**, and then expand the application to contain the send port.</span></span>  
  
2. <span data-ttu-id="a9449-121">以滑鼠右鍵按一下**傳送埠**，按一下**新增**，然後按一下**動態單向傳送埠**或是**動態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="a9449-121">Right-click **Send Ports**, click **New**, and then click **Dynamic One-way Send Port** or **Dynamic Solicit-Response Send Port**.</span></span>  
  
3. <span data-ttu-id="a9449-122">在 **屬性**，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="a9449-122">In  **Properties**, click **Configure**.</span></span>  
  
    <span data-ttu-id="a9449-123">配接器會與預設傳送處理常式一起列出。</span><span class="sxs-lookup"><span data-stu-id="a9449-123">The adapters are listed with the default Send Handler.</span></span> <span data-ttu-id="a9449-124">按一下向下箭頭以選取不同的主控件。</span><span class="sxs-lookup"><span data-stu-id="a9449-124">Click the down arrow to select a different host.</span></span>  
  
4. <span data-ttu-id="a9449-125">按一下 **確定**儲存設定。</span><span class="sxs-lookup"><span data-stu-id="a9449-125">Click **OK** save the settings.</span></span>  
  
5. <span data-ttu-id="a9449-126">取消登錄，並重新編列新的動態傳送埠。</span><span class="sxs-lookup"><span data-stu-id="a9449-126">Unenlist and reenlist the new dynamic send port.</span></span>  
  
6. <span data-ttu-id="a9449-127">重新啟動原始的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="a9449-127">Restart the original host instance.</span></span>  
  
7. <span data-ttu-id="a9449-128">重新啟動新的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="a9449-128">Restart the new host instance.</span></span>  
  
   <span data-ttu-id="a9449-129">其他傳送埠設定選項包含：</span><span class="sxs-lookup"><span data-stu-id="a9449-129">Additional Send Port configuration options include:</span></span>  
  
- [<span data-ttu-id="a9449-130">如何設定傳送埠的傳輸進階選項</span><span class="sxs-lookup"><span data-stu-id="a9449-130">How to Configure Transport Advanced Options for a Send Port</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=267697)  
  
- [<span data-ttu-id="a9449-131">如何設定傳送埠備份傳輸選項</span><span class="sxs-lookup"><span data-stu-id="a9449-131">How to Configure Backup Transport Options for a Send Port</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=267698)  
  
- [<span data-ttu-id="a9449-132">如何設定傳送埠的輸出對應</span><span class="sxs-lookup"><span data-stu-id="a9449-132">How to Configure Outbound Maps for a Send Port</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=267699)  
  
- [<span data-ttu-id="a9449-133">如何設定傳送埠的篩選</span><span class="sxs-lookup"><span data-stu-id="a9449-133">How to Configure Filters for a Send Port</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=267700)  
  
- [<span data-ttu-id="a9449-134">如何指派憑證給傳送埠</span><span class="sxs-lookup"><span data-stu-id="a9449-134">How to Assign a Certificate to a Send Port</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=267701)  
  
- [<span data-ttu-id="a9449-135">如何設定傳送埠的追蹤</span><span class="sxs-lookup"><span data-stu-id="a9449-135">How to Configure Tracking for a Send Port</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=267702)  
  
  <span data-ttu-id="a9449-136">您可以微調不同的主控件。</span><span class="sxs-lookup"><span data-stu-id="a9449-136">The different hosts can be fine-tuned.</span></span> <span data-ttu-id="a9449-137">下列連結將討論效能最佳化：</span><span class="sxs-lookup"><span data-stu-id="a9449-137">The following links discuss performance optimization:</span></span>  
  
  [<span data-ttu-id="a9449-138">一般 BizTalk Server 最佳化</span><span class="sxs-lookup"><span data-stu-id="a9449-138">General BizTalk Server Optimizations</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=267703)  
  
  [<span data-ttu-id="a9449-139">管理 BizTalk Server 效能設定</span><span class="sxs-lookup"><span data-stu-id="a9449-139">Managing BizTalk Server Performance Settings</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=267704)