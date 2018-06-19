---
title: 啟用 [追蹤傳送埠] |Microsoft 文件
description: 開啟訊息內文追蹤，並在 BizTalk Server 中的傳送埠上追蹤訊息屬性
ms.custom: ''
ms.date: 12/13/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f32e97b0-244c-4acc-8f3f-b18cdb9ec0da
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 223c417769086cc71f501b044410bf2d3e4cbc74
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/13/2017
ms.locfileid: "26686629"
---
# <a name="configure-send-port-tracking-in-biztalk-server"></a><span data-ttu-id="db470-103">在 BizTalk Server 中設定傳送埠的追蹤</span><span class="sxs-lookup"><span data-stu-id="db470-103">Configure send port tracking in BizTalk Server</span></span>
<span data-ttu-id="db470-104">使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定追蹤傳送埠，例如選項，以檢視訊息內文和升級屬性。</span><span class="sxs-lookup"><span data-stu-id="db470-104">Use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to configure tracking for a send port, such as options to view message bodies and promoted properties.</span></span> <span data-ttu-id="db470-105">這可以協助您監控 BizTalk 實作的狀況並找出任何瓶頸。</span><span class="sxs-lookup"><span data-stu-id="db470-105">This helps you monitor the health of your BizTalk implementation and identify any bottlenecks.</span></span> <span data-ttu-id="db470-106">您設定的追蹤設定適用於傳送埠的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="db470-106">The tracking settings that you configure apply to all of the instances of the send port.</span></span>  
  
 <span data-ttu-id="db470-107">如需有關追蹤功能的訊息事件和服務執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)</span><span class="sxs-lookup"><span data-stu-id="db470-107">For more information about the message event and service instance tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md)</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="db470-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="db470-108">Prerequisites</span></span>  
<span data-ttu-id="db470-109">使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。</span><span class="sxs-lookup"><span data-stu-id="db470-109">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span> <span data-ttu-id="db470-110">如需詳細的權限的相關資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="db470-110">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="enable-tracking-on-a-send-port"></a><span data-ttu-id="db470-111">啟用 [追蹤] 傳送埠</span><span class="sxs-lookup"><span data-stu-id="db470-111">Enable tracking on a send port</span></span>  
  
1.  <span data-ttu-id="db470-112">在**BizTalk Server 管理**、 依序展開 [BizTalk 群組] 和您傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="db470-112">In **BizTalk Server Administration**, expand the BizTalk group, and then expand your BizTalk application that has the send port.</span></span>  
  
2.  <span data-ttu-id="db470-113">選取**傳送埠**、 以滑鼠右鍵按一下傳送埠、 選取**屬性**，然後選取**追蹤**。</span><span class="sxs-lookup"><span data-stu-id="db470-113">Select **Send Ports**, right-click the send port, select **Properties**, and then select **Tracking**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="db470-114">一個傳送埠只能與一個傳送管線相關聯。</span><span class="sxs-lookup"><span data-stu-id="db470-114">One send port can be associated with only one send pipeline.</span></span> <span data-ttu-id="db470-115">訊息內文追蹤已停用在傳送管線，不會追蹤在傳送埠。</span><span class="sxs-lookup"><span data-stu-id="db470-115">If message body tracking is disabled on the send pipeline, then nothing is tracked on the send port.</span></span> <span data-ttu-id="db470-116">在這類情況下，您可以停用該傳送埠上的「追蹤」選項。</span><span class="sxs-lookup"><span data-stu-id="db470-116">In such a scenario, you can disable the "Tracking" options on that send port.</span></span>  
  
