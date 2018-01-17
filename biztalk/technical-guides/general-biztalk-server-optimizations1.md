---
title: "一般 BizTalk Server Optimizations1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8032553-bae3-440d-9197-b926160b0bdf
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e9e799822c63cb78eda1b989cb157c71fd357d8
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="general-biztalk-server-optimizations"></a>一般 BizTalk Server 最佳化
下列建議可以用於增加 BizTalk Server 效能。 安裝和設定 BizTalk Server 後，會套用本主題中列出的最佳化。  
  
## <a name="configure-msdtc"></a>設定 MSDTC  
 若要簡化 SQL Server 與 BizTalk Server 之間的交易，您必須啟用 Microsoft 分散式交易協調器 (MS DTC)。 若要在 BizTalk Server 上設定 MSDTC，請參閱主題[改善作業系統效能的一般指導方針](../technical-guides/general-guidelines-for-improving-operating-system-performance.md)。  
  
## <a name="recommendations-for-configuring-biztalk-server-hosts"></a>設定 BizTalk Server 主控件的建議  
 本節提供設定 BizTalk Server 主控件的建議。  
  
### <a name="create-multiple-biztalk-server-hosts-and-separate-host-instances-by-functionality"></a>建立多個 BizTalk Server 主控件和個別的主控件執行個體功能  
 請遵循下列指導方針來建立多個 BizTalk Server 主控件，並在這些主機上配置的工作負載：  
  
-   建立個別的主控件來傳送、 接收、 處理及追蹤功能。 建立多個 BizTalk 主控件提供的彈性設定 BizTalk 群組中的工作負載時，將處理分散到 BizTalk 群組中執行 BizTalk Server 之電腦的主要方法。 使用多部主機，可讓您停止一部主機，而不會影響其他主機。 比方說，您可能想要停止傳送訊息，通知他們佇列 MessageBox 資料庫中同時，仍允許接收配接器執行不同的主控件執行個體中來接收傳入的訊息。 分隔主控件執行個體功能也會提供下列優點：  
  
    -   執行多個 BizTalk 主控件會減少 MessageBox 資料庫主應用程式佇列資料表上的競爭，因為每一部主機指派自己 MessageBox 資料庫中的工作佇列資料表。  
  
    -   節流是 BizTalk Server 中實作主機層級。 這可讓您設定每個主控件節流的特性不同。  
  
    -   在主機層級; 實作安全性每一部主機會使用不連續的 Windows 身分識別下執行。 這可讓您，比方說，讓 Host_A 存取 FileShare_B，同時不允許任何其他主機，才能存取檔案共用。  
  
-   每個主控件執行個體的.NET 執行緒集區中有它自己的資源，例如記憶體、 控制代碼，以及執行緒集。 在主機上配置的工作負載時請考慮將一起調整的資源放在相同的主機。  
  
-   個別的配接器和協調流程中不同的主控件具有不同優先順序的資源。 這項技術可容納主機專用的 BizTalk Server 電腦上執行高優先順序的應用程式的位置。  
  
