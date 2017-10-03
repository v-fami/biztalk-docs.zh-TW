---
title: "部署服務導向解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, service solution tutorial
- deploying, tutorials
- service solution tutorial, deploying
- service solution tutorial, background information
- tutorials, deploying
ms.assetid: 88d4d28d-9031-4fb8-ab62-04ee27949673
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7246635c4e0d55fd424fd0052eee91e118c8cb17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-the-service-oriented-solution"></a>部署服務導向解決方案
「服務導向架構」(Service Oriented Architecture，SOA) 是一種建置分散式系統的方法。 服務導向解決方案展示如何將數個使用不同通訊協定的後端系統彙總成用戶端可以取用的單一服務。 此解決方案使用可保證傳遞和效能特性的方法來整合服務。  
  
 服務導向解決方案是依照一個服務等級協議實例來建立模型，此實例會給定三秒的時間，讓 BizTalk Server 和連線於此的商務營運系統 (LOB) 應用程式伺服器可以回應服務要求。 這三秒中有一秒可能會給 BizTalk Server 佔用。  
  
 本節中的主題描述如何在單一電腦和多台實際伺服器上安裝和測試服務導向解決方案。  
  
> [!NOTE]
>  有三個版本的服務導向解決方案： 配接器、 內嵌和虛設常式。 如需服務導向解決方案的三個版本之間差異的詳細資訊，請參閱[瞭解服務導向解決方案](../core/understanding-the-service-oriented-solution.md)。  
  
 **讀取器的指引**  
  
 本文件假設您已熟悉 BizTalk Server、Windows Server 和 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。 同時假設您也瞭解企業應用程式整合和 Web 服務的基本概念。 此外，建議您要熟悉使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 建置應用程式的方式，並熟悉建立專案、設定參考以及使用偵錯模式以偵錯和測試解決方案等工作。 用於 IT 專業人員和開發人員技術及知識的相關資訊，請參閱[必要條件技術和知識](../core/prerequisite-skills-and-knowledge5.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [開發人員電腦設定為服務導向解決方案](../core/developer-machine-setup-for-the-service-oriented-solution.md)