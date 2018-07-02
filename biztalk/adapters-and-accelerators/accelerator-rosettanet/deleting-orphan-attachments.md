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
# <a name="deleting-orphan-attachments"></a>刪除孤立的附件
Microsoft[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]儲存已接收訊息的附件。 在特定情況下，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會儲存附件，但卻從 MessagesToLOB 資料表中刪除相關訊息，導致出現孤立的附件。 這可能是當您送出訊息，有一個附件，並具有資訊清單不是有效的例如 numberofattachments 資訊清單 = 0。 您可能需要定期刪除孤立的附件，以維護系統效能。  
  
## <a name="how-to-delete-orphan-attachments"></a>如何刪除孤立的附件  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會將附件儲存在 BTARNDATA 資料庫的 Attachments 資料表。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 將相關聯的訊息儲存在 MessagesToLOB 資料表中。 當附件的 `outMessageID` 屬性與 MessagesToLOB 資料表中訊息的 `MessageID` 屬性不一致時，便會產生孤立的附件。  
  
 您可能需要定期使用預存程序，刪除在 MessagesToLOB 資料表中沒有對應訊息的附件，藉此從資料表中刪除附件。 預存程序的範例 SQL 陳述式如下：  
  
```  
delete from attachments where outMessageID not in (select messageid from messagestolob)  
```  
  
 此外，建議您刪除超過某一時段的附件，並且不需要進行任何深入研究。 Attachments 資料表含有 `TimeCreated` 屬性，您可以利用此屬性刪除舊有的附件。 此程序與刪除舊摘要的程序類似。 刪除舊摘要的預存程序的範例 SQL 陳述式，請參閱 <<c0> [ 刪除摘要](../../adapters-and-accelerators/accelerator-rosettanet/deleting-digests.md)。  
  
 同時也建議您針對 Attachments 與 MessagestoLOB 資料表中對應的 MessageID 欄位編製索引。  
  
## <a name="see-also"></a>另請參閱  
 [維護 BTARN 資料庫](../../adapters-and-accelerators/accelerator-rosettanet/maintaining-btarn-databases.md)