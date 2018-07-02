---
title: 從暖備份還原生產 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bda14b8-b3cc-4a5e-a353-fca5885fd594
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66177cd1f6f10e252a71d2875b4079e660125719
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971359"
---
# <a name="restoring-production-from-a-warm-backup"></a>從暖備份還原生產環境
如果來源系統變得不可靠，您可從目的地的資料庫還原至原始檔。 執行下列程序，將來自目的地的資料庫還原至原始檔。  
  
### <a name="to-restore-the-databases-from-the-destination-to-the-source-follow-these-steps"></a>若要還原目的地的資料庫來源請遵循下列步驟  
  
1. 停用來源 （生產） 上的所有備份工作[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。  
  
2. 所有還原目的地的災害復原 (DR) 上完成的工作等候[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。  
  
3. 停用的目的地 (DR) 上的所有還原作業[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。  
  
4. 還原所有資料庫與目的地 (DR) 上的 STOPATMARK[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。  
  
5. 停止所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]所有 BizTalk 伺服器上的服務。  
  
6. 卸除所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-相關來源 （生產） 上的資料庫[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。  
  
7. 所有資料庫 （完整） 都備份目的地 (DR) 上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。  
  
8. 還原 （完整） 與所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫備份在步驟 7 到來源 （生產）[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。  
  
9. 重新啟動所有 BizTalk 伺服器，包括主要密碼伺服器。  
  
10. 卸除所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-相關的目的地 (DR) 上的資料庫[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。  
  
11. 啟用來源上的備份作業[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。  
  
12. 啟用目的地 (DR) 上的還原作業[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [備份和 Restore2 進階的資訊](../technical-guides/advanced-information-about-backup-and-restore2.md)