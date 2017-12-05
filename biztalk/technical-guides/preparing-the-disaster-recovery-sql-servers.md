---
title: "正在準備嚴重損壞修復的 SQL Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44b77fe8-393d-4781-b0b0-5b7f6e50a67b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47bd787fe5fa33a30f01bc37fd4988ab26db99d1
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="preparing-the-disaster-recovery-sql-servers"></a>正在準備嚴重損壞修復的 SQL Server
建立一組[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫在災害復原站台的執行個體。 若要確認嚴重損壞修復[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫執行個體可以提供相同等級的生產環境的效能[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫執行個體、 嚴重損壞修復[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫執行個體應該使用 「 類似設定硬體和執行的實體電腦數目[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 在此案例中，記錄傳送將會針對每個實際執行的 BizTalk Server[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]要套用至相對應的資料庫執行個體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]在災害復原站台資料庫執行個體。  
  
 BizTalk Server 記錄傳送要求的索引鍵是磁碟機代號儲存資料庫檔案將生產站台上的磁碟區符合磁碟機代號在災害復原站台還原 」 資料庫檔案的磁碟區。 因此，如果[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫檔案群組位於 G:\data 在生產環境中，在目的地 (DR) 伺服器上，必須有 G:\data 目錄或還原將會失敗。  
  
 BizTalk Server 記錄傳送不支援**RESTORE WITH MOVE** [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]命令。 因此，我們建議在災害復原站台資料庫執行個體名稱是否符合在生產環境中的資料庫執行個體名稱 （根據預設，執行個體名稱是檔案路徑的一部分）。 另一個選項是直接在對應的磁碟機代號，執行災害復原電腦上建立目錄[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]以便**還原**作業可以建立檔案相同的目錄結構中使用中生產環境。  
  
 建立[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]對應至生產網站，如此，需要容錯移轉至災害復原站台，則所有必要的安全性登入的災害復原站台的安全性登入都存在於目的系統。  
  
 一次的嚴重損壞修復的安裝[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]完成時執行個體，執行 master 和 msdb 資料庫的完整備份，如此可切換至災害復原站台失敗時，就可以還原乾淨系統。