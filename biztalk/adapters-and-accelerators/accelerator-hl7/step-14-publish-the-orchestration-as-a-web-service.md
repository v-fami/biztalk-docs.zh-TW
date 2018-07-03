---
title: 步驟 14： 發佈為 Web 服務協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Web services, publishing
- publishing, orchestrations
- Web services, orchestrations
- message enrichment tutorial, orchestrations
- publishing, Web services
- message enrichment tutorial, Web services
ms.assetid: 8f29a7be-a679-4ca6-a648-35338d9e9e98
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64bcc47364cca427f2fc02a807528e7105a40837
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992079"
---
# <a name="step-14-publish-the-orchestration-as-a-web-service"></a><span data-ttu-id="71018-102">步驟 14： 發佈為 Web 服務協調流程</span><span class="sxs-lookup"><span data-stu-id="71018-102">Step 14: Publish the Orchestration as a Web Service</span></span>
<span data-ttu-id="71018-103">在此步驟中，您可以使用 BizTalk Web 服務發佈精靈發佈為 Web 服務協調流程。</span><span class="sxs-lookup"><span data-stu-id="71018-103">In this step, you use the BizTalk Web Services Publishing Wizard to publish your orchestration as a Web service.</span></span>  
  
 <span data-ttu-id="71018-104">之前協調流程發佈為 Web 服務，您必須確保 biztalkserverisolatedhost 主控的登入帳戶會是 BizTalk 外掛式主控件使用者群組的一部分，因此它有 BizTalk 資料庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="71018-104">Before publishing the orchestration as a Web service, you need to ensure that the logon account for BizTalkServerIsolatedHost is part of the BizTalk Isolated Host Users group, so it has access to the BizTalk databases.</span></span> <span data-ttu-id="71018-105">這是必要的因為本教學課程中建立 Web 服務發佈精靈所 SOAPReceivePort 接收位置的接收處理常式是 BizTalkServerIsolatedHost，不是 BizTalkServerApplication。</span><span class="sxs-lookup"><span data-stu-id="71018-105">This is necessary because the receive handler for the SOAPReceivePort receive location that is created by the Web Service Publishing Wizard for this tutorial is BizTalkServerIsolatedHost, not BizTalkServerApplication.</span></span> <span data-ttu-id="71018-106">因為 SOAP 配接器會執行 IIS 處理序，而非 BizTalk 處理序的接收處理常式會是 BizTalkServerIsolatedHost。</span><span class="sxs-lookup"><span data-stu-id="71018-106">The receive handler is BizTalkServerIsolatedHost because the SOAP adapter runs under the IIS process, not the BizTalk process.</span></span>  
  
### <a name="to-ensure-access-privileges-for-the-soapreceiveport-receive-location"></a><span data-ttu-id="71018-107">為了確保存取權限 SOAPReceivePort 接收位置</span><span class="sxs-lookup"><span data-stu-id="71018-107">To ensure access privileges for the SOAPReceivePort receive location</span></span>  
  
1.  <span data-ttu-id="71018-108">在 BizTalk Server 管理主控台，底下**主控件執行個體**中**平台設定**節點，以滑鼠右鍵按一下**BizTalkServerIsolatedHost**，然後按一下  **屬性**。</span><span class="sxs-lookup"><span data-stu-id="71018-108">In BizTalk Server Administration Console, under **Host Instances** in the **Platform Settings** node, right-click **BizTalkServerIsolatedHost**, and then click **Properties**.</span></span> <span data-ttu-id="71018-109">在 [屬性] 對話方塊中，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="71018-109">In the Properties dialog box, click **Configure**.</span></span> <span data-ttu-id="71018-110">附註**登入**帳戶。</span><span class="sxs-lookup"><span data-stu-id="71018-110">Note the **Logon** account.</span></span>  
  
2.  <span data-ttu-id="71018-111">在 [電腦管理] 對話方塊中下,**群組**中**本機使用者和群組**節點中，按兩下**BizTalk Isolated Host Users**。</span><span class="sxs-lookup"><span data-stu-id="71018-111">In the Computer Management dialog box, under **Groups** in the **Local Users and Groups** node, double-click **BizTalk Isolated Host Users**.</span></span> <span data-ttu-id="71018-112">如果登入帳戶**BizTalkServerIsolatedHost**不是成員**BizTalkServerIsolatedHost**，將它新增至群組。</span><span class="sxs-lookup"><span data-stu-id="71018-112">If the logon account for **BizTalkServerIsolatedHost** is not a member of **BizTalkServerIsolatedHost**, add it to the group.</span></span>  
  
### <a name="to-run-the-biztalk-web-services-publishing-wizard"></a><span data-ttu-id="71018-113">若要執行 BizTalk Web 服務發佈精靈</span><span class="sxs-lookup"><span data-stu-id="71018-113">To run the BizTalk Web Services Publishing Wizard</span></span>  
  
1. <span data-ttu-id="71018-114">在 Visual Studio 的方案總管，按一下**解決方案 'BTAHL7V22Common'**。</span><span class="sxs-lookup"><span data-stu-id="71018-114">In Solution Explorer of Visual Studio, click **Solution 'BTAHL7V22Common'**.</span></span> <span data-ttu-id="71018-115">在 **工具**功能表上，按一下**BizTalk Web 服務發佈精靈**。</span><span class="sxs-lookup"><span data-stu-id="71018-115">On the **Tools** menu, click **BizTalk Web Services Publishing Wizard**.</span></span>  
  
