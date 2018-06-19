---
title: 部分備份集 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9f15c0-4d31-4322-ac0a-8efdeed6f71e
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9740cb0f45d6bb46c13a95e50e4717ef142b164
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298158"
---
# <a name="partial-backup-sets"></a><span data-ttu-id="53410-102">部分備份集</span><span class="sxs-lookup"><span data-stu-id="53410-102">Partial Backup Sets</span></span>
<span data-ttu-id="53410-103">當資料庫分別備份在來源系統上，該部分備份組中的結果，可能發生問題。</span><span class="sxs-lookup"><span data-stu-id="53410-103">When backing up the databases on the source system, problems may occur that result in a partial backup set.</span></span> <span data-ttu-id="53410-104">當發生這種情況時，Master.dbo.bts_LogShippingHistory 資料表會包含 0 **SetComplete**集中的所有記錄的資料行。</span><span class="sxs-lookup"><span data-stu-id="53410-104">When this occurs, the Master.dbo.bts_LogShippingHistory table will contain a 0 in the **SetComplete** column for all records in the set.</span></span>  
  
 <span data-ttu-id="53410-105">無法還原這些設定。</span><span class="sxs-lookup"><span data-stu-id="53410-105">These sets cannot be restored.</span></span> <span data-ttu-id="53410-106">如此一來記錄備份組鏈結已中斷。</span><span class="sxs-lookup"><span data-stu-id="53410-106">As a result the log backup set chain is broken.</span></span> <span data-ttu-id="53410-107">必須忽略集，以及所有記錄備份組之後，至下一個完整備份集。</span><span class="sxs-lookup"><span data-stu-id="53410-107">The set must be ignored, as well as all log backup sets after it, up to the next full backup set.</span></span> <span data-ttu-id="53410-108">還原作業會自動尋找下一個有效的完整備份組。</span><span class="sxs-lookup"><span data-stu-id="53410-108">The restore job will automatically look for the next valid full backup set.</span></span> <span data-ttu-id="53410-109">如果它找不到其中一個，它會失敗，並將還原的設定，才能修復目的地環境。</span><span class="sxs-lookup"><span data-stu-id="53410-109">If it does not find one, it fails and restores that set in order to repair the destination environment.</span></span>  
  
 <span data-ttu-id="53410-110">在大部分情況下來源系統會偵測部分備份組已發生，並會自動產生完整備份集，在下一次執行如果它被設定為執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="53410-110">In most cases the source system will detect that a partial backup set has occurred and will automatically produce a full backup set the next time it runs if it is configured to do so.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="53410-111">發生此問題最常見的原因是在目的系統上的檔案群組的磁碟空間不足。</span><span class="sxs-lookup"><span data-stu-id="53410-111">The most common cause of this problem is insufficient disk space for the file groups on the destination system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53410-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53410-112">See Also</span></span>  
 [<span data-ttu-id="53410-113">疑難排解記錄傳送</span><span class="sxs-lookup"><span data-stu-id="53410-113">Troubleshooting Log Shipping</span></span>](../technical-guides/troubleshooting-log-shipping.md)