---
title: 使用 BizTalk Server 記錄傳送災害復原 |Microsoft 文件
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
ms.openlocfilehash: 16f2cf9e1d8b717ff42536ef9c0dba79132b9663
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302294"
---
# <a name="using-biztalk-server-log-shipping-for-disaster-recovery"></a>使用 BizTalk Server 記錄傳送災害復原
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]實作資料庫待命的功能，透過使用資料庫記錄傳送。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送會自動備份和還原的資料庫和交易記錄檔，允許繼續處理的實際執行資料庫伺服器失敗，資料庫的待命伺服器。  
  
## <a name="how-log-shipping-works"></a>如何記錄檔傳送運作  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]所使用的代理程式作業[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送同步處理在生產環境中使用的來源伺服器與目的地伺服器作為備用，以每隔 15 分鐘預設使用 （每個 「 備份 BizTalk Server 」 工作執行的時間） 之間的資料。  
  
## <a name="using-log-shipping-for-disaster-recovery"></a>使用記錄傳送災害復原  
 執行下列動作時使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送災害復原：  
  
-   遵循本主題中的步驟[檢查清單： 提高可用性與災害復原](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)以提高可用性生產[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中使用災害復原。  
  
-   請確認嚴重損壞修復伺服器有能力處理生產負載。  
  
     確定待命伺服器具有相同或類似可用的資源 （CPU/記憶體/磁碟） 做為實際執行伺服器。  
  
-   請確定您的災害復原常式的細節會完善記載。  
  
     您的嚴重損壞修復的準備和實作詳細資料中的每個步驟的文件。 嚴重損壞很少攻擊時很方便，我們假設負責實作嚴重損壞修復程序的合作對象，開始其第一天的工作，而且會進行這個第一次。  
  
-   一般測試的作法是容錯移轉至災害復原站台的一部分，尤其是以新的 BizTalk 應用程式會放在生產環境中。  
  
     執行測試時的一般測試和維護，以確保它可以執行順暢的容錯移轉。  
  
## <a name="see-also"></a>另請參閱  
 [嚴重損壞修復](../technical-guides/disaster-recovery.md)