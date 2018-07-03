---
title: 企業單一登入的高可用性 |Microsoft Docs
ms.custom: ''
ms.date: 2016-02-29
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Master Secret server, availability
- high availability, SSO
- Master Secret server, high availability
- SSO, high availability
ms.assetid: 6c631b5c-7147-4cc0-b58a-6749e83df9d3
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9acc933df7b958ea6ae0f0651fd66ba14daad913
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019242"
---
# <a name="high-availability-for-enterprise-single-sign-on"></a>企業單一登入的高可用性
即使您未使用「企業單一登入」(SSO) 功能來對應認證和單一登入，SSO 仍然是整個 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 基礎結構的重要部分，因為 BizTalk Server 會使用 SSO 協助保護接收位置的資訊。  
  
 您必須將安裝 SSO 服務的第一部電腦設定為主要密碼伺服器。 主要密碼伺服器是儲存主要密碼 (加密金鑰) 的 SSO 伺服器。 主要密碼是一種加密金鑰，供 SSO 系統用來加密和解密儲存在 SSO 資料庫中的資料。  
  
 若 SSO 伺服器失敗，且在其他 BizTalk Server 電腦 (也就是 SSO 伺服器) 執行相同的主控件執行個體，則其他 SSO 伺服器會繼續進行其工作。 這表示主要密碼伺服器仍可正確運作，因此 BizTalk Server 處理會繼續。  
  
 若主要密碼伺服器失敗，則所有在它失敗之前正在執行的執行階段作業 (包括認證的解密) 可成功地繼續進行。 不過，您無法加密新的認證。 因此，BizTalk Server 環境與主要密碼伺服器的可用性相依，如下圖所示。  
  
 ![失敗點](../core/media/tdi-highava-pointsfailure-mss.gif "TDI_HighAva_PointsFailure_MSS")  
  
> [!NOTE]
>  如果主要密碼伺服器無法使用，在下列情況發生前，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主控件執行個體仍可使用主要密碼的記憶體中快取複本進行執行階段作業：  
> 
> - 主控件執行個體重新啟動。  
>   -   執行 BizTalk 主控件執行個體之電腦上的 SSO 服務重新啟動。  
>   -   SSO 主要密碼變更。  
> 
>   如果重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上的 SSO 服務或變更 SSO 主要密碼，則會從記憶體中釋出主要密碼的快取複本，且 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 必須能夠連線主要密碼伺服器才能取得主要密碼的另一個複本。 如果主要密碼伺服器無法使用，則需要存取主要密碼伺服器以進行加密的任何管理作業將會失敗。  
  
## <a name="making-the-master-secret-server-available"></a>讓主要密碼伺服器可用  
 為了讓 SSO 系統可用 (也就是讓 BizTalk Server 環境可用)，請務必在主要密碼產生之後立即將它備份。 若遺失該主要密碼，您將遺失使用它來加密的 SSO 系統資料。 如需備份主要祕密的詳細資訊，請參閱[如何重新設定主要密碼](../core/how-to-back-up-the-master-secret.md)。  
  
 可使用兩種方法讓主要密碼伺服器可用：  
  
-   **可供使用，但不是高度可用。** 所有 SSO 伺服器都會將主要密碼快取在記憶體中，且即使主要密碼伺服器失敗，執行階段作業仍然會繼續。 不過，您將無法變更連接埠組態或 SSO 組態。 BizTalk Server 執行階段將會順利繼續進行，但是您無法做任何設計變更。  
  
     即使此組態不是高度可用，但它仍可滿足大部分的實例，且它與向外擴充接收、傳送和處理主控件一致。  
  
-   **高可用性。** 若要提供主要密碼伺服器的備援，請在不同的主要密碼伺服器叢集上使用 Windows 叢集，或在現有的資料庫叢集上設定主要密碼伺服器。 主要密碼伺服器所提供的服務不會耗用太多資源，且在資料庫叢集上安裝時，通常不會影響資料庫的功能或效能。 下圖顯示如何讓主要密碼伺服器高度可用。  
  
     ![高可用性的主要密碼伺服器](../core/media/tdi-highava-msscluster.gif "TDI_HighAva_MSSCluster")  
  
     雖然此組態高度可用，它仍然需要額外的硬體資源。 如需高可用性 SSO 安裝選項的詳細資訊，請參閱[高可用性 SSO 安裝選項](../core/high-availability-sso-installation-options.md)。 本節包含設定為高可用性的叢集資源的 Windows Server 叢集上的 SSO 主要祕密伺服器的詳細的資訊。  
  
    > [!NOTE]
    >  若要減少高度可用方案的硬體資源，您可以在 SQL Server 叢集中新增主要密碼伺服器做為叢集資源。 您不需要購買額外的 BizTalk Server 授權，另一部電腦上安裝 SSO 服務。  
  
## <a name="see-also"></a>另請參閱  
 [叢集 BizTalk Server 資料庫](../core/clustering-the-biztalk-server-databases1.md)   
 [建立高可用性的 BizTalk Server 環境](../core/creating-a-highly-available-biztalk-server-environment.md)   
 [如何叢集化主要密碼伺服器](../core/how-to-cluster-the-master-secret-server1.md)