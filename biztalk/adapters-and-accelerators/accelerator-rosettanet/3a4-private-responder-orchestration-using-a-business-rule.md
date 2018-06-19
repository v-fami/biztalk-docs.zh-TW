---
title: 使用商務規則的 3A4 私用回應者協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33d87952-def6-4202-b535-3d80171332eb
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 130349d707c8e4382c50cd7b65d01d346bf0a7fc
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006279"
---
# <a name="3a4-private-responder-orchestration-using-a-business-rule"></a><span data-ttu-id="aa3fe-102">使用商務規則的 3A4 私用回應者協調流程</span><span class="sxs-lookup"><span data-stu-id="aa3fe-102">3A4 Private Responder Orchestration Using a Business Rule</span></span>
<span data-ttu-id="aa3fe-103">PIP3A4PrivateResponder.odx 範例屬於私用程序協調流程，示範如何實作特定夥伴介面程序 (PIP) 的回應者私用程序，以整合商務規則。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-103">The PIP3A4PrivateResponder.odx sample is a private-process orchestration that demonstrates how to implement a Partner Interface Process (PIP)-specific responder private process incorporating a business rule.</span></span> <span data-ttu-id="aa3fe-104">如需此程序的詳細資訊，請參閱[私用程序協調流程中定義商務規則](../../adapters-and-accelerators/accelerator-rosettanet/defining-a-business-rule-for-a-private-process-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-104">For more information about this process, see [Defining a Business Rule for a Private Process Orchestration](../../adapters-and-accelerators/accelerator-rosettanet/defining-a-business-rule-for-a-private-process-orchestration.md).</span></span>  
  
 <span data-ttu-id="aa3fe-105">根據預設， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]安裝程式安裝中的範例\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator forRosettanet\sdk\pipautomation\3a4。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-105">By default, the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Setup program installs the sample in \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\PipAutomation\3A4.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="aa3fe-106">程序</span><span class="sxs-lookup"><span data-stu-id="aa3fe-106">Procedures</span></span>  
  
#### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="aa3fe-107">若要建置並初始化這個範例</span><span class="sxs-lookup"><span data-stu-id="aa3fe-107">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="aa3fe-108">在命令提示字元中，找出*\<磁碟機\>*: files\ Microsoft BizTalk Accelerator for RosettaNet\<版本\>\SDK\PIPAutomation\3A4 資料夾。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-108">At a command prompt, locate the *\<drive\>*:\Program Files\ Microsoft BizTalk Accelerator for RosettaNet \<version\>\SDK\PIPAutomation\3A4 folder.</span></span>  
  
