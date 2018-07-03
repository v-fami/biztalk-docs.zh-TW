---
title: 步驟 1： 準備 AS2 教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3421c33b-0ccd-4e9d-b1c3-b161278e4d98
caps.latest.revision: 39
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f394df645774752993064676345a371eb3135a0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003671"
---
# <a name="step-1-prepare-for-the-as2-tutorial"></a><span data-ttu-id="919e3-102">步驟 1： 準備 AS2 教學課程</span><span class="sxs-lookup"><span data-stu-id="919e3-102">Step 1: Prepare for the AS2 Tutorial</span></span>
<span data-ttu-id="919e3-103">![步驟 11-1](../core/media/tut-step1-of-11.gif "Tut_Step1_of_11")</span><span class="sxs-lookup"><span data-stu-id="919e3-103">![Step 1 of 11](../core/media/tut-step1-of-11.gif "Tut_Step1_of_11")</span></span>  
  
 <span data-ttu-id="919e3-104">AS2 教學課程可在單一電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="919e3-104">The AS2 tutorial is run on a single computer.</span></span> <span data-ttu-id="919e3-105">若要準備本教學課程，您必須安裝和設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中所述[BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)一節。</span><span class="sxs-lookup"><span data-stu-id="919e3-105">To prepare for the tutorial, you must install and configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] as described in [Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5) section.</span></span> <span data-ttu-id="919e3-106">您也必須依照本主題描述的方式新增對 BizTalk Server EDI 應用程式的參考。</span><span class="sxs-lookup"><span data-stu-id="919e3-106">You must also add a reference to the BizTalk Server EDI Application as described in this topic.</span></span> <span data-ttu-id="919e3-107">AS2 教學課程所需的檔案位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="919e3-107">The files required for the AS2 tutorial are located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial folder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="919e3-108">為了讓此教學課程順利運作，您必須同時針對內含式主控件執行個體和外掛式主控件執行個體使用相同的登入帳戶。</span><span class="sxs-lookup"><span data-stu-id="919e3-108">For this tutorial to work, you need to use the same logon account for both the in-process host instance and the isolated host instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="919e3-109">為進行此教學課程，此教學課程所用的 BizTalk Server 主控件必須標示為 32 位元。</span><span class="sxs-lookup"><span data-stu-id="919e3-109">For this tutorial to work, the BizTalk Server host that is used for this tutorial must be marked as 32-bit.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="919e3-110">此教學課程必須在 IIS 7.0 或 IIS 7.5 平台上執行，且應用程式集區的「啟用 32 位元應用程式」必須設定為 True。</span><span class="sxs-lookup"><span data-stu-id="919e3-110">For this tutorial to work, it must be run on a platform using IIS 7.0 or IIS 7.5, and the Enable 32-Bit Application Setting for the Application Pools must be set to True.</span></span>  
  
 <span data-ttu-id="919e3-111">AS2 教學課程的資料夾包括三個 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將在其中寫入測試輸出檔的資料夾 (EDI 內容、997 和 MDN)。</span><span class="sxs-lookup"><span data-stu-id="919e3-111">The AS2 tutorial folders include three folders that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will write test output files to (the EDI payload, 997, and MDN).</span></span> <span data-ttu-id="919e3-112">這些資料夾已經建立，但是您必須為 997 和 MDN 這兩個資料夾設定安全性權限 (請參閱下述程序)。</span><span class="sxs-lookup"><span data-stu-id="919e3-112">These folder have already been created, but you must set the security permissions for two of the 997 and MDN folders (see the procedure below).</span></span>  
  
 <span data-ttu-id="919e3-113">教學課程所需的資料夾和檔案如下：</span><span class="sxs-lookup"><span data-stu-id="919e3-113">The folders and files required for the tutorial are as follows:</span></span>  
  