> [!NOTE]  
>  優點，可建立其他主控件執行個體時，也有缺點如果太多的主控件執行個體所建立。 每個主控件執行個體是 Windows 服務 (BTSNTSvc.exe)，會產生對 MessageBox 資料庫的額外負載，並使用電腦資源 （例如 CPU、 記憶體、 執行緒）。  
  
 如需有關修改 BizTalk Server 主機的內容，請參閱[如何修改主機內容](http://go.microsoft.com/fwlink/?LinkID=154359)(http://go.microsoft.com/fwlink/?LinkID=154359) BizTalk Server 2010 說明中。  
  
### <a name="configure-a-dedicated-tracking-host"></a>設定專用的追蹤主控件  
 BizTalk Server 已針對輸送量最佳化，因此主要協調流程和傳訊引擎不實際訊息直接來移動的 BizTalk 追蹤資料庫或 BAM 資料庫，因為這會轉向這些引擎從執行商務程序的主要工作。 相反地，BizTalk Server 將訊息保留在 MessageBox 資料庫，並將其標示為需要移至 「 BizTalk 追蹤資料庫。 背景處理序 （追蹤主控件），然後移動訊息至 BizTalk 追蹤資料庫和 BAM 資料庫。 追蹤是需要大量資源的作業，因為個別的主控件應建立專門用來追蹤，藉此追蹤的訊息處理至專用的主機上的影響降到最低。 為了達到最佳效能，應該有至少一個追蹤主控件執行個體，每個 MessageBox 資料庫。 追蹤主控件執行個體的實際數目應為 N + 1，其中 N = MessageBox 資料庫數目。 "+ 1"是作為備援，其中一部電腦裝載追蹤失敗時。  
  
 使用專用的追蹤主控件也可讓您停止其他 BizTalk 主控件，而不會干擾 BizTalk Server 追蹤。 追蹤資料從 MessageBox 資料庫的移動是狀況良好的 BizTalk Server 系統的關鍵。 如果停止 BizTalk 主控件負責將追蹤資料移 BizTalk 群組中，將不會執行追蹤資料解碼服務。 這個影響是，如下所示：  
  
-   HAT 追蹤資料不會從 MessageBox 資料庫移動到 BizTalk 追蹤資料庫。  
  
-   BAM 追蹤資料會從 MessageBox 資料庫移至 BAM 主要匯入資料庫。  
  
-   不移動資料，因為它無法從 MessageBox 資料庫刪除。  
  
-   追蹤資料解碼服務停止時，追蹤攔截器仍會引發，將追蹤資料寫入至 MessageBox 資料庫。 如果未移動資料，這會導致 MessageBox 資料庫變得繁雜，這樣會影響一段時間的效能。 即使自訂屬性不會受到追蹤，或是未設定 BAM 設定檔，根據預設某些會追蹤資料 （例如，管線接收 / 傳送事件和協調流程事件）。 如果您不想執行的追蹤資料解碼服務，請關閉所有的追蹤，以便任何攔截器會將資料儲存至資料庫。 若要停用全域追蹤，請參閱[如何關閉全域追蹤](http://go.microsoft.com/fwlink/?LinkID=154193)(http://go.microsoft.com/fwlink/?LinkID=154193) BizTalk Server 2010 說明中。 使用 BizTalk Server 管理主控台，以選擇性地停用追蹤事件。  
  
 追蹤主控件應執行 BizTalk Server （適用於在其中一個失敗的情況下的備援性） 的至少兩部電腦上執行。 為了達到最佳效能，您應該有至少一個追蹤主控件執行個體，每個 MessageBox 資料庫。 追蹤主控件執行個體的實際數目應為 （N + 1），其中 N = MessageBox 資料庫數目。 "+ 1"是作為備援，其中一部電腦裝載追蹤失敗時。  
  
 追蹤主控件執行個體移動特定的 MessageBox 資料庫的追蹤資料，但是會永遠不會有多個追蹤主控件執行個體特定的 MessageBox 資料庫移動資料。 例如，如果您有三個 MessageBox 資料庫，且只有兩個追蹤主控件執行個體，然後其中一個主控件執行個體需要移動兩個 MessageBox 資料庫的資料。 加入第三個追蹤主控件執行個體分散追蹤裝載執行 BizTalk Server 的另一部電腦的工作。 在此案例中，加入第四個追蹤主控件執行個體不會散佈任何的多個追蹤主控件使用，但會提供額外的追蹤主控件執行個體的容錯功能。  
  
 如需有關 BAM 事件匯流排服務的詳細資訊，請參閱 BizTalk Server 2010 說明中的下列主題：  
  
-   [管理 BAM 事件匯流排服務](http://go.microsoft.com/fwlink/?LinkID=154194)(http://go.microsoft.com/fwlink/?LinkID=154194)。  
  
-   [建立的 BAM 事件匯流排服務執行個體](http://go.microsoft.com/fwlink/?LinkID=154195)(http://go.microsoft.com/fwlink/?LinkID=154195)。  
  
### <a name="do-not-cluster-biztalk-hosts-unless-absolutely-necessary"></a>除非未叢集化 BizTalk 主控件有絕對的必要性  
 BizTalk Server 2010，可讓您將 BizTalk 主控件設定為叢集資源，您應該只考慮這麼做，如果您需要提供高可用性，無法跨多個 BizTalk 電腦裝載的資源。 例如，使用 FTP 配接器的連接埠應只位於一個主控件執行個體，因為 FTP 通訊協定不提供檔案鎖定。 不過，這會帶來單點失敗，可從叢集獲益。 包含配接器，例如檔案、 SQL、 HTTP 或處理只有主機的主機可以在內部負載平衡的電腦，並不會受益於叢集。  
  
## <a name="increase-the-number-of--http-concurrent-connections-allowed-by-changing-the-value-for-the-maxconnection-parameter"></a>增加 HTTP 變更 maxconnection 參數的值所允許的並行連線的數目  
 根據預設，HTTP 配接器 （包括 WCF 基礎 HTTP 配接器） 會從每部執行 BizTalk Server 至任何特定的目的地伺服器的電腦開啟只有兩個並行的 HTTP 連接。  
  
 此設定符合 HTTP 1.1 規格，IETF RFC，雖然它是適用於使用者案例，它不適合高輸送量。 設定實際上會先調節每一部伺服器的輸出 HTTP 呼叫兩個並行傳送到從每部執行 BizTalk Server 的電腦。  
  
 若要增加並行連接數目，您可以修改 maxconnection 參數，BizTalk Server 組態檔，BTSNTSvc.exe.config （或 64 位元主控件的 BTSNTSvc64.exe.config），每個 BizTalk Server 中的值。 您可以增加此呼叫的特定伺服器。 根據經驗法則，請為 maxconnection 參數的值應該設定為 12 * 的 Cpu 或裝載的 web 應用程式的電腦上的核心數目。  
  
> [!NOTE]  
>  請勿增加這類較大的值所呼叫的 Web 伺服器使用 HTTP 連線爆 maxconnection 參數的值。 在之後變更 maxconnection 參數的值，來執行壓力測試要求傳送到每個目的地 Web 伺服器，以判斷的值將會提供良好的效能和 HTTP 的 maxconnection 傳送但不過度目標網站伺服器。  
  
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
  
 設定 maxconnection 屬性時，可以指定 HTTP、 HTTPS、 web 站台 IP 位址和連接埠號碼。 其他範例包括：  
  
 **\<add address="https://www.contoso.com" maxconnection="24" /\>**   
**\<add address="http://www.contoso.com:8080" maxconnection="24" /\>**   
**\<新增位址 ="http://*IPAddress*"maxconnection = 「 24 」 /\>** 微調 IIS 和 ASP.NET Web 服務設定的詳細資訊，請參閱 < ASP.NET 設定，可能會影響 HTTP 配接器效能 」 一節[組態參數會影響配接器效能](http://go.microsoft.com/fwlink/?LinkID=154200)(http://go.microsoft.com/fwlink/?LinkID=154200) BizTalk Server 2010 說明中。  
  
## <a name="manage-aspnet-thread-usage-or-concurrently-executing-requests-for-web-applications-that-can-host--isolated-received-locations-back-end-web-services-and-wcf-services"></a>管理 ASP.NET 執行緒用法，或同時執行之要求的可裝載的 Web 應用程式隔離的接收的位置、 後端 Web 服務和 WCF 服務  
 背景工作和 I/O 執行緒 （IIS 7.5 和傳統模式中的 IIS 7.0） 或同時執行要求 （IIS 7.5 和 7.0 整合的模式） 的 ASP.NET Web 應用程式主機隔離接收的位置、 後端 Web 服務和 WCF 服務的數目的數目在下列情況下應修改：  
  
-   CPU 使用率不是在裝載的 Web 伺服器上的瓶頸。  
  
-   值：  
  
    -   **ASP.NET 應用程式 v4.0.30319 \Request Wait Time**或**ASP.NET 應用程式 v4.0.30319 \Request 執行時間**效能計數器是特別高。  
  
    -   **ASP.NET 應用程式 v2.0.50727\Request Wait Time**或**ASP.NET 應用程式 v2.0.50727\Request 執行時間**效能計數器是特別高。  
  
-   裝載 Web 應用程式的電腦的應用程式記錄檔中會產生類似下列的錯誤。  
  
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
  
### <a name="manage-aspnet-thread-usage-for-web-applications-that-can-host-isolated-received-locations-back-end-web-services-and-wcf-services-on-iis-75-and-iis-70-running-in-classic-mode"></a>管理 Web 應用程式可以裝載外掛式接收的位置、 後端 Web 服務和 IIS 7.5 和 IIS 7.0 以傳統模式執行的 WCF 服務的 ASP.NET 執行緒用法  
 當**autoConfig**以傳統模式執行 IIS 7.5 和 IIS 7.0 伺服器的 machine.config 檔案中的值設定為**true**，ASP.NET 2.0 和 ASP.NET 4 管理背景工作執行緒和 I/O 執行緒的數目會配置給任何相關聯的 IIS 工作者處理序。  
  
```  
<processModel autoConfig="true" />  
```  
  
 若要以手動方式修改的背景工作 」 與 ASP.NET 2.0 和 ASP.Net 4 Web 應用程式的 I/O 執行緒數目，開啟相關聯的 machine.config 檔案，，然後輸入新值**maxWorkerThreads**和**maxIoThreads**參數。  
  
```  
<!-- <processModel autoConfig="true" /> -->  
    <processModel maxWorkerThreads="200" maxIoThreads="200" />  
```  
  
> [!NOTE]  
>  這些值是指導方針; 僅限請測試變更這些參數。  
  
 如需調整 ASP.NET 2.0 Web 應用程式的 machine.config 檔案中的參數的詳細資訊，請參閱 Microsoft 知識庫文章 821268[爭用、 效能不佳和死結，當您從 ASP Web 服務要求。NET 應用程式](http://go.microsoft.com/fwlink/?LinkID=144169)(http://go.microsoft.com/fwlink/?LinkID=144169)。  
  
### <a name="manage-the-number-of-concurrently-executing-requests-for-aspnet-20-web-applications-that-can-host-isolated-received-locations-back-end-web-services-and-wcf-services-on-iis-75-and-iis-70-running-in-integrated-mode"></a>管理並行執行 ASP.NET 2.0 Web 應用程式可以裝載外掛式接收的位置、 後端 Web 服務和 IIS 7.5 和 IIS 7.0 以整合模式執行的 WCF 服務的要求數目  
 在 IIS 7.5 和 IIS 7.0 上裝載 ASP.NET 2.0 整合模式中時, 使用的執行緒的處理方式與在 IIS 7.5 和 IIS 7.0 上以傳統模式。 在 IIS 7.5 和 IIS 7.0 上裝載 ASP.NET 2.0 整合模式中，當 ASP.NET 2.0 限制同時執行的數目**要求**而不是數**執行緒**並行執行要求。 同步的情況下這會間接限制執行緒數目，但非同步案例的要求和執行緒的數目可能會非常不同。 整合式模式，在 IIS 7.5 和 IIS 7.0 上執行 ASP.NET 2.0 時**maxWorkerThreads**和**maxIoThreads** machine.config 檔案中的參數不會用來管理執行中執行緒的數目。 相反地，同時執行要求的數目可以變更從 12 每一 CPU 的預設值修改為指定的值**maxConcurrentRequestsPerCPU**。 **MaxConcurrentRequestsPerCPU** reqistry 或 aspnet.config 檔案的組態區段中，可以指定值。 請遵循下列步驟來變更預設值為**maxConcurrentRequestsPerCPU**來管理 並行執行要求的數目：  
  
 **在登錄中設定 maxConcurrentRequestsPerCPU 值**  
  
> [!WARNING]  
>  不當使用登錄編輯程式可能會導致問題，需要重新安裝作業系統。 您必須自行負擔使用「登錄編輯程式」的風險。 如需如何備份、 還原和修改登錄的詳細資訊，請參閱 Microsoft 知識庫文章 256986[進階使用者的 Windows 登錄資訊](http://go.microsoft.com/fwlink/?LinkId=62729)(http://go.microsoft.com/fwlink/?LinkId=62729)。  
  
> [!NOTE]  
>  這項設定是全域設定，不能變更個別的應用程式集區或應用程式。  
  
1.  按一下 **[開始]**、按一下 **[執行]**、輸入 **regedit.exe**，然後按一下 **[確定]** 以啟動「登錄編輯程式」。  
  
2.  瀏覽至**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0**  
  
3.  依照下列步驟中建立機碼：  
  
    1.  在**編輯**功能表上，按一下 **新增**，然後按一下 **金鑰**。  
  
    2.  型別**maxConcurrentRequestsPerCPU**，然後按下**ENTER**。  
  
    3.  在下**maxConcurrentRequestsPerCPU**機碼中，建立 DWORD 項目 maxConcurrentRequestsPerCPU 的新值。  
  
    4.  關閉 [登錄編輯程式]。  
  
 **若要設定應用程式集區的 maxConcurrentRequestsPerCPU 值 aspnet.config 檔案的組態區段中**  
  
> [!NOTE]  
>  必須安裝 Microsoft.NET Framework 3.5 Service Pack 1，以容納透過組態檔設定下列值。 您可以下載 Microsoft.NET Framework 3.5 Service Pack 1 從[Microsoft.NET Framework 3.5 Service Pack 1](http://go.microsoft.com/fwlink/?LinkID=136345) (http://go.microsoft.com/fwlink/?LinkID=136345)。  
  
 開啟應用程式集區的 aspnet.config 檔案，然後輸入新值**maxConcurrentRequestsPerCPU**和**requestQueueLimit**參數。  
  
```  
<system.web>  
    <applicationPool maxConcurrentRequestsPerCPU="12" requestQueueLimit="5000"/>  
</system.web>  
```  
  
> [!NOTE]  
>  這個值會覆寫指定的值**maxConcurrentRequestsPerCPU**登錄中。 RequestQueueLimit 設定等同於 processModel/requestQueueLimit，不同之處在於 aspnet.config 檔案中的設定會覆寫 machine.config 檔案中的設定。  
  
 如需在 IIS 7.0 上設定 ASP.NET 執行緒用法的詳細資訊，請參閱[Thomas Marquardt 部落格上 IIS 7.0 ASP.NET 執行緒用法](http://go.microsoft.com/fwlink/?LinkId=157518)(http://go.microsoft.com/fwlink/?LinkId=157518)。  
  
### <a name="manage-the-number-of-concurrently-executing-requests-for-aspnet-4web-applications-that-can-host-isolated-received-locations-back-end-web-services-and-wcf-services-on-iis-75-and-70-running-in-integrated-mode"></a>管理並行執行的外掛式接收的位置、 後端 Web 服務和 IIS 7.5 和 7.0 整合模式執行的 WCF 服務可以裝載的 ASP.NET 4Web 應用程式的要求數目  
 .NET Framework 4，maxConcurrentRequestsPerCPU 的預設值為 5000，這可能會非常大的值，並因此將允許充足的同時執行的非同步要求。 如需詳細資訊，請參閱[ \<applicationPool\>項目 （Web 設定）](http://go.microsoft.com/fwlink/?LinkID=205339) (http://go.microsoft.com/fwlink/?LinkID=205339)。  
  
 IIS 7.5 和 IIS 7.0 整合模式中，名為 MaxConcurrentRequestsPerCPU 內 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\4.0.30319.0 DWORD 會決定每一 CPU 的並行要求數目。 根據預設，登錄機碼不存在，且每一 CPU 的要求數目限制為 5000。  
  
 **在登錄中設定 maxConcurrentRequestsPerCPU 值**  
  
> [!WARNING]  
>  不當使用登錄編輯程式可能會導致問題，需要重新安裝作業系統。 您必須自行負擔使用「登錄編輯程式」的風險。 如需如何備份、 還原和修改登錄的詳細資訊，請參閱 Microsoft 知識庫文章 256986[進階使用者的 Windows 登錄資訊](http://go.microsoft.com/fwlink/?LinkId=62729)(http://go.microsoft.com/fwlink/?LinkId=62729)。  
  
> [!NOTE]  
>  這項設定是全域設定，不能變更個別的應用程式集區或應用程式。  
  
1.  按一下 **[開始]**、按一下 **[執行]**、輸入 **regedit.exe**，然後按一下 **[確定]** 以啟動「登錄編輯程式」。  
  
2.  瀏覽至**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\4.0.30319.0**。  
  
3.  依照下列步驟中建立機碼：  
  
    1.  在**編輯**功能表上，按一下 **新增**，然後按一下 **金鑰**。  
  
    2.  型別**maxConcurrentRequestsPerCPU**，然後按下**ENTER**。  
  
    3.  在下**maxConcurrentRequestsPerCPU**機碼中，建立 DWORD 項目 maxConcurrentRequestsPerCPU 的新值。  
  
    4.  關閉 [登錄編輯程式]。  
  
 **若要設定應用程式集區的 maxConcurrentRequestsPerCPU 值 aspnet.config 檔案的組態區段中**  
  
> [!NOTE]  
>  必須安裝 Microsoft.NET Framework 4，以容納透過組態檔設定下列值。 您可以下載從 Microsoft.NET Framework 4 [Microsoft.NET Framework 4 （Web 安裝程式）](http://go.microsoft.com/fwlink/?LinkID=189318) (http://go.microsoft.com/fwlink/?LinkID=189318)。  
  
-   開啟應用程式集區的 aspnet.config 檔案，然後輸入新值**maxConcurrentRequestsPerCPU**和**requestQueueLimit**參數。  
  
     下列範例中的值是預設值。  
  
    ```  
    <system.web>  
        <applicationPool maxConcurrentRequestsPerCPU="5000" requestQueueLimit="5000"/>  
    </system.web>  
    ```  
  
> [!NOTE]  
>  這個值會覆寫指定的值**maxConcurrentRequestsPerCPU**登錄中。 **RequestQueueLimit**設定等同於 processModel/requestQueueLimit，不同之處在於 aspnet.config 檔案中的設定會覆寫 machine.config 檔案中的設定。  
  
## <a name="define-clr-hosting-thread-values-for-biztalk-host-instances"></a>定義的 CLR 裝載執行緒值 BizTalk 主控件執行個體  
 由於 Windows 執行緒是 Windows 程序可使用的最基本可執行單位，所以為與 BizTalk 主控件執行個體關聯的 .NET 執行緒集區配置足夠的執行緒，以避免執行緒不足，是很重要的。 若發生執行緒不足，沒有足夠的執行緒可用來執行要求的工作的效能受到負面影響。 同時，您也必須小心避免配置超出需要的執行緒給與主控件關聯的 .NET 執行緒集區。 與主機相關聯的.NET 執行緒集區過多執行緒配置可能會增加內容切換。 Windows 核心從執行一個執行緒不同的執行緒，會產生效能成本會切換時，就會發生內容切換。 過度的執行緒配置可能會導致內容切換過多，這會造成負面影響整體效能。 預設的 BizTalk 主控件執行個體的.NET 執行緒集區配置的執行緒數目取決於所安裝的.NET framework 版本。 .NET Framework 4 和.NET Framework 3.5 SP1 會大幅增加 BizTalk Server 電腦和 MessageBox 資料庫上的過多的鎖定爭用會導致過度的執行緒配置的預設值。  
  
 使用**BizTalk 設定儀表板**，針對.NET 中的可用 Windows 執行緒數目的執行緒與 BizTalk 主控件執行個體相關聯的集區，您可以修改預設值。 如需如何修改.NET CLR 設定的詳細資訊，請參閱[如何修改.NET CLR 設定](http://go.microsoft.com/fwlink/?LinkID=205344)(http://go.microsoft.com/fwlink/?LinkID=205344)。 .NET CLR 設定為每個核心 CPU。  
  
> [!NOTE]  
>  **背景工作執行緒**用來處理佇列的工作項目和**I/O 執行緒**專用的回呼執行緒來處理已完成的非同步 I/O 要求 I/O 完成通訊埠相關聯。  
  
|執行緒設定|預設值|建議值|  
|------------------------|-------------------|-----------------------|  
|最大 IO 執行緒|250|250|  
|最大工作者執行緒|25|100**重要事項：**增加此值超過 100，則可以有裝載 BizTalk Server MessageBox 資料庫之 SQL Server 電腦的效能造成負面影響。 發生此問題時，SQL Server 可能會遇到死結狀況。 我們建議您在不增加超過 100 的值，這個參數。|  
|最小 IO 執行緒|25|25|  
|最小的背景工作執行緒|5|25|  
  
> [!NOTE]  
>  建議的值不是絕對的而且可能需要調整不同的 BizTalk 應用程式。 變更一次一個參數，然後再進行其他變更測量的效能和穩定性 BizTalk 平台上的影響。  
  
> [!NOTE]  
>  這些值會以隱含方式乘以伺服器上的處理器數目。 例如，設定**MaxWorkerThreads**到 100 的值會有效地上設定項目值為 400 4 CPU 伺服器。  
  
## <a name="disable-biztalk-server-group-level-tracking"></a>停用 BizTalk Server 群組層級追蹤  
 追蹤導致 BizTalk Server 中的額外負荷的效能，因為資料已寫入至 MessageBox 資料庫，然後以非同步方式移動到 BizTalk 追蹤資料庫。 在生產環境 BizTalk Server 中設定追蹤時，就會適用下列考量：  
  
-   根據經驗法則，如果追蹤不是一項業務需求，然後停用群組層級追蹤，以減少額外負荷並提高效能。  
  
     若要停用 BizTalk Server 群組層級追蹤，請執行下列步驟：  
  
    1.  在**BizTalk Server 管理主控台**，依序展開**BizTalk Server 管理**，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **設定**.  
  
    2.  在 [BizTalk 設定儀表板] 對話方塊中，在 [群組] 頁面中清除**啟用群組層級追蹤**核取方塊。  
  
    3.  按一下**確定**以套用變更並結束 設定儀表板。  
  
-   只會使用訊息內文追蹤，如有必要。 根據訊息的處理能力和訊息大小，訊息內文追蹤可能會造成顯著的額外負荷。 雖然 BizTalk 活動追蹤有明顯的好處，偵錯和稽核，也有相當大的效能和延展性的含意。 因此，您應該追蹤資料，是絕對必要的偵錯和安全性理由，並可避免追蹤多餘的資訊。  
  
-   根據預設，下列的追蹤選項可供協調流程：  
  
    -   協調流程開始和結束  
  
    -   訊息傳送與接收  
  
    -   圖形開始和結束  
  
     追蹤選項 」 圖形開始與結束 「 協調流程會產生大量負擔，且不應啟用其中需要高輸送量是在生產環境中。 協調流程的追蹤選項會在上的 BizTalk 管理主控台中存取**追蹤**協調流程屬性 對話方塊的頁面。  
  
 如需有關如何設定追蹤的詳細資訊，請參閱[設定追蹤使用 BizTalk Server 管理主控台](http://go.microsoft.com/fwlink/?LinkId=158021)(http://go.microsoft.com/fwlink/?LinkId=158021)。  
  
## <a name="decrease-the-purging-period-for-the-dta-purge-and-archive-job-from-7-days-to-2-days-in-high-throughput-scenarios"></a>在清除期間減少 DTA 清除和封存工作從 7 天在高輸送量的 2 天  
 根據預設，追蹤 BizTalk Server 中的資料的清除間隔設定為 7 天。 在高輸送量實例中，導致在追蹤資料庫中，最後將會影響 MessageBox 和依次造成負面影響訊息處理輸送量的效能資料過多建置設定。  
  
 在高輸送量的情況下，減少硬與軟清除來自預設值是 7 天的間隔為 2 天。 如需設定清除間隔的詳細資訊，請參閱[如何設定 DTA 清除與封存工作](http://go.microsoft.com/fwlink/?LinkID=153814)(http://go.microsoft.com/fwlink/?LinkID=153814) BizTalk Server 2010 說明中。  
  
## <a name="configure-the-temp-path-for-the-biztalk-service-account-to-point-to-a-separate-disk-or-lun"></a>設定 BizTalk 服務帳戶，以指向不同的磁碟或 LUN 的 %temp%路徑  
 這應該會完成，因為 BizTalk 會暫存位置使用資料流檔案來執行複雜的對應作業時的磁碟。  
  
## <a name="install-the-latest-service-packs"></a>安裝最新的 service pack  
 應該安裝最新的 service pack，BizTalk Server 與.NET Framework，因為其中包含可以修正您可能會遇到效能問題的修正程式。  
  
## <a name="performance-optimizations-in-the-biztalk-server-documentation"></a>BizTalk Server 文件中的效能最佳化  
 適用於適當的 BizTalk Server 文件的下列建議：  
  
-   [MessageBox 延遲問題疑難排解](http://go.microsoft.com/fwlink/?LinkId=158019)(http://go.microsoft.com/fwlink/?LinkId=158019)  
  
-   [找出效能瓶頸](http://go.microsoft.com/fwlink/?LinkID=154238)(http://go.microsoft.com/fwlink/?LinkID=154238)  
  
-   [避免 DBNETLIB 例外狀況](http://go.microsoft.com/fwlink/?LinkID=155308)(http://go.microsoft.com/fwlink/?LinkID=155308)  
  
-   [避免 TCP/IP 連接埠耗盡](http://go.microsoft.com/fwlink/?LinkID=153240)(http://go.microsoft.com/fwlink/?LinkID=153240)  
  
-   [設定 EPM 執行緒集區大小](http://go.microsoft.com/fwlink/?LinkId=158020)(http://go.microsoft.com/fwlink/?LinkId=158020)  
  
## <a name="see-also"></a>另請參閱  
 [最佳化 BizTalk Server 效能](../technical-guides/optimizing-biztalk-server-performance.md)