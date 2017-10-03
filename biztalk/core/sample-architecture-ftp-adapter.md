---
title: "範例架構： FTP 配接器 |Microsoft 文件"
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
- independent software vendor (ISV)
- security, examples
- security, architecture
- examples, architecture
- architecture, security
- FTP adapters, security
- FTP adapters, architecture examples
ms.assetid: 13fc1086-6acc-483c-be83-4ff6a60cd2bc
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bed15e06027bec5e73c19cf73548674bc51ce68a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architecture-ftp-adapter"></a>範例架構： FTP 配接器
當您使用 FTP 配接器傳送和接收訊息時，本主題描述的範例架構。  
  
 下圖顯示使用 FTP 配接器時 BizTalk Server 範例架構的元件。  
  
 **圖 1 顯示 FTP 配接器的範例架構**  
  
 ![範例架構的 FTP 配接器](../core/media/tdi-sec-refarch-ftp.gif "TDI_Sec_RefArch_FTP")  
  
 此範例架構包含下列章節所討論的元件。  
  
## <a name="perimeter-networkinternet"></a>周邊網路─網際網路  
 當您使用 FTP 配接器時，網際網路周邊網路中有一個 FTP 伺服器。  
  
> [!NOTE]
>  FTP 伺服器也可以位於環境外部-在協力電腦的網路中，或第三方獨立軟體廠商 (ISV) 所裝載。  
  
## <a name="perimeter-networkintranet"></a>周邊網路─內部網路  
 公司通常使用 FTP 通訊協定來進行網際網路通訊，因此內部網路周邊網路中不需要任何伺服器來支援此實例。  
  
## <a name="e-business-domain"></a>電子商務網域  
 此網域中的伺服器包括：  
  
-   **BizTalk Server （處理、 FTP 配接器，以及追蹤主控件）。** 此伺服器有 BizTalk Server 執行階段安裝，而且擁有主控件執行個體，其中包含 BizTalk 協調流程、管線、商務規則引擎以及其他商務程序。 這是 BizTalk Server 連接埠、接收位置、管線、對應、結構描述以及組件的位置，用來接收、傳遞、處理和傳送訊息。 此伺服器還有可支援追蹤狀況監控與商務監控資料之主控件的主控件執行個體。 此外，此主控件還包含執行 FTP 傳送與接收配接器的主控件執行個體。  
  
    > [!NOTE]
    >  當您的效能需求增加時，可以為處理主控件的主控件執行個體在環境中加入更多 BizTalk Server。 如需如何設定 BizTalk Server 高可用性的詳細資訊，請參閱[高可用性規劃](../core/planning-for-high-availability3.md)。  
  
-   **主要密碼伺服器。** 中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。  
  
-   **SQL Server。** 與相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。  
  
-   **網域控制站。** 與中的相同相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。  
  
-   **系統管理工具。** 中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [小型與中型公司的範例架構](../core/sample-architectures-for-small-medium-sized-companies.md)   
 [威脅模型分析的範例案例](../core/sample-scenarios-for-threat-model-analysis.md)