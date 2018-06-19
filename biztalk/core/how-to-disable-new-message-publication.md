---
title: 停用新訊息發佈 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9099ecaa-31ed-4880-a0f6-8dbfaf783f7a
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 478cf89ac4677d60e9a5b5a855998e0b0e5120c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254558"
---
# <a name="disable-new-message-publication"></a><span data-ttu-id="4cebe-102">停用新訊息發佈</span><span class="sxs-lookup"><span data-stu-id="4cebe-102">Disable New Message Publication</span></span>

## <a name="overview"></a><span data-ttu-id="4cebe-103">概觀</span><span class="sxs-lookup"><span data-stu-id="4cebe-103">Overview</span></span>
<span data-ttu-id="4cebe-104">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台或 Windows Management Instrumentation (WMI)，來停用新訊息發佈。</span><span class="sxs-lookup"><span data-stu-id="4cebe-104">You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console or Windows Management Instrumentation (WMI) to disable new message publication.</span></span> <span data-ttu-id="4cebe-105">您可停用 MessageBox 資料庫中的新訊息發佈，以停止 MessageBox 資料庫接收新訊息。</span><span class="sxs-lookup"><span data-stu-id="4cebe-105">You disable new message publication in the MessageBox database to stop the receipt of new messages by the MessageBox database.</span></span> <span data-ttu-id="4cebe-106">在某些 BizTalk Server 環境中，若您停用主要 MessageBox 資料庫的新訊息發佈，即能改善效能。</span><span class="sxs-lookup"><span data-stu-id="4cebe-106">In some BizTalk Server environments, you can improve performance if you disable new message publication for the master MessageBox database.</span></span> <span data-ttu-id="4cebe-107">停用新訊息發佈並不會影響 MessageBox 資料庫中的現有訊息或是進行中的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="4cebe-107">Disabling new message publication does not affect existing messages in the MessageBox database or service instances that are in progress.</span></span>  
  
 <span data-ttu-id="4cebe-108">如需使用 WMI 停用新訊息發佈的詳細資訊，請參閱**MSBTS_MsgBoxSetting.DisableNewMessagePublication 屬性 (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="4cebe-108">For information about using WMI to disable new message publication, see the **MSBTS_MsgBoxSetting.DisableNewMessagePublication Property (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
> [!IMPORTANT]
>  <span data-ttu-id="4cebe-109">刪除 MessageBox 資料庫前，必須先停用新訊息發佈。</span><span class="sxs-lookup"><span data-stu-id="4cebe-109">You must disable the publication of new messages before you delete a MessageBox database.</span></span> <span data-ttu-id="4cebe-110">如需刪除 MessageBox 資料庫的詳細資訊，請參閱[如何刪除 MessageBox 資料庫](../core/how-to-delete-a-messagebox-database.md)。</span><span class="sxs-lookup"><span data-stu-id="4cebe-110">For information about deleting a MessageBox database, see [How to Delete a MessageBox Database](../core/how-to-delete-a-messagebox-database.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4cebe-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="4cebe-111">Prerequisites</span></span>  
 <span data-ttu-id="4cebe-112">管理 MessageBox 資料庫的系統管理員必須具備必要的使用者權限。</span><span class="sxs-lookup"><span data-stu-id="4cebe-112">Administrators who manage MessageBox databases must have the required user rights.</span></span> <span data-ttu-id="4cebe-113">您必須具備下列使用者權限，才能管理 MessageBox 資料庫和停用新訊息發佈：</span><span class="sxs-lookup"><span data-stu-id="4cebe-113">You must have the following user rights to manage MessageBox databases and disable new message publication:</span></span>  
  
-   <span data-ttu-id="4cebe-114">您必須以「BizTalk Server 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="4cebe-114">You must be logged on as a member of the BizTalk Server Administrators group.</span></span>  
  
-   <span data-ttu-id="4cebe-115">您必須是資料庫所在電腦的 SQL Server 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="4cebe-115">You must be a SQL Server Administrator on the computer where the database exists.</span></span>  
  
## <a name="disable-steps"></a><span data-ttu-id="4cebe-116">停用步驟</span><span class="sxs-lookup"><span data-stu-id="4cebe-116">Disable steps</span></span>
  
1.  <span data-ttu-id="4cebe-117">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="4cebe-117">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="4cebe-118">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，展開 BizTalk 群組，按一下**平台設定**，然後按一下 **訊息方塊**。</span><span class="sxs-lookup"><span data-stu-id="4cebe-118">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, click **Platform Settings**, and then click **Message Boxes**.</span></span>  
  
3.  <span data-ttu-id="4cebe-119">在詳細資料窗格中，以滑鼠右鍵按一下您想要停用，然後按一下 MessageBox 資料庫**屬性**。</span><span class="sxs-lookup"><span data-stu-id="4cebe-119">In the details pane, right-click the MessageBox database you want to disable, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="4cebe-120">在**Messagebox 屬性**對話方塊中，選取**停用新訊息發佈**核取方塊，然後**確定**。</span><span class="sxs-lookup"><span data-stu-id="4cebe-120">In the **Message Box Properties** dialog box, select the **Disable new message publication** check box, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cebe-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cebe-121">See Also</span></span>  
 <span data-ttu-id="4cebe-122">[管理 MessageBox 資料庫](../core/managing-messagebox-databases.md) </span><span class="sxs-lookup"><span data-stu-id="4cebe-122">[Managing MessageBox Databases](../core/managing-messagebox-databases.md) </span></span>  
 <span data-ttu-id="4cebe-123">[加入新的 MessageBox 資料庫](../core/how-to-add-a-new-messagebox-database.md) </span><span class="sxs-lookup"><span data-stu-id="4cebe-123">[Add a New MessageBox Database](../core/how-to-add-a-new-messagebox-database.md) </span></span>  
 <span data-ttu-id="4cebe-124">[刪除 MessageBox 資料庫](../core/how-to-delete-a-messagebox-database.md) </span><span class="sxs-lookup"><span data-stu-id="4cebe-124">[Delete a MessageBox Database](../core/how-to-delete-a-messagebox-database.md) </span></span>  
 [<span data-ttu-id="4cebe-125">MessageBox 資料庫</span><span class="sxs-lookup"><span data-stu-id="4cebe-125">The MessageBox Database</span></span>](../core/the-messagebox-database.md)