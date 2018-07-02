---
title: 備份檔案損毀 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48197c-944a-4f0a-ba01-8e1d91c88ad3
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5947b527dea1206255daf52f128569fd7a4f659c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987911"
---
# <a name="corrupt-backup-files"></a><span data-ttu-id="622bb-102">備份檔案損毀</span><span class="sxs-lookup"><span data-stu-id="622bb-102">Corrupt Backup Files</span></span>
<span data-ttu-id="622bb-103">備份檔案可能損毀、 已損毀或遺失。</span><span class="sxs-lookup"><span data-stu-id="622bb-103">A backup file may become corrupt, damaged, or missing.</span></span> <span data-ttu-id="622bb-104">如果發生這種情況，就無法還原至少一個檔案。</span><span class="sxs-lookup"><span data-stu-id="622bb-104">If this occurs, at least one file cannot be restored.</span></span> <span data-ttu-id="622bb-105">發生失敗的系統上的還原作業會搜尋下一個有效的完整備份組。</span><span class="sxs-lookup"><span data-stu-id="622bb-105">The restore job on the system that suffered the failure searches for the next valid full backup set.</span></span> <span data-ttu-id="622bb-106">在大部分情況下它必須在來源系統上強制進行完整備份。</span><span class="sxs-lookup"><span data-stu-id="622bb-106">In most cases it will be necessary to force a full backup on the source system.</span></span> <span data-ttu-id="622bb-107">如果沒有這樣的集合存在，還原作業失敗，直到抵達有效的完整備份集，每個後續的執行也會失敗。</span><span class="sxs-lookup"><span data-stu-id="622bb-107">If no such set exists, the restore job fails and each subsequent run also fails until a valid full backup set arrives.</span></span> <span data-ttu-id="622bb-108">如果一組不存在，它用來修復環境。</span><span class="sxs-lookup"><span data-stu-id="622bb-108">If a set does exist, it is used to repair the environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="622bb-109">因為方法[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]將備份資料寫入至檔案，就可以，[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]會報告已成功完成，即使實際將資料寫入期間備份失敗。</span><span class="sxs-lookup"><span data-stu-id="622bb-109">Due to the manner in which [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] writes backup data to a file, it is possible that [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] will report successful completion even if the backup failed during the actual writing of the data.</span></span> <span data-ttu-id="622bb-110">要寫入的磁碟不是本機電腦和網路失敗或發生中斷時，主要是就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="622bb-110">This scenario primarily occurs when the disk being written to is not local to the computer and a network failure or interruption occurs.</span></span> <span data-ttu-id="622bb-111">基於一般考量，如果備份作業執行時，就會發生網路失敗，強制進行完整備份之後解決網路連線問題。</span><span class="sxs-lookup"><span data-stu-id="622bb-111">As a general precaution, if a network failure occurs while the backup job is running, force a full backup after the network connectivity problem is resolved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="622bb-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="622bb-112">See Also</span></span>  
 [<span data-ttu-id="622bb-113">針對記錄傳送進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="622bb-113">Troubleshooting Log Shipping</span></span>](../technical-guides/troubleshooting-log-shipping.md)