|<span data-ttu-id="919e3-114">資料夾\檔案</span><span class="sxs-lookup"><span data-stu-id="919e3-114">Folder\File</span></span>|<span data-ttu-id="919e3-115">目的</span><span class="sxs-lookup"><span data-stu-id="919e3-115">Purpose</span></span>|  
|------------------|-------------|  
|<span data-ttu-id="919e3-116">\\_997ToFabrikam</span><span class="sxs-lookup"><span data-stu-id="919e3-116">\\_997ToFabrikam</span></span>|<span data-ttu-id="919e3-117">這個空資料夾將接收 EDI 處理之後傳回的 997 通知訊息。</span><span class="sxs-lookup"><span data-stu-id="919e3-117">This empty folder will receive the 997 acknowledgment message returned after EDI processing.</span></span> <span data-ttu-id="919e3-118">這個資料夾會模擬在 Fabrikam 合作對象中產生 EDI 訊息的應用程式。</span><span class="sxs-lookup"><span data-stu-id="919e3-118">The folder simulates the application originating the EDI message at the Fabrikam party.</span></span>|  
|<span data-ttu-id="919e3-119">\\_EDIXMLToContoso</span><span class="sxs-lookup"><span data-stu-id="919e3-119">\\_EDIXMLToContoso</span></span>|<span data-ttu-id="919e3-120">這個空資料夾將在 BizTalk Server 處理過 EDI 訊息之後接收 XML 內容檔。</span><span class="sxs-lookup"><span data-stu-id="919e3-120">This empty folder will receive the XML payload file after BizTalk Server has processed the EDI message.</span></span> <span data-ttu-id="919e3-121">這個資料夾會模擬商務營運應用程式，該應用程式為 EDI 內容的最終目的地。</span><span class="sxs-lookup"><span data-stu-id="919e3-121">This folder simulates the line-of-business application that is the final destination of the EDI payload.</span></span>|  
|<span data-ttu-id="919e3-122">\\_MDNToFabrikam</span><span class="sxs-lookup"><span data-stu-id="919e3-122">\\_MDNToFabrikam</span></span>|<span data-ttu-id="919e3-123">這個空資料夾將接收 AS2 處理之後自 BizTalk Server 傳回的 MDN 訊息。</span><span class="sxs-lookup"><span data-stu-id="919e3-123">This empty folder will receive the MDN message returned from BizTalk Server after AS2 processing.</span></span> <span data-ttu-id="919e3-124">這個資料夾會在 Fabrikam 合作對象中模擬應用程式。</span><span class="sxs-lookup"><span data-stu-id="919e3-124">The folder simulates an application at the Fabrikam party.</span></span>|  
|<span data-ttu-id="919e3-125">\Fabrikam</span><span class="sxs-lookup"><span data-stu-id="919e3-125">\Fabrikam</span></span>|<span data-ttu-id="919e3-126">這個資料夾包含 Default.aspx 檔，該檔案會將 997 儲存到 _997ToFabrikam 資料夾，以及將 MDN 儲存到 _MDNToFabrikam 資料夾。</span><span class="sxs-lookup"><span data-stu-id="919e3-126">This folder contains the Default.aspx file that saves the 997 into the _997ToFabrikam folder and saves the MDN into the _MDNToFabrikam folder.</span></span>|  
|<span data-ttu-id="919e3-127">\Schemas</span><span class="sxs-lookup"><span data-stu-id="919e3-127">\Schemas</span></span>|<span data-ttu-id="919e3-128">這個資料夾包含 X12_00401_864.xsd 結構描述，以及 BizTalk 用來處理 EDI 訊息的其他結構描述。</span><span class="sxs-lookup"><span data-stu-id="919e3-128">This folder contains the X12_00401_864.xsd schema and other schemas that BizTalk uses to process the EDI message.</span></span> <span data-ttu-id="919e3-129">這個資料夾還包含您將建置和部署的 Schemas.btproj 專案，以便用來部署結構描述。</span><span class="sxs-lookup"><span data-stu-id="919e3-129">The folder also contains the Schemas.btproj project that you will build and deploy in order to deploy the schemas.</span></span>|  
|<span data-ttu-id="919e3-130">\Sender</span><span class="sxs-lookup"><span data-stu-id="919e3-130">\Sender</span></span>|<span data-ttu-id="919e3-131">這個資料夾包含您將建置和編譯以建立 Sender.exe 的 Sender.csproj 專案，並且用來傳送 X12_00401_864.edi 測試訊息 (在 \AS2 Tutorial 資料夾中) 和傳回 MDN。</span><span class="sxs-lookup"><span data-stu-id="919e3-131">This folder contains the Sender.csproj project that you will build and compile to create Sender.exe, which you use to send the X12_00401_864.edi test message (in the \AS2 Tutorial folder) and to return the MDN.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="919e3-132">必要條件</span><span class="sxs-lookup"><span data-stu-id="919e3-132">Prerequisites</span></span>  
 <span data-ttu-id="919e3-133">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="919e3-133">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="919e3-134">程序</span><span class="sxs-lookup"><span data-stu-id="919e3-134">Procedures</span></span>  
  
