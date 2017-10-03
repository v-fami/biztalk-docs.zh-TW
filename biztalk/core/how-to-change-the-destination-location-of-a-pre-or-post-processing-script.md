---
title: "如何變更前置或後置處理指令碼的目的地位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scripts, file locations
- scripts, modifying
- managing [scripts], modifying
- managing [scripts], file locations
ms.assetid: 4a4fdaef-099f-4c29-9815-12404c7a2212
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7eb4ba338790e301e54a9bf262a49808a0a55315
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-change-the-destination-location-of-a-pre--or-post-processing-script"></a><span data-ttu-id="ff147-102">如何變更前置或後置處理指令碼的目的地位置</span><span class="sxs-lookup"><span data-stu-id="ff147-102">How to Change the Destination Location of a Pre- or Post-processing Script</span></span>
<span data-ttu-id="ff147-103">本主題描述如何使用 [BizTalk Server 管理主控台] 來變更前置或後置處理指令碼的目的地位置。</span><span class="sxs-lookup"><span data-stu-id="ff147-103">This topic describes how to use the BizTalk Server Administration console to change the destination location of a pre- or post-processing script.</span></span> <span data-ttu-id="ff147-104">這是在安裝應用程式時便會將指令碼複製到其中的位置。</span><span class="sxs-lookup"><span data-stu-id="ff147-104">This is the location to which the script is copied when the application is installed.</span></span> <span data-ttu-id="ff147-105">在將應用程式部署到不同的環境時，您就可能需要變更目的地位置。</span><span class="sxs-lookup"><span data-stu-id="ff147-105">You might want to change the destination location when deploying an application into a different environment.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ff147-106">請確定為解除安裝應用程式時執行的指令碼提供目的地位置。</span><span class="sxs-lookup"><span data-stu-id="ff147-106">Be sure to provide a destination location for a script that will run when the application is uninstalled.</span></span> <span data-ttu-id="ff147-107">如果沒有提供位置，就不會將指令碼複製到本機檔案系統，因此不會在解除安裝時執行。</span><span class="sxs-lookup"><span data-stu-id="ff147-107">If you do not, the script will not be copied to the local file system, and therefore will not run during uninstallation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ff147-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="ff147-108">Prerequisites</span></span>  
 <span data-ttu-id="ff147-109">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="ff147-109">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="ff147-110">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="ff147-110">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-modify-the-deployment-properties-of-a-pre--or-post-processing-script"></a><span data-ttu-id="ff147-111">若要修改前置或後置處理指令碼的部署屬性</span><span class="sxs-lookup"><span data-stu-id="ff147-111">To modify the deployment properties of a pre- or post-processing script</span></span>  
  
1.  <span data-ttu-id="ff147-112">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="ff147-112">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="ff147-113">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，展開包含要修改的指令碼的 BizTalk 群組，然後再展開包含指令碼的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff147-113">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group containing the script to modify, and then expand the application containing the script.</span></span>  
  
3.  <span data-ttu-id="ff147-114">按一下**資源**資料夾中，指令碼，以滑鼠右鍵按一下，然後按一下**修改**。</span><span class="sxs-lookup"><span data-stu-id="ff147-114">Click the **Resources** folder, right-click the script, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="ff147-115">在**目的地位置**，輸入目的地位置，包括檔案名稱的完整路徑，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ff147-115">In **Destination location**, type the full path of the destination location, including the file name, and then click **OK**.</span></span> <span data-ttu-id="ff147-116">(您可以在路徑中使用 %BTAD_InstallDir% 環境變數來指定應用程式安裝資料夾)。</span><span class="sxs-lookup"><span data-stu-id="ff147-116">(You can use the environment variable %BTAD_InstallDir% in the path to specify the application installation folder.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff147-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff147-117">See Also</span></span>  
 [<span data-ttu-id="ff147-118">管理前置或後置處理指令碼</span><span class="sxs-lookup"><span data-stu-id="ff147-118">Managing Pre- and Post-processing Scripts</span></span>](../core/managing-pre-and-post-processing-scripts.md)