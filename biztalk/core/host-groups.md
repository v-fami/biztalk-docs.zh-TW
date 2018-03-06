---
title: "主機群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d92478b-b3a2-4c5a-925e-5495ee481e82
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b3132b4084ed0d153895e252c5c64419ce0ac72
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="host-groups"></a><span data-ttu-id="63781-102">主控件群組</span><span class="sxs-lookup"><span data-stu-id="63781-102">Host Groups</span></span>

## <a name="overview"></a><span data-ttu-id="63781-103">概觀</span><span class="sxs-lookup"><span data-stu-id="63781-103">Overview</span></span>
<span data-ttu-id="63781-104">主控件群組是 Windows 群組 (預設名稱為「BizTalk 應用程式使用者」群組)，用於具有內含式 BizTalk 主控件 (BizTalk Server 中的主控件程序) 存取權的帳戶。</span><span class="sxs-lookup"><span data-stu-id="63781-104">The host group is the Windows group (named the BizTalk Application Users group by default) that you use for accounts with access to the in-process BizTalk hosts (host processes in BizTalk Server).</span></span> <span data-ttu-id="63781-105">建議您在環境中對每個內含式主控件使用一個主控件群組。</span><span class="sxs-lookup"><span data-stu-id="63781-105">It is recommended that you use one host group for each in-process host in your environment.</span></span>  
  
 <span data-ttu-id="63781-106">只將一個 Windows 群組與主應用程式產生關聯 (稱為 *主機群組*)。</span><span class="sxs-lookup"><span data-stu-id="63781-106">You can only associate a host with one Windows group (called a *host group*).</span></span> <span data-ttu-id="63781-107">主控件群組必須擁有所有相關的 BizTalk Server 資料庫中的 SQL Server 登入和權限。</span><span class="sxs-lookup"><span data-stu-id="63781-107">The host group must have a SQL Server login and privileges in all relevant BizTalk Server databases.</span></span> <span data-ttu-id="63781-108">建立主控件與主控件群組的關聯時，您就將主控件群組的權限授與主控件。</span><span class="sxs-lookup"><span data-stu-id="63781-108">When you associate a host with the host group, you grant the host the privileges of the host group.</span></span>  
  
 <span data-ttu-id="63781-109">若是使用「組態精靈」建立主控件，而且指定本機 Windows 群組用於主控件，則「組態精靈」會自動建立兩個 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="63781-109">If you use the Configuration Wizard to create hosts, and you specify a local Windows group to use for hosts, the Configuration Wizard automatically creates two Windows groups.</span></span> <span data-ttu-id="63781-110">這些群組的預設名稱為「BizTalk 應用程式使用者」群組及「BizTalk 外掛式主控件使用者」群組。</span><span class="sxs-lookup"><span data-stu-id="63781-110">The default names of these groups are the BizTalk Application Users group and the BizTalk Isolated Host Users group.</span></span>  
  
 <span data-ttu-id="63781-111">建立與主控件群組關聯之主控件的主控件執行個體時，此主控件執行個體即繼承了主控件群組的資料庫權限。</span><span class="sxs-lookup"><span data-stu-id="63781-111">When you create a host instance of a host associated with the host group, the host instance inherits the database privileges of the host group.</span></span>  
  
 <span data-ttu-id="63781-112">主控件群組是主控件 Windows Management Instrumentation (WMI) 物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="63781-112">The host group is a property of the host Windows Management Instrumentation (WMI) object.</span></span> <span data-ttu-id="63781-113">若是主控件沒有主控件執行個體，則可變更主控件所屬的 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="63781-113">You can change the Windows group that a host belongs to if there are no host instances of the host.</span></span>  
  
 <span data-ttu-id="63781-114">建立主控件時可指定主控件所屬的主控件群組。</span><span class="sxs-lookup"><span data-stu-id="63781-114">You specify the host group a host belongs to when you create the host.</span></span> <span data-ttu-id="63781-115">BizTalk WMI 提供者將主控件群組具有的權限授與主控件，例如，BizTalk Server 執行階段功能的權限，包括 SQL Server 登入和資料庫使用者存取。</span><span class="sxs-lookup"><span data-stu-id="63781-115">The BizTalk WMI provider grants the privileges that the host group has (for example, the BizTalk Server privileges required for runtime functionality, including SQL Server logins and database user access) to the host.</span></span> <span data-ttu-id="63781-116">建立主控件執行個體時必須指定正確的服務帳戶 (主控件)，如此 BizTalk Server WMI 提供者才能將主控件群組的權限授與主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="63781-116">You must specify the correct service account (host) when you create a host instance, so that the BizTalk Server WMI provider grants the privileges of the host group to the host instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63781-117">若是要建立本機主控件群組，可以建立本機 Windows 群組，並指定網域使用者為群組成員。</span><span class="sxs-lookup"><span data-stu-id="63781-117">If you want to create a local host group, you can create a local Windows group and assign a domain user as a member of the group.</span></span> <span data-ttu-id="63781-118">若指定本機 Windows 群組給主控件，則無論是網域或本機使用者的 Windows 群組成員都可以做為主控件執行個體登入使用者。</span><span class="sxs-lookup"><span data-stu-id="63781-118">If you specify a local Windows group for the Host, the Windows group member, whether it is a domain or local user, can be used as the host instance log-on user.</span></span>  

