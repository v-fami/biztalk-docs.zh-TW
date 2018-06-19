---
title: 實作會反白顯示的服務導向解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service solution tutorial, performance
- performance, service solutions
- service solution tutorial, implementing
ms.assetid: 3dbd8dfd-45b7-4290-ba07-b0c5e6264629
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c593c24c72e5666525001e6a52e2b0bf6eac2de
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257750"
---
# <a name="implementation-highlights-of-the-service-oriented-solution"></a>實作會反白顯示的服務導向解決方案
解決特定內容中的特定問題之解決方案。 服務導向解決方案也不例外，且專用於 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和此實例。 如需 Woodgrove Bank 案例的詳細資訊，請參閱[瞭解服務導向解決方案](../core/understanding-the-service-oriented-solution.md)。  
  
 開發此實例時，有幾個層面已經證實為減少回應時間至可接受層級的瓶頸。 使用配接器傳送訊息至後端系統，會在取得回應時造成顯著的延遲。 一般而言，配接器本身造成極少延遲。 不過，BizTalk 的分散式架構需要配接器使用 MessageBox 與協調流程主控件執行個體通訊。 這將造成需往返資料庫，並影響延遲時間。 基於這個原因，此解決方案的內嵌版本 (最快速的版本) 在協調流程本身建置可直接呼叫後端系統的配接器功能。 後端系統有三種，這表示有三種可能的不同機制可以和後端系統通訊。  
  
 另一個已證實有效能問題的層面是從「企業單一登入」(SSO) 擷取組態資料。 若要加速擷取時間時保留為了方便和普遍性的 SSO，解決方案會使用本機快取組態值。 使用 SSO 也能讓您更容易管理組態資料。 您不需在執行主控件執行個體的伺服器上變更設定，就能新增其他主控件執行個體以滿足延遲與效能需求。  
  
 此解決方案的另一個特殊項目是可直接從程式碼呼叫管線。 這可以讓您重複使用自訂管線元件。  
  
 最後，您可以變更數個 BizTalk Server 設定，以從這個解決方案提升其他效能。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [內嵌後端叫用](../core/inlining-back-end-invocation.md)  
  
-   [有效使用 SSO，在服務導向解決方案](../core/using-sso-efficiently-in-the-service-oriented-solution.md)  
  
-   [使用管線從服務導向解決方案](../core/using-pipelines-from-the-service-oriented-solution.md)  
  
-   [調整服務導向解決方案](../core/tuning-the-service-oriented-solution.md)  
  
-   [減少傳輸類型與處理](../core/decoupling-transport-type-and-processing.md)