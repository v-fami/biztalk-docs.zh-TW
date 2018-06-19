---
title: 如何調整組態快取重新整理間隔 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 63c6c998-e9c0-48f1-a36a-f1fcb916321b
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad9459fadd65af220982ab31ae0e464cb7f1986e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22297878"
---
# <a name="how-to-adjust-the-configuration-cache-refresh-interval"></a>如何調整組態快取重新整理間隔
設定快取重新整理間隔會定義 BizTalk Server 中更新端點的組態的時間週期。 當您啟動 BizTalk Server 時，BizTalk Server 管理，例如 MessageBox 資料庫、 伺服器屬性、 配接器，以及到追蹤資料庫的連接中的所有項目會儲存在設定快取。 快取中的所有項目會由組態重新整理間隔重新整理。 根據預設，這是每隔 60 秒，但伺服器資料庫連線和伺服器屬性除外。 這表示，如果您變更 BizTalk 群組，例如 SMTP 主機的一般屬性所做的變更會收取 60 秒內。 系統目前開啟的執行個體的 BizTalk Server 管理主控台之外所做的變更不會反映您重新整理之前。  
  
 設定快取重新整理間隔是 BizTalk 群組屬性的一部分。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須為 BizTalk Server 系統管理員群組的成員登入。  
  
### <a name="to-adjust-the-cache-refresh-interval"></a>若要調整快取重新整理間隔  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下**設定**。  
  
3.  在**BizTalk 設定儀表板**對話方塊中，選取**一般** 索引標籤。如**組態重新整理間隔**屬性，輸入或選取的時間 （以秒為單位） 的所有項目中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理快取必須設定快取重新整理，之間等候，然後按 **[確定]**.  
  
    > [!NOTE]  
    >  重新整理時所涵蓋的項目包括 MessageBox 資料庫、伺服器屬性、配接器，以及追蹤資料庫的連線。  
  
    > [!NOTE]  
    >  根據預設，設定快取中的所有物件會重新都整理每隔 60 秒，但伺服器資料庫連線和伺服器屬性除外。