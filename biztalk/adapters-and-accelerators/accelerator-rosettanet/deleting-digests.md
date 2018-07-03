---
title: 刪除摘要 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deleting, digests
- messages, digests
- digests
- databases, deleting digests
- maintaining databases, deleting digests
ms.assetid: bcc7cb11-2f6a-4996-ad50-040d41993e09
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10e32f8d86d6723965e8a27ad51f7551fdda0b60
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002399"
---
# <a name="deleting-digests"></a><span data-ttu-id="682d6-102">刪除摘要</span><span class="sxs-lookup"><span data-stu-id="682d6-102">Deleting Digests</span></span>
<span data-ttu-id="682d6-103">Microsoft[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]儲存外寄訊息的摘要，因此它可以針對訊號內容驗證它們。</span><span class="sxs-lookup"><span data-stu-id="682d6-103">Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] stores digests for outgoing messages, so it can validate them against signal content.</span></span> <span data-ttu-id="682d6-104">不過，驗證後，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 並不會刪除摘要。</span><span class="sxs-lookup"><span data-stu-id="682d6-104">However, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not delete the digests after validation.</span></span> <span data-ttu-id="682d6-105">您可能需要定期刪除這些摘要，以維護系統效能。</span><span class="sxs-lookup"><span data-stu-id="682d6-105">Periodically, you may want to delete these digests to maintain system performance.</span></span>  
  
## <a name="when-and-how-to-delete-digests"></a><span data-ttu-id="682d6-106">刪除摘要的時機與方法</span><span class="sxs-lookup"><span data-stu-id="682d6-106">When and How to Delete Digests</span></span>  
 <span data-ttu-id="682d6-107">摘要是儲存在 BTARNDATA 資料庫的 MessageDigestHelper 資料表中。</span><span class="sxs-lookup"><span data-stu-id="682d6-107">Digests are stored in the MessageDigestHelper table of the BTARNDATA database.</span></span> <span data-ttu-id="682d6-108">您可能需要定期使用預存程序，刪除某一特定時段以前的摘要，藉此從資料表中刪除這些摘要。</span><span class="sxs-lookup"><span data-stu-id="682d6-108">Periodically, you may want to delete these digests from the table by using a stored procedure that deletes only those digests that are older than a certain period.</span></span> <span data-ttu-id="682d6-109">MessageDigestHelper 資料表含有可以達成此目的 `TimeCreated` 屬性。</span><span class="sxs-lookup"><span data-stu-id="682d6-109">The MessageDigestHelper table contains a `TimeCreated` property that you can use for this purpose.</span></span>  
  
 <span data-ttu-id="682d6-110">請使用下列 SQL 陳述式 (依照您的目的進行修改) 建立預存程序，並執行預存程序刪除舊有的摘要。</span><span class="sxs-lookup"><span data-stu-id="682d6-110">Create a stored procedure with the following SQL statement (as modified for your purposes), and run the stored procedure to delete old digests.</span></span> <span data-ttu-id="682d6-111">此範例陳述式會刪除所有超過七天的摘要：</span><span class="sxs-lookup"><span data-stu-id="682d6-111">This sample statement deletes all digests more than seven days old:</span></span>  
  
```  
delete from MessageDigestHelper where datediff(day, TimeCreated, getutcdate()) > 7  
```  
  
> [!NOTE]
>  <span data-ttu-id="682d6-112">預存程序必須包含在呼叫`getutcdate`，而非`getdate`，因為所有[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]資料庫使用 UTC (Universal Time Coordinate) 時間。</span><span class="sxs-lookup"><span data-stu-id="682d6-112">The stored procedure must include a call to `getutcdate`, not `getdate`, because all [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] databases use UTC (Universal Time Coordinate) time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="682d6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="682d6-113">See Also</span></span>  
 [<span data-ttu-id="682d6-114">維護 BTARN 資料庫</span><span class="sxs-lookup"><span data-stu-id="682d6-114">Maintaining BTARN Databases</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/maintaining-btarn-databases.md)