---
title: "發出和贖回單一登入票證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0323a6-cc31-460d-b64d-b4d8142c3855
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9988eedb545b3b1a348a5de6275b176abe2be7e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="issuing-and-redeeming-a-single-sign-on-ticket"></a>發出和贖回單一登入票證
一旦您將使用者與分支機構應用程式連結在一起之後，您就可以發出票證，確保在維持通訊時的安全性。 單一登入票證的運作方式就像其他票證技術一樣： 之前傳送郵件，您將附加的單一登入 」 票證至訊息當成字串。 伺服器收到您的訊息後，會解碼票證並在適當時使用這項資訊。  
  
### <a name="to-issue-a-single-sign-on-ticket"></a>發出單一登入票證  
  
1.  使用 I`SSOTicket` 的呼叫建立新的票證物件。  
  
2.  使用 I`SSOTicket.IssueTicket` 的呼叫發出票證。  
  
### <a name="to-redeem-a-single-sign-on-ticket"></a>贖回單一登入票證  
  
1.  使用 I`SSOTicket` 的呼叫建立新的票證物件。  
  
2.  使用 I`SSOTicket.RedeemTicket` 的呼叫贖回票證。  
  
## <a name="see-also"></a>另請參閱  
 [使用企業單一登入進行程式設計](../core/programming-with-enterprise-single-sign-on.md)