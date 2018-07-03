---
title: 執行身分設定檔 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98ac0a0c-91d8-4d12-aa40-2ad2e29ec784
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a1281fa77956d96e4461a91fffb737499327ef2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982087"
---
# <a name="run-as-profiles"></a><span data-ttu-id="7c9ea-102">執行身分設定檔</span><span class="sxs-lookup"><span data-stu-id="7c9ea-102">Run As Profiles</span></span>
<span data-ttu-id="7c9ea-103">第一次匯入 BizTalk Server 核心程式庫管理組件時，它會建立兩個新執行身分設定檔：</span><span class="sxs-lookup"><span data-stu-id="7c9ea-103">When the BizTalk Server Core Library Management Pack is first imported, it creates two new Run As Profiles:</span></span>  
  
- <span data-ttu-id="7c9ea-104">**BizTalk Server 探索帳戶**。</span><span class="sxs-lookup"><span data-stu-id="7c9ea-104">**BizTalk Server Discovery Account**.</span></span> <span data-ttu-id="7c9ea-105">此設定檔是與 BizTalk Server 角色元件的所有探索相關聯。</span><span class="sxs-lookup"><span data-stu-id="7c9ea-105">This profile is associated with all discoveries of BizTalk Server role components.</span></span>  
  
- <span data-ttu-id="7c9ea-106">**BizTalk Server 監視帳戶**。</span><span class="sxs-lookup"><span data-stu-id="7c9ea-106">**BizTalk Server Monitoring Account**.</span></span> <span data-ttu-id="7c9ea-107">此設定檔與所有監視器和工作有關聯。</span><span class="sxs-lookup"><span data-stu-id="7c9ea-107">This profile is associated with all monitors and tasks.</span></span>  
  
  <span data-ttu-id="7c9ea-108">根據預設，所有探索、 監視器和 BizTalk Server 管理組件預設都會使用 「 預設動作帳戶 」 執行身分設定檔中定義的帳戶中定義的工作。</span><span class="sxs-lookup"><span data-stu-id="7c9ea-108">By default, all discoveries, monitors, and tasks defined in the BizTalk Server Management Packs default to using the accounts defined in the “Default Action Account” Run As Profile.</span></span>  <span data-ttu-id="7c9ea-109">如果指定系統的預設動作帳戶沒有探索或監視 BizTalk 的必要權限，然後這些系統可以繫結到 BizTalk Server 執行身分設定檔中確實具備存取 BizTalk Server 的更為專屬認證。</span><span class="sxs-lookup"><span data-stu-id="7c9ea-109">If the default action account for a given system does not have the necessary permissions to discover or monitor BizTalk, then those systems can be bound to more specific credentials in the BizTalk Server Run As Profiles, which do have access to BizTalk Server.</span></span>  
  
  <span data-ttu-id="7c9ea-110">若要設定 BizTalk server 的執行身分設定檔的一般步驟如下：</span><span class="sxs-lookup"><span data-stu-id="7c9ea-110">The following are the generic steps to configure Run As Profiles for BizTalk Server:</span></span>  
  
### <a name="to-configure-run-as-profiles"></a><span data-ttu-id="7c9ea-111">若要設定執行身分設定檔</span><span class="sxs-lookup"><span data-stu-id="7c9ea-111">To configure Run As profiles</span></span>  
  
1.  <span data-ttu-id="7c9ea-112">識別預設動作帳戶沒有足夠的權限，來監控 BizTalk Server 的其中的目標電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="7c9ea-112">Identify the name(s) of the target computer(s) where the default action account has insufficient rights to monitor BizTalk Server.</span></span>  
  
2.  <span data-ttu-id="7c9ea-113">每個系統建立或使用現有的一組認證至少具有中所討論的 BizTalk Server 權限[低權限環境](../technical-guides/low-privilege-environments.md)區段，此管理組件指南。</span><span class="sxs-lookup"><span data-stu-id="7c9ea-113">For each system create or use an existing set of credentials that have at least the BizTalk Server privileges discussed in the [Low-Privilege Environments](../technical-guides/low-privilege-environments.md) section of this management pack guide.</span></span>  
  
3.  <span data-ttu-id="7c9ea-114">每一組步驟 2 中識別的認證，請確定管理群組中存在對應的執行身分帳戶。</span><span class="sxs-lookup"><span data-stu-id="7c9ea-114">For each set of credentials identified in step 2, make sure that a corresponding Run As Account exists in the management group.</span></span> <span data-ttu-id="7c9ea-115">如有必要，請建立執行身分帳戶。</span><span class="sxs-lookup"><span data-stu-id="7c9ea-115">Create the Run As Account if it is necessary.</span></span>  
  
4.  <span data-ttu-id="7c9ea-116">在 [設定目標和執行身分帳戶之間的對應**執行身分帳戶**的每個執行身分設定檔] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7c9ea-116">Set up the mappings between the targets and the Run As Account(s) on the **Run As Accounts** tab of each of the Run As Profiles.</span></span>