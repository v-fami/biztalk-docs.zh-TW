---
title: 範例架構： 基本 BizTalk Server |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, examples
- IPSec
- BizTalk Server, examples
- security, examples
- security, architecture
- IPSec, about IPSec
- BizTalk Server, architecture
- architecture, security
ms.assetid: 7ccc1ef3-670f-423f-b6ca-3d56b9bbeabf
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea815c0165f58c28cea8ce7cae35fd6ed7437323
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architecture-base-biztalk-server"></a>範例架構： 基本 BizTalk Server
本主題討論基本範例架構。 其中描述與配接器無關的 BizTalk Server 部署中的元件。 建議任何 BizTalk Server 部署至少都要有這些元件。  
  
 下圖顯示基本 BizTalk Server 範例架構的元件。 這些元件會在後面章節所討論的各種配接器特定 BizTalk Server 架構中出現。  
  
 **圖 1 基本架構元件**  
  
 ![基底架構元件](../core/media/tdi-sec-refarch.gif "TDI_Sec_RefArch_")  
  
 此範例架構包含下列章節中討論的項目。  
  
## <a name="perimeter-networkinternet"></a>周邊網路─網際網路  
  
-   周邊網路 (也稱為 DMZ 以及過濾的子網路) 包含提供網際網路相關服務的伺服器。 在此網域中沒有 BizTalk Server、BizTalk 接收位置或企業單一登入伺服器。  
  
## <a name="perimeter-networkintranet"></a>周邊網路─內部網路  
 周邊網路包含提供內部網路相關服務的伺服器。 它會在內部網路 (例如企業網路) 和執行應用程式的伺服器之間，提供額外的安全性階層。 類似於網際網路周邊網路，內部網路周邊網路不包含 BizTalk Server、BizTalk 接收位置或「企業單一登入」(SSO) 伺服器。  
  
## <a name="e-business-domain"></a>電子商務網域  
 此網域包含 BizTalk Server 實作所使用的所有基礎結構與應用程式。 此網域中的伺服器包括：  
  
-   **BizTalk Server。** 此伺服器擁有一個 BizTalk Server 執行階段安裝與許多「BizTalk 主控件」的執行個體。 環境中 BizTalk Server 的數目依它們執行的主控件類型與效能需求而定。 當您的效能需求增加時，可以為處理主控件的主控件執行個體在環境中加入更多 BizTalk Server。  
  
-   **主要密碼伺服器。** 此伺服器是「企業單一登入」(SSO) 主要密碼伺服器。 其中保存 SSO 系統用來加密 SSO 資料庫中資料的主要密碼 (加密金鑰)。  
  
-   **SQL Server。** 此伺服器包含 BizTalk 資料庫。  
  
    > [!IMPORTANT]
    >  對於容錯移轉保護，建議您叢集每個 BizTalk 資料庫。 如需有關 Microsoft SQL Server 容錯移轉叢集的詳細資訊，請參閱 Microsoft MSDN 網站，網址[http://go.microsoft.com/fwlink/?LinkID=190216](http://go.microsoft.com/fwlink/?LinkID=190216)。  
  
    > [!NOTE]
    >  依據您的效能需求，您可能必須將 BizTalk 資料庫分割至執行 SQL Server 的多部電腦上。  
  
-   **網域控制站。** 此伺服器裝載電子商務 Active Directory 網域。 其中包含需要存取 BizTalk Server 的所有群組與個別帳戶的相關資訊。  
  
-   **系統管理工具。** 此網域的其中一個伺服器會裝載下列管理工具：BizTalk 管理主控台和企業單一登入 (SSO) 管理公用程式。  
  
## <a name="firewalls-and-domains"></a>防火牆與網域  
 在圖 1 中，Forefront Threat Management Gateway (TMG) 2010 server 扮演軟體防火牆協助保護，並包含每個網域。 此外，電子商務網域有它自己的網域控制站，此網域不信任任何其他網域。 如需如何設定網域和信任的防火牆的詳細資訊，請參閱 「 Microsoft 說明及支援 」 網站，網址[http://go.microsoft.com/fwlink/?LinkId=25230](http://go.microsoft.com/fwlink/?LinkId=25230)。  
  
 範例架構有兩個防火牆：  
  
-   **防火牆 1。** 此防火牆有三個網路介面：它會路由傳送來自網際網路、內部網路以及周邊網路的流量。  
  
-   **防火牆 2。** 此防火牆是雙重主機：它會路由傳送來自周邊網路 (網際網路與內部網路) 與電子商務網域的流量。  
  
 周邊網路中的電腦不是任何網域的成員，而且它們不會相互通訊。  
  
## <a name="ipsec"></a>IPsec  
 建議您使用網際網路通訊協定安全性 (IPSec) 來協助保護電子商務網域中所有伺服器之間的通訊安全。 IPsec 規則如下：  
  
-   允許 BizTalk Server 與網域控制站之間已驗證的流量。  
  
-   允許 BizTalk Server 與管理工具伺服器之間已驗證的流量。  
  
-   允許 BizTalk Server 與主要密碼伺服器之間已驗證的流量。  
  
-   允許 BizTalk Server 與 SQL Server 之間已驗證的流量。  
  
-   允許主要密碼伺服器與網域控制站之間已驗證的流量。  
  
-   允許主要密碼伺服器與 BizTalk Server (外掛式、處理、內含式以及追蹤主控件) 之間已驗證的流量。  
  
-   允許主要密碼伺服器與 SQL Server (SSO 資料庫) 之間已驗證的流量。  
  
-   允許網域控制站與網域中所有伺服器之間已驗證的流量。  
  
-   允許管理工具伺服器與網域中所有伺服器之間已驗證的流量。  
  
 若您在網域中有其他應用程式不需要存取 BizTalk Server、SQL Server 以及主要密碼伺服器或管理工具伺服器，請封鎖那些應用程式與適當伺服器之間的流量。  
  
## <a name="see-also"></a>另請參閱  
 [安全性規劃](../core/planning-for-security.md)   
 [小型與中型公司的範例架構](../core/sample-architectures-for-small-medium-sized-companies.md)   
 [威脅模型分析的範例案例](../core/sample-scenarios-for-threat-model-analysis.md)