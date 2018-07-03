---
title: 什麼是 BizTalk Server 記錄傳送？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79a2088a-ff36-4590-97c9-51d5bb245486
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7735617b0d70aa3c693b1808b07d7670e6137f15
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999335"
---
# <a name="what-is-biztalk-server-log-shipping"></a>什麼是 BizTalk Server 記錄傳送？
BizTalk Server 嚴重損壞修復程序是以 BizTalk 記錄傳送。 BizTalk 記錄傳送發生災害時的資料庫還原藉由簡化了持續到災害復原站台資料庫中套用交易記錄檔更新。  
  
 雖然記錄傳送根據類似的原則，做為 BizTalk[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]記錄傳送，[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]不支援記錄傳送[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]備份資料庫做為備份 BizTalk Server SQL Agent 作業的一部分。  
  
## <a name="how-does-biztalk-log-shipping-work"></a>BizTalk 記錄傳送工作如何？  
 BizTalk 記錄傳送功能，以類似方式[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]記錄傳送。 生產[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組設定為備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]UNC 位置的資料庫。 根據預設，每隔一小時的完整備份和記錄備份每隔 15 分鐘，會執行備份的 BizTalk SQL Agent 作業。 「 備份 BizTalk Server 」 工作會實作邏輯，以自動啟動的完整備份，如果偵測到備份失敗。  
  
 當損毀修復[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體已針對 BizTalk 記錄傳送備份 BizTalk Server SQL 代理程式作業會在災害復原站台每隔 15 分鐘預設還原所建立的備份檔案。 備份檔案會透過網路複製 SQL 還原命令。 只有在下列情況下，會複製完整備份的檔案：  
  
- 第一次設定時 BizTalk 記錄傳送  
  
- 當新的資料庫新增至 「 備份 BizTalk Server 」 工作。  
  
- 還原失敗發生在災害復原站台  
  
  每個[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]在災害復原站台的執行個體一部分 BizTalk 記錄傳送還原資料庫裝載在實際執行上個別設定[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫執行個體。 當[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體設定 BizTalk server 記錄傳送和**BTS 記錄傳送還原資料庫**啟用作業時， **BTS 記錄傳送還原資料庫**作業將會連接到在生產環境的 BizTalk 管理資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。  
  
  如上方所述，當第一次設定目的地伺服器的完整資料庫備份還原到目的地伺服器。 大部分的時間還原的記錄檔時**BTS 記錄傳送還原資料庫**作業執行。  
  
  檢視的災害復原時[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體與[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Management Studio 中，資料庫將會顯示在 「 載入 」 的狀態。 這是因為永遠不會自動還原備份組中的最後一個記錄檔。 一旦新的記錄檔可供使用，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送還原至最後一個記錄檔的下一步。 當在災害復原事件發生和災害復原站台必須上線、 使用 STOPATMARK 命令可將資料庫復原還原最後一個記錄檔和資料庫將不再顯示為處於 「 正在載入 」 狀態。