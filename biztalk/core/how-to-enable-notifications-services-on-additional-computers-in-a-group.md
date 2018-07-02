---
title: 如何在群組中的其他電腦上啟用 Notifications Services |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 571d6b45-b0cc-47f2-bed3-7c6f3e70decc
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fd8a1a49be2416fb8b7fe5d160dd5228a95e94f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983391"
---
# <a name="how-to-enable-notifications-services-on-additional-computers-in-a-group"></a><span data-ttu-id="1b4d6-102">如何在群組中的其他電腦啟用 Notification Services</span><span class="sxs-lookup"><span data-stu-id="1b4d6-102">How to Enable Notifications Services on Additional Computers In A Group</span></span>
<span data-ttu-id="1b4d6-103">當執行 BAM 時在多重電腦環境中，您必須啟用 Notification Services，您將會用來執行 BAM 管理公用程式來部署活動的每一部電腦上。</span><span class="sxs-lookup"><span data-stu-id="1b4d6-103">When running BAM in a multi-computer environment, you must enable Notification Services on each computer on which you will run the BAM Management Utility to deploy an activity.</span></span>  
  
 <span data-ttu-id="1b4d6-104">請考慮下列案例：</span><span class="sxs-lookup"><span data-stu-id="1b4d6-104">Consider the following scenario:</span></span>  
  
- <span data-ttu-id="1b4d6-105">群組 A 包含下列電腦：</span><span class="sxs-lookup"><span data-stu-id="1b4d6-105">Group A consists of the following computers:</span></span>  
  
  - <span data-ttu-id="1b4d6-106">電腦 1 當做 BAM 管理電腦。</span><span class="sxs-lookup"><span data-stu-id="1b4d6-106">Computer 1 is used as a BAM administration computer.</span></span>  
  
  - <span data-ttu-id="1b4d6-107">電腦 2 裝載 BAM PIT 和「星狀結構描述」資料庫。</span><span class="sxs-lookup"><span data-stu-id="1b4d6-107">Computer 2 hosts the BAM PIT and Star Schema database.</span></span>  
  
  - <span data-ttu-id="1b4d6-108">電腦 3 裝載 BAM「封存」和「分析」資料庫。</span><span class="sxs-lookup"><span data-stu-id="1b4d6-108">Computer 3 hosts the BAM Archive and Analysis databases.</span></span>  
  
  - <span data-ttu-id="1b4d6-109">電腦 4 裝載 BAM「警示」資料庫。</span><span class="sxs-lookup"><span data-stu-id="1b4d6-109">Computer 4 hosts the BAM Alerts database.</span></span>  
  
  - <span data-ttu-id="1b4d6-110">電腦 5 裝載其餘的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="1b4d6-110">Computer 5 hosts the rest of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span>  
  
- <span data-ttu-id="1b4d6-111">群組 B：</span><span class="sxs-lookup"><span data-stu-id="1b4d6-111">Group B:</span></span>  
  
  -   <span data-ttu-id="1b4d6-112">電腦 6 當做 BAM 管理電腦，其所有資料庫與群組 A 共用。</span><span class="sxs-lookup"><span data-stu-id="1b4d6-112">Computer 6 is used as a BAM administration computer on which all the databases are shared with Group A.</span></span>  
  
  <span data-ttu-id="1b4d6-113">若要從群組 B 的電腦將活動部署至群組 A 的資料庫，您必須在裝載告知服務的 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 註冊 Notification Services。</span><span class="sxs-lookup"><span data-stu-id="1b4d6-113">To be able to deploy an activity to the databases in group A from the computer in group B, you must first register the Notification Services with the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] hosting the notifications services.</span></span> <span data-ttu-id="1b4d6-114">如果未註冊 Notification Service，您將會收到下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="1b4d6-114">If the Notification Services are not registered, you will receive the following error:</span></span>  
  
  <span data-ttu-id="1b4d6-115">正在部署警示...錯誤： BAM 部署失敗。</span><span class="sxs-lookup"><span data-stu-id="1b4d6-115">Deploying Alert... ERROR: The BAM deployment failed.</span></span>  
  
  <span data-ttu-id="1b4d6-116">未部署警示。</span><span class="sxs-lookup"><span data-stu-id="1b4d6-116">The alerts were not deployed.</span></span>  
  
  <span data-ttu-id="1b4d6-117">引動過程的目標傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1b4d6-117">Exception has been thrown by the target of an invocation.</span></span>  
  
  <span data-ttu-id="1b4d6-118">找不到指定的 Notification Services 執行個體的登錄項目。</span><span class="sxs-lookup"><span data-stu-id="1b4d6-118">The registry entries for the specified instance of Notification Services could not be found.</span></span>  
  
### <a name="to-register-notifications-services-additional-computers"></a><span data-ttu-id="1b4d6-119">在其他電腦中註冊 Notification Services</span><span class="sxs-lookup"><span data-stu-id="1b4d6-119">To register notifications services additional computers</span></span>  
  
1.  <span data-ttu-id="1b4d6-120">在電腦上的其他群組中，按一下**開始**，指向**所有程式**，按一下  **Microsoft SQL Server 2005**，按一下 **組態工具**，然後按一下**Notification Services 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="1b4d6-120">On the computer in the additional group, click **Start**, point to **All Programs**, click **Microsoft SQL Server 2005**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="1b4d6-121">在命令提示字元中，輸入： **nscontrol register-名稱\<NS 前置詞的名稱，在設定選擇\>-伺服器\<ns db 的 sql server\>**。</span><span class="sxs-lookup"><span data-stu-id="1b4d6-121">At the command prompt, type: **nscontrol register -name \<NS Prefix name chosen at config\> -server \<ns db sql server\>**.</span></span> <span data-ttu-id="1b4d6-122">這樣可以讓 Notification Services 登入正確的資料庫 (這項資訊是在服務電腦的登錄中由 nscontrol 執行維護)。</span><span class="sxs-lookup"><span data-stu-id="1b4d6-122">This enables Notification Services to log on to the correct database (this information is maintained in the registry of the service machine by nscontrol).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b4d6-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b4d6-123">See Also</span></span>  
 <span data-ttu-id="1b4d6-124">[變更 BAM 執行階段設定](../core/changing-bam-runtime-settings.md) </span><span class="sxs-lookup"><span data-stu-id="1b4d6-124">[Changing BAM Runtime Settings](../core/changing-bam-runtime-settings.md) </span></span>  
 [<span data-ttu-id="1b4d6-125">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="1b4d6-125">BAM Management Utility</span></span>](../core/bam-management-utility.md)