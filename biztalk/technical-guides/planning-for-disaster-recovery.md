---
title: "規劃災害復原 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a33e8875-cfde-4a60-9dab-fc6bb3ac4f1c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3619a34c843665750abd4f5d852b0f1af5210e1c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="planning-for-disaster-recovery"></a>規劃損毀復原
本主題提供災害復原需求的應用程式小組和 BizTalk Server 程序指引。 Microsoft BizTalk Server 會儲存在組態和處理資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 BizTalk Server 高可用性和災害復原透過的高可用性和災害復原功能來達成[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。  
  
 BizTalk 群組由一組資料庫裝載於[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 一組資料庫裝載於[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]可以成為高可用性，透過使用 Windows Server 叢集。 在 BizTalk 環境中，執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供執行的電腦上的 [執行階段環境] 及資料庫[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]提供環境的持續性存放區。 因此，BizTalk Server 備份、 還原和災害復原程序經常會著重於[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。  
  
## <a name="purpose"></a>目的  
 本主題彙總[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]嚴重損壞修復資訊的核心文件、 各種 Microsoft 網站，而且從資訊從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]定義嚴重損壞修復程序的產品小組[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  
  
 應用程式小組應徹底測試備份、 還原和災害復原程序。 您也應該確定程序會調整以符合再進入實際執行的應用程式的需求。  
  
## <a name="scope"></a>範圍。  
 本節著重於嚴重損壞修復程序適用於 BizTalk Server 和相關的程序[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 本指南是根據有關如何備份和還原 BizTalk Server 的相關文件。  
  
 如需有關備份和還原的詳細資訊，請參閱這份文件，請參閱[備份和還原 BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=154071) (http://go.microsoft.com/fwlink/?LinkID=154071) 在 BizTalk Server 說明中。 每個應用程式的小組必須擴充文件的電腦名稱、 磁碟機代號，例如其環境特有的其他程序與本主題中的資訊和相關的叢集設定，以及嚴重損壞修復程序這些方案的一部分的非 BizTalk 應用程式。  
  
 本主題不提供詳細的嚴重損壞修復程序的下列區域：  
  
-   非 BizTalk 應用程式  
  
-   應用程式的原始程式碼  
  
-   憑證  
  
-   應用程式作業  
  
 可能有需要，以上未列出的應用程式的災害復原方案中的文件必須處理的每個應用程式小組的其他區域。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [災害復原的最佳做法](../technical-guides/best-practices-for-disaster-recovery.md)  
  
-   [什麼是 BizTalk Server 記錄傳送？](../technical-guides/what-is-biztalk-server-log-shipping.md)