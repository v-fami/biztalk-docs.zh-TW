---
title: 測試結果： BizTalk Server 關鍵效能指標 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 902cdfc1-21ab-4f56-b97b-2f8979514b11
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab682b0d773a613e6dfcdf143ef0afbeb5af48fa
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26009919"
---
# <a name="test-results-biztalk-server-key-performance-indicators"></a>測試結果： BizTalk Server 關鍵效能指標
本主題摘要說明 BizTalk Server 關鍵效能指標 (KPI) 內所觀測到的測試案例。 特別是這些測試評估所測量的輸送量"**BizTalk： 傳訊/文件 processed/Sec**「 效能監視器計數器和延遲，以 Visual studio 用戶端的回應時間來衡量。  
  
## <a name="summary-of-biztalk-server-key-performance-indicators"></a>BizTalk Server 關鍵效能指標的摘要  
 每個案例實體機器已受限制，讓邏輯處理器數目和虛擬處理器的對等。 這項作業完成使用 /maxmem 和 /numproc 的 boot.ini 參數。 使用這些參數的詳細資訊，請參閱 < 開機 INI 選項參考 >，網址[http://go.microsoft.com/fwlink/?LinkId=122139](http://go.microsoft.com/fwlink/?LinkId=122139)。  
  
 **BizTalk Server 關鍵效能指標 – 比較**HYPER-V 虛擬機器上執行 BizTalk Server 此測試案例的實體硬體上提供大約 95%的輸送量和延遲 BizTalk 伺服器的效能。 由於無狀態的本質之故[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，其他的 BizTalk Server 虛擬機器可以輕鬆地新增到環境為必要項目來提供向外的延展，並增加系統的整體效能。 建立並加入其他 BizTalk Server 環境可藉由使用 sysprep 公用程式來產生新的映像的基底映像。  
  
> [!NOTE]  
>  Sysprep 回應檔案和指令碼會提供與 BizTalk Server，以配合從現有的已在電腦映像建立額外的映像使用 sysprep 安裝 BizTalk Server。 這些範例指令碼專為在 32 位元和 64 位元版本的 Windows Server 2008 上安裝 BizTalk server。 如需詳細資訊，請參閱 BizTalk Server 的線上文件。  
  
 佈建、 彙總及管理的虛擬機器可以是大幅加速透過使用 System Center Virtual Machine Manager (VMM)。 如需 System Center Virtual Machine Manager 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkID=111303](http://go.microsoft.com/fwlink/?LinkID=111303)  
  
 取得在這個實驗室中的效能結果會顯示標示為從執行時所獲得的效能改進[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]上[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]在 HYPER-V 虛擬機器。 執行[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]上 HYPER-V 虛擬機器提供約 75%的輸送量和延遲效能[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]與實體硬體上執行 BizTalk Server 時，觀察到大約 95%的效能和[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]在 HYPER-V 虛擬機器。 這種效能提升是主要是能歸因於改善的效能[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]HYPER-V 上做為客體作業系統執行時。 從相關的效能比較[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]HYPER-V 指南將會位於[http://go.microsoft.com/fwlink/?LinkId=147144](http://go.microsoft.com/fwlink/?LinkId=147144)。  
  
 下圖將說明在不同的測試平台上的 BizTalk Server 效能：  
  
 ![BizTalk 關鍵效能指標](../technical-guides/media/biztalkkpi.gif "BizTAlkKPI")  
  
 下表說明收集 KPI 的每個組態的相對效能。 每個結果集的計算方式為基準設定 KPI 的百分比表示。  
  
|KPI|虛擬 BizTalk/實體 SQL|在不同的主機虛擬 BizTalk/虛擬 SQL|合併環境上的虛擬 BizTalk/虛擬 SQL|  
|---------|-----------------------------------|----------------------------------------------------|--------------------------------------------------------------|  
|已處理的 \BizTalk:Messaging\Documents/秒|94.3%|79.8%|67%|  
|Visual Studio 用戶端所測量的延遲|94.3%|79.7%|66.9%|  
  
 如需如何最佳化 BizTalk Server 解決方案的效能的詳細資訊，請參閱 BizTalk Server 效能最佳化指南位於[http://go.microsoft.com/fwlink/?LinkId=122477](http://go.microsoft.com/fwlink/?LinkId=122477)。  
  
## <a name="performance-comparison-results-summary"></a>效能比較結果摘要  
 94.3%輸送量和 94.3%延遲時只會在執行達成[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 上的建議，此層，您的方案使用 HYPER-V 虛擬化提供優異的效能，以及佈建、 彙總、 彈性與簡易管理的可能會將方案部署到 HYPER-V 環境時。  
  
### <a name="throughput-comparison-sample-results"></a>輸送量比較範例結果  
 當[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用 BizTalk Server 環境中電腦所執行 HYPER-V 的虛擬機器上的 BizTalk Server 解決方案所測量的輸送量"**BizTalk： 傳訊/文件 processed/Sec**"當所有 BizTalk Server 環境中使用的電腦已安裝在實體硬體的輸送量未偏離正軌 94.3%是從 67%的效能監視器計數器。  
  
### <a name="latency-comparison-sample-results"></a>延遲的比較範例結果  
 當[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用 BizTalk Server 環境中電腦所執行 HYPER-V 的虛擬機器上的 BizTalk Server 解決方案 Visual Studio 用戶端回應所測量的延遲時間時是從 66.9%94.3%未偏離正軌延遲的所有使用 BizTalk Server 環境中的電腦已安裝在實體硬體上。