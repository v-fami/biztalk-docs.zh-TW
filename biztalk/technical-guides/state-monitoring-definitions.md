---
title: 狀態監控定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2c8247-5e25-4624-9f0d-c7fe621ffba2
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 95a15bc55bce7c39bdae67e04ff0a323776a180a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011679"
---
# <a name="state-monitoring-definitions"></a>狀態監控定義
狀態監視，可協助回答問題的受監視的電腦在指定的時間，從特定的應用程式的觀點來看中是否狀況良好。 System Center Operations Manager (SCOM) 更新不同受管理的實體公開給使用者的狀態，並將狀態顯示為狀態監視檢視的一部分。  
  
 若要了解[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]狀態監視檢視，您必須瞭解 SCOM 狀態監控的基本概念。 下列用語將會用來描述狀態監控的主要組成部分：  
  
- **角色**-伺服器由服務探索所決定的環境中執行的角色。 例如，BizTalk 執行階段角色封裝的執行階段成品和 BizTalk Server 中的執行個體。  
  
- **元件**-健全狀況彙總的一部分來評量伺服器角色的整體健全狀況的子角色。 例如，BAM 警示元件用來產生警示，以指示整體健全狀況狀態。  
  
- **執行個體**-特定電腦可能裝載伺服器角色的執行個體。  
  
  簡單地說，SCOM 狀態監控的重要原則如下：  
  
- 電腦群組的健全狀況被衍生自電腦群組中所含的電腦的健全狀況。  
  
- 電腦的狀態會顯示電腦上執行的應用程式 (稱為伺服器角色) 是否狀況良好，而此狀況是由其中裝載之應用程式的狀況衍生而來。  
  
- 在應用程式層級 (伺服器角色) 上，伺服器角色的狀態是伺服器角色之所有應用程式執行個體的整體狀態。 比方說，健全狀況的一或多個成品，如協調流程、 接收位置、 接收埠和等會影響的 BizTalk 應用程式的整體健全狀況與狀態。  
  
- 在應用程式的執行個體層級 （伺服器角色執行個體） 中，應用程式執行個體的健全狀況被衍生自應用程式執行個體 （稱為元件） 各個不同部分的健全狀況。  
  
- SCOM 警示與元件的健康狀況有關聯。 當觸發警示以指示整體狀況時，元件狀態會設定為紅色、黃色或綠色。  
  
- 元件的狀況對伺服器角色的狀況會產生一定程度的影響。  
  
  在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中：  
  
- 每個 BizTalk Server 會被視為 BizTalk Server 角色的執行個體。  
  
- 因此，電腦中的 BizTalk Server 角色經過計算之後，其結果所代表的會是該電腦中所有 BizTalk Server 處理序的所有事件/活動。  
  
  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件提供 BizTalk Server 成品，包括監視狀態  
  
- 應用程式成品，例如協調流程。 這類訊息元件的接收埠、 接收位置和傳送埠。  
  
- 部署成品，例如伺服器、 主控件執行個體，SSO，依此類推。  
  
  下表列出以視覺方式呈現所有 BizTalk Server 平台和應用程式層級成品的健全狀況狀態的三種狀態。 這種方式可以在多伺服器部署中，為 SCOM 操作員提供高層次的檢視，以便快速專注於重要的問題。  
  
|成品|綠色|黃色|紅色|  
|---------------|-----------|------------|---------|  
|應用程式層級成品|處於執行狀態。|錯誤不超過 70%的執行個體。|超過 70%的執行個體將會發生錯誤，或是導致嚴重的錯誤。|  
|部署層級成品|處於執行狀態。|不適用|不在執行中狀態或已停止。|