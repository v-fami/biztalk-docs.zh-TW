---
title: 步驟 7： 建置與部署 DoubleAction SDK 範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, building solutions
- deploying, solutions
- building solutions
- double action tutorial, deploying solutions
ms.assetid: f67f8aee-1004-48ee-a6fd-881097382888
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d9ebd9fe513e302c5bee83e902ed0d275c8785b
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26005375"
---
# <a name="step-7-building-and-deploying-the-doubleaction-sdk-sample"></a><span data-ttu-id="f048e-102">步驟 7： 建置與部署 DoubleAction SDK 範例</span><span class="sxs-lookup"><span data-stu-id="f048e-102">Step 7: Building and Deploying the DoubleAction SDK Sample</span></span>
<span data-ttu-id="f048e-103">DoubleAction.odx 範例會顯示如何實作協調流程，自動為雙向動作「夥伴介面程序」(PIP) 0C2、0C4、3A2 和 3A4 產生回應。</span><span class="sxs-lookup"><span data-stu-id="f048e-103">The DoubleAction.odx sample shows how to implement an orchestration to generate responses automatically for the double-action Partner Interface Processes (PIPs) 0C2, 0C4, 3A2, and 3A4.</span></span> <span data-ttu-id="f048e-104">您可以擴充此範例專案來支援其他的雙向動作 PIP。</span><span class="sxs-lookup"><span data-stu-id="f048e-104">You can extend this sample project to support additional double-action PIPs.</span></span>  
  
 <span data-ttu-id="f048e-105">您將使用此範例，在 Fabrikam 使用四種 PIP 中任一種產生要求時，自動傳送回應給 Fabrikam。</span><span class="sxs-lookup"><span data-stu-id="f048e-105">You use this sample to send a response automatically to Fabrikam whenever Fabrikam makes a request using any one of the four PIPs.</span></span>  
  
### <a name="to-build-and-initialize-the-doubleaction-sample"></a><span data-ttu-id="f048e-106">建置與初始化 DoubleAction 範例</span><span class="sxs-lookup"><span data-stu-id="f048e-106">To build and initialize the DoubleAction sample</span></span>  
  
1.  <span data-ttu-id="f048e-107">在 Contoso 電腦上的命令提示字元視窗中，移至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="f048e-107">On the Contoso computer, in a command prompt window, move to the following folder:</span></span>   
    <span data-ttu-id="f048e-108">*\<磁碟機\>*: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本\>Accelerator for rosettanet\sdk\pipautomation\doubleaction 中\\。</span><span class="sxs-lookup"><span data-stu-id="f048e-108">*\<drive\>*:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\PIPAutomation\DoubleAction\\.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f048e-109">執行安裝程式前，在 [記事本] 中開啟 DoubleAction.sql 檔案 (位於上述資料夾)。</span><span class="sxs-lookup"><span data-stu-id="f048e-109">Before running the Setup program, open the DoubleAction.sql file (in the above folder) in Notepad.</span></span> <span data-ttu-id="f048e-110">在**檔案**功能表上，按一下 **存**。</span><span class="sxs-lookup"><span data-stu-id="f048e-110">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="f048e-111">在**編碼**方塊中，選取**ANSI**從下拉式清單，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="f048e-111">In the **Encoding** box, select **ANSI** from the drop-down list, and then click **Save**.</span></span> <span data-ttu-id="f048e-112">按一下**是**覆寫現有檔案。</span><span class="sxs-lookup"><span data-stu-id="f048e-112">Click **Yes** to overwrite the existing file.</span></span>  
  
