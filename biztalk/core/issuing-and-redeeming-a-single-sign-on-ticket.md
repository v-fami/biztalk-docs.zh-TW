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
# <a name="issuing-and-redeeming-a-single-sign-on-ticket"></a><span data-ttu-id="95e79-102">發出和贖回單一登入票證</span><span class="sxs-lookup"><span data-stu-id="95e79-102">Issuing and Redeeming a Single Sign-On Ticket</span></span>
<span data-ttu-id="95e79-103">一旦您將使用者與分支機構應用程式連結在一起之後，您就可以發出票證，確保在維持通訊時的安全性。</span><span class="sxs-lookup"><span data-stu-id="95e79-103">After you link a user and an affiliate application, you can issue tickets to help ensure security while maintaining communications.</span></span> <span data-ttu-id="95e79-104">單一登入票證的運作方式就像其他票證技術一樣： 之前傳送郵件，您將附加的單一登入 」 票證至訊息當成字串。</span><span class="sxs-lookup"><span data-stu-id="95e79-104">Single Sign-On ticketing works just like other ticketing technologies: before sending the message off, you append the Single Sign-On ticket to the message as a string.</span></span> <span data-ttu-id="95e79-105">伺服器收到您的訊息後，會解碼票證並在適當時使用這項資訊。</span><span class="sxs-lookup"><span data-stu-id="95e79-105">The server receives your message, decodes the ticket, and uses the information as appropriate.</span></span>  
  
### <a name="to-issue-a-single-sign-on-ticket"></a><span data-ttu-id="95e79-106">發出單一登入票證</span><span class="sxs-lookup"><span data-stu-id="95e79-106">To issue a Single Sign-On ticket</span></span>  
  
1.  <span data-ttu-id="95e79-107">使用 I`SSOTicket` 的呼叫建立新的票證物件。</span><span class="sxs-lookup"><span data-stu-id="95e79-107">Create a new ticket object with a call to I`SSOTicket`.</span></span>  
  
2.  <span data-ttu-id="95e79-108">使用 I`SSOTicket.IssueTicket` 的呼叫發出票證。</span><span class="sxs-lookup"><span data-stu-id="95e79-108">Issue the ticket with a call to I`SSOTicket.IssueTicket`.</span></span>  
  
### <a name="to-redeem-a-single-sign-on-ticket"></a><span data-ttu-id="95e79-109">贖回單一登入票證</span><span class="sxs-lookup"><span data-stu-id="95e79-109">To redeem a Single Sign-On ticket</span></span>  
  
1.  <span data-ttu-id="95e79-110">使用 I`SSOTicket` 的呼叫建立新的票證物件。</span><span class="sxs-lookup"><span data-stu-id="95e79-110">Create a new ticket object with a call to I`SSOTicket`.</span></span>  
  
2.  <span data-ttu-id="95e79-111">使用 I`SSOTicket.RedeemTicket` 的呼叫贖回票證。</span><span class="sxs-lookup"><span data-stu-id="95e79-111">Redeem the ticket with a call to I`SSOTicket.RedeemTicket`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95e79-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95e79-112">See Also</span></span>  
 [<span data-ttu-id="95e79-113">使用企業單一登入進行程式設計</span><span class="sxs-lookup"><span data-stu-id="95e79-113">Programming with Enterprise Single Sign-On</span></span>](../core/programming-with-enterprise-single-sign-on.md)