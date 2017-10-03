---
title: "如何備份 BizTalk Server 組態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14f89050-c204-4d44-a875-299e690489ef
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad54aba8f8f49adeb8534bdbe28add15f0fe9638
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-back-up-the-biztalk-server-configuration"></a>如何備份 BizTalk Server 組態
做為備份的一部分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您應該備份執行的電腦相關聯的組態設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 當您遇到硬體失敗而需要更換電腦時，如果預先備有原始組態檔的複本，就能大幅簡化還原程序。  
  
 執行每一部電腦的組態設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會儲存在 BizTalk Server 組態管理員 」 建立的 XML 檔案。 每當變更 BizTalk Server 組態時，您應該將更新的組態檔匯出至備份位置。 這有助於確保組態檔可在必須更換 BizTalk Server 的狀況中派上用場。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 BizTalk Server 系統管理員群組的成員身分登入，才能執行這個程序。  
  
### <a name="to-back-up-the-biztalk-server-configuration"></a>備份 BizTalk Server 組態  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft BizTalk Server**，然後按一下  **BizTalk Server 組態**。  
  
2.  在**Microsoft BizTalk Server 組態**，按一下 **匯出組態**。  
  
3.  在**存**對話方塊中，瀏覽至您用來儲存備份的位置。  
  
4.  在**檔案名稱**方塊中，輸入組態檔的名稱，然後按一下**儲存**。  
  
## <a name="see-also"></a>另請參閱  
 [備份執行 BizTalk Server 的電腦](../core/backing-up-a-computer-running-biztalk-server.md)   
 [如何復原 BizTalk Server 組態](../core/how-to-recover-the-biztalk-server-configuration.md)