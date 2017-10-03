---
title: "還原 BizTalk 群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14a9af44-d6de-49c7-9600-21ece389727f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c12a1deff8fea6d769f138aa34bf6dab269a167f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="restoring-the-biztalk-group"></a>還原 BizTalk 群組
BizTalk 群組由一組[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 資料庫、 SSIS 封裝和 SQL 代理程式作業。 本章節描述還原 BizTalk 群組的程序。  
  
 確認需要轉換，轉換為目的系統 （災害復原站台），則必須完成下列步驟：  
  
1.  還原[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和 Analysis Services 資料庫。  
  
2.  還原[!INCLUDE[prague](../includes/prague-md.md)]執行階段伺服器及應用程式。  
  
 完成這些步驟的詳細資訊，BizTalk 群組已建立在災害復原站台，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以設定執行階段伺服器，而且應用程式部署到 BizTalk 群組。 本節中的主題涵蓋在此程序的詳細資料。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [停止處理在來源系統上的應用程式](../technical-guides/stopping-application-processing-on-the-source-system.md)  
  
-   [如何還原 「 備份 BizTalk Server 」 工作中的資料庫](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)  
  
-   [還原資料庫不包含在備份 BizTalk Server 作業](../technical-guides/restoring-databases-not-included-in-the-backup-biztalk-server-job.md)