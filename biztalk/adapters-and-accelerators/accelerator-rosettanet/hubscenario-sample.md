---
title: HubScenario 範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb6990ec-aea2-4362-8573-7f737a4fc7f1
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c47f7ba8320a43cbfdc98a3b3e5becdce9a898f9
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006343"
---
# <a name="hubscenario-sample"></a><span data-ttu-id="14db8-102">HubScenario 範例</span><span class="sxs-lookup"><span data-stu-id="14db8-102">HubScenario Sample</span></span>
<span data-ttu-id="14db8-103">HubScenario 範例示範如何在集線器實例中管理訊息傳輸。</span><span class="sxs-lookup"><span data-stu-id="14db8-103">The HubScenario sample demonstrates how to manage message transmission in a hub scenario.</span></span> <span data-ttu-id="14db8-104">它會將傳送到中繼集線器的訊息轉換成要傳送給最後收件者的訊息。</span><span class="sxs-lookup"><span data-stu-id="14db8-104">It transforms a message sent to an intermediary hub into a message to be sent to the final recipient.</span></span>  
  
 <span data-ttu-id="14db8-105">HubScenario 會從服務內容擷取最後收件者的 DUNS 編號，</span><span class="sxs-lookup"><span data-stu-id="14db8-105">HubScenario extracts the DUNS number of the final recipient from the service content.</span></span> <span data-ttu-id="14db8-106">並管理簽章和加密憑證以及目的地 URL，</span><span class="sxs-lookup"><span data-stu-id="14db8-106">It manages signing and encryption certificates, and the destination URL.</span></span> <span data-ttu-id="14db8-107">為最後收件者產生新的訊息。</span><span class="sxs-lookup"><span data-stu-id="14db8-107">It generates a new message for the final recipient.</span></span>  
  
 <span data-ttu-id="14db8-108">本範例處理 3A4 要求和回應訊息以及 0C1 要求訊息。</span><span class="sxs-lookup"><span data-stu-id="14db8-108">This sample handles 3A4 request and response messages, and 0C1 request messages.</span></span> <span data-ttu-id="14db8-109">當您針對某個目的使用 HubScenario 建立應用程式時，必須為每個訊息交易夥伴介面程序 (PIP) 產生常式。</span><span class="sxs-lookup"><span data-stu-id="14db8-109">When you use HubScenario to create an application for your purposes, you will have to generate routines for each message Partner Interface Process (PIP).</span></span>  
  
 <span data-ttu-id="14db8-110">HubScenario 範例包含 HubHelper.cs 和 HubScenario.odx 專案。</span><span class="sxs-lookup"><span data-stu-id="14db8-110">The HubScenario sample includes HubHelper.cs and HubScenario.odx projects.</span></span>  
  
 <span data-ttu-id="14db8-111">HubScenario 範例也包含繫結檔案，您可使用此檔案匯入接收埠 (MessagesToLOB_Receive_Port) 與接收位置 (MessagesToLOB_Receive_Location) 的繫結，搭配 HubScenario.odx 協調流程使用。</span><span class="sxs-lookup"><span data-stu-id="14db8-111">The HubScenario sample also includes a binding file that you can use to import bindings for a receive port (MessagesToLOB_Receive_Port) and receive location (MessagesToLOB_Receive_Location) for use with the HubScenario.odx orchestration.</span></span> <span data-ttu-id="14db8-112">此繫結檔案 (HubScenarioBinding.xml) 位於*\<磁碟機\>*: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Microsoft BizTalk\<版本\>加速器for RosettaNet \SDK\HubScenario。</span><span class="sxs-lookup"><span data-stu-id="14db8-112">This binding file (HubScenarioBinding.xml) is located in *\<drive\>*:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Microsoft BizTalk \<version\> Accelerator for RosettaNet \SDK\HubScenario.</span></span> <span data-ttu-id="14db8-113">請使用 BTSTask 命令匯入繫結。</span><span class="sxs-lookup"><span data-stu-id="14db8-113">Use the BTSTask command to import the bindings.</span></span> <span data-ttu-id="14db8-114">如需詳細資訊，請參閱 BizTalk Server 說明中的"< ImportBindings 命令 > 主題。</span><span class="sxs-lookup"><span data-stu-id="14db8-114">For more information, see the "ImportBindings Command" topic in BizTalk Server Help.</span></span>  
  
### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="14db8-115">若要建置並初始化這個範例</span><span class="sxs-lookup"><span data-stu-id="14db8-115">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="14db8-116">在 Visual Studio 中開啟\<磁碟機\>: \Program Files\Microsoft Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\HubScenario\HubScenario.btproj。</span><span class="sxs-lookup"><span data-stu-id="14db8-116">In Visual Studio, open \<drive\>:\Program Files\Microsoft Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\HubScenario\HubScenario.btproj.</span></span> <span data-ttu-id="14db8-117">在 [方案總管] 中，以滑鼠右鍵按一下 HubScenario 專案，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="14db8-117">In Solution Explorer, right-click the HubScenario project, and then click Properties.</span></span> <span data-ttu-id="14db8-118">在 HubScenario 專案的 [屬性] 頁面中，於 [簽署] 索引標籤選取**簽署組件**核取方塊，然後選取**HubScenario.snk**中**選擇強式名稱金鑰檔**按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="14db8-118">In the Properties page for the HubScenario project, in the Signing tab select **Sign the assembly** checkbox, and select **HubScenario.snk** in **Choose a strong name key file** and click **Ok**.</span></span>  
  
