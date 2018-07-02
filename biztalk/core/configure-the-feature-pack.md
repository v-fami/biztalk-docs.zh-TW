---
title: 設定 feature pack |Microsoft Docs
description: 安裝並設定功能套件 1，功能套件 2。 請參閱新的功能清單，包括 API 管理、 team services 部署，Azure 的新配接器、 備份和 BizTalk Server 2016 中的其他資訊
ms.custom: ''
ms.date: 06/26/2018
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
ms.openlocfilehash: 210089dc225d85271a8c8fdc426d2ca68bf353e1
ms.sourcegitcommit: 080224caa88f9935b5b13fa035d372f8964d2e52
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957866"
---
# <a name="configure-the-feature-pack"></a>設定 feature pack

## <a name="overview"></a>概觀

[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] 您可以使用 feature pack 來提供增強功能、 功能及更緊密地整合與 Azure。 這些功能的組件擴充中重要的領域，例如部署、 安全性、 分析、 執行階段、 維護、 標準的合規性，以及混合式整合的功能。 

> [!NOTE]
> Feature pack 所提供的 Enterprise 和 Developer edition[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]時： 
> 
> - 使用具備軟體保證 (SA)，或
> - 執行[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]在 Azure 中使用 Enterprise 合約
> 
> Feature pack 不適用於任何其他[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]edition （標準版與 Branch 版），或任何其他[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]版本 (2013 R2、 2013、 2010，依此類推)。 

## <a name="download-and-install"></a>下載並安裝

Feature pack 是累計的。 因此當您安裝 feature pack 3，也會取得的功能和更新在 feature pack 2 和 1。 您也可以取得最新的累計更新。

