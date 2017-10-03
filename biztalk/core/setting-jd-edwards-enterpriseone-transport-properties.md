---
title: "設定 JD Edwards EnterpriseOne 傳輸屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Max Concurrent Calls parameter
- JD Edwards EnterpriseOne adapters, transport properties
- transport properties, configuring [JD Edwards EnterpriseOne adapters]
- adapters [JD Edwards EnterpriseOne adapters], transport properties
- Bootstrap Data Source properties
ms.assetid: 7d258ee6-1cb3-4b88-ac41-49e639833574
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ed3118230f2e4ae48676b297ac444da9c392221
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="setting-jd-edwards-enterpriseone-transport-properties"></a>設定 JD Edwards EnterpriseOne 傳輸屬性
JD Edwards EnterpriseOne 傳輸屬性是用於設計與執行階段。 在**傳輸屬性**對話方塊中，您設定的連接和認證參數特定伺服器系統和您嘗試存取的物件。  
  
 設定連線參數之後，您可以在「配接器精靈」中瀏覽 JD Edwards EnterpriseOne 系統表格、檢視和程序。  
  
 進行 JD Edwards EnterpriseOne 連線時，參數會傳遞至連線物件 (使用者、密碼、環境)。 該物件則會傳回 JD Edwards EnterpriseOne 應用程式商務功能的執行個體。 認證會進一步以企業/應用程式伺服器的名稱以及定義的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接聽的 TCP/IP 連接埠來定義。  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中已設定企業伺服器名稱與連接埠的預設值。 它們也會從稱為 jdeinterop.ini 的檔案中讀取。 如果您收到登入錯誤，請仔細檢查認證與值。  
  
### <a name="to-specify-transport-properties"></a>若要指定傳輸屬性  
  
1.  在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。  
  
2.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
3.  在**傳送埠屬性**對話方塊中，按一下內部**名稱**方塊並輸入此連接埠的名稱 (例如， `JDEEnterpriseOneSend`)。  
  
4.  在下**一般**，請在**傳輸類型**方塊中，選取**JDE EnterpriseOne**下拉式清單中。  
  
5.  在**位址 (URI)**屬性中，按一下省略符號 (**...**).  
  
     **JDE EnterpriseOne 傳輸屬性** 對話方塊隨即出現。  
  
     ![](../core/media/jdeenterprise-trans.gif "JDEEnterprise_Trans")  
  
6.  在**JDE EnterpriseOne 傳輸屬性**對話方塊方塊中，展開 **配接器必要屬性**，並輸入 JD Edwards EnterpriseOne 伺服器連線的所有必要的資訊。  
  
     使用下列指導方針設定傳輸屬性：  
  
    |使用|完成|  
    |--------------|----------------|  
    |**配接器必要屬性**||  
    |Host|輸入主控件伺服器電腦的名稱 (例如：<br /><br /> `actsvr1`)<br /><br /> -或-<br /><br /> 輸入電腦的 IP 位址 (例如，<br /><br /> `123.456.0.789`)|  
    |JAVA_HOME|輸入 JDK 安裝的完整路徑 (例如，<br /><br /> `C:\jdk1sdk1.4.2_07`)|  
    |JDEdwards 環境|在 JD Edwards EnterpriseOne 中輸入環境的名稱 (例如， `DV7333`)。<br /><br /> DV7333 是開發環境的一般名稱，PY7333 常見於原型環境，PD7333 常見於實際執行環境。|  
    |JDEdwards JAR 檔案|輸入每個 JAR 檔案的完整路徑與檔案名稱：<br /><br /> -C:\JDEOWJars\Connector.jar<br />-C:\JDEOWJars\Kernel.jar<br />-Program Files\Microsoft BizTalk Adapters for Enterprise applications\j.d.edwards。 Edwards EnterpriseOne(r)\Classes\JDEDynAccess.jar<br /><br /> 每個 jar 檔案都必須以不加空格的分號 (;) 分隔 (例如，<br /><br /> `<c:>\Connector.jar;<c:>\Kernel.jar;`)|  
    |密碼|輸入使用者密碼。 如果不使用單一登入 (SSO)，您必須為 BizTalk Adapter for JD Edwards EnterpriseOne 設定認證參數以存取伺服器系統。 此密碼會對應於使用者名稱，其決定了您在存取資料庫時可享有的權限。|  
    |通訊埠|輸入的數字識別碼的傳送或接收埠 (例如， `6009`)。|  
    |使用者名稱|輸入使用者名稱，然後按一下**確定**。|  
    |**啟動程序的資料來源必要的屬性\*\***||  
    |資料來源名稱|輸入資料來源的名稱。 此名稱對所有資料類型而言是必要的。|  
    |資料庫擁有者|輸入資料庫擁有者的名稱。|  
    |資料庫伺服器名稱|輸入資料庫伺服器的名稱。|  
    |資料庫伺服器連接埠|輸入識別資料庫伺服器連接埠的數字。|  
    |資料庫類型|輸入單一字元以代表資料庫類型。 例如：<br /><br /> **我**-iSeries<br /><br /> **O** -Oracle<br /><br /> **S** -SQL Server<br /><br /> **L** -SQL Server OLEDB<br /><br /> **W** -UDB|  
    |實體資料庫名稱|輸入實體資料庫名稱。 所有資料類型都需要有此名稱。|  
    |**並行控制**||  
    |同時呼叫數目上限|輸入的數值**同時呼叫數目上限**。 這個數字代表同時呼叫數目上限，例如`10`。<br /><br /> 此欄位的預設值是 5。|  
    |**重新整理代理程式**||  
    |重新整理代理程式|選取**是**如**重新整理代理程式**強制 runtimeagent.exe 和 browsingagent.exe 程序在必要時自動重新啟動。<br /><br /> 例如，您希望處理程序在與伺服器中斷連線時自動重新啟動，或是您在伺服器加上其他項目，但是該項目並未出現在 Microsoft 配接器精靈的選項中。|  
    |**安全性伺服器**||  
    |安全性伺服器名稱|輸入安全性伺服器的名稱。 此欄位是選用的，且預設為 JD Edwards 伺服器主機。|  
    |服務名稱連接|輸入安全性伺服器和物件組態對應 (OCM) 使用的連接埠號碼。 預設值為 JD Edwards 伺服器連接埠。|  
    |**單一登入**||  
    |分支機構應用程式|只有在您要使用 SSO 時，才從下拉式清單選取分支機構應用程式。|  
    |使用 SSO|選取**是**如果您使用 SSO; 密碼就不需要在此情況下。|  
  
