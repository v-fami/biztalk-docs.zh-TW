---
title: "規則引擎組態和調整參數 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting, registry keys
- registry keys
- Business Rules Engine, registry keys
- troubleshooting, business rules
- validating, business rules
- business rules, validating
ms.assetid: cb0bcffe-bbc6-4495-84d2-2a822c3413b3
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6d2acc5b70f7a2be120db5159f893922135a429
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="rule-engine-configuration-and-tuning-parameters"></a>規則引擎組態和調整參數
下表包含登錄機碼的清單，這對於組態驗證和疑難排解相當有用。 這些登錄機碼會儲存在**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BusinessRules\3.0**。  
  
 除了列出的前三個索引鍵，這些機碼要讓產品，並不是使用者-自訂規則引擎。 所有機碼都是在安裝時建立，不過並沒有提供介面來設定其中的任何值。  
  
 資料表資料行的定義如下：  
  
-   **名稱**。 登錄機碼的名稱。  
  
-   **描述**。 關於機碼的位置與使用的簡短描述。  
  
-   **組態預設值**。 如果機碼不存在會傳回值。  
  
-   **安裝預設**。 安裝規則引擎時 BizTalk Server 設定的值。  
  
|名稱|Description|組態預設值|安裝預設值|  
|----------|-----------------|--------------------|---------------------|  
|InstallPath|在組態階段使用 BRE 檔案的位置。|(Null)|C:\Program Files\Common Files\Microsoft BizTalk （或在 64 位元作業系統上的 C:\Program Files (x86) \common BizTalk）|  
|DatabaseServer|使用的資料庫伺服器。|(空字串)|BRE 組態期間所指定的資料庫伺服器的名稱。|  
|DatabaseName|即將使用的資料庫名稱。|(空字串)|BRE 組態期間所指定的資料庫名稱。 一般來說，這是 BizTalkRuleEngineDb|  
|PubSubAdapterAssembly|pub/sub 配接器的組件名稱。|Microsoft.RuleEngine|Microsoft.RuleEngine|  
|PubSubAdapterClass|Pub/sub 配接器的類別名稱。|Microsoft.RuleEngine.PubSubAdapter|Microsoft.RuleEngine.PubSubAdapter|  
|DeploymentDriverAssembly|部署驅動程式的組件名稱。|Microsoft.RuleEngine|Microsoft.BizTalk.RuleEngineExtensions|  
|DeploymentDriverClass|部署驅動程式的類別名稱。|Microsoft.RuleEngine.RuleSetDeploymentDriver|Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver|  
|TrackingInterceptorAssembly|追蹤攔截器的組件名稱。|(空字串)|Microsoft.BizTalk.RuleEngineExtensions|  
|TrackingInterceptorClass|追蹤攔截器的類別名稱。|(空字串)|Microsoft.BizTalk.RuleEngineExtensions.RuleSetTrackingInterceptor|  
|TranslationTimeout|可以用來轉譯規則集的最大時間 (以毫秒為單位)。 **注意：**這可以使用 rulesetconfiguration 以覆寫每個規則集為基礎)。|60000 (1 分鐘)|60000|  
|UpdateServiceName|.NET 遠端用來尋找服務的「更新」服務名稱。|RemoteUpdateService|RemoteUpdateService|  
|UpdateServiceHost|.NET 遠端用來尋找服務的「更新」服務主機電腦。 **注意：**服務目前限制傳入訊息到同一部電腦。|localhost|localhost|  
|UpdateServicePort|.NET 遠端用來尋找服務之「更新」服務所使用的 TCP 連接埠編號。|3132|3132|  
|CacheEntries|「更新」服務快取的規則集最大值。|32|32|  
|CacheTimeout|項目超過「更新」服務快取的時間 (以秒計)。|3600 (1 小時)|3600|  
|PollingInterval|「更新」服務檢查 SqlRuleStore 以取得更新的時間 (以秒計)。|60 （1 分鐘）|60|  
|SqlTimeout|存取 SQL 規則存放區之 SQL 命令的逾時值。 此機碼的值解譯如下：<br /><br /> < 0 - 使用 .NET 預設值 (30 秒)<br /><br /> = 0 - 無限制逾時<br /><br /> > 0 - 查詢逾時之前的時間上限|-1|-1|  
  
 您也可以新增登錄機碼中所述，名為 StaticSupport[叫用類別的靜態成員](../core/invoking-static-members-of-a-class.md)。  
  
 登錄設定是所有裝載規則引擎執行個體之應用程式的全域設定。 您可以使用應用程式組態，在應用程式層級覆寫這些設定。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式中，主控件應用程式是 BTSNTSvc.exe，而組態檔則是 BTSNTSvc.exe.config；您可以在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝目錄中找到這些檔案。  您必須在如以下所示的應用程式組態檔中，為想要覆寫的組態參數指定值：  
  
```  
<configuration>  
    <configSections>  
        <section name="Microsoft.RuleEngine" type="System.Configuration.SingleTagSectionHandler" />  
    </configSections>  
    <Microsoft.RuleEngine  
        UpdateServiceHost="localhost"  
        UpdateServicePort="3132"  
        UpdateServiceName="RemoteUpdateService"  
        CacheEntries="32"  
        CacheTimeout="3600"  
        PollingInterval="60"  
        TranslationTimeout="3600"  
        CachePruneInterval="60"  
        DatabaseServer="(localhost)"  
        DatabaseName="BizTalkRuleEngineDb"  
        SqlTimeout="-1"  
        StaticSupport="1"  
    />  
</configuration>  
```