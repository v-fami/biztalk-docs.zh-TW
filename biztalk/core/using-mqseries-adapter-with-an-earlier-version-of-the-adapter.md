---
title: "以舊版配接器使用 MQSeries 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MQSeries adapters, compatibility
ms.assetid: 278a13ff-8e46-4af4-a76e-b6d4aad5b768
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba635b9bc4569f17418fc925c54c64d0fdc67461
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-mqseries-adapter-with-an-earlier-version-of-the-adapter"></a><span data-ttu-id="e44fe-102">以舊版配接器使用 MQSeries 配接器</span><span class="sxs-lookup"><span data-stu-id="e44fe-102">Using MQSeries Adapter with an Earlier Version of the Adapter</span></span>
<span data-ttu-id="e44fe-103">[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]、[!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] 和 [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] 版本的 MQSeries 配接器都可與 Windows 上相同的遠端 WebSphere MQ Server 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="e44fe-103">The [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)], [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)], and [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] versions of the MQSeries adapter can all work with the same remote WebSphere MQ Server on Windows.</span></span> <span data-ttu-id="e44fe-104">這是可能的，因為與 MQSeries 配接器搭配使用的下列版本 COM+ 應用程式，可同時存在相同的 WebSphere MQSeries 電腦上：</span><span class="sxs-lookup"><span data-stu-id="e44fe-104">This is possible because the following versions of the COM+ applications used with the MQSeries adapter can coexist on the same WebSphere MQSeries computer:</span></span>  
  
