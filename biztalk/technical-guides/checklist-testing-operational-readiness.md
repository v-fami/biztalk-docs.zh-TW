---
title: 檢查清單： 測試作業整備 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ecdf2609-ba77-4756-a949-ab4e10c54313
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58a10610595b990e6fc2bae1838fa5653a4b2be0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982597"
---
# <a name="checklist-testing-operational-readiness"></a>檢查清單： 測試作業整備
作業整備測試是常被忽略，或只有最少執行的重要程序。 任何企業級應用程式中，關鍵需求是進行徹底測試和開發的方案使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]也不例外。 至少，您應該執行下列測試，再移至生產環境的 BizTalk 解決方案：  


|                                                                                                                                                                                         步驟                                                                                                                                                                                          |                                                  參考                                                  |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
|                                                                                                                                                                                      單元測試                                                                                                                                                                                      |                  [執行單元測試](../technical-guides/performing-unit-testing.md)                  |
|                                                                                                                                                                                   功能測試                                                                                                                                                                                   |            [執行功能測試](../technical-guides/performing-functional-testing.md)            |
|                                                                                                                                                                             瓶頸測試與微調                                                                                                                                                                              | [執行瓶頸測試與調整](../technical-guides/performing-bottleneck-testing-and-tuning.md) |
|                                                                                                                                                                 負載和測試的最大持續輸送量 (MST)                                                                                                                                                                  |   [執行負載和輸送量測試](../technical-guides/performing-load-and-throughput-testing.md)   |
| 可用性測試：<br /><br /> -測試個別硬體元件失敗。<br />-測試[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]失敗。<br />-測試叢集節點容錯移轉。<br />-測試復原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫使用 SQL Server 記錄傳送。 |          [執行可用性測試](../technical-guides/performing-availability-testing.md)          |

## <a name="in-this-section"></a>本節內容  

-   [執行單元測試](../technical-guides/performing-unit-testing.md)  

-   [執行功能測試](../technical-guides/performing-functional-testing.md)  

-   [執行瓶頸測試與調整](../technical-guides/performing-bottleneck-testing-and-tuning.md)  

-   [執行負載和輸送量測試](../technical-guides/performing-load-and-throughput-testing.md)  

-   [執行可用性測試](../technical-guides/performing-availability-testing.md)  

-   [測試的工具](~/technical-guides/tools-for-testing.md)