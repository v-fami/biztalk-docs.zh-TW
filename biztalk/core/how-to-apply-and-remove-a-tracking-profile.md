---
title: "如何套用和移除追蹤設定檔 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, tracking profiles
- tracking profiles, testing
- tracking profiles, deleting
- testing, tracking profiles
ms.assetid: 77cef14b-c390-4da7-a383-b3abe414a168
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 955b2ccddb215b79fd7cdc7d51ed6f5160c297fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-apply-and-remove-a-tracking-profile"></a><span data-ttu-id="4fc88-102">如何套用和移除追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="4fc88-102">How to Apply and Remove a Tracking Profile</span></span>
<span data-ttu-id="4fc88-103">在建立或修改追蹤設定檔之後，下一個步驟就是將它套用到測試資料庫，並透過整合測試驗證結果。</span><span class="sxs-lookup"><span data-stu-id="4fc88-103">Once you have created or modified the tracking profile, the next step is to apply it to a test database and verify the result through integration testing.</span></span> <span data-ttu-id="4fc88-104">您可從追蹤設定檔編輯器 (TPE) 本身或使用命令列套用追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="4fc88-104">You can apply the tracking profile from within Tracking Profile Editor (TPE) itself or by using the command line.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4fc88-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="4fc88-105">Prerequisites</span></span>  
 <span data-ttu-id="4fc88-106">您之前已建立並儲存到硬碟的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="4fc88-106">A previously created tracking profile that you saved to your hard drive.</span></span>  
  
### <a name="to-apply-the-tracking-profile-from-within-the-tpe"></a><span data-ttu-id="4fc88-107">從 TPE 套用追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="4fc88-107">To apply the tracking profile from within the TPE</span></span>  
  
1.  <span data-ttu-id="4fc88-108">按一下**啟動**，指向 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下 **追蹤設定檔編輯器**。</span><span class="sxs-lookup"><span data-stu-id="4fc88-108">Click **Start**, point to **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Tracking Profile Editor**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4fc88-109">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="4fc88-109">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="4fc88-110">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="4fc88-110">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="4fc88-111">在**檔案**功能表上，按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="4fc88-111">On the **File** menu, click **Open**.</span></span> <span data-ttu-id="4fc88-112">瀏覽至硬碟上正確的 .btt 檔。</span><span class="sxs-lookup"><span data-stu-id="4fc88-112">Navigate to the correct .btt file on your hard drive.</span></span> <span data-ttu-id="4fc88-113">按一下**開啟**載入它。</span><span class="sxs-lookup"><span data-stu-id="4fc88-113">Click **Open** to load it.</span></span>  
  
3.  <span data-ttu-id="4fc88-114">在**工具**功能表上，按一下 **套用追蹤設定檔**.btt 檔套用到您已經將設定管理資料庫**設定管理資料庫**上的功能表項目**工具**功能表。</span><span class="sxs-lookup"><span data-stu-id="4fc88-114">On the **Tools** menu, click **Apply Tracking Profile** to apply the .btt file to a management database that you have set from the **Set Management Database** menu item on the **Tools** menu.</span></span> <span data-ttu-id="4fc88-115">透過整合測試驗證結果。</span><span class="sxs-lookup"><span data-stu-id="4fc88-115">Verify the result through integration testing.</span></span>  
  
4.  <span data-ttu-id="4fc88-116">請通知您組織中負責部署的人員，追蹤設定檔測試正常並且已可供部署。</span><span class="sxs-lookup"><span data-stu-id="4fc88-116">Notify the person in your organization responsible for deployment that the tracking profile tests correctly and is ready for deployment.</span></span>  
  
### <a name="to-apply-the-tracking-profile-from-the-command-line"></a><span data-ttu-id="4fc88-117">從命令列套用追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="4fc88-117">To apply the tracking profile from the command line</span></span>  
  
