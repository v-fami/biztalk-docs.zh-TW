---
title: 使用 SSO |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [SSO]
- SSO, managing
ms.assetid: e7245632-9c71-4b1f-836d-a4ea1dd6e5ee
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 850425f140b526baf251568f09ab47db9115e8ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287814"
---
# <a name="using-sso"></a><span data-ttu-id="8b01b-102">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="8b01b-102">Using SSO</span></span>
<span data-ttu-id="8b01b-103">您可以使用 MMC 嵌入式管理單元或是命令列管理公用程式 (ssomanage)，以管理 SSO 系統。</span><span class="sxs-lookup"><span data-stu-id="8b01b-103">You can use either the MMC Snap-in or the command line management utility (ssomanage) to manage the SSO system.</span></span> <span data-ttu-id="8b01b-104">這包括像是更新 SSO 資料庫、新增、刪除和管理應用程式以及管理使用者對應等活動。</span><span class="sxs-lookup"><span data-stu-id="8b01b-104">This includes activities such as updating the SSO database, adding, deleting, and managing applications, and administering user mappings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b01b-105">在系統上可支援使用者帳戶控制 (UAC)，您可能需要以系統管理權限執行 SSO 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="8b01b-105">On a system that supports User Account Control (UAC), you may need to run the SSO command line tools with Administrative privileges.</span></span>  
  
 <span data-ttu-id="8b01b-106">只有「單一登入」系統管理員可以執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="8b01b-106">Only Single Sign-On Administrators can perform these tasks.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b01b-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="8b01b-107">In This Section</span></span>  
  
-   [<span data-ttu-id="8b01b-108">如何設定 SSO 伺服器</span><span class="sxs-lookup"><span data-stu-id="8b01b-108">How to Set the SSO Server</span></span>](../core/how-to-set-the-sso-server.md)  
  
-   [<span data-ttu-id="8b01b-109">如何啟用 SSO</span><span class="sxs-lookup"><span data-stu-id="8b01b-109">How to Enable SSO</span></span>](../core/how-to-enable-sso.md)  
  
-   [<span data-ttu-id="8b01b-110">如何變更主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="8b01b-110">How to Change the Master Secret Server</span></span>](../core/how-to-change-the-master-secret-server.md)  
  
-   [<span data-ttu-id="8b01b-111">如何停用 SSO</span><span class="sxs-lookup"><span data-stu-id="8b01b-111">How to Disable SSO</span></span>](../core/how-to-disable-sso.md)  
  
-   [<span data-ttu-id="8b01b-112">如何更新 SSO 資料庫</span><span class="sxs-lookup"><span data-stu-id="8b01b-112">How to Update the SSO Database</span></span>](../core/how-to-update-the-sso-database.md)  
  
-   [<span data-ttu-id="8b01b-113">如何顯示 SSO 資料庫資訊</span><span class="sxs-lookup"><span data-stu-id="8b01b-113">How to Display the SSO Database Information</span></span>](../core/how-to-display-the-sso-database-information.md)  
  
-   [<span data-ttu-id="8b01b-114">如何設定 SSO 票證</span><span class="sxs-lookup"><span data-stu-id="8b01b-114">How to Configure the SSO Tickets</span></span>](../core/how-to-configure-the-sso-tickets.md)  
  
-   [<span data-ttu-id="8b01b-115">如何稽核 SSO</span><span class="sxs-lookup"><span data-stu-id="8b01b-115">How to Audit SSO</span></span>](../core/how-to-audit-sso.md)  
  
-   [<span data-ttu-id="8b01b-116">如何為 SSO 啟用 SSL</span><span class="sxs-lookup"><span data-stu-id="8b01b-116">How to Enable SSL for SSO</span></span>](../core/how-to-enable-ssl-for-sso.md)  
  
-   [<span data-ttu-id="8b01b-117">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="8b01b-117">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)  
  
-   [<span data-ttu-id="8b01b-118">如何指定 SSO 系統管理員和分支機構系統管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="8b01b-118">How to Specify SSO Administrators and Affiliate Administrators Accounts</span></span>](../core/how-to-specify-sso-administrators-and-affiliate-administrators-accounts.md)  
  
-   [<span data-ttu-id="8b01b-119">管理分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="8b01b-119">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)  
  
-   [<span data-ttu-id="8b01b-120">管理使用者對應</span><span class="sxs-lookup"><span data-stu-id="8b01b-120">Managing User Mappings</span></span>](../core/managing-user-mappings.md)  
  
-   [<span data-ttu-id="8b01b-121">主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="8b01b-121">Host Initiated SSO</span></span>](../core/host-initiated-sso.md)