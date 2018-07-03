---
title: 正在還原 BizTalk 群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 14a9af44-d6de-49c7-9600-21ece389727f
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9bea20bacdd6b681d39e2bf3995d7626b9b1f63
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021638"
---
# <a name="restoring-the-biztalk-group"></a>正在還原 BizTalk 群組
BizTalk 群組由一組[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 資料庫、 SSIS 封裝和 SQL Agent 作業。 本章節描述還原 BizTalk 群組的程序。  
  
 轉換，轉換為目的系統 （災害復原站台） 是必要的則必須完成下列步驟：  
  
1. 還原[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和 Analysis Services 資料庫。  
  
2. 還原 BizTalk Server 執行階段伺服器和應用程式。  
  
   完成這些步驟的詳細資訊，BizTalk 群組已在災害復原站台，建立[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以設定執行階段伺服器，而且應用程式可以部署到 BizTalk 群組。 在本節中的主題涵蓋了此程序的詳細資料。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [停止來源系統上的應用程式處理](../technical-guides/stopping-application-processing-on-the-source-system.md)  
  
-   [如何在備份 BizTalk Server 作業中還原資料庫](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)  
  
-   [還原不包含在備份 BizTalk Server 作業中的資料庫](../technical-guides/restoring-databases-not-included-in-the-backup-biztalk-server-job.md)