2. <span data-ttu-id="71018-116">在 [ **BizTalk Web 服務發佈精靈**上**歡迎**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="71018-116">In the **BizTalk Web Services Publishing Wizard**, on the **Welcome** page, click **Next**.</span></span>  
  
3. <span data-ttu-id="71018-117">在 [**建立 Web 服務**頁面上，選取**BizTalk 協調流程發佈為 web 服務**，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="71018-117">On the **Create Web Service** page, select **Publish BizTalk orchestrations as web services**, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="71018-118">在  **BizTalk 組件**頁面上，於**BizTalk 組件檔案 (\*.dll)** 欄位中，瀏覽至或輸入 **\<*磁碟機*\>: \Tutorial\BTAHL7V22Common\BTAHL7 Project\bin\development**，按一下**BTAHL7 Project.dll**，按一下 **開啟**，然後按一下 **下一步**.</span><span class="sxs-lookup"><span data-stu-id="71018-118">On the **BizTalk Assembly** page, in the **BizTalk assembly file (\*.dll)** field, browse to or type **\<*drive*\>:\Tutorial\BTAHL7V22Common\BTAHL7 Project\bin\development**, click **BTAHL7 Project.dll**, click **Open**, and then click **Next**.</span></span>  
  
5. <span data-ttu-id="71018-119">在 [**協調流程和連接埠**頁面上，確定所有節點都已選取，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="71018-119">On the **Orchestrations and Ports** page, ensure that all nodes are selected, and then click **Next**.</span></span>  
  
6. <span data-ttu-id="71018-120">上**Web 服務屬性**頁面上，如**的 web 服務的目標命名空間**，型別**http://localhost**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="71018-120">On the **Web Service Properties** page, for **Target namespace of web service**, type **http://localhost**, and then click **Next**.</span></span>  
  
7. <span data-ttu-id="71018-121">在  **Web 服務專案**頁面上，選取**允許匿名存取 web 服務**並**建立 BizTalk 接收位置，在下列應用程式中**。</span><span class="sxs-lookup"><span data-stu-id="71018-121">On the **Web Service Project** page, select **Allow anonymous access to web service** and **Create BizTalk receive locations in the following application**.</span></span> <span data-ttu-id="71018-122">選取  **BizTalk Application 1**應用程式。</span><span class="sxs-lookup"><span data-stu-id="71018-122">Select **BizTalk Application 1** for the application.</span></span> <span data-ttu-id="71018-123">保留預設值**位置**欄位。</span><span class="sxs-lookup"><span data-stu-id="71018-123">Keep the default in the **Location** field.</span></span> <span data-ttu-id="71018-124">按一下 [**下一步]** 接受預設專案位置。</span><span class="sxs-lookup"><span data-stu-id="71018-124">Click **Next** to accept the default project location.</span></span>  
  
8. <span data-ttu-id="71018-125">在  **Web 服務專案摘要**頁面上，按一下**建立**來產生 ASP.NET Web 服務專案。</span><span class="sxs-lookup"><span data-stu-id="71018-125">On the **Web Service Project Summary** page, click **Create** to generate the ASP.NET Web Service project.</span></span>  
  
9. <span data-ttu-id="71018-126">按一下 **[完成]** 關閉精靈。</span><span class="sxs-lookup"><span data-stu-id="71018-126">Click **Finish** to close the wizard.</span></span>  
  
10. <span data-ttu-id="71018-127">開啟 [BizTalk Server 管理] 主控台。</span><span class="sxs-lookup"><span data-stu-id="71018-127">Open the BizTalk Server Administration Console.</span></span> <span data-ttu-id="71018-128">在主控台中，依序展開**BizTalk Server 管理**，展開**BizTalk 群組**，展開**應用程式**，然後展開**BizTalk Application 1**.</span><span class="sxs-lookup"><span data-stu-id="71018-128">In the console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
11. <span data-ttu-id="71018-129">按一下 **接收位置**，以滑鼠右鍵按一下**WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**，然後按一下 **屬性**.</span><span class="sxs-lookup"><span data-stu-id="71018-129">Click **Receive Locations**, right-click **WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**, and then click **Properties**.</span></span>  
  
12. <span data-ttu-id="71018-130">在 接收位置屬性 對話方塊中，按一下**接收管線**，選取**Microsoft.BizTalk.DefaultPipelines.XMLReceive**從下拉式清單中，然後按一下  **確定**.</span><span class="sxs-lookup"><span data-stu-id="71018-130">In the Receive Location Properties dialog box, click **Receive Pipeline**, select **Microsoft.BizTalk.DefaultPipelines.XMLReceive** from the drop-down list, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="71018-131">以滑鼠右鍵按一下**WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="71018-131">Right-click **WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**, and then click **Enable**.</span></span>  
  
    <span data-ttu-id="71018-132">請繼續進行[步驟 15： 設定傳送埠和接收埠](../../adapters-and-accelerators/accelerator-hl7/step-15-configure-the-send-and-receive-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="71018-132">Proceed to [Step 15: Configure the Send and Receive Ports](../../adapters-and-accelerators/accelerator-hl7/step-15-configure-the-send-and-receive-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71018-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71018-133">See Also</span></span>  
 [<span data-ttu-id="71018-134">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="71018-134">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)