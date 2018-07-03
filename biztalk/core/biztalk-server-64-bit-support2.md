---
title: BizTalk Server 的 64 位元支援概觀 |Microsoft Docs
description: 以配接器、 處理程序、 BizTalk 管理、 BAM 工具、 組件、 協調流程，在 BizTalk Server 的 64 位元支援
ms.custom: ''
ms.date: 09/27/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52ae9037-a7af-48e4-b6a3-bff7600802de
caps.latest.revision: 42
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6bf9af93cfad3f495e56a3e1390006b2654f8571
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013783"
---
# <a name="biztalk-server-64-bit-support"></a>BizTalk Server 64 位元的支援
本主題會回答關於 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 64 位元支援的常見問題。  
  
## <a name="which-versions-of-64-bit-windows-are-supported"></a>支援哪些版本的 64 位元 Windows？  
 所有版本的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]支援 32 位元執行和原生的 64 位元執行受支援的作業系統上。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含 32 位元和 64 位元的組態選項。 
 
  [BizTalk Server 2016 的硬體和軟體需求](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)  
  
 [BizTalk Server 2013 和 2013 R2 的硬體和軟體需求](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md)  
  
## <a name="is-there-an-extra-cost-for-64-bit-support"></a>64 位元支援是否有額外的成本？  
 資料分割 64 位元支援是不額外收費。  
  
