---
title: 設定此功能套件 |Microsoft 文件
description: 安裝和設定功能組件 1、 和功能套件 2。 請參閱新的功能清單，包括 API 管理中，team services 部署，Azure 的新配接器、 備份及多個 BizTalk Server 2016 中
ms.custom: ''
ms.date: 11/22/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1027bfa6-49b9-4f58-a2e2-3e0ae2fc3bf3
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5b4164cf1f1355ab9a0d2f350aa5b3b5ce411e0
ms.sourcegitcommit: f4c0d7bc4b617688c643101a34062db90014851a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2017
ms.locfileid: "25550757"
---
# <a name="configure-the-feature-pack"></a>設定此功能套件

## <a name="overview"></a>概觀

[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]您可以使用 feature pack 來提供增強功能、 功能和更緊密地與 Azure 整合。 這些功能的組件可以擴充主要區域，例如部署、 安全性、 分析、 執行階段中，與備份中的功能。 

> [!NOTE]
> Feature pack 可用與 Enterprise 和 Developer edition 搭配[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]時： 
> 
> - 搭配軟體保證 (SA)，或
> - 執行[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]在 Azure 中使用 Enterprise 合約
> 
> Feature pack 不適用於任何其他[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]edition 或任何其他[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]版本。 

## <a name="download-and-install"></a>下載並安裝

Feature pack 是累計的。 因此當您安裝功能套件 2，您也得到的功能和更新 feature pack 1。

