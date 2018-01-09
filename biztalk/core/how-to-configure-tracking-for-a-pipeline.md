---
title: "啟用追蹤的管線 |Microsoft 文件"
description: "追蹤訊息內文和在管線處理訊息，BizTalk Server 中的事件"
ms.custom: 
ms.date: 12/13/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f7f3c4a-4464-4170-a580-b4ce9296a097
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ed836947ff47e21eeeb3bc306e94ea08f5464f0
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/13/2017
---
# <a name="configure-pipeline-tracking-in-biztalk-server"></a><span data-ttu-id="4e24b-103">設定追蹤 BizTalk Server 中的管線</span><span class="sxs-lookup"><span data-stu-id="4e24b-103">Configure pipeline tracking in BizTalk Server</span></span>
<span data-ttu-id="4e24b-104">您可以使用 BizTalk Server 管理來設定管線追蹤。</span><span class="sxs-lookup"><span data-stu-id="4e24b-104">Use the BizTalk Server Administration to configure tracking for a pipeline.</span></span> <span data-ttu-id="4e24b-105">您可能需要設定追蹤做為疑難排解和稽核之用。</span><span class="sxs-lookup"><span data-stu-id="4e24b-105">You might want to configure tracking for troubleshooting and auditing purposes.</span></span> <span data-ttu-id="4e24b-106">您可以檢視訊息屬性、 連接埠事件和訊息事件。</span><span class="sxs-lookup"><span data-stu-id="4e24b-106">You can view message properties, port events, and message events.</span></span> <span data-ttu-id="4e24b-107">您也可以追蹤訊息事件和訊息的連接埠事件。</span><span class="sxs-lookup"><span data-stu-id="4e24b-107">You can also track message events and port events for messages.</span></span>  
  
 <span data-ttu-id="4e24b-108">您可以設定追蹤其中一個預設管線隨附[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或自訂管線已部署到 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4e24b-108">You can configure tracking for one of the default pipelines included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or a custom pipeline that has been deployed into a BizTalk application.</span></span> <span data-ttu-id="4e24b-109">您設定的追蹤設定會套用到管線的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="4e24b-109">The tracking settings that you configure apply to all of the instances of the pipeline.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4e24b-110">雖然您可以設定管線追蹤，這會產生大量的資料因為資料會全域收集使用管線的所有連接埠。</span><span class="sxs-lookup"><span data-stu-id="4e24b-110">Although you can configure tracking for a pipeline, this generates a large amount of data because data is gathered globally for all ports that use the pipeline.</span></span> <span data-ttu-id="4e24b-111">相反地，我們建議您設定追蹤傳送和接收埠中所述[設定傳送埠的追蹤](../core/how-to-configure-tracking-for-a-send-port.md)和[設定追蹤接收埠](../core/how-to-configure-tracking-for-a-receive-port.md)。</span><span class="sxs-lookup"><span data-stu-id="4e24b-111">Instead, we recommend that you configure tracking on your send and receive ports, as described in [Configure Tracking for a Send Port](../core/how-to-configure-tracking-for-a-send-port.md) and [Configure Tracking for a Receive Port](../core/how-to-configure-tracking-for-a-receive-port.md).</span></span>  
  
 <span data-ttu-id="4e24b-112">如需有關追蹤功能的訊息事件和服務執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)</span><span class="sxs-lookup"><span data-stu-id="4e24b-112">For more information about the message event and service instance tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md)</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4e24b-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="4e24b-113">Prerequisites</span></span>  
<span data-ttu-id="4e24b-114">使用 BizTalk Server 系統管理員群組的成員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="4e24b-114">Sign in with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="4e24b-115">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="4e24b-115">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="enable-pipeline-tracking"></a><span data-ttu-id="4e24b-116">啟用管線追蹤</span><span class="sxs-lookup"><span data-stu-id="4e24b-116">Enable pipeline tracking</span></span>
  
1.  <span data-ttu-id="4e24b-117">在**BizTalk Server 管理**，展開包含管線的 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="4e24b-117">In **BizTalk Server Administration**, expand the BizTalk group that contains the pipeline.</span></span> 
  
2.  <span data-ttu-id="4e24b-118">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="4e24b-118">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="4e24b-119">若要設定追蹤其中一個預設 BizTalk 管線中，展開 \<所有成品\>。</span><span class="sxs-lookup"><span data-stu-id="4e24b-119">To configure tracking for one of the default BizTalk pipelines, expand \<All Artifacts\>.</span></span>  
  
    -   <span data-ttu-id="4e24b-120">若要設定追蹤已部署到 BizTalk 應用程式的自訂管線，請展開包含管線的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4e24b-120">To configure tracking for a custom pipeline that has been deployed into a BizTalk application, expand the application containing the pipeline.</span></span>  
  
3.  <span data-ttu-id="4e24b-121">選取**管線**資料夾中，以滑鼠右鍵按一下管線，然後選取**追蹤**。</span><span class="sxs-lookup"><span data-stu-id="4e24b-121">Select the **Pipelines** folder, right-click the pipeline, and then select **Tracking**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4e24b-122">若要設定追蹤，多個管線，按住 Shift 鍵，選取要設定每個管線，以滑鼠右鍵按一下其中一個管線，然後選取**追蹤**。</span><span class="sxs-lookup"><span data-stu-id="4e24b-122">To configure tracking for multiple pipelines at once, hold down the Shift key, select each pipeline to configure, right-click one of the pipelines, and then select **Tracking**.</span></span>  
  