-   <span data-ttu-id="e44fe-105">**MQSAgent (MQSAgent2) COM + 應用程式**MQSeries 配接器搭配使用[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e44fe-105">**MQSAgent (MQSAgent2) COM+ application** used with the MQSeries Adapter for [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)].</span></span>  
  
-   <span data-ttu-id="e44fe-106">**MQSAgent COM + 應用程式**MQSeries 配接器搭配使用[!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e44fe-106">**MQSAgent COM+ application** used with the MQSeries Adapter for [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)].</span></span>  
  
-   <span data-ttu-id="e44fe-107">**MQHelper COM + 應用程式**MQSeries 配接器搭配使用[!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e44fe-107">**MQHelper COM+ application** used with the MQSeries Adapter for [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e44fe-108">設定這些 COM+ 應用程式並存的安裝時，請確定沒有任何 COM+ 應用程式設為使用相同的 MQSeries 佇列。</span><span class="sxs-lookup"><span data-stu-id="e44fe-108">When configuring a side-by-side installation of these COM+ applications, ensure that none of these COM+ applications are configured to use the same MQSeries queues.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e44fe-109">MQSeries Adapter COM+ 應用程式與舊版 MQSeries Adapter COM+ 應用程式的 [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] 版並存安裝只有在 WebSphere MQSeries 電腦上未安裝舊版 BizTalk Server 時才支援。</span><span class="sxs-lookup"><span data-stu-id="e44fe-109">Side-by-side installation of the [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] version of the MQSeries Adapter COM+ application with an earlier version of the MQSeries Adapter COM+ application is only supported if an earlier version of BizTalk Server is not installed on the WebSphere MQSeries computer.</span></span>  
  
### <a name="to-install-the-biztalk-server-2006-version-of-the-mqseries-adapter-com-application-on-a-websphere-mqseries-computer-that-is-running-an-earlier-version-of-the-mqseries-adapter-com-application"></a><span data-ttu-id="e44fe-110">在執行舊版 MQSeries Adapter COM+ 應用程式的 WebSphere MQSeries 電腦上安裝 MQSeries Adapter COM+ 應用程式的 BizTalk Server 2006 版</span><span class="sxs-lookup"><span data-stu-id="e44fe-110">To install the BizTalk Server 2006 version of the MQSeries Adapter COM+ application on a WebSphere MQSeries computer that is running an earlier version of the MQSeries Adapter COM+ application</span></span>  
  
1.  <span data-ttu-id="e44fe-111">從 [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] 光碟上的 \Platform\BootStrap\ 目錄執行 Bootstrap.msi，將相依檔案 MSVCR80.dll 和 MSVCP80.dll 複製到 WebSphere MQSeries 電腦中。</span><span class="sxs-lookup"><span data-stu-id="e44fe-111">Run the Bootstrap.msi from the \Platform\BootStrap\ directory of the [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] CD to copy the dependency files MSVCR80.dll and MSVCP80.dll to the WebSphere MQSeries computer.</span></span>  
  
2.  <span data-ttu-id="e44fe-112">從 [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] 光碟上的 \Msi\Program Files\ 目錄將 MQSAgent.dll 複製到 WebSphere MQSeries 電腦中。</span><span class="sxs-lookup"><span data-stu-id="e44fe-112">Copy the file MQSAgent.dll from the \Msi\Program Files\ directory on the [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] CD to the WebSphere MQSeries computer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e44fe-113">如果您打算使用 MQSAgent 追蹤公用程式，則從此目錄一併將 MQSTrace.cmd 檔複製到 WebSphere MQSeries 電腦上。</span><span class="sxs-lookup"><span data-stu-id="e44fe-113">Also copy the file MQSTrace.cmd from this directory to the WebSphere MQSeries computer if you plan on using the MQSAgent tracing utility.</span></span> <span data-ttu-id="e44fe-114">如需 MQSAgent 追蹤公用程式請參閱[使用追蹤工具分析 MQSeries 配接器錯誤](../core/analyzing-mqseries-adapter-errors-with-the-trace-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="e44fe-114">For more information about the MQSAgent tracing utility see [Analyzing MQSeries Adapter Errors with the Trace Tools](../core/analyzing-mqseries-adapter-errors-with-the-trace-tools.md).</span></span>  
  
3.  <span data-ttu-id="e44fe-115">在 WebSphere MQSeries 電腦上執行 regsvr32 mqsagent.dll，以便在 MQSAgent.dll 中手動註冊元件：</span><span class="sxs-lookup"><span data-stu-id="e44fe-115">Manually register the components in MQSAgent.dll by running regsvr32 mqsagent.dll on the WebSphere MQSeries computer:</span></span>  
  
    ```  
    regsvr32 MQSAgent.dll  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e44fe-116">從您將 MQSAgent.dll 複製到其中的同一個目錄執行此命令。</span><span class="sxs-lookup"><span data-stu-id="e44fe-116">Run this command from the same directory that you copied MQSAgent.dll to.</span></span>  
  
4.  <span data-ttu-id="e44fe-117">為 MQSAgent 元件建立新的 COM+ 應用程式：</span><span class="sxs-lookup"><span data-stu-id="e44fe-117">Create a new COM+ application for the MQSAgent components:</span></span>  
  
    -   <span data-ttu-id="e44fe-118">以滑鼠右鍵按一下 COM + 應用程式中，按一下**新增**，**應用程式**顯示**COM + 應用程式安裝精靈**按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="e44fe-118">Right-click COM+ Applications, click **New**, **Application** to display the **COM+ Application Install Wizard** and click **Next**.</span></span>  
  
    -   <span data-ttu-id="e44fe-119">按一下**建立空白的應用程式**。</span><span class="sxs-lookup"><span data-stu-id="e44fe-119">Click **Create an empty application**.</span></span>  
  
    -   <span data-ttu-id="e44fe-120">輸入名稱**MQSAgent2**，保留預設選項為**伺服器應用程式**啟用，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="e44fe-120">Enter the name **MQSAgent2**, leave the default option for **Server application** enabled and click **Next**.</span></span>  
  
    -   <span data-ttu-id="e44fe-121">選取的選項**這位使用者**，輸入適當的帳戶資訊，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="e44fe-121">Select the option for **This user**, enter the appropriate account information and click **Next**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="e44fe-122">在適當的 IBM WebSphere MQ 佇列上，此帳戶應該具備「連線」與「放置」以及/或「取得」權限。</span><span class="sxs-lookup"><span data-stu-id="e44fe-122">This account should have connect and put and/or get permissions on the appropriate IBM WebSphere MQ queues.</span></span>  
  
    -   <span data-ttu-id="e44fe-123">按一下**下一步**在 [新增**應用程式角色**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e44fe-123">Click **Next** on the Add **Application Roles** dialog box.</span></span>  
  
    -   <span data-ttu-id="e44fe-124">按一下**下一步**上**將使用者加入角色** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e44fe-124">Click **Next** on the **Add Users to Roles** dialog box.</span></span>  
  
    -   <span data-ttu-id="e44fe-125">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="e44fe-125">Click **Finish**.</span></span>  
  
5.  <span data-ttu-id="e44fe-126">新增 MQSAgent.dll 元件至 MQSAgent2 COM+ 應用程式：</span><span class="sxs-lookup"><span data-stu-id="e44fe-126">Add the MQSAgent.dll components to the MQSAgent2 COM+ application:</span></span>  
  
    -   <span data-ttu-id="e44fe-127">按一下以展開**MQSAgent2** COM + 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e44fe-127">Click to expand the **MQSAgent2** COM+ Application.</span></span>  
  
    -   <span data-ttu-id="e44fe-128">以滑鼠右鍵按一下**元件**按一下**新增**，**元件**啟動 COM + 元件安裝精靈，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="e44fe-128">Right-click **Components** and click **New**, **Component** to launch the COM+ Component Install Wizard and then click **Next**.</span></span>  
  
    -   <span data-ttu-id="e44fe-129">按一下**安裝新元件**，瀏覽至 MQSAgent.dll 檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="e44fe-129">Click **Install New Components**, browse to the file MQSAgent.dll and then click **Open**.</span></span>  
  
    -   <span data-ttu-id="e44fe-130">按 **[下一步]**，再按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="e44fe-130">Click **Next**, and then click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e44fe-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e44fe-131">See Also</span></span>  
 [<span data-ttu-id="e44fe-132">使用 MQSeries 配接器</span><span class="sxs-lookup"><span data-stu-id="e44fe-132">Using the MQSeries Adapter</span></span>](../core/using-the-mqseries-adapter.md)