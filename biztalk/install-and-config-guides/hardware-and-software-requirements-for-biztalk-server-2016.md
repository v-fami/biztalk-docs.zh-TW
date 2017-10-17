---
title: "硬體和軟體需求適用於 BizTalk Server 2016 |Microsoft 文件"
description: "軟體必要條件和支援的版本會列出安裝 BizTalk Server 2016"
ms.custom: 
ms.prod: biztalk-server
ms.date: 10/09/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6120afd-310e-4155-8c23-aadb5b9a1a35
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63993b544aead238d28623ab291887535e2f06ab
ms.sourcegitcommit: 85e816bcdeb3d66ea5018cf88aea7059f74f7d80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2017
---
# <a name="hardware-and-software-requirements-for-biztalk-server-2016"></a>BizTalk Server 2016 的硬體和軟體需求

## <a name="hardware-requirements"></a>硬體需求
下表列出 BizTalk Server 電腦的最小硬體需求。 在實際執行環境中，流量可能需要更大的伺服器硬體需求。 

| 資源  |最小需求 |
| --- | --- |
|電腦和處理器 | 配備 Intel Pentium 相容 CPU 的電腦： <ul><li>1 GHz 以上的單一處理器</li><li>900 MHz 以上的雙處理器</li><li>700 MHz 以上的四處理器</li></ul> **注意**：支援超執行緒和雙核心處理器。<br/><br/>64 位元版本的 BizTalk Server 需要在 x64 系統上執行 64 位元作業系統。 採用與 AMD64 (x86-64) 和延伸記憶體 64 位元技術 (EM64T) 處理器架構相容之 CPU 的電腦會被視為 x64 架構系統。<br/><br/>Itanium 系統不支援 BizTalk Server。 |
|記憶體 | 2 GB 或以上|
|硬碟  |完整安裝需要 10 GB 的可用硬碟空間，包括作業系統和所有必要軟體。 硬碟必須是 NTFS 格式。|

