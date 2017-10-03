---
title: "健全狀況彙總的方式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c37644cd-7d3c-4e93-ad56-101043cfa685
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25dd7a2aea4d01a2fd84fe294f793cda833d1322
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-health-rolls-up"></a>健全狀況的積存方式
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件會將 BizTalk Server 部署、 應用程式和其構成成品分類成其中一層的健全狀況可以相依於較低層級的健全狀況的圖層結構。  
  
-   BizTalk 部署  
  
-   BizTalk 應用程式  
  
## <a name="health-roll-up-for-biztalk-deployment"></a>註冊 BizTalk 部署健康狀況彙總  
 下圖顯示 BizTalk Server 部署的健全狀況狀態的彙總方式在此管理組件中。  
  
 ![部署模型](../technical-guides/media/biztalk2010mp-deploymentmodel.gif "BizTalk2010MP DeploymentModel")  
  
 下表描述 BizTalk Server 部署工作流程圖表中顯示的元件。  
  
|名稱|Description|健全狀況|  
|----------|-----------------|------------|  
|BizTalk 部署群組|包含多個元件，例如執行階段規則引擎的執行階段伺服器的群組。|此群組的健全狀況需視的可用性<br /><br /> -BAM 角色<br />BizTalk 主控件的部署<br />BizTalk 執行階段角色<br />規則引擎的規則|  
|BAM 角色|伺服器的 BAM 安裝元件。|這個健全狀況取決於 BAM 執行階段角色和 BAM 入口網站。|  
|BizTalk 主控件的部署|定義執行階段參數或要執行的各種應用程式成品的界限的邏輯實體。 以 NT 服務的這個 （主控件執行個體） 的數個執行個體是不同的執行階段伺服器上執行。|此群組的健全狀況取決於此主控件的不同執行個體的可用性。|  
|BizTalk 執行階段角色|安裝 BizTalk 執行階段的伺服器。|此群組的健全狀況需視的可用性<br /><br /> 為 SSO 服務<br />管理資料庫<br />MessageBox 資料庫<br />-SSO 資料庫<br />追蹤資料庫|  
|規則引擎的角色|伺服器有安裝規則引擎。|此群組的健全狀況取決於規則引擎服務和規則引擎資料庫的可用性<br /><br /> 規則引擎服務<br />規則引擎資料庫|  
|BAM 執行階段角色|安裝 BAM 執行階段元件伺服器。|這個健全狀況需視的可用性<br /><br /> -BAM 主要匯入資料庫<br />-BAM 封存資料庫<br />-BAM 分析<br />-BAM 警示|  
|BAM 入口網站|有了 BAM 入口網站應用程式安裝並設定 Web 伺服器。|這個健全狀況取決於 BAM 入口網站應用程式的可用性。|  
|主控件執行個體|Windows NT 服務設定為在 BizTalk 執行階段伺服器上執行。|這個健全狀況是取決於 Windows NT 服務的狀態。|  
|SSO 服務|Sso Windows NT 服務。|這個健全狀況就會根據 SSO 服務的狀態。|  
|管理資料庫|SQL Server，其中包含一或多個 BizTalk 資料庫。|這個健全狀況就會根據 SQL Server 資料庫可用性的可用性。|  
|MessageBox 資料庫|SQL Server 包含一或多個 BizTalk MessageBox 資料庫。|這個健全狀況就會根據 SQL Server 資料庫可用性的可用性。|  
|規則引擎服務|規則引擎的服務用來處理 BizTalk 規則。|這個健全狀況取決於規則引擎服務的可用性。|  
|規則引擎資料庫|SQL Server 包含一或多個 BizTalk 規則引擎資料庫。|這個健全狀況就會根據 SQL Server 資料庫可用性的可用性。|  
|BAM 主要匯入資料庫|SQL Server，其中包含 BAM 資料庫。|這個健全狀況就會根據 SQL Server 資料庫可用性的可用性。|  
|BAM 封存資料庫|SQL Server 資料庫，其中包含已封存的資料。|這個健全狀況就會根據 SQL Server 資料庫可用性的可用性。|  
|BAM 分析|包含離線和線上 BAM 分析資料。|這個健全狀況就會根據 BAM 分析資料的可用性。|  
|BAM 警示|SQL notification service。|這個健全狀況就會根據通知服務的狀態。|  
|BAM 警示的服務|SQL notification service。|這個健全狀況就會根據通知服務的狀態。|  
|BAM 分析資料庫|SQL Server 資料庫，其中包含離線和線上 BAM 分析資料。|這個健全狀況就會根據 SQL Server 資料庫可用性的可用性。|  
|BAM 星狀結構描述資料庫|包含臨時資料表以及量值和維度資料表。|這個健全狀況就會根據 SQL Server 資料庫可用性的可用性。|  
|追蹤資料庫|SQL Server 資料庫儲存狀況監控 BizTalk Server 追蹤引擎所追蹤的資料。|這個健全狀況就會根據 SQL Server 資料庫可用性的可用性。|  
|SSO 資料庫|SQL Server 裝載 SSO 資料庫。|這個健全狀況就會根據 SQL Server 資料庫可用性的可用性。|  
  
