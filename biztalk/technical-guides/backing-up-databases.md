---
title: 備份資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0524a8f0-15a3-4731-a7bd-c0c935fff6c8
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6a4b40be0a9a7d4846dd965a4d9f934e69690e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22300534"
---
# <a name="backing-up-databases"></a>備份資料庫
因為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用分散式交易，跨多個資料庫時，「 備份 BizTalk Server 」 工作建立的所有同步的備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 這被透過使用標示的交易具有 「 完整 」 資料庫復原模式。 這是必要的備份，以跨資料庫交易一致。 如需詳細資訊，請參閱["標示的交易、 完整備份和記錄備份 」](http://go.microsoft.com/fwlink/?LinkId=151565) (http://go.microsoft.com/fwlink/?LinkId=151565) 中的 BizTalk Server 文件。  
  
## <a name="advantages-of-the-backup-biztalk-server-job"></a>「 備份 BizTalk Server 」 工作的優點  
 「 備份 BizTalk Server 」 工作是唯一支援的方法來備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]備份作業[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不支援在生產環境中的資料庫。  
  
 如果備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]無法執行作業，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫交易記錄檔將會無限制的成長。 備份作業會截斷交易記錄檔，讓它們保持無限制成長。 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫交易記錄檔持續成長，它們無法在某個時間點填滿它們裝載於該磁碟。  
  
> [!NOTE]  
>  使用這兩種備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業和記錄傳送 是目前唯一完整記載的支援方法來執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]database 備份和還原。  
  
## <a name="guidelines-for-the-backup-biztalk-server-job"></a>「 備份 BizTalk Server 」 工作的指導方針  
 您應該在還原整個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]以規則為基礎的環境。 這包括不只是 SQL server 和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，但也在執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 您應該將文件，並實施這些程序，才能實際發生失敗。  
  
> [!NOTE]  
>  備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業不會刪除舊的備份檔案。 您必須定義，並將處理程序在封存舊的備份檔案，並將它們移到備份作業使用的備份目錄的位置。  
  
## <a name="additional-resources"></a>其他資源  
 請參閱下列主題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]文件：  
  
-   如需有關特定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]備份和還原工作，請參閱[「 檢查清單:: 備份和還原 」](http://go.microsoft.com/fwlink/?LinkId=154070) (http://go.microsoft.com/fwlink/?LinkId=154070)。  
  
-   如需備份和還原的概觀[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[」 備份和還原 BizTalk Server 」](http://go.microsoft.com/fwlink/?LinkId=154071) (http://go.microsoft.com/fwlink/?LinkId=154071)。  
  
-   如需有關如何設定 「 備份 BizTalk Server 」 工作的詳細資訊，請參閱[「 方式來設定備份 BizTalk Server 作業 」](http://go.microsoft.com/fwlink/?LinkId=154072) (http://go.microsoft.com/fwlink/?LinkId=154072)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 記錄傳送災害復原](../technical-guides/using-biztalk-server-log-shipping-for-disaster-recovery.md)