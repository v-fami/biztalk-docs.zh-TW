---
title: 規劃災害復原 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a33e8875-cfde-4a60-9dab-fc6bb3ac4f1c
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43f90723634a7192d6b8908a37f5d62fa2476997
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006119"
---
# <a name="planning-for-disaster-recovery"></a>規劃損毀復原
本主題提供災害復原需求的應用程式小組和 BizTalk server 的程序的指導方針。 Microsoft BizTalk Server 會儲存在組態和處理資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 BizTalk Server 高可用性和災害復原可透過高可用性和災害復原功能的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。  
  
 BizTalk 群組由一組資料庫裝載於[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 一組資料庫裝載於[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]可以成為高可用性使用 Windows Server 叢集。 在 BizTalk 環境中，執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供執行的電腦上的 「 執行階段環境 」 和資料庫[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]提供環境的持續性存放區。 因此，BizTalk Server 備份、 還原及災害復原的程序大量著重於[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。  
  
## <a name="purpose"></a>目的  
 本主題彙總[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]災害復原的資訊的核心文件、 各大 Microsoft 網站和來自[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]定義的嚴重損壞修復程序的產品小組[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  
  
 應用程式小組應該徹底測試備份、 還原及災害復原程序。 您也應該確定程序需求量身訂做應用程式需求後，再進入生產環境。  
  
## <a name="scope"></a>範圍。  
 本節著重於災害復原程序適用於 BizTalk Server 和相關的程序[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 本指南是根據有關如何備份和還原 BizTalk Server 的相關文件。  
  
 如需有關備份和還原的詳細資訊，請參閱這份文件，並查看[備份和還原 BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=154071) (http://go.microsoft.com/fwlink/?LinkID=154071)在 BizTalk Server 說明中。 每個應用程式小組必須加強環境，例如文件的電腦名稱、 磁碟機代號，特定的其他程序與本主題中的資訊和相關的叢集組態中，以及嚴重損壞修復程序為解決方案一部分的非 BizTalk 應用程式。  
  
 本主題不提供詳細的嚴重損壞修復程序的下列區域：  
  
- 非 BizTalk 應用程式  
  
- 應用程式來源程式碼  
  
- 憑證  
  
- 應用程式作業  
  
  可能需要在其上方未列出的應用程式的災害復原計劃中的文件必須解決每個應用程式小組的其他區域。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [災害復原的最佳做法](../technical-guides/best-practices-for-disaster-recovery.md)  
  
-   [什麼是 BizTalk Server 記錄傳送？](../technical-guides/what-is-biztalk-server-log-shipping.md)