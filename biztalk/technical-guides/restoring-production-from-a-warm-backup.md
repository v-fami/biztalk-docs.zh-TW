---
title: 從暖備份還原生產 |Microsoft 文件
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
ms.openlocfilehash: 8e590b4eccb6ee946a915ff1f3a0265bbfe977e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302086"
---
# <a name="restoring-production-from-a-warm-backup"></a>從暖備份還原生產環境
如果來源系統變得不可靠，它可能會從目的地將資料庫還原到來源。 執行下列程序，從目的資料庫還原到來源。  
  
### <a name="to-restore-the-databases-from-the-destination-to-the-source-follow-these-steps"></a>若要還原目的地的資料庫來源請遵循下列步驟  
  
1.  停用來源 （生產環境） 上的所有備份作業[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體。  
  
2.  所有還原目的地的災害復原 (DR) 上完成的作業等候[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體。  
  
3.  停用所有的還原作業的目的地 (DR) 上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體。  
  
4.  還原所有資料庫與目的地 (DR) 上的 STOPATMARK[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體。  
  
5.  停止所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]所有 BizTalk 伺服器上的服務。  
  
6.  卸除所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-相關資料庫 （生產環境） 在來源上的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體。  
  
7.  所有資料庫 （完整） 都備份目的地 (DR) 上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體。  
  
8.  還原 （完整） 所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫備份在步驟 7 到來源 （生產環境）[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體。  
  
9. 重新啟動所有 BizTalk 伺服器，包括主要密碼伺服器。  
  
10. 卸除所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-相關資料庫的目的地 (DR) 上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體。  
  
11. 啟用來源上的備份作業[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體。  
  
12. 啟用目的地 (DR) 上的還原作業[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [備份和 Restore2 的進階的資訊](../technical-guides/advanced-information-about-backup-and-restore2.md)