#### <a name="to-set-the-security-permission-for-the-997-and-mdn-folders"></a><span data-ttu-id="919e3-135">設定 997 和 MDN 資料夾的安全性權限</span><span class="sxs-lookup"><span data-stu-id="919e3-135">To set the security permission for the 997 and MDN folders</span></span>  
  
1. <span data-ttu-id="919e3-136">在 Windows 檔案總管中，移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_997ToFabrikam 資料夾。</span><span class="sxs-lookup"><span data-stu-id="919e3-136">In Windows Explorer, move to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_997ToFabrikam folder.</span></span> <span data-ttu-id="919e3-137">以滑鼠右鍵按一下\\_997ToFabrikam 資料夾，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="919e3-137">Right-click the \\_997ToFabrikam folder, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="919e3-138">按一下 **安全性**索引標籤，然後再按一下**編輯**。</span><span class="sxs-lookup"><span data-stu-id="919e3-138">Click the **Security** tab, and then click **Edit**.</span></span> <span data-ttu-id="919e3-139">在 [**權限**] 對話方塊中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="919e3-139">In the **Permissions** dialog box, click **Add**.</span></span>  
  
3. <span data-ttu-id="919e3-140">在 **選取使用者、 電腦、 服務帳戶或群組**對話方塊中，在 物件名稱 窗格中，輸入`Everyone`，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="919e3-140">In the **Select Users, Computers, Service Accounts, or Groups** dialog box, in the object names pane, enter `Everyone`, and then click **OK**.</span></span>  
  
4. <span data-ttu-id="919e3-141">選取**Everyone**中**群組或使用者名稱**方塊中，按一下核取方塊**撰寫**(下**允許**資料行) 中的**權限**窗格中，然後再按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="919e3-141">Select **Everyone** in the **Group or user names** box, click the check box for **Write** (under the **Allow** column) in the **Permissions** pane, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="919e3-142">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="919e3-142">Click **OK**.</span></span>  
  
6. <span data-ttu-id="919e3-143">重複這些步驟\\_MDNToFabrikam 資料夾。</span><span class="sxs-lookup"><span data-stu-id="919e3-143">Repeat these steps for the \\_MDNToFabrikam folder.</span></span>  
  
#### <a name="to-mark-the-biztalk-server-host-as-32-bit"></a><span data-ttu-id="919e3-144">將 BizTalk Server 主控件標示為 32 位元</span><span class="sxs-lookup"><span data-stu-id="919e3-144">To mark the BizTalk Server Host as 32-Bit</span></span>  
  
