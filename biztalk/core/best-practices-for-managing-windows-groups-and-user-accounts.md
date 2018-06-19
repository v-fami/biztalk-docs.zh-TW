---
title: 管理 Windows 群組和使用者帳戶的最佳作法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- best practices, Windows groups
- authenticating, best practices
- Windows groups, security
- best practices, user accounts
- best practices, security
- security, best practices
- user accounts, security
- authenticating, security
- Windows groups, best practices
- best practices, authenticating
- user accounts, best practices
- hosts, security
- hosts, best practices
- best practices, hosts
ms.assetid: 0c4a141e-97ce-434a-8e45-a56c634bbd6c
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 71f7560e3867bf290f20e0f2f49a740d7298131b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231222"
---
# <a name="best-practices-for-managing-windows-groups-and-user-accounts"></a><span data-ttu-id="f0edb-102">管理 Windows 群組和使用者帳戶的最佳作法</span><span class="sxs-lookup"><span data-stu-id="f0edb-102">Best Practices for Managing Windows Groups and User Accounts</span></span>
<span data-ttu-id="f0edb-103">本節包含管理 Windows 群組和使用者帳戶安全性的最佳作法和秘訣。</span><span class="sxs-lookup"><span data-stu-id="f0edb-103">This section contains best practices and tips for managing security for Windows groups and user accounts.</span></span>  
  
-   <span data-ttu-id="f0edb-104">**使用服務帳戶與主控件執行個體所需的最小權限**</span><span class="sxs-lookup"><span data-stu-id="f0edb-104">**Use service accounts with minimum privileges necessary for host instances**</span></span>  
  
     <span data-ttu-id="f0edb-105">為協助保障 BizTalk Server 環境的安全性，建議您使用只具備執行主控件執行個體所需之最小權限的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="f0edb-105">To help ensure the security of your BizTalk Server environment, we recommend that you use service accounts with the minimum privileges necessary to run host instances.</span></span> <span data-ttu-id="f0edb-106">如需有關服務帳戶需要的最低權限的詳細資訊，請參閱[存取控制與資料安全性](../core/access-control-and-data-security.md)。</span><span class="sxs-lookup"><span data-stu-id="f0edb-106">For more information about the minimum privileges that service accounts require, see [Access Control and Data Security](../core/access-control-and-data-security.md).</span></span>  
  
-   <span data-ttu-id="f0edb-107">**信任的驗證和非信任的主控件使用不同的使用者群組**</span><span class="sxs-lookup"><span data-stu-id="f0edb-107">**Use different user groups for authentication trusted and non-trusted hosts**</span></span>  
  
     <span data-ttu-id="f0edb-108">為確保非驗證信任之主控件的權限比驗證信任之主控件的權限小，您必須針對每個主控件使用不同的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="f0edb-108">To ensure that non-authentication trusted hosts have fewer privileges than authentication trusted hosts, you must use different service accounts for each host.</span></span>  
  
-   <span data-ttu-id="f0edb-109">**針對每個 BizTalk 主控件使用不同的使用者群組**</span><span class="sxs-lookup"><span data-stu-id="f0edb-109">**Use a different user group for each BizTalk Host**</span></span>  
  
     <span data-ttu-id="f0edb-110">為最大化主控件間的安全範圍，建議您針對 BizTalk 群組中的每個 BizTalk 主控件使用不同的 Windows 使用者群組。</span><span class="sxs-lookup"><span data-stu-id="f0edb-110">To maximize the security boundary between hosts, we recommend that you use a different Windows user group for each BizTalk Host in your BizTalk group.</span></span>  
  
-   <span data-ttu-id="f0edb-111">**從 BizTalk Server 系統管理員群組中移除安裝使用者**</span><span class="sxs-lookup"><span data-stu-id="f0edb-111">**Remove the installation user from the BizTalk Server Administrators group**</span></span>  
  
     <span data-ttu-id="f0edb-112">當您在具備本機群組的單一電腦上安裝 BizTalk Server 時，會自動將執行 BizTalk Server 互動式安裝的使用者新增到 BizTalk Server 系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="f0edb-112">When you install BizTalk Server on a single computer with local groups, the user performing an interactive installation of BizTalk Server is automatically added to the BizTalk Server Administrators group.</span></span> <span data-ttu-id="f0edb-113">這可讓該使用者以組態管理員來設定 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="f0edb-113">This allows that user to configure BizTalk Server with the Configuration Manager.</span></span>  
  
     <span data-ttu-id="f0edb-114">如果安裝 BizTalk Server 的使用者將不會管理 BizTalk Server，建議您在設定 BizTalk Server 後將這位使用者從 BizTalk Server 系統管理員群組移除。</span><span class="sxs-lookup"><span data-stu-id="f0edb-114">If the user who installs BizTalk Server will not be administering BizTalk Server, we recommend that you remove this user from the BizTalk Server Administrators group after BizTalk Server is configured.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0edb-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0edb-115">See Also</span></span>  
 [<span data-ttu-id="f0edb-116">管理 BizTalk Server 安全性</span><span class="sxs-lookup"><span data-stu-id="f0edb-116">Managing BizTalk Server Security</span></span>](../core/managing-biztalk-server-security.md)