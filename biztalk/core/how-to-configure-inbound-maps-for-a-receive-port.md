---
title: "如何設定的輸入的對應接收埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [receive ports], configuring
- configuring, maps
- configuring, inbound maps
- maps, configuring
- receive ports, configuring
- receive ports, inbound maps
- configuring, receive ports
- maps, inbound
- managing [receive ports], inbound maps
ms.assetid: b7448b39-f024-4353-818b-f753c2d60751
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5275b2701d42240df06810ef43563ca4a200151f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-inbound-maps-for-a-receive-port"></a><span data-ttu-id="59c93-102">如何設定接收埠的輸入對應</span><span class="sxs-lookup"><span data-stu-id="59c93-102">How to Configure Inbound Maps for a Receive Port</span></span>
<span data-ttu-id="59c93-103">本主題描述如何使用 BizTalk Server 管理主控台來設定接收埠的輸入對應。</span><span class="sxs-lookup"><span data-stu-id="59c93-103">This topic describes how to use the BizTalk Server Administration console to configure inbound maps for a receive port.</span></span> <span data-ttu-id="59c93-104">您會使用輸入對應，將輸入訊息從一個結構描述轉換至其他結構描述；例如，將接收自夥伴的訊息轉換成可供公司使用的結構描述。</span><span class="sxs-lookup"><span data-stu-id="59c93-104">You use inbound maps to transform inbound messages from one schema to another; for example to transform messages received from a partner into a schema that your company uses.</span></span>  
  
 <span data-ttu-id="59c93-105">您可以使用對應，將 XSL 轉換套用至接收埠傳送的訊息，而無需透過協調流程處理訊息。</span><span class="sxs-lookup"><span data-stu-id="59c93-105">You use a map to apply an XSL transformation to a message sent by the receive port without processing the message through an orchestration.</span></span> <span data-ttu-id="59c93-106">您可以新增輸入對應、移除對應，或將現有對應變更為不同的對應。</span><span class="sxs-lookup"><span data-stu-id="59c93-106">You can add an inbound map, remove a map, or change an existing map to a different one.</span></span> <span data-ttu-id="59c93-107">您可以新增一個以上的對應到接收埠，但每一個對應都必須有唯一的來源結構描述。</span><span class="sxs-lookup"><span data-stu-id="59c93-107">You can add more than one map to a receive port, but each map must have a unique source schema.</span></span> <span data-ttu-id="59c93-108">如需對應的背景資訊，請參閱[對應](../core/maps.md)。</span><span class="sxs-lookup"><span data-stu-id="59c93-108">For background information about maps, see [Maps](../core/maps.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59c93-109">應用程式開發人員可以使用此主題中的程序，在開發程序中設定接收埠的對應。</span><span class="sxs-lookup"><span data-stu-id="59c93-109">The application developer can configure maps for a receive port during the development process by using the procedure in this.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="59c93-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="59c93-110">Prerequisites</span></span>  
 <span data-ttu-id="59c93-111">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="59c93-111">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="59c93-112">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="59c93-112">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-inbound-maps-for-a-receive-port"></a><span data-ttu-id="59c93-113">設定接收埠的輸入對應</span><span class="sxs-lookup"><span data-stu-id="59c93-113">To configure inbound maps for a receive port</span></span>  
  
1.  <span data-ttu-id="59c93-114">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="59c93-114">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="59c93-115">在主控台樹狀結構中，展開您要為其設定接收埠輸入對應的 BizTalk 群組和 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="59c93-115">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure an inbound maps for a receive port.</span></span>  
  
3.  <span data-ttu-id="59c93-116">按一下**接收埠**，以滑鼠右鍵按一下接收埠，按一下**屬性**，然後按一下 **輸入對應**。</span><span class="sxs-lookup"><span data-stu-id="59c93-116">Click **Receive Ports**, right-click the receive port, click **Properties**, and then click **Inbound Maps**.</span></span>  
  
4.  <span data-ttu-id="59c93-117">下表中所述設定輸入的對應，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="59c93-117">Configure the inbound maps as described in the following table, and then click **OK**.</span></span>  
  
    |<span data-ttu-id="59c93-118">使用</span><span class="sxs-lookup"><span data-stu-id="59c93-118">Use this</span></span>|<span data-ttu-id="59c93-119">動作</span><span class="sxs-lookup"><span data-stu-id="59c93-119">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="59c93-120">**移除**</span><span class="sxs-lookup"><span data-stu-id="59c93-120">**Remove**</span></span>|<span data-ttu-id="59c93-121">按一下以移除選取的對應。</span><span class="sxs-lookup"><span data-stu-id="59c93-121">Click to remove the selected map.</span></span>|  
    |<span data-ttu-id="59c93-122">**來源文件**</span><span class="sxs-lookup"><span data-stu-id="59c93-122">**Source Document**</span></span>|<span data-ttu-id="59c93-123">從下拉式清單選取要與此連接埠一起使用的來源結構描述。</span><span class="sxs-lookup"><span data-stu-id="59c93-123">From the drop-down list, select the source schema to use with this port.</span></span>|  
    |<span data-ttu-id="59c93-124">**對應**</span><span class="sxs-lookup"><span data-stu-id="59c93-124">**Map**</span></span>|<span data-ttu-id="59c93-125">從下拉式清單選取您要與此連接埠產生關聯的對應。</span><span class="sxs-lookup"><span data-stu-id="59c93-125">From the drop-down list, select the map you want to associate with this port.</span></span>|  
    |<span data-ttu-id="59c93-126">**目標文件**</span><span class="sxs-lookup"><span data-stu-id="59c93-126">**Target Document**</span></span>|<span data-ttu-id="59c93-127">從下拉式清單選取要與此連接埠一起使用的目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="59c93-127">From the drop-down list, select the destination schema to use with this port.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59c93-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59c93-128">See Also</span></span>  
 <span data-ttu-id="59c93-129">[管理接收埠](../core/managing-receive-ports.md) </span><span class="sxs-lookup"><span data-stu-id="59c93-129">[Managing Receive Ports](../core/managing-receive-ports.md) </span></span>  
 [<span data-ttu-id="59c93-130">管理對應</span><span class="sxs-lookup"><span data-stu-id="59c93-130">Managing Maps</span></span>](../core/managing-maps.md)