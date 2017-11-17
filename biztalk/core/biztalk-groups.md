---
title: "BizTalk 群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Management database, groups
- groups
- groups, Management database
- groups, about groups
ms.assetid: 197cbcf6-c722-4cbb-9642-3cb8a34757e2
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b9cd38012f0e2a7ba5f4cfcb56ae63678aacbf8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-groups"></a><span data-ttu-id="e638c-102">BizTalk 群組</span><span class="sxs-lookup"><span data-stu-id="e638c-102">BizTalk Groups</span></span>

## <a name="overview"></a><span data-ttu-id="e638c-103">概觀</span><span class="sxs-lookup"><span data-stu-id="e638c-103">Overview</span></span>
<span data-ttu-id="e638c-104">*BizTalk 群組*是通常代表企業、 部門、 集線器或需要包含的 BizTalk Server 實作其他業務單位的組織單位。</span><span class="sxs-lookup"><span data-stu-id="e638c-104">The *BizTalk group* is a unit of organization that usually represents an enterprise, department, hub, or other business unit that requires a contained BizTalk Server implementation.</span></span> <span data-ttu-id="e638c-105">BizTalk 群組與 BizTalk Server 管理資料庫 (在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 是為 BizTalk Server 組態資料庫) 有一對一的關係。</span><span class="sxs-lookup"><span data-stu-id="e638c-105">The BizTalk group has a one-to-one relationship with a BizTalk Server Management database (known as the BizTalk Server Configuration database in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e638c-106">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組可包含多部 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦，但任一部指定的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦只能與單一 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組關聯。</span><span class="sxs-lookup"><span data-stu-id="e638c-106">While [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groups may contain multiple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers, any given [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer may only be associated with a single [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group.</span></span>  
  
 <span data-ttu-id="e638c-107">「BizTalk 管理」資料庫會儲存 BizTalk 群組及該群組中 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="e638c-107">The BizTalk Management database stores configuration information for the BizTalk group and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers in that group.</span></span> <span data-ttu-id="e638c-108">此組態資訊指定伺服器的訊息處理邏輯部分以及該邏輯將實際執行的地方。</span><span class="sxs-lookup"><span data-stu-id="e638c-108">This configuration information specifies part of the message-processing logic for the servers and where this logic will physically run.</span></span> <span data-ttu-id="e638c-109">如需有關 BizTalk Server 管理資料庫的詳細資訊，請參閱[BizTalk Server 中的資料庫](../core/databases-in-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e638c-109">For more information about the BizTalk Server Management database, see [Databases in BizTalk Server](../core/databases-in-biztalk-server.md).</span></span>  
  
 <span data-ttu-id="e638c-110">對群組中每個伺服器安裝必須指定相同的 BizTalk Server 管理資料庫，如此即可從管理主控台管理每個伺服器。</span><span class="sxs-lookup"><span data-stu-id="e638c-110">You must specify the same BizTalk Server Management database for each server installation in the group so that you can administer each server from the administration console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e638c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e638c-111">See Also</span></span>  
 <span data-ttu-id="e638c-112">[設定 BizTalk Server](../install-and-config-guides/configure-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="e638c-112">[Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md) </span></span>  
 <span data-ttu-id="e638c-113">[管理群組](../core/managing-groups.md) </span><span class="sxs-lookup"><span data-stu-id="e638c-113">[Managing Groups](../core/managing-groups.md) </span></span>  
 [<span data-ttu-id="e638c-114">實體</span><span class="sxs-lookup"><span data-stu-id="e638c-114">Entities</span></span>](../core/entities.md)