---
title: "如何設定管線追蹤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [pipelines], tracking warning
- tracking, pipelines
- tracking, warnings
- configuring, pipelines
- pipelines, tracking
- managing [pipelines], configuring
- tracking, configuring
- pipelines, configuring
- configuring [HAT tracking], pipelines
- HAT, pipelines
- managing [pipelines], tracking
ms.assetid: 4f7f3c4a-4464-4170-a580-b4ce9296a097
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f34abe4d9d8b97b1c61bfc6201c3d36b977d0697
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-tracking-for-a-pipeline"></a><span data-ttu-id="c7e49-102">如何設定管線的追蹤</span><span class="sxs-lookup"><span data-stu-id="c7e49-102">How to Configure Tracking for a Pipeline</span></span>
<span data-ttu-id="c7e49-103">本主題描述如何使用「BizTalk Server 管理」來設定管線追蹤。</span><span class="sxs-lookup"><span data-stu-id="c7e49-103">This topic describes how to use the BizTalk Server Administration to configure tracking for a pipeline.</span></span> <span data-ttu-id="c7e49-104">您可能需要設定追蹤做為疑難排解和稽核之用。</span><span class="sxs-lookup"><span data-stu-id="c7e49-104">You might want to configure tracking for troubleshooting and auditing purposes.</span></span> <span data-ttu-id="c7e49-105">您可以檢視訊息屬性、 連接埠事件和訊息事件。</span><span class="sxs-lookup"><span data-stu-id="c7e49-105">You can view message properties, port events, and message events.</span></span> <span data-ttu-id="c7e49-106">您也可以追蹤訊息事件和訊息的連接埠事件。</span><span class="sxs-lookup"><span data-stu-id="c7e49-106">You can also track message events and port events for messages.</span></span>  
  
 <span data-ttu-id="c7e49-107">您可以設定追蹤其中一個預設管線隨附[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或自訂管線已部署到 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c7e49-107">You can configure tracking for one of the default pipelines included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or a custom pipeline that has been deployed into a BizTalk application.</span></span> <span data-ttu-id="c7e49-108">您設定的追蹤設定會套用到管線的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="c7e49-108">The tracking settings that you configure apply to all of the instances of the pipeline.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c7e49-109">您可以設定管線追蹤，但這將產生大量資料，因為會全域收集使用管線的所有連接埠的資料。</span><span class="sxs-lookup"><span data-stu-id="c7e49-109">Although you can configure tracking for a pipeline, this will generate a large amount of data because data is gathered globally for all ports that use the pipeline.</span></span> <span data-ttu-id="c7e49-110">我們建議您改為您設定追蹤傳送和接收埠中所述[如何設定傳送埠的追蹤](../core/how-to-configure-tracking-for-a-send-port.md)和[如何設定追蹤接收埠](../core/how-to-configure-tracking-for-a-receive-port.md)。</span><span class="sxs-lookup"><span data-stu-id="c7e49-110">We recommend instead that you configure tracking on your send and receive ports, as described in [How to Configure Tracking for a Send Port](../core/how-to-configure-tracking-for-a-send-port.md) and [How to Configure Tracking for a Receive Port](../core/how-to-configure-tracking-for-a-receive-port.md).</span></span>  
  
 <span data-ttu-id="c7e49-111">如需有關追蹤功能的訊息事件和服務執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)</span><span class="sxs-lookup"><span data-stu-id="c7e49-111">For more information about the message event and service instance tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md)</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c7e49-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="c7e49-112">Prerequisites</span></span>  
 <span data-ttu-id="c7e49-113">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="c7e49-113">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="c7e49-114">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="c7e49-114">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-tracking-for-a-pipeline"></a><span data-ttu-id="c7e49-115">設定管線的追蹤</span><span class="sxs-lookup"><span data-stu-id="c7e49-115">To configure tracking for a pipeline</span></span>  
  
1.  <span data-ttu-id="c7e49-116">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="c7e49-116">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="c7e49-117">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**展開包含要設定追蹤的管線的 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="c7e49-117">In the console tree, expand **BizTalk Server Administration** and expand the BizTalk group containing the pipeline for which to configure tracking.</span></span>  
  
3.  <span data-ttu-id="c7e49-118">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="c7e49-118">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="c7e49-119">若要設定追蹤其中一個預設 BizTalk 管線中，展開 \<所有成品\>。</span><span class="sxs-lookup"><span data-stu-id="c7e49-119">To configure tracking for one of the default BizTalk pipelines, expand \<All Artifacts\>.</span></span>  
  
    -   <span data-ttu-id="c7e49-120">若要設定追蹤已部署到 BizTalk 應用程式的自訂管線，請展開包含管線的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c7e49-120">To configure tracking for a custom pipeline that has been deployed into a BizTalk application, expand the application containing the pipeline.</span></span>  
  
4.  <span data-ttu-id="c7e49-121">按一下**管線**資料夾中，以滑鼠右鍵按一下管線，然後按一下**追蹤**。</span><span class="sxs-lookup"><span data-stu-id="c7e49-121">Click the **Pipelines** folder, right-click the pipeline, and then click **Tracking**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c7e49-122">若要設定的多個管線，按住 Shift 鍵，按一下 設定每個管線追蹤，以滑鼠右鍵按一下其中一個管線，然後**追蹤**。</span><span class="sxs-lookup"><span data-stu-id="c7e49-122">To configure tracking for multiple pipelines at once, hold down the Shift key, click each pipeline to configure, right-click one of the pipelines, and then click **Tracking**.</span></span>  
  
