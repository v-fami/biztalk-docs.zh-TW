---
title: 監視磁碟空間使用量 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ac68022-a9c5-4eb9-8854-cd1ee849282b
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ae87de0b00e70ae03a30dd8ef20ede4a972388d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298590"
---
# <a name="monitoring-disk-space-usage"></a><span data-ttu-id="56a4b-102">監視磁碟空間使用量</span><span class="sxs-lookup"><span data-stu-id="56a4b-102">Monitoring Disk Space Usage</span></span>
<span data-ttu-id="56a4b-103">監視的程序的操作整備[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，監視的磁碟空間使用量，如下所示：</span><span class="sxs-lookup"><span data-stu-id="56a4b-103">As part of the monitoring process for operational readiness of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], monitor the disk space usage as follows:</span></span>  
  
-   <span data-ttu-id="56a4b-104">**判斷磁碟所需的空間。**</span><span class="sxs-lookup"><span data-stu-id="56a4b-104">**Determine the disk space required.**</span></span>  
  
     <span data-ttu-id="56a4b-105">當使用檔案或 MSMQ 傳送 / 接收位置時，請確認有足夠的磁碟空間可容納的中斷[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或接收的系統。</span><span class="sxs-lookup"><span data-stu-id="56a4b-105">When using File or MSMQ send / receive locations, ensure that there is ample disk space available to accommodate outages of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or of the receiving systems.</span></span> <span data-ttu-id="56a4b-106">例如，如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在 SAN 上的寫入檔案到共用，並接收系統已關閉，有兩天，判斷是否有足夠的磁碟空間，以允許將排入佇列檔案。</span><span class="sxs-lookup"><span data-stu-id="56a4b-106">For example, if [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is writing files to a share on a SAN and the receiving system is down for two days, determine whether there is enough disk space to allow the files to queue up.</span></span>  
  
-   <span data-ttu-id="56a4b-107">**定期清除 BizTalk Server 的備份檔案的目錄。**</span><span class="sxs-lookup"><span data-stu-id="56a4b-107">**Clean up the BizTalk Server backup files directory periodically.**</span></span>  
  
     <span data-ttu-id="56a4b-108">您可以執行此清除使用呼叫 SQL Server Agent 作業的指令碼。</span><span class="sxs-lookup"><span data-stu-id="56a4b-108">You can perform this cleanup using a script called from a SQL Server Agent job.</span></span>  
  
-   <span data-ttu-id="56a4b-109">**定期清除 BizTalk 追蹤資料庫封存檔案目錄。**</span><span class="sxs-lookup"><span data-stu-id="56a4b-109">**Clean up the BizTalk Tracking database archive files directory periodically.**</span></span>  
  
-   <span data-ttu-id="56a4b-110">**請確認有足夠的磁碟空間可容納更大的 BizTalk Server 資料庫 (.mdf) 和交易記錄 (.ldf) 檔案，在尖峰資料流程的時間。**</span><span class="sxs-lookup"><span data-stu-id="56a4b-110">**Ensure that there is sufficient disk space available to accommodate larger BizTalk Server database (.mdf) and transaction log (.ldf) files during times of peak data flow.**</span></span>