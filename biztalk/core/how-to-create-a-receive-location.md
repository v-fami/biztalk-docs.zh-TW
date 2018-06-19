---
title: 如何建立接收位置 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.admin.procedure.createreceivelocation
helpviewer_keywords:
- receive locations, creating
- managing [receive locations], creating
- creating, receive locations
ms.assetid: ec0202cf-0e69-4ae2-aba6-8cd2c3c77e82
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe82afdc62a7ba2c10087c78a6a24c1722e5812a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249686"
---
# <a name="how-to-create-a-receive-location"></a><span data-ttu-id="6c496-102">如何建立接收位置</span><span class="sxs-lookup"><span data-stu-id="6c496-102">How to Create a Receive Location</span></span>
<span data-ttu-id="6c496-103">本主題描述如何使用 BizTalk Server 管理主控台建立新的接收位置，並指定該位置所屬的接收埠。</span><span class="sxs-lookup"><span data-stu-id="6c496-103">This topic describes how to use the BizTalk Server Administration console to create a new receive location and specify the receive port to which it belongs.</span></span> <span data-ttu-id="6c496-104">接收位置是輸入訊息送達的位址，也是處理在該位址所接收之訊息的傳訊管線。</span><span class="sxs-lookup"><span data-stu-id="6c496-104">A receive location is an address where inbound messages arrive as well as the messaging pipeline that processes messages received at that address.</span></span>  
  
 <span data-ttu-id="6c496-105">在建立接收位置之前，在這個應用程式中必須已經有接收埠存在 (該應用程式的類型要與所建立之接收位置相同)。</span><span class="sxs-lookup"><span data-stu-id="6c496-105">Before you can create a receive location, a receive port must already exist in this application that of the same type as the receive location you want to create.</span></span> <span data-ttu-id="6c496-106">如需建立接收埠的指示，請參閱[如何建立接收埠](../core/how-to-create-a-receive-port.md)。</span><span class="sxs-lookup"><span data-stu-id="6c496-106">For instructions on creating a receive port, see [How to Create a Receive Port](../core/how-to-create-a-receive-port.md).</span></span>  
  
 <span data-ttu-id="6c496-107">您可以建立下列類型的接收位置：</span><span class="sxs-lookup"><span data-stu-id="6c496-107">You can create the following types of receive locations:</span></span>  
  
-   <span data-ttu-id="6c496-108">單向：用在應用程式放置訊息但不同步等候回覆時</span><span class="sxs-lookup"><span data-stu-id="6c496-108">One-way — used for applications that drop off a message and do not wait synchronously for a reply</span></span>  
  
-   <span data-ttu-id="6c496-109">要求-回應：用在應用程式需要訊息的回應時</span><span class="sxs-lookup"><span data-stu-id="6c496-109">Request-response — used with applications that require a response to a message</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c496-110">應用程式開發人員可以使用此主題中的程序，在開發程序中建立接收位置。</span><span class="sxs-lookup"><span data-stu-id="6c496-110">The application developer can create a receive location during the development process by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6c496-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="6c496-111">Prerequisites</span></span>  
 <span data-ttu-id="6c496-112">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="6c496-112">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="6c496-113">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="6c496-113">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span> <span data-ttu-id="6c496-114">此外，您必須擁有適當的 SSO 資料庫權限。</span><span class="sxs-lookup"><span data-stu-id="6c496-114">In addition, you need to have appropriate permissions on the SSO database.</span></span>  
  
### <a name="to-create-a-receive-location"></a><span data-ttu-id="6c496-115">建立接收位置</span><span class="sxs-lookup"><span data-stu-id="6c496-115">To create a receive location</span></span>  
  
1.  <span data-ttu-id="6c496-116">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="6c496-116">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="6c496-117">在主控台樹狀結構中，展開您要建立其接收位置的 BizTalk 群組和 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="6c496-117">In the console tree, expand the BizTalk group and the BizTalk application for which you want to create a receive location.</span></span>  
  
3.  <span data-ttu-id="6c496-118">以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下 **單向接收位置**或**要求回應接收位置**根據的接收位置類型來建立。</span><span class="sxs-lookup"><span data-stu-id="6c496-118">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location** or **Request Response Receive Location**, according to the type of receive location to create.</span></span>  
  