> [!TIP] 
> 列出的硬體需求是最小需求。 每個環境都不同，但您的環境極有可能需要更多需求。 請參閱 [Recommendations for Installing, Sizing, Deploying, and Maintaining a BizTalk Server Solution](http://social.technet.microsoft.com/wiki/contents/articles/666.recommendations-for-installing-sizing-deploying-and-maintaining-a-biztalk-server-solution.aspx) (安裝、調整大小、部署和維護 BizTalk Server 解決方案的建議)。 


## <a name="software-requirements--supported-versions"></a>軟體需求 （& s) 支援的版本

| 軟體  |   版本 |  必要項目 | 
| --- | --- | --- | 
| Microsoft Windows | <ul><li>Windows Server 2016</li><li>Windows Server 2012 R2</li><li>Windows 10</li><li>Windows 8.1 </li></ul> | | 
| Internet Information Services (IIS)   | 隨附於作業系統的版本。<br/><br/> [KB 224609](https://support.microsoft.com/kb/224609) 會列出 IIS 版本。 | 提供可擴充的 Web 應用程式基礎結構，而且是 EDI、BAM 和 SharePoint 配接器的必要項目。 |
| Windows Identity Foundation | 隨附於作業系統的**功能**。 | 選擇性。 <br/><br/>供 Windows SharePoint Services 用戶端物件模型 (CSOM) 使用，這個模型是在安裝 BizTalk Server 時自動安裝。 | 
| Microsoft SharePoint  | <ul><li>SharePoint Services 2016</li><li>SharePoint Services 2013 SP1</li><li>SharePoint Services Online</li></ul>  | 選擇性。 <br/><br/>如果您想要接收或傳送來自 SharePoint Services 的訊息，則需要 SharePoint Services 電腦。 它可以安裝在 BizTalk Server 所在的同一部電腦上，但最好安裝在不同的電腦上。 |
| Microsoft Office  | <ul><li>Microsoft Office Excel 2016</li><li>Microsoft Office Excel 2013</li></ul>**請注意**：BizTalk Server 只支援 32 位元版本的 Office。  | 選擇性。 <br/><br/>商務活動監控 (BAM) 須有此項目，才能即時顯示商務處理序。 | 
| Microsoft .NET Framework  | <ul><li>.NET framework 4.7 (開頭為[CU2](https://support.microsoft.com/kb/4021095))</li><li>.NET Framework 4.6.*x* </li></ul>**請注意**： 在 Visual Studio 中建立的 BizTalk 專案需要 Visual Studio 建置 」 目標設為.NET Framework 版本。 | 所有由 BizTalk Server 管理的元件都需要這個項目。 | 
| Microsoft Visual Studio |Visual Studio 2015 | 選擇性。 <br/><br/>提供建置 BizTalk Server 應用程式的開發環境。 建議使用 Ultimate 版，但也支援 Premium 和 Professional 版本。 BizTalk Server 開發人員工具和 SDK 的必要項目。 |
| Microsoft Visual C++ 2013 可轉散發套件 | 需要 x86 和 x64 版本。 下載於[適用於 Visual Studio 2013 的 Visual C++ 可轉散發套件](https://support.microsoft.com/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package)。    | 必要。<br/><br/>在未安裝 Visual C++ 的電腦上，Microsoft Visual C++ 可轉散發套件會安裝執行以 Visual C++ 開發之應用程式所需的 Visual C++ 程式庫執行階段元件。<br/><br/>**注意**: <br/> 即使使用 Visual Studio 2015，2013 還是必要版本。|
| Microsoft SQL Server  | <ul><li>Microsoft SQL Server 2016</li><li>Microsoft SQL Server 2014 SP1</li></ul> | BizTalk Server 執行階段、EDI 和 BAM 的必要項目。 <br/><br/>為了達到最佳效能，Microsoft 建議您使用 Enterprise Edition 的 SQL Server。 若要充分運用 BizTalk Server SDK 或從 Visual Studio 部署 BizTalk Server 應用程式，請安裝 SQL Server 開發工具。 <br/><br/>其他考量： <ul><li>若要使用 SQL Server AlwaysOn 可用性群組 (AG)，請使用 SQL Server 2016 和更新版本。 只有 SQL Server 2016 AlwaysOn AG 才支援 MSDTC，而 BizTalk 需要 MSDTC。 </li><li>SQL Server Standard Edition 不支援 BAM 即時彙總 (RTA)。 若要使用 BAM RTA，請安裝 SQL Server Enterprise Edition。</li><li>不建議使用 SQL Server Express Edition。 Express Edition 不包含 BizTalk Server 所需的特定功能。</li><li>除了二進位定序之外，BizTalk Server 還支援所有區分大小寫和不區分大小寫的 SQL Server 定序。 不支援二進位定序。</li></ul> |  |
| SQL Server Database Mail  | 隨附於 SQL Server 的版本。 [設定 SQL Server Database Mail](https://msdn.microsoft.com/library/hh245116(v=sql.130).aspx)。| 選擇性。 <br/><br/>使用 BAM 警示時需要。 | 
| SQL XML | SQL XML 4.0 (含 Service Pack 1)。 [下載 SqlXml 4.0 Service Pack 1 (SP1)](https://www.microsoft.com/en-us/download/details.aspx?id=30403)。 | BizTalk Server 執行階段、系統管理工具和 BAM 的必要項目。 <br/><br/> SQLXML 可以為您的 SQL Server 資料庫啟用 XML 支援。 它可讓開發人員銜接 XML 和關聯式資料的缺口。 您可以建立現有關聯式資料的 XML 檢視，然後如同 XML 檔案一樣使用該檢視。 <br/><br/>**注意**: <br/>可轉散發封包檔會自動安裝這個檢視。 SQL XML 可能會有自己的軟體需求 (例如 `.NET Framework 3.5` 和 `.NET Framework 2.0`)，這些需求未包含在封包檔中。 如果 BizTalk Server 可以存取網際網路，則可能會自動安裝 SQL XML 軟體需求。 如果 BizTalk Server 不能存取網際網路，則會手動安裝 SQL XML 軟體需求。| 
| WinSCP | WinSCP 5.7.7 版。 [下載 WinSCP](http://winscp.net)。| 使用 SFTP 配接器時需要。 |
|LOB 和企業系統 | [支援的特定業務 (LOB) 和企業系統](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)列出支援的版本。 | 需要： 當 BizTalk Adapter Pack 中使用配接器。 <br/><br/> [BizTalk Adapter Pack](../adapters-and-accelerators/biztalk-adapter-pack.md)列出可用的系統的配接器。 |

## <a name="service-pack-and-cumulative-update-support"></a>Service Pack 與累積更新支援

BizTalk Server 支援所有的 Service Pack、累積更新、安全性更新和 Hot Fix 。 極力建議您安裝 Windows、SQL Server、Visual Studio 以及任何已安裝程式的最新更新。 Microsoft 產品的 Service Pack 支援比照該產品的標準支援。 請參閱 BizTalk Server、SQL Server、Visual Studio 以及其他 Microsoft 程式的[支援週期索引](http://go.microsoft.com/fwlink/p/?LinkID=151890)。

[Service Pack 和累計更新清單，以便讓 BizTalk Server](https://support.microsoft.com/help/2555976)

 ## <a name="next-step"></a>下一個步驟
 
 [設定和安裝必要元件](../install-and-config-guides/set-up-and-install-prerequisites-for-biztalk-server-2016.md)
