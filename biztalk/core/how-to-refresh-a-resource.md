---
title: 如何重新整理資源 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [resources], refreshing
- refreshing resources
- resources, refreshing
ms.assetid: d6ff7c9d-8aaf-42a4-b1a3-00c05f6ac869
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bee05b9f137bbec92eccfa217084b66f1e5bf8ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254542"
---
# <a name="how-to-refresh-a-resource"></a><span data-ttu-id="ed159-102">如何重新整理資源</span><span class="sxs-lookup"><span data-stu-id="ed159-102">How to Refresh a Resource</span></span>
<span data-ttu-id="ed159-103">本主題描述如何使用 BizTalk Server 管理主控台來重新整理資源成品。</span><span class="sxs-lookup"><span data-stu-id="ed159-103">This topic describes how to use the BizTalk Server Administration console to refresh a resource artifact.</span></span> <span data-ttu-id="ed159-104">此作業會更新 BizTalk 管理資料庫中的成品資訊。</span><span class="sxs-lookup"><span data-stu-id="ed159-104">This updates the artifact information in the BizTalk Management database.</span></span> <span data-ttu-id="ed159-105">若要這樣做的另一個方法是將成品新增至應用程式使用 BTSTask [AddResource 命令](../core/addresource-command.md)與覆寫選項。</span><span class="sxs-lookup"><span data-stu-id="ed159-105">Another way to do this is by adding the artifact to the application using the BTSTask [AddResource Command](../core/addresource-command.md) with the overwrite option.</span></span>  
  
 <span data-ttu-id="ed159-106">資源成品包含在應用程式的 [資源] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="ed159-106">Resource artifacts are contained in an application's Resources folder.</span></span> <span data-ttu-id="ed159-107">如果您變更了來源檔案，而且想要以更新過的檔案取代應用程式中的檔案，您可能需要重新整理資源成品。</span><span class="sxs-lookup"><span data-stu-id="ed159-107">You might want to refresh a resource artifact if you make changes to the source file and want to replace the file in the application with the updated file.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ed159-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="ed159-108">Prerequisites</span></span>  
 <span data-ttu-id="ed159-109">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="ed159-109">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="ed159-110">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="ed159-110">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-refresh-a-resource-artifact"></a><span data-ttu-id="ed159-111">若要重新整理資源成品</span><span class="sxs-lookup"><span data-stu-id="ed159-111">To refresh a resource artifact</span></span>  
  
1.  <span data-ttu-id="ed159-112">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="ed159-112">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="ed159-113">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組包含資源成品重新整理，然後展開包含該成品的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed159-113">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the resource artifact to refresh, and then expand the application containing the artifact.</span></span>  
  
3.  <span data-ttu-id="ed159-114">按一下**資源**資料夾、 以滑鼠右鍵按一下要重新整理檔案，然後按一下**修改**。</span><span class="sxs-lookup"><span data-stu-id="ed159-114">Click the **Resources** folder, right-click the file to refresh, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="ed159-115">在**修改資源**對話方塊、 選取要重新整理檔案，然後按一下**重新整理**。</span><span class="sxs-lookup"><span data-stu-id="ed159-115">In the **Modify Resources** dialog box, select the file to refresh, and then click **Refresh**.</span></span>  
  
5.  <span data-ttu-id="ed159-116">瀏覽至您要取代目前的檔案更新的檔案，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ed159-116">Browse to the updated file with which you want to replace the current file, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ed159-117">目前的檔案隨即取代成更新的檔案。</span><span class="sxs-lookup"><span data-stu-id="ed159-117">The current file is replaced with the updated file.</span></span> <span data-ttu-id="ed159-118">在加入、 設定、 設定顯示在**選項** 索引標籤**修改資源**對話方塊會套用到的重新整理的檔案。</span><span class="sxs-lookup"><span data-stu-id="ed159-118">In addition, the configuration, settings displayed on the **Options** tab of the **Modify Resources** dialog box are applied to the refreshed file.</span></span> <span data-ttu-id="ed159-119">如需有關如何變更這些設定的詳細資訊，請按一下**協助**在對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="ed159-119">For more information about changing these settings, click **Help** in the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed159-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed159-120">See Also</span></span>  
 <span data-ttu-id="ed159-121">[管理前置或後置處理指令碼](../core/managing-pre-and-post-processing-scripts.md) </span><span class="sxs-lookup"><span data-stu-id="ed159-121">[Managing Pre- and Post-processing Scripts](../core/managing-pre-and-post-processing-scripts.md) </span></span>  
 <span data-ttu-id="ed159-122">[管理.NET 組件、 憑證和其他資源](../core/managing-net-assemblies-certificates-and-other-resources.md) </span><span class="sxs-lookup"><span data-stu-id="ed159-122">[Managing .NET Assemblies, Certificates, and Other Resources](../core/managing-net-assemblies-certificates-and-other-resources.md) </span></span>  
 [<span data-ttu-id="ed159-123">管理資源</span><span class="sxs-lookup"><span data-stu-id="ed159-123">Managing Resources</span></span>](../core/managing-resources.md)