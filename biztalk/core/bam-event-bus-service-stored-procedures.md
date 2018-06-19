---
title: BAM 事件匯流排服務預存程序 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- stored procedures, Even Bus Service [BAM]
- Event Bus Service [BAM], stored procedures
ms.assetid: 18a7bd40-50ce-44f2-88ae-45a2e3c8d3f4
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f44dce10113b8a3a85b7c1dd177f637933b582ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230334"
---
# <a name="bam-event-bus-service-stored-procedures"></a><span data-ttu-id="68bdb-102">BAM 事件匯流排服務預存程序</span><span class="sxs-lookup"><span data-stu-id="68bdb-102">BAM Event Bus Service Stored Procedures</span></span>
<span data-ttu-id="68bdb-103">請使用下列預存程序管理 BAM 事件匯流排服務：</span><span class="sxs-lookup"><span data-stu-id="68bdb-103">You use the following stored procedures to manage the BAM Event Bus service:</span></span>  
  
-   <span data-ttu-id="68bdb-104">若要暫停 BAM 事件匯流排服務，請在 BAM 資料庫的交易中執行 TDDS_BlockTDDS 預存程序 (不認可交易)。</span><span class="sxs-lookup"><span data-stu-id="68bdb-104">To pause the BAM Event Bus service, execute the TDDS_BlockTDDS stored procedure within a transaction (without committing the transaction) on the BAM database.</span></span> <span data-ttu-id="68bdb-105">若要繼續 BAM 事件匯流排服務，請認可 TDDS_BlockTDDS 交易。</span><span class="sxs-lookup"><span data-stu-id="68bdb-105">To resume the BAM Event Bus service, commit the TDDS_BlockTDDS transaction.</span></span>  
  
-   <span data-ttu-id="68bdb-106">若要在多台電腦上啟用 BAM 事件匯流排服務，請識別要用於追蹤的主控件，然後將這些電腦加入追蹤主控件。</span><span class="sxs-lookup"><span data-stu-id="68bdb-106">To enable the BAM Event Bus service on multiple computers, identify which host(s) to use for tracking, and then join those computers to the tracking host.</span></span>  
  
-   <span data-ttu-id="68bdb-107">若要設定工作階段逾時和活動訊號間隔，請使用 TDDS_UpdateSettings 預存程序。</span><span class="sxs-lookup"><span data-stu-id="68bdb-107">To set up a session time-out and heartbeat interval, use the TDDS_UpdateSettings stored procedure.</span></span> <span data-ttu-id="68bdb-108">只有 BTS_ADMIN_USERS 群組的成員才具有執行這個預存程序的權限。</span><span class="sxs-lookup"><span data-stu-id="68bdb-108">Only members of the BTS_ADMIN_USERS group have permission to execute this stored procedure.</span></span>  
  
     <span data-ttu-id="68bdb-109">TDDS_UpdateSettings 預存程序包含下列參數：</span><span class="sxs-lookup"><span data-stu-id="68bdb-109">The TDDS_UpdateSettings stored procedure has the following parameters:</span></span>  
  
    -   <span data-ttu-id="68bdb-110">@RefreshIntervalint。設定為大於 60 秒。</span><span class="sxs-lookup"><span data-stu-id="68bdb-110">@RefreshInterval int. Set to greater than 60 seconds.</span></span>  
  
    -   <span data-ttu-id="68bdb-111">@SqlCommandTimeoutint。設定為小於 RefreshInterval。</span><span class="sxs-lookup"><span data-stu-id="68bdb-111">@SqlCommandTimeout int. Set to less than RefreshInterval.</span></span>  
  
    -   <span data-ttu-id="68bdb-112">@SessionTimeoutint。設定為大於 RefreshInterval 的兩倍。</span><span class="sxs-lookup"><span data-stu-id="68bdb-112">@SessionTimeout int. Set to greater than two times the RefreshInterval.</span></span>  
  
    -   <span data-ttu-id="68bdb-113">@EventLoggingIntervalnvarchar(16)。</span><span class="sxs-lookup"><span data-stu-id="68bdb-113">@EventLoggingInterval nvarchar(16).</span></span> <span data-ttu-id="68bdb-114">設定為大於 60 秒。</span><span class="sxs-lookup"><span data-stu-id="68bdb-114">Set to greater than 60 seconds.</span></span>  
  
    -   <span data-ttu-id="68bdb-115">@RetryCountint。設定為大於 60 秒。</span><span class="sxs-lookup"><span data-stu-id="68bdb-115">@RetryCount int. Set to greater than 60 seconds</span></span>  
  
    -   <span data-ttu-id="68bdb-116">@ThreadPerSessionint。此參數已經過時。</span><span class="sxs-lookup"><span data-stu-id="68bdb-116">@ThreadPerSession int. This parameter is obsolete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68bdb-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68bdb-117">See Also</span></span>  
 [<span data-ttu-id="68bdb-118">管理 BAM</span><span class="sxs-lookup"><span data-stu-id="68bdb-118">Managing BAM</span></span>](../core/managing-bam.md)