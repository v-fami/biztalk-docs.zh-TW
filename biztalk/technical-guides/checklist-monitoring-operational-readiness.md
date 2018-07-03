---
title: 檢查清單： 監視作業整備 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef77ccc2-1d39-4e78-8fea-5c17d05c8174
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfd8b5ead6ceea7154e7f035d16f3c0fba7be1d4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021940"
---
# <a name="checklist-monitoring-operational-readiness"></a>檢查清單： 監視作業整備
本主題列出監視生產環境時，您應該遵循的步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  


|                                                                                                                                                                      步驟                                                                                                                                                                       |                                                                                                  參考                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                                                           選取並實作您的 BizTalk 應用程式和基礎結構的監視策略。                                                                                                                           |                                                [監視 BizTalk Server 環境](../technical-guides/monitoring-the-biztalk-server-environment.md)                                                 |
|                                                                                                                                                            監視磁碟空間使用量。                                                                                                                                                             |                                                              [監視磁碟空間使用量](../technical-guides/monitoring-disk-space-usage.md)                                                               |
| 監視 SQL Server:<br /><br /> -確認執行 SQL Server 外罩該電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]受監視的資料庫。<br />-確認[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]受監視的工作。 |            -   [監視 SQL Server](../technical-guides/monitoring-sql-servers.md)<br />-   [監視 BizTalk Server 資料庫](../technical-guides/monitoring-biztalk-server-databases.md)            |
|          監控 BizTalk 應用程式：<br /><br /> -修改現有的規則和/或複製的規則，以自訂的管理組件來監視自訂的 BizTalk 應用程式。<br />-建立每個已定義的規則的動作。<br />-建立反覆的程序，以將手動工作自動化。<br />-使用臨界值規則以將手動工作自動化。          | -   [監視應用程式和主控件執行個體](../technical-guides/monitoring-applications-and-host-instances.md)<br />-   [監視 BizTalk Server2](../technical-guides/monitoring-biztalk-server2.md) |

## <a name="in-this-section"></a>本節內容  

-   [監視磁碟空間使用量](../technical-guides/monitoring-disk-space-usage.md)