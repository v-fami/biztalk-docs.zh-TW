---
title: 什麼是 BizTalk Server 2016 的新功能 |Microsoft 文件
description: 變更和改進，包括 feature pack、 配接器、 安全性、 追蹤、 效能及多個 BizTalk Server 2016
ms.custom: ''
ms.prod: biztalk-server
ms.date: 11/15/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3fce1fe8-f515-462d-bf6d-19408d515479
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa8e28b3c54afd130176e9bb19b2e0b1a59415d0
ms.sourcegitcommit: f65e8ed2b8c18cded26b9d60868fb6a56bcc1205
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
ms.locfileid: "25497759"
---
# <a name="whats-new-in-biztalk-server-2016"></a>BizTalk Server 2016 的新功能
閱讀以了解 [!INCLUDE[bts2016](../includes/bts2016-md.md)] 的新功能。 
  
## <a name="new-in-biztalk-server-2016"></a>BizTalk Server 2016 的新功能  
  
|功能|說明|  
|-------------|-----------------|  
|支援較新的平台|[!INCLUDE[bts2016](../includes/bts2016-md.md)] 新增對下列 Microsoft 平台的支援：<br /><br /> -   Visual Studio 2015<br />-   Windows Server 2016<br />-   [!INCLUDE[sqlserver2016](../includes/sqlserver2016-md.md)]<br />-   Office 2016<br/><br/>[BizTalk Server 2016 的硬體和軟體需求](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)|  
| Feature Pack 2 | 增強功能包括使用 API 管理更緊密地整合 Azure 事件中心配接器、 備份至 Azure blob 儲存體帳戶、 服務匯流排的磁碟分割的支援以及更多。 <br/><br/>[安裝 Feature Pack](https://www.microsoft.com/download/details.aspx?id=55100)<br/>[請參閱什麼納入，並設定其功能](../core/configure-the-feature-pack.md) |
| Feature Pack 1 | 包含使用 VSTS 自動部署的支援、將追蹤資料傳送給 Azure Application Insights 與 Power BI，以及接收位置的進階排程選項等等。<br/><br/>[安裝 Feature Pack](https://www.microsoft.com/download/details.aspx?id=55100)<br/>[請參閱什麼納入，並設定其功能](../core/configure-the-feature-pack.md) |
|[!INCLUDE[sqlserver2016](../includes/sqlserver2016-md.md)] AlwaysOn 可用性群組|支援包括：<br /><br /> -   以內部部署方式及在 [!INCLUDE[winazure](../includes/winazure-md.md)] IaaS 虛擬機器中使用<br />-   用於生產環境工作負載<br />-   提供 [!INCLUDE[winazure](../includes/winazure-md.md)] 的高可用性 (HA) 解決方案 <br/><br/>[使用 SQL Server AlwaysOn 的高可用性群組](../core/high-availability-using-sql-server-always-on-availability-groups.md)<br/><br/> 請參閱[分散式交易，永遠在 ag](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring)針對任何 SQL 特定需求和功能。|  
|生產環境中的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Azure VM|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Azure 虛擬機器現已完全支援生產環境。 現在，您可以使用 [!INCLUDE[sqlserver2016](../includes/sqlserver2016-md.md)] AlwaysOn 的高可用性解決方案。<br/><br/>[使用 SQL Server AlwaysOn 的高可用性群組](../core/high-availability-using-sql-server-always-on-availability-groups.md)|  
|Logic Apps 配接器|連接到裝載在 Azure 中的 Logic Apps，並取得 Salesforce、SharePoint、CRM Online 等所有連接器的存取權。 比方說，您可以在 BizTalk Server 中接受訂單、連接 Logic Apps 並更新 Salesforce。<br/><br/>[Logic Apps 配接器](../core/logic-app-adapter.md)|  
| File adapter (FILE 配接器) | 連接 Azure 儲存體檔案共用。 您可以接收來自 Azure 檔案共用的檔案，並將訊息傳送至 Azure 檔案共用。 <br/><br/>[設定 FILE 配接器](../core/configure-the-file-adapter.md)|
| FTP 配接器 | 不再需要 SYST 命令。 當您設定接收位置或傳送埠上的 FTP 配接器時，有一個名稱為 [FTP 伺服器類型] 的屬性。 您可以使用這個屬性來選擇所要的 FTP 伺服器，以決定是否需要使用 SYST。 <br/><br/>這項變更可讓系統支援更多 FTP 伺服器。 <br/><br/> [設定 FTP 配接器](../core/configuring-the-ftp-adapter.md)|
|SFTP 配接器| SFTP 配接器已經過重新設計，可使用 WinSCP 來連接 SFTP，以便支援更多 SFTP 伺服器。 用戶端記錄和其他加密編碼器也是新增的功能。 <br/><br/>[SFTP 配接器](../core/sftp-adapter.md)|  
| 允許匯入追蹤設定 | 將繫結匯入檔案時，您可以選擇匯入 (或不匯入) 協調流程、傳送埠等項目上所啟用的追蹤屬性。 這是全域設定 (於群組層級設定)，因此您可以在不同環境中設定這項功能。 比方說，您可以針對開發環境匯入現有的追蹤屬性；針對生產環境則不匯入追蹤屬性。<br/><br/>請參閱**BizTalk 設定儀表板，群組頁面** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|
| 共用存取簽章 (SAS) | 針對服務匯流排與 *BasicHttpRelay*、*NetTcpRelay*、*BasicHttp* 和 *WebHttp* 配接器的連線，您可以使用 SAS 驗證。<br/><br/>[WCF-BasicHttpRelay 配接器](../core/wcf-basichttprelay-adapter.md)<br/>[WCF-NetTcpRelay 配接器](../core/wcf-nettcprelay-adapter.md)<br/>[WCF-BasicHttp 配接器](../core/wcf-basichttp-adapter.md)<br/>[WCF-WebHTTP 配接器](../core/wcf-webhttp-adapter.md)<br/><br/> [SB-Messaging 配接器](../core/sb-messaging-adapter.md)現已包含可使用 PowerShell 取得存取控制 (ACS) 值的步驟。|
|動態連接埠上的排序傳遞|適用於支援在靜態傳送埠上進行排序傳遞的配接器。 您可以在 BizTalk 管理主控台中，啟用排序的傳遞選項。<br /><br />[如何設定傳送埠的傳輸進階選項](../core/how-to-configure-backup-transport-options-for-a-send-port.md)<br />[訊息的排序傳遞](../core/ordered-delivery-of-messages.md)|  
|SHA-2 雜湊函數|完全支援 SHA-2，包括：<br /><br /> <ul><li>BizTalk 可跨所有元件使用 SHA2 簽署的憑證，包括 HTTPS、FTPS、POP3 及 WCF 配接器中的 SSL 訊息傳送 </li><li>AS2、RosettaNet 和 MIME/SMIME 編碼器中的簽章金鑰，支援下列進階加密標準 (AES) 交換系統：<ul><li>AES128 (預設)</li><li>AES192</li><li>AES256</li><br /></ul></li><li>AS2 支援下列以 SHA2 為基礎的 MIC 計算：<ul><li>SHA256 (預設)</li><li>SHA384</li><li>SHA512</li><br /></ul></li><li>RosettaNet 支援使用下列以 SHA-2 為基礎的摘要方法：<ul><li>SHA256 (預設)</li><li>SHA384</li><li>SHA512</li><br /></ul></li><li>基於回溯相容性，SHA1 憑證將持續運作</li></ul><br />[設定驗證 (AS2)](../core/configuring-validation-as2.md)<br />[設定通知 (MDN) (AS2)](../core/configuring-acknowledgements-mdns-as2.md)<br />[如何設定 MIME SMIME 編碼器管線元件](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)|  
|編譯對應|使用 XslTransform 或 XslCompiledTransform 來編譯對應<br/><br/>[設定對應編譯和輸出設定](../core/how-to-specify-xslt-output-settings.md)|  
|結構描述視窗|在 BizTalk 對應工具中，您可新增/取代來源結構描述和目的結構描述。 當您執行此作業時，型別選擇器視窗即可調整大小。 此變更可讓您放大視窗，檢視您結構描述的完整名稱。<br/><br/>[如何調整結構描述選擇器的大小，以及展開和摺疊結構描述樹狀結構](../core/how-to-resize-the-schema-picker-and-expand-and-collapse-the-schema-trees.md)|  
|配接器和加速器|改進和變更包括：<ul><li>SAP 配接器支援傳統 RFC SDK，以及 SAP 繫結屬性中的 .NET 連接器。 <br/><br/>安裝「適用於 .NET 的 SAP 連接器」，這可在 SAP Service Marketplace (service.sap.com/connectors) 取得。 在安裝期間，請務必選取 [將組件安裝到 GAC]。<br/><br/>如需其他詳細資料，請參閱 [SAP.NET 連接器的 WCF SAP 配接器支援](https://support.microsoft.com/kb/3100811)。  </li><br /><li>BizTalk Accelerator for HL7：接收位置上的 MLLP 配接器現已提供選項，讓您可以起始對遠端 LOB 接聽程式的輸出連線。</li></ul>|  
|匯入/匯出合作對象|變更包括：<br /><br /> -   匯入和匯出選項可與應用程式區隔開來獨立運作。 例如，您可以匯出合作對象，而不匯出應用程式。 您也可以匯入合作對象，而不匯入應用程式。<br />-   可以選擇您想要匯入或匯出哪些合作對象、商務設定檔與協議。<br />-   可以繼續按照 [!INCLUDE[bts2013r2](../includes/bts2013r2-md.md)], [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013 和  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010 的方式，匯入/匯出企業對企業的成品。<br/><br/>[使用繫結檔案匯入或匯出](../core/use-binding-files-to-import-or-export.md)|  
|BizTalk 管理|除了更新穎的外觀和操作方式以外，還包括下列一些其他變更：<br /><br /> -   可同時設定多個主控件/主控件執行個體。 例如，您可以同時設定多個主控件執行個體的 .NET CLR 設定。<br />-   使用新的搜尋功能來篩選並尋找應用程式中的成品，例如結構描述、資源等項目。<br />-   在進行擱置訊息的疑難排解時，您可以同時將多個擱置訊息儲存到檔案中。<br /><br />[使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md)|  
|其他更新|<ul><li>[!INCLUDE[HL7_CurrentVersion_FirstRef_md](../includes/hl7-currentversion-firstref-md.md)] 會啟動與企業營運伺服器 (LOB) 之間的連線，並透過連線推送訊息。 LOB 會等候連線，然後傳送訊息。 <br/><br/>在先前的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 版本中，HL7 MLLP 接收配接器會等候 LOB 伺服器連線到 HL7，然後再傳送訊息。 LOB 連線到 HL7，然後傳送訊息。 </li><br/><li>Office Web 元件 (OWC) 在安裝中現已為選擇性，並另外列於 [程式] 中</li><br/><li>已將協調流程執行個體識別碼新增到 XLANG FireEvent 追蹤輸出</li></ul>|   
  
## <a name="deprecated--removed-list"></a>已取代及已移除項目的清單  
  
|計畫|狀態|取代|  
|-------------|------------|-----------------|  
|RFID Mobile|已移除|無|  
|RFID 伺服器|已移除|無|  
|SharePoint SSOM/Web 服務配接器|已移除|請使用 CSOM (用戶端物件模型) 選項。<br /><br /> [Windows SharePoint Services 配接器](../core/windows-sharepoint-services-adapter.md)<br /><br /> [附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)|  
|SOAP adapter (SOAP 配接器)|已被取代|[WCF-BasicHttp 配接器](../core/wcf-basichttp-adapter.md)|  
|舊的 SQL 配接器|已被取代|[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] 中的 WCF-SQL 配接器|  
|UDDI|已移除|無|  
  
> [!IMPORTANT]
>  較新版本的 BizTalk 中可能還存有這些已被取代的部分功能。 在這種情況下，請注意下列事項：  
>   
> -   此功能可能在 BizTalk 中，在內部使用，且不是客戶解決方案所使用。 客戶解決方案不支援這類功能。  
> -   介面已由 Microsoft 修改，可能無法公開使用。

## <a name="next-steps"></a>後續的步驟
[硬體和軟體需求](hardware-and-software-requirements-for-biztalk-server-2016.md)  
[安裝與安裝的必要條件](set-up-and-install-prerequisites-for-biztalk-server-2016.md)  
[安裝 BizTalk](install-biztalk-server-2016.md)