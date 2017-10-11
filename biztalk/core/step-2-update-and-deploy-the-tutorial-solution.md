---
title: "步驟 2： 更新和部署教學課程解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d03adfdd-1160-4e8c-a564-3acb2ecd0476
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca9f035eb97190c5a8999f73138d371e7dfddf98
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-update-and-deploy-the-tutorial-solution"></a><span data-ttu-id="48ad1-102">步驟 2： 更新和部署教學課程解決方案</span><span class="sxs-lookup"><span data-stu-id="48ad1-102">Step 2: Update and Deploy the Tutorial Solution</span></span>
<span data-ttu-id="48ad1-103">![步驟 2 的 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-2of9.gif "Step_2of9")</span><span class="sxs-lookup"><span data-stu-id="48ad1-103">![Step 2 of 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-2of9.gif "Step_2of9")</span></span>  
  
 <span data-ttu-id="48ad1-104">在這個步驟中，您會更新為本教學課程所提供的解決方案，然後建置並部署教學課程組件。</span><span class="sxs-lookup"><span data-stu-id="48ad1-104">In this step you update the solution provided for this tutorial, and then build and deploy the tutorial assembly.</span></span> <span data-ttu-id="48ad1-105">必要的結構描述、自訂傳送管線和對應，已因應本教學課程目的而完成建立。</span><span class="sxs-lookup"><span data-stu-id="48ad1-105">For the purposes of this tutorial, the necessary schema, custom send pipeline, and map have already been created.</span></span> <span data-ttu-id="48ad1-106">對應是用來將 850 EDI 資料轉換為「訂單系統」所需的格式。</span><span class="sxs-lookup"><span data-stu-id="48ad1-106">The map is used to convert the 850 EDI data into the format required by your Order System.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="48ad1-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="48ad1-107">Prerequisites</span></span>  
 <span data-ttu-id="48ad1-108">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="48ad1-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-enable-the-edi-inbound-processing-solution-to-be-built-in-visual-studio"></a><span data-ttu-id="48ad1-109">若要啟用在 Visual Studio 中建置 EDI 輸入處理解決方案</span><span class="sxs-lookup"><span data-stu-id="48ad1-109">To enable the EDI Inbound Processing solution to be built in Visual Studio</span></span>  
  
