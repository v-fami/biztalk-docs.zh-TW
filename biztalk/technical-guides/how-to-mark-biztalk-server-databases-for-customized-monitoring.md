---
title: BizTalk Server 資料庫標示為的自訂監視如何 |Microsoft 文件
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
ms.openlocfilehash: 08807b1a365b84765221e3a71cb131d8c037fcf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298238"
---
# <a name="how-to-mark-biztalk-server-databases-for-customized-monitoring"></a>如何將 BizTalk Server 資料庫標示為的自訂監視
如果您已安裝 Microsoft[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]管理組件，您可以自訂方式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫會受到監視。 如此可確保[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]管理組件會監視下列[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫：  
  
-   BAM 封存 (BAMArchive) 資料庫  
  
-   BAM 主要匯入 (BAMPrimaryImport) 資料庫  
  
-   BAM 星狀結構描述 (BAMStarSchema) 資料庫  
  
-   BizTalk 追蹤 (BizTalkDTADb) 資料庫  
  
-   BizTalk 管理 (BizTalkMgmtDb) 資料庫  
  
-   BizTalk MessageBox (BizTalkMsgBoxDb) 資料庫  
  
-   規則引擎 (BizTalkRuleEngineDb) 資料庫  
  
-   企業單一登入 (SSODB) 資料庫  
  
> [!NOTE]  
>  您必須以 Operations Manager 進階操作員角色的成員登入或[!INCLUDE[opsmgr_short](../includes/opsmgr-short-md.md)]管理群組。  
  
### <a name="to-mark-biztalk-server-databases-for-customized-monitoring"></a>若要將 BizTalk Server 資料庫標示的自訂監視  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  **System Center Operations Manager 2007**，然後按一下  **Operations 主控台**。  
  
2.  在 Operations 主控台中，按一下**製作** 按鈕。  
  
3.  在**製作** 窗格中，展開 **管理組件物件**，然後按一下 **物件探索**。  
  
4.  若要找出適用於 SQL Server 的探索，Operations 主控台工具列上按一下**尋找**，然後在**尋找**文字方塊中，輸入**SQL 2008**搜尋 SQL Server 2008。  
  
5.  在下**找到的類型： SQL 2008 DB**類別目錄中，選取**探索資料庫引擎的資料庫**。  
  
6.  在 Operations 主控台工具列中，按一下 **會覆寫**，然後指向**覆寫物件探索**。 您可以選擇覆寫探索，特定類型的物件或群組內的所有物件。 選擇要覆寫，物件類型的群組之後**覆寫內容**對話方塊隨即開啟。  
  
    > [!NOTE]  
    >  如果**會覆寫**按鈕便無法使用，請確定您已在 [監視] 窗格中選取監視器，而不是容器物件。  
  
7.  選取核取方塊，在**覆寫**旁邊的資料行**排除清單**參數，然後在**覆寫值**資料行中，輸入您想要排除的資料庫名稱從監視。 請確定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中不會列出您想要監視的資料庫**覆寫值**資料行。  
  
    > [!TIP]  
    >  若要建立新的管理組件，您可以使用修改過的物件探索。 在底部窗格中，**選取目的地管理組件**下拉式清單會顯示預設值是**預設管理組件**。 按一下**新增**建立新的管理組件，使用已修改的物件探索。  
  
## <a name="see-also"></a>另請參閱  
 [監視 SQL Server](../technical-guides/monitoring-sql-servers.md)