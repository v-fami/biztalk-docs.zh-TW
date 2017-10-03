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
# <a name="resolving-login-issues-after-restoring-the-destination-system"></a>登入問題解決之後還原目的地系統
根據來源系統的設定方式在部署期間，「 被遺棄的 」 的使用者可能需要加以解決。 被遺棄的資料庫使用者是沒有對應的安全性的使用者登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 建立這些使用者的對應登入才可以使重新系統線上使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]SQL Management Studio (在**安全性**，**登入**)。 您可以建立這些登入，在任何時間點，但我們建議您建立它們時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定記錄傳送。  
  
 所建立的登入應該對應至 Windows 帳戶與群組所使用的時機[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]已設定來源系統上，並以手動方式建立及用於任何任何登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-建立角色。 如果這些登入對應到本機 Windows 帳戶或群組、 帳戶和群組必須先建立後，才能新增登入。 如果未變更 BizTalk server 的電腦名稱，然後解決與登入的本機帳戶與群組相關聯的使用者。  
  
 設定時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送，請依照 Microsoft 知識庫文章 918992[如何在 SQL Server 2008 的 SQL Server 2005 執行個體之間傳送登入和密碼](http://go.microsoft.com/fwlink/?LinkId=157143)(http://go.microsoft.com/fwlink/ 嗎？LinkId = 157143) 建立的指令碼會將必要的登入加入到目的地伺服器。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解記錄傳送](../technical-guides/troubleshooting-log-shipping.md)