1.  <span data-ttu-id="48ad1-110">啟動**Microsoft Visual Studio**身為系統管理員。</span><span class="sxs-lookup"><span data-stu-id="48ad1-110">Start **Microsoft Visual Studio** as an administrator.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="48ad1-111">如果您未以系統管理員權限啟動 Visual Studio，則您將方案部署至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="48ad1-111">If you do not start Visual Studio with administrator privileges, you will get an error while deploying the solution to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="48ad1-112">在 Visual Studio 中，按一下 **檔案**，指向 **開啟**，然後按一下**專案/方案**。</span><span class="sxs-lookup"><span data-stu-id="48ad1-112">In Visual Studio, click **File**, point to **Open**, and then click **Project/Solution**.</span></span> <span data-ttu-id="48ad1-113">移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial，選取**EDI Inbound processing.sln**，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="48ad1-113">Move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial, select **EDI Inbound Processing.sln**, and then click **Open**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="48ad1-114">本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)，</span><span class="sxs-lookup"><span data-stu-id="48ad1-114">This topic assumes that you have already added a reference from your application to the BizTalk EDI Application, which contains EDI schemas, pipelines, and orchestrations.</span></span> <span data-ttu-id="48ad1-115">如果沒有，請參閱[如何將參考加入至 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。</span><span class="sxs-lookup"><span data-stu-id="48ad1-115">If not, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span></span>  
  
3.  <span data-ttu-id="48ad1-116">以滑鼠右鍵按一下**Inbound_EDI**專案在 [方案總管] 中，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="48ad1-116">Right-click the **Inbound_EDI** project in the Solution Explorer, and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="48ad1-117">在主控台樹狀目錄中的**Inbound_EDI 屬性頁面**對話方塊中，選取**部署**和**伺服器**欄位確保，輸入您的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="48ad1-117">In the console tree of the **Inbound_EDI Property Pages** dialog box, select  **Deployment** and in the **Server** field ensure that your computer name is entered.</span></span>  
  
5.  <span data-ttu-id="48ad1-118">在主控台樹狀目錄中，按一下**簽署**，然後選取 **簽署組件**。</span><span class="sxs-lookup"><span data-stu-id="48ad1-118">In the console tree, click **Signing** and then select **Sign the assembly**.</span></span> <span data-ttu-id="48ad1-119">如**選擇強式金鑰名稱檔**，選取\<**新增...**>，然後輸入**keyfile.snk**為**金鑰檔名稱**。</span><span class="sxs-lookup"><span data-stu-id="48ad1-119">For **Choose a strong key name file**, select \<**New…**> and enter  **keyfile.snk** as the **Key file name**.</span></span> <span data-ttu-id="48ad1-120">清除**保護我的密碼金鑰檔**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="48ad1-120">Clear **Protect my key file with a password** and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="48ad1-121">關閉**[Inbound_EDI 屬性頁面**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="48ad1-121">Close the **Inbound_EDI Property Pages** dialog box.</span></span>  
  
### <a name="to-deploy-the-project"></a><span data-ttu-id="48ad1-122">若要部署此專案</span><span class="sxs-lookup"><span data-stu-id="48ad1-122">To deploy the project</span></span>  
  
1.  <span data-ttu-id="48ad1-123">在 [方案總管] 中，按兩下**X12_00401_850.xsd**結構描述。</span><span class="sxs-lookup"><span data-stu-id="48ad1-123">In Solution Explorer, double-click the **X12_00401_850.xsd** schema.</span></span> <span data-ttu-id="48ad1-124">確認它已開啟。</span><span class="sxs-lookup"><span data-stu-id="48ad1-124">Confirm that it opens.</span></span>  
  
2.  <span data-ttu-id="48ad1-125">在 [方案總管] 中，按兩下**Inbound4010850_to_OrderFile.btm**對應。</span><span class="sxs-lookup"><span data-stu-id="48ad1-125">In Solution Explorer, double-click the **Inbound4010850_to_OrderFile.btm** map.</span></span> <span data-ttu-id="48ad1-126">確認它已開啟。</span><span class="sxs-lookup"><span data-stu-id="48ad1-126">Confirm that it opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="48ad1-127">專案中的 Inbound4010850_to_OrderFile.btm 對應會將輸入 850 測試訊息中的資料，對應到已傳遞到 OrderSystem 資料夾 (\toOrderSystem) 的輸出 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="48ad1-127">The Inbound4010850_to_OrderFile.btm map in the project maps the data in the inbound 850 test message to the outbound XML file delivered to the OrderSystem folder (\toOrderSystem).</span></span>  
  
3.  <span data-ttu-id="48ad1-128">在 [方案總管] 中，以滑鼠右鍵按一下**Inbound_EDI**專案，然後選取**建置**建置專案。</span><span class="sxs-lookup"><span data-stu-id="48ad1-128">In Solution Explorer, right-click the **Inbound_EDI** project and select **Build** to build the project.</span></span>  
  
4.  <span data-ttu-id="48ad1-129">在 [方案總管] 中，以滑鼠右鍵按一下**Inbound_EDI**專案，然後選取**部署**部署專案。</span><span class="sxs-lookup"><span data-stu-id="48ad1-129">In Solution Explorer, right-click the **Inbound_EDI** project and select **Deploy** to deploy the project.</span></span>  
  
5.  <span data-ttu-id="48ad1-130">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開  **BizTalk Server 管理**， **BizTalk 群組**，**應用程式**， \< **所有成品**>，然後選取 **資源**。</span><span class="sxs-lookup"><span data-stu-id="48ad1-130">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, \<**All Artifacts**> and then select **Resources**.</span></span> <span data-ttu-id="48ad1-131">確認**Inbound_EDI**有列出組件。</span><span class="sxs-lookup"><span data-stu-id="48ad1-131">Verify that the **Inbound_EDI** assembly is listed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="48ad1-132">後續步驟</span><span class="sxs-lookup"><span data-stu-id="48ad1-132">Next Steps</span></span>  
 <span data-ttu-id="48ad1-133">您為您的組織設定合作對象與商務設定檔 (**OrderSystem**) 中所述，[步驟 3： 設定適用於您組織的合作對象與商務設定檔](../core/step-3-configure-a-party-and-business-profile-for-your-organization1.md)</span><span class="sxs-lookup"><span data-stu-id="48ad1-133">You configure a party and business profile for your organization (**OrderSystem**), as described in [Step 3: Configure a Party and Business Profile for Your Organization](../core/step-3-configure-a-party-and-business-profile-for-your-organization1.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48ad1-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48ad1-134">See Also</span></span>  
 [<span data-ttu-id="48ad1-135">步驟 1： 準備 EDI 介面開發人員教學課程</span><span class="sxs-lookup"><span data-stu-id="48ad1-135">Step 1: Prepare for the EDI Interface Developer Tutorial</span></span>](../core/step-1-prepare-for-the-edi-interface-developer-tutorial.md)