## <a name="required-permissions"></a><span data-ttu-id="63781-119">必要權限</span><span class="sxs-lookup"><span data-stu-id="63781-119">Required permissions</span></span>  
 <span data-ttu-id="63781-120">主控件群組需要下列權限：</span><span class="sxs-lookup"><span data-stu-id="63781-120">The host group requires the following privileges:</span></span>  
  
-   <span data-ttu-id="63781-121">它在下列資料庫中必須是 BTS_HOST_USERS SQL Server 角色的成員：</span><span class="sxs-lookup"><span data-stu-id="63781-121">It must be a member of the BTS_HOST_USERS SQL Server role in the following databases:</span></span>  
  
    -   <span data-ttu-id="63781-122">BizTalk 管理</span><span class="sxs-lookup"><span data-stu-id="63781-122">BizTalk Management</span></span> 
  
    -   <span data-ttu-id="63781-123">MessageBox</span><span class="sxs-lookup"><span data-stu-id="63781-123">MessageBox</span></span>  
  
    -   <span data-ttu-id="63781-124">規則引擎</span><span class="sxs-lookup"><span data-stu-id="63781-124">Rule Engine</span></span>  
  
    -   <span data-ttu-id="63781-125">追蹤</span><span class="sxs-lookup"><span data-stu-id="63781-125">Tracking</span></span>  
  
    -   <span data-ttu-id="63781-126">BAM 主要匯入</span><span class="sxs-lookup"><span data-stu-id="63781-126">BAM Primary Import</span></span>  
  
-   <span data-ttu-id="63781-127">它必須是成員的 BTS_<\<內含式主控件名稱\>（_u） MessageBox 資料庫的 SQL Server 角色</span><span class="sxs-lookup"><span data-stu-id="63781-127">It must be a member of the BTS_\<in-process host name\>_USERS SQL Server role for the MessageBox database</span></span>  
  
-   <span data-ttu-id="63781-128">在 BAM 主要匯入資料庫中必須是 BAM_EVENT_WRITER SQL Server 角色的成員。</span><span class="sxs-lookup"><span data-stu-id="63781-128">It must be a member of the BAM_EVENT_WRITER SQL Server role in the BAM Primary Import database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63781-129">若是指定主控件為追蹤主控件，「BizTalk Server 管理」會自動為「追蹤」資料庫移除 SQL Server 角色中的「BizTalk 主控件」群組。</span><span class="sxs-lookup"><span data-stu-id="63781-129">If you designate a host as a tracking host, BizTalk Server Administration automatically removes the BizTalk Host group from the SQL Server roles for the Tracking database.</span></span> <span data-ttu-id="63781-130">您必須從「BizTalk 管理」資料庫和 MessageBox 資料庫的 SQL Server 角色中，手動移除 BizTalk 主控件群組。</span><span class="sxs-lookup"><span data-stu-id="63781-130">You must manually remove the BizTalk Host group from the SQL Server roles for the BizTalk Management database and the MessageBox database.</span></span> <span data-ttu-id="63781-131">如需將主控件指定為追蹤主控件的資訊，請參閱[修改主機內容](../core/how-to-modify-host-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="63781-131">For information about designating a host as a tracking host, see [Modify Host Properties](../core/how-to-modify-host-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63781-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63781-132">See Also</span></span>  
 [<span data-ttu-id="63781-133">實體</span><span class="sxs-lookup"><span data-stu-id="63781-133">Entities</span></span>](../core/entities.md)