---
title: "管理成品 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [applications], artifacts
- managing [artifacts]
- artifacts, managing
- managing [artifacts], about managing artificats
ms.assetid: aa7c5e60-7c16-4bcf-b913-b1bdfc5c7543
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ccca48682f009a24f538015b055c45dd79a9587
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-artifacts"></a>管理成品
本節說明如何管理成品，包括如何在 BizTalk 應用程式中新增和移除成品，以及如何設定其屬性。  
  
 成品是 BizTalk 應用程式中包含的項目，應用程式必須有這些項目才能執行。 如需如何使用成品的 BizTalk 應用程式中的背景資訊，請參閱[什麼是 BizTalk 應用程式？](../core/what-is-a-biztalk-application.md) 如需成品的背景資訊，請參閱[執行階段架構](../core/runtime-architecture.md)。 如需管理成品，當您建立和修改 BizTalk 應用程式資訊，請參閱[建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)。  

## <a name="tracking-artifacts"></a>追蹤成品
管理您所建立之成品的大一部分追蹤。 您可以設定各種追蹤選項，在執行階段的協調流程、 傳送埠、 接收埠，以及使用 BizTalk Server 管理主控台的管線。 您可以隨時變更任何項目的追蹤選項，而不需要中斷商務程序。

追蹤組態設定可讓您追蹤下列資料類型：

- 輸入和 (或) 輸出事件資料。 例如，訊息識別碼、成品的啟動與停止時間。

- 輸入和 (或) 輸出訊息屬性。 例如，成品所處理的每個訊息的一般和升級屬性。

- 輸入和 (或) 輸出訊息內文和部分。 例如，成品所處理的每個訊息的內文和部分。

- 協調流程。 協調流程圖形的執行資料。

[檢視追蹤訊息及執行個體資料](../core/viewing-tracked-message-and-instance-data.md)提供資訊很有用。 


> [!TIP]
> 如果您設定管線的追蹤選項，然後追蹤選項會全域設定的每個管線所使用的連接埠。 這會導致更多超過您可能想要而且可能會影響系統效能正在追蹤的資料。 在開發期間，這可能是正常現象。 在生產案例中，我們建議您啟用任何追蹤選項，傳送埠和接收埠，而不是管線。
  
## <a name="in-this-section"></a>本節內容  
  
-   [管理協調流程](../core/managing-orchestrations.md)  
  
-   [管理角色連結](../core/managing-role-links.md)  
  
-   [管理傳送埠與傳送埠群組](../core/managing-send-ports-and-send-port-groups.md)  
  
-   [管理接收埠](../core/managing-receive-ports.md)  
  
-   [管理接收位置](../core/managing-receive-locations.md)  
  
-   [管理原則](../core/managing-policies.md)  
  
-   [管理結構描述](../core/managing-schemas.md)  
  
-   [管理對應](../core/managing-maps.md)  
  
-   [管理管線](../core/managing-pipelines.md)  
  
-   [管理資源](../core/managing-resources.md)