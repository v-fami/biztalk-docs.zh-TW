---
title: 執行 PeopleSoft Enterprise Get 範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb54f14c-3fce-44d6-91bb-cb1ca38a20da
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1e4601264b8dc407d1cc1bed323b4d3504bc91d
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50753246"
---
# <a name="execute-a-peoplesoft-enterprise-sample-get"></a><span data-ttu-id="3675e-102">執行 PeopleSoft Enterprise Get 範例</span><span class="sxs-lookup"><span data-stu-id="3675e-102">Execute a PeopleSoft Enterprise Sample Get</span></span>
<span data-ttu-id="3675e-103">您可以從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統使用 PeopleSoft 配接器存取 PeopleSoft 系統。</span><span class="sxs-lookup"><span data-stu-id="3675e-103">The PeopleSoft system is accessible from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system by using the PeopleSoft adapter.</span></span> <span data-ttu-id="3675e-104">此配接器隨附[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3675e-104">This adapter is included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>
  
 <span data-ttu-id="3675e-105">這是 PeopleSoft 實驗室工作的第二個部分。</span><span class="sxs-lookup"><span data-stu-id="3675e-105">This is the second part of the PeopleSoft lab work.</span></span> <span data-ttu-id="3675e-106">在第一部分 (實驗室 1) 中，您可在不需 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 或其他 Microsoft 技術協助的情況下，手動存取及修改 PeopleSoft 系統上的資料。</span><span class="sxs-lookup"><span data-stu-id="3675e-106">In the first part (Lab 1), you manually accessed and modified data on the PeopleSoft system without the assistance of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or other Microsoft technologies.</span></span> <span data-ttu-id="3675e-107">在這個部分 (實驗室 2) 中，您將建立 BizTalk 協調流程，做為 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk 專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="3675e-107">In this part (Lab 2), you will create a BizTalk orchestration as part of a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project.</span></span> <span data-ttu-id="3675e-108">您將設定此協調流程上的連接埠，以使用 PeopleSoft 配接器自 PeopleSoft 系統取得資料。</span><span class="sxs-lookup"><span data-stu-id="3675e-108">You will configure ports on this orchestration to use the PeopleSoft adapter to get data from a PeopleSoft system.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3675e-109">先決條件</span><span class="sxs-lookup"><span data-stu-id="3675e-109">Prerequisites</span></span>  
  
- <span data-ttu-id="3675e-110">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3675e-110">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>
  
- <span data-ttu-id="3675e-111">Microsoft BizTalk Adapters for Enterprise Applications</span><span class="sxs-lookup"><span data-stu-id="3675e-111">Microsoft BizTalk Adapters for Enterprise Applications</span></span>  
  
- <span data-ttu-id="3675e-112">Microsoft Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3675e-112">Microsoft Visual Studio</span></span>  
  
- <span data-ttu-id="3675e-113">Sun Systems Java Development Kit (JDK) 1.4 (含) 以上版本</span><span class="sxs-lookup"><span data-stu-id="3675e-113">Sun Systems Java Development Kit (JDK) version 1.4 or higher</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3675e-114">請參閱[安裝及設定企業應用程式的介面卡](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md)的 JD Edwards、 PeopleSoft 和 TIBCO 配接器的重要組態資訊。</span><span class="sxs-lookup"><span data-stu-id="3675e-114">See [Install and configure the adapters for enterprise applications](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md) for key configuration information for the JD Edwards, PeopleSoft, and TIBCO adapters.</span></span>  
  
## <a name="lab-2---executing-a-peoplesoft-sample-get"></a><span data-ttu-id="3675e-115">實驗室 2 - 執行 PeopleSoft 的 Get 範例</span><span class="sxs-lookup"><span data-stu-id="3675e-115">Lab 2 - Executing a PeopleSoft Sample Get</span></span>  
 <span data-ttu-id="3675e-116">在這個實驗室中，您將針對 PeopleSoft 系統執行 **Get** 作業。</span><span class="sxs-lookup"><span data-stu-id="3675e-116">In this lab, you will execute a **Get** operation against the PeopleSoft system.</span></span> <span data-ttu-id="3675e-117">也就是說，您將執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="3675e-117">Specifically you will perform the following tasks:</span></span>  
  
- <span data-ttu-id="3675e-118">驗證 PeopleSoft 必要條件</span><span class="sxs-lookup"><span data-stu-id="3675e-118">Verify the PeopleSoft prerequisites</span></span>  
  
- <span data-ttu-id="3675e-119">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中設定 PeopleSoft 傳送埠</span><span class="sxs-lookup"><span data-stu-id="3675e-119">Set up a PeopleSoft send port in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>  
  
- <span data-ttu-id="3675e-120">建立 BizTalk 協調流程專案</span><span class="sxs-lookup"><span data-stu-id="3675e-120">Create a BizTalk orchestration project</span></span>  
  
- <span data-ttu-id="3675e-121">建置和部署專案</span><span class="sxs-lookup"><span data-stu-id="3675e-121">Build and deploy the project</span></span>  
  
- <span data-ttu-id="3675e-122">測試應用程式並檢視 XML 輸出</span><span class="sxs-lookup"><span data-stu-id="3675e-122">Test the application and view the XML output</span></span>  
  
## <a name="procedures-for-lab-2--executing-a-peoplesoft-sample-get"></a><span data-ttu-id="3675e-123">實驗室 2 程序 - 執行 PeopleSoft 的 Get 範例</span><span class="sxs-lookup"><span data-stu-id="3675e-123">Procedures for Lab 2- Executing a PeopleSoft Sample Get</span></span>  
 <span data-ttu-id="3675e-124">PeopleSoft 系統的適當介面存取需要兩個檔案：PSJOA.JAR 和 GET_CI_INFO.PC。</span><span class="sxs-lookup"><span data-stu-id="3675e-124">Two files are necessary for proper interface access to a PeopleSoft system: PSJOA.JAR and GET_CI_INFO.PC.</span></span> <span data-ttu-id="3675e-125">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上，PeopleSoft 配接器會使用 PeopleSoft Java 介面與 PeopleSoft 系統通訊。</span><span class="sxs-lookup"><span data-stu-id="3675e-125">On the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer, the PeopleSoft adapter communicates with the PeopleSoft system by using the PeopleSoft Java interface.</span></span> <span data-ttu-id="3675e-126">此介面是由 PSJOA.JAR 檔案所提供。</span><span class="sxs-lookup"><span data-stu-id="3675e-126">This interface is supplied by the PSJOA.JAR file.</span></span> <span data-ttu-id="3675e-127">放置在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的此檔案複本來源，通常來自所存取之 PeopleSoft 伺服器系統的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="3675e-127">A copy of this file placed onto the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] typically comes from the administrator of the PeopleSoft server system that is being accessed.</span></span> <span data-ttu-id="3675e-128">在此實驗室中，PSJOA.JAR 的複本位在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上的 C:\PSJars\Ver841\ 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3675e-128">In this lab, a copy of PSJOA.JAR exists in the C:\PSJars\Ver841\ folder on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="3675e-129">此檔案的位置是在 PeopleSoft 配接器組態屬性中所指定。</span><span class="sxs-lookup"><span data-stu-id="3675e-129">The location of this file is specified in the PeopleSoft adapter configuration properties.</span></span>  
  
 <span data-ttu-id="3675e-130">PeopleSoft 系統本身必須安裝自訂元件介面 (CI)。</span><span class="sxs-lookup"><span data-stu-id="3675e-130">On the PeopleSoft system itself, a custom component interface (CI) must be installed.</span></span> <span data-ttu-id="3675e-131">這可讓配接器在配接器組態期間瀏覽 PeopleSoft 物件。</span><span class="sxs-lookup"><span data-stu-id="3675e-131">This allows the adapter to browse PeopleSoft objects during adapter configuration.</span></span> <span data-ttu-id="3675e-132">呼叫自訂元件介面 (從 [新增產生的項目] 步驟中) 可取得可存取 PeopleSoft 物件的清單。</span><span class="sxs-lookup"><span data-stu-id="3675e-132">The custom component interface is called (from within the Add Generated Items step) to get a list of accessible PeopleSoft objects.</span></span> <span data-ttu-id="3675e-133">這些物件會判斷提供給用戶端系統的 PeopleSoft 公開功能。</span><span class="sxs-lookup"><span data-stu-id="3675e-133">These objects determine exposed PeopleSoft functionality available to the client system.</span></span>  
  
 <span data-ttu-id="3675e-134">特別是自訂元件 GET_CI_INFO，必須在初始安裝期間安裝於 PeopleSoft 系統上。</span><span class="sxs-lookup"><span data-stu-id="3675e-134">Specifically the custom component, GET_CI_INFO, must be installed on the PeopleSoft system once during initial setup.</span></span> <span data-ttu-id="3675e-135">您可以修改這個檔案以限制 GET_CI_INFO 所公開的項目 (預設會公開 PeopleSoft 系統內的所有元件介面)。</span><span class="sxs-lookup"><span data-stu-id="3675e-135">This file can be modified to limit what the GET_CI_INFO exposes (by default it exposes all component interfaces within the PeopleSoft system).</span></span> <span data-ttu-id="3675e-136">其來源位於下列預設位置中的 GET_CI_INFO 文字檔：</span><span class="sxs-lookup"><span data-stu-id="3675e-136">Its source is found in the GET_CI_INFO.PC text file at the following default location:</span></span>  
  
 <span data-ttu-id="3675e-137">**C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r) \Config**</span><span class="sxs-lookup"><span data-stu-id="3675e-137">**C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r)\Config**</span></span>  
  
 <span data-ttu-id="3675e-138">提供一般指示 GET_CI_INFO 元件介面安裝至 PeopleSoft[安裝及設定企業應用程式的介面卡](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="3675e-138">General instructions about installing the GET_CI_INFO component interface into PeopleSoft are provided in [Install and configure the adapters for enterprise applications](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md).</span></span> <span data-ttu-id="3675e-139">這些指示適用於經驗豐富的 PeopleSoft 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="3675e-139">These instructions are for an experienced PeopleSoft administrator.</span></span>  
  
## <a name="step-1-confirm-the-peoplesoft-rerequisites"></a><span data-ttu-id="3675e-140">步驟 1： 確認 PeopleSoft rerequisites</span><span class="sxs-lookup"><span data-stu-id="3675e-140">Step 1: Confirm the PeopleSoft rerequisites</span></span>  
 <span data-ttu-id="3675e-141">在您開始建立搭配 PeopleSoft 配接器使用的 BizTalk 專案之前，必須先確定所有事項都已正確設定，以便存取 PeopleSoft。</span><span class="sxs-lookup"><span data-stu-id="3675e-141">Before you start creating a BizTalk project for use with the PeopleSoft adapter, you need to be sure that everything is set up correctly to access PeopleSoft.</span></span>  
  
1. <span data-ttu-id="3675e-142">確認 PSJOA。JAR 檔案存在於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]的 C:\psjars\ver841 資料夾中的電腦。</span><span class="sxs-lookup"><span data-stu-id="3675e-142">Confirm that the PSJOA.JAR file exists on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer in the C:\psjars\ver841 folder.</span></span> <span data-ttu-id="3675e-143">(這個檔案在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上可能會位於不同的位置。</span><span class="sxs-lookup"><span data-stu-id="3675e-143">(This file can exist at a different location on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="3675e-144">在下方提供的組態中，會假設檔案是在這個位置。)</span><span class="sxs-lookup"><span data-stu-id="3675e-144">In the configuration given below, it is assumed the file is at this location.)</span></span>  
  
