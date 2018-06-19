---
title: 如何修改 BizTalk 組件的部署選項 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- modifying, deploying
- managing [assemblies], modifying
- deploying, assemblies
- managing [assemblies], deploying
- assemblies, deploying
ms.assetid: d25e2f71-08bd-4786-ab6c-35ae4e88b8cc
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58365383b1981ae40e87ee23891929bf05c8530e
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26007751"
---
# <a name="how-to-modify-the-deployment-options-of-a-biztalk-assembly"></a><span data-ttu-id="73154-102">如何修改 BizTalk 組件的部署選項</span><span class="sxs-lookup"><span data-stu-id="73154-102">How to Modify the Deployment Options of a BizTalk Assembly</span></span>
<span data-ttu-id="73154-103">本主題描述如何使用 BizTalk Server 管理主控台來修改 BizTalk 組件的部署選項。</span><span class="sxs-lookup"><span data-stu-id="73154-103">This topic describes how to use the BizTalk Server Administration console to modify the deployment options of a BizTalk assembly.</span></span>  
  
 <span data-ttu-id="73154-104">您可以指定下列部署選項：</span><span class="sxs-lookup"><span data-stu-id="73154-104">You can specify the following deployment options:</span></span>  
  
-   <span data-ttu-id="73154-105">**新增至全域組件快取新增資源 (gacutil) 上。**</span><span class="sxs-lookup"><span data-stu-id="73154-105">**Add to the global assembly cache on add resource (gacutil).**</span></span> <span data-ttu-id="73154-106">如果選取此選項，將組件新增至應用程式時，便會將組件新增至本機電腦上的全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="73154-106">When you select this option, the assembly is added to the global assembly cache (GAC) on the local computer when the assembly is added to the application.</span></span> <span data-ttu-id="73154-107">此外，如果您稍後重新整理組件 (以滑鼠右鍵按一下它，然後按一下**重新整理**)，組件加入至 GAC。</span><span class="sxs-lookup"><span data-stu-id="73154-107">In addition, if you later refresh the assembly (right-click it and click **Refresh**), the assembly is added to the GAC.</span></span> <span data-ttu-id="73154-108">清除這個選項的核取方塊並不會從 GAC 移除該組件 (如果該組件目前在 GAC 中)。</span><span class="sxs-lookup"><span data-stu-id="73154-108">Clearing the check box for this option does not remove the assembly from the GAC, if it currently exists there.</span></span>  
  
-   <span data-ttu-id="73154-109">**新增至 MSI 檔案匯入 (gacutil) 的全域組件快取。**</span><span class="sxs-lookup"><span data-stu-id="73154-109">**Add to the global assembly cache on MSI file import (gacutil).**</span></span> <span data-ttu-id="73154-110">在匯入應用程式 .msi 檔案時，將組件安裝到本機電腦的 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="73154-110">Install the assembly to the GAC on the local computer when the application .msi file is imported.</span></span>  
  
-   <span data-ttu-id="73154-111">**新增至 MSI 檔案安裝 (gacutil) 的全域組件快取。**</span><span class="sxs-lookup"><span data-stu-id="73154-111">**Add to the global assembly cache on MSI file install (gacutil).**</span></span> <span data-ttu-id="73154-112">從 .msi 匯入應用程式時，將組件安裝到本機電腦的 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="73154-112">Install the assembly to the GAC on the local computer when the application is installed from the .msi file.</span></span>  
  
-   <span data-ttu-id="73154-113">**目的地位置：** 複製到其中的組件檔會在安裝應用程式的路徑。</span><span class="sxs-lookup"><span data-stu-id="73154-113">**Destination location:** Path to which the assembly file will be copied when the application is installed.</span></span> <span data-ttu-id="73154-114">如果沒有提供路徑，安裝時就不會將組件檔案複製到本機檔案系統。</span><span class="sxs-lookup"><span data-stu-id="73154-114">If a path is not provided, the assembly file is not copied to the local file system on installation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="73154-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="73154-115">Prerequisites</span></span>  
 <span data-ttu-id="73154-116">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="73154-116">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="73154-117">此外，如果您選取立即將組件新增至 GAC 的選項，您的帳戶也必須是本機「系統管理員」群組的成員。</span><span class="sxs-lookup"><span data-stu-id="73154-117">In addition, if you select an option that immediately adds the assembly to the GAC, your account must also be a member of the local Administrator's group.</span></span> <span data-ttu-id="73154-118">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="73154-118">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-modify-the-deployment-options-of-a-biztalk-assembly"></a><span data-ttu-id="73154-119">若要修改 BizTalk 組件的部署選項</span><span class="sxs-lookup"><span data-stu-id="73154-119">To modify the deployment options of a BizTalk assembly</span></span>  
  
1.  <span data-ttu-id="73154-120">按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="73154-120">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="73154-121">在主控台樹狀目錄中，展開 [BizTalk Server 管理]，展開包含要為其修改部署選項的 BizTalk 組件的 BizTalk 群組，然後展開包含 BizTalk 組件的應用程式。</span><span class="sxs-lookup"><span data-stu-id="73154-121">In the console tree, expand BizTalk Server Administration, expand the BizTalk group containing the BizTalk assembly for which to modify deployment options, and then expand the application containing the BizTalk assembly.</span></span>  
  
3.  <span data-ttu-id="73154-122">按一下**資源**資料夾中，以滑鼠右鍵按一下 BizTalk 組件，然後按一下**修改**。</span><span class="sxs-lookup"><span data-stu-id="73154-122">Click the **Resources** folder, right-click the BizTalk assembly, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="73154-123">在**選項**，選取您想要的部署選項的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="73154-123">In **Options**, select the check boxes of the deployment options that you want.</span></span>  
  
5.  <span data-ttu-id="73154-124">必要時，在**目的地位置**編輯的路徑的組件安裝應用程式時，會複製，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="73154-124">If necessary, in **Destination location** edit the path where the assembly will be copied when the application is installed, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73154-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="73154-125">See Also</span></span>  
 [<span data-ttu-id="73154-126">管理 BizTalk 組件</span><span class="sxs-lookup"><span data-stu-id="73154-126">Managing BizTalk Assemblies</span></span>](../core/managing-biztalk-assemblies.md)