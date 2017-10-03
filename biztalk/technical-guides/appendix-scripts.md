---
title: "附錄： 指令碼 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6394321-13c9-4b1d-b529-eba3d53b33c4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12df00876f6b2da9ebb98631016bd42947b4a40a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="appendix-scripts"></a>附錄： 指令碼
下列指令碼會包含在此管理組件。  
  
|指令碼|目的|  
|------------|-------------|  
|Microsoft.BizTalk.Server.2013.ArtifactsDiscovery.vbs|此指令碼會探索 $Config 為基礎的應用程式成品選項 $ 參數。 選項包括<br /><br /> -所有傳送埠，請在應用程式，其裝載的相關傳送埠群組，應用程式和 [傳送埠群組包含傳送埠] 的關聯性。<br />-所有協調流程應用程式中，其與應用程式的裝載關聯性。<br />-All 接收埠、 接收位置的應用程式，其裝載關聯性 '應用程式和' 接收埠包含接收位置 ' 的關聯。|  
|Microsoft.BizTalk.Server.2013.ApplicationDiscovery.vbs|此指令碼會探索下列各項：<br /><br /> 的群組以及 「 群組主機應用程式 」 的關聯性中所有應用程式。<br />-所有主機群組以及 「 主機群組主機 」 的關聯性。|  
|Microsoft.BizTalk.Server.2013.BAMAnalysisDiscovery.vbs|此指令碼會探索 BAM 分析，並發出警示在探索到 BAM 執行階段元件的電腦上的元件。|  
|Microsoft.BizTalk.Server.2013.BAMPortalDiscovery.vbs|此指令碼會探索 iis 的電腦上設定 BAM 入口網站。 這也會探索 BAM 角色和 BAM 入口網站中的內含項目。|  
|Microsoft.BizTalk.Server.2013.BAMRuntimeDiscovery.vbs|此指令碼會探索傳遞做為參數 $Config 的電腦上的 BAM 執行階段元件/ComputerName$。 如果未傳遞的電腦名稱，然後它會探索 BAM 管理資料庫中的最小伺服器識別碼的執行階段電腦上。 這也會探索 BAM 角色和 BAM 執行階段中的內含項目。|  
|Microsoft.BizTalk.Server.2013.BizTalkApplicationServiceDiscovery.vbs|此指令碼會探索所有的 BizTalk 應用程式服務，以及其裝載的關係，以執行階段角色的電腦上。|  
|Microsoft.BizTalk.Server.2013.BizTalkGroupDiscovery.vbs|此指令碼會探索傳遞做為參數 $Config 的電腦上的 BizTalk 群組/ComputerName$。 如果電腦名稱未跳過會探索 「 管理 」 資料庫中的最低伺服器識別碼的執行階段電腦上的群組。|  
|Microsoft.BizTalk.Server.2013.BizTalkRoleDiscovery.vbs|此指令碼會探索指定參數為基礎的電腦中的 BizTalk 伺服器角色。 $Config 選項 $。 其中包括下列選項：<br /><br /> BizTalk 執行階段角色、 BizTalk 群組的部署和執行階段群組部署中的內含項目。<br />BizTalk 規則引擎的角色、 BizTalk 群組的部署和群組部署中的規則引擎的內含項目。 BAM 角色一律會探索與任何一個選項，以及其群組部署中的內含項目。|  
|BizTalkAnalysisDatabaseMonitor.vbs|此指令碼會產生的連線為基礎的 SQL 分析資料庫可用性的監視資料。 監視狀態可以是成功或錯誤。|  
|BizTalkArtifactConfigurationMonitor.vbs|此指令碼會產生 BizTalk 應用程式成品組態的監視資料。 每個成品將會是三個監視的狀態成功、 警告和錯誤的其中之一。|  
|BizTalkArtifactSuspendedInstancesMonitor.vbs|此指令碼會產生擱置的執行個體，每個成品的數目為基礎的 BizTalk 應用程式成品執行階段狀態的監視資料。 每個成品會在三個監視的狀態成功、 警告和錯誤的其中一個。|  
|BizTalkBAMPortalMonitor.vbs|此指令碼會產生 BAM 入口網站的可用性監視資料。 監視狀態可以是成功或錯誤。|  
|BizTalkHostConfigurationMonitor.vbs|此指令碼會產生所有其主機執行個體的可用性 (BTSNTSvc.exe) 為基礎的 BizTalk 主控件的監視資料。 可以是任一個成功的監視狀態 (執行 > = 成功限制)、 警告 (執行 > = 警告限制且在執行 < 成功限制) 或錯誤。|  
|BizTalkDatabaseMonitor.vbs|此指令碼會產生的連線為基礎的 SQL 資料庫可用性的監視資料。 監視狀態可以是成功或錯誤。|  
|BizTalkMultipleDatabaseMonitor.vbs|此指令碼會產生可用性群組的 SQL 資料庫當做單一實體連線為基礎的監視資料。 監視狀態可能是其中一個錯誤 （主要資料庫無法使用），警告 （某些無法使用的非主要資料庫） 或 成功 （所有可用的資料庫）。|  
|BizTalkHostProbeAction.vbs|此指令碼會產生診斷資料為根據的所有主機的執行個體 (BTSNTSvc.exe) 可用性的 BizTalk 主控件。 錯誤和警告狀態，它會顯示未執行的主控件執行個體。|  
|Microsoft.BizTalk.Server.2013.HostAction.vbs|此指令碼用來啟動/停止 BizTalk 主控件。|  
|Microsoft.BizTalk.Server.2013.OrchestrationAction.vbs|此指令碼用來啟動/停止協調流程 （BizTalk 應用程式成品）。|  
|Microsoft.BizTalk.Server.2013.EnableReceiveLocation.vbs|此指令碼是用來啟用/停用接收位置 （BizTalk 應用程式成品）。|  
|Microsoft.BizTalk.Server.2013.SendPortAction.vbs|此指令碼用來啟動/停止傳送埠 （BizTalk 應用程式成品）。|  
|Microsoft.BizTalk.Server.2013.SendPortGroupAction.vbs|此指令碼用來啟動/停止傳送埠群組 （BizTalk 應用程式成品）。|