---
title: "如何將伺服器從一個群組移至另一個 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- groups, servers
- groups, moving
- managing [groups], moving servers
- servers, moving
- managing [servers], moving
- servers, groups
ms.assetid: 3f789a62-f597-426b-9cea-74c1fe22b694
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c9e5dfdf266d2205283afa7cd9804c31fc93ff3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-a-server-from-one-group-to-another"></a><span data-ttu-id="fe1ee-102">如何將伺服器從一個群組移至另一個群組</span><span class="sxs-lookup"><span data-stu-id="fe1ee-102">How to Move a Server from One Group to Another</span></span>
<span data-ttu-id="fe1ee-103">一部伺服器僅能與一個 BizTalk Server 群組關聯。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-103">A server can only be associated with one BizTalk Server group.</span></span> <span data-ttu-id="fe1ee-104">若要將伺服器從一個群組移至另一個群組，必須先取消設定此伺服器，從原始群組移除它，然後將它加入新群組中。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-104">To move a server from one group to another, you must first remove the server from the original group by unconfiguring it, and then add the server to the new group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fe1ee-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="fe1ee-105">Prerequisites</span></span>  
 <span data-ttu-id="fe1ee-106">若要執行此程序，您必須以「SSO 系統管理員」群組及「Windows 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-106">To perform this procedure, you must be logged on as a member of the SSO Administrators group and as a member of the Windows Administrators group.</span></span>  
  
### <a name="to-move-a-server-from-one-biztalk-group-to-another"></a><span data-ttu-id="fe1ee-107">將伺服器從一個 BizTalk 群組移至另一個群組</span><span class="sxs-lookup"><span data-stu-id="fe1ee-107">To move a server from one BizTalk group to another</span></span>  
  
1.  <span data-ttu-id="fe1ee-108">按一下您想要從 BizTalk 群組移至另一部電腦上**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 組態**.</span><span class="sxs-lookup"><span data-stu-id="fe1ee-108">On the computer that you want to move from the BizTalk group to another, click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.</span></span>  
  
2.  <span data-ttu-id="fe1ee-109">在功能表列上，按一下 **取消設定功能**。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-109">On the menu bar, click **Unconfigure Features**.</span></span>  
  
3.  <span data-ttu-id="fe1ee-110">在**取消設定功能**對話方塊中，選取**企業單一登入**，選取**群組**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-110">In the **Unconfigure Features** dialog box, select **Enterprise SSO**, select **Group**, and then click **OK**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="fe1ee-111">取消設定群組也會將該電腦上設定的所有相關功能取消設定。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-111">Unconfiguring a group will also unconfigure all dependent features that are already configured on that computer.</span></span>  
  
4.  <span data-ttu-id="fe1ee-112">按一下 **[是]**。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-112">Click **Yes**.</span></span>  
  
5.  <span data-ttu-id="fe1ee-113">在**Microsoft BizTalk Server 組態**視窗中，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-113">In the **Microsoft BizTalk Server Configuration** window, click **Next**.</span></span>  
  
     <span data-ttu-id="fe1ee-114">會取消設定企業 SSO、群組以及它們相依的功能。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-114">Enterprise SSO, the Group, and their dependent features are unconfigured.</span></span>  
  
6.  <span data-ttu-id="fe1ee-115">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-115">Click **Finish**.</span></span>  
  
7.  <span data-ttu-id="fe1ee-116">在**Microsoft BizTalk Server 組態**視窗中，選取**自訂組態**。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-116">In the **Microsoft BizTalk Server Configuration** window, select **Custom configuration**.</span></span>  
  
8.  <span data-ttu-id="fe1ee-117">在**資料庫伺服器名稱**，輸入您要移動伺服器之 BizTalk 群組的 SQL server 名稱。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-117">In **Database server name**, type the name of the SQL server for the BizTalk Group where you are moving the server.</span></span>  
  
9. <span data-ttu-id="fe1ee-118">在**服務認證**，輸入適當的使用者名稱和密碼，服務會使用，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-118">In **Service credential**, type the appropriate user name and password that the services will use, and then click **Configure**.</span></span>  
  