4.  <span data-ttu-id="4e24b-123">使用下列詳細資料，若要設定追蹤選項，然後再選取**確定**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="4e24b-123">Use the follwoing details to configure the tracking options you want, and then select **OK** to save your changes.</span></span>  
  
    |<span data-ttu-id="4e24b-124">使用</span><span class="sxs-lookup"><span data-stu-id="4e24b-124">Use this</span></span>|<span data-ttu-id="4e24b-125">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="4e24b-125">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="4e24b-126">**追蹤事件-傳送埠開始與結束事件**</span><span class="sxs-lookup"><span data-stu-id="4e24b-126">**Track Events - Port start and end events**</span></span>|<span data-ttu-id="4e24b-127">只有當執行個體的開始和結束追蹤。</span><span class="sxs-lookup"><span data-stu-id="4e24b-127">Tracks only when an instance starts and ends.</span></span> <span data-ttu-id="4e24b-128">詳細資訊包括項目名稱、組件及其他中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4e24b-128">Details include item name, assembly, and other metadata.</span></span>|  
    |<span data-ttu-id="4e24b-129">**追蹤事件-訊息傳送與接收事件**</span><span class="sxs-lookup"><span data-stu-id="4e24b-129">**Track Events - Message send and receive events**</span></span>|<span data-ttu-id="4e24b-130">追蹤訊息傳送與接收事件。</span><span class="sxs-lookup"><span data-stu-id="4e24b-130">Tracks message send and receive events.</span></span> <span data-ttu-id="4e24b-131">僅適用於當**連接埠開始與結束事件**已選取。</span><span class="sxs-lookup"><span data-stu-id="4e24b-131">Only available if **Port start and end events** is selected.</span></span>|  
    |<span data-ttu-id="4e24b-132">**追蹤訊息內文-管線處理之前的訊息**</span><span class="sxs-lookup"><span data-stu-id="4e24b-132">**Track Message Bodies - Messages before pipeline processing**</span></span>|<span data-ttu-id="4e24b-133">儲存及追蹤管線，其中包含中繼資料，例如 Url 及升級屬性所接收的訊息內文。</span><span class="sxs-lookup"><span data-stu-id="4e24b-133">Saves and tracks the message bodies received by the pipeline, which holds metadata such as URLs and promoted properties.</span></span> <span data-ttu-id="4e24b-134">若此管線屬於接收管線，則訊息內文即為傳輸元件提交給管線的原始訊息。</span><span class="sxs-lookup"><span data-stu-id="4e24b-134">If this is a receive pipeline, the message body is the raw message as submitted to the pipeline by the transport component.</span></span> <span data-ttu-id="4e24b-135">視您的應用程式而定，訊息可能經過加密、簽章或編碼。</span><span class="sxs-lookup"><span data-stu-id="4e24b-135">Depending on the application, the message might be encrypted, signed, or encoded.</span></span> <span data-ttu-id="4e24b-136">使用 BizTalk 對應時，如果此管線屬於接收管線，則會在處理輸入對應之後執行追蹤。</span><span class="sxs-lookup"><span data-stu-id="4e24b-136">When using a BizTalk map, if this is a receive pipeline, tracking takes place after the inbound map is processed.</span></span><br /><br /> <span data-ttu-id="4e24b-137">僅適用於當**訊息傳送與接收事件**已選取。</span><span class="sxs-lookup"><span data-stu-id="4e24b-137">Only available if **Message send and receive events** is selected.</span></span>|  
    |<span data-ttu-id="4e24b-138">**追蹤訊息內文-管線處理後的訊息**</span><span class="sxs-lookup"><span data-stu-id="4e24b-138">**Track Message Bodies - Messages after pipeline processing**</span></span>|<span data-ttu-id="4e24b-139">儲存和追蹤訊息內文，傳送管線，其中包含中繼資料，例如 Url 及升級屬性。</span><span class="sxs-lookup"><span data-stu-id="4e24b-139">Saves and tracks the message bodies sent by the pipeline, which holds metadata such as URLs and promoted properties.</span></span> <span data-ttu-id="4e24b-140">若此管線屬於接收管線，則訊息內文即為要提交給 MessageBox 資料庫的已處理訊息，視您的應用程式而定，這個訊息可能是 XML。</span><span class="sxs-lookup"><span data-stu-id="4e24b-140">If this is a receive pipeline, the message body is the processed message to be submitted to the MessageBox database, which may be XML depending on your application.</span></span> <span data-ttu-id="4e24b-141">使用 BizTalk 對應時，如果此管線屬於傳送管線，則會在處理輸出對應之前執行追蹤。</span><span class="sxs-lookup"><span data-stu-id="4e24b-141">When using a BizTalk map, if this is a send pipeline, tracking takes place before the outbound map is processed.</span></span><br /><br /> <span data-ttu-id="4e24b-142">僅適用於當**訊息傳送與接收事件**已選取。</span><span class="sxs-lookup"><span data-stu-id="4e24b-142">Only available if **Message send and receive events** is selected.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4e24b-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="4e24b-143">See Also</span></span>  
 [<span data-ttu-id="4e24b-144">管理管線</span><span class="sxs-lookup"><span data-stu-id="4e24b-144">Managing Pipelines</span></span>](../core/managing-pipelines.md)
