---
title: 如何從群組移除伺服器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- groups, servers
- managing [groups], deleting servers
- servers, deleting
- deleting, groups
- servers
- managing [servers], deleting from groups
- groups, deleting
- servers, groups
- deleting, servers
ms.assetid: 85596e18-fa17-4f44-bc20-2e4cb578e109
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b69eb694da320e598c7d0cfe5a03d58e0a723a8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255382"
---
# <a name="how-to-remove-a-server-from-a-group"></a><span data-ttu-id="61947-102">如何從群組移除伺服器</span><span class="sxs-lookup"><span data-stu-id="61947-102">How to Remove a Server from a Group</span></span>
<span data-ttu-id="61947-103">一部伺服器僅能與一個 BizTalk 群組關聯。</span><span class="sxs-lookup"><span data-stu-id="61947-103">A server can only be associated with one BizTalk group.</span></span> <span data-ttu-id="61947-104">如果伺服器已經屬於其他群組，您必須先從目前的群組移除該伺服器，才可將其新增至新群組。</span><span class="sxs-lookup"><span data-stu-id="61947-104">If a server already belongs to another group, you must first remove that server from its current group before you can add it to a new group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="61947-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="61947-105">Prerequisites</span></span>  
 <span data-ttu-id="61947-106">若要執行此程序，您必須以「Windows 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="61947-106">To perform this procedure, you must be logged on as a member of the Windows Administrators group.</span></span>  
  
### <a name="to-remove-a-server-from-a-group"></a><span data-ttu-id="61947-107">從群組移除伺服器</span><span class="sxs-lookup"><span data-stu-id="61947-107">To remove a server from a group</span></span>  
  
1.  <span data-ttu-id="61947-108">您想要從 BizTalk Server 群組中移除的電腦，按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 組態**.</span><span class="sxs-lookup"><span data-stu-id="61947-108">On the computer that you want to remove from a BizTalk Server group, click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.</span></span>  
  
2.  <span data-ttu-id="61947-109">在功能表列上，按一下 **取消設定功能**。</span><span class="sxs-lookup"><span data-stu-id="61947-109">On the menu bar, click **Unconfigure Features**.</span></span>  
  
3.  <span data-ttu-id="61947-110">在**取消設定功能**對話方塊中，選取**群組**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="61947-110">In the **Unconfigure Features** dialog box, select **Group**, and then click **OK**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="61947-111">取消設定群組也會將該電腦上設定的所有相關功能取消設定。</span><span class="sxs-lookup"><span data-stu-id="61947-111">Unconfiguring a group will also unconfigure all dependent features that are already configured on that computer.</span></span>  
  
4.  <span data-ttu-id="61947-112">按一下 **[是]**。</span><span class="sxs-lookup"><span data-stu-id="61947-112">Click **Yes**.</span></span>  
  
5.  <span data-ttu-id="61947-113">在 Microsoft BizTalk Server 組態精靈中，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="61947-113">In the Microsoft BizTalk Server Configuration Wizard, click **Next**.</span></span>  
  
     <span data-ttu-id="61947-114">群組和其相依的功能已取消設定。</span><span class="sxs-lookup"><span data-stu-id="61947-114">The Group and its dependent features are unconfigured.</span></span>  
  
6.  <span data-ttu-id="61947-115">按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="61947-115">Click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61947-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61947-116">See Also</span></span>  
 <span data-ttu-id="61947-117">[管理群組](../core/managing-groups.md) </span><span class="sxs-lookup"><span data-stu-id="61947-117">[Managing Groups](../core/managing-groups.md) </span></span>  
 <span data-ttu-id="61947-118">[BizTalk 群組](../core/biztalk-groups.md) </span><span class="sxs-lookup"><span data-stu-id="61947-118">[BizTalk Groups](../core/biztalk-groups.md) </span></span>  
 <span data-ttu-id="61947-119">[如何將伺服器新增至群組](../core/how-to-add-a-server-to-a-group.md) </span><span class="sxs-lookup"><span data-stu-id="61947-119">[How to Add a Server to a Group](../core/how-to-add-a-server-to-a-group.md) </span></span>  
 <span data-ttu-id="61947-120">[如何將伺服器從一個群組移至另一個](../core/how-to-move-a-server-from-one-group-to-another.md) </span><span class="sxs-lookup"><span data-stu-id="61947-120">[How to Move a Server from One Group to Another](../core/how-to-move-a-server-from-one-group-to-another.md) </span></span>  
 <span data-ttu-id="61947-121">[如何修改群組屬性](../core/how-to-modify-group-properties.md) </span><span class="sxs-lookup"><span data-stu-id="61947-121">[How to Modify Group Properties](../core/how-to-modify-group-properties.md) </span></span>  
 [<span data-ttu-id="61947-122">管理伺服器</span><span class="sxs-lookup"><span data-stu-id="61947-122">Managing Servers</span></span>](../core/managing-servers.md)