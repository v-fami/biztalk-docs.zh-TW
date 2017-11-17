---
title: "網域群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9adc090e-e18c-46b6-b985-49b200d42966
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42833e24ee4b0ad8f78a8f60139d66ceb41a5f8f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="domain-groups-in-biztalk"></a><span data-ttu-id="13f81-102">在 BIzTalk 網域群組</span><span class="sxs-lookup"><span data-stu-id="13f81-102">Domain Groups in BIzTalk</span></span>
<span data-ttu-id="13f81-103">BizTalk Server 在單一電腦組態和多電腦組態中都支援網域群組和使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="13f81-103">BizTalk Server supports domain group and user accounts in both single and multiple computer configurations.</span></span> <span data-ttu-id="13f81-104">對於多電腦組態，您必須遵守本節以及《安裝指南》中的＜多伺服器環境的考量＞所規定的要求。</span><span class="sxs-lookup"><span data-stu-id="13f81-104">For multiple computer configurations, you must observe the requirements provided in this section and in the Considerations for Multiserver Environments in the Installation Guide.</span></span> <span data-ttu-id="13f81-105">如需詳細資訊，請參閱[安裝概觀](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md)。</span><span class="sxs-lookup"><span data-stu-id="13f81-105">For more information, see the [installation overview](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="13f81-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="13f81-106">Before you begin</span></span>
-   <span data-ttu-id="13f81-107">若您在 BizTalk Server 組態使用網域群組，則必須在設定 BizTalk Server 之前手動建立群組。</span><span class="sxs-lookup"><span data-stu-id="13f81-107">If you use domain groups for your BizTalk Server configuration, you must manually create the groups before you configure BizTalk Server.</span></span> <span data-ttu-id="13f81-108">「組態管理員」無法建立網域群組。</span><span class="sxs-lookup"><span data-stu-id="13f81-108">The Configuration Manager cannot create domain groups.</span></span>  
  
-   <span data-ttu-id="13f81-109">建立網域群組和/或使用者帳戶之後, 將使用者帳戶新增到正確的群組中的群組分支機構根據[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="13f81-109">After creating domain groups and/or user accounts, add user accounts to the proper groups according to the group affiliations in [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="13f81-110">使用 **\<DomainName >\\< 使用者名稱\>** Configuration Manager 中指定網域帳戶資訊時。</span><span class="sxs-lookup"><span data-stu-id="13f81-110">Use **\<DomainName>\\<UserName\>** when specifying domain account information in the Configuration Manager.</span></span>  
  
-   <span data-ttu-id="13f81-111">BizTalk Server 需要網域帳戶，才能用於所有叢集實例。</span><span class="sxs-lookup"><span data-stu-id="13f81-111">BizTalk Server requires domain accounts for all clustering scenarios.</span></span> <span data-ttu-id="13f81-112">您無法將本機帳戶用於叢集化 SQL Server 或叢集化 SSO Server (主要密碼伺服器)。</span><span class="sxs-lookup"><span data-stu-id="13f81-112">You cannot use local accounts with clustered SQL Server or clustered SSO Server (master secret server).</span></span>  
  
-   <span data-ttu-id="13f81-113">安裝和設定 BizTalk Server 系統管理員必須是下列群組的成員： SSO 系統管理員 （僅在設定主要密碼伺服器）。本機系統管理員。sysadmin SQL Server 角色。OLAP 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="13f81-113">The administrator installing and configuring BizTalk Server must be a member of the following groups: SSO Administrators (only when configuring the master secret server); local Administrators; sysadmin SQL Server role; OLAP Administrators.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13f81-114">如果您在「SSO 系統管理員」和「SSO 分支機構系統管理員」組態設定期間指定網域群組，而且也有足夠的權限，則可以自動建立網域群組。</span><span class="sxs-lookup"><span data-stu-id="13f81-114">You can create the domain group automatically if you specify a domain group during configuration for the SSO Administrators and SSO Affiliate Administrators, and you have sufficient privileges.</span></span> <span data-ttu-id="13f81-115">若您沒有足夠的權限，請確定這些群組已經存在。</span><span class="sxs-lookup"><span data-stu-id="13f81-115">If you do not have sufficient privileges, ensure that these groups already exist.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f81-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13f81-116">See Also</span></span>  
 <span data-ttu-id="13f81-117">[本機群組](../core/local-groups.md) </span><span class="sxs-lookup"><span data-stu-id="13f81-117">[Local Groups](../core/local-groups.md) </span></span>  
 <span data-ttu-id="13f81-118">[安裝概觀](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md) </span><span class="sxs-lookup"><span data-stu-id="13f81-118">[Installation Overview](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md) </span></span>  
 [<span data-ttu-id="13f81-119">BizTalk Server 中的 Windows 群組和使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="13f81-119">Windows Groups and User Accounts in BizTalk Server</span></span>](../core/windows-groups-and-user-accounts-in-biztalk-server.md)