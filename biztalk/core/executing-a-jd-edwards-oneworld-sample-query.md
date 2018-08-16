---
title: 執行 JD Edwards OneWorld 範例查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b060d383-a2df-472f-90cc-e79078b0bcfd
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4183124a5306b42fa4ef66eec7b0fe0a0390c0c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001831"
---
# <a name="execute-a-jd-edwards-oneworld-sample-query"></a><span data-ttu-id="1e196-102">執行 JD Edwards OneWorld 範例查詢</span><span class="sxs-lookup"><span data-stu-id="1e196-102">Execute a JD Edwards OneWorld Sample Query</span></span>
<span data-ttu-id="1e196-103">JD Edwards OneWorld (JDEOW) 系統是從存取[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用 JD Edwards OneWorld 配接器的系統。</span><span class="sxs-lookup"><span data-stu-id="1e196-103">The JD Edwards OneWorld (JDEOW) system is accessible from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system by using the JD Edwards OneWorld adapter.</span></span> <span data-ttu-id="1e196-104">此配接器隨附[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1e196-104">This adapter is included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>
  
 <span data-ttu-id="1e196-105">這是 JD Edwards OneWorld 實驗室工作的第二個部分。</span><span class="sxs-lookup"><span data-stu-id="1e196-105">This is the second part of the JD Edwards OneWorld lab work.</span></span> <span data-ttu-id="1e196-106">在第一個部分 (實驗室 1) 中，您以手動方式存取資料，而不需要的協助在 JD Edwards OneWorld 系統上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或其他 Microsoft 技術。</span><span class="sxs-lookup"><span data-stu-id="1e196-106">In the first part (Lab 1), you manually accessed data on the JD Edwards OneWorld system without the assistance of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or other Microsoft technologies.</span></span> <span data-ttu-id="1e196-107">在這個部分 (實驗室 2) 中，您將建立 BizTalk 協調流程的一部分[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="1e196-107">In this part (Lab 2), you will create a BizTalk orchestration as part of a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project.</span></span> <span data-ttu-id="1e196-108">在此協調流程，以使用 JD Edwards OneWorld 配接器自 JD Edwards OneWorld 系統取得資料，您將設定連接埠。</span><span class="sxs-lookup"><span data-stu-id="1e196-108">You will configure ports on this orchestration to use the JD Edwards OneWorld adapter to get data from a JD Edwards OneWorld system.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1e196-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="1e196-109">Prerequisites</span></span>  
  
- <span data-ttu-id="1e196-110">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e196-110">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>
  
- <span data-ttu-id="1e196-111">Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e196-111">Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]</span></span> 
  
- <span data-ttu-id="1e196-112">JD Edwards OneWorld Client 軟體</span><span class="sxs-lookup"><span data-stu-id="1e196-112">JD Edwards OneWorld Client software</span></span>  
  
- <span data-ttu-id="1e196-113">JD Edwards OneWorld 系統在另一部伺服器上的網路連線</span><span class="sxs-lookup"><span data-stu-id="1e196-113">Network connectivity to a JD Edwards OneWorld system on another server</span></span>  
  
- <span data-ttu-id="1e196-114">Microsoft BizTalk Adapters for Enterprise Applications</span><span class="sxs-lookup"><span data-stu-id="1e196-114">Microsoft BizTalk Adapters for Enterprise Applications</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e196-115">請參閱[安裝及設定企業應用程式的介面卡](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md)的 JD Edwards、 PeopleSoft 和 TIBCO 配接器的重要組態資訊。</span><span class="sxs-lookup"><span data-stu-id="1e196-115">See [Install and configure the adapters for enterprise applications](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md) for key configuration information for the JD Edwards, PeopleSoft, and TIBCO adapters.</span></span>  
  
## <a name="lab-2---executing-a-jd-edwards-oneworld-sample-query"></a><span data-ttu-id="1e196-116">實驗室 2 - 執行 JD Edwards OneWorld 範例查詢</span><span class="sxs-lookup"><span data-stu-id="1e196-116">Lab 2 - Executing a JD Edwards OneWorld Sample Query</span></span>  
 <span data-ttu-id="1e196-117">在此實驗室中，您將執行**取得**對 JD Edwards OneWorld 系統的作業。</span><span class="sxs-lookup"><span data-stu-id="1e196-117">In this lab, you will execute a **Get** operation against the JD Edwards OneWorld system.</span></span> <span data-ttu-id="1e196-118">也就是說，您將執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="1e196-118">Specifically you will perform the following tasks:</span></span>  
  
- <span data-ttu-id="1e196-119">確認 JD Edwards OneWorld 必要條件</span><span class="sxs-lookup"><span data-stu-id="1e196-119">Verify the JD Edwards OneWorld prerequisites</span></span>  
  
- <span data-ttu-id="1e196-120">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中設定 JD Edwards OneWorld 傳送埠</span><span class="sxs-lookup"><span data-stu-id="1e196-120">Set up a JD Edwards OneWorld send port in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>  
  
- <span data-ttu-id="1e196-121">建立 BizTalk 協調流程專案</span><span class="sxs-lookup"><span data-stu-id="1e196-121">Create a BizTalk orchestration project</span></span>  
  
- <span data-ttu-id="1e196-122">建置和部署專案</span><span class="sxs-lookup"><span data-stu-id="1e196-122">Build and deploy the project</span></span>  
  
- <span data-ttu-id="1e196-123">測試應用程式並檢視 XML 輸出</span><span class="sxs-lookup"><span data-stu-id="1e196-123">Test the application and view the XML output</span></span>  
  
  <span data-ttu-id="1e196-124">您將會使用 JD Edwards OneWorld 配接器從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 存取 JD Edwards OneWorld 系統上的資料。</span><span class="sxs-lookup"><span data-stu-id="1e196-124">You will use the JD Edwards OneWorld adapter to access data on the JD Edwards OneWorld system from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
  <span data-ttu-id="1e196-125">此配接器可用以使用協調流程執行的要求和回應，處理 JD Edwards OneWorld 物件。</span><span class="sxs-lookup"><span data-stu-id="1e196-125">This adapter enables the processing of JD Edwards OneWorld objects by using requests and responses executed by an orchestration.</span></span> <span data-ttu-id="1e196-126">對於結構描述物件，有許多方法可用。</span><span class="sxs-lookup"><span data-stu-id="1e196-126">Many methods are available for a schema object.</span></span> <span data-ttu-id="1e196-127">這個實驗室會示範如何使用**Address Book MBF**方法。</span><span class="sxs-lookup"><span data-stu-id="1e196-127">This lab demonstrates how to use the **Address Book MBF** method.</span></span>  
  
  <span data-ttu-id="1e196-128">執行服務要求之前，您必須針對特定 JD Edwards OneWorld 物件建立服務要求和回應結構描述。</span><span class="sxs-lookup"><span data-stu-id="1e196-128">Before running a service request, you must create service request and response schemas for the specific JD Edwards OneWorld object.</span></span> <span data-ttu-id="1e196-129">新增產生的項目/新增配接器精靈會透過直接詢問 JD Edwards OneWorld 中的支援中繼資料物件，來建立這些結構描述。</span><span class="sxs-lookup"><span data-stu-id="1e196-129">The Add Generated Items/Add Adapter Wizard creates these schemas by directly interrogating the supporting metadata object in JD Edwards OneWorld.</span></span> <span data-ttu-id="1e196-130">此實驗室示範建立結構描述所需的步驟**Address Book MBF**方法，並處理查詢。</span><span class="sxs-lookup"><span data-stu-id="1e196-130">This lab illustrates the steps required to create schemas for the **Address Book MBF** method and to process a query.</span></span>  
  
## <a name="step-1-verify-the-jd-edwards-oneworld-prerequisites"></a><span data-ttu-id="1e196-131">步驟 1： 確認 JD Edwards OneWorld 必要條件</span><span class="sxs-lookup"><span data-stu-id="1e196-131">Step 1: Verify the JD Edwards OneWorld prerequisites</span></span>  
 <span data-ttu-id="1e196-132">在您開始建立要與 JD Edwards OneWorld 配接器搭配使用的 BizTalk 專案之前，您必須確定已正確設定檔案和配接器，以便存取 JD Edwards OneWorld 系統。</span><span class="sxs-lookup"><span data-stu-id="1e196-132">Before you start creating a BizTalk project for use with the JD Edwards OneWorld adapter, you need to be sure the files and the adapter are set up correctly to access the JD Edwards OneWorld system.</span></span> <span data-ttu-id="1e196-133">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上，JD Edwards OneWorld 配接器會利用 Java 介面與 JD Edwards OneWorld 系統通訊。</span><span class="sxs-lookup"><span data-stu-id="1e196-133">On the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer, the JD Edwards OneWorld adapter communicates with the JD Edwards OneWorld system by using the Java interface.</span></span>    

1. <span data-ttu-id="1e196-134">四個檔案所需的適當介面存取 JD Edwards OneWorld 系統，請使用 JD Edwards OneWorld 配接器： Connector.jar、 Kernel.jar、 BTSLIBinterop.jar 及 JDEJAccess.jar。</span><span class="sxs-lookup"><span data-stu-id="1e196-134">Four files are necessary for proper interface access to a JD Edwards OneWorld system using the JD Edwards OneWorld adapter: Connector.jar, Kernel.jar, BTSLIBinterop.jar, and JDEJAccess.jar.</span></span>  
  
    -   <span data-ttu-id="1e196-135">Connector.jar 和 Kernel.jar 檔案來自 JD Edwards OneWorld 系統，可以向 JD Edwards OneWorld 系統管理員取得。</span><span class="sxs-lookup"><span data-stu-id="1e196-135">The Connector.jar and Kernel.jar files come with the JD Edwards OneWorld system and are obtained from a JD Edwards OneWorld administrator.</span></span> <span data-ttu-id="1e196-136">這些檔案都位於 C:\JDEOWJars 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="1e196-136">These files are located in the C:\JDEOWJars folder.</span></span>  
  
    -   <span data-ttu-id="1e196-137">BTSLIBinterop.jar 檔案是遵循配接器的《安裝指南》包含的指示後，由 JD Edwards OneWorld 系統所產生。</span><span class="sxs-lookup"><span data-stu-id="1e196-137">The BTSLIBinterop.jar file is generated by the JD Edwards OneWorld system by following the instructions included in the Installation Guide for the adapters.</span></span> <span data-ttu-id="1e196-138">此檔案位於 C:\JDEOWJars 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="1e196-138">This file is located in the C:\JDEOWJars folder.</span></span>  
  
    -   <span data-ttu-id="1e196-139">JDEJAccess.jar 檔案是 JDEOW 配接器的一部分，因此會隨配接器的安裝而存在。</span><span class="sxs-lookup"><span data-stu-id="1e196-139">The JDEJAccess.jar file is a part of the JDEOW adapter and is included with the installation of the adapter.</span></span> <span data-ttu-id="1e196-140">根據預設，它位於 C:\Program Files\Microsoft BizTalk Adapters for Enterprise applications\j.d.edwards。</span><span class="sxs-lookup"><span data-stu-id="1e196-140">By default, it is located in the C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\J.D.</span></span> <span data-ttu-id="1e196-141">Edwards OneWorld® \Classes 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="1e196-141">Edwards OneWorld®\Classes folder.</span></span>  
  
2. <span data-ttu-id="1e196-142">確認 Connector.jar、 Kernel.jar，和 BTSLIBinterop.jar 檔案存在於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]C:\JDEOWJars 資料夾中的電腦。</span><span class="sxs-lookup"><span data-stu-id="1e196-142">Confirm the Connector.jar, Kernel.jar, and BTSLIBinterop.jar files exist on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer in the C:\JDEOWJars folder.</span></span>  
  
3. <span data-ttu-id="1e196-143">確認 JDEJAccess.jar 檔案存在於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在 C:\Program Files\Microsoft BizTalk Adapters for Enterprise applications\j.d.edwards 的電腦。</span><span class="sxs-lookup"><span data-stu-id="1e196-143">Confirm the JDEJAccess.jar file exists on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer in the C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\J.D.</span></span> <span data-ttu-id="1e196-144">Edwards OneWorld\Classes 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="1e196-144">Edwards OneWorld\Classes folder.</span></span>  
  
## <a name="step-2-configure-biztalk-send-ports"></a><span data-ttu-id="1e196-145">步驟 2： 設定 BizTalk 傳送埠</span><span class="sxs-lookup"><span data-stu-id="1e196-145">Step 2: Configure BizTalk send ports</span></span>  
<span data-ttu-id="1e196-146">接下來，確認 JD Edwards OneWorld 配接器已安裝，並且建立傳送埠。</span><span class="sxs-lookup"><span data-stu-id="1e196-146">Next, verify that the JD Edwards OneWorld adapter is installed, and create the send port.</span></span>  

1. <span data-ttu-id="1e196-147">開啟**BizTalk Server 管理**，展開**主控台根目錄**，展開**BizTalk Server 管理**，展開**BizTalk 群組**，依序展開**平台設定**，然後展開**配接器**。</span><span class="sxs-lookup"><span data-stu-id="1e196-147">Open **BizTalk Server Administration**, expand **Console Root**, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
   <span data-ttu-id="1e196-148">確認**JDE_OneWorld**配接器會列出。</span><span class="sxs-lookup"><span data-stu-id="1e196-148">Confirm the **JDE_OneWorld** adapter is listed.</span></span> <span data-ttu-id="1e196-149">如果未安裝 JD Edwards OneWorld 配接器，請安裝 BizTalk Adapters for Enterprise Applications (請參閱稍早的「必要條件」一節)。</span><span class="sxs-lookup"><span data-stu-id="1e196-149">If the JD Edwards OneWorld adapter is not installed, install the BizTalk Adapters for Enterprise Applications (see the earlier "Prerequisites" section).</span></span> <span data-ttu-id="1e196-150">安裝配接器之後，請以滑鼠右鍵按一下**配接器**，然後按一下**新增-配接器**安裝 JD Edwards OneWorld 配接器。</span><span class="sxs-lookup"><span data-stu-id="1e196-150">After the adapters are installed, right-click **Adapters** and then click **New - Adapter** to install the JD Edwards OneWorld adapter.</span></span> <span data-ttu-id="1e196-151">重新啟動主控件執行個體，這個選項才會生效。</span><span class="sxs-lookup"><span data-stu-id="1e196-151">Restart the host instance for this to take effect.</span></span>  
  
2. <span data-ttu-id="1e196-152">依序展開**應用程式**，然後展開**BizTalk Application 1**。</span><span class="sxs-lookup"><span data-stu-id="1e196-152">Expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
3. <span data-ttu-id="1e196-153">以滑鼠右鍵按一下**傳送埠**，按一下**新增**，然後按一下**靜態請求-回應傳送埠**。這些欄位中輸入下列值：</span><span class="sxs-lookup"><span data-stu-id="1e196-153">Right-click **Send Ports**, click **New**, and then click **Static Solicit-Response Send Port**.Enter the following values for these fields:</span></span>  
  
   1.  <span data-ttu-id="1e196-154">**名稱：**  `JDE_OneWorldPort`</span><span class="sxs-lookup"><span data-stu-id="1e196-154">**Name:**  `JDE_OneWorldPort`</span></span>  
  
   2.  <span data-ttu-id="1e196-155">**類型：**  `JDE_OneWorld`</span><span class="sxs-lookup"><span data-stu-id="1e196-155">**Type:**  `JDE_OneWorld`</span></span>  
  
   3.  <span data-ttu-id="1e196-156">**傳送處理常式：**  `BizTalkServerApplication`</span><span class="sxs-lookup"><span data-stu-id="1e196-156">**Send handler:**  `BizTalkServerApplication`</span></span>  
  
   4.  <span data-ttu-id="1e196-157">**傳送管線︰**  `XMLTransmit`</span><span class="sxs-lookup"><span data-stu-id="1e196-157">**Send pipeline:**  `XMLTransmit`</span></span>  
  
   5.  <span data-ttu-id="1e196-158">**接收管線︰**  `XMLReceive`</span><span class="sxs-lookup"><span data-stu-id="1e196-158">**Receive pipeline:**  `XMLReceive`</span></span>  
  
4. <span data-ttu-id="1e196-159">按一下 [設定] ，然後輸入下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="1e196-159">Click **Configure**, and then enter the following property values:</span></span>  
  
   1. <span data-ttu-id="1e196-160">**主機：** \<輸入 JDEOW 主控件名稱\></span><span class="sxs-lookup"><span data-stu-id="1e196-160">**Host:** \<enter your JDEOW host name\></span></span>  
  
   2. <span data-ttu-id="1e196-161">**JAVA_HOME:** `C:\j2sdk1.4.2_08`</span><span class="sxs-lookup"><span data-stu-id="1e196-161">**JAVA_HOME:** `C:\j2sdk1.4.2_08`</span></span>  
  
   3. <span data-ttu-id="1e196-162">**JDEdwards 環境：** \<輸入 JDEOW 環境\></span><span class="sxs-lookup"><span data-stu-id="1e196-162">**JDEdwards Environment:** \<enter your JDEOW environment\></span></span>  
  
   4. <span data-ttu-id="1e196-163">**JDEdwards JAR 檔案：** \<輸入 JAR 檔案的完整路徑\></span><span class="sxs-lookup"><span data-stu-id="1e196-163">**JDEdwards JAR files:** \<enter full path of JAR files\></span></span>  
  
       `C:\JDEOWJars\BTSLIBInterop.jar; C:\JDEOWJars\Connector.jar; C:\JDEOWJars\Kernel.jar;C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\J.D. Edwards OneWorld®\Classes\JDEJAccess.jar`  
  
   5. <span data-ttu-id="1e196-164">**密碼：** 使用下拉式清單，然後輸入 JD Edwards OneWorld 密碼。</span><span class="sxs-lookup"><span data-stu-id="1e196-164">**Password:** Use the drop-down list and then enter your JD Edwards OneWorld password.</span></span>  
  
   6. <span data-ttu-id="1e196-165">**連接埠：**  `6009`</span><span class="sxs-lookup"><span data-stu-id="1e196-165">**Port:**  `6009`</span></span>  
  
   7. <span data-ttu-id="1e196-166">**使用者名稱：** \<輸入您的 JD Edwards 使用者名稱\></span><span class="sxs-lookup"><span data-stu-id="1e196-166">**User Name:** \<enter your JD Edwards User Name\></span></span>  
  
      <span data-ttu-id="1e196-167">![](../core/media/jdeow-transportproperties-configurebutton.gif "JDEOW_TransportProperties_ConfigureButton")</span><span class="sxs-lookup"><span data-stu-id="1e196-167">![](../core/media/jdeow-transportproperties-configurebutton.gif "JDEOW_TransportProperties_ConfigureButton")</span></span>  
  
5. <span data-ttu-id="1e196-168">選取  **確定**以關閉**傳送埠屬性**。</span><span class="sxs-lookup"><span data-stu-id="1e196-168">Select **OK** to close the **Send Port Properties**.</span></span>  
  
## <a name="step-3-create-a-biztalk-orchestration-project"></a><span data-ttu-id="1e196-169">步驟 3： 建立 BizTalk 協調流程專案</span><span class="sxs-lookup"><span data-stu-id="1e196-169">Step 3: Create a BizTalk Orchestration Project</span></span>  
<span data-ttu-id="1e196-170">接下來，建立 BizTalk 專案中的[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，並設定要處理之間的通訊之專案中的協調流程[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 JD Edwards OneWorld 系統。</span><span class="sxs-lookup"><span data-stu-id="1e196-170">Next, create a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], and configure an orchestration in the project to handle communication between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the JD Edwards OneWorld system.</span></span> <span data-ttu-id="1e196-171">您將新增傳送和接收埠、建置專案，然後部署專案。</span><span class="sxs-lookup"><span data-stu-id="1e196-171">You will add send and receive ports, build the project, and then deploy the project.</span></span>  

  
1. <span data-ttu-id="1e196-172">開啟[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，並在 C:\LABS 資料夾中建立新的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="1e196-172">Open [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], and create a new BizTalk project in the C:\LABS folder.</span></span> <span data-ttu-id="1e196-173">在 [檔案]  功能表上，按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="1e196-173">On the **File** menu, click **New**.</span></span> <span data-ttu-id="1e196-174">[新增專案]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="1e196-174">The **New Project** dialog box appears.</span></span> <span data-ttu-id="1e196-175">在 [傳送埠屬性]  區段下，選取 [空白 BizTalk Server 專案] </span><span class="sxs-lookup"><span data-stu-id="1e196-175">In the **Templates** section, select **Empty BizTalk Server project.**</span></span> <span data-ttu-id="1e196-176">請輸入`JDE_OW_Test`做為唯一的專案名稱，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="1e196-176">Enter `JDE_OW_Test` as the unique project name, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="1e196-177">在方案總管中，以滑鼠右鍵按一下專案，按一下 [新增] 及 [新增產生的項目] 。</span><span class="sxs-lookup"><span data-stu-id="1e196-177">In Solution Explorer, right-click the project, click **Add**, and then click **Add Generated Items**.</span></span> <span data-ttu-id="1e196-178">在 [分類] 窗格中，選取**新增的配接器中繼資料**，在 [範本] 窗格中，選取**新增配接器中繼資料**，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="1e196-178">In the Categories pane, select **Add Adapter Metadata**, in the Templates pane, select **Add Adapter Metadata**, and then click **Add**.</span></span>  
  
3. <span data-ttu-id="1e196-179">在 [新增配接器精靈] 中，選取**JD Edwards OneWorld**配接器，選取**JDE_OneWorldPort**傳送埠，您在之前程序中，建立及 [**下一步]**.</span><span class="sxs-lookup"><span data-stu-id="1e196-179">In the Add Adapter Wizard, select the **JD Edwards OneWorld** adapter, select the **JDE_OneWorldPort** send port that you created in the preceding procedure, and then click **Next**.</span></span>  
  
    <span data-ttu-id="1e196-180">![](../core/media/jdeow-addadapterwizardselectadapter.gif "JDEOW_AddAdapterWizardSelectAdapter")</span><span class="sxs-lookup"><span data-stu-id="1e196-180">![](../core/media/jdeow-addadapterwizardselectadapter.gif "JDEOW_AddAdapterWizardSelectAdapter")</span></span>  
  
4. <span data-ttu-id="1e196-181">在 **選取要匯入服務**頁面上，開啟**JD Edwards OneWorld**。</span><span class="sxs-lookup"><span data-stu-id="1e196-181">On the **Select Services to Import** page, open **JD Edwards OneWorld**.</span></span> <span data-ttu-id="1e196-182">系統隨即使用 BrowsingAgent 程式透過配接器聯繫 JDEOW 系統。</span><span class="sxs-lookup"><span data-stu-id="1e196-182">The JDEOW system is contacted through the adapter by using the BrowsingAgent program.</span></span> <span data-ttu-id="1e196-183">BrowsingAgent 會傳回下列服務。</span><span class="sxs-lookup"><span data-stu-id="1e196-183">The BrowsingAgent returns the following services.</span></span>  
  
    <span data-ttu-id="1e196-184">![](../core/media/jdeow-callbsfn.gif "JDEOW_CALLBSFN")</span><span class="sxs-lookup"><span data-stu-id="1e196-184">![](../core/media/jdeow-callbsfn.gif "JDEOW_CALLBSFN")</span></span>  
  
5. <span data-ttu-id="1e196-185">依序展開 **[callbsfn]** 向下捲動至**N0100041-Address Book MBF**。</span><span class="sxs-lookup"><span data-stu-id="1e196-185">Expand **CALLBSFN** and scroll down to **N0100041 - Address Book MBF**.</span></span> <span data-ttu-id="1e196-186">選取 N0100041，然後按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="1e196-186">Select N0100041 and then click **Finish**.</span></span>  
  
6. <span data-ttu-id="1e196-187">在 [方案總管] 中，沒有新的 BizTalk 協調流程含有兩個新的相關聯的結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="1e196-187">In Solution Explorer, there is a new BizTalk orchestration with two new associated schema files.</span></span> <span data-ttu-id="1e196-188">這些檔案是由 [新增配接器精靈] 所建立。</span><span class="sxs-lookup"><span data-stu-id="1e196-188">These files are created by the Add Adapter Wizard.</span></span> <span data-ttu-id="1e196-189">按兩下 [BizTalk Orchestration.odx]  檔案開啟協調流程。</span><span class="sxs-lookup"><span data-stu-id="1e196-189">Double-click the **BizTalk Orchestration.odx** file to open the orchestration.</span></span>  
  
    <span data-ttu-id="1e196-190">![](../core/media/jdeow-solution-explorer-jde-ow-test-schemas.gif "JDEOW_Solution_Explorer_JDE_OW_TEST_Schemas")</span><span class="sxs-lookup"><span data-stu-id="1e196-190">![](../core/media/jdeow-solution-explorer-jde-ow-test-schemas.gif "JDEOW_Solution_Explorer_JDE_OW_TEST_Schemas")</span></span>  
  
   <span data-ttu-id="1e196-191">此協調流程接受做為從 JD Edwards OneWorld 系統的格式為 XML 檔案的 File 配接器的輸入。</span><span class="sxs-lookup"><span data-stu-id="1e196-191">This orchestration accepts as input from the File adapter an XML file formatted for the JD Edwards OneWorld system.</span></span> <span data-ttu-id="1e196-192">協調流程會使用 JD Edwards OneWorld 配接器，將 XML 檔案傳送至 JD Edwards OneWorld 系統。</span><span class="sxs-lookup"><span data-stu-id="1e196-192">The orchestration uses the JD Edwards OneWorld adapter to send the XML file to the JD Edwards OneWorld system.</span></span> <span data-ttu-id="1e196-193">JD Edwards OneWorld 會處理查詢，並且產生包含結果的輸出 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="1e196-193">JD Edwards OneWorld processes the query and generates an output XML file containing the results.</span></span> <span data-ttu-id="1e196-194">此 XML 檔案會透過 JD Edwards OneWorld 配接器傳回至協調流程，然後 File 配接器會將 XML 檔案寫入至磁碟上的輸出位置。</span><span class="sxs-lookup"><span data-stu-id="1e196-194">This XML file returns to the orchestration through the JD Edwards OneWorld adapter, and the File adapter writes the XML file to the output location on disk.</span></span>  
  
   <span data-ttu-id="1e196-195">若要完成協調流程，您需要建立及設定連接埠來接收和傳送 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="1e196-195">To complete the orchestration, you need to create and configure ports to receive and send the XML files.</span></span> <span data-ttu-id="1e196-196">首先，設定 File 配接器要使用的接收埠，以將包含查詢的 XML 從磁碟輸入至協調流程。</span><span class="sxs-lookup"><span data-stu-id="1e196-196">First, configure a receive port to be used by the File adapter to input the XML containing the query into the orchestration from disk.</span></span>  
  
#### <a name="configure-a-receive-port-to-accept-the-input-xml-file"></a><span data-ttu-id="1e196-197">設定接收埠以接受輸入的 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="1e196-197">Configure a receive port to accept the input XML file</span></span>  
  
1. <span data-ttu-id="1e196-198">按兩下 [BizTalk Orchestration.odx]  檔案開啟協調流程。</span><span class="sxs-lookup"><span data-stu-id="1e196-198">Double-click the **BizTalk Orchestration.odx** file to open the orchestration.</span></span>  
  
2. <span data-ttu-id="1e196-199">在 BizTalk Orchestration.odx 檔內，以滑鼠右鍵按一下左側連接埠介面，並再按**新設定連接埠**。</span><span class="sxs-lookup"><span data-stu-id="1e196-199">In the BizTalk Orchestration.odx file, right-click the left port surface and then click **New Configured Port**.</span></span> <span data-ttu-id="1e196-200">如此將啟動 [連接埠組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="1e196-200">This starts the Port Configuration Wizard.</span></span> <span data-ttu-id="1e196-201">在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="1e196-201">On the **Welcome to the Port Configuration Wizard** page, click **Next**.</span></span>  
  
3. <span data-ttu-id="1e196-202">上**連接埠內容**頁面上，輸入`JDE_File_In`如**名稱**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="1e196-202">On the **Port Properties** page, enter `JDE_File_In` for **Name**, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="1e196-203">在 [選取連接埠類型]  頁面上，選取 [建立新的連接埠類型] ，然後輸入或選取下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="1e196-203">On the **Select a Port Type** page, select **Create a new Port Type**, and then enter or select the following property values:</span></span>  
  
    <span data-ttu-id="1e196-204">**連接埠類型名稱**: `JDE_FileIn_Port`</span><span class="sxs-lookup"><span data-stu-id="1e196-204">**Port Type Name**: `JDE_FileIn_Port`</span></span>  
  
    <span data-ttu-id="1e196-205">**通訊模式**： **單向**</span><span class="sxs-lookup"><span data-stu-id="1e196-205">**Communication Pattern**: **One Way**</span></span>  
  
    <span data-ttu-id="1e196-206">**存取限制**： **內部 - 限制於此專案**</span><span class="sxs-lookup"><span data-stu-id="1e196-206">**Access Restrictions**: **Internal - limited to this project**</span></span>  
  
5. <span data-ttu-id="1e196-207">按 [下一步]  移至 [連接埠繫結]  頁面，然後選取下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="1e196-207">Click **Next** to go to the **Port Binding** page, and then select the following property values:</span></span>  
  
    <span data-ttu-id="1e196-208">**連接埠通訊方向**： **我將總是在此連接埠接收訊息**</span><span class="sxs-lookup"><span data-stu-id="1e196-208">**Port direction of communication**: **I'll always be receiving messages on this port**</span></span>  
  
    <span data-ttu-id="1e196-209">**連接埠繫結**： **稍後指定**</span><span class="sxs-lookup"><span data-stu-id="1e196-209">**Port binding**: **Specify later**</span></span>  
  
6. <span data-ttu-id="1e196-210">按 **[下一步]**，再按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="1e196-210">Click **Next**, and then click **Finish**.</span></span>  
  
   <span data-ttu-id="1e196-211">接著，建立傳送/接收埠，以將包含查詢的初始 XML 輸入檔案傳送至 JD Edwards OneWorld 系統。</span><span class="sxs-lookup"><span data-stu-id="1e196-211">Next, create a send/receive port to send the initial XML input file containing the query to the JD Edwards OneWorld system.</span></span> <span data-ttu-id="1e196-212">此連接埠也會接收 JD Edwards OneWorld 系統在收到呼叫後，所傳回之包含查詢結果的輸出 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="1e196-212">This port will also receive an output XML file containing the query results from the call to the JD Edwards OneWorld system.</span></span>  
  
#### <a name="configure-a-sendreceive-port-to-interface-with-jd-edwards-oneworld"></a><span data-ttu-id="1e196-213">使用 JD Edwards OneWorld 設定介面傳送/接收埠</span><span class="sxs-lookup"><span data-stu-id="1e196-213">Configure a send/receive port to interface with JD Edwards OneWorld</span></span>  
  
1. <span data-ttu-id="1e196-214">在 BizTalk Orchestration.odx 檔內，以滑鼠右鍵按一下右側連接埠介面，並再按**新設定連接埠**。</span><span class="sxs-lookup"><span data-stu-id="1e196-214">In the BizTalk Orchestration.odx file, right-click the right port surface and then click **New Configured Port**.</span></span> <span data-ttu-id="1e196-215">如此將啟動 [連接埠組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="1e196-215">This starts the Port Configuration Wizard.</span></span> <span data-ttu-id="1e196-216">在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="1e196-216">On the **Welcome to the Port Configuration Wizard** page, click **Next**.</span></span>  
  
2. <span data-ttu-id="1e196-217">在 **[選取連接埠類型]** 頁面上，選取 **[使用現有連接埠類型]**。</span><span class="sxs-lookup"><span data-stu-id="1e196-217">On the **Select a Port Type** page, select **Use an existing Port Type**.</span></span> <span data-ttu-id="1e196-218">底下**可用的連接埠類型**，選取 **[JD_OW_Test.N0100041**，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="1e196-218">Under **Available Port Types**, select **JD_OW_Test.N0100041**,and then click **Next**.</span></span>  
  
    <span data-ttu-id="1e196-219">![](../core/media/a421358c-6e90-4fe0-b243-6beb1b51955a.gif "a421358c-6e90-4fe0-b243-6beb1b51955a")</span><span class="sxs-lookup"><span data-stu-id="1e196-219">![](../core/media/a421358c-6e90-4fe0-b243-6beb1b51955a.gif "a421358c-6e90-4fe0-b243-6beb1b51955a")</span></span>  
  
3. <span data-ttu-id="1e196-220">選取下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="1e196-220">Select the following property values:</span></span>  
  
    <span data-ttu-id="1e196-221">**連接埠通訊方向**:**我將會傳送要求並接收回應**</span><span class="sxs-lookup"><span data-stu-id="1e196-221">**Port direction of communication**: **I'll be sending a request and receiving a response**</span></span>  
  
    <span data-ttu-id="1e196-222">**連接埠繫結**： **稍後指定**</span><span class="sxs-lookup"><span data-stu-id="1e196-222">**Port binding**: **Specify later**</span></span>  
  
4. <span data-ttu-id="1e196-223">按 **[下一步]**，再按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="1e196-223">Click **Next**, and then click **Finish**.</span></span> <span data-ttu-id="1e196-224">您將會在連接埠介面上看到連接埠和可用的方法。</span><span class="sxs-lookup"><span data-stu-id="1e196-224">On the port surface you will see the port and the available methods.</span></span>  
  
   <span data-ttu-id="1e196-225">最後，設定 File 配接器要使用的傳送埠，以將包含查詢結果的 XML 輸出至磁碟。</span><span class="sxs-lookup"><span data-stu-id="1e196-225">Finally, configure a send port to be used by the File adapter to output the XML containing the query results to disk.</span></span>  
  
#### <a name="configure-a-send-port-to-output-the-xml-file-to-disk"></a><span data-ttu-id="1e196-226">設定傳送埠來輸出至磁碟的 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="1e196-226">Configure a send port to output the XML file to disk</span></span>  
  
1. <span data-ttu-id="1e196-227">在 BizTalk Orchestration.odx 檔內，以滑鼠右鍵按一下左側連接埠介面，並再按**新設定連接埠**。</span><span class="sxs-lookup"><span data-stu-id="1e196-227">In the BizTalk Orchestration.odx file, right-click the left port surface and then click **New Configured Port**.</span></span> <span data-ttu-id="1e196-228">如此將啟動 [連接埠組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="1e196-228">This starts the Port Configuration Wizard.</span></span> <span data-ttu-id="1e196-229">在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="1e196-229">On the **Welcome to the Port Configuration Wizard** page, click **Next**.</span></span>  
  
2. <span data-ttu-id="1e196-230">上**連接埠內容**頁面上，輸入`JDE_FileOut`如**名稱**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="1e196-230">On the **Port Properties** page, enter `JDE_FileOut` for **Name**, and then click **Next**.</span></span>  
  
3. <span data-ttu-id="1e196-231">在 [選取連接埠類型]  頁面上，選取 [建立新的連接埠類型] ，然後輸入或選取下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="1e196-231">On the **Select a Port Type** page, select **Create a new Port Type**, and then enter or select the following property values:</span></span>  
  
    <span data-ttu-id="1e196-232">**連接埠類型名稱**: `JDE_FileOut_Port`</span><span class="sxs-lookup"><span data-stu-id="1e196-232">**Port Type Name**: `JDE_FileOut_Port`</span></span>  
  
    <span data-ttu-id="1e196-233">**通訊模式**： **單向**</span><span class="sxs-lookup"><span data-stu-id="1e196-233">**Communication Pattern**: **One Way**</span></span>  
  
    <span data-ttu-id="1e196-234">**存取限制**： **內部 - 限制於此專案**</span><span class="sxs-lookup"><span data-stu-id="1e196-234">**Access Restrictions**: **Internal - limited to this project**</span></span>  
  
4. <span data-ttu-id="1e196-235">按 [下一步]  移至 [連接埠繫結]  頁面，然後選取下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="1e196-235">Click **Next** to go to the **Port Binding** page, and then select the following property values:</span></span>  
  
    <span data-ttu-id="1e196-236">**連接埠通訊方向**： **我將總是在此連接埠傳送訊息**</span><span class="sxs-lookup"><span data-stu-id="1e196-236">**Port direction of communication**: **I'll always be sending messages on this port**</span></span>  
  
    <span data-ttu-id="1e196-237">**連接埠繫結**： **稍後指定**</span><span class="sxs-lookup"><span data-stu-id="1e196-237">**Port binding**: **Specify later**</span></span>  
  
5. <span data-ttu-id="1e196-238">按 **[下一步]**，再按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="1e196-238">Click **Next**, and then click **Finish**.</span></span>  
  
   <span data-ttu-id="1e196-239">新的連接埠 」 和 「 的 JD Edwards OneWorld 服務可用的方法，會顯示在連接埠介面上。</span><span class="sxs-lookup"><span data-stu-id="1e196-239">Displayed on the port surface are the new ports and the available methods for the JD Edwards OneWorld services.</span></span> <span data-ttu-id="1e196-240">稍後您將指定的 JD Edwards OneWorld 配接器傳送和接收來自 JD Edwards OneWorld 系統的檔案。</span><span class="sxs-lookup"><span data-stu-id="1e196-240">Later you will specify the JD Edwards OneWorld adapter to send and receive files from the JD Edwards OneWorld system.</span></span>  
  
   <span data-ttu-id="1e196-241">**JDE_File_In**並**JDE_File_Out**您剛建立需要的連接埠相關聯的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="1e196-241">The **JDE_File_In** and **JDE_File_Out** ports you just created need associated message types.</span></span>  
  
#### <a name="assign-message-types-to-the-ports"></a><span data-ttu-id="1e196-242">指派的連接埠的訊息類型</span><span class="sxs-lookup"><span data-stu-id="1e196-242">Assign message types to the ports</span></span>  
  
1. <span data-ttu-id="1e196-243">在左側連接埠介面上**JDE_File_In**連接埠，按一下**要求**。</span><span class="sxs-lookup"><span data-stu-id="1e196-243">On the left port surface, on the **JDE_File_In** port, click **Request**.</span></span> <span data-ttu-id="1e196-244">在 [屬性] 視窗中，依序展開**訊息類型**，展開**多部分訊息**，然後按一下**JDE_OW_TestAddressBookMasterMBF**。</span><span class="sxs-lookup"><span data-stu-id="1e196-244">In the Properties window, expand **Message Type**, expand **Multi-part Message**, and then click **JDE_OW_TestAddressBookMasterMBF**.</span></span>  
  
2. <span data-ttu-id="1e196-245">在左側連接埠介面上**JDE_File_Out**連接埠，按一下**要求**。</span><span class="sxs-lookup"><span data-stu-id="1e196-245">On the left port surface, on the **JDE_File_Out** port, click **Request**.</span></span> <span data-ttu-id="1e196-246">在 [屬性] 視窗中，依序展開**訊息類型**，展開**多部分訊息**，然後按一下**JDE_OW_TestAddressBookMasterMBFResponse**。</span><span class="sxs-lookup"><span data-stu-id="1e196-246">In the Properties window, expand **Message Type**, expand **Multi-part Message**, and then click **JDE_OW_TestAddressBookMasterMBFResponse**.</span></span>  
  
   <span data-ttu-id="1e196-247">將兩個**傳送**圖形與兩個**接收**圖形插入協調流程，以連結至連接埠。</span><span class="sxs-lookup"><span data-stu-id="1e196-247">Insert two **Send** shapes and two **Receive** shapes into the orchestration to link to the ports.</span></span>  
  
#### <a name="add-send-and-receive-shapes"></a><span data-ttu-id="1e196-248">新增傳送和接收圖形</span><span class="sxs-lookup"><span data-stu-id="1e196-248">Add Send and Receive shapes</span></span>  
  
1.  <span data-ttu-id="1e196-249">從工具箱拖曳 **接收** 元件，緊解著將其放置於協調流程 (綠色圓形) 的開頭下方。</span><span class="sxs-lookup"><span data-stu-id="1e196-249">Drag a **Receive** component from the Toolbox and drop it immediately below the start of the orchestration (the green circle).</span></span> <span data-ttu-id="1e196-250">按一下 **接收**圖形，然後在 屬性 視窗中，輸入`Get_File`如**名稱**，並設定**啟動**至`true`。</span><span class="sxs-lookup"><span data-stu-id="1e196-250">Click the **Receive** shape, and in the Properties window, enter `Get_File` for the **Name**, and set **Activate** to `true`.</span></span> <span data-ttu-id="1e196-251">如此會在此接收埠收到內送文件時啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="1e196-251">Doing so will activate the orchestration when an incoming document is received on this receive port.</span></span>  
  
2.  <span data-ttu-id="1e196-252">拖曳**傳送**元件從 [工具箱] 中，把它放在正下方**GetFileReceive**圖形。</span><span class="sxs-lookup"><span data-stu-id="1e196-252">Drag a **Send** component from the Toolbox and drop it immediately below the **GetFileReceive** shape.</span></span> <span data-ttu-id="1e196-253">按一下新**傳送**圖形，然後在 [屬性] 視窗中，輸入`SendToJDEOW`如**名稱**。</span><span class="sxs-lookup"><span data-stu-id="1e196-253">Click the new **Send** shape, and in the Properties window, enter `SendToJDEOW` for the **Name**.</span></span>  
  
3.  <span data-ttu-id="1e196-254">拖曳**接收**元件從 [工具箱] 中，把它放在正下方**SendToJDEOWSend**圖形。</span><span class="sxs-lookup"><span data-stu-id="1e196-254">Drag a **Receive** component from the Toolbox and drop it immediately below the **SendToJDEOWSend** shape.</span></span> <span data-ttu-id="1e196-255">按一下 **接收**圖形，然後在 屬性 視窗中，輸入`JDEOW_Resp`如**名稱**。</span><span class="sxs-lookup"><span data-stu-id="1e196-255">Click the **Receive** shape, and in the Properties window, enter `JDEOW_Resp` for the **Name**.</span></span>  
  
4.  <span data-ttu-id="1e196-256">拖曳**傳送**元件從 [工具箱] 中，把它放在正下方**JDEOW_RespReceive**圖形。</span><span class="sxs-lookup"><span data-stu-id="1e196-256">Drag a **Send** component from the Toolbox and drop it immediately below the **JDEOW_RespReceive** shape.</span></span> <span data-ttu-id="1e196-257">按一下新**傳送**圖形，然後在 [屬性] 視窗中，輸入`FileToDisk`如**名稱**。</span><span class="sxs-lookup"><span data-stu-id="1e196-257">Click the new **Send** shape, and in the Properties window, enter `FileToDisk` for the **Name**.</span></span>  
  
     <span data-ttu-id="1e196-258">![](../core/media/jdeow-orchestration-multipartmessages.gif "JDEOW_Orchestration_MultiPartMessages")</span><span class="sxs-lookup"><span data-stu-id="1e196-258">![](../core/media/jdeow-orchestration-multipartmessages.gif "JDEOW_Orchestration_MultiPartMessages")</span></span>  
  
5.  <span data-ttu-id="1e196-259">連接 **[jde_filein]** 連接埠連接到**GetFileReceive**元件。</span><span class="sxs-lookup"><span data-stu-id="1e196-259">Connect the **JDE_FileIn** port to the **GetFileReceive** component.</span></span>  
  
6.  <span data-ttu-id="1e196-260">連接**JDE_FileOut**連接埠連接到**FileToDiskReceive**元件。</span><span class="sxs-lookup"><span data-stu-id="1e196-260">Connect the **JDE_FileOut** port to the **FileToDiskReceive** component.</span></span>  
  
7.  <span data-ttu-id="1e196-261">移至**協調流程檢視**並展開**訊息**。</span><span class="sxs-lookup"><span data-stu-id="1e196-261">Go to **Orchestration View** and expand **Messages**.</span></span> <span data-ttu-id="1e196-262">變更的識別項**Message_1**要`MsgToJDEOW`，以及**Message_2**至 `JDEOW_Resp.`</span><span class="sxs-lookup"><span data-stu-id="1e196-262">Change the identifier for **Message_1** to `MsgToJDEOW`, and for **Message_2** to `JDEOW_Resp.`</span></span>  
  
8.  <span data-ttu-id="1e196-263">反白顯示**SendToJDEOWSend**元件並設定其**訊息**屬性設**MsgToJDEOW**。</span><span class="sxs-lookup"><span data-stu-id="1e196-263">Highlight the **SendToJDEOWSend** component and set its **Message** property to **MsgToJDEOW**.</span></span>  
  
9. <span data-ttu-id="1e196-264">反白顯示**JDEOW_RespReceive**元件並設定其**訊息**屬性設 **[jdeow_resp]**。</span><span class="sxs-lookup"><span data-stu-id="1e196-264">Highlight the **JDEOW_RespReceive** component and set its **Message** property to **JDEOW_Resp**.</span></span>  
  
10. <span data-ttu-id="1e196-265">連接 **[sendtojdeow]** 要**要求**一部分**JDE_OW_Port**連接埠。</span><span class="sxs-lookup"><span data-stu-id="1e196-265">Connect **SendToJDEOW** to the **Request** portion of the **JDE_OW_Port** port.</span></span>  
  
11. <span data-ttu-id="1e196-266">連接 **[jdeow_resp]** 要**回應**一部分**JDE_OW_Port**連接埠。</span><span class="sxs-lookup"><span data-stu-id="1e196-266">Connect **JDEOW_Resp** to the **Response** portion of the **JDE_OW_Port** port.</span></span>  
  
     <span data-ttu-id="1e196-267">![](../core/media/jdeow-portsurface-connectcomponentstoports.gif "JDEOW_PortSurface_ConnectComponentsToPorts")</span><span class="sxs-lookup"><span data-stu-id="1e196-267">![](../core/media/jdeow-portsurface-connectcomponentstoports.gif "JDEOW_PortSurface_ConnectComponentsToPorts")</span></span>  
  
## <a name="step-4-build-and-deploy-the-project"></a><span data-ttu-id="1e196-268">步驟 4： 建置並部署專案</span><span class="sxs-lookup"><span data-stu-id="1e196-268">Step 4: Build and deploy the project</span></span>  
 <span data-ttu-id="1e196-269">現在 BizTalk 專案已完成，然後您可以建置並部署在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1e196-269">Now the BizTalk project is complete and you can build and deploy it in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
1.  <span data-ttu-id="1e196-270">開始**Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="1e196-270">Start **Visual Studio Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="1e196-271">若要建置專案時，您會需要強式名稱金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="1e196-271">To build the project, you need a strong name key file.</span></span> <span data-ttu-id="1e196-272">在命令提示字元中，輸入下列命令以建立強式名稱金鑰檔：</span><span class="sxs-lookup"><span data-stu-id="1e196-272">At the command prompt, enter the following to create a strong name key file:</span></span>  
  
     <span data-ttu-id="1e196-273">**sn-k [labs.snk]**</span><span class="sxs-lookup"><span data-stu-id="1e196-273">**sn -k labs.snk**</span></span>  
  
3.  <span data-ttu-id="1e196-274">在 [方案總管] 中，以滑鼠右鍵按一下 **[jd_ow_test]** 專案，然後再按一下**屬性**啟動專案的專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="1e196-274">In Solution Explorer, right-click the **JD_OW_Test** project, and then click **Properties** to launch the Project Designer for the project.</span></span>  
  
4.  <span data-ttu-id="1e196-275">按一下 [ **簽署** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1e196-275">Click the **Signing** tab.</span></span>  
  
5.  <span data-ttu-id="1e196-276">選取 **[簽署組件]** 選項、按一下 **[選擇強式名稱金鑰檔]** 選項的下拉式清單，然後按一下 **[瀏覽]**。</span><span class="sxs-lookup"><span data-stu-id="1e196-276">Select **Sign the assembly** option, click drop-down list for the **Choose a strong name key file** option, and then click **Browse**.</span></span>  
  
6.  <span data-ttu-id="1e196-277">瀏覽並選取金鑰檔： **[labs.snk]**，然後按一下 **[開啟]**。</span><span class="sxs-lookup"><span data-stu-id="1e196-277">Browse to select the key file: **labs.snk**, and then click **Open**.</span></span>  
  
7.  <span data-ttu-id="1e196-278">按一下 [專案設計工具] 中的 **[部署]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1e196-278">Click **Deployment** tab in the Project Designer.</span></span>  
  
8.  <span data-ttu-id="1e196-279">設定**應用程式名稱**至`JDE_OW_Test`。</span><span class="sxs-lookup"><span data-stu-id="1e196-279">Set the **Application Name** to `JDE_OW_Test`.</span></span>  
  
9. <span data-ttu-id="1e196-280">在 [方案總管] 中，以滑鼠右鍵按一下**JDE_OW_Test**專案，然後再按一下**建置。**</span><span class="sxs-lookup"><span data-stu-id="1e196-280">In Solution Explorer, right-click the **JDE_OW_Test** project, and then click **Build.**</span></span>  
  
     <span data-ttu-id="1e196-281">![](../core/media/jdeow-buildcompleteoutput.gif "JDEOW_BuildCompleteOutput")</span><span class="sxs-lookup"><span data-stu-id="1e196-281">![](../core/media/jdeow-buildcompleteoutput.gif "JDEOW_BuildCompleteOutput")</span></span>  
  
10. <span data-ttu-id="1e196-282">順利完成建置之後，請以滑鼠右鍵按一下 **[XX_JD Edwards oneworldquery]** 專案，然後再按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="1e196-282">After the build completes successfully, right-click the **XX_JD Edwards OneWorldQuery** project, and then click **Deploy**.</span></span> <span data-ttu-id="1e196-283">在輸出視窗中會顯示下列輸出：</span><span class="sxs-lookup"><span data-stu-id="1e196-283">In the output window the following output will be displayed:</span></span>  
  
     <span data-ttu-id="1e196-284">![](../core/media/jdeow-deployoutput.gif "JDEOW_DeployOutput")</span><span class="sxs-lookup"><span data-stu-id="1e196-284">![](../core/media/jdeow-deployoutput.gif "JDEOW_DeployOutput")</span></span>  
  
## <a name="step-5-test-the-application-and-viewing-the-xml-output"></a><span data-ttu-id="1e196-285">步驟 5： 測試應用程式，並檢視 XML 輸出</span><span class="sxs-lookup"><span data-stu-id="1e196-285">Step 5: Test the Application and Viewing the XML Output</span></span>  
 <span data-ttu-id="1e196-286">現在您將測試所建立和部署的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1e196-286">Now you will test the application that you have created and deployed.</span></span> <span data-ttu-id="1e196-287">您會建立啟動協調流程處理序的 XML 檔案，然後設定在應用程式內接收和傳送 XML 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="1e196-287">You will create the XML file that starts the orchestration process, and then you will configure folders to receive and send XML files within the application.</span></span> <span data-ttu-id="1e196-288">設定應用程式之後，您將會執行它並檢視協調流程所傳回的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="1e196-288">After you have configured the application, you will run it and view the XML files that the orchestration returns.</span></span>  
  
#### <a name="generate-the-xml-file-for-the-query"></a><span data-ttu-id="1e196-289">產生查詢的 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="1e196-289">Generate the XML file for the query</span></span>  
  
1.  <span data-ttu-id="1e196-290">在 [方案總管] 中，按兩下 **[n0100041service_n0100041.xsd]** 開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="1e196-290">In Solution Explorer, double-click **N0100041Service_N0100041.xsd** to open the file.</span></span>  
  
2.  <span data-ttu-id="1e196-291">以滑鼠右鍵按一下 **[n0100041service_n0100041.xsd]** ，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="1e196-291">Right-click **N0100041Service_N0100041.xsd** and then click **Properties**.</span></span> <span data-ttu-id="1e196-292">針對 **輸出執行個體檔案名稱** 輸入範例 XML 的下列路徑和檔案名稱：</span><span class="sxs-lookup"><span data-stu-id="1e196-292">For the **Output Instance Filename** enter the following path and file name for the sample XML:</span></span>  
  
     `C:\LABS\JDE_OW_TEST\SAMPLE.XML`  
  
3.  <span data-ttu-id="1e196-293">按一下 **[確定].**</span><span class="sxs-lookup"><span data-stu-id="1e196-293">Click **OK.**</span></span> <span data-ttu-id="1e196-294">在 [屬性] 視窗中，選取**\<結構描述\>** 並設定**根參考：** 至`AddressBookMasterMBF`。</span><span class="sxs-lookup"><span data-stu-id="1e196-294">In the Properties window, select **\<Schema\>** and set **Root Reference:** to `AddressBookMasterMBF`.</span></span> <span data-ttu-id="1e196-295">這會導致產生的 XML 只包含**查詢**xml。</span><span class="sxs-lookup"><span data-stu-id="1e196-295">This will cause the generated XML to include only the **Query** xml.</span></span>  
  
     <span data-ttu-id="1e196-296">![](../core/media/jdeow-jde-ow-test-msvisualstudio-schemas.gif "JDEOW_JDE_OW_Test_MSVISUALSTUDIO_SCHEMAS")</span><span class="sxs-lookup"><span data-stu-id="1e196-296">![](../core/media/jdeow-jde-ow-test-msvisualstudio-schemas.gif "JDEOW_JDE_OW_Test_MSVISUALSTUDIO_SCHEMAS")</span></span>  
  
4.  <span data-ttu-id="1e196-297">以滑鼠右鍵按一下 **[n0100041service_n0100041.xsd]** ，然後按一下**產生的執行個體**。</span><span class="sxs-lookup"><span data-stu-id="1e196-297">Right-click **N0100041Service_N0100041.xsd** and then click **Generate Instance**.</span></span> <span data-ttu-id="1e196-298">這會產生**Sample.xml**檔案。</span><span class="sxs-lookup"><span data-stu-id="1e196-298">This generates the **Sample.xml** file.</span></span> <span data-ttu-id="1e196-299">這個檔案將做為配接器的輸入，放置在接收位置以啟動協調流程處理序。</span><span class="sxs-lookup"><span data-stu-id="1e196-299">This file will be dropped in the receive location as input to the adapter to start the orchestration process.</span></span>  
  
#### <a name="configure-and-start-the-biztalk-application"></a><span data-ttu-id="1e196-300">設定並啟動 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="1e196-300">Configure and start the BizTalk application</span></span>  
  
1. <span data-ttu-id="1e196-301">設定用於接收內送檔案及傳送外寄檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="1e196-301">Configure folders for receiving the incoming files and sending the outgoing files.</span></span> <span data-ttu-id="1e196-302">移至**C:\LABS\JDE_OW_Test**並建立兩個新的子資料夾，名為`FileIn`和`FileOut`。</span><span class="sxs-lookup"><span data-stu-id="1e196-302">Go to **C:\LABS\JDE_OW_Test** and create two new subfolders named `FileIn` and `FileOut`.</span></span>  
  
2. <span data-ttu-id="1e196-303">中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**主控台根目錄**，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="1e196-303">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console,expand **Console Root**, expand**BizTalk Server Administration**, expand **BizTalk Group**, and expand **Applications**.</span></span>  
  
3. <span data-ttu-id="1e196-304">以滑鼠右鍵按一下**JDE_OW_Test**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="1e196-304">Right-click **JDE_OW_Test**, and then click **Configure**.</span></span>  
  
    <span data-ttu-id="1e196-305">![](../core/media/jdeow-configureapplicationjde-ow-test.gif "JDEOW_ConfigureApplicationJDE_OW_Test")</span><span class="sxs-lookup"><span data-stu-id="1e196-305">![](../core/media/jdeow-configureapplicationjde-ow-test.gif "JDEOW_ConfigureApplicationJDE_OW_Test")</span></span>  
  
4. <span data-ttu-id="1e196-306">選取 [Orchestration_1]  ，並按一下 [主機]  下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="1e196-306">Select **Orchestration_1** and click the **Host** drop-down box.</span></span> <span data-ttu-id="1e196-307">選取 **[BizTalkServerApplication]**。</span><span class="sxs-lookup"><span data-stu-id="1e196-307">Select **BizTalkServerApplication**.</span></span>  
  
5. <span data-ttu-id="1e196-308">底下**接收連接埠**，按一下 **\<None\>**。</span><span class="sxs-lookup"><span data-stu-id="1e196-308">Under **Receive Ports**, click **\<None\>**.</span></span> <span data-ttu-id="1e196-309">在下拉式清單中選取 [新增接收埠] 。</span><span class="sxs-lookup"><span data-stu-id="1e196-309">In the drop-down list, select **New Receive Port**.</span></span>  
  
6. <span data-ttu-id="1e196-310">針對**名稱**，型別`JDE_FileIn_Port`，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="1e196-310">For **Name**, type `JDE_FileIn_Port`, and then click **OK**.</span></span> <span data-ttu-id="1e196-311">訊息方塊會出現，指出您需要指定接收位置。</span><span class="sxs-lookup"><span data-stu-id="1e196-311">A message box appears stating that you need to designate a receive location.</span></span> <span data-ttu-id="1e196-312">按一下 [確定] 及 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="1e196-312">Click **OK**, and then click **New**.</span></span>  
  
    <span data-ttu-id="1e196-313">![](../core/media/jdeow-filein-port-receiveportproperties.gif "JDEOW_FileIn_Port_ReceivePortProperties")</span><span class="sxs-lookup"><span data-stu-id="1e196-313">![](../core/media/jdeow-filein-port-receiveportproperties.gif "JDEOW_FileIn_Port_ReceivePortProperties")</span></span>  
  
7. <span data-ttu-id="1e196-314">輸入或選取屬性的下列值：</span><span class="sxs-lookup"><span data-stu-id="1e196-314">Type or select the following values for the properties:</span></span>  
  
    <span data-ttu-id="1e196-315">**名稱**: JDE_`FileInLoc`</span><span class="sxs-lookup"><span data-stu-id="1e196-315">**Name**: JDE_`FileInLoc`</span></span>  
  
    <span data-ttu-id="1e196-316">**類型**： **檔案**</span><span class="sxs-lookup"><span data-stu-id="1e196-316">**Type**: **File**</span></span>  
  
    <span data-ttu-id="1e196-317">**接收處理常式**： **BizTalkServerApplication**</span><span class="sxs-lookup"><span data-stu-id="1e196-317">**Receive Handler**: **BizTalkServerApplication**</span></span>  
  
    <span data-ttu-id="1e196-318">**接收管線**： **XMLReceive**</span><span class="sxs-lookup"><span data-stu-id="1e196-318">**Receive Pipeline**: **XMLReceive**</span></span>  
  
    <span data-ttu-id="1e196-319">![](../core/media/jdeow-filein-loc-receivelocationproperties.gif "JDEOW_FileIn_Loc_ReceiveLocationProperties")</span><span class="sxs-lookup"><span data-stu-id="1e196-319">![](../core/media/jdeow-filein-loc-receivelocationproperties.gif "JDEOW_FileIn_Loc_ReceiveLocationProperties")</span></span>  
  
8. <span data-ttu-id="1e196-320">按一下 **設定**，型別`C:\LABS\JDE_OW_Test\FileIn`如**接收資料夾**，然後按一下**確定**三次。</span><span class="sxs-lookup"><span data-stu-id="1e196-320">Click **Configure**, type `C:\LABS\JDE_OW_Test\FileIn` for **Receive Folder**, and then click **OK** three times.</span></span>  
  
    <span data-ttu-id="1e196-321">![](../core/media/jdeow-file-transport-properties-filein.gif "JDEOW_File_Transport_Properties_FileIn")</span><span class="sxs-lookup"><span data-stu-id="1e196-321">![](../core/media/jdeow-file-transport-properties-filein.gif "JDEOW_File_Transport_Properties_FileIn")</span></span>  
  
9. <span data-ttu-id="1e196-322">按一下  **\<無\>** for **JDE_OW_Port**下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="1e196-322">Click **\<None\>** for **JDE_OW_Port** in the drop-down list.</span></span>  
  
10. <span data-ttu-id="1e196-323">選取 **新傳送埠**，然後選取或輸入屬性的下列值：</span><span class="sxs-lookup"><span data-stu-id="1e196-323">Select **New Send Port** and then select or type the following values for the properties:</span></span>  
  
     <span data-ttu-id="1e196-324">**名稱**：`JDE_OW_Port`</span><span class="sxs-lookup"><span data-stu-id="1e196-324">**Name**: `JDE_OW_Port`</span></span>  
  
     <span data-ttu-id="1e196-325">**型別**: **JDE_OneWorld**</span><span class="sxs-lookup"><span data-stu-id="1e196-325">**Type**: **JDE_OneWorld**</span></span>  
  
     <span data-ttu-id="1e196-326">**傳送處理常式**： **BizTalkServerApplication**</span><span class="sxs-lookup"><span data-stu-id="1e196-326">**Send Handler**: **BizTalkServerApplication**</span></span>  
  
     <span data-ttu-id="1e196-327">**管線**： **XMLTransmit** 和 **XMLReceive**</span><span class="sxs-lookup"><span data-stu-id="1e196-327">**Pipelines**: **XMLTransmit** and **XMLReceive**</span></span>  
  
11. <span data-ttu-id="1e196-328">按一下 [設定] ，然後輸入下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="1e196-328">Click **Configure**, and then enter the following property values:</span></span>  
  
     <span data-ttu-id="1e196-329">**主機：** \<輸入 JDEOW 主控件名稱\></span><span class="sxs-lookup"><span data-stu-id="1e196-329">**Host:** \<enter your JDEOW host name\></span></span>  
  
     <span data-ttu-id="1e196-330">**JAVA_HOME:** `C:\j2sdk1.4.2_08`</span><span class="sxs-lookup"><span data-stu-id="1e196-330">**JAVA_HOME:** `C:\j2sdk1.4.2_08`</span></span>  
  
     <span data-ttu-id="1e196-331">**JDEdwards 環境：** \<輸入 JDEOW 環境\></span><span class="sxs-lookup"><span data-stu-id="1e196-331">**JDEdwards Environment:** \<enter your JDEOW environment\></span></span>  
  
     <span data-ttu-id="1e196-332">**JDEdwards JAR 檔案：** <enter full path of JAR files></span><span class="sxs-lookup"><span data-stu-id="1e196-332">**JDEdwards JAR files:** <enter full path of JAR files></span></span>  
  
     `C:JDEOWJarsBTSLIBInterop.jar; C:JDEOWJarsConnector.jar; C:JDEOWJarsKernel.jar;C:Program FilesMicrosoft BizTalk Adapters for Enterprise ApplicationsJ.D. Edwards OneWorld®ClassesJDEJAccess.jar`  
  
     <span data-ttu-id="1e196-333">**密碼：** 使用下拉式清單，然後輸入 JD Edwards OneWorld 密碼。</span><span class="sxs-lookup"><span data-stu-id="1e196-333">**Password:** Use the drop-down list and then enter your JD Edwards OneWorld password.</span></span>  
  
     <span data-ttu-id="1e196-334">**連接埠：**  `6009`</span><span class="sxs-lookup"><span data-stu-id="1e196-334">**Port:**  `6009`</span></span>  
  
     <span data-ttu-id="1e196-335">**使用者名稱：** <enter your JD Edwards User Name></span><span class="sxs-lookup"><span data-stu-id="1e196-335">**User Name:** <enter your JD Edwards User Name></span></span>  
  
     <span data-ttu-id="1e196-336">![](../core/media/jdeow-transportproperties-configurebutton2.gif "JDEOW_TransportProperties_ConfigureButton2")</span><span class="sxs-lookup"><span data-stu-id="1e196-336">![](../core/media/jdeow-transportproperties-configurebutton2.gif "JDEOW_TransportProperties_ConfigureButton2")</span></span>  
  
12. <span data-ttu-id="1e196-337">按兩下 [確定]  關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1e196-337">Click **OK** twice to close the dialog boxes.</span></span>  
  
13. <span data-ttu-id="1e196-338">在 設定 Applicationwindow 中，按一下**\<無\>** for **JDE_FileOut**下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="1e196-338">In the Configure Applicationwindow, click **\<None\>** for **JDE_FileOut** in the drop-down list.</span></span>  
  
14. <span data-ttu-id="1e196-339">選取 [新增傳送埠]  ，然後選取或輸入下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="1e196-339">Select **New Send Port** and type or select the following values for the properties:</span></span>  
  
     <span data-ttu-id="1e196-340">**名稱**：`FileOutPort`</span><span class="sxs-lookup"><span data-stu-id="1e196-340">**Name**: `FileOutPort`</span></span>  
  
     <span data-ttu-id="1e196-341">**類型**： **檔案**</span><span class="sxs-lookup"><span data-stu-id="1e196-341">**Type**: **File**</span></span>  
  
     <span data-ttu-id="1e196-342">**傳送處理常式**： **BizTalkServerApplication**</span><span class="sxs-lookup"><span data-stu-id="1e196-342">**Send Handler**: **BizTalkServerApplication**</span></span>  
  
     <span data-ttu-id="1e196-343">**傳送管線**： **XMLTransmit**</span><span class="sxs-lookup"><span data-stu-id="1e196-343">**Send Pipeline**: **XMLTransmit**</span></span>  
  
15. <span data-ttu-id="1e196-344">按一下 **設定**並輸入`C:\Labs\JDE_OW_Test\FileOut`如**目的地資料夾。**</span><span class="sxs-lookup"><span data-stu-id="1e196-344">Click **Configure** and type`C:\Labs\JDE_OW_Test\FileOut` for **Destination Folder.**</span></span> <span data-ttu-id="1e196-345">保持 **%MessageID%.xml** for**檔案名稱**因為這會導致每個訊息的唯一檔案。</span><span class="sxs-lookup"><span data-stu-id="1e196-345">Keep **%MessageID%.xml** for **File Name** because this results in a unique file for each message.</span></span>  
  
     <span data-ttu-id="1e196-346">![](../core/media/jdeow-file-transport-properties-fileout.gif "JDEOW_File_Transport_Properties_FileOut")</span><span class="sxs-lookup"><span data-stu-id="1e196-346">![](../core/media/jdeow-file-transport-properties-fileout.gif "JDEOW_File_Transport_Properties_FileOut")</span></span>  
  
16. <span data-ttu-id="1e196-347">按三下 [確定]  關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1e196-347">Click **OK** three times to close the dialog boxes.</span></span>  
  
17. <span data-ttu-id="1e196-348">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下滑鼠右鍵**JDE_OW_Test**應用程式，，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="1e196-348">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console,right-click the **JDE_OW_Test** application, and then click **Start**.</span></span>  
  
#### <a name="test-the-orchestration"></a><span data-ttu-id="1e196-349">測試協調流程</span><span class="sxs-lookup"><span data-stu-id="1e196-349">Test the orchestration</span></span>  
  
1.  <span data-ttu-id="1e196-350">在  **C:\Labs\JDE_OW_Test**目錄**Sample.xml**檔案會顯示為：</span><span class="sxs-lookup"><span data-stu-id="1e196-350">In the **C:\Labs\JDE_OW_Test** directory the **Sample.xml** file will appear as:</span></span>  
  
     <span data-ttu-id="1e196-351">![](../core/media/jdeow-samplexml-notepad-addressbookmastermbf.gif "JDEOW_SampleXML_Notepad_AddressBookMasterMBF")</span><span class="sxs-lookup"><span data-stu-id="1e196-351">![](../core/media/jdeow-samplexml-notepad-addressbookmastermbf.gif "JDEOW_SampleXML_Notepad_AddressBookMasterMBF")</span></span>  
  
2.  <span data-ttu-id="1e196-352">編輯**Sample.xml**檔案，以移除以外的所有內容**cActionCode**並**mnAddressBookNumber**項目。</span><span class="sxs-lookup"><span data-stu-id="1e196-352">Edit the **Sample.xml** file to remove everything except the **cActionCode** and **mnAddressBookNumber** elements.</span></span>  
  
     <span data-ttu-id="1e196-353">![](../core/media/jdeow-samplexml-notepad-cactioncode.gif "JDEOW_SampleXML_Notepad_cActionCode")</span><span class="sxs-lookup"><span data-stu-id="1e196-353">![](../core/media/jdeow-samplexml-notepad-cactioncode.gif "JDEOW_SampleXML_Notepad_cActionCode")</span></span>  
  
3.  <span data-ttu-id="1e196-354">針對**cActionCode**項目插入字母`i`。</span><span class="sxs-lookup"><span data-stu-id="1e196-354">For the **cActionCode** element insert the letter `i`.</span></span>  
  
4.  <span data-ttu-id="1e196-355">針對**mnAddressBookNumber**插入數字`500`。</span><span class="sxs-lookup"><span data-stu-id="1e196-355">For **mnAddressBookNumber** insert the number `500`.</span></span>  
  
5.  <span data-ttu-id="1e196-356">儲存變更，並將檔案複製到**C:\Labs\JDE_OW_Test\FileIn**資料夾。</span><span class="sxs-lookup"><span data-stu-id="1e196-356">Save the changes and copy the file to the **C:\Labs\JDE_OW_Test\FileIn** folder.</span></span> <span data-ttu-id="1e196-357">這是啟動協調流程程序的接收位置。</span><span class="sxs-lookup"><span data-stu-id="1e196-357">This is the receive location that starts the orchestration process.</span></span>  
  
6.  <span data-ttu-id="1e196-358">在幾秒鐘之後，XML 檔案應該會出現在**C:\Labs\JDE_OW_Test\FileOut**資料夾。</span><span class="sxs-lookup"><span data-stu-id="1e196-358">In a few seconds, an XML file should appear in the **C:\Labs\JDE_OW_Test\FileOut** folder.</span></span> <span data-ttu-id="1e196-359">此項應該包含所有記錄的位址是 500 的位置。</span><span class="sxs-lookup"><span data-stu-id="1e196-359">This should contain the all the records where the address is 500.</span></span>  
  
     <span data-ttu-id="1e196-360">![](../core/media/jdeow-xml-output-jde-callbsfn.gif "JDEOW_XML_Output_JDE_CALLBSFN")</span><span class="sxs-lookup"><span data-stu-id="1e196-360">![](../core/media/jdeow-xml-output-jde-callbsfn.gif "JDEOW_XML_Output_JDE_CALLBSFN")</span></span>  
  
     <span data-ttu-id="1e196-361">這個傳回的記錄資料應符合在實驗室 1 中的 JD Edwards OneWorld 系統查詢所傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="1e196-361">This returned record data should match the data returned by the query against the JD Edwards OneWorld system in Lab 1.</span></span> <span data-ttu-id="1e196-362">藉由比較您在實驗室 1 中取得的記錄，您可以確認**取得**方法運作正常。</span><span class="sxs-lookup"><span data-stu-id="1e196-362">By comparing the records you obtained in Lab 1, you can verify that the **Get** method worked properly.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="1e196-363">摘要</span><span class="sxs-lookup"><span data-stu-id="1e196-363">Summary</span></span>  
 <span data-ttu-id="1e196-364">在此實驗室中，您先確認了必要條件已正確設定，以便存取 JD Edwards OneWorld 系統。</span><span class="sxs-lookup"><span data-stu-id="1e196-364">In this lab, you first verified that the prerequisites were set up correctly to access the JD Edwards OneWorld system.</span></span> <span data-ttu-id="1e196-365">之後，使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]來建立新的 BizTalk 專案包含協調流程。</span><span class="sxs-lookup"><span data-stu-id="1e196-365">Then you used [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to create a new BizTalk project containing an orchestration.</span></span> <span data-ttu-id="1e196-366">您會設定 BizTalk 協調流程，以使用 JD Edwards OneWorld 配接器自 JD Edwards OneWorld 系統取得資料。</span><span class="sxs-lookup"><span data-stu-id="1e196-366">You configured the BizTalk orchestration to use the JD Edwards OneWorld adapter to get data from the JD Edwards OneWorld system.</span></span> <span data-ttu-id="1e196-367">為了設定協調流程，您建立了傳送、接收與傳送/接收埠。</span><span class="sxs-lookup"><span data-stu-id="1e196-367">To configure the orchestration, you created send, receive, and send/receive ports.</span></span> <span data-ttu-id="1e196-368">您的 JD Edwards OneWorld 配接器中，受限於這些連接埠，並指派訊息到適當的連接埠。</span><span class="sxs-lookup"><span data-stu-id="1e196-368">You bound these ports to the JD Edwards OneWorld adapter, and assigned messages to the appropriate ports.</span></span>  
  
 <span data-ttu-id="1e196-369">完成 BizTalk 專案之後，您會使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]建置，並將它部署。</span><span class="sxs-lookup"><span data-stu-id="1e196-369">After you completed the BizTalk project, you used [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to build and deploy it.</span></span> <span data-ttu-id="1e196-370">然後，您會設定新的應用程式並加以執行，以從 JD Edwards OneWorld 系統取得資料。</span><span class="sxs-lookup"><span data-stu-id="1e196-370">You then configured your new application and ran it to get data from the JD Edwards OneWorld system.</span></span> <span data-ttu-id="1e196-371">為了確定應用程式正確運作，您將其輸出 XML 檔與實驗室 1 中自 JD Edwards OneWorld 系統中接收的檔案做比較。</span><span class="sxs-lookup"><span data-stu-id="1e196-371">To verify that the application worked correctly, you compared its output XML file to the file that you received from the JD Edwards OneWorld system in Lab 1.</span></span>