2.  <span data-ttu-id="14db8-119">在 [方案總管] 中，以滑鼠右鍵按一下 HubHelper 專案，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="14db8-119">In Solution Explorer, right-click the HubHelper project, and then click Properties.</span></span> <span data-ttu-id="14db8-120">在 HubHelper 專案的 [屬性] 頁面中，核取 [簽署] 索引標籤中的 [簽署組件] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="14db8-120">In the Properties page for the HubHelper project, in the Signing tab check Sign the assembly checkbox.</span></span> <span data-ttu-id="14db8-121">在 [選擇強式名稱金鑰檔] 欄位中選取新的型別**HubHelper.snk**做為金鑰檔名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="14db8-121">In Choose a strong name key file field, select new type **HubHelper.snk** as Key file name and click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="14db8-122">如果您沒有在 HubScenario 和 HubHelper 專案中以手動方式輸入組件金鑰檔，這些組件將不會部署。</span><span class="sxs-lookup"><span data-stu-id="14db8-122">If you do not manually enter the assembly key file in the HubScenario and HubHelper projects, the assemblies will not deploy.</span></span>  
  
3.  <span data-ttu-id="14db8-123">在命令提示字元中，移至*\<磁碟機\>*: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\HubScenario 資料夾。</span><span class="sxs-lookup"><span data-stu-id="14db8-123">At a command prompt, move to *\<drive\>*:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\HubScenario folder.</span></span> <span data-ttu-id="14db8-124">執行 Setup.bat 檔案 (若在 64 位元電腦上，請執行 Setupx64.bat)。</span><span class="sxs-lookup"><span data-stu-id="14db8-124">Run the file Setup.bat (or on a 64-bit computer, run Setupx64.bat).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="14db8-125">示範</span><span class="sxs-lookup"><span data-stu-id="14db8-125">Demonstrates</span></span>  
 <span data-ttu-id="14db8-126">HubScenario.ods 協調流程示範如何執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="14db8-126">The HubScenario.ods orchestration demonstrates how to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="14db8-127">從商務營運系統應用程式接收訊息。</span><span class="sxs-lookup"><span data-stu-id="14db8-127">Receives the message from the line-of-business application.</span></span>  
  
2.  <span data-ttu-id="14db8-128">從服務內容中移除 `CDATA` 項目，傳回 XML 字串。</span><span class="sxs-lookup"><span data-stu-id="14db8-128">Removes the `CDATA` element from the service content, returning the XML string.</span></span>  
  
3.  <span data-ttu-id="14db8-129">擷取最後訊息的目的合作對象、PIPCode、PIPInstanceID 和 PIPVersion。</span><span class="sxs-lookup"><span data-stu-id="14db8-129">Retrieves the destination party name, PIPCode, PIPInstanceID, and PIPVersion for the final message.</span></span>  
  
4.  <span data-ttu-id="14db8-130">擷取最後收件者的 DUNS 編號。</span><span class="sxs-lookup"><span data-stu-id="14db8-130">Retrieves the DUNS number for the final recipient.</span></span>  
  
5.  <span data-ttu-id="14db8-131">決定訊息的類別，並將包含適當結構描述之參考的 DOCTYPE 項目新增至服務內容。</span><span class="sxs-lookup"><span data-stu-id="14db8-131">Determines the category of the message, and adds the DOCTYPE element that contains a reference to the appropriate schema to the service content.</span></span>  
  
6.  <span data-ttu-id="14db8-132">使用新的目的合作對象、DUNS 編號、PIP 代碼資訊即服務內容建構訊息。</span><span class="sxs-lookup"><span data-stu-id="14db8-132">Constructs a message with the new destination party name, DUNS number, PIP code information, and service content.</span></span>  
  
7.  <span data-ttu-id="14db8-133">提交訊息，供 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 處理。</span><span class="sxs-lookup"><span data-stu-id="14db8-133">Submits the message for processing by [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].</span></span> <span data-ttu-id="14db8-134">這是 `SubmitRNIF.SubmitMessage` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="14db8-134">This is a call to `SubmitRNIF.SubmitMessage`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14db8-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="14db8-135">See Also</span></span>  
 <span data-ttu-id="14db8-136">[範例中樞架構實例](../../adapters-and-accelerators/accelerator-rosettanet/sample-hub-based-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="14db8-136">[Sample Hub-Based Scenario](../../adapters-and-accelerators/accelerator-rosettanet/sample-hub-based-scenario.md) </span></span>  
 [<span data-ttu-id="14db8-137">協調流程範例</span><span class="sxs-lookup"><span data-stu-id="14db8-137">Orchestration Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)