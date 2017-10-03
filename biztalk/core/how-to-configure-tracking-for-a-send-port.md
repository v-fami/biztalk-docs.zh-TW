---
title: "如何設定傳送埠的追蹤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, send ports
- configuring, tracking
- tracking, send ports
- configuring [HAT tracking], send ports
- send ports, tracking
- managing [send ports], configuring
- tracking, configuring
- send ports, configuring
- managing [send ports], tracking
- HAT, send ports
ms.assetid: f32e97b0-244c-4acc-8f3f-b18cdb9ec0da
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60ba83b7d3451599a0422ec370fed41eeba94407
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-tracking-for-a-send-port"></a><span data-ttu-id="4fa85-102">如何設定傳送埠的追蹤</span><span class="sxs-lookup"><span data-stu-id="4fa85-102">How to Configure Tracking for a Send Port</span></span>
<span data-ttu-id="4fa85-103">本主題描述如何使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定追蹤傳送埠，例如選項，以檢視訊息內文和升級屬性。</span><span class="sxs-lookup"><span data-stu-id="4fa85-103">This topic describes how to use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to configure tracking for a send port, such as options to view message bodies and promoted properties.</span></span> <span data-ttu-id="4fa85-104">這可以協助您監控 BizTalk 實作的狀況並找出任何瓶頸。</span><span class="sxs-lookup"><span data-stu-id="4fa85-104">This helps you monitor the health of your BizTalk implementation and identify any bottlenecks.</span></span> <span data-ttu-id="4fa85-105">您設定的追蹤設定適用於傳送埠的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="4fa85-105">The tracking settings that you configure apply to all of the instances of the send port.</span></span>  
  
 <span data-ttu-id="4fa85-106">如需有關追蹤功能的訊息事件和服務執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)</span><span class="sxs-lookup"><span data-stu-id="4fa85-106">For more information about the message event and service instance tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md)</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4fa85-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="4fa85-107">Prerequisites</span></span>  
 <span data-ttu-id="4fa85-108">若要執行這個主題中的程序，您必須使用「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="4fa85-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span> <span data-ttu-id="4fa85-109">如需詳細的權限的相關資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="4fa85-109">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-tracking-for-a-send-port"></a><span data-ttu-id="4fa85-110">設定傳送埠的追蹤</span><span class="sxs-lookup"><span data-stu-id="4fa85-110">To configure tracking for a send port</span></span>  
  
1.  <span data-ttu-id="4fa85-111">按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="4fa85-111">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="4fa85-112">在主控台樹狀結構中，展開您要為傳送埠設定追蹤的 BizTalk 群組與 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4fa85-112">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure tracking for a send port.</span></span>  
  
3.  <span data-ttu-id="4fa85-113">按一下**傳送埠**，以滑鼠右鍵按一下傳送埠，按一下**屬性**，然後按一下 **追蹤**。</span><span class="sxs-lookup"><span data-stu-id="4fa85-113">Click **Send Ports**, right-click the send port, click **Properties**, and then click **Tracking**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4fa85-114">一個傳送埠只能與一個傳送管線相關聯。</span><span class="sxs-lookup"><span data-stu-id="4fa85-114">One send port can be associated with only one send pipeline.</span></span> <span data-ttu-id="4fa85-115">如果停用傳送管線上的訊息內文追蹤，則也不會對傳送埠進行任何追蹤。</span><span class="sxs-lookup"><span data-stu-id="4fa85-115">If message body tracking is disabled on the send pipeline, nothing can be tracked on the send port as well.</span></span> <span data-ttu-id="4fa85-116">在這類情況下，您可以停用該傳送埠上的「追蹤」選項。</span><span class="sxs-lookup"><span data-stu-id="4fa85-116">In such a scenario, you can disable the "Tracking" options on that send port.</span></span>  
  
4.  <span data-ttu-id="4fa85-117">下表中所述，設定您要的追蹤選項，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4fa85-117">Configure the tracking options you want, as described in the following table, and then click **OK**.</span></span>  
  
    |<span data-ttu-id="4fa85-118">使用</span><span class="sxs-lookup"><span data-stu-id="4fa85-118">Use this</span></span>|<span data-ttu-id="4fa85-119">動作</span><span class="sxs-lookup"><span data-stu-id="4fa85-119">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="4fa85-120">**追蹤訊息內文-連接埠處理前要求訊息**</span><span class="sxs-lookup"><span data-stu-id="4fa85-120">**Track Message Bodies - Request message before port processing**</span></span>|<span data-ttu-id="4fa85-121">選取此核取方塊，可讓您在收到訊息之前儲存和追蹤訊息內容。</span><span class="sxs-lookup"><span data-stu-id="4fa85-121">Select this check box to enable you to save and track message content before the message is received.</span></span> <span data-ttu-id="4fa85-122">**注意：**您必須啟用訊息內文管線追蹤，才能成功追蹤連接埠處理前的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="4fa85-122">**Note:**  You must enable message body pipeline tracking to successfully track the response message before port processing.</span></span>|  
    |<span data-ttu-id="4fa85-123">**追蹤訊息內文-連接埠處理後要求訊息**</span><span class="sxs-lookup"><span data-stu-id="4fa85-123">**Track Message Bodies - Request message after port processing**</span></span>|<span data-ttu-id="4fa85-124">選取此核取方塊，可讓您在收到訊息之後儲存和追蹤訊息內容。</span><span class="sxs-lookup"><span data-stu-id="4fa85-124">Select this check box to enable you to save and track message content after the message is received.</span></span>|  
    |||  
    |||  
    |<span data-ttu-id="4fa85-125">**追蹤訊息屬性-連接埠處理前要求訊息**</span><span class="sxs-lookup"><span data-stu-id="4fa85-125">**Track Message Properties - Request message before port processing**</span></span>|<span data-ttu-id="4fa85-126">選取此核取方塊，可追蹤輸入訊息的升級屬性。</span><span class="sxs-lookup"><span data-stu-id="4fa85-126">Select this check box to track the promoted properties of an inbound message.</span></span>|  
    |<span data-ttu-id="4fa85-127">**追蹤訊息屬性-連接埠處理後要求訊息**</span><span class="sxs-lookup"><span data-stu-id="4fa85-127">**Track Message Properties - Request message after port processing**</span></span>|<span data-ttu-id="4fa85-128">若您想要追蹤輸出訊息的升級屬性，請選取此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="4fa85-128">Select this check box if you want to track the promoted properties of an outbound message.</span></span>|  
    |||  
    |||  
  
## <a name="see-also"></a><span data-ttu-id="4fa85-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fa85-129">See Also</span></span>  
 [<span data-ttu-id="4fa85-130">建立和設定傳送埠</span><span class="sxs-lookup"><span data-stu-id="4fa85-130">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)