---
title: "開發人員電腦設定為服務導向解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- developer servers
- service solution tutorial, deployment prerequisites
- service solution tutorial, developer servers
ms.assetid: a088696f-c1ee-4578-ac02-af29b6de086b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb3407dbccbc4dccc902892cf04fa71991b8d93e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="developer-machine-setup-for-the-service-oriented-solution"></a>服務導向解決方案的開發人員電腦設定
「服務導向架構」(Service Oriented Architecture，SOA) 是一種建置分散式系統的方法。 服務導向解決方案展示如何將數個使用不同通訊協定的後端系統彙總成用戶端可以取用的單一服務。 此方案整合服務的方法也將確保您能滿足服務等級協議上的交貨及效能等特徵。  
  
 服務導向解決方案是依照一個服務等級協議實例來建立模型，此實例會給定三秒的時間，讓 BizTalk Server 和連線於此的商務營運系統 (LOB) 應用程式伺服器可以回應服務要求。 這三秒中有一秒可能會給 BizTalk Server 佔用。  
  
 有三個版本的服務導向解決方案： 配接器、 內嵌和虛設常式。 如需服務導向解決方案的三個版本之間差異的詳細資訊，請參閱[瞭解服務導向解決方案](../core/understanding-the-service-oriented-solution.md)。 如果您是開發人員，請取得使用虛設常式版實例執行的實例。 這個版本無須使用任何 LOB 後端伺服器即可執行。 在此之後，您可以使用配接器版本的實例，學習如何整合各種配接器與後端伺服器，以及如何設定它們使用 BizTalk 伺服器做為單一服務以進行回應。 然後您可以衡量由 BizTalk Server 及其配接器所造成的延遲。  
  
 如果 BizTalk 伺服器延遲超過服務需求，您可以安裝並執行 SOA 內嵌版本，以略過 LOB 配接器持續點。 由於 MessageBox 持續點的作用，此版本會略過配接器，從而略過這些配接器的延遲比重。 內嵌版本則不同，它會透過「遠端程序呼叫」(RPC) 機制 (如 DCOM)，與後端伺服器直接交談。  
  
 如需 MessageBox 持續點的詳細資訊，請參閱[持續性和協調流程引擎](../core/persistence-and-the-orchestration-engine.md)。  
  
 這份部署指南說明如何在單一電腦上安裝與測試服務導向解決方案的三個版本。  
  
 如需有關服務導向解決方案的詳細資訊，請參閱[瞭解服務導向解決方案](../core/understanding-the-service-oriented-solution.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [然後再安裝服務導向解決方案](../core/before-installing-the-service-oriented-solution.md)  
  
-   [How to Install 虛設常式版本的服務導向解決方案](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md)  
  
-   [如何安裝內嵌和配接器版本的服務導向解決方案](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md)  
  
-   [如何執行服務導向解決方案](../core/how-to-run-the-service-oriented-solution.md)