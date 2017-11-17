---
title: "如何部署新版應用程式與現有版本執行的並行 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1677c6a5-2c4c-4d70-ab83-f7e0bb3aaf6e
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 053145729546453b959dc35c7901932c1c8690c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-deploy-a-new-version-of-an-application-to-run-side-by-side-with-an-existing-version"></a><span data-ttu-id="4429c-102">如何部署應用程式的新版本，使其與現有版本並存執行。</span><span class="sxs-lookup"><span data-stu-id="4429c-102">How to Deploy a New Version of an Application to Run Side-by-side with an Existing Version</span></span>
<span data-ttu-id="4429c-103">如何部署將會執行由並行的應用程式的新版本與現有版本。</span><span class="sxs-lookup"><span data-stu-id="4429c-103">How to deploy a new version of an application that will run side-by-side with an existing version.</span></span> 

## <a name="overview"></a><span data-ttu-id="4429c-104">概觀</span><span class="sxs-lookup"><span data-stu-id="4429c-104">Overview</span></span>
<span data-ttu-id="4429c-105">您可能會想要這麼做，以累加方式展開主要應用程式升級；例如，開始時先讓一部分的商務夥伴使用，而不是一下子就提供給所有的夥伴使用。</span><span class="sxs-lookup"><span data-stu-id="4429c-105">You might want to do this to roll out a major application upgrade incrementally, for example making it available to a subset of business partners initially, rather than to all partners at once.</span></span> <span data-ttu-id="4429c-106">使用這種方式，可讓您繼續執行現有的應用程式來服務尚未使用新版本的使用者，直到您準備好完全轉入新版本為止。</span><span class="sxs-lookup"><span data-stu-id="4429c-106">Using this approach allows you to continue running the existing application to service the users who are not yet using the new version until you are ready to completely cut over to the new version.</span></span> <span data-ttu-id="4429c-107">如需此案例的背景資訊，請參閱[案例： 部署兩個版本的應用程式](../core/scenario-deploying-two-versions-of-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="4429c-107">For background information on this scenario, see [Scenario: Deploying Two Versions of an Application](../core/scenario-deploying-two-versions-of-an-application.md).</span></span>  
  
 <span data-ttu-id="4429c-108">與建立組件版本不同，您並非以遞增版本號碼的方式建立應用程式版本。</span><span class="sxs-lookup"><span data-stu-id="4429c-108">You do not create application versions in the same manner that you create assembly versions, by incrementing the version number.</span></span> <span data-ttu-id="4429c-109">而是建立名稱不同於原始應用程式的新應用程式，再以應用程式成品的新版本填入。</span><span class="sxs-lookup"><span data-stu-id="4429c-109">Instead, you create a new application that has a different name than the original application, and populate it with the new versions of the application artifacts.</span></span>  
  
 <span data-ttu-id="4429c-110">因為有許多類型的成品 (例如，組件) 只能存在於 BizTalk 群組中的一個應用程式，所以您必須遞增已存在於群組內之任何組件的版本號碼，才可以將它們部署到新的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="4429c-110">Because many types of artifacts, such as assemblies, can exist in only one application in a BizTalk group, you must increment the version number of any assemblies that already exist in the group before you can deploy them into the new application.</span></span> <span data-ttu-id="4429c-111">如需詳細資訊，請參閱[成品，必須是唯一的應用程式或群組](../core/artifacts-that-must-be-unique-in-an-application-or-group.md)。</span><span class="sxs-lookup"><span data-stu-id="4429c-111">For more information, see [Artifacts That Must Be Unique in an Application or Group](../core/artifacts-that-must-be-unique-in-an-application-or-group.md).</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="4429c-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="4429c-112">Prerequisites</span></span>  
<span data-ttu-id="4429c-113">使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。</span><span class="sxs-lookup"><span data-stu-id="4429c-113">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span> <span data-ttu-id="4429c-114">您的帳戶也必須具有本機檔案系統和全域組件快取的讀取/寫入權限。</span><span class="sxs-lookup"><span data-stu-id="4429c-114">Your account also must have Read/Write permission on the local file system, and the global assembly cache.</span></span> <span data-ttu-id="4429c-115">本機電腦上的「系統管理員」帳戶具有這項權限。</span><span class="sxs-lookup"><span data-stu-id="4429c-115">The Administrators account on the local computer has this permission.</span></span>  

<span data-ttu-id="4429c-116">如需詳細的權限的相關資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，和[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4429c-116">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).</span></span> 
  
## <a name="deploy-a-new-version-of-an-application"></a><span data-ttu-id="4429c-117">部署新版本的應用程式</span><span class="sxs-lookup"><span data-stu-id="4429c-117">Deploy a new version of an application</span></span>  
  
1.  <span data-ttu-id="4429c-118">在 Visual Studio 中，對您要部署到新版應用程式中的組件進行任何必要的變更</span><span class="sxs-lookup"><span data-stu-id="4429c-118">In Visual Studio, make any necessary changes to the assemblies that you want to deploy into the new version of the application</span></span>  
  
2.  <span data-ttu-id="4429c-119">依下列方式遞增每個組件的版本號碼：</span><span class="sxs-lookup"><span data-stu-id="4429c-119">Increment the version number of each assembly, as follows:</span></span>  
  
    1.  <span data-ttu-id="4429c-120">在 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案，然後**屬性**為專案啟動專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="4429c-120">In Solution Explorer, right-click the BizTalk project, and then click **Properties** to launch Project Designer for the project.</span></span>  
  
    2.  <span data-ttu-id="4429c-121">按一下**應用程式**如果不是使用中 索引標籤，然後按一下 **組件資訊** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4429c-121">Click the **Application** tab if it is not active, and then click **Assembly Information** button.</span></span>  
  
    3.  <span data-ttu-id="4429c-122">增加組件版本號碼，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="4429c-122">Increase the assembly version number, and then click **OK**.</span></span>  
  
    4.  <span data-ttu-id="4429c-123">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="4429c-123">Save the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4429c-124">請使用「管線設計師物件模型」，避免在遞增組件版本時發生結構描述衝突。</span><span class="sxs-lookup"><span data-stu-id="4429c-124">Use the Pipeline Designer Object Model to avoid schema collisions when incrementing assembly versions.</span></span>  
  
3.  <span data-ttu-id="4429c-125">在方案的每個專案的部署屬性中，執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="4429c-125">In deployment properties for each project in the solution, do the following:</span></span>  
  
    -   <span data-ttu-id="4429c-126">將應用程式名稱變更為新應用程式所要使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="4429c-126">Change the application name to the name you want to use for the new application.</span></span>  
  
    -   <span data-ttu-id="4429c-127">確定已選取會將組件安裝在全域組件快取 (GAC) 中的選項。</span><span class="sxs-lookup"><span data-stu-id="4429c-127">Ensure that the option to install the assemblies in the global assembly cache (GAC) is selected.</span></span>  
  
     <span data-ttu-id="4429c-128">如需指示，請參閱[如何在 Visual Studio 中設定部署屬性](../core/how-to-set-deployment-properties-in-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="4429c-128">For instructions, see [How to Set Deployment Properties in Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md).</span></span> <span data-ttu-id="4429c-129">當您部署方案時，組件將會部署到新的應用程式中，並且安裝在 GAC 內。</span><span class="sxs-lookup"><span data-stu-id="4429c-129">When you deploy the solution, the assemblies will be deployed into the new application and installed in the GAC.</span></span>  
  
4.  <span data-ttu-id="4429c-130">部署包含該組件的方案。</span><span class="sxs-lookup"><span data-stu-id="4429c-130">Deploy the solution(s) containing the assemblies.</span></span> <span data-ttu-id="4429c-131">如需指示，請參閱[如何部署 BizTalk 組件從 Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="4429c-131">For instructions, see [How to Deploy a BizTalk Assembly from Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md).</span></span>  
  
5.  <span data-ttu-id="4429c-132">指定您希望夥伴將訊息傳送到的新 URL，以建立新的接收埠和任何必要的接收位置。</span><span class="sxs-lookup"><span data-stu-id="4429c-132">Create a new receive port and any needed receive locations specifying the new URL(s) to which you want partners to send messages.</span></span> <span data-ttu-id="4429c-133">如需指示，請參閱[如何建立接收埠](../core/how-to-create-a-receive-port.md)。</span><span class="sxs-lookup"><span data-stu-id="4429c-133">For instructions, see [How to Create a Receive Port](../core/how-to-create-a-receive-port.md).</span></span> <span data-ttu-id="4429c-134">另請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="4429c-134">Also see [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).</span></span>  
  
6.  <span data-ttu-id="4429c-135">中所述，如有必要，建立適當的傳送埠[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。</span><span class="sxs-lookup"><span data-stu-id="4429c-135">Create the appropriate send ports as necessary, as described in [How to Create a Send Port](../core/how-to-create-a-send-port2.md).</span></span>  
  
7.  <span data-ttu-id="4429c-136">繫結至新建立新的應用程式接收和傳送埠中所述[如何設定應用程式](../core/how-to-configure-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="4429c-136">Bind the new application to the newly created receive and send ports, as described in [How to Configure an Application](../core/how-to-configure-an-application.md).</span></span>  
  
8.  <span data-ttu-id="4429c-137">中所述，從您的測試環境匯出至.msi 檔案的應用程式[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="4429c-137">Export the application into an .msi file from your test environment, as described in [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4429c-138">您可以使用下列步驟，對應用程式進行測試並將其部署到實際執行環境中。</span><span class="sxs-lookup"><span data-stu-id="4429c-138">You can use the following steps for testing the application as well as deploying it into your production environment.</span></span> <span data-ttu-id="4429c-139">如需開發、 測試、 預備及生產環境中的應用程式部署工作的詳細資訊，請參閱[應用程式部署工作](../core/application-deployment-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="4429c-139">For more information about application deployment tasks in development, test, staging, and production, see [Application Deployment Tasks](../core/application-deployment-tasks.md).</span></span>  
  
9. <span data-ttu-id="4429c-140">在實際執行環境中，BizTalk 群組應用程式.msi 檔案匯入中所述[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="4429c-140">Import the application .msi file into the BizTalk group in your production environment, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).</span></span> <span data-ttu-id="4429c-141">如果應用程式必須參考，您可以加入它們時使用 「 匯入 MSI 精靈 」，或更新版本中所述[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。</span><span class="sxs-lookup"><span data-stu-id="4429c-141">If the application requires references, you can add them while using the Import MSI Wizard, or later as described in [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).</span></span>  
  
10. <span data-ttu-id="4429c-142">將執行它，每個主控件執行個體上安裝新的應用程式中所述[如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="4429c-142">Install the new application on each host instance that will run it, as described in [How to Install a BizTalk Application](../core/how-to-install-a-biztalk-application.md).</span></span> <span data-ttu-id="4429c-143">確認是否已在每台裝載組件之電腦的 GAC 中安裝每個更新的組件。</span><span class="sxs-lookup"><span data-stu-id="4429c-143">Verify that each updated assembly has been installed in the GAC on each computer that hosts the assembly.</span></span> <span data-ttu-id="4429c-144">如有必要，將組件安裝在 gac、 中所述[如何在 GAC 中安裝組件](../core/how-to-install-an-assembly-in-the-gac.md)。</span><span class="sxs-lookup"><span data-stu-id="4429c-144">If necessary, install the assemblies in the GAC, as described in [How to Install an Assembly in the GAC](../core/how-to-install-an-assembly-in-the-gac.md).</span></span>  
  
11. <span data-ttu-id="4429c-145">執行完整啟動應用程式中所述[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="4429c-145">Perform a Full Start of the application, as described in [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).</span></span>  
  
12. <span data-ttu-id="4429c-146">通知您的夥伴開始傳送訊息至新的 URL。</span><span class="sxs-lookup"><span data-stu-id="4429c-146">Notify your partners that they should begin sending messages to the new URLS.</span></span> <span data-ttu-id="4429c-147">他們這麼做之後，應用程式便會開始處理指定夥伴的訊息。</span><span class="sxs-lookup"><span data-stu-id="4429c-147">Once they do this, the application begins processing messages for the specified partners.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4429c-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4429c-148">See Also</span></span>  
 [<span data-ttu-id="4429c-149">更新 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="4429c-149">Updating BizTalk Applications</span></span>](../core/updating-biztalk-applications.md)