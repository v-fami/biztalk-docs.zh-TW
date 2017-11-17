---
title: "存取控制和資料安全性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- access control, BizTalk Server Operator role
- databases, SQL roles
- access control, about access control
- BizTalk Server Administrator role
- databases, access control
- access control
- access control, BizTalk Server Administrator role
- access control, SQL roles
- user accounts, access control
- BizTalk Server Operator role
ms.assetid: f04fd4a3-0f8c-4170-934a-9cc77edd7f34
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11cb00eabf6110de78e2d194e0a25bfac6a3b6b0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="access-control-and-data-security"></a><span data-ttu-id="cafc5-102">存取控制與資料安全性</span><span class="sxs-lookup"><span data-stu-id="cafc5-102">Access Control and Data Security</span></span>
<span data-ttu-id="cafc5-103">BizTalk Server 會使用最低使用者權限來限制對其程序和資料庫的存取；您可以使用 Microsoft Windows Server 中的功能，協助保護系統中重要資料的安全。</span><span class="sxs-lookup"><span data-stu-id="cafc5-103">BizTalk Server limits access to its processes and databases by using minimum user rights; you can help secure important data in the system by using features from Microsoft Windows Server.</span></span> <span data-ttu-id="cafc5-104">基於安全考量，BizTalk Server 系統管理員和 BizTalk 主控件只應具備足以執行其工作的權限，而不宜有過多的授權。</span><span class="sxs-lookup"><span data-stu-id="cafc5-104">For security reasons, BizTalk Server Administrators and BizTalk Hosts should not have more user rights than necessary to perform their jobs.</span></span>  
  
 <span data-ttu-id="cafc5-105">BizTalk 會使用 SQL 角色來控制資料的「系統管理」存取權，從而透過工具及直接透過資料庫來控制資料存取。</span><span class="sxs-lookup"><span data-stu-id="cafc5-105">BizTalk controls Administrative access to data using SQL roles, thereby controlling access to data both via tools and directly via the database.</span></span> <span data-ttu-id="cafc5-106">資料的 BizTalk 主控件存取權是使用「主控件使用者」群組和帳戶來加以控制。</span><span class="sxs-lookup"><span data-stu-id="cafc5-106">BizTalk Host access to data is controlled using Host User groups and accounts.</span></span>  
  
 <span data-ttu-id="cafc5-107">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，有兩個系統管理角色： BizTalk Server 系統管理員和 BizTalk Server 操作員。</span><span class="sxs-lookup"><span data-stu-id="cafc5-107">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], there are two Administrative Roles: the BizTalk Server Administrator, and the BizTalk Server Operator.</span></span> <span data-ttu-id="cafc5-108">在任何時候透過安裝或 BizTalk Server 管理主控台建立 BizTalk Server 資料庫，BizTalk Server 都會自動替該資料庫中的這兩個系統管理角色建立 SQL 角色。</span><span class="sxs-lookup"><span data-stu-id="cafc5-108">Anytime you create a BizTalk Server database through installation or the BizTalk Server Administration Console, BizTalk Server automatically creates SQL roles for both these administrative roles in that database.</span></span> <span data-ttu-id="cafc5-109">BizTalk Server 會將系統管理員對 SQL Server 物件 (資料表、檢視、預存程序等) 所需的最低使用者權限，授與每個角色和任何指派給角色的 SQL Server 登入，以便對該資料庫執行管理工作。</span><span class="sxs-lookup"><span data-stu-id="cafc5-109">BizTalk Server grants each role, and any SQL Server login assigned to the role, the minimum user rights needed by administrators on the SQL Server objects (tables, views, stored procedures, etc) to perform administrative tasks on that database.</span></span>  
  
 <span data-ttu-id="cafc5-110">BizTalk Server 系統管理員是具有組態和追蹤資料存取權的高權限角色。</span><span class="sxs-lookup"><span data-stu-id="cafc5-110">The BizTalk Server Administrator is a high privilege role with access to configuration and tracking data.</span></span> <span data-ttu-id="cafc5-111">BizTalk Server 操作員則是低權限角色，僅具有用來監控和疑難排解動作的存取權。</span><span class="sxs-lookup"><span data-stu-id="cafc5-111">The BizTalk Server Operator is a low privilege role with access only to monitoring and troubleshooting actions.</span></span> <span data-ttu-id="cafc5-112">後者這個角色可以檢視服務狀態及訊息流程，並且可以啟動或停止應用程式以及終止和繼續服務執行個體，但是無法變更組態或檢視訊息屬性和內容。</span><span class="sxs-lookup"><span data-stu-id="cafc5-112">This latter role can view service state and message flow and can start or stop applications and terminate and resume service instances, but cannot change configuration or view message properties and content.</span></span>  
  
 <span data-ttu-id="cafc5-113">同樣的，BizTalk Server 會在每個資料庫中為每個主控件的使用者群組建立 SQL 角色，並且將使用者群組執行該主控件工作所需的最低使用者權限授與這個角色。</span><span class="sxs-lookup"><span data-stu-id="cafc5-113">Similarly, BizTalk Server creates in each database a SQL role for the user group for each host, and grants this role the minimum user rights it needs for the user group to perform tasks for that host.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cafc5-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="cafc5-114">In This Section</span></span>  
  
-   [<span data-ttu-id="cafc5-115">BizTalk Server 中的 Windows 群組和使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="cafc5-115">Windows Groups and User Accounts in BizTalk Server</span></span>](../core/windows-groups-and-user-accounts-in-biztalk-server.md)  
  
-   [<span data-ttu-id="cafc5-116">群組和服務帳戶的存取控制</span><span class="sxs-lookup"><span data-stu-id="cafc5-116">Access Control for Groups and Service Accounts</span></span>](../core/access-control-for-groups-and-service-accounts.md)  
  
-   [<span data-ttu-id="cafc5-117">系統管理角色的存取控制</span><span class="sxs-lookup"><span data-stu-id="cafc5-117">Access Control for Administrative Roles</span></span>](../core/access-control-for-administrative-roles.md)  
  
-   [<span data-ttu-id="cafc5-118">部署商務資訊的存取控制</span><span class="sxs-lookup"><span data-stu-id="cafc5-118">Access Control to Business Information</span></span>](../core/access-control-to-business-information.md)  
  
-   [<span data-ttu-id="cafc5-119">最小安全性使用者權限</span><span class="sxs-lookup"><span data-stu-id="cafc5-119">Minimum Security User Rights</span></span>](../core/minimum-security-user-rights.md)