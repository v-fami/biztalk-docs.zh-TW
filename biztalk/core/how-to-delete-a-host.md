---
title: 刪除主控件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e3df8719-27cb-4010-82e3-68226ab74b17
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fd5f54fa84ddb521444cfb3f2351a8062c4de00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249150"
---
# <a name="delete-a-host"></a><span data-ttu-id="bc341-102">刪除主控件</span><span class="sxs-lookup"><span data-stu-id="bc341-102">Delete a Host</span></span>
<span data-ttu-id="bc341-103">只有在下列情況才可以刪除主控件：</span><span class="sxs-lookup"><span data-stu-id="bc341-103">You can delete a host only in the following circumstances:</span></span>  
  
-   <span data-ttu-id="bc341-104">不是預設主控件。</span><span class="sxs-lookup"><span data-stu-id="bc341-104">It is not the default host.</span></span>  
  
-   <span data-ttu-id="bc341-105">不是執行主控件追蹤的唯一主控件。</span><span class="sxs-lookup"><span data-stu-id="bc341-105">It is not the only host that is performing host tracking.</span></span>  
  
-   <span data-ttu-id="bc341-106">沒有裝載任何配接器處理常式。</span><span class="sxs-lookup"><span data-stu-id="bc341-106">It is not hosting any adapter handlers.</span></span>  
  
-   <span data-ttu-id="bc341-107">沒有已登錄的協調流程。</span><span class="sxs-lookup"><span data-stu-id="bc341-107">It has no enlisted orchestrations.</span></span>  
  
-   <span data-ttu-id="bc341-108">沒有已開始的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc341-108">There are no started instances of the host.</span></span>  
  
-   <span data-ttu-id="bc341-109">如果主控件未叢集化。</span><span class="sxs-lookup"><span data-stu-id="bc341-109">If the host is not clustered.</span></span>  
  
 <span data-ttu-id="bc341-110">如需主控件的詳細資訊，請參閱[主機](../core/hosts.md)。</span><span class="sxs-lookup"><span data-stu-id="bc341-110">For more information about hosts, see [Hosts](../core/hosts.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bc341-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="bc341-111">Prerequisites</span></span>  
 <span data-ttu-id="bc341-112">您必須具有以下的使用者權限才能建立主控件、修改主控件屬性和刪除主控件：</span><span class="sxs-lookup"><span data-stu-id="bc341-112">You must have the following user rights to create hosts, modify host properties, and delete hosts:</span></span>  
  
-   <span data-ttu-id="bc341-113">您必須是「BizTalk Server 系統管理員」群組的成員。</span><span class="sxs-lookup"><span data-stu-id="bc341-113">You must be a member of the BizTalk Server Administrators group.</span></span>  
  
-   <span data-ttu-id="bc341-114">在 SQL Server 中您必須具有以下權限：</span><span class="sxs-lookup"><span data-stu-id="bc341-114">You must have the following rights in SQL Server:</span></span>  
  
    -   <span data-ttu-id="bc341-115">您必須是 SQL Server 系統管理員，或是 BizTalk 追蹤資料庫 (BizTalk DTADb)、MessageBox 資料庫 (BizTalkMsgBoxDb)，以及 BAM 主要匯入資料庫 (BAMPrimaryImport) 中 db_owner 或 db_securityadmin SQL Server 資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="bc341-115">You must be either a SQL Server administrator, or a member of the db_owner or db_securityadmin SQL Server database roles in the BizTalk Tracking database (BizTalk DTADb), MessageBox databases (BizTalkMsgBoxDb), and the BAM Primary Import database (BAMPrimaryImport).</span></span>  
  
    -   <span data-ttu-id="bc341-116">您必須是具有 MessageBox 資料庫之所有電腦上 sysadmin SQL Server 角色的成員，或是所有 MessageBox 資料庫中 db_owner 或 db_ddladmin SQL Server 角色的成員。</span><span class="sxs-lookup"><span data-stu-id="bc341-116">You must be a member of the sysadmin SQL Server role on all the computers where there are MessageBox databases, or a member of the db_owner or db_ddladmin SQL Server role for all the MessageBox databases.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="bc341-117">步驟</span><span class="sxs-lookup"><span data-stu-id="bc341-117">Steps</span></span> 
  
1.  <span data-ttu-id="bc341-118">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="bc341-118">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="bc341-119">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，展開 BizTalk 群組，按一下**平台設定**，然後按一下 **主機**。</span><span class="sxs-lookup"><span data-stu-id="bc341-119">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, click **Platform Settings**, and then click **Hosts**.</span></span>  
  
3.  <span data-ttu-id="bc341-120">在詳細資料窗格中，以滑鼠右鍵按一下您想要刪除，然後按一下 的主機**刪除**。</span><span class="sxs-lookup"><span data-stu-id="bc341-120">In the details pane, right-click the host you want to delete, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="bc341-121">在**確認主機刪除**對話方塊中，按一下 **是**。</span><span class="sxs-lookup"><span data-stu-id="bc341-121">In the **Confirm host delete** dialog box, click **Yes**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc341-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc341-122">See Also</span></span>  
-  [<span data-ttu-id="bc341-123">管理 BizTalk 主控件和主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="bc341-123">Managing BizTalk Hosts and Host Instances</span></span>](../core/managing-biztalk-hosts-and-host-instances.md)   
-  [<span data-ttu-id="bc341-124">如何建立新的主機</span><span class="sxs-lookup"><span data-stu-id="bc341-124">How to Create a New Host</span></span>](../core/how-to-create-a-new-host.md)   
-  [<span data-ttu-id="bc341-125">如何修改主控件屬性</span><span class="sxs-lookup"><span data-stu-id="bc341-125">How to Modify Host Properties</span></span>](../core/how-to-modify-host-properties.md)   
-  <span data-ttu-id="bc341-126">**MSBTS_Host (WMI)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="bc341-126">**MSBTS_Host (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>