---
title: "安裝配接器至 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1164468d-75a9-4116-87a6-6055948c198b
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1bc585e0574610a867d3f890ce456930bc936dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="install-the-adapter-into-biztalk-server"></a><span data-ttu-id="0ad93-102">將配接器安裝到 BizTalk Server 中</span><span class="sxs-lookup"><span data-stu-id="0ad93-102">Install the Adapter into BizTalk Server</span></span>
<span data-ttu-id="0ad93-103">將正確的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 項目寫入登錄之後，必須將配接器新增至 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="0ad93-103">After the proper [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] entries have been written to the registry the adapter must be added to the BizTalk Management database.</span></span> <span data-ttu-id="0ad93-104">配接器新增至此資料庫之後，即是目前所設定要使用的配接器，只要設定正確就可以開始處理訊息。</span><span class="sxs-lookup"><span data-stu-id="0ad93-104">After the adapter is added to this database it is an actively configured adapter and can process messages when it is properly configured.</span></span> <span data-ttu-id="0ad93-105">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台，將配接器安裝到資料庫中。</span><span class="sxs-lookup"><span data-stu-id="0ad93-105">You install the adapter into the database by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="0ad93-106">在資料庫中安裝配接器之後，請重新啟動主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="0ad93-106">After installing the adapter in the database, restart the host instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ad93-107">為了能在 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 中看見新增的配接器，必須在 HKLM 登錄中正確註冊該配接器，而且必須實作必要的配接器介面。</span><span class="sxs-lookup"><span data-stu-id="0ad93-107">To be visible for addition in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, an adapter must be properly registered in the HKLM registry and must implement the necessary adapter interfaces.</span></span>  
  
### <a name="to-install-the-static-sample-adapter"></a><span data-ttu-id="0ad93-108">安裝範例靜態配接器</span><span class="sxs-lookup"><span data-stu-id="0ad93-108">To install the static sample adapter</span></span>  
  
1.  <span data-ttu-id="0ad93-109">按一下**啟動**，指向**所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="0ad93-109">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="0ad93-110">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按兩下**BizTalk 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="0ad93-110">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, double-click the  **BizTalk Group** node.</span></span>  
  
3.  <span data-ttu-id="0ad93-111">展開**平台設定**選取**配接器**。</span><span class="sxs-lookup"><span data-stu-id="0ad93-111">Expand **Platform Settings** and select **Adapters**.</span></span>  
  
4.  <span data-ttu-id="0ad93-112">以滑鼠右鍵按一下**配接器**，按一下 **新增**，然後按一下 **配接器**。</span><span class="sxs-lookup"><span data-stu-id="0ad93-112">Right-click **Adapters**, click **New**, and then click **Adapter**.</span></span>  
  
5.  <span data-ttu-id="0ad93-113">在**配接器屬性**對話方塊方塊中，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="0ad93-113">In the **Adapter Properties** dialog box, do the following.</span></span>  
  
    |<span data-ttu-id="0ad93-114">使用</span><span class="sxs-lookup"><span data-stu-id="0ad93-114">Use this</span></span>|<span data-ttu-id="0ad93-115">動作</span><span class="sxs-lookup"><span data-stu-id="0ad93-115">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="0ad93-116">名稱</span><span class="sxs-lookup"><span data-stu-id="0ad93-116">Name</span></span>|<span data-ttu-id="0ad93-117">型別**靜態**。</span><span class="sxs-lookup"><span data-stu-id="0ad93-117">Type **Static**.</span></span>|  
    |<span data-ttu-id="0ad93-118">配接器</span><span class="sxs-lookup"><span data-stu-id="0ad93-118">Adapter</span></span>|<span data-ttu-id="0ad93-119">選取**Static dotnetfile**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="0ad93-119">Select **Static DotNetFile** from the drop-down list.</span></span>|  
    |<span data-ttu-id="0ad93-120">Description</span><span class="sxs-lookup"><span data-stu-id="0ad93-120">Description</span></span>|<span data-ttu-id="0ad93-121">型別**範例靜態配接器**。</span><span class="sxs-lookup"><span data-stu-id="0ad93-121">Type **Sample Static Adapter**.</span></span>|  
  
6.  <span data-ttu-id="0ad93-122">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="0ad93-122">Click **OK**.</span></span>  
  
     <span data-ttu-id="0ad93-123">靜態配接器現在會出現在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台右邊視窗的配接器清單中。</span><span class="sxs-lookup"><span data-stu-id="0ad93-123">The static adapter now appears in the list of adapters in the right window of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
### <a name="to-stop-and-restart-the-host-instance"></a><span data-ttu-id="0ad93-124">停止並重新啟動主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="0ad93-124">To stop and restart the host instance</span></span>  
  
1.  <span data-ttu-id="0ad93-125">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **管理**。</span><span class="sxs-lookup"><span data-stu-id="0ad93-125">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**.</span></span>  
  
2.  <span data-ttu-id="0ad93-126">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按兩下**BizTalk 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="0ad93-126">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, double-click the  **BizTalk Group** node.</span></span>  
  
3.  <span data-ttu-id="0ad93-127">展開**平台設定**，選取**主機**，然後選取**BizTalkServerApplication**結果窗格中。</span><span class="sxs-lookup"><span data-stu-id="0ad93-127">Expand **Platform Settings**, select **Hosts**, and then select **BizTalkServerApplication** in the results pane.</span></span>  
  
4.  <span data-ttu-id="0ad93-128">主控件執行個體 （通常是電腦名稱），以滑鼠右鍵按一下，然後按一下 **停止**。</span><span class="sxs-lookup"><span data-stu-id="0ad93-128">Right-click the host instance (typically, the computer name), and then click **Stop**.</span></span>  
  
     <span data-ttu-id="0ad93-129">主控件執行個體狀態會變更為**已停止**。</span><span class="sxs-lookup"><span data-stu-id="0ad93-129">The status of the host instance changes to **Stopped**.</span></span>  
  
5.  <span data-ttu-id="0ad93-130">在結果窗格中，以滑鼠右鍵按一下主控件執行個體，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="0ad93-130">In the results pane, right-click the host instance, and then click **Start**.</span></span>  
  
     <span data-ttu-id="0ad93-131">主控件執行個體狀態會變更為**開始擱置**。</span><span class="sxs-lookup"><span data-stu-id="0ad93-131">The status of the host instance changes to **Start pending**.</span></span> <span data-ttu-id="0ad93-132">您必須按一下**重新整理**，或以滑鼠右鍵按一下主控件執行個體，然後按一下**重新整理**，以將狀態變更為**執行**。</span><span class="sxs-lookup"><span data-stu-id="0ad93-132">You must click **Refresh**, or right-click the host instance and then click **Refresh**, to change the status to **Running**.</span></span>