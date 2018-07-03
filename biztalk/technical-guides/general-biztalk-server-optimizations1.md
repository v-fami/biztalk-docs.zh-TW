---
title: 一般 BizTalk Server Optimizations1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8032553-bae3-440d-9197-b926160b0bdf
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2605a7acd9610b0b5417e8c5d7c875f67f22f30c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006711"
---
# <a name="general-biztalk-server-optimizations"></a>一般 BizTalk Server 最佳化
下列建議可用來增加 BizTalk Server 效能。 安裝和設定 BizTalk Server 之後，會套用此主題中所列的最佳化。  
  
## <a name="configure-msdtc"></a>設定 MSDTC  
 若要加速 SQL Server 與 BizTalk Server 之間的交易，您必須啟用 Microsoft Distributed Transaction Coordinator (MS DTC)。 若要在 BizTalk Server 上設定 MSDTC，請參閱主題[改善作業系統效能的一般指導方針](../technical-guides/general-guidelines-for-improving-operating-system-performance.md)。  
  
## <a name="recommendations-for-configuring-biztalk-server-hosts"></a>設定 BizTalk Server 主控件的建議  
 本節提供設定 BizTalk Server 主控件的建議。  
  
### <a name="create-multiple-biztalk-server-hosts-and-separate-host-instances-by-functionality"></a>依功能建立多個 BizTalk Server 主控件和個別的主控件執行個體  
 請遵循下列指導方針來建立多個 BizTalk Server 主控件，並跨這些主機配置的工作負載：  
  
-   建立個別的主控件來傳送、 接收、 處理及追蹤功能。 建立多個 BizTalk 主控件提供的彈性設定 BizTalk 群組中的工作負載時，將處理分散到 BizTalk 群組中執行 BizTalk Server 之電腦的主要方法。 使用多部主機，可讓您停止一部主機，而不會影響其他主機。 比方說，您可能要停止傳送訊息，讓他們佇列 MessageBox 資料庫中同時仍允許接收配接器不同的主控件執行個體中執行以接收輸入的訊息。 主控件執行個體分隔功能時，也會提供下列優點：  
  
    -   執行多個 BizTalk 主控件可減少 MessageBox 資料庫主應用程式佇列資料表上的競爭，因為每一部主機指派其本身在 MessageBox 資料庫中的工作佇列資料表。  
  
    -   節流是在 BizTalk Server 中實作主機層級。 這可讓您設定每個主控件節流特性不同。  
  
    -   安全性被實作在主機層級;每個主控件是離散的 Windows 身分識別下執行。 這可讓您，比方說，為 Host_A 存取 FileShare_B，同時不允許任何其他主機存取檔案共用。  
  
-   每個主控件執行個體有自己的資源，例如記憶體、 控制代碼，以及執行緒集.NET 執行緒集區中。 配置到主機的工作負載時請考慮將資源一起調整，放在相同的主控件。  
  
-   個別的配接器和協調流程中不同的主控件具有不同優先順序的資源。 這項技術可容納在專用的 BizTalk Server 電腦上執行高優先順序應用程式主機的放置。  
  
