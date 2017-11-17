---
title: "如何升級協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef3f032f-28a1-4d52-9d85-d5748c9e9682
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: edd9fa8e98b62ec92b1313cc1028efc5320ce17e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-upgrade-an-orchestration"></a><span data-ttu-id="a8ee2-102">如何升級協調流程</span><span class="sxs-lookup"><span data-stu-id="a8ee2-102">How to Upgrade an Orchestration</span></span>
<span data-ttu-id="a8ee2-103">如何更新協調流程處理長時間執行的交易或正在等候請求-回應連接埠的回應時，會將實際執行環境中執行的協調流程。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-103">How to update an orchestration that is running in a production environment when the orchestration handles long-running transactions or is waiting for a response from a solicit-response port.</span></span>

## <a name="overview"></a><span data-ttu-id="a8ee2-104">概觀</span><span class="sxs-lookup"><span data-stu-id="a8ee2-104">Overview</span></span>
 <span data-ttu-id="a8ee2-105">當協調流程不會處理長時間執行的交易時，您可以加以更新中所述[檢查清單： 更新 BizTalk 應用程式中的成品](../core/checklist-update-the-artifacts-in-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-105">When an orchestration does not handle long-running transactions, you can update it as described in [Checklist: Update the Artifacts in a BizTalk Application](../core/checklist-update-the-artifacts-in-a-biztalk-application.md).</span></span> <span data-ttu-id="a8ee2-106">不過，如果協調流程有處理長時間執行的交易，就無法立即切換到協調流程的更新版本。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-106">When an orchestration handles long-running transactions, however, you cannot cut over to the updated version of the orchestration immediately.</span></span> <span data-ttu-id="a8ee2-107">您必須讓原始的版本完成訊息的處理，以避免訊息遺失。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-107">You must allow the original version to finish processing its messages, so that they are not lost.</span></span> <span data-ttu-id="a8ee2-108">若要完成這項作業，您要將更新的協調流程部署到與原始版本相同的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-108">To accomplish this, you deploy the updated orchestration into the same application as the original one.</span></span> <span data-ttu-id="a8ee2-109">然後再停止原始的版本，並啟動更新版本使它可以接收所有新的訊息，而舊版本則持續處理任何已傳遞的訊息。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-109">You then stop the original version and start the updated version so that it receives all new messages while the previous version continues to process any in-flight messages.</span></span> <span data-ttu-id="a8ee2-110">在原始的協調流程完成所有其訊息的處理之後，請將它從部署所在的 BizTalk 應用程式中解除部署。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-110">After the original orchestration has finished processing all of its messages, you undeploy it from the BizTalk application in which it was deployed.</span></span>  
  
 <span data-ttu-id="a8ee2-111">如需有關此案例的詳細資訊，請參閱[案例： 更新應用程式成品](../core/scenario-updating-application-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-111">For more information about this scenario, see [Scenario: Updating Application Artifacts](../core/scenario-updating-application-artifacts.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a8ee2-112">如果有一個以上的協調流程繫結到相同的接收埠，而每個協調流程都已啟動或登錄，則您會在系統中導入重複的訊息。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-112">If more than one orchestration is bound to the same receive port, and each orchestration is started or enlisted, you will introduce duplicate messages into the system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8ee2-113">在升級到新的協調流程時，有些協調流程執行個體會在高壓力情況下而變成「已擱置 (可繼續)」，這是因為舊的協調流程與新的協調流程在升級過程中出現競爭而造成的。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-113">When upgrading to a new orchestration, some orchestration instances can become Suspended (resumable) under high stress because of the race condition between the old orchestration and the new orchestration during the upgrade.</span></span> <span data-ttu-id="a8ee2-114">若要手動繼續這些協調流程執行個體，請參閱[如何繼續已擱置協調流程執行個體](../core/how-to-resume-suspended-orchestration-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-114">To manually resume these orchestration instances, see [How to Resume Suspended Orchestration Instances](../core/how-to-resume-suspended-orchestration-instances.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a8ee2-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="a8ee2-115">Prerequisites</span></span>  
<span data-ttu-id="a8ee2-116">使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-116">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span> <span data-ttu-id="a8ee2-117">您的帳戶也必須具有本機檔案系統和全域組件快取的讀取/寫入權限。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-117">Your account also must have Read/Write permission on the local file system, and the global assembly cache.</span></span> <span data-ttu-id="a8ee2-118">本機電腦上的「系統管理員」帳戶具有這項權限。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-118">The Administrators account on the local computer has this permission.</span></span>  

<span data-ttu-id="a8ee2-119">如需詳細的權限的相關資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，和[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-119">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).</span></span> 
 
## <a name="update-an-orchestration"></a><span data-ttu-id="a8ee2-120">更新協調流程</span><span class="sxs-lookup"><span data-stu-id="a8ee2-120">Update an orchestration</span></span>  
  
1.  <span data-ttu-id="a8ee2-121">對協調流程進行必要的變更。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-121">Make the necessary changes to the orchestration.</span></span>  
  
2.  <span data-ttu-id="a8ee2-122">依下列方式遞增組件的版本號碼：</span><span class="sxs-lookup"><span data-stu-id="a8ee2-122">Increment the assembly version number, as follows:</span></span>  
  
    1.  <span data-ttu-id="a8ee2-123">在 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案，然後**屬性**啟動專案的專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-123">In Solution Explorer, right-click the BizTalk project, and then click **Properties** to launch the Project Designer for the project.</span></span>  
  
    2.  <span data-ttu-id="a8ee2-124">按一下**應用程式**如果還沒有使用中] 索引標籤，然後按一下 [**組件資訊**。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-124">Click the **Application** tab if it is not already active, and then click **Assembly Information**.</span></span>  
  
    3.  <span data-ttu-id="a8ee2-125">在右方窗格中增加組件的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-125">In the right pane, increase the assembly version number.</span></span> <span data-ttu-id="a8ee2-126">您只應該增加主要或次要的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-126">You should increase only the major or minor version number.</span></span> <span data-ttu-id="a8ee2-127">主要版本號碼是序列中的第一個數字 (**0**.0.0.0); 的次要版本號碼是序列中的第二位數 (0。**0**.0.0)。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-127">The major version number is the first digit in the sequence (**0**.0.0.0); the minor version number is the second digit in the sequence (0.**0**.0.0).</span></span> <span data-ttu-id="a8ee2-128">BizTalk Server 將無法辨識版本號碼變更為序列，例如 0.0 後面。**0**.0 或 0.0.0。**0**。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-128">BizTalk Server will not recognize a version number change that is later in the sequence, such as 0.0.**0**.0 or 0.0.0.**0**.</span></span>  
  
    4.  <span data-ttu-id="a8ee2-129">按一下**確定**關閉**組件資訊** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-129">Click **OK** to close the **Assembly Information** dialog box.</span></span>  
  
    5.  <span data-ttu-id="a8ee2-130">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-130">Save the project.</span></span>  
  
3.  <span data-ttu-id="a8ee2-131">從 Visual Studio 將組件部署到 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-131">Deploy the assembly from Visual Studio into a BizTalk application.</span></span> <span data-ttu-id="a8ee2-132">如需指示，請參閱[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-132">For instructions, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span></span> <span data-ttu-id="a8ee2-133">請確定您選取的部署選項會將組件部署在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-133">Make sure you select the deployment option to install the assembly in the GAC.</span></span>  
  
4.  <span data-ttu-id="a8ee2-134">測試包含協調流程的組件。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-134">Test the assembly containing the orchestration.</span></span>  
  
5.  <span data-ttu-id="a8ee2-135">匯出至.msi 檔案，您的測試環境中的應用程式的組件中所述[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-135">Export the assembly from the application in your test environment into an .msi file, as described in [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a8ee2-136">您可以使用下列步驟，對組件進行測試並將其部署到實際執行環境中。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-136">You can use the following steps for testing the assembly as well as deploying it into your production environment.</span></span> <span data-ttu-id="a8ee2-137">如需開發、 測試、 預備及生產環境中的應用程式部署工作的詳細資訊，請參閱[應用程式部署工作](../core/application-deployment-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-137">For more information about application deployment tasks in development, test, staging, and production, see [Application Deployment Tasks](../core/application-deployment-tasks.md).</span></span>  
  
6.  <span data-ttu-id="a8ee2-138">將.msi 檔案匯入實際執行環境，其中包含您想要更新中所述的協調流程的 BizTalk 應用程式[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-138">Import the .msi file into the BizTalk application in your production environment that contains the orchestration that you want to update, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).</span></span>  
  
7.  <span data-ttu-id="a8ee2-139">將更新與原始協調流程中，使用相同的繫結的協調流程的繫結中所述[如何設定協調流程繫結](../core/how-to-configure-bindings-for-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-139">Bind the updated orchestration using the same bindings as the original orchestration, as described in [How to Configure Bindings for an Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md).</span></span>  
  
8.  <span data-ttu-id="a8ee2-140">取消登錄原始的協調流程，然後啟動更新的協調流程。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-140">Unenlist the original orchestration, and then start the updated orchestration.</span></span> <span data-ttu-id="a8ee2-141">避免任何訊息遺失，您應該執行下列作業以程式設計方式中所述[部署和啟動新版本的協調流程以程式設計方式](../core/deploying-and-starting-a-new-version-of-an-orchestration-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-141">To avoid any dropped messages, you should do this programmatically, as described in [Deploying and Starting a New Version of an Orchestration Programmatically](../core/deploying-and-starting-a-new-version-of-an-orchestration-programmatically.md).</span></span> <span data-ttu-id="a8ee2-142">或者，您可以執行下列步驟手動中所述[如何取消登錄協調流程](../core/how-to-unenlist-an-orchestration.md)，[如何登錄協調流程](../core/how-to-enlist-an-orchestration.md)，和[如何啟動協調流程](../core/how-to-start-an-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="a8ee2-142">Alternatively, you can perform these steps manually, as described in [How to Unenlist an Orchestration](../core/how-to-unenlist-an-orchestration.md), [How to Enlist an Orchestration](../core/how-to-enlist-an-orchestration.md), and [How to Start an Orchestration](../core/how-to-start-an-orchestration.md).</span></span>  
  
9. <span data-ttu-id="a8ee2-143">監視系統中所述，使用 群組中樞的原始協調流程版本的執行個體頁面查詢檢視[如何檢視協調流程的執行個體資訊](../core/how-to-view-instance-information-for-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-143">Monitor the system for instances of the original orchestration version using the Group Hub page query view, as described in [How to View Instance Information for an Orchestration](../core/how-to-view-instance-information-for-an-orchestration.md).</span></span>  
  
10. <span data-ttu-id="a8ee2-144">所有其作用中、 凍結和擱置的執行個體完成時，解除部署應用程式，從原始的協調流程中所述[如何從應用程式移除協調流程](../core/how-to-remove-an-orchestration-from-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-144">When all of its active, dehydrated, and suspended instances are complete, undeploy the original orchestration from the application, as described in [How to Remove an Orchestration from an Application](../core/how-to-remove-an-orchestration-from-an-application.md).</span></span>  
  
11. <span data-ttu-id="a8ee2-145">選擇性地從解除安裝的原始組件版本上執行應用程式，每一部電腦的 GAC 中所述[如何從 GAC 解除安裝組件](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4)。</span><span class="sxs-lookup"><span data-stu-id="a8ee2-145">Optionally uninstall the original assembly version from the GAC on each computer running the application, as described in [How to Uninstall an Assembly from the GAC](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8ee2-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8ee2-146">See Also</span></span>  
 <span data-ttu-id="a8ee2-147">[更新 BizTalk 應用程式](../core/updating-biztalk-applications.md) </span><span class="sxs-lookup"><span data-stu-id="a8ee2-147">[Updating BizTalk Applications](../core/updating-biztalk-applications.md) </span></span>  
 [<span data-ttu-id="a8ee2-148">管理協調流程</span><span class="sxs-lookup"><span data-stu-id="a8ee2-148">Managing Orchestrations</span></span>](../core/managing-orchestrations.md)