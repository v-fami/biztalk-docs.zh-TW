---
title: 範例架構： BizTalk 訊息佇列 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, security
- Message Queuing binary protocol
- architecture, examples
- security, examples
- security, architecture
- examples, architecture
- MSMQ adapters, security
- architecture, security
- MSMQ adapters, architecture examples
- servers, Windows Message Queuing
- Windows Message Queuing
- message queuing adapters
ms.assetid: a660c798-1c45-4759-a6c8-f11550683a31
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f38d373680fd1b47722fc1ac52c56b113ef59cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269790"
---
# <a name="sample-architecture-biztalk-message-queuing"></a>範例架構： BizTalk 訊息佇列
當您使用 「 BizTalk 訊息佇列配接器傳送和接收訊息時，本主題描述的範例架構。  
  
 下圖顯示使用 BizTalk 訊息佇列配接器時 BizTalk Server 範例架構的元件。  
  
 **圖 1 顯示 BizTalk 訊息佇列配接器的範例架構**  
  
 ![BizTalk 訊息佇列的範例架構](../core/media/tdi-sec-refarch-msmq.gif "TDI_Sec_RefArch_MSMQ")  
  
 此範例架構包含下列章節所討論的元件。  
  
## <a name="perimeter-networkinternet"></a>周邊網路─網際網路  
 我們不建議在網際網路上使用訊息佇列二進位通訊協定。 您不應該讓任何訊息佇列流量通過防火牆 1。 如果您想要使用 BizTalk 訊息佇列配接器，透過網際網路接收訊息，執行下列作業：  
  
-   在周邊網路中使用訊息佇列伺服器。  
  
-   透過網際網路使用訊息佇列 HTTP 通訊協定。  
  
-   周邊網路中有個轉送應用程式，它會拾取來自訊息佇列伺服器的訊息，然後使用二進位通訊協定轉送到 BizTalk 訊息佇列配接器。  
  
    > [!IMPORTANT]
    >  即使您使用 BizTalk 訊息佇列從網際網路接收訊息，在防火牆 1 上仍必須讓 BizTalk 訊息佇列使用的連接埠保持關閉狀態。  
  
## <a name="perimeter-networkintranet"></a>周邊網路─內部網路  
 當您使用 BizTalk 訊息佇列配接器從內部網路接收訊息時，有一個 Windows 訊息佇列伺服器會將訊息佇列流量轉送到 BizTalk Server，而此 BizTalk Server 是執行 BizTalk 訊息佇列配接器的主控件執行個體。  
  
 若內部網路與電子商務網域共用一般的 Active Directory，訊息會通過一系列的訊息佇列路由器，直到它抵達正確的目的地 (執行 BizTalk 訊息佇列接收配接器的主控件執行個體的 BizTalk Server)。 這個選項未顯示在圖中，因為它沒有第一個選項安全。  
  
## <a name="e-business-domain"></a>電子商務網域  
 此網域中的伺服器包括：  
  
-   **BizTalk Server （處理、 BizTalk 訊息佇列配接器以及追蹤主控件）。** 此伺服器有 BizTalk Server 執行階段安裝，而且擁有主控件執行個體，其中包含 BizTalk 協調流程、管線、商務規則引擎以及其他商務程序。 這是 BizTalk Server 連接埠、接收位置、管線、對應、結構描述以及組件的位置，用來接收、傳遞、處理和傳送訊息。 此伺服器還有可支援追蹤狀況監控與商務監控資料之主控件的主控件執行個體。 此外，此主控件還包含執行 BizTalk 訊息佇列傳送與接收配接器的主控件執行個體。  
  
    > [!NOTE]
    >  當您的效能需求增加時，可以為處理主控件的主控件執行個體在環境中加入更多 BizTalk Server。  
  
-   **主要密碼伺服器。** 中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。  
  
-   **SQL Server。** 中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。  
  
-   **網域控制站。** 中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。  
  
-   **系統管理工具。** 中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [小型與中型公司的範例架構](../core/sample-architectures-for-small-medium-sized-companies.md)   
 [威脅模型分析的範例案例](../core/sample-scenarios-for-threat-model-analysis.md)