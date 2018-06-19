---
title: 如何設定接收和傳送位置以及連接埠的 BAM WCF 攔截 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 501194dc-427a-4910-88c9-19cf47daeaad
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa77f39e8320c0d6598caaf5ea547592078774ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248438"
---
# <a name="how-to-configure-receive-and-send-locations-and-ports-for-bam-wcf-interception"></a><span data-ttu-id="a023a-102">如何設定 BAM WCF 攔截的接收和傳送位置及連接埠</span><span class="sxs-lookup"><span data-stu-id="a023a-102">How to Configure Receive and Send Locations and Ports for BAM WCF Interception</span></span>
<span data-ttu-id="a023a-103">在這個程序中，您將在根據訊息內容決定路由 (CBR) 的情況下設定接收和傳送位置，以最直接的方式說明重要概念。</span><span class="sxs-lookup"><span data-stu-id="a023a-103">In this procedure you configure the receive and send locations in a content-based routing (CBR) scenario in order to demonstrate the key concepts in a straightforward manner.</span></span> <span data-ttu-id="a023a-104">此處說明的概念適用於做為 [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] 服務公開的協調流程。</span><span class="sxs-lookup"><span data-stu-id="a023a-104">The concepts demonstrated here can be applied to an orchestration that is exposed as a [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] service.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a023a-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="a023a-105">Prerequisites</span></span>  
 <span data-ttu-id="a023a-106">此程序假設您已經：</span><span class="sxs-lookup"><span data-stu-id="a023a-106">This procedure assumes that you have:</span></span>  
  
-   <span data-ttu-id="a023a-107">修改 machince.config 檔案中所示[如何新增 BAM 攔截器行為至 Machine.config 檔](../core/how-to-add-the-bam-interceptor-behavior-to-the-machine-config-file.md)。</span><span class="sxs-lookup"><span data-stu-id="a023a-107">Modified your machince.config file as shown in [How to Add the BAM Interceptor Behavior to the Machine.config File](../core/how-to-add-the-bam-interceptor-behavior-to-the-machine-config-file.md).</span></span>  
  
