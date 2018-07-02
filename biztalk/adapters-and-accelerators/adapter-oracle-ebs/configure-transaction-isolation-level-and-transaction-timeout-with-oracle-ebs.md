---
title: 使用 Oracle E-business Suite 設定交易隔離等級和交易等待時間 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db3d64ad-037d-486a-bdde-45c8199613f1
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8bbff645105feb4732afdf86aa3a591252c0d88c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969214"
---
# <a name="configure-transaction-isolation-level-and-transaction-timeout-with-oracle-e-business-suite"></a>使用 Oracle E-business Suite 設定交易隔離等級和交易等待時間
在執行輸入的作業 （「 輪詢 」 和 「 通知 」） 時使用[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您應該適當地設定交易隔離等級和交易逾時值。 若要這樣做：  

1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

2. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。  

3. 在產生中繼資料的使用之後，您已部署的 BizTalk 應用程式[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  

4. 以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**。  

5. 在 **接收埠屬性**對話方塊的 **一般**索引標籤上，輸入接收埠的名稱。  

6. 在左窗格中**接收埠屬性** 對話方塊中，按一下**接收位置**，然後按一下**新增**右邊的窗格，即可定義新接收位置。  

7. 在 [**接收位置屬性**] 對話方塊中，按一下**Wcf-custom**中**型別**清單。  

8. 按一下 **設定**相鄰**型別**清單。  

9. 在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**行為** 索引標籤。  

10. 在**行為**清單中，以滑鼠右鍵按一下**ServiceBehavior**，然後按一下**新增擴充功能**。  

11. 在 [**選取行為延伸模組**] 對話方塊中，選取**oracleEBSAdapterInboundTransactionBehavior**，然後按一下 **[確定]**。  

12. 在左窗格中**Wcf-custom 傳輸屬性**，選取**oracleEBSAdapterInboundTransactionBehavior**服務**ServiceBehavior**。  

13. 在右窗格中**Wcf-custom 傳輸屬性**，指定適當的值，如**transactionIsolationLevel**並**transactionTimeout**參數。 您可以選取任何下列的交易隔離等級： **Serializable**， **RepeatableRead**， **ReadCommitted**， **ReadUncommitted**，**快照集**，**混亂**，和**未指定**。 如需這些交易隔離等級的詳細資訊，請參閱**成員**一節[ http://go.microsoft.com/fwlink/?LinkId=126983 ](http://go.microsoft.com/fwlink/?LinkId=126983)。  

    > [!IMPORTANT]
    >  Oracle E-business Suite 支援只有下列兩個交易隔離等級： ReadCommitted 和 Serializable。  

     ![設定交易隔離層級](../../adapters-and-accelerators/adapter-oracle-ebs/media/2bafbb9d-4daa-43c0-abcb-35220e6a3cb5.gif "2bafbb9d-4daa-43c0-abcb-35220e6a3cb5")  

14. 按一下 [ **[確定]** 中**Wcf-custom 傳輸屬性**] 對話方塊。  

15. 按一下 **確定**在開啟對話方塊，來儲存所做的變更。
