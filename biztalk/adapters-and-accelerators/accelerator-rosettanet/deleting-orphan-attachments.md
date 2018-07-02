---
title: 刪除孤立的附件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maintaining databases, deleting orphaned attachments
- databases, deleting orphaned attachments
- attachments
ms.assetid: 38280464-9c9d-4890-9fc5-4b8031dd3f88
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99b31633c27aaed7cb8ae7289f383a5bfcac8d1b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971887"
---
# <a name="deleting-orphan-attachments"></a><span data-ttu-id="45473-102">刪除孤立的附件</span><span class="sxs-lookup"><span data-stu-id="45473-102">Deleting Orphan Attachments</span></span>
<span data-ttu-id="45473-103">Microsoft[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]儲存已接收訊息的附件。</span><span class="sxs-lookup"><span data-stu-id="45473-103">Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] stores attachments for received messages.</span></span> <span data-ttu-id="45473-104">在特定情況下，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會儲存附件，但卻從 MessagesToLOB 資料表中刪除相關訊息，導致出現孤立的附件。</span><span class="sxs-lookup"><span data-stu-id="45473-104">In certain circumstances, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] saves the attachment, but deletes the associated message from the MessagesToLOB table, resulting in an orphan attachment.</span></span> <span data-ttu-id="45473-105">這可能是當您送出訊息，有一個附件，並具有資訊清單不是有效的例如 numberofattachments 資訊清單 = 0。</span><span class="sxs-lookup"><span data-stu-id="45473-105">This can occur when you submit a message that has an attachment and has a manifest that is not valid, for example, a manifest in which NumberOfAttachments = 0.</span></span> <span data-ttu-id="45473-106">您可能需要定期刪除孤立的附件，以維護系統效能。</span><span class="sxs-lookup"><span data-stu-id="45473-106">Periodically, you may want to delete orphan attachments to maintain system performance.</span></span>  
  
## <a name="how-to-delete-orphan-attachments"></a><span data-ttu-id="45473-107">如何刪除孤立的附件</span><span class="sxs-lookup"><span data-stu-id="45473-107">How to Delete Orphan Attachments</span></span>  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="45473-108"> 會將附件儲存在 BTARNDATA 資料庫的 Attachments 資料表。</span><span class="sxs-lookup"><span data-stu-id="45473-108"> stores attachments in the Attachments table of the BTARNDATA database.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="45473-109"> 將相關聯的訊息儲存在 MessagesToLOB 資料表中。</span><span class="sxs-lookup"><span data-stu-id="45473-109"> stores the associated messages in the MessagesToLOB table.</span></span> <span data-ttu-id="45473-110">當附件的 `outMessageID` 屬性與 MessagesToLOB 資料表中訊息的 `MessageID` 屬性不一致時，便會產生孤立的附件。</span><span class="sxs-lookup"><span data-stu-id="45473-110">An orphan attachment results when the attachment has an `outMessageID` property that does not correspond to the `MessageID` property of a message in the MessagesToLOB table.</span></span>  
  
 <span data-ttu-id="45473-111">您可能需要定期使用預存程序，刪除在 MessagesToLOB 資料表中沒有對應訊息的附件，藉此從資料表中刪除附件。</span><span class="sxs-lookup"><span data-stu-id="45473-111">Periodically, you may want to delete attachments from the table by using a stored procedure that deletes only those attachments that do not have a corresponding message in the MessagesToLOB table.</span></span> <span data-ttu-id="45473-112">預存程序的範例 SQL 陳述式如下：</span><span class="sxs-lookup"><span data-stu-id="45473-112">A sample SQL statement for the stored procedure is:</span></span>  
  
```  
delete from attachments where outMessageID not in (select messageid from messagestolob)  
```  
  
 <span data-ttu-id="45473-113">此外，建議您刪除超過某一時段的附件，並且不需要進行任何深入研究。</span><span class="sxs-lookup"><span data-stu-id="45473-113">Additionally, it is recommended that you delete attachments that are older than a certain period, and do not require any more investigation.</span></span> <span data-ttu-id="45473-114">Attachments 資料表含有 `TimeCreated` 屬性，您可以利用此屬性刪除舊有的附件。</span><span class="sxs-lookup"><span data-stu-id="45473-114">The Attachments table contains a `TimeCreated` property that you can use to delete old attachments.</span></span> <span data-ttu-id="45473-115">此程序與刪除舊摘要的程序類似。</span><span class="sxs-lookup"><span data-stu-id="45473-115">This process is similar to the process used to delete old digests.</span></span> <span data-ttu-id="45473-116">刪除舊摘要的預存程序的範例 SQL 陳述式，請參閱 <<c0> [ 刪除摘要](../../adapters-and-accelerators/accelerator-rosettanet/deleting-digests.md)。</span><span class="sxs-lookup"><span data-stu-id="45473-116">For a sample SQL statement for a stored procedure that deletes old digests, see [Deleting Digests](../../adapters-and-accelerators/accelerator-rosettanet/deleting-digests.md).</span></span>  
  
 <span data-ttu-id="45473-117">同時也建議您針對 Attachments 與 MessagestoLOB 資料表中對應的 MessageID 欄位編製索引。</span><span class="sxs-lookup"><span data-stu-id="45473-117">It is also recommended that you index the Attachments and MessagestoLOB tables on the respective MessageID columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45473-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45473-118">See Also</span></span>  
 [<span data-ttu-id="45473-119">維護 BTARN 資料庫</span><span class="sxs-lookup"><span data-stu-id="45473-119">Maintaining BTARN Databases</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/maintaining-btarn-databases.md)