-   <span data-ttu-id="4fc88-118">在命令提示字元中執行位於 \Tracking 資料夾中的 bttdeploy.exe 工具，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4fc88-118">From the command prompt, run the bttdeploy.exe tool located in the \Tracking folder as follows:</span></span>  
  
    ```  
    bttdeploy.exe <profile name>.btt  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="4fc88-119">您必須具有 BizTalk 系統管理員權限才可使用此工具。</span><span class="sxs-lookup"><span data-stu-id="4fc88-119">You must have BizTalk Administrator privileges to use this tool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4fc88-120">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="4fc88-120">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="4fc88-121">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="4fc88-121">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4fc88-122">在部署期間，bttdeploy 會驗證追蹤設定檔中所包含的組件版本，並與已部署之組件的版本進行比對。</span><span class="sxs-lookup"><span data-stu-id="4fc88-122">During the deployment, bttdeploy verifies the assembly version contained in the tracking profiles and matches it to the version of the deployed assembly.</span></span> <span data-ttu-id="4fc88-123">如果該組件目前尚未部署，bttdeploy 就會失敗。</span><span class="sxs-lookup"><span data-stu-id="4fc88-123">Bttdeploy will fail if the assembly is not currently deployed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4fc88-124">從命令列套用追蹤設定檔時，bttdeploy 會將設定檔套用到您在執行組態精靈時所指定的 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="4fc88-124">When applying a tracking profile from the command line, bttdeploy applies the profile to the BizTalk Management database that you indicated when you ran the configuration wizard.</span></span> <span data-ttu-id="4fc88-125">如果您在追蹤設定檔編輯器選項「設定管理資料庫」中指定不同的資料庫設定，則便會使用該設定。</span><span class="sxs-lookup"><span data-stu-id="4fc88-125">If you specify a different database setting in the Tracking Profile Editor Option "Set Management Database," then that setting is used.</span></span> <span data-ttu-id="4fc88-126">如果您指定管理伺服器和資料庫做為 bttdeploy 命令列選項的一部分，則該命令列選項會覆寫所有其他部分。</span><span class="sxs-lookup"><span data-stu-id="4fc88-126">If you specify a management server and database as part of the command line option to bttdeploy, then the command line option overrides everything else.</span></span> <span data-ttu-id="4fc88-127">如需使用 bttdeploy 的詳細資訊，請參閱[追蹤設定檔部署公用程式](../core/tracking-profile-deployment-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="4fc88-127">For more information about using bttdeploy, see [Tracking Profile Deployment Utility](../core/tracking-profile-deployment-utility.md).</span></span>  
  
### <a name="to-remove-a-tracking-profile"></a><span data-ttu-id="4fc88-128">移除追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="4fc88-128">To remove a tracking profile</span></span>  
  
1.  <span data-ttu-id="4fc88-129">按一下**啟動**，指向 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下 **追蹤設定檔編輯器**。</span><span class="sxs-lookup"><span data-stu-id="4fc88-129">Click **Start**, point to **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Tracking Profile Editor**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4fc88-130">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="4fc88-130">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="4fc88-131">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="4fc88-131">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="4fc88-132">在**檔案**功能表上，按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="4fc88-132">On the **File** menu, click **Open**.</span></span> <span data-ttu-id="4fc88-133">瀏覽至硬碟上正確的 .btt 檔。</span><span class="sxs-lookup"><span data-stu-id="4fc88-133">Navigate to the correct .btt file on your hard drive.</span></span> <span data-ttu-id="4fc88-134">按一下**開啟**載入它。</span><span class="sxs-lookup"><span data-stu-id="4fc88-134">Click **Open** to load it.</span></span>  
  
3.  <span data-ttu-id="4fc88-135">在**工具**功能表上，按一下 **移除追蹤設定檔**從 BizTalk 管理資料庫中的.btt 檔為基礎的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="4fc88-135">On the **Tools** menu, click **Remove Tracking Profile** to remove the tracking profile based on the .btt file from the BizTalk Management database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fc88-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fc88-136">See Also</span></span>  
 [<span data-ttu-id="4fc88-137">建立追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="4fc88-137">Creating Tracking Profiles</span></span>](../core/creating-tracking-profiles.md)