---
title: 分散式系統問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 287b0adb-d5f9-4e47-80f8-0ba5d90c7864
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24abe471a66e8bc0724ad731388c5a0e7c07b573
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22297750"
---
# <a name="distributed-system-problems"></a><span data-ttu-id="9bf3e-102">分散式的系統問題</span><span class="sxs-lookup"><span data-stu-id="9bf3e-102">Distributed System Problems</span></span>
<span data-ttu-id="9bf3e-103">分散式的目的系統中的還原作業並不知道的錯誤或其他電腦上的問題。</span><span class="sxs-lookup"><span data-stu-id="9bf3e-103">In a distributed destination system the restore jobs are not aware of errors or problems on the other computers.</span></span> <span data-ttu-id="9bf3e-104">例如，假設電腦 A 正在還原 BizTalk 管理資料庫和 BizTalk 追蹤資料庫，而且電腦 B 正在還原 BizTalk MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9bf3e-104">For example, suppose that computer A is restoring the BizTalk Management database and the BizTalk Tracking database, and computer B is restoring the BizTalk MessageBox database.</span></span> <span data-ttu-id="9bf3e-105">這兩部電腦已成功還原備份組 1 至 25。</span><span class="sxs-lookup"><span data-stu-id="9bf3e-105">Both computers successfully restore backup sets 1 through 25.</span></span> <span data-ttu-id="9bf3e-106">設定 26，不過，有損毀的記錄備份檔案的 BizTalk MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9bf3e-106">Set 26, however, has a corrupted log backup file of the BizTalk MessageBox database.</span></span> <span data-ttu-id="9bf3e-107">電腦 A 正確還原其資料庫，但電腦 B 無法還原損毀的檔案。</span><span class="sxs-lookup"><span data-stu-id="9bf3e-107">Computer A restores its databases correctly but computer B fails to restore the corrupted file.</span></span>  
  
 <span data-ttu-id="9bf3e-108">在此情況下，請在來源系統上強制進行完整備份。</span><span class="sxs-lookup"><span data-stu-id="9bf3e-108">In this situation, force a full backup on the source system.</span></span> <span data-ttu-id="9bf3e-109">接續上例，假設已診斷的問題，並建立完整備份組 35。</span><span class="sxs-lookup"><span data-stu-id="9bf3e-109">Continuing the example above, assume that the problem was diagnosed and a full backup was created for set 35.</span></span> <span data-ttu-id="9bf3e-110">直到它看到完整備份集 35 及後續的記錄備份組 （請記住，就必須一律是一組一個後續的完整記錄備份要還原的 36 電腦 A 則還原集 26 到 34，因為它並不知道電腦 B 的電腦上的問題將會失敗d) 中。</span><span class="sxs-lookup"><span data-stu-id="9bf3e-110">Computer A then restores sets 26 to 34, because it is not aware of the problem on Computer B. Computer B will fail until it sees full backup set 35 and subsequent log backup set 36 (remember that there must always be one subsequent complete log backup for a set to be restored).</span></span> <span data-ttu-id="9bf3e-111">集合 35 及 36 到達時在電腦 B 上，它將會修復使用 35 本身。</span><span class="sxs-lookup"><span data-stu-id="9bf3e-111">When sets 35 and 36 arrive on computer B, it will repair itself using 35.</span></span> <span data-ttu-id="9bf3e-112">修復完成後，電腦 A 和 B 會同步。</span><span class="sxs-lookup"><span data-stu-id="9bf3e-112">After the repair is complete, computer A and B will be in sync.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bf3e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bf3e-113">See Also</span></span>  
 [<span data-ttu-id="9bf3e-114">疑難排解記錄傳送</span><span class="sxs-lookup"><span data-stu-id="9bf3e-114">Troubleshooting Log Shipping</span></span>](../technical-guides/troubleshooting-log-shipping.md)