---
title: "範例架構： HTTP 和 SOAP 配接器 |Microsoft 文件"
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
- SOAP adapters, security
- Web Publishing
- security, examples
- security, architecture
- SOAP adapters, architecture examples
- examples, architecture
- architecture, security
- HTTP adapters, architecture examples
- reverse proxy rules
- ISA Server implementation
- HTTP adapters, security
ms.assetid: 935197d0-5108-4970-b237-3c6d5b40c5e9
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dae8be185084a9a838876e3d50b605a63c161b66
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architecture-http-and-soap-adapters"></a>範例架構： HTTP 和 SOAP 配接器
當您使用的 HTTP 與 SOAP 配接器傳送和接收訊息時，本主題描述的範例架構。  
  
 下圖顯示使用 HTTP 或 SOAP 配接器時 BizTalk Server 範例架構的元件。  
  
 **圖 1 顯示 HTTP 或 SOAP 配接器的範例架構**  
  
 ![範例 HTTP 或 SOAP 配接器的架構](../core/media/tdi-sec-refarch-http.gif "TDI_Sec_RefArch_HTTP")  
  
 此範例架構包含下列章節所討論的元件。  
  
## <a name="perimeter-networkinternet"></a>周邊網路─網際網路  
 當您使用的 SOAP 和 HTTP 配接器時，我們建議您使用反向 proxy 規則 （TMG Server 實作稱為 Web 發佈） 訊息到來自網際網路對向防火牆 (防火牆 1) 防火牆協助保護電子商務網域 (防火牆 2)，並從此執行外掛式主控的件的 BizTalk 伺服器防火牆。 如需 Web 發佈 」 規則的詳細資訊，請參閱 Microsoft 網站，網址[http://go.microsoft.com/fwlink/?LinkID=205340](http://go.microsoft.com/fwlink/?LinkID=205340) (http://go.microsoft.com/fwlink/?LinkID=205340)。  
  
> [!NOTE]
>  當您使用反向 Proxy 時，周邊網路中就不需要 Web 伺服器。  
  
## <a name="perimeter-networkintranet"></a>周邊網路─內部網路  
 公司通常會使用 HTTP 與 SOAP 通訊協定來進行網際網路通訊，因此內部網路周邊網路中不需要任何伺服器來支援此實例。 若您在透過 HTTP 或 SOAP 通訊協定來整合 BizTalk Server 的內部網路中有內部應用程式，就應該遵循針對網際網路周邊網路的建議。  
  
## <a name="e-business-domain"></a>電子商務網域  
 此網域包含 BizTalk Server 實作所使用的所有基礎結構與應用程式。 此網域中的伺服器包括：  
  
-   **BizTalk Server （處理與追蹤主控件）。** 此伺服器有 BizTalk Server 執行階段安裝，而且擁有主控件執行個體，其中包含 BizTalk 協調流程、管線、商務規則引擎以及其他商務程序。 此伺服器還有可支援追蹤狀況監控與商務監控資料之主控件的主控件執行個體。  
  
    > [!NOTE]
    >  當您的效能需求增加時，可以為處理主控件的主控件執行個體在環境中加入更多 BizTalk Server。  
  
-   **BizTalk Server （SOAP 和 HTTP 配接器的外掛式主控件）。** 此伺服器有 BizTalk Server 執行階段的安裝，而且只擁有主控件的執行個體，其中包含 HTTP 與 SOAP 配接器。 這些主控件會在個別伺服器上執行，因為這些配接器要求您在執行的電腦上安裝網際網路資訊服務 (IIS)。  
  
    > [!NOTE]
    >  當您的效能需求增加時，可以將更多的 BizTalk Server 新增到您的環境中，以做為 HTTP 與 SOAP 配接器主控件的主控件執行個體。 當您如此做時，還必須設定網路負載平衡 (NLB)。 如需如何設定 BizTalk Server 高可用性的詳細資訊，請參閱[高可用性規劃](../core/planning-for-high-availability3.md)。  
  
-   **主要密碼伺服器。** 中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。  
  
-   **SQL Server。** 中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。  
  
-   **網域控制站。** 中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。  
  
-   **系統管理工具。** 中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [小型與中型公司的範例架構](../core/sample-architectures-for-small-medium-sized-companies.md)   
 [威脅模型分析的範例案例](../core/sample-scenarios-for-threat-model-analysis.md)