---
title: "何謂 MQSeries 配接器？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, about MQSeries adapters
- MQSeries adapters
ms.assetid: fd3dfa9a-344a-46e5-a342-bc56da7c1c50
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f72d0012050fc8022b53120377aeb648641d21f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-mqseries-adapter"></a>何謂 MQSeries 配接器？
透過 MQSeries 配接器，您就可以使用 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來傳送和接收 MQSeries 系統的訊息。  
  
 此配接器依賴 MQSeries Server for Windows。 此設計會保證可靠的傳訊，因為 MQSeries Server for Windows 支援「Microsoft 分散式交易協調器」(MSDTC)。  
  
 此配接器支援叢集 MQSeries Server、叢集 MQSeries 佇列管理員，以及叢集 BizTalk Server。  
  
 您可以使用 MQSeries 配接器，來執行下列動作：  
  
-   傳送訊息至 MQSeries 遠端定義佇列、本機佇列、傳輸佇列，以及來自 BizTalk Server 的別名佇列。  
  
-   接收來自 MQSeries 傳輸佇列、本機佇列，以及別名佇列的訊息。  
  
-   傳送和接收來自 MQSeries Server for Windows 的訊息，而 MQSeries Server 可以在與 BizTalk Server 相同的電腦或是在遠端安裝上執行。 您只需要部署一個 MQSAgent (配接器的 COM+ 元件) 複本，即可支援所有的 BizTalk Server 安裝。  
  
-   以等待間隔輪詢 MQSeries Server。  
  
-   使用動態傳送埠來控制配接器。  
  
-   在執行階段動態建立查詢。  
  
-   動態接收佇列，根據 MQSeries 比對選項的訊息。  
  
-   針對傳輸和接收訊息，將內容屬性對應到標頭屬性。 您可以透過 BizTalk Server 內容屬性來取得和設定 MQSeries 標頭屬性 (包括 MQMD、MQXQH、MQCIH，以及 MQIIH)。  
  
-   透過 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 或是 MQSeries Server 建立相互關聯識別項來啟用相互關聯。  
  
-   針對要傳送和接收的訊息要求交易式和非交易式傳遞。  
  
> [!NOTE]
>  當使用 MQSeries 這類會對伺服器進行「分散式元件物件模型」(Distributed Component Object Model，DCOM) 呼叫的功能時，請確定您並未啟用「網路位址轉譯」(Network Address Translation，NAT) 架構的防火牆。 用戶端必須能以伺服器的實際 IP 位址來存取伺服器，而 NAT 架構的防火牆會將此位址轉譯為用戶端無法辨識的位址。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [MQSeries 配接器的元件](../core/components-of-the-mqseries-adapter.md)  
  
-   [MQSeries 配接器架構](../core/mqseries-adapter-architecture.md)  
  
-   [使用 MQSeries 配接器](../core/using-the-mqseries-adapter.md)  
  
-   [MQSeries 配接器安全性](../core/mqseries-adapter-security.md)