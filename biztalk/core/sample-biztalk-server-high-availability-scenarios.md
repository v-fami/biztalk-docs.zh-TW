---
title: 範例 BizTalk Server 高可用性實例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, small distributions
- examples, high availability
- architecture, examples
- high availability, examples
- examples, architecture
- databases, clustering
- architecture, medium distributions
- scaling
- architecture, large distributions
ms.assetid: ad9e3f57-1a23-41c2-82c9-dc8e1b29ed4d
caps.latest.revision: 30
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff4db96e89dc91ee96aaf5f0b60f0de34ce83425
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271662"
---
# <a name="sample-biztalk-server-high-availability-scenarios"></a>BizTalk Server 高可用性實例範例
本主題說明在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中透過向外擴充的主控件層提供高可用性的實例。 藉由在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中分隔功能部分為不同的主控件和階層，系統管理員可以為每個主控件提供備援並可獨立於其他主控件之外擴充它們。 若要為每個功能部分提供高可用性，您可以為每個主要功能 (接收、處理、傳送和追蹤) 建立不同的主控件，並叢集 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫及「企業單一登入」主要密碼伺服器。  
  
## <a name="small-biztalk-server-deployments"></a>小型 BizTalk Server 部署  
 可同時為 SQL Server 和 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供高可用性的最小 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署，是由兩部具有 SQL Server 主動/主動叢集組態的電腦所組成。 兩部電腦都包含環境中所有 BizTalk 主控件的執行個體。 若一部電腦失敗或發生錯誤，其他電腦仍會維護 SQL Server 與 BizTalk Server 的服務可用性。 此組態並不真的高度可用，因為其並不支援主要密碼伺服器叢集，不支援的原因是因為在叢集「企業單一登入」資源為被動的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主控件執行個體無法啟動。 如需叢集化主要密碼伺服器的詳細資訊，請參閱[高可用性的企業單一登入](../core/high-availability-for-enterprise-single-sign-on.md)。  
  
 對於 5 部電腦以下的小型 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署，建議您讓包含 BizTalk Server 資料庫的 SQL Server 叢集在與 BizTalk Server 電腦不同的電腦上執行。 BizTalk Server 電腦可執行所有 BizTalk 主控件 (接收、處理和傳送)。 若要讓這個部署高度可用，請叢集 SQL Server 及「企業單一登入」主要密碼伺服器，並具備兩個 BizTalk Server，使其各自在您的環境中執行每個主控件的執行個體。  
  
 下圖顯示高度可用的小型 BizTalk Server 部署。  
  
 ![小型 BizTalk Server 部署](../core/media/tdi-highava-smalldepl.gif "TDI_HighAva_SmallDepl")  
  
## <a name="medium-sized-biztalk-server-deployments"></a>中型 BizTalk Server 部署  
 對於包含五至十部電腦的中型部署，建議您叢集包含 BizTalk Server 資料庫及「企業單一登入」主要密碼伺服器的 SQL Server。 若您的實例需要執行大量接收，您可能要指派兩部 BizTalk Server 專用於執行接收主控件執行個體，以提供高度可用的方案。 接著您可以讓兩部或以上的電腦執行處理和傳送主控件執行個體。 若要讓此成為高度可用的部署，請在兩部 BizTalk Server 上建立處理和傳送主控件的主控件執行個體。 同樣地，若您的實例需要執行大量處理，您可能要指派兩部 BizTalk Server 專用於執行處理主控件執行個體，並讓其餘兩部 BizTalk Server 執行接收和傳送主控件的執行個體。  
  
 下圖顯示高度可用的中型 BizTalk Server 部署，其中包含兩部專用於接收作業的 BizTalk Server。  
  
 ![媒體 &#45;BizTalk Server 部署的大小調整](../core/media/tdi-highava-meddepl.gif "TDI_HighAva_MedDepl")  
  
 如需高可用性的企業單一登入，請參閱[高可用性的企業單一登入](../core/high-availability-for-enterprise-single-sign-on.md)。  
  
## <a name="large-scale-biztalk-server-deployments"></a>大型 BizTalk Server 部署  
 對於包含 10 部或以上電腦的大型部署，請為接收、處理和傳送功能指派獨立的 BizTalk Server 電腦。 另外，若在群組中有許多 BizTalk Server 電腦，您可以納入其他 MessageBox 資料庫電腦以增加效能。 在此情況下，請叢集 MessageBox 資料庫及主要密碼伺服器，以提供高可用性。  
  
 像這樣的分散式組態可以展現 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的彈性，因為它能讓您評估和識別部署中特定的失敗點，然後策略性地配置資源以減少系統中的那些失敗點。 今日動態的商務環境需要這樣的彈性，因為工作負載變動和商務需求可能每天都在改變。  
  
 您只要將資源從耗用較少資源的電腦移到需要大量資源的電腦，以使用現有的資源來達成高可用性，而不需花費額外的金錢來升級或取得新硬體。  
  
 下圖顯示大型 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署。  
  
 ![大型 &#45;調整 BizTalk Server 部署](../core/media/tdi-highava-largedepl.gif "TDI_HighAva_LargeDepl")  
  
 如需高可用性的企業單一登入，請參閱[高可用性的企業單一登入](../core/high-availability-for-enterprise-single-sign-on.md)。  
  
## <a name="providing-high-availability-using-hyper-v-and-failover-clustering"></a>使用 Hyper-V 和容錯移轉叢集提供高可用性  
 將 Windows® Server 2008 Hyper-V 角色和 Windows Server 2008 容錯移轉叢集功能一起使用，可提供虛擬伺服器運算環境的高可用性。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署中所用的 BizTalk Server 電腦和 SQL Server 電腦可以安裝在 Hyper-V 虛擬環境，然後透過容錯移轉叢集功能得到高度可用性。 因為在 Hyper-V 上執行虛擬作業系統會有相關的系統資源成本，所以建議在將此類方案部署到實際執行環境之前，先執行徹底的效能測試。 如需有關使用 HYPER-V 和容錯移轉叢集在一起以提供高可用性的虛擬機器，請參閱 「 HYPER-V 逐步指南:: HYPER-V 和容錯移轉叢集 」 在[http://go.microsoft.com/fwlink/?LinkID=129113](http://go.microsoft.com/fwlink/?LinkID=129113)。 如需有關部署[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]到 HYPER-V 虛擬化環境，請參閱 BizTalk Server HYPER-V 指南 》 下載[http://go.microsoft.com/fwlink/?LinkId=189706](http://go.microsoft.com/fwlink/?LinkId=189706)。  
  
## <a name="see-also"></a>另請參閱  
 [為 BizTalk 主控件提供高可用性](../core/providing-high-availability-for-biztalk-hosts.md)   
 [為 BizTalk Server 資料庫提供高可用性](../core/providing-high-availability-for-biztalk-server-databases.md)   
 [企業單一登入的高可用性](../core/high-availability-for-enterprise-single-sign-on.md)