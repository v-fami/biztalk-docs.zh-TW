---
title: 如何設定傳送埠的輸出對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, outbound maps
- configuring, send ports
- managing [send ports], configuring
- send ports, outbound maps
- send ports, configuring
- managing [send ports], outbound maps
ms.assetid: 9f5f5504-5a7f-4b21-9a65-91dce9d35890
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51d3feaba929d1a7585a8e7c3b29f6868dcc9dc7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248086"
---
# <a name="how-to-configure-outbound-maps-for-a-send-port"></a><span data-ttu-id="6b0ea-102">如何設定傳送埠的輸出對應</span><span class="sxs-lookup"><span data-stu-id="6b0ea-102">How to Configure Outbound Maps for a Send Port</span></span>
<span data-ttu-id="6b0ea-103">本主題描述如何使用 BizTalk Server 管理主控台來設定傳送埠的輸出對應。</span><span class="sxs-lookup"><span data-stu-id="6b0ea-103">This topic describes how to configure outbound maps for a send port by using the BizTalk Server Administration console.</span></span> <span data-ttu-id="6b0ea-104">您將會使用對應將 XSL 轉換套用至傳送埠傳所傳送的訊息，而無需協調流程處理訊息。</span><span class="sxs-lookup"><span data-stu-id="6b0ea-104">You use a map to apply an XSL transformation to a message sent by the send port without processing the message through an orchestration.</span></span> <span data-ttu-id="6b0ea-105">您可以新增輸出對應、移除對應，或將現有對應變更為不同的對應。</span><span class="sxs-lookup"><span data-stu-id="6b0ea-105">You can add an outbound map, remove a map, or change an existing map to a different one.</span></span> <span data-ttu-id="6b0ea-106">您可以新增一個以上的對應到傳送埠，但是每一個對應都必須有唯一的來源結構描述。</span><span class="sxs-lookup"><span data-stu-id="6b0ea-106">You can add more than one map to a send port, but each map must have a unique source schema.</span></span> <span data-ttu-id="6b0ea-107">如需對應的背景資訊，請參閱[對應](../core/maps.md)。</span><span class="sxs-lookup"><span data-stu-id="6b0ea-107">For background information about maps, see [Maps](../core/maps.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6b0ea-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="6b0ea-108">Prerequisites</span></span>  
 <span data-ttu-id="6b0ea-109">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="6b0ea-109">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="6b0ea-110">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="6b0ea-110">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-outbound-maps-for-a-send-port"></a><span data-ttu-id="6b0ea-111">設定傳送埠的輸出對應</span><span class="sxs-lookup"><span data-stu-id="6b0ea-111">To configure outbound maps for a send port</span></span>  
  
1.  <span data-ttu-id="6b0ea-112">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="6b0ea-112">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="6b0ea-113">在主控台樹狀結構中，展開您要為其設定傳送埠輸出對應的 BizTalk 群組與 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="6b0ea-113">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure the outbound maps for a send port.</span></span>  
  
3.  <span data-ttu-id="6b0ea-114">展開**傳送埠**，以滑鼠右鍵按一下傳送埠，按一下**屬性**，然後按一下 **輸出對應**。</span><span class="sxs-lookup"><span data-stu-id="6b0ea-114">Expand **Send Ports**, right-click the send port, click **Properties**, and then click **Outbound Maps**.</span></span>  
  
4.  <span data-ttu-id="6b0ea-115">下表中所述，設定輸出對應，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6b0ea-115">Configure outbound maps as described in the following table, and then click **OK**.</span></span> <span data-ttu-id="6b0ea-116">視需要重複新增或移除多個對應。</span><span class="sxs-lookup"><span data-stu-id="6b0ea-116">Repeat as needed to add or remove multiple maps.</span></span>  
  
    |<span data-ttu-id="6b0ea-117">使用</span><span class="sxs-lookup"><span data-stu-id="6b0ea-117">Use this</span></span>|<span data-ttu-id="6b0ea-118">動作</span><span class="sxs-lookup"><span data-stu-id="6b0ea-118">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="6b0ea-119">**移除**</span><span class="sxs-lookup"><span data-stu-id="6b0ea-119">**Remove**</span></span>|<span data-ttu-id="6b0ea-120">按一下以移除選取的對應。</span><span class="sxs-lookup"><span data-stu-id="6b0ea-120">Click to remove the selected map.</span></span>|  
    |<span data-ttu-id="6b0ea-121">**輸出對應-來源文件**</span><span class="sxs-lookup"><span data-stu-id="6b0ea-121">**Outbound maps - Source Document**</span></span>|<span data-ttu-id="6b0ea-122">從下拉式清單選取輸出對應的來源文件。</span><span class="sxs-lookup"><span data-stu-id="6b0ea-122">From the drop-down list, select the source document for the outbound map.</span></span>|  
    |<span data-ttu-id="6b0ea-123">**輸出對應-對應**</span><span class="sxs-lookup"><span data-stu-id="6b0ea-123">**Outbound maps - Map**</span></span>|<span data-ttu-id="6b0ea-124">從下拉式清單選取與來源及目標文件關聯的對應。</span><span class="sxs-lookup"><span data-stu-id="6b0ea-124">From the drop-down list, select the map to associate with the source and target documents.</span></span>|  
    |<span data-ttu-id="6b0ea-125">**輸出對應-目標文件**</span><span class="sxs-lookup"><span data-stu-id="6b0ea-125">**Outbound maps - Target Document**</span></span>|<span data-ttu-id="6b0ea-126">從下拉式清單選取輸出對應的目標文件。</span><span class="sxs-lookup"><span data-stu-id="6b0ea-126">From the drop-down list, select the target document for the outbound map.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6b0ea-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b0ea-127">See Also</span></span>  
 <span data-ttu-id="6b0ea-128">[建立和設定傳送埠](../core/creating-and-configuring-send-ports.md) </span><span class="sxs-lookup"><span data-stu-id="6b0ea-128">[Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md) </span></span>  
 [<span data-ttu-id="6b0ea-129">管理對應</span><span class="sxs-lookup"><span data-stu-id="6b0ea-129">Managing Maps</span></span>](../core/managing-maps.md)