* 下載[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 3](https://aka.ms/bts2016fp3)。

* 下載[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 2](https://aka.ms/bts2016fp2)。

* 下載[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100)。

#### <a name="install"></a>安裝

1. 以系統管理員身分執行安裝程式。
2. 在 [**歡迎**，選取**下一步]**。 
3. 接受授權合約，然後選取 [下一步]。 
4. 繼續安裝作業。 安裝過程中，可能會開啟數個命令視窗，並將其關閉中。 完成時，系統會提示您**完成**。

安裝程式記錄檔中建立`C:\ProgramData\Microsoft\E-Business Servers Updates\Updates\Uninstall4014788-FP2\setup.log`。

>[!TIP]
> 如需完整安裝的詳細指引，請參閱[BizTalk Server 2016 功能套件 3年︰ 逐步安裝](https://blog.sandro-pereira.com/2018/06/26/biztalk-server-2016-feature-pack-3/)部落格文章。

## <a name="feature-pack-3-updates"></a>功能 Pack 3 更新

**Office 365 配接器**


Microsoft Office 365 是雲端架構的訂用帳戶服務，結合最佳的人們工具現在的運作。 Office 365 內建藉由結合同級產品中的應用程式，例如 Excel 和 Outlook，OneDrive 和 Microsoft Teams 等的功能強大的雲端服務，可讓任何人建立並共用任何地方在任何裝置上。

適用於 Office 365 的 Microsoft BizTalk Server 配接器可讓 IT 專業人員和企業開發人員與 BizTalk Server 2016 為基礎的新方案整合 Outlook 郵件、 連絡人和排程。

#### <a name="office-365-mail-adapteroffice365-mail-adaptermd"></a>[Office 365 郵件配接器](office365-mail-adapter.md)
您可以使用 BizTalk Adapter for Office 365 電子郵件，來讀取、 標示為已讀取或刪除 Outlook 電子郵件訊息，透過單向的 BizTalk Server 接收位置。 使用此配接器，您可以撰寫電子郵件訊息，包括設定訊息的優先權，透過單向靜態或動態 BizTalk Server 傳送埠。

#### <a name="office-365-calendar-adapteroffice365-calendar-adaptermd"></a>[Office 365 行事曆配接器](office365-calendar-adapter.md)
使用 BizTalk Adapter for Office 365 行事曆，您可以取得未來的行事曆事件透過單向的 BizTalk Server 接收位置。 您可以使用此配接器，來建立行事曆事件和輸入必要和選擇性出席者，透過單向靜態或動態的 BizTalk Server 傳送埠。

#### <a name="office-365-contact-adapteroffice365-contact-adaptermd"></a>[Office 365 連絡人配接器](office365-contact-adapter.md)
使用 BizTalk Adapter for Office 365 連絡人，您可以建立的連絡人，並輸入所有的設定，透過單向靜態或動態的 BizTalk Server 傳送埠。

## <a name="feature-pack-2-updates"></a>功能 Pack 2 更新

#### <a name="expose-soap-endpoints-with-api-managementcoreconnect-to-azure-api-managementmd"></a>[公開 SOAP 端點，使用 API 管理](../core/connect-to-azure-api-management.md)

展開含 Feature Pack 1 所做的 API 管理整合，您現在可以公開 Wcf-basichttp 接收位置做為使用 BizTalk Server 管理主控台的 SOAP 端點。 

#### <a name="use-the-event-hub-adapterevent-hubs-adaptermd"></a>[使用事件中樞配接器](event-hubs-adapter.md)

從 BizTalk 將訊息傳送至 Azure 事件中樞，並從 Azure 事件中樞接收訊息，BizTalk server。 當您設定傳輸屬性時，您可以輕鬆地登入您的 Azure 帳戶，並自動選取 您的 Azure 事件中樞命名空間和事件中樞。

#### <a name="backup-to-azure-blob-accountcorehow-to-configure-the-backup-biztalk-server-jobmd"></a>[備份至 Azure blob 帳戶](../core/how-to-configure-the-backup-biztalk-server-job.md)
「 備份 BizTalk Server 」 工作會備份 BizTalk 資料庫和記錄檔。 當您設定這個 SQL Agent 作業時，您可以輸入 Azure blob 儲存體帳戶內的工作屬性。 這可讓您以備份您的資料，而不是使用本機的實體磁碟的另一個選項。 

#### <a name="multi-machine-deployment-using-vstscoreconfigure-automatic-deployment-with-visual-studio-team-services-in-biztalkmd"></a>[使用 VSTS 的多電腦部署](../core/configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)
您可以使用部署群組，來部署您的應用程式的多個 BizTalk 伺服器。 您也可以設定在應用程式專案中，應用程式名稱，並輸入您的管理伺服器來安裝您的應用程式。

[部署群組](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index)如何做到這點在 VSTS 中提供更多詳細資料。  

#### <a name="use-service-bus-premiumcoresb-messaging-adaptermd"></a>[使用服務匯流排進階版](../core/sb-messaging-adapter.md)

服務匯流排配接器支援服務匯流排進階層，包括將訊息傳送至資料分割的佇列和主題。 [服務匯流排進階和標準傳訊層級](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-premium-messaging)詳細說明有關服務匯流排進階詳細資訊。 

#### <a name="use-named-instances-with-application-insightscoresend-tracking-data-to-azure-application-insights-using-biztalk-servermd"></a>[使用 Application Insights 中使用具名執行個體](../core/send-tracking-data-to-azure-application-insights-using-biztalk-server.md)
當您啟用分析，並輸入 Application Insights 金鑰時，您可能會收到錯誤： 

```
Group settings were not applied. (A database failure occurred due to database connectivity problems.)
```

會發生這種情況是當您使用具名執行個體的 SQL。 此問題已在此功能套件;您可以使用 SQL 的預設執行個體，和 SQL 具名執行個體。 

#### <a name="tls-12-support"></a>TLS 1.2 支援

在 BizTalk Server 中，包括所有配接器和所有加速器完全支援 TLS 1.2。 您可以停用 SSL、 TLS 1.0 及 BizTalk Server 上的 TLS 1.1。 

重要資訊： 

* 也與 BizTalk 通訊的任何外部系統必須支援 TLS 1.2
* 任何自訂程式碼，例如運算質，可能需要更新為支援 TLS 1.2

[TLS/SSL 通訊協定描述](https://support.microsoft.com/kb/3155464)描述如何設定 TLS 1.2 的環境。 

#### <a name="use-latest-newtonsoft-json"></a>使用最新的 Newtonsoft JSON 
Newtonsoft 是適用於.NET 的 JSON 架構。 此功能組件中，在支援版本 10.0.3 則會包含項目。 [下載 v。10.0.3](https://www.nuget.org/packages/Newtonsoft.Json/10.0.3)直接從 NuGet。 


## <a name="feature-pack-1-updates"></a>功能 Pack 1 更新

#### <a name="send-tracking-data-to-application-insightscoresend-tracking-data-to-azure-application-insights-using-biztalk-servermd"></a>[將追蹤資料傳送至 Application Insights](../core/send-tracking-data-to-azure-application-insights-using-biztalk-server.md)

將追蹤資料傳送至 Azure Application Insights，以使用其功能，例如分析、 機器學習服務、 診斷和更多功能。 

#### <a name="configure-the-operational-data-feed-using-power-bicoreconfigure-the-operational-data-feed-for-power-bi-with-biztalk-servermd"></a>[設定操作資料摘要使用 Power BI](../core/configure-the-operational-data-feed-for-power-bi-with-biztalk-server.md)

將追蹤資料傳送至 Power BI 使用 oData。 例如，從您的連接埠和協調流程取得追蹤資料的視覺表示法。 

#### <a name="connect-to-the-management-rest-apis-in-biztalkcoreinstall-and-configure-the-management-rest-apis-in-biztalk-servermd"></a>[連線到管理 BizTalk 中的 REST Api](../core/install-and-configure-the-management-rest-apis-in-biztalk-server.md)

使用 REST Api，以從遠端管理您的 BizTalk 成品，包括合約、 擱置的執行個體、 取消登錄協調流程等等。

#### <a name="configure-advanced-schedulingcoreconfigure-the-time-zone-and-recurrence-scheduling-in-biztalk-servermd"></a>[設定進階排程](../core/configure-the-time-zone-and-recurrence-scheduling-in-biztalk-server.md)

啟用進階排程在您的接收位置。 例如，設定時區，或設定在特定月份的特定日期的循環服務窗口。

#### <a name="configure-automatic-deployments-with-vstscoreconfigure-automatic-deployment-with-visual-studio-team-services-in-biztalkmd"></a>[使用 VSTS 設定自動部署](../core/configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)  

若要自動部署您的解決方案，使用 Visual Studio Team Services (VSTS) 或更新現有的應用程式。 與安裝代理程式通訊的 VSTS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。

#### <a name="connect-to-sql-server-always-encrypted-columns-with-biztalk-servercoreconnect-to-sql-server-always-encrypted-columns-with-biztalk-servermd"></a>[連接至 SQL Server Always Encrypted 資料行，與 BizTalk Server](../core/connect-to-sql-server-always-encrypted-columns-with-biztalk-server.md)  

若要查詢加密資料行，從 SQL Server 的 Always Encrypted 資料庫使用 WCF-SQL 配接器。

#### <a name="integrate-with-api-managementcoreconnect-to-azure-api-managementmd"></a>[與 API 管理整合](../core/connect-to-azure-api-management.md)

在 Azure API 管理服務中，您可以建立並公開 API 的 WSDL，並使用 BizTalk SOAP 端點的 URI。  
