---
title: 如何標示 BizTalk Server 資料庫的自訂監視 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cfbdc73d-a108-42ee-a5d8-401d5bfe5e7d
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea069140b9dd89fafa13fe57be9eefa17eceb790
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023708"
---
# <a name="how-to-mark-biztalk-server-databases-for-customized-monitoring"></a>如何標示 BizTalk Server 資料庫的自訂監視
如果您已安裝 Microsoft[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]管理組件，您可以自訂的方式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫會受到監視。 這可確保[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]管理組件會監視下列[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫：  
  
-   BAM 封存 (BAMArchive) 資料庫  
  
-   BAM 主要匯入 (BAMPrimaryImport) 資料庫  
  
-   BAM 星狀結構描述 (BAMStarSchema) 資料庫  
  
-   BizTalk 追蹤 (BizTalkDTADb) 資料庫  
  
-   BizTalk 管理 (BizTalkMgmtDb) 資料庫  
  
-   BizTalk MessageBox (BizTalkMsgBoxDb) 資料庫  
  
-   規則引擎 (BizTalkRuleEngineDb) 資料庫  
  
-   企業單一登入 (SSODB) 資料庫  
  
> [!NOTE]
>  您必須為 Operations Manager 進階操作員角色的成員登入或[!INCLUDE[opsmgr_short](../includes/opsmgr-short-md.md)]管理群組。  
  
### <a name="to-mark-biztalk-server-databases-for-customized-monitoring"></a>將 BizTalk Server 資料庫的自訂監視  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  **System Center Operations Manager 2007**，然後按一下**Operations 主控台**。  
  
2. 在 Operations 主控台中，按一下**Authoring**  按鈕。  
  
3. 在  **Authoring**  窗格中，展開**管理組件物件**，然後按一下 **物件探索**。  
  
4. 若要尋找探索適用於 SQL Server，在 Operations 主控台工具列上按一下**尋找**，然後在**尋求**文字方塊中，輸入**SQL 2008**搜尋 SQL Server 2008。  
  
5. 底下**找到的類型： SQL 2008 DB**類別目錄中，選取**探索的資料庫，資料庫引擎的**。  
  
6. 在 Operations 主控台工具列中，按一下 **會覆寫**，再指向**覆寫物件探索**。 您可以選擇覆寫探索，針對特定類型的物件或群組中的所有物件。 您選擇要覆寫時，物件類型群組之後**覆寫內容**對話方塊隨即開啟。  
  
   > [!NOTE]  
   >  如果**會覆寫**按鈕便無法使用，請確定您已在 [監視] 窗格中選取監視器，而不是容器物件。  
  
7. 選取核取方塊，在**覆寫**旁的資料行**排除清單**參數，然後在**覆寫值** 欄中，輸入您想要排除的資料庫名稱從監視。 請確定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中未列出您想要監視的資料庫**覆寫值**資料行。  
  
   > [!TIP]  
   >  若要建立新的管理組件，您可以使用修改過的物件探索。 在底部窗格中，**選取目的地管理組件**下拉式清單會顯示預設值是**預設管理組件**。 按一下 **新增**建立新的管理組件，使用修改過的物件探索。  
  
## <a name="see-also"></a>另請參閱  
 [監視 SQL Server](../technical-guides/monitoring-sql-servers.md)