---
redirect_url: /biztalk/core/mqseries-adapter-deployment-options
redirect_document_id: 
ROBOTS: NOINDEX
ms.openlocfilehash: 2aa74be2d86bcb8f32661fdcf06727eb6391861d
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="using-mqseries-adapter-with-an-earlier-version-of-the-adapter"></a><span data-ttu-id="f51fa-101">以舊版配接器使用 MQSeries 配接器</span><span class="sxs-lookup"><span data-stu-id="f51fa-101">Using MQSeries Adapter with an Earlier Version of the Adapter</span></span>
<span data-ttu-id="f51fa-102">MQSeries 配接器的不同 BizTalk Server 版本可以全部使用相同的遠端 WebSphere MQ Server 上的 Windows。</span><span class="sxs-lookup"><span data-stu-id="f51fa-102">The different BizTalk Server versions of the MQSeries adapter can all work with the same remote WebSphere MQ Server on Windows.</span></span> <span data-ttu-id="f51fa-103">MQSeries 어댑터에 사용되는 다음 버전의 COM+ 응용 프로그램을 같은 WebSphere MQSeries 컴퓨터에서 함께 사용할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="f51fa-103">This is possible because the following versions of the COM+ applications used with the MQSeries adapter can coexist on the same WebSphere MQSeries computer:</span></span>  
  
-   <span data-ttu-id="f51fa-104">**MQSAgent (MQSAgent2) COM + 應用程式**MQSeries 配接器 (BizTalk Server 2006) 搭配使用</span><span class="sxs-lookup"><span data-stu-id="f51fa-104">**MQSAgent (MQSAgent2) COM+ application** used with the MQSeries Adapter (BizTalk Server 2006)</span></span> 
  
-   <span data-ttu-id="f51fa-105">**MQSAgent COM + 應用程式**MQSeries 配接器 (BizTalk Server 2004) 搭配使用</span><span class="sxs-lookup"><span data-stu-id="f51fa-105">**MQSAgent COM+ application** used with the MQSeries Adapter (BizTalk Server 2004)</span></span>  
  
-   <span data-ttu-id="f51fa-106">**MQHelper COM + 應用程式**MQSeries 配接器 (BizTalk Server 2002) 搭配使用</span><span class="sxs-lookup"><span data-stu-id="f51fa-106">**MQHelper COM+ application** used with the MQSeries Adapter (BizTalk Server 2002)</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="f51fa-107">이러한 COM+ 응용 프로그램을 함께 설치하도록 구성하는 경우 해당 응용 프로그램 중 같은 MQSeries 큐를 사용하도록 구성되지 않은 응용 프로그램이 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f51fa-107">When configuring a side-by-side installation of these COM+ applications, ensure that none of these COM+ applications are configured to use the same MQSeries queues.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f51fa-108">如果未安裝舊版的 BizTalk Server 上的 WebSphere MQSeries Adapter COM + 應用程式版本與舊版 MQSeries Adapter COM + 應用程式的 BizTalk Server 2006-並存安裝才支援MQSeries 電腦中。</span><span class="sxs-lookup"><span data-stu-id="f51fa-108">Side-by-side installation of the BizTalk Server 2006 version of the MQSeries Adapter COM+ application with an earlier version of the MQSeries Adapter COM+ application is only supported if an earlier version of BizTalk Server is not installed on the WebSphere MQSeries computer.</span></span>  
  
### <a name="to-install-the-biztalk-server-2006-version-of-the-mqseries-adapter-com-application-on-a-websphere-mqseries-computer-that-is-running-an-earlier-version-of-the-mqseries-adapter-com-application"></a><span data-ttu-id="f51fa-109">이전 버전의 MQSeries 어댑터 COM+ 응용 프로그램을 실행 중인 WebSphere MQSeries 컴퓨터에 BizTalk Server 2006 버전의 MQSeries 어댑터 COM+ 응용 프로그램을 설치하려면</span><span class="sxs-lookup"><span data-stu-id="f51fa-109">To install the BizTalk Server 2006 version of the MQSeries Adapter COM+ application on a WebSphere MQSeries computer that is running an earlier version of the MQSeries Adapter COM+ application</span></span>  
  
1.  <span data-ttu-id="f51fa-110">從 BizTalk Server 2006 CD，若要將相依檔案 MSVCR80.dll 和 MSVCP80.dll 複製到 WebSphere MQSeries 電腦的 \Platform\BootStrap\ 目錄執行 Bootstrap.msi。</span><span class="sxs-lookup"><span data-stu-id="f51fa-110">Run the Bootstrap.msi from the \Platform\BootStrap\ directory of the BizTalk Server 2006 CD to copy the dependency files MSVCR80.dll and MSVCP80.dll to the WebSphere MQSeries computer.</span></span>  
  
