---
title: 使用 BizTalk Server 記錄傳送災害復原 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d65015c-de53-4590-b644-5c2f66f763db
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2ded5686cc81b1cc3b629601b142a19c3b7b193
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023380"
---
# <a name="using-biztalk-server-log-shipping-for-disaster-recovery"></a>使用 BizTalk Server 記錄傳送災害復原
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 實作資料庫的待命資料庫的功能，透過使用資料庫記錄傳送。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 備份和還原的資料庫和交易記錄檔，可讓待命伺服器，在繼續處理資料庫的可實際執行資料庫伺服器失敗時，會自動執行記錄傳送。  
  
## <a name="how-log-shipping-works"></a>如何記錄 傳送的運作方式  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]所使用的代理程式作業[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送同步處理生產環境中使用的來源伺服器和目的地所使用的伺服器作為備用，以每隔 15 分鐘預設值 （「 備份 BizTalk Server 」 工作執行每個時間） 之間的資料。  
  
## <a name="using-log-shipping-for-disaster-recovery"></a>使用記錄傳送災害復原  
 使用時，請執行下列[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送災害復原：  
  
- 請依照下列主題中的步驟[檢查清單： 增加的可用性與災害復原](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)以提高可用性的生產[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中使用災害復原。  
  
- 請確認嚴重損壞修復伺服器都能夠處理生產負載。  
  
   確定待命伺服器具有相同或類似可用的資源 （CPU/記憶體/磁碟） 做為實際執行伺服器。  
  
- 請確定您的災害復原例行工作的細節有詳細的記錄。  
  
   記錄您的嚴重損壞修復準備工作和實作詳細資料中的每個步驟。 災害通常不絕地時很方便，因此假設負責實作災害復原程序的合作對象開始其第一天運作，而且會進行這第一次。  
  
- 一般測試的做法是容錯移轉至災害復原站台的一部分，特別是為新的 BizTalk 應用程式會放在生產環境中。  
  
   執行測試時的一般測試和維護，以確保它可以執行順暢的容錯移轉。  
  
## <a name="see-also"></a>另請參閱  
 [災害復原](../technical-guides/disaster-recovery.md)