## <a name="health-roll-up-for-biztalk-application"></a>註冊 BizTalk 應用程式的健康狀況彙總  
 下圖顯示 BizTalk 應用程式和其構成成品的健全狀況狀態的彙總方式在此管理組件中。  
  
 ![應用程式模型](../technical-guides/media/biztalkserver2010mp-applicationmodel.gif "BizTalkServer2010MP ApplicationModel")  
  
 下表描述 BizTalk 應用程式工作流程圖表中顯示的元件。  
  
|名稱|Description|健全狀況|  
|----------|-----------------|------------|  
|BizTalk 群組|包含應用程式成品的群組。 所有這些成品會儲存在名為組態資料庫的集中式資料庫。 這些成品可以從任何執行階段電腦探索。|此群組的健全狀況取決於 BizTalk 主控件和 BizTalk 應用程式的可用性。|  
|Host|定義執行階段參數或要執行的各種應用程式成品的界限的邏輯實體。 以 NT 服務的這個 （主控件執行個體） 的數個執行個體是不同的執行階段伺服器上執行。|此群組的健全狀況取決於此主控件的不同執行個體的可用性。|  
|應用程式|此群組的 BizTalk 應用程式成品，例如協調流程、 結構描述、 對應和管線。 訊息元件，例如傳送埠、 接收位置和接收埠。 當 BizTalk Server 收到適當的訊息時這些成品的執行個體執行的主控件執行個體。|這個健全狀況取決於<br /><br /> 設定狀態的接收埠<br />-執行階段狀態的接收埠<br />設定傳送連接埠的狀態<br />-協調流程的健全狀況<br />協調流程的執行階段狀態|  
|接收埠|在主控件執行個體中執行之 BizTalk 成品。 這會在 BizTalk Server 接收訊息時執行。 接收埠包含一或多個接收位置。|這個健全狀況取決於設定狀態和執行階段狀態的接收埠。|  
|接收位置|從外部系統接收訊息之 BizTalk 成品。 這與它相關聯的端點會使用配接器接收訊息時。|這個健全狀況取決於設定狀態和執行階段狀態的接收位置。|  
|傳送埠|將處理過的訊息傳送至外部系統。|這個健全狀況取決於設定狀態和執行階段狀態的傳送埠。|  
|協調流程|收到的訊息從接收埠和處理訊息。 協調流程是與工作流程類似。|這個健全狀況取決於協調流程的設定狀態和執行階段狀態。|  
|傳送埠群組|邏輯群組的傳送埠接收訊息從 BizTalk 訊息方塊，並將它傳送到外部系統。|此群組的健全狀況取決於此群組中的傳送埠的健全狀況。|