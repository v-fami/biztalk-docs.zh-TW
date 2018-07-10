---
title: 無法建立繫結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fbe1bd54-6031-4f90-a445-c1647b382a1a
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 567b3d88ced85f427fde492cd3e68cefaaf47394
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999201"
---
# <a name="cannot-create-binding"></a><span data-ttu-id="33e40-102">無法建立繫結</span><span class="sxs-lookup"><span data-stu-id="33e40-102">Cannot create binding</span></span>
## <a name="details"></a><span data-ttu-id="33e40-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="33e40-103">Details</span></span>  
  
|                 |                                                                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="33e40-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="33e40-104">Product Name</span></span>   |                               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                               |
| <span data-ttu-id="33e40-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="33e40-105">Product Version</span></span> |                                           [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                           |
|    <span data-ttu-id="33e40-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="33e40-106">Event ID</span></span>     |                                                                       <span data-ttu-id="33e40-107">0</span><span class="sxs-lookup"><span data-stu-id="33e40-107">0</span></span>                                                                        |
|  <span data-ttu-id="33e40-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="33e40-108">Event Source</span></span>   |                                                                       <span data-ttu-id="33e40-109">0</span><span class="sxs-lookup"><span data-stu-id="33e40-109">0</span></span>                                                                        |
|    <span data-ttu-id="33e40-110">元件</span><span class="sxs-lookup"><span data-stu-id="33e40-110">Component</span></span>    |                                                                       <span data-ttu-id="33e40-111">0</span><span class="sxs-lookup"><span data-stu-id="33e40-111">0</span></span>                                                                        |
|  <span data-ttu-id="33e40-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="33e40-112">Symbolic Name</span></span>  |                                                                       <span data-ttu-id="33e40-113">0</span><span class="sxs-lookup"><span data-stu-id="33e40-113">0</span></span>                                                                        |
|  <span data-ttu-id="33e40-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="33e40-114">Message Text</span></span>   | <span data-ttu-id="33e40-115">無法建立繫結，因為未指定繫結類型。</span><span class="sxs-lookup"><span data-stu-id="33e40-115">Cannot create binding since binding type was not specified.</span></span> <span data-ttu-id="33e40-116">指定繫結類型，例如"basicHttpBinding"、"wsHttpBinding"或"customBinding</span><span class="sxs-lookup"><span data-stu-id="33e40-116">Specify a binding type like "basicHttpBinding", "wsHttpBinding", or "customBinding</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="33e40-117">說明</span><span class="sxs-lookup"><span data-stu-id="33e40-117">Explanation</span></span>  
 <span data-ttu-id="33e40-118">您未設定 BindingType 屬性程式碼中設定 Wcf-custom 或 Wcf-customisolated 傳輸之後。</span><span class="sxs-lookup"><span data-stu-id="33e40-118">You did not set the BindingType property in the code after configuring a WCF-Custom or a WCF-CustomIsolated transport.</span></span> <span data-ttu-id="33e40-119">或者，問題可能是其他程式碼路徑中。</span><span class="sxs-lookup"><span data-stu-id="33e40-119">Or the problem could be in other code paths.</span></span> <span data-ttu-id="33e40-120">值必須在繫結設定的使用者介面中。</span><span class="sxs-lookup"><span data-stu-id="33e40-120">You must have a value in the user interface for binding setting.</span></span> <span data-ttu-id="33e40-121">檢閱組態，並確定已從下拉式清單中，接收位置屬性 區域中選定繫結類型。</span><span class="sxs-lookup"><span data-stu-id="33e40-121">Review your configuration and ensure that a binding type was chosen from the drop-down list in the receive location Properties area.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="33e40-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="33e40-122">User Action</span></span>  
 <span data-ttu-id="33e40-123">若要解決這個錯誤，檢閱設定 Wcf-custom 或 Wcf-customisolated 傳輸的程式碼。</span><span class="sxs-lookup"><span data-stu-id="33e40-123">To resolve this error, review the code configuring the WCF-Custom or WCF-CustomIsolated transport.</span></span> <span data-ttu-id="33e40-124">請確認**BindingType**屬性中的 XML 資料**TransportTypeData** ITransportInfo 介面的屬性已正確設定。</span><span class="sxs-lookup"><span data-stu-id="33e40-124">Ensure that the **BindingType** property in the XML data for the **TransportTypeData** property of the ITransportInfo interface is set properly.</span></span>  
  
 <span data-ttu-id="33e40-125">此外，指定繫結型別**basicHttpBinding**， **wsHttpBinding**，或**customBinding**。</span><span class="sxs-lookup"><span data-stu-id="33e40-125">Also, specify a binding type like **basicHttpBinding**, **wsHttpBinding**, or **customBinding**.</span></span>  
  
1. <span data-ttu-id="33e40-126">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="33e40-126">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="33e40-127">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="33e40-127">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3. <span data-ttu-id="33e40-128">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="33e40-128">Locate your application and then locate your transport.</span></span>  
  
4. <span data-ttu-id="33e40-129">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="33e40-129">Right-click the transport name.</span></span>  
  
5. <span data-ttu-id="33e40-130">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="33e40-130">Click **Properties**.</span></span>  
  
6. <span data-ttu-id="33e40-131">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="33e40-131">In the port **Type** list, select the correct port.</span></span>  
  
7. <span data-ttu-id="33e40-132">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="33e40-132">Click **Configure**.</span></span>  
  
8. <span data-ttu-id="33e40-133">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**繫結**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="33e40-133">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="33e40-134">請確定指定的值時，則在**繫結的型別**清單。</span><span class="sxs-lookup"><span data-stu-id="33e40-134">Ensure that a value is specified in the **Binding Type** list.</span></span>  
  
   <span data-ttu-id="33e40-135">如需有關如何設定繫結的詳細資訊，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="33e40-135">For additional information on configuring binding, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="33e40-136">如何設定 Wcf-customisolated 接收位置</span><span class="sxs-lookup"><span data-stu-id="33e40-136">How to Configure a WCF-CustomIsolated Receive Location</span></span>](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [<span data-ttu-id="33e40-137">如何設定 Wcf-custom 接收位置</span><span class="sxs-lookup"><span data-stu-id="33e40-137">How to Configure a WCF-Custom Receive Location</span></span>](../core/how-to-configure-a-wcf-custom-receive-location.md)  
  
-   [<span data-ttu-id="33e40-138">如何設定 Wcf-custom 傳送埠</span><span class="sxs-lookup"><span data-stu-id="33e40-138">How to Configure a WCF-Custom Send Port</span></span>](../core/how-to-configure-a-wcf-custom-send-port.md)