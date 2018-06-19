---
title: 如何建立服務帳戶新主控件和主控件執行個體 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Configuration Manager, service accounts
- Windows groups, service accounts
- Configuration Manager
- service accounts, Windows groups
- hosts, service accounts
- service accounts, hosts
- service accounts, Configuration Manager
- service accounts, creating
- creating, service accounts
ms.assetid: cef97f4a-8db1-41b6-9614-608c2fbf59a9
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d4887d78466340b12b95ed43d27523955ab0689
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969373"
---
# <a name="how-to-create-service-accounts-for-new-hosts-and-host-instances"></a><span data-ttu-id="71811-102">如何建立新主控件和主控件執行個體的服務帳戶</span><span class="sxs-lookup"><span data-stu-id="71811-102">How to Create Service Accounts for New Hosts and Host Instances</span></span>
<span data-ttu-id="71811-103">當您在單一電腦上安裝及設定 BizTalk Server 時，「組態管理員」會設定必要的 Windows 群組和使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="71811-103">The Configuration Manager configures the necessary Windows groups and user accounts when you install and configure BizTalk Server on a single computer.</span></span>  
  
 <span data-ttu-id="71811-104">執行「組態管理員」前，必須先手動建立 Windows 群組和使用者帳戶，並將使用者帳戶新增到網域環境中的 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="71811-104">You must manually create Windows groups and user accounts, and add the user accounts to the Windows groups in a domain environment before running the Configuration Manager.</span></span> <span data-ttu-id="71811-105">如需詳細資訊，請參閱[網域群組](../core/domain-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="71811-105">For more information, see [Domain Groups](../core/domain-groups.md).</span></span>  
  
 <span data-ttu-id="71811-106">您必須執行下列程序，才能建立新的主控件和主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="71811-106">You must perform the following procedure before creating a new host or host instance.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="71811-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="71811-107">Prerequisites</span></span>  
 <span data-ttu-id="71811-108">您必須以 Administrators 或 Domain Admins 群組成員的身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="71811-108">You must be logged on as a member of Administrators or Domain Admins group to perform this procedure.</span></span>  
  
### <a name="to-create-service-accounts-for-new-hosts-or-host-instances"></a><span data-ttu-id="71811-109">建立新主控件和主控件執行個體的服務帳戶</span><span class="sxs-lookup"><span data-stu-id="71811-109">To create service accounts for new hosts or host instances</span></span>  
  
1.  <span data-ttu-id="71811-110">為您將建立的新主控件建立主控件 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="71811-110">Create a host Windows group for the new host that you will create.</span></span> <span data-ttu-id="71811-111">如需建立新的主控件的詳細資訊，請參閱[如何建立新的主控件](../core/how-to-create-a-new-host.md)。</span><span class="sxs-lookup"><span data-stu-id="71811-111">For more information about creating a new host, see [How to Create a New Host](../core/how-to-create-a-new-host.md).</span></span>  
  
2.  <span data-ttu-id="71811-112">為您要新增到新主控件的每個主控件執行個體建立服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="71811-112">Create service accounts for each host instance that will be added to the new host.</span></span> <span data-ttu-id="71811-113">如需有關如何建立新的主控件執行個體的詳細資訊，請參閱[如何新增主控件執行個體](../core/how-to-add-a-host-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="71811-113">For more information about creating a new host instance, see [How to Add a Host Instance](../core/how-to-add-a-host-instance.md).</span></span>  
  
3.  <span data-ttu-id="71811-114">視需要將服務帳戶新增到主控件 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="71811-114">Add the service accounts to the host Windows group as needed.</span></span> <span data-ttu-id="71811-115">如需 Windows 群組，您必須新增服務帳戶資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="71811-115">For information about the Windows groups to which you must add the service account, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
4.  <span data-ttu-id="71811-116">在建立主控件和主控件執行個體時，使用 Windows 群組和服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="71811-116">Use the Windows group and service account when creating the host and host instances.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="71811-117">未指定\<*電腦名稱*\>\ 為使用本機群組的單一電腦安裝中的前置詞。</span><span class="sxs-lookup"><span data-stu-id="71811-117">Do not specify \<*computer name*\>\ as the prefix in a single computer setup with local groups.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="71811-118">如果您使用網域群組，您必須指定\<*網域 NetBIOS 名稱*\>\ 做為主控件 Windows 群組名稱前置詞。</span><span class="sxs-lookup"><span data-stu-id="71811-118">If you are using a Domain group, you must specify \<*Domain NetBIOS Name*\>\ as the prefix for the host Windows Group name.</span></span> <span data-ttu-id="71811-119">例如 CONTOSO\btssvc。</span><span class="sxs-lookup"><span data-stu-id="71811-119">For example, CONTOSO\btssvc.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71811-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="71811-120">See Also</span></span>  
 <span data-ttu-id="71811-121">[管理主控件和服務帳戶](../core/managing-hosts-and-service-accounts.md) </span><span class="sxs-lookup"><span data-stu-id="71811-121">[Managing Hosts and Service Accounts](../core/managing-hosts-and-service-accounts.md) </span></span>  
 <span data-ttu-id="71811-122">[管理 BizTalk Server 安全性](../core/managing-biztalk-server-security.md) </span><span class="sxs-lookup"><span data-stu-id="71811-122">[Managing BizTalk Server Security](../core/managing-biztalk-server-security.md) </span></span>  
 <span data-ttu-id="71811-123">[如何管理 BizTalk Server 系統管理員群組](../core/how-to-manage-the-biztalk-server-administrators-group.md) </span><span class="sxs-lookup"><span data-stu-id="71811-123">[How to Manage the BizTalk Server Administrators Group](../core/how-to-manage-the-biztalk-server-administrators-group.md) </span></span>  
 [<span data-ttu-id="71811-124">管理 Windows 群組和使用者帳戶的最佳做法</span><span class="sxs-lookup"><span data-stu-id="71811-124">Best Practices for Managing Windows Groups and User Accounts</span></span>](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)