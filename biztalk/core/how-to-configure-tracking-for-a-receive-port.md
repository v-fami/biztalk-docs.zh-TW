---
title: 如何設定追蹤接收埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [receive ports], configuring
- configuring [HAT tracking], receive ports
- tracking, receive ports
- receive ports, tracking
- configuring, tracking
- receive ports, configuring
- tracking, configuring
- HAT, receive ports
- configuring, receive ports
- managing [receive ports], tracking
ms.assetid: dd569e84-cb1c-4191-912a-0c2eb2781a85
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e18748a5d9ff8088d09dfe28bf23c7b729b6afc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249102"
---
# <a name="how-to-configure-tracking-for-a-receive-port"></a><span data-ttu-id="f5a69-102">如何設定追蹤接收埠</span><span class="sxs-lookup"><span data-stu-id="f5a69-102">How to Configure Tracking for a Receive Port</span></span>
<span data-ttu-id="f5a69-103">本主題描述如何使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台來設定接收埠的追蹤，例如用來檢視訊息內文和升級屬性的選項。</span><span class="sxs-lookup"><span data-stu-id="f5a69-103">This topic describes how to use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to configure tracking for a receive port, such as options to view message bodies and promoted properties..</span></span> <span data-ttu-id="f5a69-104">這可以協助您監控 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 實作的狀況並找出任何瓶頸。</span><span class="sxs-lookup"><span data-stu-id="f5a69-104">This helps you monitor the health of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] implementation and identify any bottlenecks.</span></span> <span data-ttu-id="f5a69-105">您設定的追蹤設定會套用到接收埠的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="f5a69-105">The tracking settings that you configure apply to all of the instances of the receive port.</span></span>  
  
 <span data-ttu-id="f5a69-106">如需有關追蹤功能的訊息事件和服務執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[檢查清單： 訊息和執行個體資料追蹤](../core/checklist-message-and-instance-data-tracking.md)</span><span class="sxs-lookup"><span data-stu-id="f5a69-106">For more information about the message event and service instance tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Checklist: Message and Instance Data Tracking](../core/checklist-message-and-instance-data-tracking.md)</span></span>  
  
 <span data-ttu-id="f5a69-107">您設定的追蹤設定會套用到接收埠的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="f5a69-107">The tracking settings that you configure apply to all of the instances of the receive port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f5a69-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="f5a69-108">Prerequisites</span></span>  
 <span data-ttu-id="f5a69-109">若要執行這個主題中的程序，您必須使用「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="f5a69-109">To perform the procedure in this topic, you must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span> <span data-ttu-id="f5a69-110">如需詳細的權限的相關資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="f5a69-110">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-tracking-for-a-receive-port"></a><span data-ttu-id="f5a69-111">設定追蹤接收埠</span><span class="sxs-lookup"><span data-stu-id="f5a69-111">To configure tracking for a receive port</span></span>  
  
1.  <span data-ttu-id="f5a69-112">按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="f5a69-112">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="f5a69-113">在主控台樹狀結構中，展開 BizTalk 群組，並展開您要為其設定接收埠追蹤的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f5a69-113">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure tracking for a receive port.</span></span>  
  
3.  <span data-ttu-id="f5a69-114">按一下**接收埠**，以滑鼠右鍵按一下接收埠，然後按一下**追蹤**。</span><span class="sxs-lookup"><span data-stu-id="f5a69-114">Click **Receive Ports**, right-click the receive port and click **Tracking**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f5a69-115">啟用接收埠的訊息內文追蹤之前，請確定是否要完全追蹤接收埠；它可能會是負擔。</span><span class="sxs-lookup"><span data-stu-id="f5a69-115">Before enabling the message body tracking on a receive port, ensure if you want to track the receive port at all; it could be an overhead.</span></span> <span data-ttu-id="f5a69-116">例如，接收管線 RcvPipe 用在不同的接收埠的數個接收位置上。</span><span class="sxs-lookup"><span data-stu-id="f5a69-116">For example, a receive pipeline RcvPipe is used at several receive locations in different receive ports.</span></span> <span data-ttu-id="f5a69-117">如果您啟用訊息內文追蹤 rcvpipe 的選項，它會導致訊息內文追蹤所有接收位置，您可能不想要的。</span><span class="sxs-lookup"><span data-stu-id="f5a69-117">If you enable the message body tracking option on RcvPipe, it leads to message body tracking on all the receive locations, which you might not want to do.</span></span> <span data-ttu-id="f5a69-118">因此，設定訊息內文追蹤接收埠。</span><span class="sxs-lookup"><span data-stu-id="f5a69-118">Hence, set the message body tracking on receive ports as per your requirement.</span></span>  
  
4.  <span data-ttu-id="f5a69-119">下表中所述，設定您要的追蹤選項，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f5a69-119">Configure the tracking options you want, as described in the following table, and then click **OK**.</span></span>  
  
    |<span data-ttu-id="f5a69-120">使用</span><span class="sxs-lookup"><span data-stu-id="f5a69-120">Use this</span></span>|<span data-ttu-id="f5a69-121">動作</span><span class="sxs-lookup"><span data-stu-id="f5a69-121">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f5a69-122">**追蹤訊息內文-連接埠處理前要求訊息**</span><span class="sxs-lookup"><span data-stu-id="f5a69-122">**Track Message Bodies - Request message before port processing**</span></span>|<span data-ttu-id="f5a69-123">選取此核取方塊，可讓您在接收訊息之前儲存和追蹤訊息內容。</span><span class="sxs-lookup"><span data-stu-id="f5a69-123">Select this check box to save and track message content before the message is received.</span></span>|  
    |<span data-ttu-id="f5a69-124">**追蹤訊息內文-連接埠處理後要求訊息**</span><span class="sxs-lookup"><span data-stu-id="f5a69-124">**Track Message Bodies - Request message after port processing**</span></span>|<span data-ttu-id="f5a69-125">選取此核取方塊，可讓您在接收訊息之後儲存和追蹤訊息內容。</span><span class="sxs-lookup"><span data-stu-id="f5a69-125">Select this check box to save and track message content after the message is received.</span></span>|  
    |||  
    |||  
    |<span data-ttu-id="f5a69-126">**追蹤訊息屬性-連接埠處理前要求訊息**</span><span class="sxs-lookup"><span data-stu-id="f5a69-126">**Track Message Properties - Request message before port processing**</span></span>|<span data-ttu-id="f5a69-127">選取此核取方塊，可追蹤輸入訊息的升級屬性。</span><span class="sxs-lookup"><span data-stu-id="f5a69-127">Select this check box to track the promoted properties of an inbound message.</span></span>|  
    |<span data-ttu-id="f5a69-128">**追蹤訊息屬性-連接埠處理後要求訊息**</span><span class="sxs-lookup"><span data-stu-id="f5a69-128">**Track Message Properties - Request message after port processing**</span></span>|<span data-ttu-id="f5a69-129">若您想要追蹤輸出訊息的升級屬性，請選取此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f5a69-129">Select this check box if you want to track the promoted properties of an outbound message.</span></span>|  
    |||  
    |||  
  
## <a name="see-also"></a><span data-ttu-id="f5a69-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5a69-130">See Also</span></span>  
 [<span data-ttu-id="f5a69-131">管理接收埠</span><span class="sxs-lookup"><span data-stu-id="f5a69-131">Managing Receive Ports</span></span>](../core/managing-receive-ports.md)