1. > [!NOTE]
   >  <span data-ttu-id="919e3-145">AS2 管線只能用在 32 位元處理程序中。</span><span class="sxs-lookup"><span data-stu-id="919e3-145">The AS2 pipelines can only be used in a 32-bit process.</span></span> <span data-ttu-id="919e3-146">如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝在 64 位元的作業系統上，必須執行下列步驟以將主控件程序標示為僅限 32 位元。</span><span class="sxs-lookup"><span data-stu-id="919e3-146">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit operating system, the following steps must be performed to mark the host processes as 32-bit only.</span></span>  
  
    <span data-ttu-id="919e3-147">選取 **開始**，選取**所有程式**，選取**Microsoft BizTalk Server**，然後選取**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="919e3-147">Select **Start**, select **All Programs**, select **Microsoft BizTalk Server**, and then select **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="919e3-148">在主控台樹狀目錄中，依序展開**BizTalk Server 管理]**、 [BizTalk 群組中，選取**平台設定**，然後選取**主機**。</span><span class="sxs-lookup"><span data-stu-id="919e3-148">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, select **Platform Settings**, and then select **Hosts**.</span></span>  
  
3. <span data-ttu-id="919e3-149">在 [詳細資料] 窗格中，以滑鼠右鍵按一下您想要使用本教學課程，然後選取內含式主控件**屬性**。</span><span class="sxs-lookup"><span data-stu-id="919e3-149">In the details pane, right-click the in-process host you want to use for this tutorial and then select **Properties**.</span></span>  
  
4. <span data-ttu-id="919e3-150">中**主機內容**對話方塊的 **一般**索引標籤上，選取**僅 32 位元**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="919e3-150">In the **Host Properties** dialog box, on the **General** tab, select **32-bit only**, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="919e3-151">針對外掛式主控件重複步驟 3 到 4。</span><span class="sxs-lookup"><span data-stu-id="919e3-151">Repeat steps 3-4 for the isolated host.</span></span>  
  
   <span data-ttu-id="919e3-152">如果 BizTalk Server 安裝於 64 位元作業系統上，使用 32 位元的 BizTalk 主控件程序時，您也必須將 IIS 設定為以 32 位元模式執行。</span><span class="sxs-lookup"><span data-stu-id="919e3-152">If BizTalk Server is installed on a 64-bit operating system, you must also set IIS to run in 32-bit mode when using a 32-bit BizTalk host process.</span></span> <span data-ttu-id="919e3-153">設定 IIS 的指示會顯示內[步驟 5： 設定交易夥伴網頁](../core/step-5-configure-the-trading-partner-web-pages.md)IIS 可讓您設定上的 32 位元工作者處理序中，每個應用程式集區為基礎。</span><span class="sxs-lookup"><span data-stu-id="919e3-153">The instructions for setting IIS are presented within [Step 5: Configure the Trading Partner Web Pages](../core/step-5-configure-the-trading-partner-web-pages.md), as IIS allows you to set the 32-bit worker process on a per application pool basis.</span></span>  
  
#### <a name="to-add-reference-to-the-biztalk-edi-application"></a><span data-ttu-id="919e3-154">若要加入 BizTalk EDI 應用程式的參考</span><span class="sxs-lookup"><span data-stu-id="919e3-154">To add reference to the BizTalk EDI Application</span></span>  
  
1. <span data-ttu-id="919e3-155">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，底下**應用程式**] 節點，以滑鼠右鍵按一下您想要使用 edi，例如 [BizTalk Application 1 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="919e3-155">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the **Applications** node, right-click the application that you want to use for EDI, such as BizTalk Application 1.</span></span> <span data-ttu-id="919e3-156">指向**新增**，然後按一下 參考。</span><span class="sxs-lookup"><span data-stu-id="919e3-156">Point to **Add**, and then click References.</span></span>  
  
2. <span data-ttu-id="919e3-157">在 **新增應用程式參考**對話方塊中，選取**BizTalk EDI 應用程式**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="919e3-157">In the **Add Application Reference** dialog box, select **BizTalk EDI Application**, and then click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="919e3-158">後續步驟</span><span class="sxs-lookup"><span data-stu-id="919e3-158">Next Steps</span></span>  
 <span data-ttu-id="919e3-159">您將部署範例 X12 結構描述中所述[步驟 2： 建立和部署範例 X12 結構描述](../core/step-2-create-and-deploy-the-sample-x12-schema.md)</span><span class="sxs-lookup"><span data-stu-id="919e3-159">You deploy the sample X12 schema as described in [Step 2: Create and Deploy the Sample X12 Schema](../core/step-2-create-and-deploy-the-sample-x12-schema.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="919e3-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="919e3-160">See Also</span></span>  
 [<span data-ttu-id="919e3-161">教學課程 3: AS2 教學課程</span><span class="sxs-lookup"><span data-stu-id="919e3-161">Tutorial 3: AS2 Tutorial</span></span>](../core/tutorial-3-as2-tutorial.md)