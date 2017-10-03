---
title: "如何設定傳送埠的輸入的對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [send ports], inbound maps
- configuring, send ports
- send ports, inbound maps
- configuring, inbound maps
- managing [send ports], configuring
- send ports, configuring
ms.assetid: 213c66ba-928f-4c00-9a87-f45eaa9f7dca
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04179476795e7b7c224b3db1b5e83c8a87f68b72
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-inbound-maps-for-a-send-port"></a><span data-ttu-id="92b83-102">如何設定傳送埠的輸入對應</span><span class="sxs-lookup"><span data-stu-id="92b83-102">How to Configure Inbound Maps for a Send Port</span></span>
<span data-ttu-id="92b83-103">本主題描述如何使用 BizTalk Server 管理主控台來設定傳送埠的輸入對應。</span><span class="sxs-lookup"><span data-stu-id="92b83-103">This topic describes how to use the BizTalk Server Administration console to configure inbound maps for a send port.</span></span> <span data-ttu-id="92b83-104">輸入對應只能搭配動態或靜態請求-回應傳送埠使用。</span><span class="sxs-lookup"><span data-stu-id="92b83-104">Inbound maps are used only with dynamic or static solicit-response send ports.</span></span> <span data-ttu-id="92b83-105">您可以使用對應將 XSL 轉換套用到連接埠接收的回應訊息，無需透過協調流程處理訊息。</span><span class="sxs-lookup"><span data-stu-id="92b83-105">You use a map to apply an XSL transformation to a response message received by the port without processing the message through an orchestration.</span></span> <span data-ttu-id="92b83-106">您可以新增輸入對應、移除對應，或將現有對應變更為不同的對應。</span><span class="sxs-lookup"><span data-stu-id="92b83-106">You can add an inbound map, remove a map, or change an existing map to a different one.</span></span> <span data-ttu-id="92b83-107">您可以新增一個以上的對應到傳送埠，但是每一個對應都必須有唯一的來源結構描述。</span><span class="sxs-lookup"><span data-stu-id="92b83-107">You can add more than one map to a send port, but each map must have a unique source schema.</span></span> <span data-ttu-id="92b83-108">如需對應的背景資訊，請參閱[對應](../core/maps.md)。</span><span class="sxs-lookup"><span data-stu-id="92b83-108">For background information about maps, see [Maps](../core/maps.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92b83-109">應用程式開發人員可以使用此主題中的程序，在開發程序中設定對應。</span><span class="sxs-lookup"><span data-stu-id="92b83-109">The application developer can configure maps during the development process by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="92b83-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="92b83-110">Prerequisites</span></span>  
 <span data-ttu-id="92b83-111">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="92b83-111">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="92b83-112">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="92b83-112">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-inbound-maps-for-a-send-port"></a><span data-ttu-id="92b83-113">設定傳送埠的輸入對應</span><span class="sxs-lookup"><span data-stu-id="92b83-113">To configure inbound maps for a send port</span></span>  
  
1.  <span data-ttu-id="92b83-114">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="92b83-114">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="92b83-115">在主控台樹狀目錄中，展開您要為傳送埠設定輸入對應的 BizTalk 群組與 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="92b83-115">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure an inbound map for a send port.</span></span>  
  
3.  <span data-ttu-id="92b83-116">展開**傳送埠**，以滑鼠右鍵按一下傳送埠，按一下**屬性**，然後按一下 **輸入對應**。</span><span class="sxs-lookup"><span data-stu-id="92b83-116">Expand **Send Ports**, right-click the send port, click **Properties**, and then click **Inbound Maps**.</span></span>  
  
4.  <span data-ttu-id="92b83-117">下表中所述設定輸入的對應，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="92b83-117">Configure the inbound maps as described in the following table, and then click **OK**.</span></span> <span data-ttu-id="92b83-118">視需要重複新增或移除多個對應。</span><span class="sxs-lookup"><span data-stu-id="92b83-118">Repeat as needed to add or remove multiple maps.</span></span>  
  
    |<span data-ttu-id="92b83-119">使用</span><span class="sxs-lookup"><span data-stu-id="92b83-119">Use this</span></span>|<span data-ttu-id="92b83-120">動作</span><span class="sxs-lookup"><span data-stu-id="92b83-120">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="92b83-121">**移除**</span><span class="sxs-lookup"><span data-stu-id="92b83-121">**Remove**</span></span>|<span data-ttu-id="92b83-122">按一下以移除選取的對應。</span><span class="sxs-lookup"><span data-stu-id="92b83-122">Click to remove the selected map.</span></span>|  
    |<span data-ttu-id="92b83-123">**來源文件**</span><span class="sxs-lookup"><span data-stu-id="92b83-123">**Source Document**</span></span>|<span data-ttu-id="92b83-124">從下拉式清單選取輸入對應的來源文件。</span><span class="sxs-lookup"><span data-stu-id="92b83-124">From the drop-down list, select the source document for the inbound map.</span></span>|  
    |<span data-ttu-id="92b83-125">**對應**</span><span class="sxs-lookup"><span data-stu-id="92b83-125">**Map**</span></span>|<span data-ttu-id="92b83-126">從下拉式清單選取與來源及目標文件關聯的對應。</span><span class="sxs-lookup"><span data-stu-id="92b83-126">From the drop-down list, select the map to associate with the source and target documents.</span></span>|  
    |<span data-ttu-id="92b83-127">**目標文件**</span><span class="sxs-lookup"><span data-stu-id="92b83-127">**Target Document**</span></span>|<span data-ttu-id="92b83-128">從下拉式清單選取輸入對應的目標文件。</span><span class="sxs-lookup"><span data-stu-id="92b83-128">From the drop-down list, select the target document for the inbound map.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92b83-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92b83-129">See Also</span></span>  
 <span data-ttu-id="92b83-130">[建立和設定傳送埠](../core/creating-and-configuring-send-ports.md) </span><span class="sxs-lookup"><span data-stu-id="92b83-130">[Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md) </span></span>  
 [<span data-ttu-id="92b83-131">管理對應</span><span class="sxs-lookup"><span data-stu-id="92b83-131">Managing Maps</span></span>](../core/managing-maps.md)