## <a name="is-itanium-based-hardware-supported"></a>是否支援 Itanium 硬體。  
 BizTalk 執行階段中，沒有。 對於 BizTalk 資料庫中，[是]。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要支援 AMD64 或 EM64T 的 CPU 硬體。 如此一來，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不支援 Itanium 型 64 位元 Cpu 上執行的 Windows。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 支援以 Itanium 為基礎執行[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 因此，Itanium 64 位元 CPU 支援所有的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫。  
  
## <a name="which-biztalk-server-processes-run-in-64-bit-mode"></a>哪些 BizTalk Server 處理序是以 64 位元模式執行？  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可執行檔案裝載在數個不同的伺服器執行階段內。 下表列出哪些 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 程序是在 64 位元模式下執行的。  
  
|處理|32 位元支援|64 位元支援|  
|-------------|---------------------|---------------------|  
|HTTP 配接器 (IIS)|是|Partial|  
|BizTalk 主控件執行個體|是|是|  
|企業 SSO|是|是|  
|BAM 入口網站 (IIS)|是|否|  
|[SQL Server]|是|是|  
  
##### <a name="http-based-adapters-iis"></a>HTTP 配接器 (IIS)  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 元件 (例如 HTTP 與 SOAP 配接器) 是在 Internet Information Services (IIS) 內裝載和執行。 在 IIS 32 位元模式下支援所有的配接器。 有些配接器支援在 64 位元 IIS 模式下執行。 如需 64 位元配接器的完整清單，請參考本主題稍後的配接器清單。  
  
##### <a name="biztalk-host-instances"></a>BizTalk 主控件執行個體  
 BizTalk 主控件是伺服器的本機群組，每個都稱為主控件執行個體。 每個主控件執行個體部署為以根據 BTSNTSvc.exe 的 NT 服務。 協調流程和內含式配接器會載入和主控件執行個體中執行。 主控件執行個體可以設定為使用在 32 位元或 64 位元模式中執行**僅限 32 位元**中的核取方塊選項**主控件屬性** 對話方塊中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
##### <a name="enterprise-sso"></a>企業 SSO  
 Microsoft 企業單一登入 (SSO) 是在專用 NT 服務中執行 (ENTSSO.exe)。 其在 32 位元的 [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)]中是原生 32 位元，在 64 位元的 [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 中是原生 64 位元。  
  
##### <a name="bam-portal-iis"></a>BAM 入口網站 (IIS)  
 商務活動監控 (BAM) 入口網站元件必須使用 32 位元 ASP.NET 3.5，在 IIS 中執行。 在 WOW 模式下，BAM 入口網站會以 64 位元硬體執行。 的 「 執行 BAM 入口網站，在 64 位元環境中的 」，請參閱[自訂 BAM 入口網站組態](../core/customizing-the-bam-portal-configuration.md)。  
  
##### <a name="sql-server"></a>[SQL Server]  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 透過可在 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的 32 位元與 64 位元版本之間互通的原生傳輸通訊協定，與 Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 通訊。 因此，32 位元與 64 位元的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可執行檔可和 32 位元或 64 位元版本的 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 通訊。 32 位元或 64 位元的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 支援所有 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 預存程序。  
  
## <a name="what-about-32-bit64-bit-support-in-non-server-processes"></a>非伺服器處理序對於 32 位元/64 位元的支援有哪些？  
 **Microsoft Visual Studio**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設計工具的可執行檔裝載在 32 位元[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]IDE。 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 支援使用 Microsoft 的 64 位元專案的開發[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]，其可以部署到[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
 **Microsoft Management Console (MMC)**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]只能當做 32 位元 Microsoft Management Console (MMC) 應用程式，即使在 64 位元上的系統管理主控台執行[!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)]。 「企業單一登入」同時支援 32 位元與 64 位元的 MMC。  
  
 **Internet Explorer**  
  
 BAM 用戶端需要安裝 32 位元的 Internet Explorer，並使用於 64 位元的 [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 中。  
  
## <a name="how-do-i-enable-native-64-bit-execution-of-orchestrations"></a>我如何啟用協調流程的原生 64 位元執行？  
 指派要有主控件執行個體中執行的協調流程**僅限 32 位元**未選取的屬性。 主控件執行個體必須在 Windows x64 電腦上執行。  
  
## <a name="can-i-build-net-assemblies-that-run-in-64-bit-orchestrations"></a>我是否可以建立在 64 位元協調流程中執行的 .NET 組件？  
 是的。 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 開發人員可以使用 [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] 與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來建立支援以 64 位元模式執行的組件。 這些組件可以使用協調流程來部署，並在為原生 64 位元執行所設定的主控件執行個體中執行。  
  
## <a name="will-net-framework-20-compiled-assemblies-jit-compile-properly-in-both-32-bit-and-64-bit"></a>將.NET Framework 2.0 編譯的組件 JIT 編譯在 32 位元和 64 位元中正常運作嗎？  
 是的。 如果已編譯組件[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]2.0 和**AnyCPU**旗標，單一 DLL 將會 JIT 編譯在 32 位元或 64 位元的 Clr 中正常運作。  
  
## <a name="can-i-install-both-32-bit-and-64-bit-components-in-a-single-biztalk-msi-package"></a>我是否可以在單一 BizTalk MSI 封裝中安裝 32 位元與 64 位元元件？  
 是的。 系統管理員可以從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式建立 MSI 封裝檔案。 MSI 檔案可包含 32 位元及 64 位元的 DLL 及 EXE (新增至 BizTalk 應用程式的 DLL 及 EXE)。 在 32 位元 Windows 上將安裝只有 32 位元 Dll 和 Exe。 在  [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] x64，32 位元和 64 位元會安裝的 Dll 及 Exe。  
  
## <a name="how-do-32-bit-biztalk-server-executables-run-on-windows-x64"></a>32 位元的 BizTalk Server 可執行檔如何在 Windows x64 中執行？  
 Windows x64 提供在相同電腦上執行 32 位元與 64 位元可執行檔的能力。 32 位元可執行檔會使用 WOW64 服務，來模擬 32 位元執行階段環境。  
  
## <a name="will-32-bit-biztalk-server-executables-have-4gb-of-addressable-process-memory-on-windows-x64"></a>32 位元的 BizTalk Server 可執行檔在 Windows x64 上是否具有 4 GB 的可定址程序記憶體？  
 是的。 在 [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] x64 中，32 位元的 BTSNTSVC 及 IIS 程序是在 WOW64 底下執行，並且可利用完整的 4GB 虛擬記憶體。 對於 32 位元的 Windows 預設的 2GB 可定址虛擬記憶體而言，這是一項改良。  
  
 您可以設定記憶體節流閾值百分比 （%），或是用絕對值。 例如：  
  
-   如果您使用百分之可用 (0-100)，您所輸入的值就會是 2048 MB 的百分比表示。  
  
-   如果您使用絕對值，則您所輸入的值可以是任何以 mb 為單位的值為 4096 MB （32 位元的限制）。 在 64 位元主控件，您可以指定較高的值上限為 2 TB 理論上的 64 位元位址。  
  
## <a name="which-adapters-are-capable-of-running-in-64-bit-mode"></a>哪些配接器可以在 64 位元模式下執行？  
 依照預設，所有的配接器都可以在 32 位元 [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 與 64 位元 [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 的 WOW64 上，以 32 位元模式執行。 下列配接器可以在原生 64 位元模式下執行 (做為主控件程序，在 IIS 或 BTSNTSVC 上執行)：  
  
-   檔案  
  
-   HTTP  
  
-   MSMQ  
  
-   MQSeries  
  
-   SFTP  
  
-   SMTP  
  
-   SOAP  
  
-   WCF  
  
> [!NOTE]
>  在 32 位元與 64 位元程序中均支援 MQSeries 配接器。 此配接器具有可在 Windows 上執行 IBM WebSphere MQ Server 的 MQSeries 代理程式。 [準備您的電腦安裝](../install-and-config-guides/prepare-your-computer-for-installation.md)列出 MQ 需求。  
> 
> [!NOTE]
>  如果您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式連線到 Windows Server 2003 的電腦 （例如 SSO、 SQL 配接器、 MQSeries、 MQSAgent、 Oracle 等等），然後安裝[934016](http://support.microsoft.com/kb/934016)並[934849](http://support.microsoft.com/kb/934849)這些 Windows Server 上2003 伺服器。  
> 
> [!NOTE]
>  不支援在 64 位元主控件執行個體上執行 FTP 配接器、POP3 配接器及 MIME 解碼器。  
  
## <a name="are-persisted-biztalk-orchestrations-dependent-on-32-bit-or-64-bit-runtimes"></a>保存的 BizTalk 協調流程會與 32 位元或 64 位元執行階段相依嗎？  
 資料分割 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 保存執行階段元件使用的 32 位元或 64 位元執行階段無關的格式。 這包括協調流程、訊息，以及連接埠。 此保存模式允許系統管理員在 32 位元與 64 位元之間切換主控件組態，而不會造成 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料的不相容。  
  
## <a name="when-i-upgrade-to-biztalk-server-will-my-biztalk-hosts-run-as-64-bit-by-default"></a>當我升級至 BizTalk Server 時，將我的 BizTalk 主控件為 64 位元預設執行？  
 資料分割 根據預設，升級至 BizTalk Server 將只標示為 32 位元的所有 BizTalk 主控件執行個體。 系統管理員必須在 Windows x64 電腦上建立新主控件執行個體，並設定應用程式以使用它們。  
  
## <a name="can-i-have-a-mixed-biztalk-server-group-that-includes-both-32-bit-and-64-bit-biztalk-runtimes"></a>我可以擁有同時包含 32 位元和 64 位元 BizTalk 執行階段的「混合式」BizTalk Server 群組嗎？  
 是的。  
  
## <a name="what-languages-are-supported-on-64-bit-runtimes"></a>在 64 位元執行階段上支援哪些語言？  
 在 32 位元與 64 位元執行階段上支援所有支援的語言。  
  
## <a name="what-64-bit-sql-server-components-are-required-to-configure-bam-tools"></a>需要哪些 64 位元 SQL Server 元件才能設定 BAM 工具？  
 組態精靈是一個 32 位元的處理序，因此需要某些元件才能與 64 位元的 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 通訊。 您必須安裝下列 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 用戶端元件才能啟用 BAM 工具的組態：  
  
-   連接元件  
  
-   管理工具  
  
-   傳統元件  
  
## <a name="see-also"></a>另請參閱  
 [效能和容量規劃](../core/performance-and-capacity-planning.md)
