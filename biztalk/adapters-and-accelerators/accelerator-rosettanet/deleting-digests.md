---
title: 刪除摘要 |Microsoft 文件
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
ms.openlocfilehash: fefa59a7638b7dc4627d5d7a019d753b4f6290b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206742"
---
# <a name="deleting-digests"></a>刪除摘要
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]儲存針對傳出訊息的摘要，因此它可以針對訊號內容驗證它們。 不過，驗證後，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 並不會刪除摘要。 您可能需要定期刪除這些摘要，以維護系統效能。  
  
## <a name="when-and-how-to-delete-digests"></a>刪除摘要的時機與方法  
 摘要是儲存在 BTARNDATA 資料庫的 MessageDigestHelper 資料表中。 您可能需要定期使用預存程序，刪除某一特定時段以前的摘要，藉此從資料表中刪除這些摘要。 MessageDigestHelper 資料表含有可以達成此目的 `TimeCreated` 屬性。  
  
 請使用下列 SQL 陳述式 (依照您的目的進行修改) 建立預存程序，並執行預存程序刪除舊有的摘要。 此範例陳述式會刪除所有超過七天的摘要：  
  
```  
delete from MessageDigestHelper where datediff(day, TimeCreated, getutcdate()) > 7  
```  
  
> [!NOTE]
>  預存程序必須包含對`getutcdate`，而非`getdate`，因為所有[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]資料庫使用 UTC (世界標準時間) 時間。  
  
## <a name="see-also"></a>另請參閱  
 [維護 BTARN 資料庫](../../adapters-and-accelerators/accelerator-rosettanet/maintaining-btarn-databases.md)