* 下載[!INCLUDE[bts2016_md](../includes/bts2016-md.md)][功能套件 2](https://aka.ms/bts2016fp2)。

* 下載[!INCLUDE[bts2016_md](../includes/bts2016-md.md)][功能套件 1](https://www.microsoft.com/download/details.aspx?id=55100)。

#### <a name="install"></a>Install

1. 以系統管理員身分執行安裝程式。
2. 在**歡迎使用**，選取**下一步**。 
3. 接受授權合約，然後選取 [下一步]。 
4. 繼續安裝作業。 在安裝期間，數個命令視窗可能會開啟和關閉。 完成時，系統會提示您**完成**。

安裝程式記錄檔中建立`C:\ProgramData\Microsoft\E-Business Servers Updates\Updates\Uninstall4014788-FP2\setup.log`。

>[!TIP]
> 如需完整安裝的詳細指引，請參閱[Feature Pack 的逐步安裝](https://blog.sandro-pereira.com/2017/04/27/microsoft-biztalk-server-2016-feature-pack-1-step-by-step-installation/)部落格文章。

## <a name="feature-pack-2-updates"></a>功能 Pack 2 更新

#### <a name="expose-soap-endpoints-with-api-managementcoreconnect-to-azure-api-managementmd"></a>[公開 SOAP 端點，使用 API 管理](../core/connect-to-azure-api-management.md)

擴充功能組件 1 所做的 API 管理整合，您現在可以公開 Wcf-basichttp 接收位置使用 BizTalk Server 管理主控台的 SOAP 端點。 

#### <a name="use-the-event-hub-adapterevent-hubs-adaptermd"></a>[使用事件中心配接器](event-hubs-adapter.md)

從 BizTalk 傳送訊息至 Azure 事件中樞，並從 Azure 事件中心接收訊息至 BizTalk Server。 當您設定傳輸屬性時，您可以輕鬆地登入您的 Azure 帳戶，並自動選取 您的 Azure 事件中樞命名空間和事件中心。

#### <a name="backup-to-azure-blob-accountcorehow-to-configure-the-backup-biztalk-server-jobmd"></a>[備份至 Azure blob 帳戶](../core/how-to-configure-the-backup-biztalk-server-job.md)
「 備份 BizTalk Server 」 工作會備份 BizTalk 資料庫和記錄檔。 當您設定此 SQL Agent 作業時，您可以輸入的工作屬性內的 Azure blob 儲存體帳戶。 這可讓您備份您的資料，而不是使用本機實體磁碟的另一個選項。 

#### <a name="multi-machine-deployment-using-vstscoreconfigure-automatic-deployment-with-visual-studio-team-services-in-biztalkmd"></a>[使用 VSTS 多電腦部署](../core/configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)
使用部署群組，您可以部署多個 BizTalk Server 應用程式。 您也可以設定在應用程式專案中，應用程式名稱，並輸入您的管理伺服器安裝應用程式。

[部署群組](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index)這在 VSTS 中的完成方式提供更多詳細資料。  

#### <a name="use-service-bus-premiumcoresb-messaging-adaptermd"></a>[使用服務匯流排 Premium](../core/sb-messaging-adapter.md)

服務匯流排配接器支援服務匯流排 Premium，包括將訊息傳送至資料分割的佇列和主題。 [服務匯流排 Premium 和 Standard 傳訊層](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-premium-messaging)有關服務匯流排的高階詳細資料。 

#### <a name="use-named-instances-with-application-insightscoresend-tracking-data-to-azure-application-insights-using-biztalk-servermd"></a>[使用 Application Insights 中使用具名執行個體](../core/send-tracking-data-to-azure-application-insights-using-biztalk-server.md)
當您啟用分析，並輸入 Application Insights 金鑰時，您可能會收到錯誤： 

```
Group settings were not applied. (A database failure occurred due to database connectivity problems.)
```

會發生這種情況是當您使用 SQL 具名執行個體。 這是在此功能套件; 中修正您可以使用 SQL 的預設執行個體，而且 SQL 具名執行個體。 

#### <a name="tls-12-support"></a>TLS 1.2 支援

在 BizTalk Server 中，包括所有介面卡和所有加速器，則完全支援 TLS 1.2。 您可以停用 SSL、 TLS 1.0 和 BizTalk Server 上的 TLS 1.1。 

索引鍵的資訊： 

* 任何外部系統溝通 BizTalk 也需要支援 TLS 1.2
* 任何自訂程式碼，例如運算質，可能需要更新為支援 TLS 1.2

[TLS/SSL 通訊協定的描述](https://support.microsoft.com/kb/3155464)描述如何設定 TLS 1.2 環境。 

#### <a name="use-latest-newtonsoft-json"></a>使用最新 Newtonsoft JSON 
Newtonsoft 是適用於.NET 的 JSON 架構。 此功能套件，在支援版本 10.0.3 則會包含項目。 [下載 v。10.0.3](https://www.nuget.org/packages/Newtonsoft.Json/10.0.3)直接從 NuGet。 


## <a name="feature-pack-1-updates"></a>功能 Pack 1 更新

#### <a name="send-tracking-data-to-application-insightscoresend-tracking-data-to-azure-application-insights-using-biztalk-servermd"></a>[將追蹤資料傳送至 Application Insights](../core/send-tracking-data-to-azure-application-insights-using-biztalk-server.md)

將追蹤資料傳送到 Azure Application Insights 以使用其功能，例如分析、 機器學習、 診斷與多個。 

#### <a name="configure-the-operational-data-feed-using-power-bicoreconfigure-the-operational-data-feed-for-power-bi-with-biztalk-servermd"></a>[設定操作資料摘要使用 Power BI](../core/configure-the-operational-data-feed-for-power-bi-with-biztalk-server.md)

將追蹤資料傳送到 Power BI 使用 oData。 例如，從您的連接埠和協調流程取得追蹤資料的視覺表示法。 

#### <a name="connect-to-the-management-rest-apis-in-biztalkcoreinstall-and-configure-the-management-rest-apis-in-biztalk-servermd"></a>[連線到管理 REST Api，在 BizTalk 中](../core/install-and-configure-the-management-rest-apis-in-biztalk-server.md)

使用 REST Api 用來從遠端管理您的 BizTalk 成品，包括合約、 擱置的執行個體、 取消登錄協調流程、 等等。

#### <a name="configure-advanced-schedulingcoreconfigure-the-time-zone-and-recurrence-scheduling-in-biztalk-servermd"></a>[設定進階排程](../core/configure-the-time-zone-and-recurrence-scheduling-in-biztalk-server.md)

啟用進階排程在您的接收位置。 例如，設定時區，或設定的特定日期上特定月份循環服務窗口。

#### <a name="configure-automatic-deployments-with-vstscoreconfigure-automatic-deployment-with-visual-studio-team-services-in-biztalkmd"></a>[利用 VSTS 設定自動部署](../core/configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)  

若要自動部署您的解決方案，使用 Visual Studio Team Services (VSTS) 或更新現有的應用程式。 與上安裝代理程式通訊的 VSTS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。

#### <a name="connect-to-sql-server-always-encrypted-columns-with-biztalk-servercoreconnect-to-sql-server-always-encrypted-columns-with-biztalk-servermd"></a>[連接至 BizTalk Server 與 SQL Server 永遠加密的資料行](../core/connect-to-sql-server-always-encrypted-columns-with-biztalk-server.md)  

使用 WCF-SQL 配接器，來查詢從 SQL Server 中的永遠加密資料庫加密的資料行。

#### <a name="integrate-with-api-managementcoreconnect-to-azure-api-managementmd"></a>[使用 API 管理整合](../core/connect-to-azure-api-management.md)

在 Azure API 管理服務中，您可以建立和公開的 WSDL，API 和使用的 BizTalk SOAP 端點的 URI。  