2.  <span data-ttu-id="f51fa-111">將 MQSAgent.dll 檔案從 BizTalk Server 2006 CD 的 \Msi\Program Files\ 目錄複製到 WebSphere MQSeries 電腦中。</span><span class="sxs-lookup"><span data-stu-id="f51fa-111">Copy the file MQSAgent.dll from the \Msi\Program Files\ directory on the BizTalk Server 2006 CD to the WebSphere MQSeries computer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f51fa-112">또한 MQSAgent 추적 유틸리티를 사용하려는 경우 이 디렉터리에서 WebSphere MQSeries 컴퓨터로 MQSTrace.cmd 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="f51fa-112">Also copy the file MQSTrace.cmd from this directory to the WebSphere MQSeries computer if you plan on using the MQSAgent tracing utility.</span></span> <span data-ttu-id="f51fa-113">如需 MQSAgent 追蹤公用程式請參閱[使用追蹤工具分析 MQSeries 配接器錯誤](../core/analyzing-mqseries-adapter-errors-with-the-trace-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="f51fa-113">For more information about the MQSAgent tracing utility see [Analyzing MQSeries Adapter Errors with the Trace Tools](../core/analyzing-mqseries-adapter-errors-with-the-trace-tools.md).</span></span>  
  
3.  <span data-ttu-id="f51fa-114">WebSphere MQSeries 컴퓨터에서 regsvr32 mqsagent.dll을 실행하여 MQSAgent.dll에 구성 요소를 수동으로 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="f51fa-114">Manually register the components in MQSAgent.dll by running regsvr32 mqsagent.dll on the WebSphere MQSeries computer:</span></span>  
  
    ```  
    regsvr32 MQSAgent.dll  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f51fa-115">MQSAgent.dll을 복사한 대상 디렉터리에서 이 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f51fa-115">Run this command from the same directory that you copied MQSAgent.dll to.</span></span>  
  
4.  <span data-ttu-id="f51fa-116">MQSAgent 구성 요소에 대한 새 COM+ 응용 프로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f51fa-116">Create a new COM+ application for the MQSAgent components:</span></span>  
  
    -   <span data-ttu-id="f51fa-117">以滑鼠右鍵按一下 COM + 應用程式中，按一下 **新增**, ，**應用程式** 顯示 **COM + 應用程式安裝精靈** 按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="f51fa-117">Right-click COM+ Applications, click **New**, **Application** to display the **COM+ Application Install Wizard** and click **Next**.</span></span>  
  
    -   <span data-ttu-id="f51fa-118">按一下  **建立空的應用程式**。</span><span class="sxs-lookup"><span data-stu-id="f51fa-118">Click **Create an empty application**.</span></span>  
  
    -   <span data-ttu-id="f51fa-119">輸入名稱 **MQSAgent2**, ，保留預設選項為 **伺服器應用程式** 啟用，而且按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="f51fa-119">Enter the name **MQSAgent2**, leave the default option for **Server application** enabled and click **Next**.</span></span>  
  
    -   <span data-ttu-id="f51fa-120">選取的選項 **這位使用者**, 、 輸入適當的帳戶資訊，然後按一下  **下一步**。</span><span class="sxs-lookup"><span data-stu-id="f51fa-120">Select the option for **This user**, enter the appropriate account information and click **Next**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f51fa-121">이 계정에는 해당 IBM WebSphere MQ 큐에 대한 연결 권한과 넣기 및/또는 가져오기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f51fa-121">This account should have connect and put and/or get permissions on the appropriate IBM WebSphere MQ queues.</span></span>  
  
    -   <span data-ttu-id="f51fa-122">按一下  **下一步** 在 新增 **應用程式角色** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f51fa-122">Click **Next** on the Add **Application Roles** dialog box.</span></span>  
  
    -   <span data-ttu-id="f51fa-123">按一下  **下一步** 上 **將使用者新增至角色** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f51fa-123">Click **Next** on the **Add Users to Roles** dialog box.</span></span>  
  
    -   <span data-ttu-id="f51fa-124">**마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f51fa-124">Click **Finish**.</span></span>  
  
5.  <span data-ttu-id="f51fa-125">MQSAgent2 COM+ 응용 프로그램에 MQSAgent.dll 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f51fa-125">Add the MQSAgent.dll components to the MQSAgent2 COM+ application:</span></span>  
  
    -   <span data-ttu-id="f51fa-126">按一下以展開 **MQSAgent2** COM + 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f51fa-126">Click to expand the **MQSAgent2** COM+ Application.</span></span>  
  
    -   <span data-ttu-id="f51fa-127">以滑鼠右鍵按一下 **元件** 按一下 **新增**, ，**元件** 以啟動 [COM + 元件安裝精靈]，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="f51fa-127">Right-click **Components** and click **New**, **Component** to launch the COM+ Component Install Wizard and then click **Next**.</span></span>  
  
    -   <span data-ttu-id="f51fa-128">按一下  **安裝新元件**, ，瀏覽至 MQSAgent.dll 檔案，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="f51fa-128">Click **Install New Components**, browse to the file MQSAgent.dll and then click **Open**.</span></span>  
  
    -   <span data-ttu-id="f51fa-129">**다음**을 클릭한 다음 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f51fa-129">Click **Next**, and then click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f51fa-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f51fa-130">See Also</span></span>  
 [<span data-ttu-id="f51fa-131">使用 MQSeries 配接器</span><span class="sxs-lookup"><span data-stu-id="f51fa-131">Using the MQSeries Adapter</span></span>](../core/using-the-mqseries-adapter.md)