7.  按一下**確定**以接受所有屬性。  
  
## <a name="bootstrap-data-source-required-properties"></a>開機資料來源必要屬性  
 [開機] 區段是在登入時期使用，以提供對系統資料表的存取。 [開機資料來源] 資訊會定義 OCM 所在的資料來源。  
  
 並非所有平台都需要設定所有 [開機資料來源] 參數。 如果您使用的不常見的資料庫，您可能必須更新的 [JDBJ-JDBC DRIVERS] 區段**jdeinterop.ini**宣告 JDBC 驅動程式。 下列清單識別各平台的必要設定：  
  
-   **iSeries**。 資料來源名稱、資料庫類型、資料庫伺服器名稱、實體資料庫名稱  
  
-   **Oracle**。 資料來源名稱、資料庫類型、實體資料庫名稱、資料庫擁有者  
  
-   **SQL Server**。 資料來源名稱、資料庫類型、資料庫伺服器名稱、資料庫伺服器連接埠、實體資料庫名稱、資料庫擁有者  
  
-   **SQL Server OLEDB**。 資料來源名稱、資料庫類型、資料庫伺服器名稱、資料庫伺服器連接埠、實體資料庫名稱、資料庫擁有者  
  
-   **UDB**。 資料來源名稱、資料庫類型、實體資料庫名稱、資料庫擁有者  
  
## <a name="optimization-configuration"></a>最佳化組態  
 下列資訊可協助您最佳化 BizTalk Adapter for JD Edwards EnterpriseOne 的組態。  
  
### <a name="max-concurrent-calls-parameter"></a>同時呼叫數目上限參數  
 您可以在輸送量超過後端處理能力的情況下使用 `Max Concurrent Calls` 參數。 您將參數新增到中的配接器**傳送埠傳輸屬性**頁面，即可啟動訊息多載保護。 預設值為 -1，表示呼叫沒有上限。  
  
 當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提交訊息給傳輸配接器時，它會先從配接器取得批次，然後在該批次上叫用 `TransmitMessage()` 來傳輸每個訊息。 完成傳輸時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會在批次上叫用 `Done()`，這時配接器就會開始將訊息傳輸至後端。  
  
 如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在叫用 `Done` 之前會取得多個批次，`Done` 命令可能就永遠不會發生。 藉由設定批次中的訊息數目上限，您便可以控制送到後端的訊息。  
  
 參數變更才會在一分鐘內生效。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]必須擷取 SQL 資料庫中儲存的配接器組態的變更。  
  
### <a name="refresh-agent"></a>重新整理代理程式  
 當您選取**是**如**重新整理代理程式**，您可以強制 runtimeagent.exe 和 browsingagent.exe 程序在必要時自動重新啟動。  
  
 例如，您希望程序在失去伺服器連線時自動重新啟動，或是您在伺服器加上其他項目，但是該項目並未出現在 Microsoft 配接器精靈的選項中。  
  
 [重新整理代理程式] 參數是在 [傳輸屬性] 視窗中設定，並會重新整理瀏覽與執行階段代理程式。 runtimeagent.exe 會在一分鐘之後或在下一次呼叫 Send 時才重新整理。  
  
> [!NOTE]
>  browsingagent.exe 要等到您終止目前的瀏覽工作階段才會重新整理。 例如，您必須結束 「 新增產生的項目...」 瀏覽工作階段，然後重新輸入重新整理 browsingagent.exe。  
  
### <a name="single-sign-on"></a>單一登入 (SSO)  
 有兩種方法可用來存取 JD Edwards EnterpriseOne 系統。 您可以使用登入認證 ([傳輸屬性] 的 [登入] 參數) 或單一登入 (SSO)。 選取**是**中**使用 SSO**欄位，以使用單一登入。  
  
 如需詳細資訊和基本指示，設定單一登入的設定，請參閱[使用單一登入](../core/using-single-sign-on1.md)。  
  
 您也必須從下拉式清單中選取分支機構應用程式。 由企業單一登入工具所建立的分支機構應用程式，代表像是 JD Edwards EnterpriseOne 的應用程式。 BizTalk Adapter for JD Edwards EnterpriseOne 會使用應用程式使用者的認證。  
  
 這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 資料庫中擷取所得。 這些認證就是啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案之使用者 (應用程式使用者) 的認證。  
  
 如需如何建立分支機構應用程式的詳細資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications4.md)。 您也可以參閱 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 線上說明。  
  
## <a name="see-also"></a>另請參閱  
 [單一登入與 BizTalk Adapter for JD Edwards EnterpriseOne](../core/single-sign-on-and-biztalk-adapter-for-jd-edwards-enterpriseone.md)   
 [建立 JD Edwards EnterpriseOne 傳送處理常式](../core/creating-jd-edwards-enterpriseone-send-handlers.md)