> [!NOTE]  
>  權益，以建立其他主控件執行個體時，也有缺點如果建立太多的主控件執行個體。 每個主控件執行個體是 Windows 服務 (BTSNTSvc.exe)，這會產生額外的負載，對 MessageBox 資料庫，並使用電腦資源 （例如 CPU、 記憶體、 執行緒）。  
  
 如需有關修改 BizTalk Server 主機的內容，請參閱 <<c0> [ 如何修改主機內容](http://go.microsoft.com/fwlink/?LinkID=154359)(http://go.microsoft.com/fwlink/?LinkID=154359) BizTalk Server 2010 說明中。  
  
### <a name="configure-a-dedicated-tracking-host"></a>設定專用的追蹤主控件  
 BizTalk Server 已針對輸送量最佳化的因此主要的協調流程和傳訊引擎執行不實際訊息直接移至 BizTalk 追蹤 」 或 「 BAM 資料庫，因為這會將轉向這些引擎從執行商務程序的主要工作。 相反地，BizTalk Server 會將訊息保留在 MessageBox 資料庫，並將其標示為需要移至 「 BizTalk 追蹤資料庫。 背景處理序 （追蹤主控件），然後移動訊息至 「 BizTalk 追蹤 」 及 「 BAM 資料庫。 追蹤是需要大量資源的作業，因為個別的主控件應建立專門用來追蹤，所以可以盡可能降低追蹤對專用的主機，與訊息處理的影響。 為了達到最佳效能，應該有至少一個追蹤主控件執行個體，每個 MessageBox 資料庫。 追蹤主控件執行個體的實際數目應該是 N + 1，其中 N = MessageBox 資料庫數目。 "+ 1"為備援，萬一其中一部電腦裝載追蹤失敗。  
  
 使用專用的追蹤主控件也可讓您停止其他 BizTalk 主控件，而不會干擾 BizTalk Server 追蹤。 追蹤從 MessageBox 資料庫的資料移動是狀況良好的 BizTalk Server 系統的關鍵。 如果停止 BizTalk 主控件，負責移動 BizTalk 群組中的追蹤資料，將不會執行追蹤資料解碼服務。 影響如下所示：  
  
- HAT 追蹤資料會從 MessageBox 資料庫移動到 BizTalk 追蹤資料庫。  
  
- BAM 追蹤資料會從 MessageBox 資料庫移動至 BAM 主要匯入資料庫。  
  
- 資料不會移動，因為它無法從 MessageBox 資料庫刪除。  
  
- 追蹤資料解碼服務停止時，追蹤攔截器將仍會引發，並追蹤資料寫入 MessageBox 資料庫。 如果不移動資料，這會導致 MessageBox 資料庫變得過大，這樣會影響一段時間的效能。 即使自訂屬性不會受到追蹤，或是未設定 BAM 設定檔，預設情況下一些會追蹤資料 （例如管線接收 / 傳送事件和協調流程事件）。 如果您不要執行追蹤資料解碼服務，請關閉所有的追蹤，以便任何攔截器會將資料儲存至資料庫。 若要停用全域追蹤，請參閱[如何關閉全域追蹤](http://go.microsoft.com/fwlink/?LinkID=154193)(http://go.microsoft.com/fwlink/?LinkID=154193) BizTalk Server 2010 說明中。 您可以使用 BizTalk Server 管理主控台來選擇性地停用追蹤事件。  
  
  追蹤主控件應至少兩個 （適用於在其中一個失敗的情況下的備援） 執行 BizTalk Server 的電腦上執行。 為了達到最佳效能，您應該有至少一個追蹤主控件執行個體，每個 MessageBox 資料庫。 追蹤主控件執行個體的實際數目應為 （N + 1），其中 N = MessageBox 資料庫數目。 "+ 1"為備援，萬一其中一部電腦裝載追蹤失敗。  
  
  追蹤主控件執行個體移動特定的 MessageBox 資料庫的追蹤資料，但是會永遠不會有一個以上的追蹤主控件執行個體特定的 MessageBox 資料庫移動資料。 例如，如果您有三個 MessageBox 資料庫，以及追蹤主控件執行個體的唯一兩個，然後其中一個主控件執行個體必須為兩個 MessageBox 資料庫移動資料。 新增第三個追蹤主控件執行個體分散追蹤裝載執行 BizTalk Server 的另一部電腦的工作。 在此案例中，加入第四個追蹤主控件執行個體不會發佈任何詳細的追蹤主控件運作，但會提供額外的追蹤主控件執行個體的容錯功能。  
  
  如需有關 BAM 事件匯流排服務的詳細資訊，請參閱 BizTalk Server 2010 說明中的下列主題：  
  
- [管理 BAM 事件匯流排服務](http://go.microsoft.com/fwlink/?LinkID=154194)(http://go.microsoft.com/fwlink/?LinkID=154194)。  
  
- [建立 BAM 事件匯流排服務的執行個體](http://go.microsoft.com/fwlink/?LinkID=154195)(http://go.microsoft.com/fwlink/?LinkID=154195)。  
  
### <a name="do-not-cluster-biztalk-hosts-unless-absolutely-necessary"></a>除非未叢集化 BizTalk 主控件絕對必要  
 BizTalk Server 2010 可讓您將 BizTalk 主控件設定為叢集資源，您應該只考慮這麼做，如果您要提供高可用性，無法裝載在多部 BizTalk 電腦資源。 例如，使用 FTP 配接器的連接埠應該僅位於一個主控件執行個體，，因為 FTP 通訊協定不提供檔案鎖定。 不過，這會引進單一失敗點，會受益於叢集。 包含配接器，例如檔案、 SQL、 HTTP 或處理僅主機的主機可以在內部負載平衡的電腦，並不會受益於叢集。  
  
## <a name="increase-the-number-of--http-concurrent-connections-allowed-by-changing-the-value-for-the-maxconnection-parameter"></a>增加 HTTP 變更 maxconnection 參數的值允許的並行連線的數目  
 根據預設，HTTP 配接器 （包括以 WCF 為基礎的 HTTP 配接器） 會開啟只有兩個的並行 HTTP 連線至任何特定的目的地伺服器執行 BizTalk Server 的每一部電腦。  
  
 此設定符合 HTTP 1.1 規格，IETF RFC，雖然很適合使用者的案例，但它不適合用於高輸送量。 設定有效節流，每一部伺服器的輸出 HTTP 呼叫以兩個並行傳送從每部執行 BizTalk Server 的電腦。  
  
 若要增加並行連線數目，您可以修改 BizTalk Server 組態檔，BTSNTSvc.exe.config （或 BTSNTSvc64.exe.config 64 位元主機），每個 BizTalk Server 中的 maxconnection 參數的值。 您可以增加此呼叫的特定伺服器。 根據經驗法則，maxconnection 參數的值應該設定為 12 * 的 Cpu 或裝載的 web 應用程式的電腦上的核心數目。  
  
> [!NOTE]  
>  請勿增加這類較大的值，所呼叫的 Web 伺服器已無法應付 HTTP 連線的 maxconnection 參數的值。 在之後變更 maxconnection 參數的值，來執行壓力測試將要求傳送到每個目的地 Web 伺服器，以判斷會提供良好的效能和 HTTP 的 maxconnection 值傳送，而不勝任負荷目標網站伺服器。  
  
 下列是連線上限屬性的組態範例。  
  
```  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="24" />  
      <add address="*" maxconnection="48" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
 設定 maxconnection 屬性時，可以指定 HTTP、 HTTPS、 網站 IP 位址和連接埠號碼。 其他範例包括：  
  
 **\<新增地址 ="<https://www.contoso.com>"maxconnection ="24"/\>**   
**\<新增地址 ="<http://www.contoso.com:8080>"maxconnection ="24"/\>**   
**\<新增地址 ="http://*IPAddress*"maxconnection = 「 24 」 /\>** 如需調整 IIS 和 ASP.NET Web 服務設定的詳細資訊，請參閱可能會影響 HTTP 配接器 ASP.NET 設定效能 > 一節[組態參數，會影響配接器效能](http://go.microsoft.com/fwlink/?LinkID=154200)(<http://go.microsoft.com/fwlink/?LinkID=154200>) BizTalk Server 2010 說明中。  
  
## <a name="manage-aspnet-thread-usage-or-concurrently-executing-requests-for-web-applications-that-can-host--isolated-received-locations-back-end-web-services-and-wcf-services"></a>管理 ASP.NET 執行緒用法，或同時執行可裝載的 Web 應用程式要求外掛式接收的位置、 後端 Web 服務和 WCF 服務  
 背景工作和 I/O 執行緒 （IIS 7.5 和傳統模式中的 IIS 7.0） 或同時執行的要求 （IIS 7.5 和 7.0 整合的模式） 的 ASP.NET Web 應用程式主機外掛式接收的位置、 後端 Web 服務和 WCF 服務的數字的數目應該在下列情況下修改：  
  
-   CPU 使用率不是在裝載的 Web 伺服器上的瓶頸。  
  
-   值：  
  
    -   **ASP.NET 應用程式 v4.0.30319 \Request Wait Time**或是**ASP.NET 應用程式執行時間的 v4.0.30319 \Request**效能計數器是超乎尋常地高。  
  
    -   **ASP.NET 應用程式 v2.0.50727\Request Wait Time**或是**ASP.NET 應用程式 v2.0.50727\Request 執行時間**效能計數器是超乎尋常地高。  
  
-   裝載的 Web 應用程式之電腦的應用程式記錄檔中，會產生類似下面的錯誤。  
  
    ```  
    Event Type: Warning  
    Event Source: W3SVC Event Category: None  
    Event ID: 1013  
    Date: 11/4/2010  
    Time: 1:03:47 PM  
    User: N/A  
    Computer: <ComputerName>  
    Description: A process serving application pool 'DefaultAppPool' exceeded time limits during shut down. The process id was '<xxxx>'  
    ```  
  
### <a name="manage-aspnet-thread-usage-for-web-applications-that-can-host-isolated-received-locations-back-end-web-services-and-wcf-services-on-iis-75-and-iis-70-running-in-classic-mode"></a>管理 ASP.NET 執行緒用法的外掛式接收的位置、 後端 Web 服務和 IIS 7.5 和 IIS 7.0 以傳統模式執行的 WCF 服務可以裝載的 Web 應用程式  
 當**autoConfig**在傳統模式中執行 IIS 7.5 和 IIS 7.0 伺服器的 machine.config 檔案中的值設定為 **，則為 true**，ASP.NET 2.0 和 ASP.NET 4 管理背景工作執行緒和 I/O 執行緒的數目會配置到任何相關聯的 IIS 工作者處理序。  
  
```  
<processModel autoConfig="true" />  
```  
  
 若要以手動方式修改的背景工作角色和 ASP.NET 2.0 和 ASP.Net 4 Web 應用程式的 I/O 執行緒數目，開啟相關聯的 machine.config 檔案，然後輸入新的值**maxWorkerThreads**和**maxIoThreads**參數。  
  
```  
<!-- <processModel autoConfig="true" /> -->  
    <processModel maxWorkerThreads="200" maxIoThreads="200" />  
```  
  
> [!NOTE]  
>  這些值是指導方針請確定您測試變更這些參數。  
  
 如需有關調整的 ASP.NET 2.0 Web 應用程式的 machine.config 檔案中參數的詳細資訊，請參閱 Microsoft 知識庫文章 821268[爭用、 效能不佳和死結，當您從 ASP Web 服務要求。NET 應用程式](http://go.microsoft.com/fwlink/?LinkID=144169)(http://go.microsoft.com/fwlink/?LinkID=144169)。  
  
### <a name="manage-the-number-of-concurrently-executing-requests-for-aspnet-20-web-applications-that-can-host-isolated-received-locations-back-end-web-services-and-wcf-services-on-iis-75-and-iis-70-running-in-integrated-mode"></a>管理同時執行的外掛式接收的位置、 後端 Web 服務和 IIS 7.5 和 IIS 7.0 整合模式中執行的 WCF 服務可以裝載的 ASP.NET 2.0 Web 應用程式的要求的數目  
 當 IIS 7.5 和 IIS 7.0 上裝載 ASP.NET 2.0 整合模式中時，使用的執行緒的處理方式與在 IIS 7.5 和 IIS 7.0 上以傳統模式。 當 IIS 7.5 和 IIS 7.0 上裝載 ASP.NET 2.0 整合模式中時，ASP.NET 2.0 會限制同時執行的數字**要求**而不是數目**執行緒**並行執行要求。 同步的情況下這會間接限制的執行緒數目，但針對非同步案例要求和執行緒的數目可能會非常不同。 IIS 7.5 和 IIS 7.0 上執行 ASP.NET 2.0，在整合式模式中，當**maxWorkerThreads**並**maxIoThreads** machine.config 檔案中的參數不會用來管理執行中執行緒的數目。 藉由修改指定的值，相反地，可以從 12 每一 CPU 的預設值已變更並行執行要求的數目**maxConcurrentRequestsPerCPU**。 **MaxConcurrentRequestsPerCPU** reqistry 或 aspnet.config 檔案的組態區段中，可以指定值。 請遵循下列步驟變更的預設值**maxConcurrentRequestsPerCPU**控管的並行執行的要求數目：  
  
 **若要在登錄中設定 maxConcurrentRequestsPerCPU 值**  
  
> [!WARNING]  
>  不當使用登錄編輯，可能會造成問題，需要重新安裝作業系統。 您必須自行負擔使用「登錄編輯程式」的風險。 如需如何備份、 還原和修改登錄的詳細資訊，請參閱 Microsoft 知識庫文章 256986[進階使用者的 Windows 登錄資訊](http://go.microsoft.com/fwlink/?LinkId=62729)(http://go.microsoft.com/fwlink/?LinkId=62729)。  
  
> [!NOTE]  
>  這項設定是全域的而且無法變更為個別的應用程式集區或應用程式。  
  
1. 按一下 **[開始]**、按一下 **[執行]**、輸入 **regedit.exe**，然後按一下 **[確定]** 以啟動「登錄編輯程式」。  
  
2. 瀏覽至**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0**  
  
3. 依照下列步驟中建立機碼：  
  
   1.  在上**編輯**功能表上，按一下**新增**，然後按一下 **金鑰**。  
  
   2.  型別**maxConcurrentRequestsPerCPU**，然後按**ENTER**。  
  
   3.  底下**maxConcurrentRequestsPerCPU**機碼，請建立 DWORD 項目與 maxConcurrentRequestsPerCPU 的新值。  
  
   4.  關閉 [登錄編輯程式]。  
  
   **若要設定的 aspnet.config 檔案的組態區段中的應用程式集區 maxConcurrentRequestsPerCPU 值**  
  
> [!NOTE]  
>  必須安裝 Microsoft.NET Framework 3.5 Service Pack 1，以容納透過組態檔設定下列值。 您可以下載 Microsoft.NET Framework 3.5 Service Pack 1 從[Microsoft.NET Framework 3.5 Service Pack 1](http://go.microsoft.com/fwlink/?LinkID=136345) (http://go.microsoft.com/fwlink/?LinkID=136345)。  
  
 開啟應用程式集區的 aspnet.config 檔案，然後輸入新的值**maxConcurrentRequestsPerCPU**並**requestQueueLimit**參數。  
  
```  
<system.web>  
    <applicationPool maxConcurrentRequestsPerCPU="12" requestQueueLimit="5000"/>  
</system.web>  
```  
  
> [!NOTE]  
>  這個值會覆寫指定的值**maxConcurrentRequestsPerCPU**在登錄中。 RequestQueueLimit 設定等同於 processModel/requestQueueLimit，不同之處在於 aspnet.config 檔中的設定會覆寫 machine.config 檔案中的設定。  
  
 如需有關如何在 IIS 7.0 上設定 ASP.NET 執行緒用法的詳細資訊，請參閱[Thomas Marquardt 部落格上的 IIS 7.0 上的 ASP.NET 執行緒用法](http://go.microsoft.com/fwlink/?LinkId=157518)(http://go.microsoft.com/fwlink/?LinkId=157518)。  
  
### <a name="manage-the-number-of-concurrently-executing-requests-for-aspnet-4web-applications-that-can-host-isolated-received-locations-back-end-web-services-and-wcf-services-on-iis-75-and-70-running-in-integrated-mode"></a>管理同時執行的外掛式接收的位置、 後端 Web 服務和 IIS 7.5 和 7.0 整合模式中執行的 WCF 服務可以裝載 ASP.NET 4Web 應用程式的要求的數目  
 使用.NET Framework 4，maxConcurrentRequestsPerCPU 的預設值為 5000，這是一個非常大的數字，因此將允許足夠的同時執行的非同步要求。 如需詳細資訊，請參閱 < [ \<applicationPool\>項目 （Web 設定）](http://go.microsoft.com/fwlink/?LinkID=205339) (http://go.microsoft.com/fwlink/?LinkID=205339)。  
  
 IIS 7.5 和 IIS 7.0 整合模式中，名為 MaxConcurrentRequestsPerCPU 內 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\4.0.30319.0 DWORD 會判斷每一 CPU 的並行要求數目。 根據預設值，登錄機碼不存在，因此每一 CPU 的要求數目限制為 5000。  
  
 **若要在登錄中設定 maxConcurrentRequestsPerCPU 值**  
  
> [!WARNING]  
>  不當使用登錄編輯，可能會造成問題，需要重新安裝作業系統。 您必須自行負擔使用「登錄編輯程式」的風險。 如需如何備份、 還原和修改登錄的詳細資訊，請參閱 Microsoft 知識庫文章 256986[進階使用者的 Windows 登錄資訊](http://go.microsoft.com/fwlink/?LinkId=62729)(http://go.microsoft.com/fwlink/?LinkId=62729)。  
  
> [!NOTE]  
>  這項設定是全域的而且無法變更為個別的應用程式集區或應用程式。  
  
1. 按一下 **[開始]**、按一下 **[執行]**、輸入 **regedit.exe**，然後按一下 **[確定]** 以啟動「登錄編輯程式」。  
  
2. 瀏覽至**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\4.0.30319.0**。  
  
3. 依照下列步驟中建立機碼：  
  
   1.  在上**編輯**功能表上，按一下**新增**，然後按一下 **金鑰**。  
  
   2.  型別**maxConcurrentRequestsPerCPU**，然後按**ENTER**。  
  
   3.  底下**maxConcurrentRequestsPerCPU**機碼，請建立 DWORD 項目與 maxConcurrentRequestsPerCPU 的新值。  
  
   4.  關閉 [登錄編輯程式]。  
  
   **若要設定的 aspnet.config 檔案的組態區段中的應用程式集區 maxConcurrentRequestsPerCPU 值**  
  
> [!NOTE]  
>  必須安裝 Microsoft.NET Framework 4，以容納透過組態檔設定下列值。 您可以下載 Microsoft.NET Framework 4 [Microsoft.NET Framework 4 （Web 安裝程式）](http://go.microsoft.com/fwlink/?LinkID=189318) (http://go.microsoft.com/fwlink/?LinkID=189318)。  
  
-   開啟應用程式集區的 aspnet.config 檔案，然後輸入新的值**maxConcurrentRequestsPerCPU**並**requestQueueLimit**參數。  
  
     下列範例中的值是預設值。  
  
    ```  
    <system.web>  
        <applicationPool maxConcurrentRequestsPerCPU="5000" requestQueueLimit="5000"/>  
    </system.web>  
    ```  
  
> [!NOTE]  
>  這個值會覆寫指定的值**maxConcurrentRequestsPerCPU**在登錄中。 **RequestQueueLimit**設定為 processModel/requestQueueLimit，相同，不同之處在於 aspnet.config 檔中的設定會覆寫 machine.config 檔案中的設定。  
  
## <a name="define-clr-hosting-thread-values-for-biztalk-host-instances"></a>定義的 CLR 裝載執行緒值，BizTalk 主控件執行個體  
 由於 Windows 執行緒是 Windows 程序可使用的最基本可執行單位，所以為與 BizTalk 主控件執行個體關聯的 .NET 執行緒集區配置足夠的執行緒，以避免執行緒不足，是很重要的。 若發生執行緒不足，沒有足夠的執行緒可用來執行要求之工作的效能受到負面影響。 同時，您也必須小心避免配置超出需要的執行緒給與主控件關聯的 .NET 執行緒集區。 與主機相關聯的.NET 執行緒集區過多執行緒配置可能會增加內容切換。 Windows 核心切換到不同的執行緒，會產生效能成本執行一個執行緒時，就會發生內容切換。 過多的執行緒配置可能會導致內容切換過多，這會造成負面影響整體效能。 預設的 BizTalk 主控件執行個體的.NET 執行緒集區配置的執行緒數目取決於已安裝的.NET framework 版本。 .NET Framework 4 和.NET Framework 3.5 SP1 大幅增加預設值，而在 BizTalk Server 電腦和 MessageBox 資料庫上的過多的鎖定爭用造成過度的執行緒配置。  
  
 使用**BizTalk 設定儀表板**，針對在.NET 中的可用 Windows 執行緒數目的執行緒與 BizTalk 主控件執行個體相關聯的集區，您可以修改預設值。 如需如何修改.NET CLR 設定的詳細資訊，請參閱[如何修改.NET CLR 設定](http://go.microsoft.com/fwlink/?LinkID=205344)(http://go.microsoft.com/fwlink/?LinkID=205344)。 .NET CLR 設定是每一核心的 CPU。  
  
> [!NOTE]  
>  **背景工作執行緒**用來處理已排入佇列的工作項目和**I/O 執行緒**會處理已完成的非同步 I/O 要求 I/O 完成連接埠相關聯的專用的回呼執行緒。  
  
|執行緒設定|預設值|建議值|  
|------------------------|-------------------|-----------------------|  
|最大的 IO 執行緒|250|250|  
|最大工作者執行緒|25|100**重要事項：** 增加此值超過 100 可以裝載 BizTalk Server MessageBox 資料庫的 SQL Server 電腦的效能造成不良的影響。 發生此問題時，SQL Server 可能會發生鎖死的情況。 我們建議不超過 100 的值，這個參數。|  
|最小的 IO 執行緒|25|25|  
|最小的背景工作執行緒|5|25|  
  
> [!NOTE]  
>  建議的值不是絕對的而且可能需要根據 BizTalk 應用程式來調整。 變更一次的一個參數，然後進行進一步變更之前，測量的效能和穩定性的 BizTalk 平台上的影響。  
  
> [!NOTE]  
>  這些值會以隱含方式乘以伺服器上的處理器數目。 例如，設定**MaxWorkerThreads**到 100 的值的項目會有效地 4 CPU 伺服器上設定值為 400。  
  
## <a name="disable-biztalk-server-group-level-tracking"></a>停用 BizTalk Server 群組層級追蹤  
 追蹤時產生的資料已寫入 MessageBox 資料庫，並以非同步方式移動到 BizTalk 追蹤資料庫的 BizTalk Server 中的額外負荷的效能。 在生產環境 BizTalk Server 環境中設定追蹤時，就會適用下列考量：  
  
- 根據經驗法則，如果追蹤不是一項業務需求，則停用群組層級追蹤，以減少額外負荷並提高效能。  
  
   若要停用 BizTalk Server 群組層級追蹤，請執行下列步驟：  
  
  1.  在  **BizTalk Server 管理主控台**，展開**BizTalk Server 管理**，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **設定**.  
  
  2.  在 BizTalk 設定儀表板 對話方塊的 在群組頁面上，清除**啟用群組層級追蹤**核取方塊。  
  
  3.  按一下 **確定**以套用所做的修改並結束 設定儀表板。  
  
- 只能使用訊息內文追蹤，如有必要。 訊息大小和訊息輸送量，訊息內文追蹤可能會造成相當大的負擔。 追蹤的 BizTalk 活動有明顯的好處，以便進行偵錯和稽核，它也有相當大的效能和延展性的影響。 因此，您應該追蹤資料，並基於偵錯和安全性理由，是絕對必要，並避免追蹤多餘的資訊。  
  
- 根據預設，下列追蹤選項會啟用協調流程：  
  
  - 協調流程開始和結束  
  
  - 訊息傳送與接收  
  
  - 流程化開始與結束  
  
    追蹤選項 」 流程化開始與結束 「 協調流程會產生重大的額外負荷，並不應該在生產環境中，高輸送量功能需要啟用。 協調流程追蹤選項會在上的 BizTalk 管理主控台中存取**追蹤**協調流程屬性 對話方塊的頁面。  
  
  如需有關如何設定追蹤的詳細資訊，請參閱 <<c0> [ 設定追蹤使用 BizTalk Server 管理主控台](http://go.microsoft.com/fwlink/?LinkId=158021)(http://go.microsoft.com/fwlink/?LinkId=158021)。  
  
## <a name="decrease-the-purging-period-for-the-dta-purge-and-archive-job-from-7-days-to-2-days-in-high-throughput-scenarios"></a>DTA 清除與封存工作從 7 天 2 天在高輸送量情況下減少清除的期間  
 根據預設，在 BizTalk Server 中追蹤資料的清除間隔設為 7 天。 在高輸送量情況下，這可能會造成在追蹤資料庫中，最終會影響 MessageBox 和依次造成負面影響訊息處理輸送量的效能資料過多組建設定中。  
  
 在高輸送量情況下，減少硬性和軟性清除從預設的 7 天的間隔為 2 天。 如需有關設定清除間隔的詳細資訊，請參閱[如何設定 DTA 清除與封存工作](http://go.microsoft.com/fwlink/?LinkID=153814)(http://go.microsoft.com/fwlink/?LinkID=153814) BizTalk Server 2010 說明中。  
  
## <a name="configure-the-temp-path-for-the-biztalk-service-account-to-point-to-a-separate-disk-or-lun"></a>設定 BizTalk 服務帳戶，以指向不同的磁碟或 LUN 的 %temp%路徑  
 因為 BizTalk 使用資料流檔案的暫存位置，對磁碟執行複雜對應作業時，這應該會完成。  
  
## <a name="install-the-latest-service-packs"></a>安裝最新的 service pack  
 應該安裝最新的 service pack，BizTalk Server 和.NET Framework，因為其中包含可以修正您可能會遇到效能問題的修正程式。  
  
## <a name="performance-optimizations-in-the-biztalk-server-documentation"></a>在 BizTalk Server 文件中的效能最佳化  
 適用於從 BizTalk Server 文件，視下列建議：  
  
-   [MessageBox 延遲問題進行疑難排解](http://go.microsoft.com/fwlink/?LinkId=158019)(http://go.microsoft.com/fwlink/?LinkId=158019)  
  
-   [找出效能瓶頸](http://go.microsoft.com/fwlink/?LinkID=154238)(http://go.microsoft.com/fwlink/?LinkID=154238)  
  
-   [避免 DBNETLIB 例外狀況](http://go.microsoft.com/fwlink/?LinkID=155308)(http://go.microsoft.com/fwlink/?LinkID=155308)  
  
-   [避免 TCP/IP 連接埠耗盡](http://go.microsoft.com/fwlink/?LinkID=153240)(http://go.microsoft.com/fwlink/?LinkID=153240)  
  
-   [設定 EPM 執行緒集區大小](http://go.microsoft.com/fwlink/?LinkId=158020)(http://go.microsoft.com/fwlink/?LinkId=158020)  
  
## <a name="see-also"></a>另請參閱  
 [最佳化 BizTalk Server 效能](../technical-guides/optimizing-biztalk-server-performance.md)