2.  <span data-ttu-id="aa3fe-109">執行 Setup.bat 檔案，它會使用 Binding.xml 繫結檔案執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="aa3fe-109">Run the file Setup.bat, which uses the Binding.xml binding file to perform the following actions:</span></span>  
  
    -   <span data-ttu-id="aa3fe-110">編譯該 Helper 專案，並在全域組件快取中註冊組件。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-110">Compiles the Helper project and registers the assembly in the global assembly cache.</span></span>  
  
    -   <span data-ttu-id="aa3fe-111">編譯 PIP3APrivateResponder 專案，並在全域組件快取中註冊組件。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-111">Compiles the PIP3APrivateResponder project and registers the assembly in the global assembly cache.</span></span>  
  
    -   <span data-ttu-id="aa3fe-112">建立 LOB_To_PrivateResponder 接收埠。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-112">Creates the LOB_To_PrivateResponder receive port.</span></span>  
  
    -   <span data-ttu-id="aa3fe-113">建立 LOB_To_PrivateResponder 接收位置。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-113">Creates the LOB_To_PrivateResponder receive location.</span></span>  
  
    -   <span data-ttu-id="aa3fe-114">建立並啟動 PrivateResponder_To_LOB 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-114">Creates and starts the PrivateResponder_To_LOB send port.</span></span>  
  
    -   <span data-ttu-id="aa3fe-115">編譯並部署 PIP3A4PrivateResponderProcess 協調流程。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-115">Compiles and deploys the PIP3A4PrivateResponderProcess orchestration.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aa3fe-116">您必須使用 [BizTalk 總管] 完成 PIP3A4PrivateResponderProcess 協調流程的連接埠繫結組態。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-116">You must complete the port binding configuration of the PIP3A4PrivateResponderProcess orchestration using BizTalk Explorer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aa3fe-117">若要復原 setup.bat 所做的變更，請以手動方式取消登錄 PIP3A4PrivateResponder.odx 協調流程、解除部署 Helper 和 PIP3A4PrivateResponder 組件，並且解除部署然後再刪除 samplebtarnpolicy 規則原則。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-117">To undo changes made by setup.bat, manually unenlist the PIP3A4PrivateResponder.odx orchestration, undeploy the Helper and PIP3A4PrivateResponder assemblies, and undeploy and then delete the samplebtarnpolicy rules policy.</span></span> <span data-ttu-id="aa3fe-118">您無法使用中的 Cleanup.bat *\<磁碟機\>*: files\ Microsoft BizTalk Accelerator for RosettaNet\<版本\>\SDK\PIPAutomation\3A4 資料夾復原變更setup.bat 所進行。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-118">You cannot use Cleanup.bat in the *\<drive\>*:\Program Files\ Microsoft BizTalk Accelerator for RosettaNet \<version\>\SDK\PIPAutomation\3A4 folder to undo changes made by setup.bat.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="aa3fe-119">示範</span><span class="sxs-lookup"><span data-stu-id="aa3fe-119">Demonstrates</span></span>  
 <span data-ttu-id="aa3fe-120">這個範例會訂閱 3A4 要求動作和信號訊息，</span><span class="sxs-lookup"><span data-stu-id="aa3fe-120">This sample subscribes 3A4 request action and signal messages.</span></span> <span data-ttu-id="aa3fe-121">並且在 3A4 同步處理和非同步處理程序中都可以運作。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-121">It works in both 3A4 synchronous and asynchronous processes.</span></span> <span data-ttu-id="aa3fe-122">所有其他 PIP 訊息仍會透過一般 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 私用程序路由傳送。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-122">All other PIP messages still route through the generic [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] private process.</span></span> <span data-ttu-id="aa3fe-123">這個範例會叫用「[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 商務規則引擎」，並將內送 3A4 要求訊息傳遞至「規則引擎」。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-123">This sample invokes the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Business Rule Engine, and passes to the Rule Engine the incoming 3A4 request message.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="aa3fe-124">提供名為 samplebtarnpolicy.xml 的範例商務規則原則\<*磁碟機*\>: files\ Microsoft BizTalk Accelerator for RosettaNet\<版本\>\SDK\PipAutomation\3A4。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-124"> provides a sample business-rule policy named samplebtarnpolicy.xml in \<*drive*\>:\Program Files\ Microsoft BizTalk Accelerator for RosettaNet \<version\>\SDK\PipAutomation\3A4.</span></span> <span data-ttu-id="aa3fe-125">如需詳細資訊，請參閱[BTARN 商務原則範例](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-125">For more information, see [Sample BTARN Business Policy](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md).</span></span>  
  
 <span data-ttu-id="aa3fe-126">若要使用這個範例，請安裝商務規則。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-126">To work with the sample, set up a business rule.</span></span> <span data-ttu-id="aa3fe-127">如果訊息符合商務規則，這個程序便會將內送動作訊息儲存在 MessagesToLOB 資料表中，並將 [已傳遞狀態] 設定為 2。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-127">If the message meets the business rule, then the process saves the incoming action message in the MessagesToLOB table, setting the Delivered Status to 2.</span></span> <span data-ttu-id="aa3fe-128">[已傳遞] 資料行值必須為非零，讓商務營運系統應用程式知道它不需要為此要求產生確認。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-128">The Delivered column value must be nonzero, so that the line-of-business application knows that it does not have to generate a confirmation for this request.</span></span> <span data-ttu-id="aa3fe-129">然後，這個程序會將 3A4 要求訊息對應至 3A4 確認訊息，並使用 `SubmitRNIF` 方法，將回應提交至 MessageStorageIn 資料表。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-129">The process then maps the 3A4 request message to a 3A4 confirmation message, and submits the response to the MessageStorageIn table using the `SubmitRNIF` method.</span></span>  
  
 <span data-ttu-id="aa3fe-130">如果訊息不符合商務規則，這個程序便會將內送動作訊息儲存在 MessageStorageOut 資料表中，並將 [已傳遞狀態] 設定為 0。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-130">If the message does not meet the business rule, the process saves the incoming action message in the MessageStorageOut table, and sets Delivered Status to 0.</span></span>  
  
 <span data-ttu-id="aa3fe-131">這個範例包含繫結檔案 (Binding.xml)，讓您可以用來安裝能與 PIP3A4PrivateResponder.odx 協調流程搭配使用的傳送埠 (PrivateResponder_To_LOB)、接收埠 (LOB_To_PrivateResponder) 和接收位置 (LOB_To_PrivateResponder)。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-131">This sample includes a binding file (Binding.xml) that you can use to set up a send port (PrivateResponder_To_LOB), a receive port (LOB_To_PrivateResponder), and a receive location (LOB_To_PrivateResponder) for use with the PIP3A4PrivateResponder.odx orchestration.</span></span> <span data-ttu-id="aa3fe-132">請使用 BTSTask 命令匯入 Binding.xml 檔中的繫結。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-132">Use the BTSTask command to import the bindings in the Binding.xml file.</span></span> <span data-ttu-id="aa3fe-133">如需詳細資訊，請參閱 BizTalk Server 說明中的"< ImportBindings 命令 > 主題。</span><span class="sxs-lookup"><span data-stu-id="aa3fe-133">For more information, see the "ImportBindings Command" topic in BizTalk Server Help.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa3fe-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="aa3fe-134">See Also</span></span>  
 <span data-ttu-id="aa3fe-135">[Double 動作 PIPAutomation 協調流程](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="aa3fe-135">[Double Action PIPAutomation Orchestration](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md) </span></span>  
 <span data-ttu-id="aa3fe-136">[BTARN 商務原則範例](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md) </span><span class="sxs-lookup"><span data-stu-id="aa3fe-136">[Sample BTARN Business Policy](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md) </span></span>  
 [<span data-ttu-id="aa3fe-137">協調流程範例</span><span class="sxs-lookup"><span data-stu-id="aa3fe-137">Orchestration Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)