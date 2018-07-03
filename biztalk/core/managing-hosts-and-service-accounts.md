---
title: 管理主機和服務帳戶 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, managing
- managing [user accounts]
- service accounts, security
- managing [hosts], security
- security, hosts
- managing [Windows groups]
- hosts, security
- security, service accounts
- Windows groups, managing
- user accounts, managing
ms.assetid: 25797571-f1f9-42a4-8fff-5b03076bbe36
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0f33a484d67981bb72908243b82e7835e0390e3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016112"
---
# <a name="managing-hosts-and-service-accounts"></a><span data-ttu-id="df1ea-102">管理主控件和服務帳戶</span><span class="sxs-lookup"><span data-stu-id="df1ea-102">Managing Hosts and Service Accounts</span></span>
<span data-ttu-id="df1ea-103">在設定 BizTalk Server 之後，您必須管理 Windows 群組和使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="df1ea-103">After you configure BizTalk Server, you must manage Windows groups and user accounts.</span></span> <span data-ttu-id="df1ea-104">本節提供有關管理這些 BizTalk Server 帳戶的資訊。</span><span class="sxs-lookup"><span data-stu-id="df1ea-104">This section provides information about how to manage these accounts for BizTalk Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df1ea-105">如果是多伺服器安裝 BizTalk Server，您必須使用網域全域群組。</span><span class="sxs-lookup"><span data-stu-id="df1ea-105">For a multiserver installation of BizTalk Server you must use a Domain Global group.</span></span> <span data-ttu-id="df1ea-106">如果是單一伺服器安裝 BizTalk Server，您可以使用網域全域群組或本機群組。</span><span class="sxs-lookup"><span data-stu-id="df1ea-106">For a single server installation of BizTalk Server you can use either a Domain Global group or a local group.</span></span>  
  
 <span data-ttu-id="df1ea-107">您必須具備 Windows 系統管理員的身分，才能執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="df1ea-107">You must be a Windows administrator to perform the following tasks:</span></span>  
  
- <span data-ttu-id="df1ea-108">建立主控件 Windows 群組</span><span class="sxs-lookup"><span data-stu-id="df1ea-108">Create a host Windows group</span></span>  
  
- <span data-ttu-id="df1ea-109">建立每個主控件執行個體的服務帳戶</span><span class="sxs-lookup"><span data-stu-id="df1ea-109">Create service accounts for each host instance</span></span>  
  
- <span data-ttu-id="df1ea-110">將服務帳戶新增到主控件 Windows 群組</span><span class="sxs-lookup"><span data-stu-id="df1ea-110">Add the service accounts to the host Windows group</span></span>  
  
- <span data-ttu-id="df1ea-111">修改與主控件關聯的 Windows 群組</span><span class="sxs-lookup"><span data-stu-id="df1ea-111">Modify the Windows group associated with the host</span></span>  
  
  <span data-ttu-id="df1ea-112">如需完整清單和群組和 BizTalk server 及其附屬的使用者帳戶的說明，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="df1ea-112">For a complete list and description of the groups and their affiliated user accounts in the BizTalk Server, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
  <span data-ttu-id="df1ea-113">最小安全性使用者權限的系統管理工作的詳細資訊，請參閱[最小安全性使用者權限](../core/minimum-security-user-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="df1ea-113">For more information the minimum security user rights for administrative tasks, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="df1ea-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="df1ea-114">In This Section</span></span>  
  
-   [<span data-ttu-id="df1ea-115">如何建立服務帳戶的新主控件和主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="df1ea-115">How to Create Service Accounts for New Hosts and Host Instances</span></span>](../core/how-to-create-service-accounts-for-new-hosts-and-host-instances.md)  
  
-   [<span data-ttu-id="df1ea-116">如何變更服務帳戶和密碼</span><span class="sxs-lookup"><span data-stu-id="df1ea-116">How to Change Service Accounts and Passwords</span></span>](../core/how-to-change-service-accounts-and-passwords.md)