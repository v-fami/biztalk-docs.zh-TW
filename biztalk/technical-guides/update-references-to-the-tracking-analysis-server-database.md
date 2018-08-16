---
title: 更新追蹤 Analysis Server 資料庫的參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a403325-1394-4668-946f-01b610cb686e
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 417569d99b7326b435422b5fa0dff28019006116
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014703"
---
# <a name="update-references-to-the-tracking-analysis-server-database"></a>更新追蹤 Analysis Server 資料庫的參考
追蹤 Analysis Server 資料庫是選擇性的包含的線上分析處理 (OLAP) cube。 這些 OLAP Cube 是包含在 BizTalk 追蹤資料庫中的資料彙總。  
  
 若要還原追蹤 Analysis Server 資料庫，請使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]分析管理員來處理 MessageMetrics 和 ServiceMetrics cube。 如需相關指示，請參閱 <<c0> [ 管理備份和還原 (Analysis Services)](http://go.microsoft.com/fwlink/?LinkId=130939) (<http://go.microsoft.com/fwlink/?LinkId=130939>) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》。  
  
 追蹤 Analysis Server 資料庫還原到其他電腦，您也必須使用下列程序更新 BizTalk 管理資料庫中的資料庫名稱的參考。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators 群組成員的身分登入，才能執行此程序。  
  
### <a name="to-update-references-to-the-tracking-analysis-server-database-name"></a>若要更新追蹤 Analysis Server 資料庫名稱的參考  
  
1.  在目的地系統上，按一下**開始**，按一下**程式**，按一下  **Microsoft SQL Server 2008**，然後按一下  **SQL Server Management Studio**.  
  
2.  在**連接到伺服器**對話方塊中，選取**伺服器類型**做為**Database Engine**、 提供伺服器名稱、 提供認證以連線至伺服器，然後按一下  **Connect**。  
  
3.  按一下以開啟適當的伺服器，按兩下**資料庫**，按兩下**BizTalkMgmtDb**，然後按一下**資料表**。  
  
4.  在 [詳細資料] 窗格中，以滑鼠右鍵按一下 **[adm_group]**，再指向**開啟資料表**。  
  
5.  將對應至原始資料庫的資料行修改為參考新資料庫的適當值。  
  
    > [!NOTE]  
    >  *\<DBType\>*  DBServerName 並*\<DBType\>* DBName 指示位置的資料庫，其中*\<DBType\>* 對應至資料庫，例如，TrackingAnalysis 的型別。  
  
6.  關閉資料表以儲存新值。  
  
## <a name="see-also"></a>另請參閱  
 [更新資料庫參考](../technical-guides/updating-database-references.md)