2. <span data-ttu-id="3675e-145">請確認 get_ci_info.pc 檔案位於 C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r) \Config 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3675e-145">Confirm that the get_ci_info.pc file exists in the C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r)\Config folder.</span></span>  
  
3. <span data-ttu-id="3675e-146">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**主控台根目錄**，展開[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**管理**，展開**BizTalk 群組**，展開**平台設定**，然後展開**配接器**。</span><span class="sxs-lookup"><span data-stu-id="3675e-146">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **Console Root**, expand [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span> <span data-ttu-id="3675e-147">請確定已安裝 PeopleSoft 配接器，並且出現在清單上。</span><span class="sxs-lookup"><span data-stu-id="3675e-147">Ensure that the PeopleSoft adapter is installed and on the list.</span></span>  
  
    <span data-ttu-id="3675e-148">如果未安裝 PeopleSoft 配接器，請安裝 BizTalk Adapters for Enterprise Applications (請參閱稍早的＜必要條件＞一節)。</span><span class="sxs-lookup"><span data-stu-id="3675e-148">If the PeopleSoft adapter is not installed, install the BizTalk Adapters for Enterprise Applications (see the earlier "Prerequisites" section).</span></span> <span data-ttu-id="3675e-149">安裝配接器之後，用滑鼠右鍵按一下 [配接器]  ，然後按一下 [新增 - 配接器]  安裝 PeopleSoft 配接器。</span><span class="sxs-lookup"><span data-stu-id="3675e-149">After the adapters are installed, right-click **Adapters** and then click **New - Adapter** to install the PeopleSoft adapter.</span></span> <span data-ttu-id="3675e-150">重新啟動主控件執行個體，這個選項才會生效。</span><span class="sxs-lookup"><span data-stu-id="3675e-150">Restart the host instance for this to take effect.</span></span>  
  
## <a name="step-2-create-a-send-port-for-peoplesoft"></a><span data-ttu-id="3675e-151">步驟 2： 建立 PeopleSoft 傳送埠</span><span class="sxs-lookup"><span data-stu-id="3675e-151">Step 2: Create a Send Port for PeopleSoft</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] <span data-ttu-id="3675e-152">必須具有要用於與 PeopleSoft 系統通訊的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="3675e-152">needs to have a send port to use for communicating with the PeopleSoft system.</span></span> <span data-ttu-id="3675e-153">此傳送埠最終會繫結至協調流程的邏輯連接埠。</span><span class="sxs-lookup"><span data-stu-id="3675e-153">This send port will eventually be bound to the orchestration's logical ports.</span></span>  
  
1. <span data-ttu-id="3675e-154">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**主控台根目錄**，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開**BizTalk.EnterpriseApplication。**</span><span class="sxs-lookup"><span data-stu-id="3675e-154">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **Console Root**, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk.EnterpriseApplication.**</span></span>  
  
2. <span data-ttu-id="3675e-155">用滑鼠右鍵按一下 [傳送埠] ，再按一下 [新增] ，然後選取 [靜態請求-回應傳送埠] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-155">Right-click **Send Ports**, click **New**, and then select **Static Solicit-Response Send Port**.</span></span> <span data-ttu-id="3675e-156">在 [傳送埠屬性]  對話方塊中輸入屬性的下列值：</span><span class="sxs-lookup"><span data-stu-id="3675e-156">In the **Send Port Properties** dialog box, enter the following values for the properties:</span></span>  
  
   1.  <span data-ttu-id="3675e-157">**名稱：**  `PeopleSoftSamplePort`</span><span class="sxs-lookup"><span data-stu-id="3675e-157">**Name:**  `PeopleSoftSamplePort`</span></span>  
  
   2.  <span data-ttu-id="3675e-158">**類型：**  `PeopleSoft`</span><span class="sxs-lookup"><span data-stu-id="3675e-158">**Type:**  `PeopleSoft`</span></span>  
  
   3.  <span data-ttu-id="3675e-159">**傳送處理常式：**  `BizTalkServerApplication`</span><span class="sxs-lookup"><span data-stu-id="3675e-159">**Send handler:**  `BizTalkServerApplication`</span></span>  
  
   4.  <span data-ttu-id="3675e-160">**傳送管線︰**  `XMLTransmit`</span><span class="sxs-lookup"><span data-stu-id="3675e-160">**Send pipeline:**  `XMLTransmit`</span></span>  
  
   5.  <span data-ttu-id="3675e-161">**接收管線︰**  `XMLReceive`</span><span class="sxs-lookup"><span data-stu-id="3675e-161">**Receive pipeline:**  `XMLReceive`</span></span>  
  
3. <span data-ttu-id="3675e-162">按一下 [設定] ，然後輸入下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="3675e-162">Click **Configure**, and then enter the following property values:</span></span>  
  
   1. <span data-ttu-id="3675e-163">**應用程式伺服器路徑**： **//Servername:9000**</span><span class="sxs-lookup"><span data-stu-id="3675e-163">**Application server path**: **//Servername:9000**</span></span>  
  
       <span data-ttu-id="3675e-164">Servername 是您的應用程式伺服器。</span><span class="sxs-lookup"><span data-stu-id="3675e-164">Servername is your application server.</span></span> <span data-ttu-id="3675e-165">這是此 PeopleSoft 系統的特定伺服器名稱或 IP 位址以及連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="3675e-165">This is the specific server name or IP address and port number for this PeopleSoft system.</span></span>  
  
   2. <span data-ttu-id="3675e-166">**JAVA_HOME**： **C:\J2SDK1.4.2_08**</span><span class="sxs-lookup"><span data-stu-id="3675e-166">**JAVA_HOME**: **C:\J2SDK1.4.2_08**</span></span>  
  
       <span data-ttu-id="3675e-167">這個路徑在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上是 Java SDK 安裝專用。</span><span class="sxs-lookup"><span data-stu-id="3675e-167">This path is specific to the Java SDK installation on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
   3. <span data-ttu-id="3675e-168">**密碼**:\<輸入您的 PeopleSoft 密碼\></span><span class="sxs-lookup"><span data-stu-id="3675e-168">**Password**: \<enter your PeopleSoft password\></span></span>  
  
   4. <span data-ttu-id="3675e-169">**PeopleSoft 8.x JAR 檔案**： **C:\PSJARS\VER841\PSJOA.JAR**</span><span class="sxs-lookup"><span data-stu-id="3675e-169">**PeopleSoft 8.x JAR files**: **C:\PSJARS\VER841\PSJOA.JAR**</span></span>  
  
   5. <span data-ttu-id="3675e-170">**使用者名稱：** \<輸入您的 PeopleSoft Userid>\></span><span class="sxs-lookup"><span data-stu-id="3675e-170">**User name:** \<enter your PeopleSoft UserID\></span></span>  
  
      <span data-ttu-id="3675e-171">![](../core/media/7bf30707-c7c6-409f-af18-9c9dfeb0de58.gif "7bf30707-c7c6-409f-af18-9c9dfeb0de58")</span><span class="sxs-lookup"><span data-stu-id="3675e-171">![](../core/media/7bf30707-c7c6-409f-af18-9c9dfeb0de58.gif "7bf30707-c7c6-409f-af18-9c9dfeb0de58")</span></span>  
  
4. <span data-ttu-id="3675e-172">按兩下 [確定]  關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3675e-172">Click **OK** twice to close the dialog boxes.</span></span>  
  
## <a name="step-3-create-a-biztalk-orchestration-project"></a><span data-ttu-id="3675e-173">步驟 3： 建立 BizTalk 協調流程專案</span><span class="sxs-lookup"><span data-stu-id="3675e-173">Step 3: Create a BizTalk Orchestration Project</span></span>  
 <span data-ttu-id="3675e-174">現在您將會在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中建立 BizTalk 專案，並於專案中設定協調流程，以處理 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 PeopleSoft 系統之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="3675e-174">Now you will create a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and configure an orchestration in the project to handle communication between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the PeopleSoft system.</span></span> <span data-ttu-id="3675e-175">您將新增傳送和接收埠、建置專案，然後部署專案。</span><span class="sxs-lookup"><span data-stu-id="3675e-175">You will add send and receive ports, build the project, and then deploy the project.</span></span>  
  
1. <span data-ttu-id="3675e-176">開啟 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 並在 C:\LABS 資料夾中建立新的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="3675e-176">Open [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and create a new BizTalk project in the C:\LABS folder.</span></span> <span data-ttu-id="3675e-177">在 [檔案]  功能表上，按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-177">On the **File** menu, click **New**.</span></span> <span data-ttu-id="3675e-178">[新增專案]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="3675e-178">The **New Project** dialog box appears.</span></span> <span data-ttu-id="3675e-179">在 [傳送埠屬性]  區段下，選取 [空白 BizTalk Server 專案] </span><span class="sxs-lookup"><span data-stu-id="3675e-179">In the **Templates** section, select **Empty BizTalk Server project.**</span></span> <span data-ttu-id="3675e-180">請輸入`PS_Test`做為唯一的專案名稱，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3675e-180">Enter `PS_Test` as the unique project name, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="3675e-181">在方案總管中，以滑鼠右鍵按一下專案，按一下 [新增] 及 [新增產生的項目] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-181">In Solution Explorer, right-click the project, click **Add**, and then click **Add Generated Items**.</span></span> <span data-ttu-id="3675e-182">在 [類別]  窗格中選取 [新增配接器中繼資料]  ，在 [範本]  側選取 [新增配接器中繼資料]  ，然後按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-182">Select **Add Adapter Metadata** in the **Categories** pane, select **Add Adapter Metadata** on the **Templates** side, and then click **Add**.</span></span>  
  
3. <span data-ttu-id="3675e-183">在 [新增配接器精靈] 中，選取 [PeopleSoft Enterprise]  配接器，選取您在先前程序中所建立的 [PeopleSoftSamplePort]  傳送埠，然後按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-183">In the Add Adapter Wizard, select the **PeopleSoft Enterprise** adapter, select the **PeopleSoftSamplePort** send port that you created in the preceding procedure, and then click **Next**.</span></span>  
  
    <span data-ttu-id="3675e-184">![](../core/media/ed0dedc5-a8fb-444c-b884-e310cf56462c.gif "ed0dedc5-a8fb-444c-b884-e310cf56462c")</span><span class="sxs-lookup"><span data-stu-id="3675e-184">![](../core/media/ed0dedc5-a8fb-444c-b884-e310cf56462c.gif "ed0dedc5-a8fb-444c-b884-e310cf56462c")</span></span>  
  
4. <span data-ttu-id="3675e-185">在 [選取要匯入服務]  頁面上，展開 [PeopleSoft] ，然後展開 [CI] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-185">On the **Select Services to Import** page, expand **PeopleSoft**, and then expand **CI**.</span></span>  
  
    <span data-ttu-id="3675e-186">PeopleSoft 系統是由使用瀏覽代理程式的配接器所查核。</span><span class="sxs-lookup"><span data-stu-id="3675e-186">The PeopleSoft system is interrogated by the adapter using the Browsing Agent.</span></span> <span data-ttu-id="3675e-187">當您展開 [CI] 時，BrowsingAgent.exe 處理序會啟動 (您可以將其視為在工作管理員中執行) 並傳回如下圖所示的服務。</span><span class="sxs-lookup"><span data-stu-id="3675e-187">When you expand **CI**, the BrowsingAgent.exe process starts (you can view it as running in Task Manager) and returns the services shown in the following figure.</span></span>  
  
    <span data-ttu-id="3675e-188">![](../core/media/6988104c-6483-4df2-a637-3301628ea665.gif "6988104c-6483-4df2-a637-3301628ea665")</span><span class="sxs-lookup"><span data-stu-id="3675e-188">![](../core/media/6988104c-6483-4df2-a637-3301628ea665.gif "6988104c-6483-4df2-a637-3301628ea665")</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="3675e-189">從您的 PeopleSoft 系統取得及顯示的 PeopleSoft 服務，可能與此處顯示的服務稍有不同。</span><span class="sxs-lookup"><span data-stu-id="3675e-189">The PeopleSoft services obtained and displayed from your PeopleSoft system may be slightly different than the services displayed here.</span></span>  
  
5. <span data-ttu-id="3675e-190">向下捲動，選取 [位置] ，然後按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-190">Scroll down, select **LOCATION**, and then click **Finish**.</span></span>  
  
    <span data-ttu-id="3675e-191">![](../core/media/0506affd-3caa-47cb-9c25-f49c8a0ad614.gif "0506affd-3caa-47cb-9c25-f49c8a0ad614")</span><span class="sxs-lookup"><span data-stu-id="3675e-191">![](../core/media/0506affd-3caa-47cb-9c25-f49c8a0ad614.gif "0506affd-3caa-47cb-9c25-f49c8a0ad614")</span></span>  
  
6. <span data-ttu-id="3675e-192">在方案總管中，有新的 BizTalk 協調流程和兩個新的相關聯結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="3675e-192">In Solution Explorer, there is a new BizTalk orchestration and two new associated schema files.</span></span> <span data-ttu-id="3675e-193">這些檔案是由 [新增配接器精靈] 所建立。</span><span class="sxs-lookup"><span data-stu-id="3675e-193">These files are created by the Add Adapter Wizard.</span></span> <span data-ttu-id="3675e-194">按兩下 [BizTalk Orchestration.odx]  檔案開啟協調流程。</span><span class="sxs-lookup"><span data-stu-id="3675e-194">Double-click the **BizTalk Orchestration.odx** file to open the orchestration.</span></span>  
  
    <span data-ttu-id="3675e-195">![](../core/media/825c5690-78eb-4048-9a47-cd3fc7310b7b.gif "825c5690-78eb-4048-9a47-cd3fc7310b7b")</span><span class="sxs-lookup"><span data-stu-id="3675e-195">![](../core/media/825c5690-78eb-4048-9a47-cd3fc7310b7b.gif "825c5690-78eb-4048-9a47-cd3fc7310b7b")</span></span>  
  
   <span data-ttu-id="3675e-196">此協調流程以輸入形式接受 XML 檔案格式針對 PeopleSoft **Get** 方法格式化，以及將 XML 檔案傳送至 PeopleSoft 系統。</span><span class="sxs-lookup"><span data-stu-id="3675e-196">This orchestration accepts as input an XML file formatted for the PeopleSoft **Get** method and sends the XML file to the PeopleSoft system.</span></span> <span data-ttu-id="3675e-197">**Get** 方法會從 PeopleSoft 系統擷取位置資訊，並將它傳回至 BizTalk 協調流程。</span><span class="sxs-lookup"><span data-stu-id="3675e-197">The **Get** method retrieves location information from the PeopleSoft system and returns it to the BizTalk orchestration.</span></span> <span data-ttu-id="3675e-198">協調流程會使用連接埠來協助與配接器和 PeopleSoft 系統的通訊。</span><span class="sxs-lookup"><span data-stu-id="3675e-198">The orchestration uses ports to facilitate this communication with the adapter and the PeopleSoft system.</span></span> <span data-ttu-id="3675e-199">您將在此處設定的連接埠是用於接收和傳送 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="3675e-199">The ports you will configure here are for receiving and sending XML files.</span></span> <span data-ttu-id="3675e-200">外寄的 XML 檔案會告知 PeopleSoft 系統這是 **Get** 作業。</span><span class="sxs-lookup"><span data-stu-id="3675e-200">The outgoing XML file tells the PeopleSoft system that this is a **Get** operation.</span></span> <span data-ttu-id="3675e-201">內送的 XML 檔案會將位置資訊傳回至協調流程。</span><span class="sxs-lookup"><span data-stu-id="3675e-201">The incoming XML file returns the location information to the orchestration.</span></span>  
  
   <span data-ttu-id="3675e-202">若要完成協調流程，您需要建立及設定連接埠來接收和傳送 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="3675e-202">To complete the orchestration, you need to create and configure ports to receive and send the XML files.</span></span> <span data-ttu-id="3675e-203">首先，設定可接受初始 XML 輸入檔案的新接收埠 (其中包含 **Get** 方法)，來啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="3675e-203">First, set up a new receive port to accept the initial XML input file that contains the **Get** method to start the orchestration.</span></span>  
  
#### <a name="configure-a-receive-port"></a><span data-ttu-id="3675e-204">設定接收埠</span><span class="sxs-lookup"><span data-stu-id="3675e-204">Configure a receive port</span></span>  
  
1. <span data-ttu-id="3675e-205">在您上一個步驟中開啟的 BizTalk Orchestration.odx 檔案內，以滑鼠右鍵按一下左側連接埠介面，然後按一下 [新設定連接埠] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-205">Within the BizTalk Orchestration.odx file that you opened in the previous step, right-click the left port surface and then click **New Configured Port**.</span></span> <span data-ttu-id="3675e-206">如此將啟動 [連接埠組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="3675e-206">This starts the Port Configuration Wizard.</span></span> <span data-ttu-id="3675e-207">在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-207">On the **Welcome to the Port Configuration Wizard** page, click **Next**.</span></span>  
  
2. <span data-ttu-id="3675e-208">上**連接埠內容**頁面上，輸入`FileIn`如**名稱**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="3675e-208">On the **Port Properties** page, enter `FileIn` for **Name**, and then click **Next**.</span></span>  
  
3. <span data-ttu-id="3675e-209">在 [選取連接埠類型]  頁面上，選取 [建立新的連接埠類型] ，然後輸入或選取下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="3675e-209">In the **Select a Port Type** page, select **Create a new Port Type**, and then enter or select the following property values:</span></span>  
  
    <span data-ttu-id="3675e-210">**連接埠類型名稱**: `FileInPort`</span><span class="sxs-lookup"><span data-stu-id="3675e-210">**Port Type Name**: `FileInPort`</span></span>  
  
    <span data-ttu-id="3675e-211">**通訊模式**： **單向**</span><span class="sxs-lookup"><span data-stu-id="3675e-211">**Communication Pattern**: **One Way**</span></span>  
  
    <span data-ttu-id="3675e-212">**存取限制**： **內部 - 限制於此專案**</span><span class="sxs-lookup"><span data-stu-id="3675e-212">**Access Restrictions**: **Internal - limited to this project**</span></span>  
  
4. <span data-ttu-id="3675e-213">按 [下一步]  移至 [連接埠繫結]  頁面，然後選取下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="3675e-213">Click **Next** to go to the **Port Binding** page, and then select the following property values:</span></span>  
  
    <span data-ttu-id="3675e-214">**連接埠通訊方向**： **我將總是在此連接埠接收訊息**</span><span class="sxs-lookup"><span data-stu-id="3675e-214">**Port direction of communication**: **I'll always be receiving messages on this port**</span></span>  
  
    <span data-ttu-id="3675e-215">**連接埠繫結**： **稍後指定**</span><span class="sxs-lookup"><span data-stu-id="3675e-215">**Port binding**: **Specify later**</span></span>  
  
5. <span data-ttu-id="3675e-216">按 **[下一步]**，再按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="3675e-216">Click **Next**, and then click **Finish**.</span></span> <span data-ttu-id="3675e-217">您將使用 FILE 配接器，來接受此檔案為來自磁碟的輸入。</span><span class="sxs-lookup"><span data-stu-id="3675e-217">You will use the File adapter to accept this file as input from disk.</span></span>  
  
   <span data-ttu-id="3675e-218">接下來，建立傳送埠以接受包含呼叫 PeopleSoft **Get** 方法所得位置的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="3675e-218">Next, create a send port to accept the XML file containing the location results from the call to the PeopleSoft **Get** method.</span></span> <span data-ttu-id="3675e-219">協調流程會使用 FILE 配接器，經由此傳送埠將該 XML 檔案寫入磁碟。</span><span class="sxs-lookup"><span data-stu-id="3675e-219">The orchestration uses the File adapter to write that XML file to disk through this send port.</span></span>  
  
#### <a name="configure-a-send-port"></a><span data-ttu-id="3675e-220">設定傳送埠</span><span class="sxs-lookup"><span data-stu-id="3675e-220">Configure a send port</span></span>  
  
1. <span data-ttu-id="3675e-221">在 BizTalk Orchestration.odx 檔案內，以滑鼠右鍵按一下左側連接埠介面，然後按一下 [新設定連接埠] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-221">Within the BizTalk Orchestration.odx file, right-click the left port surface and then click **New Configured Port**.</span></span> <span data-ttu-id="3675e-222">如此將啟動 [連接埠組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="3675e-222">This starts the Port Configuration Wizard.</span></span> <span data-ttu-id="3675e-223">在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-223">On the **Welcome to the Port Configuration Wizard** page click **Next**.</span></span>  
  
2. <span data-ttu-id="3675e-224">上**連接埠內容**頁面上，輸入`FileOut`如**名稱**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="3675e-224">On the **Port Properties** page, enter `FileOut` for **Name**, and then click **Next**.</span></span>  
  
3. <span data-ttu-id="3675e-225">在 [選取連接埠類型]  頁面上，選取 [建立新的連接埠類型] ，然後輸入或選取下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="3675e-225">On the **Select a Port Type** page, select **Create a new Port Type**, and then enter or select the following property values:</span></span>  
  
    <span data-ttu-id="3675e-226">**連接埠類型名稱**: `FileOutPort`</span><span class="sxs-lookup"><span data-stu-id="3675e-226">**Port Type Name**: `FileOutPort`</span></span>  
  
    <span data-ttu-id="3675e-227">**通訊模式**： **單向**</span><span class="sxs-lookup"><span data-stu-id="3675e-227">**Communication Pattern**: **One Way**</span></span>  
  
    <span data-ttu-id="3675e-228">**存取限制**： **內部 - 限制於此專案**</span><span class="sxs-lookup"><span data-stu-id="3675e-228">**Access Restrictions**: **Internal - limited to this project**</span></span>  
  
4. <span data-ttu-id="3675e-229">按 [下一步]  移至 [連接埠繫結]  頁面，然後選取下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="3675e-229">Click **Next** to go to the **Port Binding** page, and then select the following property values:</span></span>  
  
    <span data-ttu-id="3675e-230">**連接埠通訊方向**： **我將總是在此連接埠傳送訊息**</span><span class="sxs-lookup"><span data-stu-id="3675e-230">**Port direction of communication**: **I'll always be sending messages on this port**</span></span>  
  
    <span data-ttu-id="3675e-231">**連接埠繫結**： **稍後指定**</span><span class="sxs-lookup"><span data-stu-id="3675e-231">**Port binding**: **Specify later**</span></span>  
  
5. <span data-ttu-id="3675e-232">按 **[下一步]**，再按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="3675e-232">Click **Next**, and then click **Finish**.</span></span>  
  
   <span data-ttu-id="3675e-233">最後，建立傳送/接收埠，以將包含 **Get** 方法的初始 XML 輸入檔案傳送至 PeopleSoft 系統。</span><span class="sxs-lookup"><span data-stu-id="3675e-233">Finally, create a send/receive port to send the initial XML input file containing the **Get** method to the PeopleSoft system.</span></span> <span data-ttu-id="3675e-234">此連接埠也會接收包含 PeopleSoft 系統上 **Get** 方法呼叫所得位置資訊的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="3675e-234">This port will also receive an XML file containing the location information that results from the **Get** method call on the PeopleSoft system.</span></span>  
  
#### <a name="configure-a-sendreceive-port"></a><span data-ttu-id="3675e-235">設定傳送/接收埠</span><span class="sxs-lookup"><span data-stu-id="3675e-235">Configure a send/receive port</span></span>  
  
1. <span data-ttu-id="3675e-236">在 BizTalk Orchestration.odx 檔案內，以滑鼠右鍵按一下右側連接埠介面，然後按一下 [新設定連接埠] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-236">Within the BizTalk Orchestration.odx file, right-click the right port surface and then click **New Configured Port**.</span></span> <span data-ttu-id="3675e-237">如此將啟動 [連接埠組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="3675e-237">This starts the Port Configuration Wizard.</span></span> <span data-ttu-id="3675e-238">在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-238">On the **Welcome to the Port Configuration Wizard** page, click **Next**.</span></span>  
  
2. <span data-ttu-id="3675e-239">上**連接埠內容**頁面上，輸入`PeopleSoft_Port`如**名稱**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="3675e-239">On the **Port Properties** page, enter `PeopleSoft_Port` for **Name**, and then click **Next**.</span></span>  
  
3. <span data-ttu-id="3675e-240">在 **[選取連接埠類型]** 頁面上，選取 **[使用現有連接埠類型]**。</span><span class="sxs-lookup"><span data-stu-id="3675e-240">On the **Select a Port Type** page, select **Use an existing Port Type**.</span></span> <span data-ttu-id="3675e-241">針對 [可用的連接埠類型] ，選取 [PS_Test.LOCATION] ，然後按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-241">For **Available Port Types**, select **PS_Test.LOCATION**, and then click **Next**.</span></span>  
  
    <span data-ttu-id="3675e-242">![](../core/media/d8b443ec-294d-4124-a29d-aeb42bbb107e.gif "d8b443ec-294d-4124-a29d-aeb42bbb107e")</span><span class="sxs-lookup"><span data-stu-id="3675e-242">![](../core/media/d8b443ec-294d-4124-a29d-aeb42bbb107e.gif "d8b443ec-294d-4124-a29d-aeb42bbb107e")</span></span>  
  
4. <span data-ttu-id="3675e-243">按 [下一步]  移至 [連接埠繫結]  頁面，然後選取下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="3675e-243">Click **Next** to go to the **Port Binding** page, and then select the following property values:</span></span>  
  
    <span data-ttu-id="3675e-244">**連接埠通訊方向**： **我將總是傳送要求並接收回應**</span><span class="sxs-lookup"><span data-stu-id="3675e-244">**Port direction of communication**: **I'll always be sending a request and receiving a response**</span></span>  
  
    <span data-ttu-id="3675e-245">**連接埠繫結**： **稍後指定**</span><span class="sxs-lookup"><span data-stu-id="3675e-245">**Port binding**: **Specify later**</span></span>  
  
5. <span data-ttu-id="3675e-246">按 **[下一步]**，再按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="3675e-246">Click **Next**, and then click **Finish**.</span></span>  
  
   <span data-ttu-id="3675e-247">在連接埠介面上顯示的是新的連接埠，以及 PeopleSoft 位置服務可用的方法。</span><span class="sxs-lookup"><span data-stu-id="3675e-247">Displayed on the port surface are the new port and the available methods for the PeopleSoft Location service.</span></span> <span data-ttu-id="3675e-248">稍後，您將會指定 PeopleSoft 配接器來傳送和接收來自 PeopleSoft 系統的檔案。</span><span class="sxs-lookup"><span data-stu-id="3675e-248">Later you will specify the PeopleSoft adapter to send and receive files from the PeopleSoft system.</span></span>  
  
   <span data-ttu-id="3675e-249">現在將兩個 **傳送** 圖形與兩個 **接收** 圖形插入協調流程，以連結至您剛才建立的連接埠。</span><span class="sxs-lookup"><span data-stu-id="3675e-249">Now insert two **Send** shapes and two **Receive** shapes into the orchestration to link to the ports you just created.</span></span>  
  
#### <a name="add-send-and-receive-shapes"></a><span data-ttu-id="3675e-250">新增傳送和接收圖形</span><span class="sxs-lookup"><span data-stu-id="3675e-250">Add Send and Receive shapes</span></span>  
  
1. <span data-ttu-id="3675e-251">從工具箱拖曳 **接收** 元件，緊解著將其放置於協調流程 (綠色圓形) 的開頭下方。</span><span class="sxs-lookup"><span data-stu-id="3675e-251">Drag a **Receive** component from the Toolbox and drop it immediately below the start of the orchestration (the green circle).</span></span> <span data-ttu-id="3675e-252">按一下 **接收**圖形，然後在 屬性 視窗中，輸入`FromDisk`如**名稱**，並設定**啟動**至`true`。</span><span class="sxs-lookup"><span data-stu-id="3675e-252">Click the **Receive** shape, and in the Properties window, enter `FromDisk` for the **Name**, and set **Activate** to `true`.</span></span> <span data-ttu-id="3675e-253">如此會在此接收埠收到內送文件時啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="3675e-253">Doing so will activate the orchestration when an incoming document is received on this receive port.</span></span>  
  
2. <span data-ttu-id="3675e-254">拖曳**傳送**元件從 [工具箱] 中，把它放在正下方**FromDiskReceive**圖形。</span><span class="sxs-lookup"><span data-stu-id="3675e-254">Drag a **Send** component from the Toolbox and drop it immediately below the **FromDiskReceive** shape.</span></span> <span data-ttu-id="3675e-255">按一下新**傳送**圖形，然後在 [屬性] 視窗中，輸入`ToPS`如**名稱**。</span><span class="sxs-lookup"><span data-stu-id="3675e-255">Click the new **Send** shape, and in the Properties window, enter `ToPS` for the **Name**.</span></span>  
  
3. <span data-ttu-id="3675e-256">拖曳**接收**元件從 [工具箱] 中，把它放在正下方**To_PS**<strong>傳送</strong>圖形。</span><span class="sxs-lookup"><span data-stu-id="3675e-256">Drag a **Receive** component from the Toolbox and drop it immediately below the **To_PS**<strong>Send</strong> shape.</span></span> <span data-ttu-id="3675e-257">按一下 **接收**圖形，然後在 屬性 視窗中，輸入`FromPS`如**名稱**。</span><span class="sxs-lookup"><span data-stu-id="3675e-257">Click the **Receive** shape, and in the Properties window, enter `FromPS` for the **Name**.</span></span>  
  
4. <span data-ttu-id="3675e-258">拖曳**傳送**元件從 [工具箱] 中，把它放在正下方**From_PSReceive**圖形。</span><span class="sxs-lookup"><span data-stu-id="3675e-258">Drag a **Send** component from the Toolbox and drop it immediately below the **From_PSReceive** shape.</span></span> <span data-ttu-id="3675e-259">按一下新**傳送**圖形，然後在 [屬性] 視窗中，輸入`ToDisk`如**名稱**。</span><span class="sxs-lookup"><span data-stu-id="3675e-259">Click the new **Send** shape, and in the Properties window, enter `ToDisk` for the **Name**.</span></span>  
  
   <span data-ttu-id="3675e-260">您必須先定義要處理的訊息類型，才可以將這些圖形連接至邏輯連接埠。</span><span class="sxs-lookup"><span data-stu-id="3675e-260">Before you can connect these shapes to logical ports, you need to define the message types to be processed.</span></span> <span data-ttu-id="3675e-261">配接器同時需要內送 (**要求** 方法) 訊息和外寄 (**回應** 方法) 訊息。</span><span class="sxs-lookup"><span data-stu-id="3675e-261">The adapter needs both an incoming (**Request** method) message and an outgoing (**Response** method) message.</span></span> <span data-ttu-id="3675e-262">每個方法的訊息都不同。</span><span class="sxs-lookup"><span data-stu-id="3675e-262">The messages for each of the methods are different.</span></span>  
  
   <span data-ttu-id="3675e-263">在此協調流程中，您只會使用 **Get-Request** 和 **Get-Response** 訊息。</span><span class="sxs-lookup"><span data-stu-id="3675e-263">In this orchestration, you are only using the **Get-Request** and **Get-Response** messages.</span></span> <span data-ttu-id="3675e-264">如果協調流程在更新資料，假設其使用 **UpdateEx** 方法，便會需要不同的要求/回應訊息。</span><span class="sxs-lookup"><span data-stu-id="3675e-264">If the orchestration were updating the data, say by using the **UpdateEx** method, it would require different Request/Response messages.</span></span>  
  
#### <a name="define-and-assign-messages-to-ports"></a><span data-ttu-id="3675e-265">定義和指派訊息到連接埠</span><span class="sxs-lookup"><span data-stu-id="3675e-265">Define and assign messages to ports</span></span>  
  
1.  <span data-ttu-id="3675e-266">在左側連接埠介面上，按一下 [FileIn]  連接埠上的 [要求]  。</span><span class="sxs-lookup"><span data-stu-id="3675e-266">On the left port surface, click **Request** on the **FileIn** port.</span></span> <span data-ttu-id="3675e-267">在 [屬性] 視窗中依序展開 [訊息類型] 和 [多部分訊息] ，然後按一下 [PS_Test.Get] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-267">In the Properties window, expand **Message Type**, expand **Multi-part Message**, and then click **PS_Test.Get**.</span></span>  
  
2.  <span data-ttu-id="3675e-268">在左側連接埠介面上，按一下 [FileOut]  連接埠上的 [要求]  。</span><span class="sxs-lookup"><span data-stu-id="3675e-268">On the left port surface, click **Request** on the **FileOut** port.</span></span> <span data-ttu-id="3675e-269">在 [屬性] 視窗中依序展開 [訊息類型] 及 [多部分訊息] ，然後按一下 [PS_Test.GetResponse] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-269">In the Properties window, expand **Message Type**, expand **Multi-part Message**, and then click **PS_Test.GetResponse**.</span></span>  
  
     <span data-ttu-id="3675e-270">![](../core/media/6b844ca3-322a-47b3-8cfd-68652c950752.gif "6b844ca3-322a-47b3-8cfd-68652c950752")</span><span class="sxs-lookup"><span data-stu-id="3675e-270">![](../core/media/6b844ca3-322a-47b3-8cfd-68652c950752.gif "6b844ca3-322a-47b3-8cfd-68652c950752")</span></span>  
  
3.  <span data-ttu-id="3675e-271">選取 [FileIn]  連接埠，並將其外寄傳送箭頭拖曳至 **FromDisk** 圖形上的內送反向接收箭頭。</span><span class="sxs-lookup"><span data-stu-id="3675e-271">Select the **FileIn** port and drag its outgoing send arrow to the incoming converse receive arrow on the **FromDisk** shape.</span></span>  
  
4.  <span data-ttu-id="3675e-272">選取 [FileOut]  連接埠，並將其內送反向接收箭頭拖曳至 **ToDisk** 圖形上的外寄傳送箭頭。</span><span class="sxs-lookup"><span data-stu-id="3675e-272">Select the **FileOut** port and drag its incoming converse receive arrow to the outgoing send arrow on the **ToDisk** shape.</span></span>  
  
5.  <span data-ttu-id="3675e-273">將現有的泛型訊息名稱重新命名為更具描述性的名稱，以遵守良好的應用程式設計原則。</span><span class="sxs-lookup"><span data-stu-id="3675e-273">Rename existing generic message names to more descriptive names to adhere to good application design principles.</span></span> <span data-ttu-id="3675e-274">在方案總管中，按一下 [協調流程檢視]  索引標籤。在 [訊息] 下，將 **Message_1** 的識別項變更為 [PS_Msg] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-274">In Solution Explorer, click the **Orchestration View** tab. Under **Messages**, change the identifier for **Message_1** to **PS_Msg**.</span></span> <span data-ttu-id="3675e-275">將 **Message_2** 的識別項變更為 [PS_Resp] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-275">Change the identifier for **Message_2** to **PS_Resp**.</span></span>  
  
     <span data-ttu-id="3675e-276">![](../core/media/5ec92b81-4a55-4d44-a360-78a6aaa64255.gif "5ec92b81-4a55-4d44-a360-78a6aaa64255")</span><span class="sxs-lookup"><span data-stu-id="3675e-276">![](../core/media/5ec92b81-4a55-4d44-a360-78a6aaa64255.gif "5ec92b81-4a55-4d44-a360-78a6aaa64255")</span></span>  
  
     <span data-ttu-id="3675e-277">![](../core/media/04b31c26-73a6-40a6-8d50-39c7c929d6a1.gif "04b31c26-73a6-40a6-8d50-39c7c929d6a1")</span><span class="sxs-lookup"><span data-stu-id="3675e-277">![](../core/media/04b31c26-73a6-40a6-8d50-39c7c929d6a1.gif "04b31c26-73a6-40a6-8d50-39c7c929d6a1")</span></span>  
  
6.  <span data-ttu-id="3675e-278">反白顯示 **To_PS** 傳送圖形並將其 **訊息** 屬性設為 [PS_Msg] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-278">Highlight the **To_PS** send shape and set its **Message** property to **PS_Msg**.</span></span>  
  
7.  <span data-ttu-id="3675e-279">反白顯示 **From_PS** 接收圖形並將其 **訊息** 屬性設為 [PS_Resp] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-279">Highlight the **From_PS** receive shape and set its **Message** property to **PS_Resp**.</span></span>  
  
8.  <span data-ttu-id="3675e-280">將 **To_PS** 傳送圖形連接至 **PeopleSoft_Port** 連接埠上 **Get** 方法的 **要求** 部分。</span><span class="sxs-lookup"><span data-stu-id="3675e-280">Connect the **To_PS** send shape to the **Request** portion of the **Get** method on the **PeopleSoft_Port** port.</span></span>  
  
9. <span data-ttu-id="3675e-281">將 **From_PS** 傳送圖形連接至 **PeopleSoft_Port** 連接埠上 **Get** 方法的 **回應** 部分。</span><span class="sxs-lookup"><span data-stu-id="3675e-281">Connect the **From_PS** send shape to the **Response** portion of the **Get** method on the **PeopleSoft_Port** port.</span></span>  
  
     <span data-ttu-id="3675e-282">![](../core/media/d16e02bc-954c-4aa2-99d6-3fee1222c730.gif "d16e02bc-954c-4aa2-99d6-3fee1222c730")</span><span class="sxs-lookup"><span data-stu-id="3675e-282">![](../core/media/d16e02bc-954c-4aa2-99d6-3fee1222c730.gif "d16e02bc-954c-4aa2-99d6-3fee1222c730")</span></span>  
  
## <a name="step-4-build-and-deploy-the-project"></a><span data-ttu-id="3675e-283">步驟 4： 建置並部署專案</span><span class="sxs-lookup"><span data-stu-id="3675e-283">Step 4: Build and Deploy the Project</span></span>  
 <span data-ttu-id="3675e-284">現在 BizTalk 專案已完成，您可以在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]中予以建置及部署。</span><span class="sxs-lookup"><span data-stu-id="3675e-284">Now the BizTalk project is complete and you can build and deploy it in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
1.  <span data-ttu-id="3675e-285">在 Visual Studio 中，指向**Visual Studio Tools**，然後選取**Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="3675e-285">In Visual Studio, point to **Visual Studio Tools**, and then select **Visual Studio Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="3675e-286">若要建置專案，您需要強式名稱金鑰檔。在命令提示字元中，輸入下列內容建立強式金鑰名稱檔：</span><span class="sxs-lookup"><span data-stu-id="3675e-286">To build the project, you need a strong name key file.At the command prompt, enter the following to create a strong name key file:</span></span>  
  
     <span data-ttu-id="3675e-287">**sn-k [labs.snk]**</span><span class="sxs-lookup"><span data-stu-id="3675e-287">**sn -k labs.snk**</span></span>  
  
3.  <span data-ttu-id="3675e-288">在方案總管中，以滑鼠右鍵按一下 [PS_Test]  專案，再按一下 [屬性]  為專案啟動 [專案設計工具]。</span><span class="sxs-lookup"><span data-stu-id="3675e-288">In Solution Explorer, right-click the **PS_Test** project and then click **Properties** to launch the Project Designer for the project..</span></span>  
  
4.  <span data-ttu-id="3675e-289">按一下 [ **簽署** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3675e-289">Click the **Signing** tab.</span></span>  
  
5.  <span data-ttu-id="3675e-290">選取 **[簽署組件]** 選項、按一下 **[選擇強式名稱金鑰檔]** 選項的下拉式清單，然後按一下 **[瀏覽]**。</span><span class="sxs-lookup"><span data-stu-id="3675e-290">Select **Sign the assembly** option, click drop-down list for the **Choose a strong name key file** option, and then click **Browse**.</span></span>  
  
6.  <span data-ttu-id="3675e-291">瀏覽並選取金鑰檔： **[labs.snk]**，然後按一下 **[開啟]**。</span><span class="sxs-lookup"><span data-stu-id="3675e-291">Browse to select the key file: **labs.snk**, and then click **Open**.</span></span>  
  
7.  <span data-ttu-id="3675e-292">按一下 [專案設計工具] 中的 **[部署]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3675e-292">Click **Deployment** tab in the Project Designer.</span></span>  
  
8.  <span data-ttu-id="3675e-293">設定**應用程式名稱**至`PS_Test`。</span><span class="sxs-lookup"><span data-stu-id="3675e-293">Set the **Application Name** to `PS_Test`.</span></span>  
  
9. <span data-ttu-id="3675e-294">在方案總管中，以滑鼠右鍵按一下 []  專案，然後按一下 [建置] </span><span class="sxs-lookup"><span data-stu-id="3675e-294">In Solution Explorer, right-click the **PS_Test** project, and then click **Build.**</span></span>  
  
10. <span data-ttu-id="3675e-295">順利完成建置後，以滑鼠右鍵按一下 [PS_Test]  專案，然後按一下 [部署] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-295">After the build completes successfully, right-click the **PS_Test** project, and then click **Deploy**.</span></span>  
  
## <a name="step-5-test-the-application-and-viewing-the-xml-output"></a><span data-ttu-id="3675e-296">步驟 5： 測試應用程式，並檢視 XML 輸出</span><span class="sxs-lookup"><span data-stu-id="3675e-296">Step 5: Test the Application and Viewing the XML Output</span></span>  
 <span data-ttu-id="3675e-297">現在您將測試所建立和部署的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3675e-297">Now you will test the application that you have created and deployed.</span></span> <span data-ttu-id="3675e-298">您會建立啟動協調流程處理序的 XML 檔案，然後設定在應用程式內接收和傳送 XML 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="3675e-298">You will create the XML file that starts the orchestration process, and then you will configure folders to receive and send XML files within the application.</span></span> <span data-ttu-id="3675e-299">設定應用程式之後，您將會執行它並檢視協調流程所傳回的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="3675e-299">After you have configured the application, you will run it and view the XML files that the orchestration returns.</span></span>  
  
#### <a name="generate-the-xml-file-for-the-query"></a><span data-ttu-id="3675e-300">產生查詢的 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="3675e-300">Generate the XML file for the query</span></span>  
  
1.  <span data-ttu-id="3675e-301">在方案總管中，按兩下 [LOCATIONService_LOCATION_x5d.xsd]  開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="3675e-301">In Solution Explorer, double-click **LOCATIONService_LOCATION_x5d.xsd** to open the file.</span></span>  
  
2.  <span data-ttu-id="3675e-302">以滑鼠右鍵按一下 [LOCATIONService_LOCATION_x5d.xsd]  ，再按一下 [屬性] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-302">Right-click **LOCATIONService_LOCATION_x5d.xsd** and then click **Properties**.</span></span> <span data-ttu-id="3675e-303">針對 **輸出執行個體檔案名稱** 輸入範例 XML 的下列路徑和檔案名稱：</span><span class="sxs-lookup"><span data-stu-id="3675e-303">For the **Output Instance Filename** enter the following path and file name for the sample XML:</span></span>  
  
     `C:\LABS\PS_TEST\SAMPLEQUERY.XML`  
  
3.  <span data-ttu-id="3675e-304">按一下 **[確定].**</span><span class="sxs-lookup"><span data-stu-id="3675e-304">Click **OK.**</span></span> <span data-ttu-id="3675e-305">在 [屬性] 視窗中，選取 **\<結構描述\>** 並設定 **根參考： 取得** 。</span><span class="sxs-lookup"><span data-stu-id="3675e-305">In the Properties window, select **\<Schema\>** and set **Root Reference: Get**.</span></span>  
  
4.  <span data-ttu-id="3675e-306">以滑鼠右鍵按一下 [LOCATIONService_LOCATION_x5d.xsd]  ，再按一下 [產生執行個體] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-306">Right-click **LOCATIONService_LOCATION_x5d.xsd** and then click **Generate Instance**.</span></span> <span data-ttu-id="3675e-307">這會產生 **SampleQuery.xml** 檔案。</span><span class="sxs-lookup"><span data-stu-id="3675e-307">This generates the **SampleQuery.xml** file.</span></span> <span data-ttu-id="3675e-308">這個檔案將做為配接器的輸入，放置在接收位置以啟動協調流程處理序。</span><span class="sxs-lookup"><span data-stu-id="3675e-308">This file will be dropped in the receive location as input to the adapter to start the orchestration process.</span></span>  
  
     <span data-ttu-id="3675e-309">![](../core/media/ef65a96c-2daa-44db-ab95-d18b1fda934e.gif "ef65a96c-2daa-44db-ab95-d18b1fda934e")</span><span class="sxs-lookup"><span data-stu-id="3675e-309">![](../core/media/ef65a96c-2daa-44db-ab95-d18b1fda934e.gif "ef65a96c-2daa-44db-ab95-d18b1fda934e")</span></span>  
  
#### <a name="configure-and-start-the-biztalk-application"></a><span data-ttu-id="3675e-310">設定並啟動 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="3675e-310">Configure and start the BizTalk application</span></span>  
  
1. <span data-ttu-id="3675e-311">設定用於接收內送檔案及傳送外寄檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="3675e-311">Configure folders for receiving the incoming files and sending the outgoing files.</span></span> <span data-ttu-id="3675e-312">移至**C:\LABS\PS_TEST**並建立兩個新的子資料夾，名為`FileIn`和`FileOut`。</span><span class="sxs-lookup"><span data-stu-id="3675e-312">Go to **C:\LABS\PS_TEST** and create two new subfolders named `FileIn` and `FileOut`.</span></span>  
  
2. <span data-ttu-id="3675e-313">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**主控台根目錄**，展開**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理**，展開 **BizTalk 群組** ，展開 **應用程式** ，以滑鼠右鍵按一下**PS_Test** ，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="3675e-313">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **Console Root**, expand **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**, expand **BizTalk Group**, expand **Applications**, right-click **PS_Test** and then click **Configure**.</span></span>  
  
    <span data-ttu-id="3675e-314">![](../core/media/e45f4c8b-fc8a-492a-9824-5232eb728d95.gif "e45f4c8b-fc8a-492a-9824-5232eb728d95")</span><span class="sxs-lookup"><span data-stu-id="3675e-314">![](../core/media/e45f4c8b-fc8a-492a-9824-5232eb728d95.gif "e45f4c8b-fc8a-492a-9824-5232eb728d95")</span></span>  
  
3. <span data-ttu-id="3675e-315">選取 [Orchestration_1]  ，並按一下 [主機]  下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="3675e-315">Select **Orchestration_1** and click the **Host** drop-down box.</span></span> <span data-ttu-id="3675e-316">選取 **[BizTalkServerApplication]**。</span><span class="sxs-lookup"><span data-stu-id="3675e-316">Select **BizTalkServerApplication**.</span></span>  
  
4. <span data-ttu-id="3675e-317">底下**接收連接埠**，按一下 **\<None\>**。</span><span class="sxs-lookup"><span data-stu-id="3675e-317">Under **Receive Ports**, click **\<None\>**.</span></span> <span data-ttu-id="3675e-318">在下拉式清單中選取 [新增接收埠] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-318">In the drop-down list, select **New Receive Port**.</span></span>  
  
5. <span data-ttu-id="3675e-319">針對**名稱**，型別`FileInPort`，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3675e-319">For **Name**, type `FileInPort`, and then click **OK**.</span></span> <span data-ttu-id="3675e-320">訊息方塊會出現，指出您需要指定接收位置。</span><span class="sxs-lookup"><span data-stu-id="3675e-320">A message box appears stating that you need to designate a receive location.</span></span> <span data-ttu-id="3675e-321">按一下 [確定] 及 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="3675e-321">Click **OK**, and then click **New**.</span></span>  
  
    <span data-ttu-id="3675e-322">![](../core/media/298638b6-0eb8-49c4-8a2e-485571d070cf.gif "298638b6-0eb8-49c4-8a2e-485571d070cf")</span><span class="sxs-lookup"><span data-stu-id="3675e-322">![](../core/media/298638b6-0eb8-49c4-8a2e-485571d070cf.gif "298638b6-0eb8-49c4-8a2e-485571d070cf")</span></span>  
  
6. <span data-ttu-id="3675e-323">輸入或選取屬性的下列值：</span><span class="sxs-lookup"><span data-stu-id="3675e-323">Type or select the following values for the properties:</span></span>  
  
    <span data-ttu-id="3675e-324">**名稱**：`FileInLoc`</span><span class="sxs-lookup"><span data-stu-id="3675e-324">**Name**: `FileInLoc`</span></span>  
  
    <span data-ttu-id="3675e-325">**類型**： **檔案**</span><span class="sxs-lookup"><span data-stu-id="3675e-325">**Type**: **File**</span></span>  
  
    <span data-ttu-id="3675e-326">**接收處理常式**： **BizTalkServerApplication**</span><span class="sxs-lookup"><span data-stu-id="3675e-326">**Receive Handler**: **BizTalkServerApplication**</span></span>  
  
    <span data-ttu-id="3675e-327">**接收管線**： **XMLReceive**</span><span class="sxs-lookup"><span data-stu-id="3675e-327">**Receive Pipeline**: **XMLReceive**</span></span>  
  
    <span data-ttu-id="3675e-328">![](../core/media/613a5dbc-effe-4827-a72b-d16eef8d0e8a.gif "613a5dbc-effe-4827-a72b-d16eef8d0e8a")</span><span class="sxs-lookup"><span data-stu-id="3675e-328">![](../core/media/613a5dbc-effe-4827-a72b-d16eef8d0e8a.gif "613a5dbc-effe-4827-a72b-d16eef8d0e8a")</span></span>  
  
7. <span data-ttu-id="3675e-329">按一下 [開始]  ，針對 [接收資料夾] `C:\LABS\PS_TEST\FILEIN` 中輸入 **C:\LABS\PS_TEST\FILEIN**，然後按一下 [BizTalk Server 管理]  。</span><span class="sxs-lookup"><span data-stu-id="3675e-329">Click **Configure** and type `C:\LABS\PS_TEST\FILEIN` for **Receive Folder**, and then click **OK** three times.</span></span>  
  
    <span data-ttu-id="3675e-330">![](../core/media/513eebb0-58ca-4aaa-a33b-31700f9cf7a8.gif "513eebb0-58ca-4aaa-a33b-31700f9cf7a8")</span><span class="sxs-lookup"><span data-stu-id="3675e-330">![](../core/media/513eebb0-58ca-4aaa-a33b-31700f9cf7a8.gif "513eebb0-58ca-4aaa-a33b-31700f9cf7a8")</span></span>  
  
8. <span data-ttu-id="3675e-331">按一下  **\<無\>** for **PeopleSoft_Port**下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="3675e-331">Click **\<None\>** for **PeopleSoft_Port** in the drop-down list.</span></span>  
  
9. <span data-ttu-id="3675e-332">選取 [新增傳送埠]  ，然後選取或輸入下列屬性值。</span><span class="sxs-lookup"><span data-stu-id="3675e-332">Select **New Send Port** and then select or type the following values for the properties.</span></span>  
  
     <span data-ttu-id="3675e-333">**名稱**：`PS_Test_Port`</span><span class="sxs-lookup"><span data-stu-id="3675e-333">**Name**: `PS_Test_Port`</span></span>  
  
     <span data-ttu-id="3675e-334">**類型**： **PeopleSoft**</span><span class="sxs-lookup"><span data-stu-id="3675e-334">**Type**: **PeopleSoft**</span></span>  
  
     <span data-ttu-id="3675e-335">**傳送處理常式**： **BizTalkServerApplication**</span><span class="sxs-lookup"><span data-stu-id="3675e-335">**Send Handler**: **BizTalkServerApplication**</span></span>  
  
     <span data-ttu-id="3675e-336">**管線**： **XMLTransmit** 和 **XMLReceive**</span><span class="sxs-lookup"><span data-stu-id="3675e-336">**Pipelines**: **XMLTransmit** and **XMLReceive**</span></span>  
  
10. <span data-ttu-id="3675e-337">按一下 [設定] ，然後輸入下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="3675e-337">Click **Configure**, and then enter the following property values:</span></span>  
  
    1. <span data-ttu-id="3675e-338">**應用程式伺服器路徑**： **//Servername:9000**</span><span class="sxs-lookup"><span data-stu-id="3675e-338">**Application server path**: **//Servername:9000**</span></span>  
  
        <span data-ttu-id="3675e-339">Servername 是您的應用程式伺服器。</span><span class="sxs-lookup"><span data-stu-id="3675e-339">Servername is your application server.</span></span> <span data-ttu-id="3675e-340">這是此 PeopleSoft 系統的特定伺服器名稱或 IP 位址以及連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="3675e-340">This is the specific server name or IP address and port number for this PeopleSoft system.</span></span>  
  
    2. <span data-ttu-id="3675e-341">**JAVA_HOME**： **C:\J2SDK1.4.2_08**</span><span class="sxs-lookup"><span data-stu-id="3675e-341">**JAVA_HOME**: **C:\J2SDK1.4.2_08**</span></span>  
  
        <span data-ttu-id="3675e-342">這個路徑在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上是 Java SDK 安裝專用。</span><span class="sxs-lookup"><span data-stu-id="3675e-342">This path is specific to the Java SDK installation on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
    3. <span data-ttu-id="3675e-343">**密碼**:\<輸入您的 PeopleSoft 密碼\></span><span class="sxs-lookup"><span data-stu-id="3675e-343">**Password**: \<enter your PeopleSoft password\></span></span>  
  
    4. <span data-ttu-id="3675e-344">**PeopleSoft 8.x JAR 檔案**： **C:\PSJARS\VER841\PSJOA.JAR**</span><span class="sxs-lookup"><span data-stu-id="3675e-344">**PeopleSoft 8.x JAR files**: **C:\PSJARS\VER841\PSJOA.JAR**</span></span>  
  
       <span data-ttu-id="3675e-345">**使用者名稱：** \<輸入您的 PeopleSoft Userid>\></span><span class="sxs-lookup"><span data-stu-id="3675e-345">**User name:** \<enter your PeopleSoft UserID\></span></span>  
  
11. <span data-ttu-id="3675e-346">按兩下 [確定]  關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3675e-346">Click **OK** twice to close the dialog boxes.</span></span>  
  
12. <span data-ttu-id="3675e-347">在 設定 Applicationwindow 中，按一下 **\<無\>** for **FileOut** 下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="3675e-347">In the Configure Applicationwindow, click **\<None\>** for **FileOut** in the drop-down list.</span></span>  
  
13. <span data-ttu-id="3675e-348">選取 [新增傳送埠]  ，然後選取或輸入下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="3675e-348">Select **New Send Port** and type or select the following values for the properties:</span></span>  
  
     <span data-ttu-id="3675e-349">**名稱**：`FileOutPort`</span><span class="sxs-lookup"><span data-stu-id="3675e-349">**Name**: `FileOutPort`</span></span>  
  
     <span data-ttu-id="3675e-350">**類型**： **檔案**</span><span class="sxs-lookup"><span data-stu-id="3675e-350">**Type**: **File**</span></span>  
  
     <span data-ttu-id="3675e-351">**傳送處理常式**： **BizTalkServerApplication**</span><span class="sxs-lookup"><span data-stu-id="3675e-351">**Send Handler**: **BizTalkServerApplication**</span></span>  
  
     <span data-ttu-id="3675e-352">**傳送管線**： **XMLTransmit**</span><span class="sxs-lookup"><span data-stu-id="3675e-352">**Send Pipeline**: **XMLTransmit**</span></span>  
  
14. <span data-ttu-id="3675e-353">按一下 **設定**並輸入`C:\Labs\PS_Test\FileOut`如**目的地資料夾。**</span><span class="sxs-lookup"><span data-stu-id="3675e-353">Click **Configure** and type`C:\Labs\PS_Test\FileOut` for **Destination Folder.**</span></span> <span data-ttu-id="3675e-354">保持 **%MessageID%.xml** for**檔案名稱**因為這會導致每個訊息的唯一檔案。</span><span class="sxs-lookup"><span data-stu-id="3675e-354">Keep **%MessageID%.xml** for **File Name** because this results in a unique file for each message.</span></span>  
  
15. <span data-ttu-id="3675e-355">按三下 [確定]  關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3675e-355">Click **OK** three times to close the dialog boxes.</span></span>  
  
16. <span data-ttu-id="3675e-356">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下滑鼠右鍵**PS_Test**應用程式，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="3675e-356">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console,right-click the **PS_Test** application and then click **Start**.</span></span>  
  
     <span data-ttu-id="3675e-357">![](../core/media/7bf30707-c7c6-409f-af18-9c9dfeb0de58.gif "7bf30707-c7c6-409f-af18-9c9dfeb0de58")</span><span class="sxs-lookup"><span data-stu-id="3675e-357">![](../core/media/7bf30707-c7c6-409f-af18-9c9dfeb0de58.gif "7bf30707-c7c6-409f-af18-9c9dfeb0de58")</span></span>  
  
#### <a name="test-the-orchestration"></a><span data-ttu-id="3675e-358">測試協調流程</span><span class="sxs-lookup"><span data-stu-id="3675e-358">Test the orchestration</span></span>  
  
1.  <span data-ttu-id="3675e-359">在 **C:\Labs\PS_Test** 目錄中，將 **Samplequery.xml** 檔案變更為下列所示：</span><span class="sxs-lookup"><span data-stu-id="3675e-359">In the **C:\Labs\PS_Test** directory, change the **Samplequery.xml** file to the following:</span></span>  
  
    ```  
    <ns0:Get xmlns:ns0="http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]">  
      <ns0:SETID>SHARE</ns0:SETID>  
      <ns0:LOCATION>AUS01</ns0:LOCATION>  
      <ns0:getHistory>true</ns0:getHistory>  
    </ns0:Get>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="3675e-360">**SHARE** 資料值將用在所有系統上。</span><span class="sxs-lookup"><span data-stu-id="3675e-360">The **SHARE** data value will be used on all systems.</span></span> <span data-ttu-id="3675e-361">不過，您將在使用在此 XML 檔案中的 **位置** 值必須存在您的系統上。</span><span class="sxs-lookup"><span data-stu-id="3675e-361">However the value you will use for **Location** in this XML file must exist on your system.</span></span> <span data-ttu-id="3675e-362">您已在實驗室 1 中發現這個原則。</span><span class="sxs-lookup"><span data-stu-id="3675e-362">You found this out in Lab 1.</span></span>  
  
2.  <span data-ttu-id="3675e-363">儲存變更，並將檔案複製到 **C:\Labs\PS_Test\FileIn** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3675e-363">Save the changes and copy the file to the **C:\Labs\PS_Test\FileIn** folder.</span></span> <span data-ttu-id="3675e-364">這是啟動協調流程處理序的 FileIn 接收位置。</span><span class="sxs-lookup"><span data-stu-id="3675e-364">This is the receive location for FileIn that starts the orchestration process.</span></span>  
  
3.  <span data-ttu-id="3675e-365">XML 檔案很快就會出現在 **C:\Labs\PS_Test\FileOut** 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3675e-365">In a few seconds, an XML file should appear in the **C:\Labs\PS_Test\FileOut** folder.</span></span> <span data-ttu-id="3675e-366">其中應包含來自位置為 AUS01 之記錄的資料。</span><span class="sxs-lookup"><span data-stu-id="3675e-366">This should contain the data from the record where the location is AUS01.</span></span>  
  
     <span data-ttu-id="3675e-367">![](../core/media/1320ea3c-b2bc-4717-b200-c3c550079ccb.gif "1320ea3c-b2bc-4717-b200-c3c550079ccb")</span><span class="sxs-lookup"><span data-stu-id="3675e-367">![](../core/media/1320ea3c-b2bc-4717-b200-c3c550079ccb.gif "1320ea3c-b2bc-4717-b200-c3c550079ccb")</span></span>  
  
     <span data-ttu-id="3675e-368">這份傳回的記錄資料應符合針對 PeopleSoft 實驗室 1 中 PeopleSoft 系統的查詢所傳回的內容。</span><span class="sxs-lookup"><span data-stu-id="3675e-368">This returned record data should match what was returned by the query against the PeopleSoft system in PeopleSoft Lab 1.</span></span> <span data-ttu-id="3675e-369">比較您在實驗室 1 取得，特別 **Address1**並 **address2 一起顯示** 行，以在這裡顯示 **\<位置： ADDRESS1\>** 並 **\<位置： address2 一起顯示\>** 欄位中，您可以確認 **取得** 方法運作正常。</span><span class="sxs-lookup"><span data-stu-id="3675e-369">By comparing the values you obtained in Lab 1, specifically the **Address1** and **Address2** lines, to what is shown here in the **\<LOCATION:ADDRESS1\>** and **\<LOCATION:ADDRESS2\>** fields, you can verify that the **Get** method worked properly.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="3675e-370">總結</span><span class="sxs-lookup"><span data-stu-id="3675e-370">Summary</span></span>  
 <span data-ttu-id="3675e-371">在此實驗室中，您先確認了已正確設定必要條件，以便存取 PeopleSoft 系統。</span><span class="sxs-lookup"><span data-stu-id="3675e-371">In this lab, you first verified that the prerequisites were set up correctly to access the PeopleSoft system.</span></span> <span data-ttu-id="3675e-372">之後，使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 建立包含協調流程的新 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="3675e-372">Then you used [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to create a new BizTalk project containing an orchestration.</span></span> <span data-ttu-id="3675e-373">您設定了此協調流程，以使用 PeopleSoft 配接器自 PeopleSoft 系統取得資料。</span><span class="sxs-lookup"><span data-stu-id="3675e-373">You configured the BizTalk orchestration to use the PeopleSoft adapter to get data from the PeopleSoft system.</span></span> <span data-ttu-id="3675e-374">為了設定協調流程，您建立了傳送、接收與傳送/接收埠。</span><span class="sxs-lookup"><span data-stu-id="3675e-374">To configure the orchestration, you created send, receive, and send/receive ports.</span></span> <span data-ttu-id="3675e-375">您將這些連接埠繫結至 PeopleSoft 配接器，並指派訊息到適當的連接埠。</span><span class="sxs-lookup"><span data-stu-id="3675e-375">You bound these ports to the PeopleSoft adapter, and assigned messages to the appropriate ports.</span></span>  
  
 <span data-ttu-id="3675e-376">完成 BizTalk 專案之後，您使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 予以建置及部署。</span><span class="sxs-lookup"><span data-stu-id="3675e-376">After you completed the BizTalk project, you used [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to build and deploy it.</span></span> <span data-ttu-id="3675e-377">然後設定了新的應用程式並加以執行，以從 PeopleSoft 系統取得資料。</span><span class="sxs-lookup"><span data-stu-id="3675e-377">You then configured your new application and ran it to get data from the PeopleSoft system.</span></span> <span data-ttu-id="3675e-378">為了確定應用程式正確運作，您將其輸出 XML 檔與在實驗室 1 中接收自 PeopleSoft 系統的檔案做比較。</span><span class="sxs-lookup"><span data-stu-id="3675e-378">To verify that the application worked correctly, you compared its output XML file to the file that you received from the PeopleSoft system in Lab 1.</span></span>