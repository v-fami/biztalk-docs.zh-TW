---
title: "檢視 Operations Manager 主控台中的資訊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6acdf425-4c36-4d89-9493-81b33481fe6d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 687932839c379ed9589a51baae0ae8562f4af705
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="viewing-information-in-the-operations-manager-console"></a>檢視 Operations Manager 主控台中的資訊
使用所提供的檢視[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件以了解目前的可用性、 設定、 健全狀況，以及 BizTalk Server 環境的效能。 檢視可能會包含冗長的物件清單。 若要尋找特定的物件或物件群組，可以使用 Operations Manager 工具列上的 [領域]、[搜尋] 和 [尋找] 按鈕。 如需詳細資訊，請參閱 「 如何管理監視資料使用領域、 搜尋和尋找 Operations Manager 2007 R2\2012 說明中的主題。  
  
 下列檢視會直接列 **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**  Operations 主控台的 [監視] 窗格中的節點。  
  
-   **應用程式檢視**: BizTalk 系統管理員是有興趣監視的狀態和健全狀況的各種 BizTalk Server 成品和應用程式，例如協調流程傳送埠、 接收位置，等等。  
  
-   **部署檢視**： 企業 IT 系統管理員想要監視的狀態和健全狀況的各種機器主控 SQL Server 資料庫，SSO 服務，主機執行個體上，IIS，在裝載電腦的企業部署網路服務等等。  
  
## <a name="application-views"></a>應用程式檢視  
 應用程式檢視包含下表中所述的元素。  
  
### <a name="elements"></a>元素  
  
|檢視表名稱|Description|  
|---------------|-----------------|  
|應用程式狀態檢視|這是顯示的 BizTalk 應用程式的健全狀況儀表板檢視。 BizTalk 應用程式的健全狀況取決於其構成成品，例如協調流程、 傳送埠群組、 傳送埠、 接收埠和接收位置的健全狀況。 [詳細資料檢視] 窗格會提供裝載 BizTalk 應用程式的屬性。|  
|群組狀態檢視|這是顯示的 BizTalk 群組的健全狀況儀表板檢視。 BizTalk 群組的健全狀況取決於 BizTalk 主控件和 BizTalk 應用程式的健全狀況。 [詳細資料檢視] 窗格會提供 BizTalk 群組的內容。|  
|主機狀態檢視|這是顯示的 BizTalk 主控件的健全狀況儀表板檢視。 BizTalk 主控件的健全狀況取決於裝載 BizTalk 應用程式的執行個體的健全狀況。 [詳細資料檢視] 窗格會提供 BizTalk 主控件的屬性。|  
  
#### <a name="application-artifacts-views"></a>應用程式成品檢視  
 應用程式成品檢視包含下表中所述的元素。  
  
### <a name="elements"></a>元素  
  
|檢視表名稱|Description|  
|---------------|-----------------|  
|協調流程狀態檢視|顯示裝載的應用程式的協調流程的組態和執行階段狀態。|  
|接收位置的狀態檢視|顯示裝載的應用程式的接收位置的組態和執行階段狀態。|  
|接收連接埠狀態檢視|顯示裝載的應用程式的接收埠的組態和執行階段狀態。|  
|傳送埠群組狀態檢視|顯示裝載的應用程式的傳送埠群組的組態和執行階段狀態。|  
|傳送連接埠狀態檢視|顯示裝載的應用程式的傳送埠的組態和執行階段狀態。|  
  
## <a name="deployment-views"></a>部署檢視  
 部署檢視包含下表中所述的元素。  
  
### <a name="elements"></a>元素  
  
|檢視表名稱|Description|  
|---------------|-----------------|  
|部署狀態檢視|這是會顯示 BizTalk 部署群組的健全狀況儀表板檢視。 BizTalk 部署群組的健全狀況取決於其構成的執行階段伺服器元件，例如 BAM 角色、 規則引擎的角色，BizTalk 執行階段角色和 BizTalk 主控件的健全狀況。 [詳細資料檢視] 窗格會提供 BizTalk 部署群組的內容。|  
|主機狀態檢視|這是顯示的 BizTalk 主控件的健全狀況儀表板檢視。 BizTalk 主控件的健全狀況取決於裝載 BizTalk 應用程式的執行個體的健全狀況。 [詳細資料檢視] 窗格會提供 BizTalk 主控件的屬性。|  
|規則引擎的角色狀態檢視|這是顯示在執行階段伺服器正在執行規則引擎服務的健全狀況儀表板檢視。 [詳細資料檢視] 窗格會提供已安裝的規則引擎服務的執行階段伺服器的屬性。|  
|執行階段角色狀態檢視|這是會顯示已安裝執行階段規則引擎服務的執行階段伺服器的健全狀況儀表板檢視。 BizTalk 執行階段角色的健全狀況取決於其元件，例如 SSO 服務、 管理資料庫、 messagebox 資料庫、 SSO 資料庫和追蹤資料庫的健全狀況。 [詳細資料檢視] 窗格會提供執行階段伺服器的內容。|  
  
### <a name="bam-component-views"></a>BAM 元件檢視  
  
### <a name="elements"></a>元素  
  
|檢視表名稱|Description|  
|---------------|-----------------|  
|BAM 警示的狀態檢視|顯示 BizTalk BAM 警示元件的狀態檢視。|  
|BAM 分析狀態檢視|顯示 BizTalk BAM 分析元件的狀態檢視。|  
|BAM 效能檢視|[圖例] 窗格會顯示 BAM 效能計數器。|  
|BAM 入口網站狀態檢視|顯示 BAM 入口網站的狀態檢視。|  
|BAM 執行階段狀態檢視|顯示 BAM 執行階段的狀態檢視。|  
  
#### <a name="bam-alerts"></a>BAM 警示  
  
### <a name="elements"></a>元素  
  
|檢視表名稱|Description|  
|---------------|-----------------|  
|BAM 警示的狀態檢視|顯示其通知服務，並產生任何重要的服務時無法使用 BizTalk BAM 警示的清單。|  
  
##### <a name="runtime-component-views"></a>執行階段元件檢視  
  
### <a name="elements"></a>元素  
  
|檢視表名稱|Description|  
|---------------|-----------------|  
|應用程式服務狀態檢視|顯示在 BizTalk 群組中的所有主控件執行個體的健全狀況。|  
|訊息方塊效能狀態檢視|[圖例] 窗格會顯示訊息方塊追蹤資料大小的效能計數器。|  
|傳訊配接器效能檢視|[圖例] 窗格顯示的效能計數器的 MSMQ 接收配接器接收的位元組。|  
|傳訊效能檢視|[圖例] 窗格會顯示使用中的接收位置的效能計數器。|  
|協調流程效能檢視|[圖例] 窗格會顯示為可執行的協調流程的效能計數器。|  
|伺服器資源使用狀況 檢視|[圖例] 窗格顯示的效能計數器的實體磁碟閒置時間百分比。|  
  
###### <a name="runtime-alerts"></a>執行階段警示  
  
### <a name="elements"></a>元素  
  
|檢視表名稱|Description|  
|---------------|-----------------|  
|核心警示檢視|顯示 BizTalk 核心警示。|  
|訊息的警示檢視|顯示 BizTalk 訊息的警示。|