3.  <span data-ttu-id="db470-117">使用下列詳細資料，若要啟用的追蹤選項，然後再選取**確定**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="db470-117">Use the following details to enable the tracking options you want, and then select **OK** to save your changes.</span></span>  
  
    |<span data-ttu-id="db470-118">使用</span><span class="sxs-lookup"><span data-stu-id="db470-118">Use this</span></span>|<span data-ttu-id="db470-119">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="db470-119">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="db470-120">**追蹤訊息內文-連接埠處理前要求訊息**</span><span class="sxs-lookup"><span data-stu-id="db470-120">**Track Message Bodies - Request message before port processing**</span></span>|<span data-ttu-id="db470-121">儲存和追蹤訊息內容，才能接收訊息。</span><span class="sxs-lookup"><span data-stu-id="db470-121">Saves and tracks message content before the message is received.</span></span> <br/><br/> <span data-ttu-id="db470-122">**請注意**： 請務必啟用訊息內文管線追蹤，才能成功追蹤連接埠處理前的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="db470-122">**Note**: Be sure to enable message body pipeline tracking to successfully track the response message before port processing.</span></span>|  
    |<span data-ttu-id="db470-123">**追蹤訊息內文-連接埠處理後要求訊息**</span><span class="sxs-lookup"><span data-stu-id="db470-123">**Track Message Bodies - Request message after port processing**</span></span>|<span data-ttu-id="db470-124">儲存並收到訊息之後，追蹤訊息內容。</span><span class="sxs-lookup"><span data-stu-id="db470-124">Saves and tracks message content after the message is received.</span></span>|  
    |<span data-ttu-id="db470-125">**追蹤訊息內文-連接埠處理前回應訊息**</span><span class="sxs-lookup"><span data-stu-id="db470-125">**Track Message Bodies – Response message before port processing**</span></span>|<span data-ttu-id="db470-126">儲存並傳送訊息之前，追蹤訊息內容。</span><span class="sxs-lookup"><span data-stu-id="db470-126">Saves and tracks message content before the message is sent.</span></span> <span data-ttu-id="db470-127">只適用於請求-回應傳送埠。</span><span class="sxs-lookup"><span data-stu-id="db470-127">Only available for solicit-response send ports.</span></span>|    
    |<span data-ttu-id="db470-128">**追蹤訊息內文-連接埠處理後回應訊息**</span><span class="sxs-lookup"><span data-stu-id="db470-128">**Track Message Bodies – Response message after port processing**</span></span>|<span data-ttu-id="db470-129">儲存並傳送訊息之後，追蹤訊息內容。</span><span class="sxs-lookup"><span data-stu-id="db470-129">Saves and tracks message content after the message is sent.</span></span> <span data-ttu-id="db470-130">只適用於請求-回應傳送埠。</span><span class="sxs-lookup"><span data-stu-id="db470-130">Only available for solicit-response send ports.</span></span>|  
    |<span data-ttu-id="db470-131">**追蹤訊息內文-連接埠處理後回應訊息**</span><span class="sxs-lookup"><span data-stu-id="db470-131">**Track Message Bodies – Response message after port processing**</span></span>|<span data-ttu-id="db470-132">追蹤輸入訊息的升級屬性。</span><span class="sxs-lookup"><span data-stu-id="db470-132">Tracks the promoted properties of an inbound message.</span></span>|  
    |<span data-ttu-id="db470-133">**追蹤訊息屬性-連接埠處理後要求訊息**</span><span class="sxs-lookup"><span data-stu-id="db470-133">**Track Message Properties - Request message after port processing**</span></span>|<span data-ttu-id="db470-134">追蹤輸出訊息的升級屬性。</span><span class="sxs-lookup"><span data-stu-id="db470-134">Tracks the promoted properties of an outbound message.</span></span>|  
    |<span data-ttu-id="db470-135">**追蹤訊息屬性-連接埠處理前回應訊息**</span><span class="sxs-lookup"><span data-stu-id="db470-135">**Track Message Properties – Response message before port processing**</span></span>|<span data-ttu-id="db470-136">儲存並傳送訊息之前，會追蹤訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="db470-136">Saves and tracks message properties before the message is sent.</span></span> <span data-ttu-id="db470-137">只適用於請求-回應傳送埠。</span><span class="sxs-lookup"><span data-stu-id="db470-137">Only available for solicit-response send ports.</span></span>|   
    |<span data-ttu-id="db470-138">**追蹤訊息屬性-連接埠處理後回應訊息**</span><span class="sxs-lookup"><span data-stu-id="db470-138">**Track Message Properties – Response message after port processing**</span></span>|<span data-ttu-id="db470-139">儲存並傳送訊息之後，會追蹤屬性。</span><span class="sxs-lookup"><span data-stu-id="db470-139">Saves and tracks properties after the message is sent.</span></span> <span data-ttu-id="db470-140">只適用於請求-回應傳送埠。</span><span class="sxs-lookup"><span data-stu-id="db470-140">Only available for solicit-response send ports.</span></span>|   
  
## <a name="see-also"></a><span data-ttu-id="db470-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="db470-141">See Also</span></span>  
 [<span data-ttu-id="db470-142">建立和設定傳送埠</span><span class="sxs-lookup"><span data-stu-id="db470-142">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)
