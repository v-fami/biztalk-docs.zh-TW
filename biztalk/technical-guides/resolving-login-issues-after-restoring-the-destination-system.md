---
title: "登入問題解決之後還原目的地系統 |Microsoft 文件"
description: "若要解決被遺棄的使用者，在 BizTalk Server 中的指令碼 SQL Server 登入記錄傳送"
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
ms.openlocfilehash: 559302718c9fe504c9c264de92f6a4af161d91f9
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="resolving-login-issues-after-restoring-the-destination-system"></a>登入問題解決之後還原目的地系統

## <a name="orphaned-users"></a>被遺棄的使用者
根據來源系統的設定方式在部署期間，「 被遺棄的 」 的使用者可能需要加以解決。 被遺棄的資料庫使用者是沒有對應的安全性的使用者登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 建立這些使用者的對應登入才可以使重新系統線上使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]SQL Management Studio (在**安全性**，**登入**)。 您可以建立這些登入，在任何時間點，但我們建議您建立它們時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定記錄傳送。  
  
 所建立的登入應該對應至 Windows 帳戶與群組所使用的時機[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]已設定來源系統上，並以手動方式建立及用於任何任何登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-建立角色。 如果這些登入對應到本機 Windows 帳戶或群組、 帳戶和群組必須先建立後，才能新增登入。 如果未變更 BizTalk server 的電腦名稱，然後解決與登入的本機帳戶與群組相關聯的使用者。  
  
 設定時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送，您可以[KB 918992: SQL Server 執行個體之間傳送登入和密碼](https://support.microsoft.com/help/918992/how-to-transfer-logins-and-passwords-between-instances-of-sql-server)建立將必要的登入加入到目的地伺服器的指令碼。  
  
## <a name="see-also"></a>另請參閱  
 [針對記錄傳送進行疑難排解](../technical-guides/troubleshooting-log-shipping.md)