10. <span data-ttu-id="fe1ee-119">在畫面左側的導覽樹狀目錄中，按一下 **企業單一登入**。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-119">In the navigation tree on the left side of the screen, click **Enterprise SSO**.</span></span>  
  
11. <span data-ttu-id="fe1ee-120">在**企業單一登入**頁面上，按一下**加入現有的 SSO 系統**。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-120">On the **Enterprise Single Sign-On** page, click **Join an existing SSO system**.</span></span>  
  
     <span data-ttu-id="fe1ee-121">請確認伺服器名稱和資料庫名稱是指向您要移動伺服器之 BizTalk Server 群組的主要 SSO 資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-121">Ensure that the server name and database name point to the master SSO database server for the BizTalk Server group where you are moving the server.</span></span>  
  
12. <span data-ttu-id="fe1ee-122">在畫面左側的導覽樹狀目錄中，按一下 **群組**。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-122">In the navigation tree on the left side of the screen, click **Group**.</span></span>  
  
13. <span data-ttu-id="fe1ee-123">在**群組**頁面上，按一下**加入現有的 BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-123">On the **Group** page, click **Join an existing BizTalk Group**.</span></span>  
  
     <span data-ttu-id="fe1ee-124">請確認伺服器名稱和資料庫名稱是指向您要移動伺服器之 BizTalk Server 群組的資料庫。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-124">Ensure that the server name and database name point to the databases for the BizTalk Server group where you are moving the server.</span></span>  
  
14. <span data-ttu-id="fe1ee-125">在功能表列上，按一下 **套用組態**設定這部電腦上的企業單一登入和群組。</span><span class="sxs-lookup"><span data-stu-id="fe1ee-125">On the menu bar, click **Apply Configuration** to configure both Enterprise Single Sign-On and the Group on this computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe1ee-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe1ee-126">See Also</span></span>  
 <span data-ttu-id="fe1ee-127">[管理群組](../core/managing-groups.md) </span><span class="sxs-lookup"><span data-stu-id="fe1ee-127">[Managing Groups](../core/managing-groups.md) </span></span>  
 <span data-ttu-id="fe1ee-128">[BizTalk 群組](../core/biztalk-groups.md) </span><span class="sxs-lookup"><span data-stu-id="fe1ee-128">[BizTalk Groups](../core/biztalk-groups.md) </span></span>  
 <span data-ttu-id="fe1ee-129">[如何將伺服器新增至群組](../core/how-to-add-a-server-to-a-group.md) </span><span class="sxs-lookup"><span data-stu-id="fe1ee-129">[How to Add a Server to a Group](../core/how-to-add-a-server-to-a-group.md) </span></span>  
 <span data-ttu-id="fe1ee-130">[如何從群組移除伺服器](../core/how-to-remove-a-server-from-a-group.md) </span><span class="sxs-lookup"><span data-stu-id="fe1ee-130">[How to Remove a Server from a Group](../core/how-to-remove-a-server-from-a-group.md) </span></span>  
 <span data-ttu-id="fe1ee-131">[如何修改群組屬性](../core/how-to-modify-group-properties.md) </span><span class="sxs-lookup"><span data-stu-id="fe1ee-131">[How to Modify Group Properties](../core/how-to-modify-group-properties.md) </span></span>  
 <span data-ttu-id="fe1ee-132">[處理組態架構](../install-and-config-guides/working-with-the-configuration-framework.md) </span><span class="sxs-lookup"><span data-stu-id="fe1ee-132">[Working with the Configuration Framework](../install-and-config-guides/working-with-the-configuration-framework.md) </span></span>  
 <span data-ttu-id="fe1ee-133">[如何新增主控件執行個體](../core/how-to-add-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="fe1ee-133">[How to Add a Host Instance](../core/how-to-add-a-host-instance.md) </span></span>  
 [<span data-ttu-id="fe1ee-134">管理伺服器</span><span class="sxs-lookup"><span data-stu-id="fe1ee-134">Managing Servers</span></span>](../core/managing-servers.md)