-   <span data-ttu-id="a023a-108">建立 BizTalk Server 中所述的 WCF 配接器[如何建立 BizTalk Server WCF 配接器](../core/how-to-create-a-wcf-adapter-for-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a023a-108">Created a WCF adapter for BizTalk Server as show in [How to Create a WCF Adapter for BizTalk Server](../core/how-to-create-a-wcf-adapter-for-biztalk-server.md).</span></span>  
  
### <a name="to-configure-the-receive-and-send-locations"></a><span data-ttu-id="a023a-109">若要設定接收和傳送位置</span><span class="sxs-lookup"><span data-stu-id="a023a-109">To configure the receive and send locations</span></span>  
  
1.  <span data-ttu-id="a023a-110">開啟 [BizTalk 管理主控台]。</span><span class="sxs-lookup"><span data-stu-id="a023a-110">Open the BizTalk Administration Console.</span></span> <span data-ttu-id="a023a-111">若要這樣做，請按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="a023a-111">To do this, click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a023a-112">展開主控台樹狀目錄，找出 BizTalk 應用程式的 [接收位置] 節點。</span><span class="sxs-lookup"><span data-stu-id="a023a-112">Expand the console tree to locate the Receive Locations node for your BizTalk application.</span></span> <span data-ttu-id="a023a-113">按一下[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，按一下 [**應用程式**，按一下您在選取的應用程式[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務類型] 對話方塊，然後按一下**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="a023a-113">Click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], click **Applications**, click the application you selected in the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Service Type dialog box, and then click **Receive Locations**.</span></span> <span data-ttu-id="a023a-114">與您所建立之接收位置相對應的新接收位置隨即出現，</span><span class="sxs-lookup"><span data-stu-id="a023a-114">There will be a new receive location corresponding to the one you created.</span></span> <span data-ttu-id="a023a-115">並且處於停用狀態。</span><span class="sxs-lookup"><span data-stu-id="a023a-115">It will be in disabled status.</span></span>  
  
3.  <span data-ttu-id="a023a-116">按兩下接收位置，以開啟**接收位置屬性**對話方塊方塊中，，然後選擇 Wcf-custom 傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="a023a-116">Double-click the receive location to open the **Receive Location Properties** dialog box, and then choose WCF-Custom as the transport type.</span></span>  
  
4.  <span data-ttu-id="a023a-117">按一下**設定** 按鈕以開啟**Wcf-custom 傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a023a-117">Click the **Configure** button to open the **WCF-Custom Transport Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="a023a-118">按一下**繫結**索引標籤上，選取您想要使用的繫結。</span><span class="sxs-lookup"><span data-stu-id="a023a-118">Click the **Binding** tab and select the binding you want to use.</span></span>  
  
6.  <span data-ttu-id="a023a-119">按一下**行為**索引標籤上，以滑鼠右鍵按一下 **[endpointbehavior]** 節點，然後再選取**加入擴充**。</span><span class="sxs-lookup"><span data-stu-id="a023a-119">Click the **Behavior** tab, right-click the **EndpointBehavior** node, and then select **Add Extension**.</span></span>  
  
7.  <span data-ttu-id="a023a-120">選取 （這是您加入至 machine.config 檔案的副檔名） [bamendpointextension]，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="a023a-120">Select the BAMEndPointExtension (this is the extension you added to the machine.config file), and then click **Ok**.</span></span>  
  
     <span data-ttu-id="a023a-121">![選取行為延伸模組畫面](../core/media/fe830d29-504e-465a-9316-b3f0db2dbc24.gif "fe830d29-504e-465a-9316-b3f0db2dbc24")</span><span class="sxs-lookup"><span data-stu-id="a023a-121">![Select Behavior Extension screen](../core/media/fe830d29-504e-465a-9316-b3f0db2dbc24.gif "fe830d29-504e-465a-9316-b3f0db2dbc24")</span></span>  
  
8.  <span data-ttu-id="a023a-122">選取您剛才建立的延伸模組，輸入下列值，然後按**確定**:</span><span class="sxs-lookup"><span data-stu-id="a023a-122">Select the extension you just created, enter the following values, and then click **OK**:</span></span>  
  
    |<span data-ttu-id="a023a-123">屬性</span><span class="sxs-lookup"><span data-stu-id="a023a-123">Property</span></span>|<span data-ttu-id="a023a-124">值</span><span class="sxs-lookup"><span data-stu-id="a023a-124">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="a023a-125">PollingIntervalSec</span><span class="sxs-lookup"><span data-stu-id="a023a-125">PollingIntervalSec</span></span>|<span data-ttu-id="a023a-126">10</span><span class="sxs-lookup"><span data-stu-id="a023a-126">10</span></span>|  
    |<span data-ttu-id="a023a-127">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="a023a-127">ConnectionString</span></span>|<span data-ttu-id="a023a-128">ConnectionString： 整合式安全性 = SSPI;保存安全性資訊 = False; 初始目錄 = BAMPrimaryImport; 資料來源 =</span><span class="sxs-lookup"><span data-stu-id="a023a-128">ConnectionString: Integrated Security=SSPI;Persist Security Info=False;Initial Catalog=BAMPrimaryImport;Data Source=</span></span>|  
  
9. <span data-ttu-id="a023a-129">在**接收位置屬性**對話方塊中，選取**PassThruReceive**從**接收管線**下拉式清單，然後按一下**確定**.</span><span class="sxs-lookup"><span data-stu-id="a023a-129">In the **Receive Location Properties** dialog box, select **PassThruReceive** from the **Receive pipeline** drop-down list, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="a023a-130">啟用接收位置並重新整理管理主控台。</span><span class="sxs-lookup"><span data-stu-id="a023a-130">Enable the receive location and refresh the Administration console.</span></span> <span data-ttu-id="a023a-131">若狀態為已啟動，表示安裝成功。</span><span class="sxs-lookup"><span data-stu-id="a023a-131">A started status indicates that the setup is successful.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a023a-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a023a-132">See Also</span></span>  
 [<span data-ttu-id="a023a-133">設定 WCF 配接器攔截 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="a023a-133">Configuring the WCF Adapter to Intercept BAM Data</span></span>](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)