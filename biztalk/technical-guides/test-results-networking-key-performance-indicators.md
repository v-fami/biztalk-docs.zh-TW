---
title: "測試結果： 網路功能關鍵效能指標 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9bdbc2df-9d19-4ae8-b540-ec1b9a7cdbe9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3eb4e10c739178e6cd923f65b51f982e05ab7f56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="test-results-networking-key-performance-indicators"></a>測試結果： 網路功能關鍵效能指標
本主題摘要說明網路關鍵效能指標 (KPI) 內所觀測到的測試案例。 這些測試評估所測量的網路效能**\Network 介面 (\*) \Bytes Total/sec**效能監視器計數器和藉由測量**SQL Network Interface\Bytes Total/sec （平均）** VSTS 2008 負載測試控制器所傳回。  
  
## <a name="summary-of-network-key-performance-indicators"></a>網路關鍵效能指標的摘要  
 **比較的網路功能關鍵效能指標 –** HYPER-V 虛擬機器上執行的 BizTalk Server 的網路輸送量發現，範圍從大約 70%到 96%達成實體 BizTalk 伺服器上的網路輸送量根據特定的測試環境。 HYPER-V 虛擬機器上執行的 SQL Server 的網路輸送量發現，範圍從大約 68%到 81%達成實體的 SQL Server，再根據特定的測試環境上的網路輸送量。 在觀察到的網路輸送量差異可以屬於 HYPER-V Hypervisor 的資源需求。  
  
 請依照[網路最佳化](../technical-guides/network-optimizations.md)來最大化所測量的 HYPER-V 虛擬機器上的網路輸送量**\Network 介面 (\*) \Bytes Total/sec**  
  
 下圖將說明在不同的測試平台上的網路效能：  
  
 ![網路功能關鍵效能指標](../technical-guides/media/networkkpi.gif "NetworkKPI")  
  
 下表說明收集 KPI 的每個組態的相對效能。 每個結果集的計算方式為基準設定 KPI 的百分比  
  
|KPI|虛擬 BizTalk/實體 SQL|在不同的主機虛擬 BizTalk/虛擬 SQL|合併環境上的虛擬 BizTalk/虛擬 SQL|  
|---------|-----------------------------------|----------------------------------------------------|--------------------------------------------------------------|  
|\Network 介面 （*） \Bytes 總數/秒 （所有 BizTalk 伺服器之間平均總）|96%|82.1%|70.2%|  
|SQL Network Interface\Bytes Total/sec （平均）|95.5%|81.2%|68.4%|  
  
 如需如何評估網路效能的詳細資訊，請參閱**測量網路效能**主題的章節[檢查清單： 在 HYPER-V 上的測量效能](../technical-guides/checklist-measuring-performance-on-hyper-v.md)。