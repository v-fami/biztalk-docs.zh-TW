---
title: 設定交易隔離等級和交易逾時與 Oracle 資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b66e764-2330-441b-89ef-29118f27b366
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13d1beea3be34dbd818a94986fb8cae876bcdd81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214510"
---
# <a name="configure-transaction-isolation-level-and-transaction-timeout-with-oracle-database"></a>設定 Oracle 資料庫的交易隔離等級和交易逾時
執行傳入的作業 （輪詢） 使用時[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您應該適當地設定交易隔離等級和交易逾時值。 若要這樣做：  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  展開產生的中繼資料使用之後，您已部署的 BizTalk 應用程式[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
4.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。  
  
5.  在**接收埠屬性**對話方塊**一般**索引標籤上，輸入接收埠的名稱。  
  
6.  在左窗格中**接收埠屬性**對話方塊中，按一下 **接收位置**，然後按一下 **新增**在右窗格來定義新接收位置。  
  
7.  在**接收位置屬性**對話方塊中，按一下  **Wcf-custom**中**類型**清單。  
  
8.  按一下**設定**相鄰**類型**清單。  
  
9. 在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**行為**] 索引標籤。  
  
10. 在**行為**清單中，以滑鼠右鍵按一下**ServiceBehavior**，然後按一下**將延伸加入**。  
  
11. 在**選取行為延伸模組**對話方塊中，選取**oracleDBAdapterInboundTransactionBehavior**，然後按一下**確定**。  
  
12. 在左窗格中**Wcf-custom 傳輸屬性**，選取**oracleDBAdapterInboundTransactionBehavior**服務**ServiceBehavior**。  
  
13. 在右窗格中**Wcf-custom 傳輸屬性**，指定適當的值**transactionIsolationLevel**和**transactionTimeout**參數。 您可以選取任何下列的交易隔離等級： **Serializable**， **RepeatableRead**， **ReadCommitted**， **ReadUncommitted**，**快照**， **Chaos**，和**未指定**。 如需這些交易隔離等級的資訊，請參閱**成員**區段在[http://go.microsoft.com/fwlink/?LinkId=126983](http://go.microsoft.com/fwlink/?LinkId=126983)。  
  
    > [!IMPORTANT]
    >  [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援只有下列兩個交易隔離等級： ReadCommitted 和 Serializable。  
  
     ![設定交易隔離層級](../../adapters-and-accelerators/adapter-oracle-database/media/96a66f86-0321-4aa6-9e72-ada30d7de064.gif "96a66f86-0321-4aa6-9e72-ada30d7de064")  
  
14. 按一下**確定**中**Wcf-custom 傳輸屬性** 對話方塊。  
  
15. 按一下**確定**中將變更儲存開啟的對話方塊。