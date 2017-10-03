---
title: "維護 BizTalk Server2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b9c10d1-101b-4b9d-8eab-767b853f17d8
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2d1b171f0506d7855d5faf23f2ebea393d21f60
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="maintaining-biztalk-server2"></a><span data-ttu-id="cd6fb-102">維護 BizTalk Server2</span><span class="sxs-lookup"><span data-stu-id="cd6fb-102">Maintaining BizTalk Server2</span></span>
<span data-ttu-id="cd6fb-103">維護活動是服務監視和控制 (讓 SMC) 系統管理函式定義 Microsoft Operations Framework (MOF) 的一部分。</span><span class="sxs-lookup"><span data-stu-id="cd6fb-103">Maintenance activities are part of the Service Monitoring and Control (SMC) system management function as defined by the Microsoft Operations Framework (MOF).</span></span> <span data-ttu-id="cd6fb-104">讓 SMC 主要目標是要觀察的健全狀況程式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。</span><span class="sxs-lookup"><span data-stu-id="cd6fb-104">The primary goal of SMC is to observe the health of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system.</span></span> <span data-ttu-id="cd6fb-105">讓 SMC 檢查可能採取補救措施以避免潛在的服務事件，並發生時，將服務事件的影響降到最低。</span><span class="sxs-lookup"><span data-stu-id="cd6fb-105">SMC checks may initiate remedial actions to avoid potential service incidents and to minimize the impact of service incidents when they do occur.</span></span>  
  
 <span data-ttu-id="cd6fb-106">基於本指南的這個章節的目的，讓 SMC 活動分為四個三大類： 可靠性、 管理、 安全性及效能。</span><span class="sxs-lookup"><span data-stu-id="cd6fb-106">For the purposes of this section of the guide, SMC activities are divided into four three broad categories: reliability, administration, security, and performance.</span></span> <span data-ttu-id="cd6fb-107">每日、 每週和每月維護檢查清單來組織讓 SMC 檢查根據每項檢查應該執行的頻率。</span><span class="sxs-lookup"><span data-stu-id="cd6fb-107">The daily, weekly, and monthly maintenance checklists organize SMC checks according to how frequently each check should be performed.</span></span> <span data-ttu-id="cd6fb-108">如果讓 SMC 檢查指出不需要修復動作，檢查清單會引導您來解決問題的其他資訊來源。</span><span class="sxs-lookup"><span data-stu-id="cd6fb-108">If SMC checks indicate that remedial action is necessary, the checklists will direct you to sources of additional information to resolve the problem.</span></span>  
  
 <span data-ttu-id="cd6fb-109">解決可靠性相關的區段，管理、 安全性和效能問題包含的資訊來識別並解決期間遇到的許多常見的問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業。</span><span class="sxs-lookup"><span data-stu-id="cd6fb-109">The sections pertaining to resolving reliability, administration, security, and performance issues contain information about identifying and resolving many common problems encountered during [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] operations.</span></span>  
  
 <span data-ttu-id="cd6fb-110">如需 Microsoft Operations Framework 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?linkid=88047](http://go.microsoft.com/fwlink/?linkid=88047)。</span><span class="sxs-lookup"><span data-stu-id="cd6fb-110">For more information about the Microsoft Operations Framework, see [http://go.microsoft.com/fwlink/?linkid=88047](http://go.microsoft.com/fwlink/?linkid=88047).</span></span> <span data-ttu-id="cd6fb-111">如需服務的監視和控制函式的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=155341](http://go.microsoft.com/fwlink/?LinkId=155341)。</span><span class="sxs-lookup"><span data-stu-id="cd6fb-111">For more information about the Service Monitoring and Control function, see [http://go.microsoft.com/fwlink/?LinkId=155341](http://go.microsoft.com/fwlink/?LinkId=155341).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cd6fb-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="cd6fb-112">In This Section</span></span>  
  
-   [<span data-ttu-id="cd6fb-113">維護可靠性</span><span class="sxs-lookup"><span data-stu-id="cd6fb-113">Maintaining Reliability</span></span>](../technical-guides/maintaining-reliability.md)  
  
-   [<span data-ttu-id="cd6fb-114">系統管理的維護</span><span class="sxs-lookup"><span data-stu-id="cd6fb-114">Administrative Maintenance</span></span>](../technical-guides/administrative-maintenance.md)  
  
-   [<span data-ttu-id="cd6fb-115">維護效能</span><span class="sxs-lookup"><span data-stu-id="cd6fb-115">Maintaining Performance</span></span>](../technical-guides/maintaining-performance.md)  
  
-   [<span data-ttu-id="cd6fb-116">維護 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="cd6fb-116">Maintaining BizTalk Server Databases</span></span>](../technical-guides/maintaining-biztalk-server-databases.md)  
  
## <a name="related-sections"></a><span data-ttu-id="cd6fb-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="cd6fb-117">Related Sections</span></span>  
 [<span data-ttu-id="cd6fb-118">檢查清單： 執行每日維護檢查</span><span class="sxs-lookup"><span data-stu-id="cd6fb-118">Checklist: Performing Daily Maintenance Checks</span></span>](../technical-guides/checklist-performing-daily-maintenance-checks.md)  
  
 [<span data-ttu-id="cd6fb-119">檢查清單： 執行每週維護檢查</span><span class="sxs-lookup"><span data-stu-id="cd6fb-119">Checklist: Performing Weekly Maintenance Checks</span></span>](../technical-guides/checklist-performing-weekly-maintenance-checks.md)  
  
 [<span data-ttu-id="cd6fb-120">檢查清單： 執行每月維護檢查</span><span class="sxs-lookup"><span data-stu-id="cd6fb-120">Checklist: Performing Monthly Maintenance Checks</span></span>](../technical-guides/checklist-performing-monthly-maintenance-checks.md)