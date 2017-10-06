---
title: "執行 PeopleSoft Enterprise 範例 Get |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb54f14c-3fce-44d6-91bb-cb1ca38a20da
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ae2233e1d98ff3fde5e27f54e8877fb4b73a96b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="executing-a-peoplesoft-enterprise-sample-get"></a><span data-ttu-id="574b8-102">執行 PeopleSoft Enterprise 的 Get 範例</span><span class="sxs-lookup"><span data-stu-id="574b8-102">Executing a PeopleSoft Enterprise Sample Get</span></span>
<span data-ttu-id="574b8-103">您可以從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統使用 PeopleSoft 配接器存取 PeopleSoft 系統。</span><span class="sxs-lookup"><span data-stu-id="574b8-103">The PeopleSoft system is accessible from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system by using the PeopleSoft adapter.</span></span> <span data-ttu-id="574b8-104">此配接器是一群八個 Microsoft 隨附以供搭配使用的特定業務 (LOB) 配接器的其中一個[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="574b8-104">This adapter is one of a group of eight line-of-business (LOB) adapters shipped by Microsoft for use with [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
 <span data-ttu-id="574b8-105">這是 PeopleSoft 實驗室工作的第二個部分。</span><span class="sxs-lookup"><span data-stu-id="574b8-105">This is the second part of the PeopleSoft lab work.</span></span> <span data-ttu-id="574b8-106">在第一個部分 (實驗室 1) 中，您以手動方式存取及修改 PeopleSoft 系統的協助而資料[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或其他 Microsoft 技術。</span><span class="sxs-lookup"><span data-stu-id="574b8-106">In the first part (Lab 1), you manually accessed and modified data on the PeopleSoft system without the assistance of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or other Microsoft technologies.</span></span> <span data-ttu-id="574b8-107">在這個部分 (實驗室 2) 中，您將建立 BizTalk 協調流程的一部分[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="574b8-107">In this part (Lab 2), you will create a BizTalk orchestration as part of a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project.</span></span> <span data-ttu-id="574b8-108">您將設定此協調流程上的連接埠，以使用 PeopleSoft 配接器自 PeopleSoft 系統取得資料。</span><span class="sxs-lookup"><span data-stu-id="574b8-108">You will configure ports on this orchestration to use the PeopleSoft adapter to get data from a PeopleSoft system.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="574b8-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="574b8-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="574b8-110">Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]</span><span class="sxs-lookup"><span data-stu-id="574b8-110">Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]</span></span>  
  
-   <span data-ttu-id="574b8-111">Microsoft BizTalk Adapters for Enterprise Applications</span><span class="sxs-lookup"><span data-stu-id="574b8-111">Microsoft BizTalk Adapters for Enterprise Applications</span></span>  
  
-   <span data-ttu-id="574b8-112">Microsoft [!INCLUDE[vs2010](../includes/vs2010-md.md)]</span><span class="sxs-lookup"><span data-stu-id="574b8-112">Microsoft [!INCLUDE[vs2010](../includes/vs2010-md.md)]</span></span>  
  
-   <span data-ttu-id="574b8-113">Sun Systems Java Development Kit (JDK) 1.4 (含) 以上版本</span><span class="sxs-lookup"><span data-stu-id="574b8-113">Sun Systems Java Development Kit (JDK) version 1.4 or higher</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="574b8-114">如需安裝及設定 Microsoft BizTalk Adapters for Enterprise Applications 的資訊，請參閱 [http://go.microsoft.com/fwlink/?LinkId=56392](http://go.microsoft.com/fwlink/?LinkId=56392)。</span><span class="sxs-lookup"><span data-stu-id="574b8-114">For information about installing and configuring Microsoft BizTalk Adapters for Enterprise Applications, see [http://go.microsoft.com/fwlink/?LinkId=56392](http://go.microsoft.com/fwlink/?LinkId=56392).</span></span> <span data-ttu-id="574b8-115">此文件包括 JD Edwards、PeopleSoft、Oracle、Tibco 和 Siebel LOB 配接器的重要組態資訊。</span><span class="sxs-lookup"><span data-stu-id="574b8-115">This document includes key configuration information for the JD Edwards, PeopleSoft, Oracle, Tibco, and Siebel LOB adapters.</span></span>  
  
## <a name="lab-2---executing-a-peoplesoft-sample-get"></a><span data-ttu-id="574b8-116">實驗室 2 - 執行 PeopleSoft 的 Get 範例</span><span class="sxs-lookup"><span data-stu-id="574b8-116">Lab 2 - Executing a PeopleSoft Sample Get</span></span>  
 <span data-ttu-id="574b8-117">在這個實驗室中，您將針對 PeopleSoft 系統執行 **Get** 作業。</span><span class="sxs-lookup"><span data-stu-id="574b8-117">In this lab, you will execute a **Get** operation against the PeopleSoft system.</span></span> <span data-ttu-id="574b8-118">也就是說，您將執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="574b8-118">Specifically you will perform the following tasks:</span></span>  
  
-   <span data-ttu-id="574b8-119">驗證 PeopleSoft 必要條件</span><span class="sxs-lookup"><span data-stu-id="574b8-119">Verify the PeopleSoft prerequisites</span></span>  
  
-   <span data-ttu-id="574b8-120">設定中的 PeopleSoft 傳送埠[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="574b8-120">Set up a PeopleSoft send port in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="574b8-121">建立 BizTalk 協調流程專案</span><span class="sxs-lookup"><span data-stu-id="574b8-121">Create a BizTalk orchestration project</span></span>  
  
-   <span data-ttu-id="574b8-122">建置和部署專案</span><span class="sxs-lookup"><span data-stu-id="574b8-122">Build and deploy the project</span></span>  
  
-   <span data-ttu-id="574b8-123">測試應用程式並檢視 XML 輸出</span><span class="sxs-lookup"><span data-stu-id="574b8-123">Test the application and view the XML output</span></span>  
  
## <a name="procedures-for-lab-2--executing-a-peoplesoft-sample-get"></a><span data-ttu-id="574b8-124">實驗室 2 程序 - 執行 PeopleSoft 的 Get 範例</span><span class="sxs-lookup"><span data-stu-id="574b8-124">Procedures for Lab 2- Executing a PeopleSoft Sample Get</span></span>  
 <span data-ttu-id="574b8-125">PeopleSoft 系統的適當介面存取需要兩個檔案：PSJOA.JAR 和 GET_CI_INFO.PC。</span><span class="sxs-lookup"><span data-stu-id="574b8-125">Two files are necessary for proper interface access to a PeopleSoft system: PSJOA.JAR and GET_CI_INFO.PC.</span></span> <span data-ttu-id="574b8-126">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦，PeopleSoft 配接器進行通訊與 PeopleSoft 系統使用 PeopleSoft Java 介面。</span><span class="sxs-lookup"><span data-stu-id="574b8-126">On the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer, the PeopleSoft adapter communicates with the PeopleSoft system by using the PeopleSoft Java interface.</span></span> <span data-ttu-id="574b8-127">此介面是由 PSJOA.JAR 檔案所提供。</span><span class="sxs-lookup"><span data-stu-id="574b8-127">This interface is supplied by the PSJOA.JAR file.</span></span> <span data-ttu-id="574b8-128">置入此檔案的副本[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]通常來自所存取之 PeopleSoft 伺服器系統的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="574b8-128">A copy of this file placed onto the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] typically comes from the administrator of the PeopleSoft server system that is being accessed.</span></span> <span data-ttu-id="574b8-129">在此實驗室中，一份 PSJOA。JAR 上的 C:\PSJars\Ver841\ 資料夾中有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="574b8-129">In this lab, a copy of PSJOA.JAR exists in the C:\PSJars\Ver841\ folder on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="574b8-130">此檔案的位置是在 PeopleSoft 配接器組態屬性中所指定。</span><span class="sxs-lookup"><span data-stu-id="574b8-130">The location of this file is specified in the PeopleSoft adapter configuration properties.</span></span>  
  
 <span data-ttu-id="574b8-131">PeopleSoft 系統本身必須安裝自訂元件介面 (CI)。</span><span class="sxs-lookup"><span data-stu-id="574b8-131">On the PeopleSoft system itself, a custom component interface (CI) must be installed.</span></span> <span data-ttu-id="574b8-132">這可讓配接器在配接器組態期間瀏覽 PeopleSoft 物件。</span><span class="sxs-lookup"><span data-stu-id="574b8-132">This allows the adapter to browse PeopleSoft objects during adapter configuration.</span></span> <span data-ttu-id="574b8-133">呼叫自訂元件介面 (從 [新增產生的項目] 步驟中) 可取得可存取 PeopleSoft 物件的清單。</span><span class="sxs-lookup"><span data-stu-id="574b8-133">The custom component interface is called (from within the Add Generated Items step) to get a list of accessible PeopleSoft objects.</span></span> <span data-ttu-id="574b8-134">這些物件會判斷提供給用戶端系統的 PeopleSoft 公開功能。</span><span class="sxs-lookup"><span data-stu-id="574b8-134">These objects determine exposed PeopleSoft functionality available to the client system.</span></span>  
  
 <span data-ttu-id="574b8-135">特別是自訂元件 GET_CI_INFO，必須在初始安裝期間安裝於 PeopleSoft 系統上。</span><span class="sxs-lookup"><span data-stu-id="574b8-135">Specifically the custom component, GET_CI_INFO, must be installed on the PeopleSoft system once during initial setup.</span></span> <span data-ttu-id="574b8-136">您可以修改這個檔案以限制 GET_CI_INFO 所公開的項目 (預設會公開 PeopleSoft 系統內的所有元件介面)。</span><span class="sxs-lookup"><span data-stu-id="574b8-136">This file can be modified to limit what the GET_CI_INFO exposes (by default it exposes all component interfaces within the PeopleSoft system).</span></span> <span data-ttu-id="574b8-137">其來源位於下列預設位置中的 GET_CI_INFO 文字檔：</span><span class="sxs-lookup"><span data-stu-id="574b8-137">Its source is found in the GET_CI_INFO.PC text file at the following default location:</span></span>  
  
 <span data-ttu-id="574b8-138">**C:\Program Files\Microsoft BizTalk Adapters for enterprise \Config**</span><span class="sxs-lookup"><span data-stu-id="574b8-138">**C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r)\Config**</span></span>  
  
 <span data-ttu-id="574b8-139">將 GET_CI_INFO 元件介面安裝至 PeopleSoft 的一般指示提供於配接器隨附的《安裝指南》，或提供於 [http://go.microsoft.com/fwlink/?LinkId=56392](http://go.microsoft.com/fwlink/?LinkId=56392)。</span><span class="sxs-lookup"><span data-stu-id="574b8-139">General instructions about installing the GET_CI_INFO component interface into PeopleSoft are provided in the Installation Guide that comes with the adapters, or at [http://go.microsoft.com/fwlink/?LinkId=56392](http://go.microsoft.com/fwlink/?LinkId=56392).</span></span> <span data-ttu-id="574b8-140">這些指示適用於經驗豐富的 PeopleSoft 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="574b8-140">These instructions are for an experienced PeopleSoft administrator.</span></span>  
  
### <a name="verifying-the-peoplesoft-prerequisites"></a><span data-ttu-id="574b8-141">驗證 PeopleSoft 必要條件</span><span class="sxs-lookup"><span data-stu-id="574b8-141">Verifying the PeopleSoft Prerequisites</span></span>  
 <span data-ttu-id="574b8-142">在您開始建立搭配 PeopleSoft 配接器使用的 BizTalk 專案之前，必須先確定所有事項都已正確設定，以便存取 PeopleSoft。</span><span class="sxs-lookup"><span data-stu-id="574b8-142">Before you start creating a BizTalk project for use with the PeopleSoft adapter, you need to be sure that everything is set up correctly to access PeopleSoft.</span></span>  
  
##### <a name="to-verify-the-peoplesoft-prerequisites"></a><span data-ttu-id="574b8-143">驗證 PeopleSoft 必要條件</span><span class="sxs-lookup"><span data-stu-id="574b8-143">To verify the PeopleSoft prerequisites</span></span>  
  
1.  <span data-ttu-id="574b8-144">請確認 PSJOA。JAR 檔案存在於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]的 C:\psjars\ver841 資料夾中的電腦。</span><span class="sxs-lookup"><span data-stu-id="574b8-144">Ensure that the PSJOA.JAR file exists on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer in the C:\psjars\ver841 folder.</span></span> <span data-ttu-id="574b8-145">(這個檔案可以位於另一個位置[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="574b8-145">(This file can exist at a different location on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="574b8-146">在下方提供的組態中，會假設檔案是在這個位置。)</span><span class="sxs-lookup"><span data-stu-id="574b8-146">In the configuration given below, it is assumed the file is at this location.)</span></span>  
  
2.  <span data-ttu-id="574b8-147">請確定 get_ci_info.pc 檔案位於 C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r)\Config 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="574b8-147">Ensure that the get_ci_info.pc file exists in the C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r)\Config folder.</span></span>  
  
3.  <span data-ttu-id="574b8-148">按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="574b8-148">Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
4.  <span data-ttu-id="574b8-149">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**主控台根目錄**，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，展開**平台設定**，然後展開**配接器**。</span><span class="sxs-lookup"><span data-stu-id="574b8-149">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **Console Root**, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span> <span data-ttu-id="574b8-150">請確定已安裝 PeopleSoft 配接器，並且出現在清單上。</span><span class="sxs-lookup"><span data-stu-id="574b8-150">Ensure that the PeopleSoft adapter is installed and on the list.</span></span>  
  
     <span data-ttu-id="574b8-151">如果未安裝 PeopleSoft 配接器，請安裝 BizTalk Adapters for Enterprise Applications (請參閱稍早的＜必要條件＞一節)。</span><span class="sxs-lookup"><span data-stu-id="574b8-151">If the PeopleSoft adapter is not installed, install the BizTalk Adapters for Enterprise Applications (see the earlier "Prerequisites" section).</span></span> <span data-ttu-id="574b8-152">安裝配接器之後，用滑鼠右鍵按一下 配接器  ，然後按一下新增 - 配接器  安裝 PeopleSoft 配接器。</span><span class="sxs-lookup"><span data-stu-id="574b8-152">After the adapters are installed, right-click **Adapters** and then click **New - Adapter** to install the PeopleSoft adapter.</span></span> <span data-ttu-id="574b8-153">您必須為此重新啟動主控件執行個體，才會生效。</span><span class="sxs-lookup"><span data-stu-id="574b8-153">You will have to restart the host instance for this to take effect.</span></span>  
  
### <a name="creating-a-send-port-for-peoplesoft"></a><span data-ttu-id="574b8-154">建立 PeopleSoft 傳送埠</span><span class="sxs-lookup"><span data-stu-id="574b8-154">Creating a Send Port for PeopleSoft</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="574b8-155">必須有要用來與 PeopleSoft 系統通訊的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="574b8-155"> needs to have a send port to use for communicating with the PeopleSoft system.</span></span> <span data-ttu-id="574b8-156">此傳送埠最終會繫結至協調流程的邏輯連接埠。</span><span class="sxs-lookup"><span data-stu-id="574b8-156">This send port will eventually be bound to the orchestration's logical ports.</span></span>  
  
##### <a name="to-create-the-peoplesoft-send-port"></a><span data-ttu-id="574b8-157">建立 PeopleSoft 傳送埠</span><span class="sxs-lookup"><span data-stu-id="574b8-157">To create the PeopleSoft send port</span></span>  
  
1.  <span data-ttu-id="574b8-158">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**主控台根目錄**，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，展開**應用程式**，然後展開**BizTalk.EnterpriseApplication。**</span><span class="sxs-lookup"><span data-stu-id="574b8-158">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console,expand **Console Root**, expand[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk.EnterpriseApplication.**</span></span>  
  
2.  <span data-ttu-id="574b8-159">用滑鼠右鍵按一下 [傳送埠] ，再按一下 [新增] ，然後選取 [靜態請求-回應傳送埠] 。</span><span class="sxs-lookup"><span data-stu-id="574b8-159">Right-click **Send Ports**, click **New**, and then select **Static Solicit-Response Send Port**.</span></span> <span data-ttu-id="574b8-160">在 [傳送埠屬性]  對話方塊中輸入屬性的下列值：</span><span class="sxs-lookup"><span data-stu-id="574b8-160">In the **Send Port Properties** dialog box, enter the following values for the properties:</span></span>  
  
    1.  <span data-ttu-id="574b8-161">**名稱：**  `PeopleSoftSamplePort`</span><span class="sxs-lookup"><span data-stu-id="574b8-161">**Name:**  `PeopleSoftSamplePort`</span></span>  
  
    2.  <span data-ttu-id="574b8-162">**類型：**  `PeopleSoft`</span><span class="sxs-lookup"><span data-stu-id="574b8-162">**Type:**  `PeopleSoft`</span></span>  
  
    3.  <span data-ttu-id="574b8-163">**傳送處理常式：**  `BizTalkServerApplication`</span><span class="sxs-lookup"><span data-stu-id="574b8-163">**Send handler:**  `BizTalkServerApplication`</span></span>  
  
    4.  <span data-ttu-id="574b8-164">**傳送管線：**  `XMLTransmit`</span><span class="sxs-lookup"><span data-stu-id="574b8-164">**Send pipeline:**  `XMLTransmit`</span></span>  
  
    5.  <span data-ttu-id="574b8-165">**接收管線：**  `XMLReceive`</span><span class="sxs-lookup"><span data-stu-id="574b8-165">**Receive pipeline:**  `XMLReceive`</span></span>  
  
3.  <span data-ttu-id="574b8-166">按一下 [設定] ，然後輸入下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="574b8-166">Click **Configure**, and then enter the following property values:</span></span>  
  
    1.  <span data-ttu-id="574b8-167">**應用程式伺服器路徑**： **//Servername:9000**</span><span class="sxs-lookup"><span data-stu-id="574b8-167">**Application server path**: **//Servername:9000**</span></span>  
  
         <span data-ttu-id="574b8-168">Servername 是您的應用程式伺服器。</span><span class="sxs-lookup"><span data-stu-id="574b8-168">Servername is your application server.</span></span> <span data-ttu-id="574b8-169">這是此 PeopleSoft 系統的特定伺服器名稱或 IP 位址以及連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="574b8-169">This is the specific server name or IP address and port number for this PeopleSoft system.</span></span>  
  
    2.  <span data-ttu-id="574b8-170">**JAVA_HOME**： **C:\J2SDK1.4.2_08**</span><span class="sxs-lookup"><span data-stu-id="574b8-170">**JAVA_HOME**: **C:\J2SDK1.4.2_08**</span></span>  
  
         <span data-ttu-id="574b8-171">這個路徑是特定上的 Java SDK 安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="574b8-171">This path is specific to the Java SDK installation on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
    3.  <span data-ttu-id="574b8-172">**密碼**:\<輸入您的 PeopleSoft 密碼 ></span><span class="sxs-lookup"><span data-stu-id="574b8-172">**Password**: \<enter your PeopleSoft password></span></span>  
  
    4.  <span data-ttu-id="574b8-173">**PeopleSoft 8.x JAR 檔案**： **C:\PSJARS\VER841\PSJOA.JAR**</span><span class="sxs-lookup"><span data-stu-id="574b8-173">**PeopleSoft 8.x JAR files**: **C:\PSJARS\VER841\PSJOA.JAR**</span></span>  
  
    5.  <span data-ttu-id="574b8-174">**使用者名稱：** \<輸入您的 PeopleSoft Userid> ></span><span class="sxs-lookup"><span data-stu-id="574b8-174">**User name:** \<enter your PeopleSoft UserID></span></span>  
  
     ![](../core/media/7bf30707-c7c6-409f-af18-9c9dfeb0de58.gif "7bf30707-c7c6-409f-af18-9c9dfeb0de58")  
  
4.  <span data-ttu-id="574b8-175">按兩下 [確定]  關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="574b8-175">Click **OK** twice to close the dialog boxes.</span></span>  
  
### <a name="creating-a-biztalk-orchestration-project"></a><span data-ttu-id="574b8-176">建立 BizTalk 協調流程專案</span><span class="sxs-lookup"><span data-stu-id="574b8-176">Creating a BizTalk Orchestration Project</span></span>  
 <span data-ttu-id="574b8-177">現在您將建立 BizTalk 專案中的[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]和處理之間的通訊專案中設定協調流程[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 PeopleSoft 系統。</span><span class="sxs-lookup"><span data-stu-id="574b8-177">Now you will create a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and configure an orchestration in the project to handle communication between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the PeopleSoft system.</span></span> <span data-ttu-id="574b8-178">您將新增傳送和接收埠、建置專案，然後部署專案。</span><span class="sxs-lookup"><span data-stu-id="574b8-178">You will add send and receive ports, build the project, and then deploy the project.</span></span>  
  
##### <a name="to-create-the-biztalk-orchestration-project-in-visual-studio"></a><span data-ttu-id="574b8-179">在 Visual Studio 中建立 BizTalk 協調流程專案</span><span class="sxs-lookup"><span data-stu-id="574b8-179">To create the BizTalk orchestration project in Visual Studio</span></span>  
  
1.  <span data-ttu-id="574b8-180">開啟[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]並在 C:\LABS 資料夾中建立新的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="574b8-180">Open [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and create a new BizTalk project in the C:\LABS folder.</span></span> <span data-ttu-id="574b8-181">在 [檔案]  功能表上，按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="574b8-181">On the **File** menu, click **New**.</span></span> <span data-ttu-id="574b8-182">[新增專案]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="574b8-182">The **New Project** dialog box appears.</span></span> <span data-ttu-id="574b8-183">在 [傳送埠屬性]  區段下，選取 [空白 BizTalk Server 專案] </span><span class="sxs-lookup"><span data-stu-id="574b8-183">In the **Templates** section, select **Empty BizTalk Server project.**</span></span> <span data-ttu-id="574b8-184">輸入`PS_Test`作為唯一的專案名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="574b8-184">Enter `PS_Test` as the unique project name, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="574b8-185">在方案總管中，以滑鼠右鍵按一下專案，按一下 [新增] 及 [新增產生的項目] 。</span><span class="sxs-lookup"><span data-stu-id="574b8-185">In Solution Explorer, right-click the project, click **Add**, and then click **Add Generated Items**.</span></span> <span data-ttu-id="574b8-186">在 類別  窗格中選取 新增配接器中繼資料  ，在 範本  側選取 新增配接器中繼資料  ，然後按一下新增 。</span><span class="sxs-lookup"><span data-stu-id="574b8-186">Select **Add Adapter Metadata** in the **Categories** pane, select **Add Adapter Metadata** on the **Templates** side, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="574b8-187">在 [新增配接器精靈] 中，選取 [PeopleSoft Enterprise]  配接器，選取您在先前程序中所建立的 [PeopleSoftSamplePort]  傳送埠，然後按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="574b8-187">In the Add Adapter Wizard, select the **PeopleSoft Enterprise** adapter, select the **PeopleSoftSamplePort** send port that you created in the preceding procedure, and then click **Next**.</span></span>  
  
     ![](../core/media/ed0dedc5-a8fb-444c-b884-e310cf56462c.gif "ed0dedc5-a8fb-444c-b884-e310cf56462c")  
  
4.  <span data-ttu-id="574b8-188">在 [選取要匯入服務]  頁面上，展開 [PeopleSoft] ，然後展開 [CI] 。</span><span class="sxs-lookup"><span data-stu-id="574b8-188">On the **Select Services to Import** page, expand **PeopleSoft**, and then expand **CI**.</span></span>  
  
     <span data-ttu-id="574b8-189">PeopleSoft 系統是由使用瀏覽代理程式的配接器所查核。</span><span class="sxs-lookup"><span data-stu-id="574b8-189">The PeopleSoft system is interrogated by the adapter using the Browsing Agent.</span></span> <span data-ttu-id="574b8-190">當您展開 [CI] 時，BrowsingAgent.exe 處理序會啟動 (您可以將其視為在工作管理員中執行) 並傳回如下圖所示的服務。</span><span class="sxs-lookup"><span data-stu-id="574b8-190">When you expand **CI**, the BrowsingAgent.exe process starts (you can view it as running in Task Manager) and returns the services shown in the following figure.</span></span>  
  
     ![](../core/media/6988104c-6483-4df2-a637-3301628ea665.gif "6988104c-6483-4df2-a637-3301628ea665")  
  
    > [!NOTE]
    >  <span data-ttu-id="574b8-191">從您的 PeopleSoft 系統取得及顯示的 PeopleSoft 服務，可能與此處顯示的服務稍有不同。</span><span class="sxs-lookup"><span data-stu-id="574b8-191">The PeopleSoft services obtained and displayed from your PeopleSoft system may be slightly different than the services displayed here.</span></span>  
  
5.  <span data-ttu-id="574b8-192">向下捲動，選取 位置 ，然後按一下完成 。</span><span class="sxs-lookup"><span data-stu-id="574b8-192">Scroll down, select **LOCATION**, and then click **Finish**.</span></span>  
  
     ![](../core/media/0506affd-3caa-47cb-9c25-f49c8a0ad614.gif "0506affd-3caa-47cb-9c25-f49c8a0ad614")  
  
6.  <span data-ttu-id="574b8-193">在方案總管中，有新的 BizTalk 協調流程和兩個新的相關聯結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="574b8-193">In Solution Explorer, there is a new BizTalk orchestration and two new associated schema files.</span></span> <span data-ttu-id="574b8-194">這些檔案是由 [新增配接器精靈] 所建立。</span><span class="sxs-lookup"><span data-stu-id="574b8-194">These files are created by the Add Adapter Wizard.</span></span> <span data-ttu-id="574b8-195">按兩下 [BizTalk Orchestration.odx]  檔案開啟協調流程。</span><span class="sxs-lookup"><span data-stu-id="574b8-195">Double-click the **BizTalk Orchestration.odx** file to open the orchestration.</span></span>  
  
     ![](../core/media/825c5690-78eb-4048-9a47-cd3fc7310b7b.gif "825c5690-78eb-4048-9a47-cd3fc7310b7b")  
  
 <span data-ttu-id="574b8-196">此協調流程以輸入形式接受 XML 檔案格式針對 PeopleSoft **Get** 方法格式化，以及將 XML 檔案傳送至 PeopleSoft 系統。</span><span class="sxs-lookup"><span data-stu-id="574b8-196">This orchestration accepts as input an XML file formatted for the PeopleSoft **Get** method and sends the XML file to the PeopleSoft system.</span></span> <span data-ttu-id="574b8-197">**Get** 方法會從 PeopleSoft 系統擷取位置資訊，並將它傳回至 BizTalk 協調流程。</span><span class="sxs-lookup"><span data-stu-id="574b8-197">The **Get** method retrieves location information from the PeopleSoft system and returns it to the BizTalk orchestration.</span></span> <span data-ttu-id="574b8-198">協調流程會使用連接埠來協助與配接器和 PeopleSoft 系統的通訊。</span><span class="sxs-lookup"><span data-stu-id="574b8-198">The orchestration uses ports to facilitate this communication with the adapter and the PeopleSoft system.</span></span> <span data-ttu-id="574b8-199">您將在此處設定的連接埠是用於接收和傳送 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="574b8-199">The ports you will configure here are for receiving and sending XML files.</span></span> <span data-ttu-id="574b8-200">外寄的 XML 檔案會告知 PeopleSoft 系統這是 **Get** 作業。</span><span class="sxs-lookup"><span data-stu-id="574b8-200">The outgoing XML file tells the PeopleSoft system that this is a **Get** operation.</span></span> <span data-ttu-id="574b8-201">內送的 XML 檔案會將位置資訊傳回至協調流程。</span><span class="sxs-lookup"><span data-stu-id="574b8-201">The incoming XML file returns the location information to the orchestration.</span></span>  
  
 <span data-ttu-id="574b8-202">若要完成協調流程，您需要建立及設定連接埠來接收和傳送 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="574b8-202">To complete the orchestration, you need to create and configure ports to receive and send the XML files.</span></span> <span data-ttu-id="574b8-203">首先，設定可接受初始 XML 輸入檔案的新接收埠 (其中包含 **Get** 方法)，來啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="574b8-203">First, set up a new receive port to accept the initial XML input file that contains the **Get** method to start the orchestration.</span></span>  
  
##### <a name="to-configure-a-receive-port"></a><span data-ttu-id="574b8-204">設定接收埠</span><span class="sxs-lookup"><span data-stu-id="574b8-204">To configure a receive port</span></span>  
  
1.  <span data-ttu-id="574b8-205">在您上一個步驟中開啟的 BizTalk Orchestration.odx 檔案內，以滑鼠右鍵按一下左側連接埠介面，然後按一下新設定連接埠 。</span><span class="sxs-lookup"><span data-stu-id="574b8-205">Within the BizTalk Orchestration.odx file that you opened in the previous step, right-click the left port surface and then click **New Configured Port**.</span></span> <span data-ttu-id="574b8-206">如此將啟動 [連接埠組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="574b8-206">This starts the Port Configuration Wizard.</span></span> <span data-ttu-id="574b8-207">在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="574b8-207">On the **Welcome to the Port Configuration Wizard** page, click **Next**.</span></span>  
  
2.  <span data-ttu-id="574b8-208">上**連接埠內容**頁面上，輸入`FileIn`如**名稱**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="574b8-208">On the **Port Properties** page, enter `FileIn` for **Name**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="574b8-209">在 [選取連接埠類型]  頁面上，選取 [建立新的連接埠類型] ，然後輸入或選取下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="574b8-209">In the **Select a Port Type** page, select **Create a new Port Type**, and then enter or select the following property values:</span></span>  
  
     <span data-ttu-id="574b8-210">**連接埠類型名稱**:`FileInPort`</span><span class="sxs-lookup"><span data-stu-id="574b8-210">**Port Type Name**: `FileInPort`</span></span>  
  
     <span data-ttu-id="574b8-211">**通訊模式**： **單向**</span><span class="sxs-lookup"><span data-stu-id="574b8-211">**Communication Pattern**: **One Way**</span></span>  
  
     <span data-ttu-id="574b8-212">**存取限制**： **內部 - 限制於此專案**</span><span class="sxs-lookup"><span data-stu-id="574b8-212">**Access Restrictions**: **Internal - limited to this project**</span></span>  
  
4.  <span data-ttu-id="574b8-213">按 [下一步]  移至 [連接埠繫結]  頁面，然後選取下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="574b8-213">Click **Next** to go to the **Port Binding** page, and then select the following property values:</span></span>  
  
     <span data-ttu-id="574b8-214">**連接埠通訊方向**： **我將總是在此連接埠接收訊息**</span><span class="sxs-lookup"><span data-stu-id="574b8-214">**Port direction of communication**: **I'll always be receiving messages on this port**</span></span>  
  
     <span data-ttu-id="574b8-215">**連接埠繫結**： **稍後指定**</span><span class="sxs-lookup"><span data-stu-id="574b8-215">**Port binding**: **Specify later**</span></span>  
  
5.  <span data-ttu-id="574b8-216">按 **[下一步]**，再按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="574b8-216">Click **Next**, and then click **Finish**.</span></span> <span data-ttu-id="574b8-217">您將使用 FILE 配接器，來接受此檔案為來自磁碟的輸入。</span><span class="sxs-lookup"><span data-stu-id="574b8-217">You will use the File adapter to accept this file as input from disk.</span></span>  
  
 <span data-ttu-id="574b8-218">接下來，建立傳送埠以接受包含呼叫 PeopleSoft **Get** 方法所得位置的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="574b8-218">Next, create a send port to accept the XML file containing the location results from the call to the PeopleSoft **Get** method.</span></span> <span data-ttu-id="574b8-219">協調流程會使用 FILE 配接器，經由此傳送埠將該 XML 檔案寫入磁碟。</span><span class="sxs-lookup"><span data-stu-id="574b8-219">The orchestration uses the File adapter to write that XML file to disk through this send port.</span></span>  
  
##### <a name="to-configure-a-send-port"></a><span data-ttu-id="574b8-220">設定傳送埠</span><span class="sxs-lookup"><span data-stu-id="574b8-220">To configure a send port</span></span>  
  
1.  <span data-ttu-id="574b8-221">在 BizTalk Orchestration.odx 檔案內，以滑鼠右鍵按一下左側連接埠介面，然後按一下新設定連接埠 。</span><span class="sxs-lookup"><span data-stu-id="574b8-221">Within the BizTalk Orchestration.odx file, right-click the left port surface and then click **New Configured Port**.</span></span> <span data-ttu-id="574b8-222">如此將啟動 [連接埠組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="574b8-222">This starts the Port Configuration Wizard.</span></span> <span data-ttu-id="574b8-223">在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="574b8-223">On the **Welcome to the Port Configuration Wizard** page click **Next**.</span></span>  
  
2.  <span data-ttu-id="574b8-224">上**連接埠內容**頁面上，輸入`FileOut`如**名稱**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="574b8-224">On the **Port Properties** page, enter `FileOut` for **Name**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="574b8-225">在 [選取連接埠類型]  頁面上，選取 [建立新的連接埠類型] ，然後輸入或選取下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="574b8-225">On the **Select a Port Type** page, select **Create a new Port Type**, and then enter or select the following property values:</span></span>  
  
     <span data-ttu-id="574b8-226">**連接埠類型名稱**:`FileOutPort`</span><span class="sxs-lookup"><span data-stu-id="574b8-226">**Port Type Name**: `FileOutPort`</span></span>  
  
     <span data-ttu-id="574b8-227">**通訊模式**： **單向**</span><span class="sxs-lookup"><span data-stu-id="574b8-227">**Communication Pattern**: **One Way**</span></span>  
  
     <span data-ttu-id="574b8-228">**存取限制**： **內部 - 限制於此專案**</span><span class="sxs-lookup"><span data-stu-id="574b8-228">**Access Restrictions**: **Internal - limited to this project**</span></span>  
  
4.  <span data-ttu-id="574b8-229">按 [下一步]  移至 [連接埠繫結]  頁面，然後選取下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="574b8-229">Click **Next** to go to the **Port Binding** page, and then select the following property values:</span></span>  
  
     <span data-ttu-id="574b8-230">**連接埠通訊方向**： **我將總是在此連接埠傳送訊息**</span><span class="sxs-lookup"><span data-stu-id="574b8-230">**Port direction of communication**: **I'll always be sending messages on this port**</span></span>  
  
     <span data-ttu-id="574b8-231">**連接埠繫結**： **稍後指定**</span><span class="sxs-lookup"><span data-stu-id="574b8-231">**Port binding**: **Specify later**</span></span>  
  
5.  <span data-ttu-id="574b8-232">按 **[下一步]**，再按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="574b8-232">Click **Next**, and then click **Finish**.</span></span>  
  
 <span data-ttu-id="574b8-233">最後，建立傳送/接收埠，以將包含 **Get** 方法的初始 XML 輸入檔案傳送至 PeopleSoft 系統。</span><span class="sxs-lookup"><span data-stu-id="574b8-233">Finally, create a send/receive port to send the initial XML input file containing the **Get** method to the PeopleSoft system.</span></span> <span data-ttu-id="574b8-234">此連接埠也會接收包含 PeopleSoft 系統上 **Get** 方法呼叫所得位置資訊的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="574b8-234">This port will also receive an XML file containing the location information that results from the **Get** method call on the PeopleSoft system.</span></span>  
  
##### <a name="to-configure-a-sendreceive-port"></a><span data-ttu-id="574b8-235">設定傳送/接收埠</span><span class="sxs-lookup"><span data-stu-id="574b8-235">To configure a send/receive port</span></span>  
  
1.  <span data-ttu-id="574b8-236">在 BizTalk Orchestration.odx 檔案內，以滑鼠右鍵按一下右側連接埠介面，然後按一下新設定連接埠 。</span><span class="sxs-lookup"><span data-stu-id="574b8-236">Within the BizTalk Orchestration.odx file, right-click the right port surface and then click **New Configured Port**.</span></span> <span data-ttu-id="574b8-237">如此將啟動 [連接埠組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="574b8-237">This starts the Port Configuration Wizard.</span></span> <span data-ttu-id="574b8-238">在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="574b8-238">On the **Welcome to the Port Configuration Wizard** page, click **Next**.</span></span>  
  
2.  <span data-ttu-id="574b8-239">上**連接埠內容**頁面上，輸入`PeopleSoft_Port`如**名稱**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="574b8-239">On the **Port Properties** page, enter `PeopleSoft_Port` for **Name**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="574b8-240">在 **[選取連接埠類型]** 頁面上，選取 **[使用現有連接埠類型]**。</span><span class="sxs-lookup"><span data-stu-id="574b8-240">On the **Select a Port Type** page, select **Use an existing Port Type**.</span></span> <span data-ttu-id="574b8-241">針對 [可用的連接埠類型] ，選取 [PS_Test.LOCATION] ，然後按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="574b8-241">For **Available Port Types**, select **PS_Test.LOCATION**, and then click **Next**.</span></span>  
  
     ![](../core/media/d8b443ec-294d-4124-a29d-aeb42bbb107e.gif "d8b443ec-294d-4124-a29d-aeb42bbb107e")  
  
4.  <span data-ttu-id="574b8-242">按 [下一步]  移至 [連接埠繫結]  頁面，然後選取下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="574b8-242">Click **Next** to go to the **Port Binding** page, and then select the following property values:</span></span>  
  
     <span data-ttu-id="574b8-243">**連接埠通訊方向**： **我將總是傳送要求並接收回應**</span><span class="sxs-lookup"><span data-stu-id="574b8-243">**Port direction of communication**: **I'll always be sending a request and receiving a response**</span></span>  
  
     <span data-ttu-id="574b8-244">**連接埠繫結**： **稍後指定**</span><span class="sxs-lookup"><span data-stu-id="574b8-244">**Port binding**: **Specify later**</span></span>  
  
5.  <span data-ttu-id="574b8-245">按 **[下一步]**，再按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="574b8-245">Click **Next**, and then click **Finish**.</span></span>  
  
 <span data-ttu-id="574b8-246">在連接埠介面上顯示的是新的連接埠，以及 PeopleSoft 位置服務可用的方法。</span><span class="sxs-lookup"><span data-stu-id="574b8-246">Displayed on the port surface are the new port and the available methods for the PeopleSoft Location service.</span></span> <span data-ttu-id="574b8-247">稍後，您將會指定 PeopleSoft 配接器來傳送和接收來自 PeopleSoft 系統的檔案。</span><span class="sxs-lookup"><span data-stu-id="574b8-247">Later you will specify the PeopleSoft adapter to send and receive files from the PeopleSoft system.</span></span>  
  
 <span data-ttu-id="574b8-248">現在將兩個 **傳送** 圖形與兩個 **接收** 圖形插入協調流程，以連結至您剛才建立的連接埠。</span><span class="sxs-lookup"><span data-stu-id="574b8-248">Now insert two **Send** shapes and two **Receive** shapes into the orchestration to link to the ports you just created.</span></span>  
  
##### <a name="to-add-send-and-receive-shapes"></a><span data-ttu-id="574b8-249">新增傳送和接收圖形</span><span class="sxs-lookup"><span data-stu-id="574b8-249">To add Send and Receive shapes</span></span>  
  
1.  <span data-ttu-id="574b8-250">從工具箱拖曳 **接收** 元件，緊解著將其放置於協調流程 (綠色圓形) 的開頭下方。</span><span class="sxs-lookup"><span data-stu-id="574b8-250">Drag a **Receive** component from the Toolbox and drop it immediately below the start of the orchestration (the green circle).</span></span> <span data-ttu-id="574b8-251">按一下**接收**圖形，然後在 [屬性] 視窗中，輸入`FromDisk`如**名稱**，並設定**Activate**至`true`。</span><span class="sxs-lookup"><span data-stu-id="574b8-251">Click the **Receive** shape, and in the Properties window, enter `FromDisk` for the **Name**, and set **Activate** to `true`.</span></span> <span data-ttu-id="574b8-252">如此會在此接收埠收到內送文件時啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="574b8-252">Doing so will activate the orchestration when an incoming document is received on this receive port.</span></span>  
  
2.  <span data-ttu-id="574b8-253">拖曳**傳送**元件從工具箱拖曳並將它放在正下方**FromDiskReceive**圖形。</span><span class="sxs-lookup"><span data-stu-id="574b8-253">Drag a **Send** component from the Toolbox and drop it immediately below the **FromDiskReceive** shape.</span></span> <span data-ttu-id="574b8-254">按一下新**傳送**圖形，然後在 [屬性] 視窗中，輸入`ToPS`如**名稱**。</span><span class="sxs-lookup"><span data-stu-id="574b8-254">Click the new **Send** shape, and in the Properties window, enter `ToPS` for the **Name**.</span></span>  
  
3.  <span data-ttu-id="574b8-255">拖曳**接收**元件從工具箱拖曳並將它放在正下方**To_PS * * * 傳送**圖形。</span><span class="sxs-lookup"><span data-stu-id="574b8-255">Drag a **Receive** component from the Toolbox and drop it immediately below the **To_PS****Send** shape.</span></span> <span data-ttu-id="574b8-256">按一下**接收**圖形，然後在 [屬性] 視窗中，輸入`FromPS`如**名稱**。</span><span class="sxs-lookup"><span data-stu-id="574b8-256">Click the **Receive** shape, and in the Properties window, enter `FromPS` for the **Name**.</span></span>  
  
4.  <span data-ttu-id="574b8-257">拖曳**傳送**元件從工具箱拖曳並將它放在正下方**From_PSReceive**圖形。</span><span class="sxs-lookup"><span data-stu-id="574b8-257">Drag a **Send** component from the Toolbox and drop it immediately below the **From_PSReceive** shape.</span></span> <span data-ttu-id="574b8-258">按一下新**傳送**圖形，然後在 [屬性] 視窗中，輸入`ToDisk`如**名稱**。</span><span class="sxs-lookup"><span data-stu-id="574b8-258">Click the new **Send** shape, and in the Properties window, enter `ToDisk` for the **Name**.</span></span>  
  
 <span data-ttu-id="574b8-259">您必須先定義要處理的訊息類型，才可以將這些圖形連接至邏輯連接埠。</span><span class="sxs-lookup"><span data-stu-id="574b8-259">Before you can connect these shapes to logical ports, you need to define the message types to be processed.</span></span> <span data-ttu-id="574b8-260">配接器同時需要內送 (**要求** 方法) 訊息和外寄 (**回應** 方法) 訊息。</span><span class="sxs-lookup"><span data-stu-id="574b8-260">The adapter needs both an incoming (**Request** method) message and an outgoing (**Response** method) message.</span></span> <span data-ttu-id="574b8-261">每個方法的訊息都不同。</span><span class="sxs-lookup"><span data-stu-id="574b8-261">The messages for each of the methods are different.</span></span>  
  
 <span data-ttu-id="574b8-262">在此協調流程中，您只會使用 **Get-Request** 和 **Get-Response** 訊息。</span><span class="sxs-lookup"><span data-stu-id="574b8-262">In this orchestration, you are only using the **Get-Request** and **Get-Response** messages.</span></span> <span data-ttu-id="574b8-263">如果協調流程在更新資料，假設其使用 **UpdateEx** 方法，便會需要不同的要求/回應訊息。</span><span class="sxs-lookup"><span data-stu-id="574b8-263">If the orchestration were updating the data, say by using the **UpdateEx** method, it would require different Request/Response messages.</span></span>  
  
##### <a name="to-define-and-assign-messages-to-ports"></a><span data-ttu-id="574b8-264">定義訊息和指派訊息到連接埠</span><span class="sxs-lookup"><span data-stu-id="574b8-264">To define and assign messages to ports</span></span>  
  
1.  <span data-ttu-id="574b8-265">在左側連接埠介面上，按一下 [FileIn]  連接埠上的 [要求]  。</span><span class="sxs-lookup"><span data-stu-id="574b8-265">On the left port surface, click **Request** on the **FileIn** port.</span></span> <span data-ttu-id="574b8-266">在 屬性 視窗中依序展開 訊息類型 和 多部分訊息 ，然後按一下PS_Test.Get 。</span><span class="sxs-lookup"><span data-stu-id="574b8-266">In the Properties window, expand **Message Type**, expand **Multi-part Message**, and then click **PS_Test.Get**.</span></span>  
  
2.  <span data-ttu-id="574b8-267">在左側連接埠介面上，按一下 [FileOut]  連接埠上的 [要求]  。</span><span class="sxs-lookup"><span data-stu-id="574b8-267">On the left port surface, click **Request** on the **FileOut** port.</span></span> <span data-ttu-id="574b8-268">在 屬性 視窗中依序展開 訊息類型 及 多部分訊息 ，然後按一下PS_Test.GetResponse 。</span><span class="sxs-lookup"><span data-stu-id="574b8-268">In the Properties window, expand **Message Type**, expand **Multi-part Message**, and then click **PS_Test.GetResponse**.</span></span>  
  
     ![](../core/media/6b844ca3-322a-47b3-8cfd-68652c950752.gif "6b844ca3-322a-47b3-8cfd-68652c950752")  
  
3.  <span data-ttu-id="574b8-269">選取 [FileIn]  連接埠，並將其外寄傳送箭頭拖曳至 **FromDisk** 圖形上的內送反向接收箭頭。</span><span class="sxs-lookup"><span data-stu-id="574b8-269">Select the **FileIn** port and drag its outgoing send arrow to the incoming converse receive arrow on the **FromDisk** shape.</span></span>  
  
4.  <span data-ttu-id="574b8-270">選取 [FileOut]  連接埠，並將其內送反向接收箭頭拖曳至 **ToDisk** 圖形上的外寄傳送箭頭。</span><span class="sxs-lookup"><span data-stu-id="574b8-270">Select the **FileOut** port and drag its incoming converse receive arrow to the outgoing send arrow on the **ToDisk** shape.</span></span>  
  
5.  <span data-ttu-id="574b8-271">將現有的泛型訊息名稱重新命名為更具描述性的名稱，以遵守良好的應用程式設計原則。</span><span class="sxs-lookup"><span data-stu-id="574b8-271">Rename existing generic message names to more descriptive names to adhere to good application design principles.</span></span> <span data-ttu-id="574b8-272">在方案總管中，按一下 [協調流程檢視]  索引標籤。在下**訊息**，變更的識別項**Message_1**至**PS_Msg**。</span><span class="sxs-lookup"><span data-stu-id="574b8-272">In Solution Explorer, click the **Orchestration View** tab. Under **Messages**, change the identifier for **Message_1** to **PS_Msg**.</span></span> <span data-ttu-id="574b8-273">將 **Message_2** 的識別項變更為 [PS_Resp] 。</span><span class="sxs-lookup"><span data-stu-id="574b8-273">Change the identifier for **Message_2** to **PS_Resp**.</span></span>  
  
     ![](../core/media/5ec92b81-4a55-4d44-a360-78a6aaa64255.gif "5ec92b81-4a55-4d44-a360-78a6aaa64255")  
  
     ![](../core/media/04b31c26-73a6-40a6-8d50-39c7c929d6a1.gif "04b31c26-73a6-40a6-8d50-39c7c929d6a1")  
  
6.  <span data-ttu-id="574b8-274">反白顯示 **To_PS** 傳送圖形並將其 **訊息** 屬性設為 [PS_Msg] 。</span><span class="sxs-lookup"><span data-stu-id="574b8-274">Highlight the **To_PS** send shape and set its **Message** property to **PS_Msg**.</span></span>  
  
7.  <span data-ttu-id="574b8-275">反白顯示 **From_PS** 接收圖形並將其 **訊息** 屬性設為 [PS_Resp] 。</span><span class="sxs-lookup"><span data-stu-id="574b8-275">Highlight the **From_PS** receive shape and set its **Message** property to **PS_Resp**.</span></span>  
  
8.  <span data-ttu-id="574b8-276">將 **To_PS** 傳送圖形連接至 **PeopleSoft_Port** 連接埠上 **Get** 方法的 **要求** 部分。</span><span class="sxs-lookup"><span data-stu-id="574b8-276">Connect the **To_PS** send shape to the **Request** portion of the **Get** method on the **PeopleSoft_Port** port.</span></span>  
  
9. <span data-ttu-id="574b8-277">將 **From_PS** 傳送圖形連接至 **PeopleSoft_Port** 連接埠上 **Get** 方法的 **回應** 部分。</span><span class="sxs-lookup"><span data-stu-id="574b8-277">Connect the **From_PS** send shape to the **Response** portion of the **Get** method on the **PeopleSoft_Port** port.</span></span>  
  
     ![](../core/media/d16e02bc-954c-4aa2-99d6-3fee1222c730.gif "d16e02bc-954c-4aa2-99d6-3fee1222c730")  
  
### <a name="building-and-deploying-the-project"></a><span data-ttu-id="574b8-278">建置和部署專案</span><span class="sxs-lookup"><span data-stu-id="574b8-278">Building and Deploying the Project</span></span>  
 <span data-ttu-id="574b8-279">現在 BizTalk 專案已完成，而且您可以建置並部署在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="574b8-279">Now the BizTalk project is complete and you can build and deploy it in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
##### <a name="to-build-and-deploy-the-project"></a><span data-ttu-id="574b8-280">建置和部署專案</span><span class="sxs-lookup"><span data-stu-id="574b8-280">To build and deploy the project</span></span>  
  
1.  <span data-ttu-id="574b8-281">按一下**啟動**，指向 **所有程式**，指向  **Microsoft [!INCLUDE[vs2010](../includes/vs2010-md.md)]** ，指向**Visual Studio Tools**，然後按一下 **[!INCLUDE[vs2010](../includes/vs2010-md.md)]命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="574b8-281">Click **Start**, point to **All Programs**, point to **Microsoft [!INCLUDE[vs2010](../includes/vs2010-md.md)]**, point to **Visual Studio Tools**, and then click**[!INCLUDE[vs2010](../includes/vs2010-md.md)] Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="574b8-282">若要建置專案，您需要強式名稱金鑰檔。在命令提示字元中，輸入下列內容建立強式金鑰名稱檔：</span><span class="sxs-lookup"><span data-stu-id="574b8-282">To build the project, you need a strong name key file.At the command prompt, enter the following to create a strong name key file:</span></span>  
  
     <span data-ttu-id="574b8-283">**sn-k [labs.snk]**</span><span class="sxs-lookup"><span data-stu-id="574b8-283">**sn -k labs.snk**</span></span>  
  
3.  <span data-ttu-id="574b8-284">在方案總管中，以滑鼠右鍵按一下 [PS_Test]  專案，再按一下 [屬性]  為專案啟動 [專案設計工具]。</span><span class="sxs-lookup"><span data-stu-id="574b8-284">In Solution Explorer, right-click the **PS_Test** project and then click **Properties** to launch the Project Designer for the project..</span></span>  
  
4.  <span data-ttu-id="574b8-285">按一下 [ **簽署** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="574b8-285">Click the **Signing** tab.</span></span>  
  
5.  <span data-ttu-id="574b8-286">選取 **[簽署組件]** 選項、按一下 **[選擇強式名稱金鑰檔]** 選項的下拉式清單，然後按一下 **[瀏覽]**。</span><span class="sxs-lookup"><span data-stu-id="574b8-286">Select **Sign the assembly** option, click drop-down list for the **Choose a strong name key file** option, and then click **Browse**.</span></span>  
  
6.  <span data-ttu-id="574b8-287">瀏覽並選取金鑰檔： **[labs.snk]**，然後按一下 **[開啟]**。</span><span class="sxs-lookup"><span data-stu-id="574b8-287">Browse to select the key file: **labs.snk**, and then click **Open**.</span></span>  
  
7.  <span data-ttu-id="574b8-288">按一下 [專案設計工具] 中的 **[部署]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="574b8-288">Click **Deployment** tab in the Project Designer.</span></span>  
  
8.  <span data-ttu-id="574b8-289">設定**應用程式名稱**至`PS_Test`。</span><span class="sxs-lookup"><span data-stu-id="574b8-289">Set the **Application Name** to `PS_Test`.</span></span>  
  
9. <span data-ttu-id="574b8-290">在方案總管中，以滑鼠右鍵按一下   專案，然後按一下建置 </span><span class="sxs-lookup"><span data-stu-id="574b8-290">In Solution Explorer, right-click the **PS_Test** project, and then click **Build.**</span></span>  
  
10. <span data-ttu-id="574b8-291">順利完成建置後，以滑鼠右鍵按一下 PS_Test  專案，然後按一下部署 。</span><span class="sxs-lookup"><span data-stu-id="574b8-291">After the build completes successfully, right-click the **PS_Test** project, and then click **Deploy**.</span></span>  
  
### <a name="testing-the-application-and-viewing-the-xml-output"></a><span data-ttu-id="574b8-292">測試應用程式並檢視 XML 輸出</span><span class="sxs-lookup"><span data-stu-id="574b8-292">Testing the Application and Viewing the XML Output</span></span>  
 <span data-ttu-id="574b8-293">現在您將測試所建立和部署的應用程式。</span><span class="sxs-lookup"><span data-stu-id="574b8-293">Now you will test the application that you have created and deployed.</span></span> <span data-ttu-id="574b8-294">您會建立啟動協調流程處理序的 XML 檔案，然後設定在應用程式內接收和傳送 XML 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="574b8-294">You will create the XML file that starts the orchestration process, and then you will configure folders to receive and send XML files within the application.</span></span> <span data-ttu-id="574b8-295">設定應用程式之後，您將會執行它並檢視協調流程所傳回的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="574b8-295">After you have configured the application, you will run it and view the XML files that the orchestration returns.</span></span>  
  
##### <a name="to-generate-the-xml-file-for-the-query"></a><span data-ttu-id="574b8-296">產生查詢的 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="574b8-296">To generate the XML file for the query</span></span>  
  
1.  <span data-ttu-id="574b8-297">在方案總管中，按兩下 [LOCATIONService_LOCATION_x5d.xsd]  開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="574b8-297">In Solution Explorer, double-click **LOCATIONService_LOCATION_x5d.xsd** to open the file.</span></span>  
  
2.  <span data-ttu-id="574b8-298">以滑鼠右鍵按一下 [LOCATIONService_LOCATION_x5d.xsd]  ，再按一下 [屬性] 。</span><span class="sxs-lookup"><span data-stu-id="574b8-298">Right-click **LOCATIONService_LOCATION_x5d.xsd** and then click **Properties**.</span></span> <span data-ttu-id="574b8-299">針對 **輸出執行個體檔案名稱** 輸入範例 XML 的下列路徑和檔案名稱：</span><span class="sxs-lookup"><span data-stu-id="574b8-299">For the **Output Instance Filename** enter the following path and file name for the sample XML:</span></span>  
  
     `C:\LABS\PS_TEST\SAMPLEQUERY.XML`  
  
3.  <span data-ttu-id="574b8-300">按一下 **[確定].**</span><span class="sxs-lookup"><span data-stu-id="574b8-300">Click **OK.**</span></span> <span data-ttu-id="574b8-301">在 [屬性] 視窗中，選取**\<結構描述 >**並設定**根參考： 取得**。</span><span class="sxs-lookup"><span data-stu-id="574b8-301">In the Properties window, select **\<Schema>** and set **Root Reference: Get**.</span></span>  
  
4.  <span data-ttu-id="574b8-302">以滑鼠右鍵按一下 [LOCATIONService_LOCATION_x5d.xsd]  ，再按一下 [產生執行個體] 。</span><span class="sxs-lookup"><span data-stu-id="574b8-302">Right-click **LOCATIONService_LOCATION_x5d.xsd** and then click **Generate Instance**.</span></span> <span data-ttu-id="574b8-303">這會產生 **SampleQuery.xml** 檔案。</span><span class="sxs-lookup"><span data-stu-id="574b8-303">This generates the **SampleQuery.xml** file.</span></span> <span data-ttu-id="574b8-304">這個檔案將做為配接器的輸入，放置在接收位置以啟動協調流程處理序。</span><span class="sxs-lookup"><span data-stu-id="574b8-304">This file will be dropped in the receive location as input to the adapter to start the orchestration process.</span></span>  
  
     ![](../core/media/ef65a96c-2daa-44db-ab95-d18b1fda934e.gif "ef65a96c-2daa-44db-ab95-d18b1fda934e")  
  
##### <a name="to-configure-and-start-the-biztalk-application"></a><span data-ttu-id="574b8-305">設定並啟動 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="574b8-305">To configure and start the BizTalk application</span></span>  
  
1.  <span data-ttu-id="574b8-306">設定用於接收內送檔案及傳送外寄檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="574b8-306">Configure folders for receiving the incoming files and sending the outgoing files.</span></span> <span data-ttu-id="574b8-307">移至**C:\LABS\PS_TEST**並建立兩個新子資料夾名為`FileIn`和`FileOut`。</span><span class="sxs-lookup"><span data-stu-id="574b8-307">Go to **C:\LABS\PS_TEST** and create two new subfolders named `FileIn` and `FileOut`.</span></span>  
  
2.  <span data-ttu-id="574b8-308">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**主控台根目錄**，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，展開**應用程式**，以滑鼠右鍵按一下**PS_Test** ，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="574b8-308">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console,expand **Console Root**, expand[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, right-click **PS_Test** and then click **Configure**.</span></span>  
  
     ![](../core/media/e45f4c8b-fc8a-492a-9824-5232eb728d95.gif "e45f4c8b-fc8a-492a-9824-5232eb728d95")  
  
3.  <span data-ttu-id="574b8-309">選取 [Orchestration_1]  ，並按一下 [主機]  下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="574b8-309">Select **Orchestration_1** and click the **Host** drop-down box.</span></span> <span data-ttu-id="574b8-310">選取 **[BizTalkServerApplication]**。</span><span class="sxs-lookup"><span data-stu-id="574b8-310">Select **BizTalkServerApplication**.</span></span>  
  
4.  <span data-ttu-id="574b8-311">在下**接收埠**，按一下  **\<無 >**。</span><span class="sxs-lookup"><span data-stu-id="574b8-311">Under **Receive Ports**, click **\<None>**.</span></span> <span data-ttu-id="574b8-312">在下拉式清單中選取 [新增接收埠] 。</span><span class="sxs-lookup"><span data-stu-id="574b8-312">In the drop-down list, select **New Receive Port**.</span></span>  
  
5.  <span data-ttu-id="574b8-313">如**名稱**，型別`FileInPort`，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="574b8-313">For **Name**, type `FileInPort`, and then click **OK**.</span></span> <span data-ttu-id="574b8-314">訊息方塊會出現，指出您需要指定接收位置。</span><span class="sxs-lookup"><span data-stu-id="574b8-314">A message box appears stating that you need to designate a receive location.</span></span> <span data-ttu-id="574b8-315">按一下 [確定] 及 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="574b8-315">Click **OK**, and then click **New**.</span></span>  
  
     ![](../core/media/298638b6-0eb8-49c4-8a2e-485571d070cf.gif "298638b6-0eb8-49c4-8a2e-485571d070cf")  
  
6.  <span data-ttu-id="574b8-316">輸入或選取屬性的下列值：</span><span class="sxs-lookup"><span data-stu-id="574b8-316">Type or select the following values for the properties:</span></span>  
  
     <span data-ttu-id="574b8-317">**名稱**:`FileInLoc`</span><span class="sxs-lookup"><span data-stu-id="574b8-317">**Name**: `FileInLoc`</span></span>  
  
     <span data-ttu-id="574b8-318">**類型**： **檔案**</span><span class="sxs-lookup"><span data-stu-id="574b8-318">**Type**: **File**</span></span>  
  
     <span data-ttu-id="574b8-319">**接收處理常式**： **BizTalkServerApplication**</span><span class="sxs-lookup"><span data-stu-id="574b8-319">**Receive Handler**: **BizTalkServerApplication**</span></span>  
  
     <span data-ttu-id="574b8-320">**接收管線**： **XMLReceive**</span><span class="sxs-lookup"><span data-stu-id="574b8-320">**Receive Pipeline**: **XMLReceive**</span></span>  
  
     ![](../core/media/613a5dbc-effe-4827-a72b-d16eef8d0e8a.gif "613a5dbc-effe-4827-a72b-d16eef8d0e8a")  
  
7.  <span data-ttu-id="574b8-321">按一下 開始  ，針對 接收資料夾 `C:\LABS\PS_TEST\FILEIN` 中輸入 **C:\LABS\PS_TEST\FILEIN**，然後按一下BizTalk Server 管理  。</span><span class="sxs-lookup"><span data-stu-id="574b8-321">Click **Configure** and type `C:\LABS\PS_TEST\FILEIN` for **Receive Folder**, and then click **OK** three times.</span></span>  
  
     ![](../core/media/513eebb0-58ca-4aaa-a33b-31700f9cf7a8.gif "513eebb0-58ca-4aaa-a33b-31700f9cf7a8")  
  
8.  <span data-ttu-id="574b8-322">按一下**\<無 >**如**PeopleSoft_Port**下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="574b8-322">Click **\<None>** for **PeopleSoft_Port** in the drop-down list.</span></span>  
  
9. <span data-ttu-id="574b8-323">選取 [新增傳送埠]  ，然後選取或輸入下列屬性值。</span><span class="sxs-lookup"><span data-stu-id="574b8-323">Select **New Send Port** and then select or type the following values for the properties.</span></span>  
  
     <span data-ttu-id="574b8-324">**名稱**:`PS_Test_Port`</span><span class="sxs-lookup"><span data-stu-id="574b8-324">**Name**: `PS_Test_Port`</span></span>  
  
     <span data-ttu-id="574b8-325">**類型**： **PeopleSoft**</span><span class="sxs-lookup"><span data-stu-id="574b8-325">**Type**: **PeopleSoft**</span></span>  
  
     <span data-ttu-id="574b8-326">**傳送處理常式**： **BizTalkServerApplication**</span><span class="sxs-lookup"><span data-stu-id="574b8-326">**Send Handler**: **BizTalkServerApplication**</span></span>  
  
     <span data-ttu-id="574b8-327">**管線**： **XMLTransmit** 和 **XMLReceive**</span><span class="sxs-lookup"><span data-stu-id="574b8-327">**Pipelines**: **XMLTransmit** and **XMLReceive**</span></span>  
  
10. <span data-ttu-id="574b8-328">按一下 [設定] ，然後輸入下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="574b8-328">Click **Configure**, and then enter the following property values:</span></span>  
  
    1.  <span data-ttu-id="574b8-329">**應用程式伺服器路徑**： **//Servername:9000**</span><span class="sxs-lookup"><span data-stu-id="574b8-329">**Application server path**: **//Servername:9000**</span></span>  
  
         <span data-ttu-id="574b8-330">Servername 是您的應用程式伺服器。</span><span class="sxs-lookup"><span data-stu-id="574b8-330">Servername is your application server.</span></span> <span data-ttu-id="574b8-331">這是此 PeopleSoft 系統的特定伺服器名稱或 IP 位址以及連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="574b8-331">This is the specific server name or IP address and port number for this PeopleSoft system.</span></span>  
  
    2.  <span data-ttu-id="574b8-332">**JAVA_HOME**： **C:\J2SDK1.4.2_08**</span><span class="sxs-lookup"><span data-stu-id="574b8-332">**JAVA_HOME**: **C:\J2SDK1.4.2_08**</span></span>  
  
         <span data-ttu-id="574b8-333">這個路徑是特定上的 Java SDK 安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="574b8-333">This path is specific to the Java SDK installation on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
    3.  <span data-ttu-id="574b8-334">**密碼**:\<輸入您的 PeopleSoft 密碼 ></span><span class="sxs-lookup"><span data-stu-id="574b8-334">**Password**: \<enter your PeopleSoft password></span></span>  
  
    4.  <span data-ttu-id="574b8-335">**PeopleSoft 8.x JAR 檔案**： **C:\PSJARS\VER841\PSJOA.JAR**</span><span class="sxs-lookup"><span data-stu-id="574b8-335">**PeopleSoft 8.x JAR files**: **C:\PSJARS\VER841\PSJOA.JAR**</span></span>  
  
     <span data-ttu-id="574b8-336">**使用者名稱：** \<輸入您的 PeopleSoft Userid> ></span><span class="sxs-lookup"><span data-stu-id="574b8-336">**User name:** \<enter your PeopleSoft UserID></span></span>  
  
11. <span data-ttu-id="574b8-337">按兩下 [確定]  關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="574b8-337">Click **OK** twice to close the dialog boxes.</span></span>  
  
12. <span data-ttu-id="574b8-338">在 設定 Applicationwindow 中，按一下  **\<無 >**如**FileOut**下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="574b8-338">In the Configure Applicationwindow, click **\<None>** for **FileOut** in the drop-down list.</span></span>  
  
13. <span data-ttu-id="574b8-339">選取 [新增傳送埠]  ，然後選取或輸入下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="574b8-339">Select **New Send Port** and type or select the following values for the properties:</span></span>  
  
     <span data-ttu-id="574b8-340">**名稱**:`FileOutPort`</span><span class="sxs-lookup"><span data-stu-id="574b8-340">**Name**: `FileOutPort`</span></span>  
  
     <span data-ttu-id="574b8-341">**類型**： **檔案**</span><span class="sxs-lookup"><span data-stu-id="574b8-341">**Type**: **File**</span></span>  
  
     <span data-ttu-id="574b8-342">**傳送處理常式**： **BizTalkServerApplication**</span><span class="sxs-lookup"><span data-stu-id="574b8-342">**Send Handler**: **BizTalkServerApplication**</span></span>  
  
     <span data-ttu-id="574b8-343">**傳送管線**： **XMLTransmit**</span><span class="sxs-lookup"><span data-stu-id="574b8-343">**Send Pipeline**: **XMLTransmit**</span></span>  
  
14. <span data-ttu-id="574b8-344">按一下**設定**和型別`C:\Labs\PS_Test\FileOut`如**目的地資料夾。**</span><span class="sxs-lookup"><span data-stu-id="574b8-344">Click **Configure** and type`C:\Labs\PS_Test\FileOut` for **Destination Folder.**</span></span> <span data-ttu-id="574b8-345">保留**%MessageID%.xml**如**檔案名稱**因為這會產生唯一的檔案，每個訊息。</span><span class="sxs-lookup"><span data-stu-id="574b8-345">Keep **%MessageID%.xml** for **File Name** because this results in a unique file for each message.</span></span>  
  
15. <span data-ttu-id="574b8-346">按三下 [確定]  關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="574b8-346">Click **OK** three times to close the dialog boxes.</span></span>  
  
16. <span data-ttu-id="574b8-347">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下滑鼠右鍵**PS_Test**應用程式，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="574b8-347">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console,right-click the **PS_Test** application and then click **Start**.</span></span>  
  
     ![](../core/media/7bf30707-c7c6-409f-af18-9c9dfeb0de58.gif "7bf30707-c7c6-409f-af18-9c9dfeb0de58")  
  
##### <a name="to-test-the-orchestration"></a><span data-ttu-id="574b8-348">測試協調流程</span><span class="sxs-lookup"><span data-stu-id="574b8-348">To test the orchestration</span></span>  
  
1.  <span data-ttu-id="574b8-349">在 **C:\Labs\PS_Test** 目錄中，將 **Samplequery.xml** 檔案變更為下列所示：</span><span class="sxs-lookup"><span data-stu-id="574b8-349">In the **C:\Labs\PS_Test** directory, change the **Samplequery.xml** file to the following:</span></span>  
  
    ```  
    <ns0:Get xmlns:ns0="http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]">  
      <ns0:SETID>SHARE</ns0:SETID>  
      <ns0:LOCATION>AUS01</ns0:LOCATION>  
      <ns0:getHistory>true</ns0:getHistory>  
    </ns0:Get>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="574b8-350">**SHARE** 資料值將用在所有系統上。</span><span class="sxs-lookup"><span data-stu-id="574b8-350">The **SHARE** data value will be used on all systems.</span></span> <span data-ttu-id="574b8-351">不過，您將在使用在此 XML 檔案中的 **位置** 值必須存在您的系統上。</span><span class="sxs-lookup"><span data-stu-id="574b8-351">However the value you will use for **Location** in this XML file must exist on your system.</span></span> <span data-ttu-id="574b8-352">您已在實驗室 1 中發現這個原則。</span><span class="sxs-lookup"><span data-stu-id="574b8-352">You found this out in Lab 1.</span></span>  
  
2.  <span data-ttu-id="574b8-353">儲存變更，並將檔案複製到 **C:\Labs\PS_Test\FileIn** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="574b8-353">Save the changes and copy the file to the **C:\Labs\PS_Test\FileIn** folder.</span></span> <span data-ttu-id="574b8-354">這是啟動協調流程處理序的 FileIn 接收位置。</span><span class="sxs-lookup"><span data-stu-id="574b8-354">This is the receive location for FileIn that starts the orchestration process.</span></span>  
  
3.  <span data-ttu-id="574b8-355">XML 檔案很快就會出現在 **C:\Labs\PS_Test\FileOut** 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="574b8-355">In a few seconds, an XML file should appear in the **C:\Labs\PS_Test\FileOut** folder.</span></span> <span data-ttu-id="574b8-356">其中應包含來自位置為 AUS01 之記錄的資料。</span><span class="sxs-lookup"><span data-stu-id="574b8-356">This should contain the data from the record where the location is AUS01.</span></span>  
  
     ![](../core/media/1320ea3c-b2bc-4717-b200-c3c550079ccb.gif "1320ea3c-b2bc-4717-b200-c3c550079ccb")  
  
     <span data-ttu-id="574b8-357">這份傳回的記錄資料應符合針對 PeopleSoft 實驗室 1 中 PeopleSoft 系統的查詢所傳回的內容。</span><span class="sxs-lookup"><span data-stu-id="574b8-357">This returned record data should match what was returned by the query against the PeopleSoft system in PeopleSoft Lab 1.</span></span> <span data-ttu-id="574b8-358">藉由比較值取得在實驗室 1 中，特別是**Address1**和**address2 一起顯示**到這裡所顯示的線條**\<位置： ADDRESS1 >**和 **\<address2 一起顯示的位置： >**欄位，您可以確認**取得**方法運作正常。</span><span class="sxs-lookup"><span data-stu-id="574b8-358">By comparing the values you obtained in Lab 1, specifically the **Address1** and **Address2** lines, to what is shown here in the **\<LOCATION:ADDRESS1>** and **\<LOCATION:ADDRESS2>** fields, you can verify that the **Get** method worked properly.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="574b8-359">摘要</span><span class="sxs-lookup"><span data-stu-id="574b8-359">Summary</span></span>  
 <span data-ttu-id="574b8-360">在此實驗室中，您先確認了已正確設定必要條件，以便存取 PeopleSoft 系統。</span><span class="sxs-lookup"><span data-stu-id="574b8-360">In this lab, you first verified that the prerequisites were set up correctly to access the PeopleSoft system.</span></span> <span data-ttu-id="574b8-361">之後，使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]來建立新的 BizTalk 專案包含協調流程。</span><span class="sxs-lookup"><span data-stu-id="574b8-361">Then you used [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to create a new BizTalk project containing an orchestration.</span></span> <span data-ttu-id="574b8-362">您設定了此協調流程，以使用 PeopleSoft 配接器自 PeopleSoft 系統取得資料。</span><span class="sxs-lookup"><span data-stu-id="574b8-362">You configured the BizTalk orchestration to use the PeopleSoft adapter to get data from the PeopleSoft system.</span></span> <span data-ttu-id="574b8-363">為了設定協調流程，您建立了傳送、接收與傳送/接收埠。</span><span class="sxs-lookup"><span data-stu-id="574b8-363">To configure the orchestration, you created send, receive, and send/receive ports.</span></span> <span data-ttu-id="574b8-364">您將這些連接埠繫結至 PeopleSoft 配接器，並指派訊息到適當的連接埠。</span><span class="sxs-lookup"><span data-stu-id="574b8-364">You bound these ports to the PeopleSoft adapter, and assigned messages to the appropriate ports.</span></span>  
  
 <span data-ttu-id="574b8-365">當您完成 BizTalk 專案之後，您使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]建置和部署它。</span><span class="sxs-lookup"><span data-stu-id="574b8-365">After you completed the BizTalk project, you used [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to build and deploy it.</span></span> <span data-ttu-id="574b8-366">然後設定了新的應用程式並加以執行，以從 PeopleSoft 系統取得資料。</span><span class="sxs-lookup"><span data-stu-id="574b8-366">You then configured your new application and ran it to get data from the PeopleSoft system.</span></span> <span data-ttu-id="574b8-367">為了確定應用程式正確運作，您將其輸出 XML 檔與在實驗室 1 中接收自 PeopleSoft 系統的檔案做比較。</span><span class="sxs-lookup"><span data-stu-id="574b8-367">To verify that the application worked correctly, you compared its output XML file to the file that you received from the PeopleSoft system in Lab 1.</span></span>