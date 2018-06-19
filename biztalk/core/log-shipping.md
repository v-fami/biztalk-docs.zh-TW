---
title: 記錄傳送 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- backing up, log shipping
- log shipping
ms.assetid: 25bc9724-1c99-43d0-8cd1-3ed8eaa60268
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5bd90e23fc99988bb134a77befe3195ca507037d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262110"
---
# <a name="log-shipping"></a>記錄傳送
記錄傳送提供待命伺服器功能，有時稱為暖備份，發生系統錯誤時可減少停機時間。  
  
 由於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的分散式資料庫設計，當您產生備份時，必須要提供一致的位置以便還原備份。 交易可以跨越多個資料庫；如果一個資料庫離線且必須要還原，則所有相關的資料庫都必須即時還原到單一位置，以確保系統保持一致的狀態。 並非所有資料庫都參與分散式交易。 如需詳細資訊，請參閱[Backing Up and Restoring BizTalk Server 資料庫](../core/backing-up-and-restoring-the-biztalk-server-databases.md)。  
  
 「備份 BizTalk Server」工作會使用 Microsoft SQL Server 記錄檔標示，以提供自動化程序來產生資料庫備份集。 這些備份集包括同步處理的位置，可在還原程序期間使用。 做為還原由「備份 BizTalk Server」工作產生一組資料庫的部分程序，使用倒數第二個標示，將每個資料庫的最後一個記錄備份檔案還原為特定的記錄標示。 這可讓您將資料庫還原為一致的狀態，大幅減少資料遺失的數量。 應該使用倒數第二個記錄標示。 雖然 SQL Server 包含記錄傳送功能，您應該只在備份和還原 BizTalk Server 資料庫時使用 BizTalk Server 記錄傳送功能。  
  
> [!NOTE]
>  SQL Server 簡單復原模式不支援搭配 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫使用，因為簡單復原模式不會備份交易記錄，因此無法維護最近一次備份後的活動記錄內容。  將 SQL Server 設定為使用完整復原模式，可以確保 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫備份集的資料完整性。  
  
## <a name="see-also"></a>另請參閱  
 [備份和還原的相關進階的資訊](../core/advanced-information-about-backup-and-restore1.md)