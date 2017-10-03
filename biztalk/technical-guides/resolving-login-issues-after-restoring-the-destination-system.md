---
title: "登入問題解決之後還原目的地系統 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9232ca3-dadb-4b3c-8ec4-4e307c32d2e5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e691e690552f6decb3eed5f55dd17295c21a4efd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="resolving-login-issues-after-restoring-the-destination-system"></a><span data-ttu-id="29bbc-102">登入問題解決之後還原目的地系統</span><span class="sxs-lookup"><span data-stu-id="29bbc-102">Resolving Login Issues After Restoring the Destination System</span></span>
<span data-ttu-id="29bbc-103">根據來源系統的設定方式在部署期間，「 被遺棄的 」 的使用者可能需要加以解決。</span><span class="sxs-lookup"><span data-stu-id="29bbc-103">Depending on how the source system was configured during deployment, "orphaned" users may need to be resolved.</span></span> <span data-ttu-id="29bbc-104">被遺棄的資料庫使用者是沒有對應的安全性的使用者登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="29bbc-104">An orphaned database user is a user who does not have a corresponding security login in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span> <span data-ttu-id="29bbc-105">建立這些使用者的對應登入才可以使重新系統線上使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]SQL Management Studio (在**安全性**，**登入**)。</span><span class="sxs-lookup"><span data-stu-id="29bbc-105">Create corresponding logins for these users before bringing the system online using the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] SQL Management Studio (in **Security**, **Logins**).</span></span> <span data-ttu-id="29bbc-106">您可以建立這些登入，在任何時間點，但我們建議您建立它們時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="29bbc-106">You can create these logins at any point, but we recommend that you create them when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping is configured.</span></span>  
  
 <span data-ttu-id="29bbc-107">所建立的登入應該對應至 Windows 帳戶與群組所使用的時機[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]已設定來源系統上，並以手動方式建立及用於任何任何登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-建立角色。</span><span class="sxs-lookup"><span data-stu-id="29bbc-107">The logins that are created should correspond to the Windows accounts and groups that were used when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] was configured on the source system and to any logins that were manually created and used in any [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-created role.</span></span> <span data-ttu-id="29bbc-108">如果這些登入對應到本機 Windows 帳戶或群組、 帳戶和群組必須先建立後，才能新增登入。</span><span class="sxs-lookup"><span data-stu-id="29bbc-108">If these logins correspond to local Windows accounts or groups, the accounts and groups must first be created before the login can be added.</span></span> <span data-ttu-id="29bbc-109">如果未變更 BizTalk server 的電腦名稱，然後解決與登入的本機帳戶與群組相關聯的使用者。</span><span class="sxs-lookup"><span data-stu-id="29bbc-109">If the computer name for the BizTalk server is not changed, then resolve the users associated with the logins for the local accounts and groups.</span></span>  
  
 <span data-ttu-id="29bbc-110">設定時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送，請依照 Microsoft 知識庫文章 918992[如何在 SQL Server 2008 的 SQL Server 2005 執行個體之間傳送登入和密碼](http://go.microsoft.com/fwlink/?LinkId=157143)(http://go.microsoft.com/fwlink/ 嗎？LinkId = 157143) 建立的指令碼會將必要的登入加入到目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="29bbc-110">When configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping, follow the steps in Microsoft Knowledge Base Article 918992 [How to transfer the logins and the passwords between instances of SQL Server 2005 and SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=157143) (http://go.microsoft.com/fwlink/?LinkId=157143) to create a script that will add the necessary logins to the destination server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29bbc-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29bbc-111">See Also</span></span>  
 [<span data-ttu-id="29bbc-112">疑難排解記錄傳送</span><span class="sxs-lookup"><span data-stu-id="29bbc-112">Troubleshooting Log Shipping</span></span>](../technical-guides/troubleshooting-log-shipping.md)