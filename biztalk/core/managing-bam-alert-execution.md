---
title: 管理 BAM 警示執行 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [BAM definitions], executing alerts
- Notification Services, configuration files
- BAM Management utility
- alerts, executing
ms.assetid: 44bb738e-fa2c-4b32-9e8d-e756d6c3778e
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d8dca3f99480b6875253eb6aca102977935160b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021980"
---
# <a name="managing-bam-alert-execution"></a><span data-ttu-id="98a54-102">管理 BAM 警示的執行</span><span class="sxs-lookup"><span data-stu-id="98a54-102">Managing BAM Alert Execution</span></span>
<span data-ttu-id="98a54-103">您可以透過三種途徑修改 BAM 警示的執行：BAM 入口網站、BAM 管理公用程式和 ProcessBamNSFiles.vbs 指令碼。</span><span class="sxs-lookup"><span data-stu-id="98a54-103">BAM Alert execution can be modified through three avenues, The BAM Portal, the BAM management utility, and the ProcessBamNSFiles.vbs script.</span></span>  
  
## <a name="bam-portal"></a><span data-ttu-id="98a54-104">BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="98a54-104">BAM Portal</span></span>  
 <span data-ttu-id="98a54-105">知識工作者和系統管理員可以使用 BAM 入口網站中的警示管理員修改警示的傳遞方式。</span><span class="sxs-lookup"><span data-stu-id="98a54-105">Knowledge workers and administrators can modify the manner in which alerts are delivered by using the Alert Manager in the BAM portal.</span></span> <span data-ttu-id="98a54-106">透過 BAM 入口網站可以啟用或停用警示，並可修改閾值層級、傳遞位置以及影響警示執行的其他參數。</span><span class="sxs-lookup"><span data-stu-id="98a54-106">From the BAM portal, the Alert can be enabled or disabled, threshold levels can be modified, delivery locations can be modified, as well as other parameters the affect the execution of the alert.</span></span>  
  
 <span data-ttu-id="98a54-107">如需有關如何修改警示的詳細資訊，請參閱 < [BAM 入口網站頁面上的警示管理員](../core/alert-manager-on-the-bam-portal-page.md)並[BAM 入口網站中的警示](../core/alerts-in-the-bam-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="98a54-107">For more information on modifying alerts, see [Alert Manager on the BAM Portal Page](../core/alert-manager-on-the-bam-portal-page.md) and [Alerts in the BAM Portal](../core/alerts-in-the-bam-portal.md).</span></span>  
  
### <a name="bam-management-utility"></a><span data-ttu-id="98a54-108">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="98a54-108">BAM Management Utility</span></span>  
 <span data-ttu-id="98a54-109">系統管理員可以使用 BAM 管理公用程式啟用、停用和移除警示。</span><span class="sxs-lookup"><span data-stu-id="98a54-109">Administrators can use the BAM Management utility to enable, disable, and remove alerts.</span></span>  
  
 <span data-ttu-id="98a54-110">如需有關使用 BAM 管理公用程式管理警示的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="98a54-110">For information on using the BAM Management Utility to mange alerts, the following topics:</span></span>  
  
-   [<span data-ttu-id="98a54-111">如何啟用警示</span><span class="sxs-lookup"><span data-stu-id="98a54-111">How to Enable Alerts</span></span>](../core/how-to-enable-alerts.md) 
  
-   [<span data-ttu-id="98a54-112">如何停用警示</span><span class="sxs-lookup"><span data-stu-id="98a54-112">How to Disable Alerts</span></span>](../core/how-to-disable-alerts.md)  
  
-   [<span data-ttu-id="98a54-113">如何移除 BAM 警示</span><span class="sxs-lookup"><span data-stu-id="98a54-113">How to Remove BAM Alerts</span></span>](../core/how-to-remove-bam-alerts.md)  
  
### <a name="modifying-notification-services-configuration-files"></a><span data-ttu-id="98a54-114">修改 Notification Services 組態檔</span><span class="sxs-lookup"><span data-stu-id="98a54-114">Modifying Notification Services Configuration Files</span></span>  
 <span data-ttu-id="98a54-115">系統管理員可以使用 ProcessBamNSFiles.vbs 指令碼，變更 Notification Services 傳遞警示的方式。</span><span class="sxs-lookup"><span data-stu-id="98a54-115">Administrators can use the ProcessBamNSFiles.vbs script to change the manner in which the Notification Services delivers alerts.</span></span> <span data-ttu-id="98a54-116">Notification services 的相關資訊的應用程式定義檔 (ADF)，請參閱[ http://go.microsoft.com/fwlink/?LinkId=127016 ](http://go.microsoft.com/fwlink/?LinkId=127016)。</span><span class="sxs-lookup"><span data-stu-id="98a54-116">For more information the Application Definition File (ADF) for Notification Services, see [http://go.microsoft.com/fwlink/?LinkId=127016](http://go.microsoft.com/fwlink/?LinkId=127016).</span></span>  
  
 <span data-ttu-id="98a54-117">若要修改與 BAM 關聯的 ADF，請依照下列一般步驟執行：</span><span class="sxs-lookup"><span data-stu-id="98a54-117">To modify the ADF associated with BAM you can follow these general steps:</span></span>  
  
1. <span data-ttu-id="98a54-118">執行指令碼以取得目前組態和 ADF 檔案。</span><span class="sxs-lookup"><span data-stu-id="98a54-118">Run the script to obtain the current configuration and ADF files.</span></span>  
  
2. <span data-ttu-id="98a54-119">修改檔案。</span><span class="sxs-lookup"><span data-stu-id="98a54-119">Modify the files.</span></span>  
  
3. <span data-ttu-id="98a54-120">執行指令碼以套用變更。</span><span class="sxs-lookup"><span data-stu-id="98a54-120">Run the script to apply the changes.</span></span>  
  
   <span data-ttu-id="98a54-121">如需 ProcessBamNSFiles.vbs 指令碼的詳細資訊，請參閱[通知服務組態檔的 BAM 命令列指令碼](../core/bam-command-line-script-for-notification-services-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="98a54-121">For more information on the ProcessBamNSFiles.vbs script, see [BAM Command-Line Script for Notification Services Configuration Files](../core/bam-command-line-script-for-notification-services-configuration-files.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98a54-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98a54-122">See Also</span></span>  
 <span data-ttu-id="98a54-123">[管理 BAM 入口網站](../core/managing-the-bam-portal.md) </span><span class="sxs-lookup"><span data-stu-id="98a54-123">[Managing the BAM Portal](../core/managing-the-bam-portal.md) </span></span>  
 <span data-ttu-id="98a54-124">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="98a54-124">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 [<span data-ttu-id="98a54-125">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="98a54-125">BAM Management Utility</span></span>](../core/bam-management-utility.md)