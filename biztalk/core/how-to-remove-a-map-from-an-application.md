---
title: 如何從應用程式移除對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications, maps
- deleting, maps
- managing [maps], deleting
- managing [maps], applications
ms.assetid: 27d9bb08-36f0-46ff-ae9a-2247be6e3f96
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8863e95aabed933872edbe9a93146e59ad7480d6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000095"
---
# <a name="how-to-remove-a-map-from-an-application"></a><span data-ttu-id="edbdb-102">如何從應用程式移除對應</span><span class="sxs-lookup"><span data-stu-id="edbdb-102">How to Remove a Map from an Application</span></span>
<span data-ttu-id="edbdb-103">本主題描述如何使用 BizTalk Server 管理主控台，從 BizTalk 應用程式中移除對應。</span><span class="sxs-lookup"><span data-stu-id="edbdb-103">This topic describes how to use the BizTalk Server Administration console to remove a map from a BizTalk application.</span></span> <span data-ttu-id="edbdb-104">您可能會想要在部署新版本的對應之後移除對應。</span><span class="sxs-lookup"><span data-stu-id="edbdb-104">You might want to remove a map after deploying a new version of the map.</span></span> <span data-ttu-id="edbdb-105">如需詳細資訊和更新應用程式成品的重要考量，請參閱 <<c0> [ 更新 BizTalk 應用程式](../core/updating-biztalk-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="edbdb-105">For more information and important considerations for updating application artifacts, see [Updating BizTalk Applications](../core/updating-biztalk-applications.md).</span></span>  
  
 <span data-ttu-id="edbdb-106">移除對應時，會發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="edbdb-106">When you remove a map, the following occurs:</span></span>  
  
-   <span data-ttu-id="edbdb-107">對應會從 BizTalk 管理資料庫中刪除。</span><span class="sxs-lookup"><span data-stu-id="edbdb-107">The map is deleted from the BizTalk Management database.</span></span>  
  
-   <span data-ttu-id="edbdb-108">包含對應的 BizTalk 組件會從 BizTalk 管理資料庫中刪除，但是不會從本機檔案系統或全域組件快取 (GAC) 中移除 (如果存在於這些位置)。</span><span class="sxs-lookup"><span data-stu-id="edbdb-108">The BizTalk assembly that contains the map is deleted from the BizTalk Management database, but is not removed from the local file system or the global assembly cache (GAC), if it exists in these locations.</span></span>  
  
-   <span data-ttu-id="edbdb-109">由於會刪除 BizTalk 組件，所以包含在組件中的所有成品也會從 BizTalk 管理資料庫中移除。</span><span class="sxs-lookup"><span data-stu-id="edbdb-109">As a consequence of the BizTalk assembly being deleted, all artifacts contained in the assembly are removed deleted the BizTalk Management database as well.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="edbdb-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="edbdb-110">Prerequisites</span></span>  
 <span data-ttu-id="edbdb-111">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="edbdb-111">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="edbdb-112">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="edbdb-112">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-remove-a-map"></a><span data-ttu-id="edbdb-113">若要移除對應</span><span class="sxs-lookup"><span data-stu-id="edbdb-113">To remove a map</span></span>  
  
1. <span data-ttu-id="edbdb-114">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="edbdb-114">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="edbdb-115">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，依序展開 BizTalk 群組包含對應中移除，然後再展開 包含對應的應用程式。</span><span class="sxs-lookup"><span data-stu-id="edbdb-115">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the map to remove, and then expand the application containing the map.</span></span>  
  
3. <span data-ttu-id="edbdb-116">按一下  **Maps**資料夾中，以滑鼠右鍵按一下地圖上，然後**移除**。</span><span class="sxs-lookup"><span data-stu-id="edbdb-116">Click the **Maps** folder, right-click the map, and then click **Remove**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="edbdb-117">若要移除多個對應，請按住 shift 鍵，請按一下移除，以滑鼠右鍵按一下其中一個對應，然後按一下 每個對應**移除**。</span><span class="sxs-lookup"><span data-stu-id="edbdb-117">To remove multiple maps, hold down the shift key, click each map to remove, right-click one of the maps, and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edbdb-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edbdb-118">See Also</span></span>  
 <span data-ttu-id="edbdb-119">[管理對應](../core/managing-maps.md) </span><span class="sxs-lookup"><span data-stu-id="edbdb-119">[Managing Maps](../core/managing-maps.md) </span></span>  
 <span data-ttu-id="edbdb-120">[如何從應用程式移除 BizTalk 組件](../core/how-to-remove-a-biztalk-assembly-from-an-application.md) </span><span class="sxs-lookup"><span data-stu-id="edbdb-120">[How to Remove a BizTalk Assembly from an Application](../core/how-to-remove-a-biztalk-assembly-from-an-application.md) </span></span>  
 [<span data-ttu-id="edbdb-121">解除部署 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="edbdb-121">Undeploying BizTalk Applications</span></span>](../core/undeploying-biztalk-applications.md)