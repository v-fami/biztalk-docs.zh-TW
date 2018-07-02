---
title: 如何編輯屬性的接收位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [receive locations], properties
- managing [receive locations], editing
- receive locations, properties
- receive locations, editing
- editing, receive locations
- editing, properties
ms.assetid: 2b622050-a875-4896-bed6-65ca39a26dd3
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bace802ee40c98cd6ffee956c967d01fcdb7994
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985927"
---
# <a name="how-to-edit-the-properties-of-a-receive-location"></a><span data-ttu-id="539a0-102">如何編輯接收位置的屬性</span><span class="sxs-lookup"><span data-stu-id="539a0-102">How to Edit the Properties of a Receive Location</span></span>
<span data-ttu-id="539a0-103">本主題描述如何使用 [BizTalk Server 管理主控台] 編輯現有接收位置的屬性。</span><span class="sxs-lookup"><span data-stu-id="539a0-103">This topic describes how to use the BizTalk Server Administration console to edit properties of an existing receive location.</span></span> <span data-ttu-id="539a0-104">如需建立接收位置的指示，請參閱 <<c0> [ 如何建立接收位置](../core/how-to-create-a-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="539a0-104">For instructions on creating a receive location, see [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="539a0-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="539a0-105">Prerequisites</span></span>  
 <span data-ttu-id="539a0-106">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="539a0-106">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="539a0-107">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="539a0-107">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-edit-the-properties-of-a-receive-location"></a><span data-ttu-id="539a0-108">編輯接收位置的屬性</span><span class="sxs-lookup"><span data-stu-id="539a0-108">To edit the properties of a receive location</span></span>  
  
1. <span data-ttu-id="539a0-109">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="539a0-109">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="539a0-110">在主控台樹狀目錄中，展開 BizTalk 群組和 BizTalk 應用程式，您要編輯的接收位置屬性，然後按一下**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="539a0-110">In the console tree, expand the BizTalk group and the BizTalk application for which you want to edit the properties of a receive location and then click **Receive Locations**.</span></span>  
  
3. <span data-ttu-id="539a0-111">在右窗格中，以滑鼠右鍵按一下接收位置，然後**屬性**。</span><span class="sxs-lookup"><span data-stu-id="539a0-111">In the right pane, right-click the receive location, and then click **Properties**.</span></span>  
  
4. <span data-ttu-id="539a0-112">在 [**接收位置屬性**] 視窗中，編輯一或多個下列的屬性，然後按一下**確定**:</span><span class="sxs-lookup"><span data-stu-id="539a0-112">In the **Receive Location Properties** window, edit one or more of the following properties, and then click **OK**:</span></span>  
  
   |<span data-ttu-id="539a0-113">使用</span><span class="sxs-lookup"><span data-stu-id="539a0-113">Use this</span></span>|<span data-ttu-id="539a0-114">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="539a0-114">To do this</span></span>|  
   |--------------|----------------|  
   |<span data-ttu-id="539a0-115">**名稱**</span><span class="sxs-lookup"><span data-stu-id="539a0-115">**Name**</span></span>|<span data-ttu-id="539a0-116">輸入接收位置的名稱。</span><span class="sxs-lookup"><span data-stu-id="539a0-116">Type the name of the receive location.</span></span>|  
   |<span data-ttu-id="539a0-117">**型別**</span><span class="sxs-lookup"><span data-stu-id="539a0-117">**Type**</span></span>|<span data-ttu-id="539a0-118">從下拉式清單選取傳輸類型或傳輸通訊協定。</span><span class="sxs-lookup"><span data-stu-id="539a0-118">From the drop-down list, select the transport type, or transport protocol.</span></span> <span data-ttu-id="539a0-119">若您變更傳輸類型，則必須設定如下所描述的傳輸屬性。</span><span class="sxs-lookup"><span data-stu-id="539a0-119">If you change the transport type, you must configure transport properties, as described next.</span></span>|  
   |<span data-ttu-id="539a0-120">**設定**</span><span class="sxs-lookup"><span data-stu-id="539a0-120">**Configure**</span></span>|<span data-ttu-id="539a0-121">選取傳輸類型之後，請按一下**設定**顯示**傳輸屬性**對話方塊設定配接器接收位置屬性。</span><span class="sxs-lookup"><span data-stu-id="539a0-121">After you select the transport type, click **Configure** to display the **Transport Properties** dialog box and configure adapter properties for the receive location.</span></span> <span data-ttu-id="539a0-122">如需指示，請按一下**協助**在對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="539a0-122">For instructions, click **Help** in the dialog box.</span></span> <span data-ttu-id="539a0-123">如需設定配接器，每種類型的詳細資訊，請參閱底下的適當主題[使用配接器](../core/using-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="539a0-123">For details on configuring each type of adapter, see the appropriate topic under [Using Adapters](../core/using-adapters.md).</span></span>|  
   |<span data-ttu-id="539a0-124">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="539a0-124">**Receive handler**</span></span>|<span data-ttu-id="539a0-125">從下拉式清單選取 BizTalk Server 主控件的執行個體 (接收位置會在其上執行)。</span><span class="sxs-lookup"><span data-stu-id="539a0-125">From the drop-down list, select the instance of the BizTalk Server host on which the receive location will run.</span></span> <span data-ttu-id="539a0-126">接收處理常式必須在此主控件上執行。</span><span class="sxs-lookup"><span data-stu-id="539a0-126">The receive handler must be running on this host.</span></span>|  
   |<span data-ttu-id="539a0-127">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="539a0-127">**Receive pipeline**</span></span>|<span data-ttu-id="539a0-128">從下拉式清單選取接收管線，用來在此接收位置接收訊息。</span><span class="sxs-lookup"><span data-stu-id="539a0-128">From the drop-down list, select the receive pipeline to use to receive messages at this receive location.</span></span>|  
   |<span data-ttu-id="539a0-129">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="539a0-129">**Send pipeline**</span></span>|<span data-ttu-id="539a0-130">從下拉式清單選取傳送管線，用來從此接收位置傳送回應。</span><span class="sxs-lookup"><span data-stu-id="539a0-130">From the drop-down list, select the send pipeline to use to send responses from this receive location.</span></span> <span data-ttu-id="539a0-131">只有和要求-回應接收埠相關聯的接收位置才能使用此清單。</span><span class="sxs-lookup"><span data-stu-id="539a0-131">This list is available only for a receive location associated with a request-response receive port.</span></span>|  
   |<span data-ttu-id="539a0-132">**將此主要位置**</span><span class="sxs-lookup"><span data-stu-id="539a0-132">**Make this the primary location**</span></span>|<span data-ttu-id="539a0-133">若接收埠有一個以上的接收位置，而且必須將連接埠傳遞給需要將訊息傳送至您組織的另一個實體時 (例如，商務合夥人)，若想要以此接收位置代表接收埠，請選取此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="539a0-133">Select this check box if you have more than one receive location for a receive port and you want this receive location to represent the receive port when the port needs to be passed to another entity, such as a business partner, that needs to send messages to your organization.</span></span> <span data-ttu-id="539a0-134">建立的第一個接收位置會自動選取為主要接收位置。</span><span class="sxs-lookup"><span data-stu-id="539a0-134">The first receive location created is automatically selected as the primary receive location.</span></span> <span data-ttu-id="539a0-135">除非您指派其他接收位置做為主要位置，否則此屬性會繼續處於選取狀態而且無法使用。</span><span class="sxs-lookup"><span data-stu-id="539a0-135">This property remains selected and unavailable until you designate a different receive location as the primary.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="539a0-136">如果您變更或修改接收位置，請重新啟動與所修改接收位置對應的外掛式主控件工作者處理序。</span><span class="sxs-lookup"><span data-stu-id="539a0-136">In case you change or modify Receive location, restart the Isolated Host Worker Processes corresponding to the modified receive location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="539a0-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="539a0-137">See Also</span></span>  
 [<span data-ttu-id="539a0-138">管理接收位置</span><span class="sxs-lookup"><span data-stu-id="539a0-138">Managing Receive Locations</span></span>](../core/managing-receive-locations.md)