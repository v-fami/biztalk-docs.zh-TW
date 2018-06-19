---
title: 登入問題解決之後還原目的地系統 |Microsoft 文件
description: 若要解決被遺棄的使用者，在 BizTalk Server 中的指令碼 SQL Server 登入記錄傳送
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9232ca3-dadb-4b3c-8ec4-4e307c32d2e5
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 559302718c9fe504c9c264de92f6a4af161d91f9
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24013797"
---
# <a name="resolving-login-issues-after-restoring-the-destination-system"></a><span data-ttu-id="e308a-103">登入問題解決之後還原目的地系統</span><span class="sxs-lookup"><span data-stu-id="e308a-103">Resolving Login Issues After Restoring the Destination System</span></span>

## <a name="orphaned-users"></a><span data-ttu-id="e308a-104">被遺棄的使用者</span><span class="sxs-lookup"><span data-stu-id="e308a-104">Orphaned users</span></span>
<span data-ttu-id="e308a-105">根據來源系統的設定方式在部署期間，「 被遺棄的 」 的使用者可能需要加以解決。</span><span class="sxs-lookup"><span data-stu-id="e308a-105">Depending on how the source system was configured during deployment, "orphaned" users may need to be resolved.</span></span> <span data-ttu-id="e308a-106">被遺棄的資料庫使用者是沒有對應的安全性的使用者登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e308a-106">An orphaned database user is a user who does not have a corresponding security login in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span> <span data-ttu-id="e308a-107">建立這些使用者的對應登入才可以使重新系統線上使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]SQL Management Studio (在**安全性**，**登入**)。</span><span class="sxs-lookup"><span data-stu-id="e308a-107">Create corresponding logins for these users before bringing the system online using the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] SQL Management Studio (in **Security**, **Logins**).</span></span> <span data-ttu-id="e308a-108">您可以建立這些登入，在任何時間點，但我們建議您建立它們時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="e308a-108">You can create these logins at any point, but we recommend that you create them when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping is configured.</span></span>  
  
 <span data-ttu-id="e308a-109">所建立的登入應該對應至 Windows 帳戶與群組所使用的時機[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]已設定來源系統上，並以手動方式建立及用於任何任何登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-建立角色。</span><span class="sxs-lookup"><span data-stu-id="e308a-109">The logins that are created should correspond to the Windows accounts and groups that were used when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] was configured on the source system and to any logins that were manually created and used in any [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-created role.</span></span> <span data-ttu-id="e308a-110">如果這些登入對應到本機 Windows 帳戶或群組、 帳戶和群組必須先建立後，才能新增登入。</span><span class="sxs-lookup"><span data-stu-id="e308a-110">If these logins correspond to local Windows accounts or groups, the accounts and groups must first be created before the login can be added.</span></span> <span data-ttu-id="e308a-111">如果未變更 BizTalk server 的電腦名稱，然後解決與登入的本機帳戶與群組相關聯的使用者。</span><span class="sxs-lookup"><span data-stu-id="e308a-111">If the computer name for the BizTalk server is not changed, then resolve the users associated with the logins for the local accounts and groups.</span></span>  
  
 <span data-ttu-id="e308a-112">設定時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送，您可以[KB 918992: SQL Server 執行個體之間傳送登入和密碼](https://support.microsoft.com/help/918992/how-to-transfer-logins-and-passwords-between-instances-of-sql-server)建立將必要的登入加入到目的地伺服器的指令碼。</span><span class="sxs-lookup"><span data-stu-id="e308a-112">When configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping, you can [KB 918992: Transfer the logins and the passwords between instances of SQL Server](https://support.microsoft.com/help/918992/how-to-transfer-logins-and-passwords-between-instances-of-sql-server) to create a script that adds the necessary logins to the destination server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e308a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e308a-113">See Also</span></span>  
 [<span data-ttu-id="e308a-114">針對記錄傳送進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="e308a-114">Troubleshooting Log Shipping</span></span>](../technical-guides/troubleshooting-log-shipping.md)
