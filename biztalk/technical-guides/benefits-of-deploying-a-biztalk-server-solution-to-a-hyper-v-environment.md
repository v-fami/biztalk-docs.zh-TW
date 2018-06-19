---
title: 潛在優點，BizTalk Server 方案部署到使用 HYPER-V 的虛擬化環境 |Microsoft 文件
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
ms.openlocfilehash: 9602a48b0deb4eeddc6f10b2d529d68d94cc781a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295926"
---
# <a name="potential-benefits-of-deploying-a-biztalk-server-solution-to-a-hyper-v-virtualized-environment"></a>潛在優點，BizTalk Server 方案部署到使用 HYPER-V 的虛擬化環境
本主題描述一些部署的優點您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 虛擬化環境中的方案。  
  
## <a name="benefits-of-running-a-biztalk-server-solution-on-a-hyper-v-virtualized-environment"></a>HYPER-V 上執行 BizTalk Server 解決方案的優點虛擬化環境  
 部署在 HYPER-V 虛擬化環境上執行 BizTalk Server 解決方案提供彈性，下列功能：  
  
-   **在單一的實體電腦-定義多個不同的邏輯安全性界限的能力**HYPER-V 可容納不同的邏輯安全性界限或單一實體硬體資源內的資料分割的建立。 資料分割是隔離的支援的 hypervisor，作業系統執行所在的單一邏輯單元。 例如，您可以建立多個 BizTalk Server 群組，來執行單一的 HYPER-V 主機電腦上，而您會無法安裝時執行這項操作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]單一主機電腦的主機作業系統上。  
  
-   **簡化部署和管理 –** 的彙總[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]成較少的實體伺服器的電腦，可簡化部署。 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]藉由使用.vhd 檔案，進行實體和虛擬電腦部署使用簡單的方法。 此外，完整的 HYPER-V 管理解決方案是使用 System Center Virtual Machine Manager。 如需 System Center Virtual Machine Manager 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkID=111303](http://go.microsoft.com/fwlink/?LinkID=111303)。  
  
-   **錯誤容錯支援透過 HYPER-V 叢集-** 因為 HYPER-V 是感知叢集應用程式、 Windows Server 2008 提供原生的主機叢集為 HYPER-V 虛擬化環境中建立的虛擬機器的支援。  
  
-   **向外延展-輕鬆**可以容納額外的處理電源、 網路頻寬和儲存容量的您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案快速且輕鬆地 apportioning 其他可用的資源從主機電腦客體虛擬機器。 這可能需要在主機電腦會在升級或客體虛擬機器會移至更適用的主機電腦。 即時移轉功能[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]可讓您移動執行中 Vm 的效能、 調整或最佳化彙總最佳的實體電腦而不會影響使用者。  
  
-   **硬體資源的彙總**多部實體伺服器可輕易地合併到相對較少的伺服器藉由實作與 HYPER-V 虛擬化。 彙總可容納已部署的硬體資源的完整使用權。  
  
 若要找出更多詳細資訊的功能和優點 HYPER-V 提供，請參閱[與 HYPER-V 虛擬化](http://go.microsoft.com/fwlink/?LinkID=202438)。