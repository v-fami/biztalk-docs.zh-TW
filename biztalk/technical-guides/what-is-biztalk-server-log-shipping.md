---
title: "什麼是 BizTalk Server 記錄傳送？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79a2088a-ff36-4590-97c9-51d5bb245486
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3b20589229b1e3868f23c3823d2a26decc56081
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="what-is-biztalk-server-log-shipping"></a>什麼是 BizTalk Server 記錄傳送？
BizTalk Server 嚴重損壞修復程序根據 BizTalk 建立記錄傳送。 BizTalk 記錄傳送可簡化資料庫還原發生災害時持續套用交易記錄更新至災害復原站台資料庫。  
  
 雖然的 BizTalk 記錄傳送根據類似的原則，為[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]記錄傳送，[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]不支援記錄傳送[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]備份資料庫做為備份 BizTalk Server SQL Agent 作業的一部分。  
  
## <a name="how-does-biztalk-log-shipping-work"></a>BizTalk 記錄傳送工作如何？  
 BizTalk 記錄傳送方式，類似於函式[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]記錄傳送。 生產環境[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組設定為備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]UNC 位置的資料庫。 根據預設，備份 BizTalk SQL Agent 作業執行的每個小時的完整備份和記錄備份每隔 15 分鐘。 「 備份 BizTalk Server 」 工作會實作邏輯，以自動啟動完整備份，如果偵測到備份失敗。  
  
 當災害復原[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體已針對 BizTalk 記錄傳送備份 BizTalk Server SQL 代理程式作業會在災害復原站台每隔 15 分鐘預設還原所建立的備份檔案。 SQL 還原命令會透過網路複製備份的檔案。 在下列情況中，只複製完整備份的檔案：  
  
-   第一次設定當 BizTalk 記錄傳送  
  
-   當新的資料庫加入至 「 備份 BizTalk Server 」 工作。  
  
-   當在災害復原站台發生還原失敗  
  
 每個[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]在災害復原站台的執行個體一部分 BizTalk 記錄傳送還原資料庫裝載在實際執行上個別設定[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫執行個體。 當[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體已針對 BizTalk Server 記錄傳送和**BTS 記錄傳送還原資料庫**工作已啟用， **BTS 記錄傳送還原資料庫**作業將會連接到對實際執行的 BizTalk 管理資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。  
  
 如上面所述，當第一次設定目的地伺服器的完整資料庫備份還原到目的地伺服器。 大部分的情況下還原的記錄檔時**BTS 記錄傳送還原資料庫**作業執行。  
  
 檢視嚴重損壞修復時[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]與執行個體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Management Studio 中，資料庫將會顯示在 「 載入 」 的狀態。 這是因為永遠不會自動還原備份組中的最後一個記錄檔。 一旦新的記錄檔可以使用，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送會在下一個還原至最後一個記錄檔。 時就會發生嚴重損壞修復事件和災害復原站台必須上線、 最後一個記錄檔使用 STOPATMARK 命令，將資料庫復原進行還原和資料庫將不再顯示為 「 載入 」 狀態。