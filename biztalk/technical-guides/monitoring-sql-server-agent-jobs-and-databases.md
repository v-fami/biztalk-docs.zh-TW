---
title: 監視 SQL Server Agent 作業和資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2eb5f318-10d3-4f43-991d-9bff2ebc20e2
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2a0b770ded2bef9ccf28a763f63f053c0b3c89e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024308"
---
# <a name="monitoring-sql-server-agent-jobs-and-databases"></a>監視 SQL Server Agent 作業和資料庫
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含多個[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行重要的功能，以維持伺服器運作中且狀況良好的代理程式作業。 您應該監視這些作業的狀況，確保它們在沒有錯誤的情況下執行。 Microsoft[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]管理組件包含規則，以便監視 SQL 資料庫等項目和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]代理程式作業。 您應該設定[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]全面監視所有的管理組件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]代理程式作業。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件包含兩個已停用的規則，以便監視的健全狀況的兩個最重要的 BizTalk[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]代理程式作業：  
  
- 嚴重錯誤： BizTalk SQL Server Agent 作業失敗-備份 BizTalk Server  
  
- 嚴重錯誤： BizTalk SQL Server Agent 作業失敗-追蹤訊息複製  
  
  若要監控所有 BizTalk Server[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]內的代理程式作業[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件，您必須啟用這些規則，並建立您想要使用下列程序監視其他作業的其他規則。  
  
- 在 Operations Manager 系統管理員主控台中，建立一份與前述的兩個規則，在任一[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]核心規則群組，並適當地重新命名的規則。  
  
- 在 [準則] 區段的規則，請參數 1 的適當變更的萬用字元比較。  
  
- 在某些情況下，作業名稱是取決於資料庫名稱，建立使用者，例如，MessageBox 資料庫的名稱。  
  
- 可以鎖定您的規則是針對工作與相關聯單一 MessageBox 或所有 Messagebox。  
  
## <a name="see-also"></a>另請參閱  
 [如何啟動 SQL Server Agent](../technical-guides/how-to-start-the-sql-server-agent.md)