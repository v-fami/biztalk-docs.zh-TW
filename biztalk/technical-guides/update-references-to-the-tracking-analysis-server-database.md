---
title: 更新追蹤 Analysis Server 資料庫的參考 |Microsoft 文件
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
ms.openlocfilehash: 2b85c5c50bc8aeb388d6b7df1591f4b13900998e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25976316"
---
# <a name="update-references-to-the-tracking-analysis-server-database"></a>更新追蹤 Analysis Server 資料庫的參考
追蹤 Analysis Server 資料庫是選擇性，而且包含線上分析處理 (OLAP) cube。 這些 OLAP Cube 是包含在 BizTalk 追蹤資料庫中的資料彙總。  
  
 若要還原追蹤 Analysis Server 資料庫，請使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]分析管理員 」 來處理 MessageMetrics 和 ServiceMetrics cube。 如需指示，請參閱[管理備份與還原 (Analysis Services)](http://go.microsoft.com/fwlink/?LinkId=130939) (http://go.microsoft.com/fwlink/?LinkId=130939) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》。  
  
 若要還原追蹤 Analysis Server 資料庫到其他電腦，您也必須使用下列程序更新 BizTalk 管理資料庫中的資料庫名稱的參考。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators 群組成員的身分登入，才能執行此程序。  
  
### <a name="to-update-references-to-the-tracking-analysis-server-database-name"></a>若要更新追蹤 Analysis Server 資料庫名稱的參考  
  
1.  在目的地系統上，按一下 **啟動**，按一下 **程式**，按一下  **Microsoft SQL Server 2008**，然後按一下  **SQL Server Management Studio**.  
  
2.  在**連接到伺服器**對話方塊中，選取**伺服器類型**為**Database Engine**、 提供伺服器名稱、 提供認證來連線至伺服器，然後按一下**連接**。  
  
3.  按一下以開啟適當的伺服器，按兩下**資料庫**，按兩下**BizTalkMgmtDb**，然後按一下**資料表**。  
  
4.  在詳細資料窗格中，以滑鼠右鍵按一下 **[adm_group]**，然後指向**開啟資料表**。  
  
5.  將對應至原始資料庫的資料行修改為參考新資料庫的適當值。  
  
    > [!NOTE]  
    >  *\<DBType\>*  DBServerName 和 *\<DBType\>*  DBName 代表資料庫位置，其中 *\<DBType\>* 對應到資料庫，例如，TrackingAnalysis 的類型。  
  
6.  關閉資料表以儲存新值。  
  
## <a name="see-also"></a>請參閱  
 [更新資料庫參考](../technical-guides/updating-database-references.md)