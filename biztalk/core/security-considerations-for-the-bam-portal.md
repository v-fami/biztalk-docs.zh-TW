---
title: "BAM 入口網站的安全性考量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM portal, security
- BAM portal, administrator accounts
- user accounts, BAM
- administrator accounts, BAM portal
- BAM portal, user accounts
- security, BAM portal
ms.assetid: 5c8e6034-dfb8-4dba-b040-0c19504abdb2
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b0f5220eba5b66daf41dffc7ab74f93df8bb509
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="security-considerations-for-the-bam-portal"></a><span data-ttu-id="d71be-102">BAM 入口網站的安全性考量</span><span class="sxs-lookup"><span data-stu-id="d71be-102">Security Considerations for the BAM Portal</span></span>
<span data-ttu-id="d71be-103">依照最低權限原則，應對使用 BAM 入口網站執行例行工作的使用者帳戶賦予嚴格的存取權限。</span><span class="sxs-lookup"><span data-stu-id="d71be-103">Using the principle of least privilege, user accounts should have restrictive permissions to perform routine tasks in the BAM portal.</span></span> <span data-ttu-id="d71be-104">當您設定 BAM 的使用者帳戶時，請記住下列重點，以便在安全性與使用者之適當存取權之間取得平衡。</span><span class="sxs-lookup"><span data-stu-id="d71be-104">Keep the following points in mind as you set up your user accounts for BAM to balance security with appropriate access for users.</span></span>  
  
## <a name="user-accounts"></a><span data-ttu-id="d71be-105">使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="d71be-105">User accounts</span></span>  
 <span data-ttu-id="d71be-106">不能使用 BAM 入口網站的分散式的 navigationfeature 具有最小權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d71be-106">User accounts with minimum permissions are not able to use the BAM portal distributed navigationfeature.</span></span> <span data-ttu-id="d71be-107">若要能夠使用此功能，這些帳戶必須有足夠的權限，可以同時從遠端電腦和本機電腦存取 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="d71be-107">To be able to use this feature, these accounts must have sufficient permissions to allow access to the Web services on the remote computer as well as on the local computer.</span></span>  
  
 <span data-ttu-id="d71be-108">BAM Web 服務的使用者帳戶必須對所有的參考資料庫擁有存取權限，而且必須是參考資料庫的 BAM_ManagementWS 角色成員。</span><span class="sxs-lookup"><span data-stu-id="d71be-108">User accounts for the BAM Web services must have permissions to access all referenced databases and must be a member of the BAM_ManagementWS role in the referenced databases.</span></span>  
  
 <span data-ttu-id="d71be-109">對於下列使用者類型，請特別留意相關的考量重點：</span><span class="sxs-lookup"><span data-stu-id="d71be-109">For the following user types, you should be aware of these considerations:</span></span>  
  
-   <span data-ttu-id="d71be-110">網域使用者對裝載其所存取之主要匯入資料庫的遠端電腦必須擁有存取權限。</span><span class="sxs-lookup"><span data-stu-id="d71be-110">Domain Users, must have access permissions on remote computers that host Primary Import databases that are being accessed.</span></span>  
  
-   <span data-ttu-id="d71be-111">指派為本機使用者角色的使用者無法使用分散式導覽。</span><span class="sxs-lookup"><span data-stu-id="d71be-111">Users who are assigned Local User role, cannot use distributed navigation.</span></span>  
  
## <a name="administrator-accounts"></a><span data-ttu-id="d71be-112">系統管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="d71be-112">Administrator accounts</span></span>  
 <span data-ttu-id="d71be-113">系統管理員必須是 securityadmin 或 sysadmin 群組的成員，才能授與權限給網域使用者。</span><span class="sxs-lookup"><span data-stu-id="d71be-113">Administrators must be members of the securityadmin or sysadmin groups to grant permissions to domain users.</span></span>  
  
 <span data-ttu-id="d71be-114">若要執行 BAM 管理公用程式，您至少必須是 BAM 資料庫的資料庫操作員。</span><span class="sxs-lookup"><span data-stu-id="d71be-114">To run the BAM Management utility, you must be at least a database operator for the BAM databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d71be-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d71be-115">See Also</span></span>  
 [<span data-ttu-id="d71be-116">BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="d71be-116">BAM Portal</span></span>](../core/bam-portal.md)