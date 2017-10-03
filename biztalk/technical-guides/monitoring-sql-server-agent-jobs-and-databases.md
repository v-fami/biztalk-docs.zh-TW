---
title: "監視 SQL Server Agent 作業，以及資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2eb5f318-10d3-4f43-991d-9bff2ebc20e2
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6c9991e7ebd61c72bbeb6a090b0497244da63e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-sql-server-agent-jobs-and-databases"></a>監視 SQL Server Agent 作業和資料庫
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]包含多個[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行重要功能以維持伺服器運作且狀況良好的代理程式作業。 您應該監視這些作業的狀況，確保它們在沒有錯誤的情況下執行。 Microsoft[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]管理組件包含監視 SQL 資料庫等項目規則和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]代理程式作業。 您應該設定[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]全面監視所有的管理組件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]代理程式作業。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件包含兩個已停用的規則，以便監視的健全狀況的兩個最重要的 BizTalk[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]代理程式作業：  
  
-   嚴重錯誤： BizTalk SQL Server Agent 作業失敗-備份 BizTalk Server  
  
-   嚴重錯誤： BizTalk SQL Server Agent 作業失敗-追蹤訊息複製  
  
 若要監控所有 BizTalk Server[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]代理程式作業從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件，您必須啟用這些規則，並建立額外的規則，您想要使用下列程序監視的其他作業。  
  
-   在 Operations Manager 系統管理員主控台中，建立一份在前述的兩個規則，在任一[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]核心規則群組，並適當地重新命名的規則。  
  
-   規則的準則區段中變更的萬用字元比較參數 1 適當。  
  
-   在某些情況下，作業名稱為相依於資料庫名稱的使用者建立時，例如，MessageBox 資料庫的名稱。  
  
-   您可以將目標設您的規則優先的工作相關聯的單一 MessageBox 或所有的 Messagebox。  
  
## <a name="see-also"></a>另請參閱  
 [如何啟動 SQL Server 代理程式](../technical-guides/how-to-start-the-sql-server-agent.md)