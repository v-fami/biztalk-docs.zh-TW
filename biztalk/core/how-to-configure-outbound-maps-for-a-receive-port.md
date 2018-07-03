---
title: 如何設定輸出對應接收埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [receive ports], configuring
- maps, outbound
- configuring, maps
- managing [receive ports], outbound maps
- maps, configuring
- receive ports, configuring
- configuring, receive ports
- receive ports, outbound maps
ms.assetid: 01a864a1-9e8c-4b82-9d03-91be09d556da
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c74fcc259b833a64a480bbe88f4cc0273d2a83c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023604"
---
# <a name="how-to-configure-outbound-maps-for-a-receive-port"></a><span data-ttu-id="411fd-102">如何設定接收埠的輸出對應</span><span class="sxs-lookup"><span data-stu-id="411fd-102">How to Configure Outbound Maps for a Receive Port</span></span>
<span data-ttu-id="411fd-103">本主題描述如何使用 BizTalk Server 管理主控台來設定接收埠的輸出對應。</span><span class="sxs-lookup"><span data-stu-id="411fd-103">This topic describes how to use the BizTalk Server Administration console to configure outbound maps for a receive port.</span></span> <span data-ttu-id="411fd-104">您可以與要求-回應接收埠一起使用輸出對應，將輸出訊息從一個結構描述轉換為另一個結構描述；例如，將您公司使用的訊息轉換為夥伴公司使用的結構描述。</span><span class="sxs-lookup"><span data-stu-id="411fd-104">You can use outbound maps with request-response receive ports to transform outbound messages from one schema to another; for example to transform messages that your company uses into a schema that a partner uses.</span></span>  
  
 <span data-ttu-id="411fd-105">您可以使用對應將 XSL 轉換套用到接收埠所傳送的回應訊息，無需透過協調流程處理訊息。</span><span class="sxs-lookup"><span data-stu-id="411fd-105">You use a map to apply an XSL transformation to a response message sent by the receive port without processing the message through an orchestration.</span></span> <span data-ttu-id="411fd-106">您可以新增輸出對應、移除對應，或將現有對應變更為不同的對應。</span><span class="sxs-lookup"><span data-stu-id="411fd-106">You can add an outbound map, remove a map, or change an existing map to a different one.</span></span> <span data-ttu-id="411fd-107">您可以新增一個以上的對應到接收埠，但每一個對應都必須有唯一的來源結構描述。</span><span class="sxs-lookup"><span data-stu-id="411fd-107">You can add more than one map to a receive port, but each map must have a unique source schema.</span></span> <span data-ttu-id="411fd-108">如需地圖的背景資訊，請參閱 <<c0> [ 對應](../core/maps.md)。</span><span class="sxs-lookup"><span data-stu-id="411fd-108">For background information about maps, see [Maps](../core/maps.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="411fd-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="411fd-109">Prerequisites</span></span>  
 <span data-ttu-id="411fd-110">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="411fd-110">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="411fd-111">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="411fd-111">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-outbound-maps-for-a-receive-port"></a><span data-ttu-id="411fd-112">設定接收埠的輸出對應</span><span class="sxs-lookup"><span data-stu-id="411fd-112">To configure outbound maps for a receive port</span></span>  
  
1. <span data-ttu-id="411fd-113">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="411fd-113">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="411fd-114">在主控台樹狀目錄中，展開 BizTalk 群組，並展開您要為其設定接收埠輸出對應的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="411fd-114">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure outbound maps for a receive port.</span></span>  
  
3. <span data-ttu-id="411fd-115">依序展開**接收連接埠**，以滑鼠右鍵按一下接收埠，按一下**屬性**，然後按一下**輸出對應**。</span><span class="sxs-lookup"><span data-stu-id="411fd-115">Expand **Receive Ports**, right-click the receive port, click **Properties**, and then click **Outbound Maps**.</span></span>  
  
4. <span data-ttu-id="411fd-116">下表中所述，設定輸出對應，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="411fd-116">Configure the outbound maps as described in the following table, and then click **OK**.</span></span>  
  
   |<span data-ttu-id="411fd-117">使用</span><span class="sxs-lookup"><span data-stu-id="411fd-117">Use this</span></span>|<span data-ttu-id="411fd-118">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="411fd-118">To do this</span></span>|  
   |--------------|----------------|  
   |<span data-ttu-id="411fd-119">**移除**</span><span class="sxs-lookup"><span data-stu-id="411fd-119">**Remove**</span></span>|<span data-ttu-id="411fd-120">按一下以移除選取的對應。</span><span class="sxs-lookup"><span data-stu-id="411fd-120">Click to remove the selected map.</span></span>|  
   |<span data-ttu-id="411fd-121">**來源文件**</span><span class="sxs-lookup"><span data-stu-id="411fd-121">**Source Document**</span></span>|<span data-ttu-id="411fd-122">從下拉式清單選取要與此連接埠一起使用的來源結構描述。</span><span class="sxs-lookup"><span data-stu-id="411fd-122">From the drop-down list, select the source schema to use with this port.</span></span>|  
   |<span data-ttu-id="411fd-123">**對應**</span><span class="sxs-lookup"><span data-stu-id="411fd-123">**Map**</span></span>|<span data-ttu-id="411fd-124">從下拉式清單選取您要與此連接埠產生關聯的對應。</span><span class="sxs-lookup"><span data-stu-id="411fd-124">From the drop-down list, select the map you want to associate with this port.</span></span>|  
   |<span data-ttu-id="411fd-125">**目標文件**</span><span class="sxs-lookup"><span data-stu-id="411fd-125">**Target Document**</span></span>|<span data-ttu-id="411fd-126">從下拉式清單選取要與此連接埠一起使用的目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="411fd-126">From the drop-down list, select the destination schema to use with this port.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="411fd-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="411fd-127">See Also</span></span>  
 <span data-ttu-id="411fd-128">[管理接收埠](../core/managing-receive-ports.md) </span><span class="sxs-lookup"><span data-stu-id="411fd-128">[Managing Receive Ports](../core/managing-receive-ports.md) </span></span>  
 [<span data-ttu-id="411fd-129">管理對應</span><span class="sxs-lookup"><span data-stu-id="411fd-129">Managing Maps</span></span>](../core/managing-maps.md)