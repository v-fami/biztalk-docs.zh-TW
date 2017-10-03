---
title: "範例架構： File 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, security
- architecture, examples
- File adapters, security
- security, examples
- security, architecture
- examples, architecture
- architecture, security
- File adapters, architecture examples
ms.assetid: fdcbba0c-e301-46ce-8940-d617232cafbd
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11884786f743ece21a8009ea339a251b107420c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architecture-file-adapter"></a>範例架構： File 配接器
當您使用 File 配接器傳送和接收訊息時，本主題描述的範例架構。  
  
## <a name="file-adapter-components"></a>FILE 配接器元件  
 下圖顯示使用 FILE 配接器時 BizTalk Server 範例架構的元件。  
  
> [!NOTE]
>  此範例架構也適用於使用 EDI 配接器時。  
  
 **圖 1 顯示 File 配接器的範例架構**  
  
 ![範例檔案配接器的架構](../core/media/tdi-sec-refarch-file.gif "TDI_Sec_RefArch_File")  
  
 此範例架構包含以下各節所討論的元件。  
  
## <a name="perimeter-network-internet"></a>周邊網路-網際網路  
 公司通常會使用 File 通訊協定來進行內部網路通訊，因此網際網路周邊網路中不需要任何伺服器來支援此實例。  
  
## <a name="perimeter-network-intranet"></a>周邊網路-內部網路  
 當您使用 FILE 配接器時，內部網路周邊網路中會有一部檔案伺服器。 這是您的夥伴放置其訊息的伺服器，而且 BizTalk FILE 接收配接器由此伺服器拾取訊息。  
  
## <a name="e-business-domain"></a>電子商務網域  
 此網域中的伺服器包括：  
  
-   **BizTalk Server （處理、 File 配接器，以及追蹤主控件）。** 此伺服器有 BizTalk Server 執行階段安裝，而且擁有主控件執行個體，其中包含 BizTalk 協調流程、管線、商務規則引擎以及其他商務程序。 這是 BizTalk Server 連接埠、接收位置、管線、對應、結構描述以及組件的位置，用來接收、傳遞、處理和傳送訊息。 此伺服器還有可支援追蹤狀況監控與商務監控資料之主控件的主控件執行個體。 此外，此主控件還包含執行 FILE 傳送與接收配接器的主控件執行個體。  
  
    > [!NOTE]
    >  當您的效能需求增加時，可以為處理主控件的主控件執行個體在環境中加入更多 BizTalk Server。 如需如何設定 BizTalk Server 高可用性的詳細資訊，請參閱[高可用性規劃](../core/planning-for-high-availability3.md)。  
  
-   **主要密碼伺服器。** 中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。  
  
-   **SQL Server。** 中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。  
  
-   **網域控制站。** 中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。  
  
-   **系統管理工具。** 中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [小型與中型公司的範例架構](../core/sample-architectures-for-small-medium-sized-companies.md)   
 [威脅模型分析的範例案例](../core/sample-scenarios-for-threat-model-analysis.md)