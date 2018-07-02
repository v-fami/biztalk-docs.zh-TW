---
title: 如何登錄或取消登錄角色的合作對象 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [role links], enlisting
- enlisting, role links
- role links, unenlisting
- role links, enlisting
- managing [role links], unenlisting
ms.assetid: 06fc2a64-3add-400c-9f9d-fab22fdf5366
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 046e51424427973534d9e4defdbf6e8d58eb8b2f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966247"
---
# <a name="how-to-enlist-or-unenlist-a-party-for-a-role"></a><span data-ttu-id="1ba89-102">如何登錄或取消登錄角色的合作對象</span><span class="sxs-lookup"><span data-stu-id="1ba89-102">How to Enlist or Unenlist a Party for a Role</span></span>
<span data-ttu-id="1ba89-103">本主題描述如何使用 BizTalk Server 管理主控台來登錄或取消登錄角色的合作對象。</span><span class="sxs-lookup"><span data-stu-id="1ba89-103">This topic describes how to use the BizTalk Server Administration console to enlist or unenlist a party for a role.</span></span> <span data-ttu-id="1ba89-104">登錄角色的合作對象會將合作對象指派給角色，而取消登錄合作對象則會將合作對象從角色中移除。</span><span class="sxs-lookup"><span data-stu-id="1ba89-104">Enlisting a party for a role assigns the party to the role and unenlisting the party removes the party from the role.</span></span>  
  
 <span data-ttu-id="1ba89-105">當登錄或取消登錄角色的合作對象時，請記住下列重點：</span><span class="sxs-lookup"><span data-stu-id="1ba89-105">When enlisting or unenlisting a party for a role, bear in mind the following points:</span></span>  
  
-   <span data-ttu-id="1ba89-106">您必須先建立合作對象，才可以將它登錄。</span><span class="sxs-lookup"><span data-stu-id="1ba89-106">You must create a party before you can enlist it.</span></span> <span data-ttu-id="1ba89-107">如需相關指示，請參閱 <<c0> [ 如何建立合作對象](http://msdn.microsoft.com/library/f6feca1d-bc83-4fb6-981d-26c9e0d53044)。</span><span class="sxs-lookup"><span data-stu-id="1ba89-107">For instructions, see [How to Create a Party](http://msdn.microsoft.com/library/f6feca1d-bc83-4fb6-981d-26c9e0d53044).</span></span>  
  
-   <span data-ttu-id="1ba89-108">您可以登錄或取消登錄角色的合作對象，而不需重新啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ba89-108">You can enlist or unenlist a party for a role without needing to restart the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ba89-109">應用程式開發人員可以使用此主題中的程序，在開發程序中登錄或取消登錄合作對象。</span><span class="sxs-lookup"><span data-stu-id="1ba89-109">The application developer can enlist or unenlist a party during the development process by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1ba89-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="1ba89-110">Prerequisites</span></span>  
 <span data-ttu-id="1ba89-111">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="1ba89-111">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="1ba89-112">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="1ba89-112">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-enlist-or-unenlist-a-party-for-a-role"></a><span data-ttu-id="1ba89-113">登錄或取消登錄角色的合作對象</span><span class="sxs-lookup"><span data-stu-id="1ba89-113">To enlist or unenlist a party for a role</span></span>  
  
1. <span data-ttu-id="1ba89-114">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="1ba89-114">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="1ba89-115">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，展開**應用程式**，然後展開包含您要登錄的角色連結的應用程式或取消登錄合作對象。</span><span class="sxs-lookup"><span data-stu-id="1ba89-115">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the role link for which you want to enlist or unenlist a party.</span></span>  
  
3. <span data-ttu-id="1ba89-116">按一下 **角色連結**，以滑鼠右鍵按一下您要登錄或取消登錄合作對象，並按一下 角色連結**屬性**。</span><span class="sxs-lookup"><span data-stu-id="1ba89-116">Click **Role Links**, right-click the role link for which you want to enlist or unenlist a party, and then click **Properties**.</span></span>  
  
4. <span data-ttu-id="1ba89-117">若要登錄合作對象，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="1ba89-117">To enlist a party, do the following:</span></span>  
  
   -   <span data-ttu-id="1ba89-118">按一下 **登錄**按一下要登錄的合作對象。</span><span class="sxs-lookup"><span data-stu-id="1ba89-118">Click **Enlist** and click the party to enlist.</span></span>  
  
   -   <span data-ttu-id="1ba89-119">按一下 **繫結**，請在**傳送連接埠**下拉式清單中，按一下傳送連接埠連接到用於此合作對象，然後按一下 **確定**兩次。</span><span class="sxs-lookup"><span data-stu-id="1ba89-119">Click **Bind**, in the **Send Port** drop-down list, click the send port to use for this party, and then click **OK** twice.</span></span>  
  
5. <span data-ttu-id="1ba89-120">要取消登錄合作對象，按一下 合作對象、 按一下**取消登錄**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="1ba89-120">To unenlist a party, click the party, click **Unenlist**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ba89-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ba89-121">See Also</span></span>  
 [<span data-ttu-id="1ba89-122">管理角色連結</span><span class="sxs-lookup"><span data-stu-id="1ba89-122">Managing Role Links</span></span>](../core/managing-role-links.md)