2.  <span data-ttu-id="f048e-113">如果您的 BizTalk Server 安裝 SQL Server 2008 R2/2008 SP1 上執行，請執行 setupx64.bat 相同資料夾中。</span><span class="sxs-lookup"><span data-stu-id="f048e-113">If your BizTalk Server installation is running on SQL Server 2008 R2/2008 SP1, run setupx64.bat in the same folder.</span></span> <span data-ttu-id="f048e-114">這個批次檔將會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f048e-114">The batch file will perform the following actions:</span></span>  
  
    -   <span data-ttu-id="f048e-115">在 BTARNDATA 資料庫中建立 SQL 預存程序 (`PipAutomationGetAction`)，以便從 MessagesToLOB 資料表擷取動作訊息。</span><span class="sxs-lookup"><span data-stu-id="f048e-115">Creates a SQL stored procedure (`PipAutomationGetAction`) in the BTARNDATA database to retrieve the action message from the MessagesToLOB table.</span></span>  
  
    -   <span data-ttu-id="f048e-116">編譯 HeaderHelper .NET 專案，並在全域組件快取中註冊組件。</span><span class="sxs-lookup"><span data-stu-id="f048e-116">Compiles the HeaderHelper .NET project and registers the assembly in the global assembly cache.</span></span>  
  
    -   <span data-ttu-id="f048e-117">建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] SQL 接收埠 (MessagesToLOB_Receive_Port)。</span><span class="sxs-lookup"><span data-stu-id="f048e-117">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] SQL receive port (MessagesToLOB_Receive_Port).</span></span>  
  
    -   <span data-ttu-id="f048e-118">啟用接收位置 (MessagesToLOB_Receive_Location)。</span><span class="sxs-lookup"><span data-stu-id="f048e-118">Enables the receive location (MessagesToLOB_Receive_Location).</span></span>  
  
    -   <span data-ttu-id="f048e-119">編譯及部署雙向動作 PIPAutomation 協調流程 (DoubleAction.odx)。</span><span class="sxs-lookup"><span data-stu-id="f048e-119">Compiles and deploys the double-action PIPAutomation orchestration (DoubleAction.odx).</span></span>  
  
    -   <span data-ttu-id="f048e-120">繫結並啟動 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 協調流程。</span><span class="sxs-lookup"><span data-stu-id="f048e-120">Binds and starts the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] orchestration.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f048e-121">範例在編譯時會出現一些警告。</span><span class="sxs-lookup"><span data-stu-id="f048e-121">The sample displays some warnings while compiling.</span></span> <span data-ttu-id="f048e-122">您可以忽略這些警告。</span><span class="sxs-lookup"><span data-stu-id="f048e-122">You can ignore these warnings.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f048e-123">確認 DoubleAction.odx 已繫結至**MessagesToLOB_Receive_Port**，並已啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="f048e-123">Verify that DoubleAction.odx has been bound to **MessagesToLOB_Receive_Port**, and that the orchestration has been started.</span></span>  
  
3.  <span data-ttu-id="f048e-124">在 BizTalk Server 管理主控台中，展開**BizTalk 群組**，**應用程式**，和**BizTalk Application 1**節點。</span><span class="sxs-lookup"><span data-stu-id="f048e-124">In BizTalk Server Administration Console, expand the **BizTalk Group**, **Applications**, and **BizTalk Application 1** nodes.</span></span> <span data-ttu-id="f048e-125">按一下**協調流程**節點。</span><span class="sxs-lookup"><span data-stu-id="f048e-125">Click the **Orchestrations** node.</span></span> <span data-ttu-id="f048e-126">以滑鼠右鍵按一下**DoubleAction**協調流程，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="f048e-126">Right-click the **DoubleAction** orchestration, and then click **Properties**.</span></span> <span data-ttu-id="f048e-127">在 屬性 對話方塊中，按一下 **繫結** 節點，並將其設定**主機**至**BizTalkServerApplication**並設定**接收埠**至**MessageToLOB_ReceivePort**。</span><span class="sxs-lookup"><span data-stu-id="f048e-127">In the Properties dialog box, click the **Bindings** node, and then set the **Host** to **BizTalkServerApplication** and set the **Receive Port** to **MessageToLOB_ReceivePort**.</span></span> <span data-ttu-id="f048e-128">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f048e-128">Click **OK**.</span></span> <span data-ttu-id="f048e-129">以滑鼠右鍵按一下**DoubleAction**協調流程，然後再按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="f048e-129">Right-click the **DoubleAction** orchestration, and then click **Start**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f048e-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="f048e-130">See Also</span></span>  
 [<span data-ttu-id="f048e-131">建立與設定 Fabrikam 解決方案</span><span class="sxs-lookup"><span data-stu-id="f048e-131">Creating and Configuring the Fabrikam Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-the-fabrikam-solution.md)