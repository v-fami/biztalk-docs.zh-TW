---
title: 潛在的優點，將 BizTalk Server 解決方案部署到使用 HYPER-V 的虛擬化環境 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 588c70f0-68f0-4e58-8f3d-aa6834397bd4
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6c88a8dcc6386b6030d4ca429010b6db1acfb81
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024444"
---
# <a name="potential-benefits-of-deploying-a-biztalk-server-solution-to-a-hyper-v-virtualized-environment"></a>潛在的優點，將 BizTalk Server 解決方案部署到使用 HYPER-V 的虛擬化環境
本主題描述一些部署的優點您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 虛擬化環境的解決方案。  
  
## <a name="benefits-of-running-a-biztalk-server-solution-on-a-hyper-v-virtualized-environment"></a>HYPER-V 上執行 BizTalk Server 解決方案的優點虛擬化環境  
 部署在 HYPER-V 虛擬化環境上執行 BizTalk Server 解決方案可提供下列的彈性和功能：  
  
- **能夠定義單一實體電腦上的多個不同的邏輯安全性界限**HYPER-V 所能容納不同的邏輯安全性界限或在單一的實體硬體資源內的資料分割的建立。 資料分割是隔離的由作業系統執行所在的 hypervisor 支援的單一邏輯單元。 例如，您可以建立多個 BizTalk Server 群組，來執行單一的 HYPER-V 主機電腦上，而您會無法安裝時，執行這項操作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主機作業系統上的單一主機電腦。  
  
- **簡化部署和管理 –** 彙總[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]成較少的實體伺服器的電腦，可簡化部署。 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] 藉由使用.vhd 檔案中使用的實體和虛擬電腦部署簡單的方法。 此外，完整的 HYPER-V 管理解決方案可與 System Center Virtual Machine Manager。 如需 System Center Virtual Machine Manager 的詳細資訊，請參閱 < [ http://go.microsoft.com/fwlink/?LinkID=111303 ](http://go.microsoft.com/fwlink/?LinkID=111303)。  
  
- **錯誤容錯支援透過 HYPER-V 叢集-** 因為 HYPER-V 是感知叢集應用程式、 Windows Server 2008 提供原生的主機叢集的 HYPER-V 虛擬化環境中建立的虛擬機器的支援。  
  
- **向外延展-方便**額外的處理能力、 網路頻寬和儲存體容量可容納的您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]解決方案快速且輕鬆地由 apportioning 其他可用的資源從主機電腦客體虛擬機器。 這可能需要在主機電腦會在升級或客體虛擬機器會移到功能更強大的主機電腦。 即時移轉功能[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]可讓您移至最佳的實體電腦的效能、 調整或最佳化彙總執行 Vm，而不會影響使用者。  
  
- **彙總的硬體資源-** 多部實體伺服器可輕鬆地合併到相對較少的伺服器藉由實作 hyper-v 虛擬化。 彙總適用於已部署的硬體資源的完整使用權。  
  
  若要深入了解詳細提供 HYPER-V 的優點與功能的相關資訊，請參閱[含 HYPER-V 的虛擬化](http://go.microsoft.com/fwlink/?LinkID=202438)。