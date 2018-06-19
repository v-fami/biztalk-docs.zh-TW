---
title: 測試結果： 記憶體關鍵效能指標 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 224c40e5-08a7-4d30-b03a-4b6add5cde1f
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4edf88023ee9e30e7fd0c808346b6231112f8ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22301870"
---
# <a name="test-results-memory-key-performance-indicators"></a>測試結果： 記憶體關鍵效能指標
本主題摘要說明記憶體關鍵效能指標 (KPI) 內所觀測到的測試案例。 這些測試會評估可用的記憶體，測量由**\Memory\Available Mbytes**效能監視器計數器。  
  
## <a name="summary-of-memory-key-performance-indicators"></a>記憶體關鍵效能指標的摘要  
 **記憶體關鍵效能指標 – 比較**適用於 SQL Server，並以所測量的 BizTalk Server 的記憶體總計**\Memory\Available Mbytes**跨所有已相當一致效能監視器計數器測試案例。 實體 BizTalk Server 電腦，並提供給虛擬機器上執行的 BizTalk Server 電腦的平均記憶體可用的平均記憶體差異是因為，兩個實體的 BizTalk Server 電腦用於測試在三個虛擬機器上執行的 BizTalk Server 電腦用於測試。  
  
 下圖將說明在不同的測試平台上的記憶體效能：  
  
 ![記憶體關鍵效能指標](../technical-guides/media/memorykpi.gif "MemoryKPI")  
  
 下表說明收集 KPI 的每個組態的相對效能。 每個結果集的計算方式為基準設定 KPI 的百分比  
  
|KPI|虛擬 BizTalk/實體 SQL|在不同的主機虛擬 BizTalk/虛擬 SQL|合併環境上的虛擬 BizTalk/虛擬 SQL|  
|---------|-----------------------------------|----------------------------------------------------|--------------------------------------------------------------|  
|SQL Server 可用的記憶體 (Mb) 每個伺服器|100.1%|97.1%|103.2%|  
|BizTalk 的總可用記憶體 (Mb)|88.3%|95.9%|96%|  
|平均每個伺服器 / BizTalk 可用記憶體 (Mb)|58.9%|63.9%|64%|  
  
 如需如何評估記憶體效能的詳細資訊，請參閱**測量記憶體效能**主題的章節[檢查清單： 在 HYPER-V 上的測量效能](../technical-guides/checklist-measuring-performance-on-hyper-v.md)。