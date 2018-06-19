---
title: 如何將伺服器新增至群組 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- groups, servers
- adding, servers
- managing [groups], adding servers
- servers, groups
- managing [servers], adding to groups
ms.assetid: 6eca1eeb-1a56-4470-b3bc-c64865cf6270
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5db5c7b760167f3e17d3ea82bf1023884b65e725
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247678"
---
# <a name="how-to-add-a-server-to-a-group"></a><span data-ttu-id="d37fb-102">如何將伺服器新增至群組</span><span class="sxs-lookup"><span data-stu-id="d37fb-102">How to Add a Server to a Group</span></span>
<span data-ttu-id="d37fb-103">您可以使用「BizTalk 伺服器組態」，將伺服器新增至 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="d37fb-103">You can use BizTalk Server Configuration to add a server to a BizTalk group.</span></span> <span data-ttu-id="d37fb-104">將額外的伺服器新增至 BizTalk 群組，可擴充您的 BizTalk Server 環境。</span><span class="sxs-lookup"><span data-stu-id="d37fb-104">You add additional servers to a BizTalk group to scale out your BizTalk Server environment.</span></span>  
  
 <span data-ttu-id="d37fb-105">一部伺服器僅能與一個 BizTalk 群組關聯。</span><span class="sxs-lookup"><span data-stu-id="d37fb-105">A server can only be associated with one BizTalk group.</span></span> <span data-ttu-id="d37fb-106">如果伺服器已經屬於其他群組，您必須先從目前的群組移除該伺服器，才可將其新增至新群組。</span><span class="sxs-lookup"><span data-stu-id="d37fb-106">If a server already belongs to another group, you must first remove that server from its current group before you can add it to a new group.</span></span> <span data-ttu-id="d37fb-107">從 BizTalk 群組移除伺服器的詳細資訊，請參閱[如何從群組移除伺服器](../core/how-to-remove-a-server-from-a-group.md)。</span><span class="sxs-lookup"><span data-stu-id="d37fb-107">For information about removing a server from a BizTalk group, see [How to Remove a Server from a Group](../core/how-to-remove-a-server-from-a-group.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d37fb-108">與 BizTalk Server 環境中不同伺服器建立關聯的 BizTalk 群組，除了交換訊息之外並不會互動。</span><span class="sxs-lookup"><span data-stu-id="d37fb-108">BizTalk groups associated with different servers in a BizTalk Server environment do not interact except to exchange messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d37fb-109">BizTalk Server 執行階段必須安裝在您想新增至 BizTalk 群組的電腦上。</span><span class="sxs-lookup"><span data-stu-id="d37fb-109">The BizTalk Server runtime must be installed on the computer you want to add to the BizTalk group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d37fb-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="d37fb-110">Prerequisites</span></span>  
 <span data-ttu-id="d37fb-111">若要執行此程序，您必須以「SSO 系統管理員」群組及「Windows 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="d37fb-111">To perform this procedure, you must be logged on as a member of the SSO Administrators group and as a member of the Windows Administrators group.</span></span>  
  
### <a name="to-add-a-server-to-a-biztalk-group"></a><span data-ttu-id="d37fb-112">將伺服器新增至 BizTalk 群組</span><span class="sxs-lookup"><span data-stu-id="d37fb-112">To add a server to a BizTalk group</span></span>  
  
1.  <span data-ttu-id="d37fb-113">您想要新增至 BizTalk Server 群組的電腦，按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 組態**.</span><span class="sxs-lookup"><span data-stu-id="d37fb-113">On the computer that you want to add to a BizTalk Server group to, click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.</span></span>  
  
2.  <span data-ttu-id="d37fb-114">在**Microsoft BizTalk Server 組態**，選取**自訂組態**。</span><span class="sxs-lookup"><span data-stu-id="d37fb-114">In **Microsoft BizTalk Server Configuration**, select **Custom configuration**.</span></span>  
  
3.  <span data-ttu-id="d37fb-115">在**資料庫伺服器名稱**，輸入伺服器正要 BizTalk 群組的 SQL Server 名稱。</span><span class="sxs-lookup"><span data-stu-id="d37fb-115">In **Database server name**, type the name of the SQL Server for the BizTalk Group the server is joining.</span></span>  
  
4.  <span data-ttu-id="d37fb-116">在**服務認證**，輸入適當的使用者名稱和密碼，服務會使用，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="d37fb-116">In **Service credential**, type the appropriate user name and password that the services will use, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="d37fb-117">在畫面左側的導覽樹狀目錄中，按一下 **企業單一登入**。</span><span class="sxs-lookup"><span data-stu-id="d37fb-117">In the navigation tree on the left side of the screen, click **Enterprise SSO**.</span></span>  
  
6.  <span data-ttu-id="d37fb-118">在**企業單一登入**頁面上，按一下**加入現有的 SSO 系統**。</span><span class="sxs-lookup"><span data-stu-id="d37fb-118">On the **Enterprise Single Sign-On** page, click **Join an existing SSO system**.</span></span>  
  
     <span data-ttu-id="d37fb-119">請確認伺服器名稱和資料庫名稱是指向伺服器正要連結之 BizTalk Server 群組的主要 SSO 資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="d37fb-119">Ensure that the server name and database name point to the master SSO database server for the BizTalk Server group the server is joining.</span></span>  
  
7.  <span data-ttu-id="d37fb-120">在畫面左側的導覽樹狀目錄中，按一下 **群組**。</span><span class="sxs-lookup"><span data-stu-id="d37fb-120">In the navigation tree on the left side of the screen, click **Group**.</span></span>  
  
8.  <span data-ttu-id="d37fb-121">在**群組**頁面上，按一下**加入現有的 BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="d37fb-121">On the **Group** page, click **Join an existing BizTalk Group**.</span></span>  
  
     <span data-ttu-id="d37fb-122">請確認伺服器名稱和資料庫名稱是指向伺服器正要連結之 BizTalk Server 群組的資料庫。</span><span class="sxs-lookup"><span data-stu-id="d37fb-122">Ensure that the server name and database name point to the databases for the BizTalk Server group the server is joining.</span></span>  
  
9. <span data-ttu-id="d37fb-123">在功能表列上，按一下 **套用組態**設定這部電腦上的企業單一登入和群組。</span><span class="sxs-lookup"><span data-stu-id="d37fb-123">On the menu bar, click **Apply Configuration** to configure both Enterprise Single Sign-On and the Group on this computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d37fb-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d37fb-124">See Also</span></span>  
 <span data-ttu-id="d37fb-125">[處理組態架構](../install-and-config-guides/working-with-the-configuration-framework.md) </span><span class="sxs-lookup"><span data-stu-id="d37fb-125">[Working with the Configuration Framework](../install-and-config-guides/working-with-the-configuration-framework.md) </span></span>  
 <span data-ttu-id="d37fb-126">[管理群組](../core/managing-groups.md) </span><span class="sxs-lookup"><span data-stu-id="d37fb-126">[Managing Groups](../core/managing-groups.md) </span></span>  
 <span data-ttu-id="d37fb-127">[BizTalk 群組](../core/biztalk-groups.md) </span><span class="sxs-lookup"><span data-stu-id="d37fb-127">[BizTalk Groups](../core/biztalk-groups.md) </span></span>  
 <span data-ttu-id="d37fb-128">[如何將伺服器從一個群組移至另一個](../core/how-to-move-a-server-from-one-group-to-another.md) </span><span class="sxs-lookup"><span data-stu-id="d37fb-128">[How to Move a Server from One Group to Another](../core/how-to-move-a-server-from-one-group-to-another.md) </span></span>  
 <span data-ttu-id="d37fb-129">[如何從群組移除伺服器](../core/how-to-remove-a-server-from-a-group.md) </span><span class="sxs-lookup"><span data-stu-id="d37fb-129">[How to Remove a Server from a Group](../core/how-to-remove-a-server-from-a-group.md) </span></span>  
 <span data-ttu-id="d37fb-130">[如何修改群組屬性](../core/how-to-modify-group-properties.md) </span><span class="sxs-lookup"><span data-stu-id="d37fb-130">[How to Modify Group Properties](../core/how-to-modify-group-properties.md) </span></span>  
 [<span data-ttu-id="d37fb-131">管理伺服器</span><span class="sxs-lookup"><span data-stu-id="d37fb-131">Managing Servers</span></span>](../core/managing-servers.md)