4.  <span data-ttu-id="6c496-119">在 選取接收埠 視窗中，按一下 接收埠，將會包含此接收位置，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6c496-119">In the Select a Receive Port window, click the receive port that will contain this receive location, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="6c496-120">在**接收位置屬性**視窗中，執行下列命令，，然後按一下**確定**:</span><span class="sxs-lookup"><span data-stu-id="6c496-120">In the **Receive Location Properties** window, do the following, and then click **OK**:</span></span>  
  
    |<span data-ttu-id="6c496-121">使用</span><span class="sxs-lookup"><span data-stu-id="6c496-121">Use this</span></span>|<span data-ttu-id="6c496-122">動作</span><span class="sxs-lookup"><span data-stu-id="6c496-122">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="6c496-123">**名稱**</span><span class="sxs-lookup"><span data-stu-id="6c496-123">**Name**</span></span>|<span data-ttu-id="6c496-124">輸入接收位置的名稱。</span><span class="sxs-lookup"><span data-stu-id="6c496-124">Type the name of the receive location.</span></span>|  
    |<span data-ttu-id="6c496-125">**型別**</span><span class="sxs-lookup"><span data-stu-id="6c496-125">**Type**</span></span>|<span data-ttu-id="6c496-126">從下拉式清單選取傳輸類型或傳輸通訊協定。</span><span class="sxs-lookup"><span data-stu-id="6c496-126">From the drop-down list, select the transport type, or transport protocol.</span></span> <span data-ttu-id="6c496-127">若您變更傳輸類型，則必須設定如下所描述的傳輸屬性。</span><span class="sxs-lookup"><span data-stu-id="6c496-127">If you change the transport type, you must configure transport properties, as described next.</span></span>|  
    |<span data-ttu-id="6c496-128">**設定**</span><span class="sxs-lookup"><span data-stu-id="6c496-128">**Configure**</span></span>|<span data-ttu-id="6c496-129">選取傳輸類型之後，請按一下**設定**顯示**傳輸屬性**對話方塊設定配接器接收位置屬性。</span><span class="sxs-lookup"><span data-stu-id="6c496-129">After you select the transport type, click **Configure** to display the **Transport Properties** dialog box and configure adapter properties for the receive location.</span></span> <span data-ttu-id="6c496-130">如需指示，請按一下**協助**在對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="6c496-130">For instructions, click **Help** in the dialog box.</span></span> <span data-ttu-id="6c496-131">如需設定配接器，每種類型的詳細資訊，請參閱底下的適當主題[使用配接器](../core/using-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="6c496-131">For details on configuring each type of adapter, see the appropriate topic under [Using Adapters](../core/using-adapters.md).</span></span>|  
    |<span data-ttu-id="6c496-132">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="6c496-132">**Receive handler**</span></span>|<span data-ttu-id="6c496-133">從下拉式清單選取 BizTalk Server 主控件的執行個體 (接收位置會在其上執行)。</span><span class="sxs-lookup"><span data-stu-id="6c496-133">From the drop-down list, select the instance of the BizTalk Server host on which the receive location will run.</span></span> <span data-ttu-id="6c496-134">接收處理常式必須在此主控件上執行。</span><span class="sxs-lookup"><span data-stu-id="6c496-134">The receive handler must be running on this host.</span></span>|  
    |<span data-ttu-id="6c496-135">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="6c496-135">**Receive pipeline**</span></span>|<span data-ttu-id="6c496-136">從下拉式清單選取接收管線，用來在此接收位置接收訊息。</span><span class="sxs-lookup"><span data-stu-id="6c496-136">From the drop-down list, select the receive pipeline to use to receive messages at this receive location.</span></span>|  
    |<span data-ttu-id="6c496-137">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="6c496-137">**Send pipeline**</span></span>|<span data-ttu-id="6c496-138">從下拉式清單選取傳送管線，用來從此接收位置傳送回應。</span><span class="sxs-lookup"><span data-stu-id="6c496-138">From the drop-down list, select the send pipeline to use to send responses from this receive location.</span></span> <span data-ttu-id="6c496-139">只有和要求-回應接收埠相關聯的接收位置才能使用此清單。</span><span class="sxs-lookup"><span data-stu-id="6c496-139">This list is available only for a receive location associated with a request-response receive port.</span></span>|  
    |<span data-ttu-id="6c496-140">**將此主要位置**</span><span class="sxs-lookup"><span data-stu-id="6c496-140">**Make this the primary location**</span></span>|<span data-ttu-id="6c496-141">若接收埠有一個以上的接收位置，而且必須將連接埠傳遞給需要將訊息傳送至您組織的另一個實體時 (例如，商務合夥人)，若想要以此接收位置代表接收埠，請選取此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6c496-141">Select this check box if you have more than one receive location for a receive port and you want this receive location to represent the receive port when the port needs to be passed to another entity, such as a business partner, that needs to send messages to your organization.</span></span> <span data-ttu-id="6c496-142">建立的第一個接收位置會自動選取為主要接收位置。</span><span class="sxs-lookup"><span data-stu-id="6c496-142">The first receive location created is automatically selected as the primary receive location.</span></span> <span data-ttu-id="6c496-143">除非您指派其他接收位置做為主要位置，否則此屬性會繼續處於選取狀態而且無法使用。</span><span class="sxs-lookup"><span data-stu-id="6c496-143">This property remains selected and unavailable until you designate a different receive location as the primary.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c496-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c496-144">See Also</span></span>  
 [<span data-ttu-id="6c496-145">管理接收位置</span><span class="sxs-lookup"><span data-stu-id="6c496-145">Managing Receive Locations</span></span>](../core/managing-receive-locations.md)