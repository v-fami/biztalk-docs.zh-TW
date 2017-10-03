---
title: "如何檢視 BizTalk 組件的相依性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing, dependencies
- assemblies, dependencies
- managing [assemblies], dependencies
- assemblies, viewing
- viewing, assemblies
- managing [assemblies], viewing
ms.assetid: 872abc99-8248-4397-9fcb-24a0ba6f4757
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99fbc09a5adb59691a4914a8ddc341c8034c8bb8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-view-the-dependencies-for-a-biztalk-assembly"></a><span data-ttu-id="80314-102">如何檢視 BizTalk 組件的相依性</span><span class="sxs-lookup"><span data-stu-id="80314-102">How to View the Dependencies for a BizTalk Assembly</span></span>
<span data-ttu-id="80314-103">本主題描述如何使用「BizTalk Server 管理」主控台來檢視相依於 BizTalk 組件的成品清單。</span><span class="sxs-lookup"><span data-stu-id="80314-103">This topic describes how to use the BizTalk Server Administration console to view the list of artifacts that have dependencies on a BizTalk assembly.</span></span> <span data-ttu-id="80314-104">如需相依性，以及它們如何影響應用程式部署的背景資訊，請參閱[相依性和應用程式部署](../core/dependencies-and-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="80314-104">For background information about dependencies and how they affect application deployment, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="80314-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="80314-105">Prerequisites</span></span>  
 <span data-ttu-id="80314-106">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組或「BizTalk 操作員」群組的成員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="80314-106">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group or BizTalk Operators group.</span></span> <span data-ttu-id="80314-107">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="80314-107">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-view-the-dependencies-of-a-biztalk-assembly"></a><span data-ttu-id="80314-108">檢視 BizTalk 組件的相依性</span><span class="sxs-lookup"><span data-stu-id="80314-108">To view the dependencies of a BizTalk assembly</span></span>  
  
1.  <span data-ttu-id="80314-109">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="80314-109">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="80314-110">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]展開包含您想要檢視相依性，此 BizTalk 組件的 BizTalk 群組，然後展開包含 BizTalk 組件的應用程式。</span><span class="sxs-lookup"><span data-stu-id="80314-110">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group containing the BizTalk assembly for which you want to view dependencies, and then expand the application containing the BizTalk assembly.</span></span>  
  
3.  <span data-ttu-id="80314-111">按一下**資源**資料夾中，以滑鼠右鍵按一下 BizTalk 組件，然後按一下**修改**。</span><span class="sxs-lookup"><span data-stu-id="80314-111">Click the **Resources** folder, right-click the BizTalk assembly, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="80314-112">按一下**相依性** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="80314-112">Click the **Dependencies** tab.</span></span>  
  
     <span data-ttu-id="80314-113">此清單中顯示相依於此 BizTalk 組件之成品的名稱和狀態。</span><span class="sxs-lookup"><span data-stu-id="80314-113">The name and status of the artifacts that have dependencies on this BizTalk assembly are displayed in the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80314-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80314-114">See Also</span></span>  
 [<span data-ttu-id="80314-115">管理 BizTalk 組件</span><span class="sxs-lookup"><span data-stu-id="80314-115">Managing BizTalk Assemblies</span></span>](../core/managing-biztalk-assemblies.md)