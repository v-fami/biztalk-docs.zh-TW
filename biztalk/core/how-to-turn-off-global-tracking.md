---
title: "如何關閉全域追蹤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eae3059a-cbdd-47c4-84cd-edfb5480b9fa
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c143d19e6071ca4f9ce488ae936082db86dc84dc
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-turn-off-global-tracking"></a>如何關閉全域追蹤
根據預設，當您安裝 BizTalk Server 時，會啟用全域追蹤。 BizTalk 追蹤 (BizTalkDTADb) 資料庫成長的大小為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理您的系統上的資料。 如果 BizTalk 追蹤資料庫導致磁碟效能低落，您可以從追蹤資料庫清除資料。 如果效能問題是藉由清除 BizTalk 追蹤資料庫而暫時解決，而您想要將 BizTalk 設定為不再收集追蹤資訊，則您可以考慮關閉全域追蹤。  
  
 請務必了解，關閉全域追蹤會停用整個的追蹤攔截器[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。 這代表 BizTalk 無法在其追蹤表格中追蹤事件。 或者，您可以關閉個別事件的追蹤。  
  
> [!NOTE]
>  如果要使用「商務活動監控」(BAM)，則應該維護專用的追蹤主控件，即使已停用全域追蹤。 這是因為 BAM 事件會使用「追蹤資料解碼服務」(TDDS)。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。  
  
### <a name="to-turn-off-global-tracking-sql-server-2008"></a>若要關閉全域追蹤 (SQL Server 2008)  
  
1.  在裝載 「 BizTalk 追蹤 (BizTalkDTADb) 資料庫的 SQL server 中，按一下 **啟動**，按一下 **程式**，按一下  **Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。  
  
2.  在**連接到伺服器**對話方塊中，確認伺服器名稱和驗證，然後按一下**連接**。  
  
3.  在 Microsoft SQL Server Management Studio 中**物件總管] 中**，依序展開\<*電腦名稱*\>，依序展開**資料庫**，展開**BizTalkMgmtDb**，依序展開**資料表**，以滑鼠右鍵按一下**[adm_group]**，然後按一下 [**開啟資料表**。  
  
4.  在資料表檢視器中水平捲動，直到您找到**[globaltrackingoption]**。  
  
5.  在**[globaltrackingoption]**資料行，將值從 1 變更為 0 時，若要關閉此功能，然後按 ENTER。  
  
6.  關閉 Microsoft SQL Server Management Studio。  
  
    > [!NOTE]
    >  您必須重新啟動 BizTalk 主控件以使變更生效。  
  
7.  按一下**啟動**，按一下 **程式**，指向  **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
8.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後按一下  **主控件執行個體**。  
  
9. 在詳細資料窗格中，以滑鼠右鍵按一下每個主機，然後**重新啟動**。  
  
## <a name="see-also"></a>請參閱  
 [封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)   
 [如何從 BizTalk 追蹤資料庫清除資料](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)   
 [如何從 BizTalk 追蹤資料庫手動清除資料](../core/how-to-manually-purge-data-from-the-biztalk-tracking-database.md)