5.  <span data-ttu-id="c7e49-123">下表中所述，設定您要的追蹤選項，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c7e49-123">Configure tracking options you want, as described in the following table, and then click **OK**.</span></span>  
  
    |<span data-ttu-id="c7e49-124">使用</span><span class="sxs-lookup"><span data-stu-id="c7e49-124">Use this</span></span>|<span data-ttu-id="c7e49-125">動作</span><span class="sxs-lookup"><span data-stu-id="c7e49-125">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="c7e49-126">**連接埠開始與結束事件**</span><span class="sxs-lookup"><span data-stu-id="c7e49-126">**Port start and end events**</span></span>|<span data-ttu-id="c7e49-127">僅限於執行個體開始與結束時，才選取此核取方塊以進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="c7e49-127">Select this check box to track only when an instance starts and ends.</span></span> <span data-ttu-id="c7e49-128">詳細資訊包括項目名稱、組件及其他中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c7e49-128">Details include item name, assembly, and other metadata.</span></span>|  
    |<span data-ttu-id="c7e49-129">**訊息傳送與接收事件**</span><span class="sxs-lookup"><span data-stu-id="c7e49-129">**Message send and receive events**</span></span>|<span data-ttu-id="c7e49-130">選取此核取方塊以追蹤訊息傳送與接收事件。</span><span class="sxs-lookup"><span data-stu-id="c7e49-130">Select this check box to track message send and receive events.</span></span> <span data-ttu-id="c7e49-131">此核取方塊才**連接埠開始與結束事件**已選取。</span><span class="sxs-lookup"><span data-stu-id="c7e49-131">This check box is available only if **Port start and end events** is selected.</span></span>|  
    |<span data-ttu-id="c7e49-132">**管線處理之前的訊息**</span><span class="sxs-lookup"><span data-stu-id="c7e49-132">**Messages before pipeline processing**</span></span>|<span data-ttu-id="c7e49-133">選取此核取方塊以儲存及追蹤管線所接收的訊息內文，其中包含 URL 及升級屬性等中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c7e49-133">Select this check box to save and track the message bodies received by the pipeline, which holds metadata such as URLs and promoted properties.</span></span> <span data-ttu-id="c7e49-134">若此管線屬於接收管線，則訊息內文即為傳輸元件提交給管線的原始訊息。</span><span class="sxs-lookup"><span data-stu-id="c7e49-134">If this is a receive pipeline, the message body is the raw message as submitted to the pipeline by the transport component.</span></span> <span data-ttu-id="c7e49-135">視您的應用程式而定，訊息可能經過加密、簽章或編碼。</span><span class="sxs-lookup"><span data-stu-id="c7e49-135">Depending on the application, the message might be encrypted, signed, or encoded.</span></span> <span data-ttu-id="c7e49-136">使用 BizTalk 對應時，如果此管線屬於接收管線，則會在處理輸入對應之後執行追蹤。</span><span class="sxs-lookup"><span data-stu-id="c7e49-136">When using a BizTalk map, if this is a receive pipeline, tracking takes place after the inbound map is processed.</span></span><br /><br /> <span data-ttu-id="c7e49-137">此核取方塊才**訊息傳送與接收事件**已選取。</span><span class="sxs-lookup"><span data-stu-id="c7e49-137">This check box is available only if **Message send and receive events** is selected.</span></span>|  
    |<span data-ttu-id="c7e49-138">**管線處理後的訊息**</span><span class="sxs-lookup"><span data-stu-id="c7e49-138">**Messages after pipeline processing**</span></span>|<span data-ttu-id="c7e49-139">選取此核取方塊以儲存及追蹤管線所傳送的訊息內文，其中包含 URL 及升級屬性等中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c7e49-139">Select this check box to save and track the message bodies sent by the pipeline, which holds metadata such as URLs and promoted properties.</span></span> <span data-ttu-id="c7e49-140">若此管線屬於接收管線，則訊息內文即為要提交給 MessageBox 資料庫的已處理訊息，視您的應用程式而定，這個訊息可能是 XML。</span><span class="sxs-lookup"><span data-stu-id="c7e49-140">If this is a receive pipeline, the message body is the processed message to be submitted to the MessageBox database, which may be XML depending on your application.</span></span> <span data-ttu-id="c7e49-141">使用 BizTalk 對應時，如果此管線屬於傳送管線，則會在處理輸出對應之前執行追蹤。</span><span class="sxs-lookup"><span data-stu-id="c7e49-141">When using a BizTalk map, if this is a send pipeline, tracking takes place before the outbound map is processed.</span></span><br /><br /> <span data-ttu-id="c7e49-142">此核取方塊才**訊息傳送與接收事件**已選取。</span><span class="sxs-lookup"><span data-stu-id="c7e49-142">This check box is available only if **Message send and receive events** is selected.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7e49-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="c7e49-143">See Also</span></span>  
 [<span data-ttu-id="c7e49-144">管理管線</span><span class="sxs-lookup"><span data-stu-id="c7e49-144">Managing Pipelines</span></span>](../core/managing-pipelines.md)