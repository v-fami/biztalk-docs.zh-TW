---
title: 一般 BizTalk Server Optimizations2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41b452e9-d94c-4bcb-8ef6-e9cea28fc0ab
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af09f938d93377a6463926fad3725c9f9dace294
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022180"
---
# <a name="general-biztalk-server-optimizations"></a>一般 BizTalk Server 最佳化
下列建議可用來增加[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能。 本主題中所列的最佳化之後，會套用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]已安裝和設定。  
  
## <a name="create-multiple-biztalk-server-hosts-and-separate-host-instances-by-functionality"></a>依功能建立多個 BizTalk Server 主控件和個別的主控件執行個體  
 應該建立不同的主控件，來傳送、 接收、 處理及追蹤功能。 建立多個 BizTalk 主控件提供彈性設定 BizTalk 群組中的工作負載時，將處理分散到 BizTalk 群組中的 BizTalk 伺服器的主要方法。 多部主機也可讓您停止一部主機，而不會影響其他主機。 比方說，您可能要停止傳送訊息，讓他們佇列在 Messagebox 資料庫中，同時仍然允許輸入的接收的訊息進行。 主控件執行個體分隔功能時，也會提供下列優點：  
  
-   每個主控件執行個體有自己的資源，例如記憶體、 控制代碼，以及執行緒集.NET 執行緒集區中。  
  
-   多個 BizTalk 主控件也會減少爭用，Messagebox 資料庫主應用程式佇列資料表，因為每一部主機指派其本身在 Messagebox 資料庫中的工作佇列資料表。  
  
-   節流是在 BizTalk Server 中實作主機層級。 這可讓您設定每個主控件節流特性不同。  
  
-   安全性被實作在主機層級;每個主控件是離散的 Windows 身分識別下執行。 這可讓您，比方說，以便 Host_A 存取 FileShare_B，同時不允許任何其他主機存取檔案共用。  
  
> [!NOTE]  
>  權益，以建立其他主控件執行個體時，也有缺點如果建立太多的主控件執行個體。 每個主控件執行個體是 Windows 服務 (BTSNTSvc.exe)，這會產生額外的負載，對 MessageBox 資料庫，並使用電腦資源 （例如 CPU、 記憶體、 執行緒）。  
  
 如需有關如何修改 BizTalk Server 主控件屬性的詳細資訊，請參閱 < 如何以修改主控件屬性 「 BizTalk Server 說明中在[ http://go.microsoft.com/fwlink/?LinkId=101588 ](http://go.microsoft.com/fwlink/?LinkId=101588)。  
  
## <a name="configure-a-dedicated-tracking-host"></a>設定專用的追蹤主控件  
 BizTalk Server 已針對輸送量最佳化的因此主要的協調流程和傳訊引擎執行不實際訊息直接移至 BizTalk 追蹤 」 或 「 BAM 資料庫，因為這會將轉向這些引擎從執行商務程序的主要工作。 相反地，BizTalk Server 會將訊息保留在 MessageBox 資料庫，並將其標示為需要移至 「 BizTalk 追蹤資料庫。 背景處理序 （追蹤主控件），然後移動訊息至 「 BizTalk 追蹤 」 及 「 BAM 資料庫。 追蹤會消耗資源的作業，因為個別的主控件應建立專門用來追蹤，所以可以盡可能降低追蹤對專用的主機，與訊息處理的影響。  
  
 使用專用的追蹤主控件也可讓您停止其他 BizTalk 主控件，而不會干擾 BizTalk Server 追蹤。 追蹤從 Messagebox 資料庫的資料移動是狀況良好的 BizTalk Server 系統的關鍵。 如果停止 BizTalk 主控件，負責移動 BizTalk 群組中的追蹤資料，將不會執行追蹤資料解碼服務。 影響如下所示：  
  
- HAT 追蹤資料會從 Messagebox 資料庫移動到 BizTalk 追蹤資料庫。  
  
- BAM 追蹤資料會從 Messagebox 資料庫移動至 BAM 主要匯入資料庫。  
  
- 資料不會移動，因為它無法從 Messagebox 資料庫刪除。  
  
- 追蹤資料解碼服務停止時，追蹤攔截器將仍會引發，並追蹤資料寫入 Messagebox 資料庫。 如果不移動資料，這會導致 Messagebox 資料庫變得過大，這樣會影響一段時間的效能。 即使自訂屬性不會受到追蹤，或是未設定 BAM 設定檔，預設情況下一些會追蹤資料 （例如管線接收 / 傳送事件和協調流程事件）。 如果您不要執行追蹤資料解碼服務，請關閉所有的追蹤，以便任何攔截器會將資料儲存至資料庫。 若要停用全域追蹤，請參閱 「 如何若要關閉全域追蹤 「 BizTalk Server 中協助在[ http://go.microsoft.com/fwlink/?LinkId=101589 ](http://go.microsoft.com/fwlink/?LinkId=101589)。 您可以使用 BizTalk Server 管理主控台來選擇性地停用追蹤事件。  
  
  追蹤主控件應至少兩個 （適用於在其中一個失敗的情況下的備援） 執行 BizTalk Server 的電腦上執行。 為了達到最佳效能，您應該有至少一個追蹤主控件執行個體，每個 Messagebox 資料庫。 追蹤主控件執行個體的實際數目應為 （N + 1），其中 N = Messagebox 資料庫數目。 "+ 1"為備援，萬一其中一部電腦裝載追蹤失敗。  
  
  追蹤主控件執行個體移動特定的 Messagebox 資料庫的追蹤資料，但是會永遠不會有一個以上的追蹤主控件執行個體特定的 Messagebox 資料庫移動資料。 例如，如果您有三個 Messagebox 資料庫，以及追蹤主控件執行個體的唯一兩個，然後其中一個主控件執行個體必須為兩個 Messagebox 資料庫移動資料。 新增第三個追蹤主控件執行個體分散追蹤裝載執行 BizTalk Server 的另一部電腦的工作。 在此案例中，加入第四個追蹤主控件執行個體不會發佈任何詳細的追蹤主控件運作，但會提供額外的追蹤主控件執行個體的容錯功能。  
  
  如需有關 BAM 事件匯流排服務的詳細資訊，請參閱 BizTalk Server 說明中的下列主題：  
  
- 在 「 管理 BAM 事件匯流排服務 「 [ http://go.microsoft.com/fwlink/?LinkId=101590 ](http://go.microsoft.com/fwlink/?LinkId=101590)。  
  
- 在 「 建立 BAM 事件匯流排服務的執行個體 」 [ http://go.microsoft.com/fwlink/?LinkId=101591 ](http://go.microsoft.com/fwlink/?LinkId=101591)。  
  
## <a name="manage-aspnet-thread-usage-or-concurrently-executing-requests-for-web-applications-that-host-orchestrations-published-as-a-web-or-wcf-service"></a>管理 ASP.NET 執行緒用法，或同時執行的 Web 應用程式主機的協調流程發佈為 Web 或 WCF 服務要求  
 背景工作和 I/O 執行緒 （IIS 6.0 和傳統模式中的 IIS 7.0） 或同時執行的 ASP.NET Web 應用程式裝載協調流程的要求 （IIS 7.0 整合模式） 的數字的數目會發行為 Web 服務應該在修改下列條件：  
  
-   CPU 使用率不是在裝載的 Web 伺服器上的瓶頸。  
  
-   值**ASP.NET 應用程式 v2.0.50727\Request Wait Time**或是**ASP.NET 應用程式 v2.0.50727\Request 執行時間**效能計數器是超乎尋常地高。  
  
-   類似於下列電腦裝載的 Web 應用程式的應用程式記錄檔中產生的錯誤：  
  
    ```  
    Event Type: Warning  
    Event Source: W3SVC Event Category: None  
    Event ID: 1013  
    Date: 6/4/2009  
    Time: 1:03:47 PM  
    User: N/A  
    Computer: <ComputerName>  
    Description: A process serving application pool 'DefaultAppPool' exceeded time limits during shut down. The process id was '<xxxx>'  
    ```  
  
### <a name="manage-aspnet-thread-usage-for-web-applications-that-host-orchestrations-on-iis-60-and-on-iis-70-running-in-classic-mode"></a>管理 ASP.NET 裝載協調流程以傳統模式執行的 IIS 7.0 和 IIS 6.0 上的 Web 應用程式的執行緒使用量  
 當**autoConfig** IIS 6.0 伺服器或傳統模式執行的 IIS 7.0 伺服器的 machine.config 檔案中的值設定為 **，則為 true**、 ASP.NET 2.0 管理背景工作執行緒數目，以及 I/O 執行緒是配置的任何相關聯的 IIS 背景工作處理序：  
  
```  
<processModel autoConfig="true" />  
```  
  
 若要以手動方式修改的背景工作角色和 ASP.NET 2.0 Web 應用程式的 I/O 執行緒數目，開啟相關聯的 machine.config 檔案，然後輸入新的值**maxWorkerThreads**和**maxIoThreads**參數：  
  
```  
<!-- <processModel autoConfig="true" /> -->  
    <processModel maxWorkerThreads="200" maxIoThreads="200" />  
```  
  
> [!NOTE]  
>  這些值是指導方針請確定您測試變更這些參數。  
  
 如需有關調整的 ASP.NET 2.0 Web 應用程式的 machine.config 檔案中參數的詳細資訊，請參閱 Microsoft 知識庫文章[821268"爭用、 效能不佳和死結，當您從 ASP.NET Web 服務要求應用程式](http://go.microsoft.com/fwlink/?LinkID=66483) (http://go.microsoft.com/fwlink/?LinkID=66483)。  
  
### <a name="manage-the-number-of-concurrently-executing-requests-for-web-applications-that-host-orchestrations-on-iis-70-running-in-integrated-mode"></a>管理並行執行裝載在 IIS 7.0 整合模式中執行的協調流程的 Web 應用程式的要求的數目  
 當在 IIS 7.0 上裝載 ASP.NET 2.0 整合模式中時，使用的執行緒的處理方式與在 IIS 6.0 或 IIS 7.0 上以傳統模式。 當在 IIS 7.0 上裝載 ASP.NET 2.0 整合模式中時，ASP.NET 2.0 會限制同時執行的數字**要求**而不是數目**執行緒**並行執行要求。 同步的情況下這會間接限制的執行緒數目，但針對非同步案例要求和執行緒的數目可能會非常不同。 在 IIS 7.0 上執行 ASP.NET 2.0，在整合式模式中，當**maxWorkerThreads**並**maxIoThreads** machine.config 檔案中的參數不會用來管理執行中執行緒的數目。 藉由修改指定的值，相反地，可以從 12 每一 CPU 的預設值已變更並行執行要求的數目**maxConcurrentThreadsPerCPU**。 **MaxConcurrentThreadsPerCPU** reqistry 或 aspnet.config 檔案的組態區段中，可以指定值。 請遵循下列步驟變更的預設值**maxConcurrentThreadsPerCPU**控管的並行執行的要求數目：  
  
 **若要在登錄中設定 maxConcurrentThreadsPerCPU 值**  
  
> [!WARNING]  
>  不當使用登錄編輯，可能會造成問題，需要重新安裝作業系統。 您必須自行負擔使用「登錄編輯程式」的風險。 有關如何備份、 還原和修改登錄的詳細資訊，請參閱 Microsoft 知識庫文章 < Microsoft Windows 登錄說明 >，網址[ http://go.microsoft.com/fwlink/?LinkId=62729 ](http://go.microsoft.com/fwlink/?LinkId=62729)。  
  
> [!NOTE]  
>  這項設定是全域的而且無法變更為個別的應用程式集區或應用程式。  
  
1. 按一下 **[開始]**、按一下 **[執行]**、輸入 **regedit.exe**，然後按一下 **[確定]** 以啟動「登錄編輯程式」。  
  
2. 瀏覽至**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0**  
  
3. 依照下列步驟中建立機碼：  
  
   1.  在上**編輯**功能表上，按一下**新增**，然後按一下 **金鑰**。  
  
   2.  型別**maxConcurrentThreadsPerCPU**，然後按**ENTER**。  
  
   3.  底下**maxConcurrentThreadsPerCPU**機碼，請建立 DWORD 項目與 maxConcurrentThreadsPerCPU 的新值。  
  
   4.  關閉 [登錄編輯程式]。  
  
   **若要設定的 aspnet.config 檔案的組態區段中的應用程式集區 maxConcurrentThreadsPerCPU 值**  
  
> [!NOTE]  
>  必須安裝 Microsoft.NET Framework 3.5 Service Pack 1，以容納透過組態檔設定下列值。 您可以下載 Microsoft.NET Framework 3.5 Service Pack 1 從[ http://go.microsoft.com/fwlink/?LinkID=136345 ](http://go.microsoft.com/fwlink/?LinkID=136345)。  
  
-   開啟應用程式集區的 aspnet.config 檔案，然後輸入新的值**maxConcurrentRequestsPerCPU**並**requestQueueLimit**參數：  
  
```  
<system.web>  
    <applicationPool maxConcurrentRequestsPerCPU="12" requestQueueLimit="5000"/>  
</system.web>  
```  
  
> [!NOTE]  
>  這個值會覆寫指定的值**maxConcurrentThreadsPerCPU**在登錄中。 RequestQueueLimit 設定等同於 processModel/requestQueueLimit，不同之處在於 aspnet.config 檔中的設定會覆寫 machine.config 檔案中的設定。  
  
## <a name="define-clr-hosting-thread-values-for-biztalk-host-instances"></a>定義的 CLR 裝載執行緒值，BizTalk 主控件執行個體  
 由於 Windows 執行緒是 Windows 程序可使用的最基本可執行單位，所以為與 BizTalk 主控件執行個體關聯的 .NET 執行緒集區配置足夠的執行緒，以避免執行緒不足，是很重要的。 若發生執行緒不足，沒有足夠的執行緒可用來執行要求之工作的效能受到負面影響。 同時，您也必須小心避免配置超出需要的執行緒給與主控件關聯的 .NET 執行緒集區。 與主機相關聯的.NET 執行緒集區過多執行緒配置可能會增加內容切換。 Windows 核心切換到不同的執行緒，會產生效能成本執行一個執行緒時，就會發生內容切換。 過多的執行緒配置可能會導致內容切換過多，這會造成負面影響整體效能。  
  
 修改 Windows 登錄 BizTalk server 中建立適當的 CLR 裝載值相關聯的 BizTalk 主控件執行個體的.NET 執行緒集區中可用的執行緒數目。  
  
> [!WARNING]  
>  不當使用登錄編輯，可能會造成問題，需要重新安裝作業系統。 您必須自行負擔使用「登錄編輯程式」的風險。 有關如何備份、 還原和修改登錄的詳細資訊，請參閱 Microsoft 知識庫文章 < Microsoft Windows 登錄說明 >，網址[ http://go.microsoft.com/fwlink/?LinkId=62729 ](http://go.microsoft.com/fwlink/?LinkId=62729)。  
  
> [!NOTE]  
>  **背景工作執行緒**用來處理已排入佇列的工作項目和**I/O 執行緒**會處理已完成的非同步 I/O 要求 I/O 完成連接埠相關聯的專用的回呼執行緒。  
  
 **若要修改與每個 BizTalk 主控件執行個體相關聯的.NET 執行緒集區中可用的執行緒數目，請遵循下列步驟：**  
  
1. 停止 BizTalk 主控件執行個體。  
  
2. 按一下 **[開始]**、按一下 **[執行]**、輸入 **regedit.exe**，然後按一下 **[確定]** 以啟動「登錄編輯程式」。  
   瀏覽至**HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc$**<em>hostname</em>] 其中*hostname*是與主機關聯的主控件的名稱執行個體。  
  
   > [!NOTE]  
   >  如果您已從 BizTalk Server 2004 升級您的 BizTalk Server 2006 安裝，此登錄機碼可表示為 **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc * * * guid*] 其中*guid*是 BizTalk Server 主控件的每個執行個體的唯一 GUID。  
  
3. 找出**CLR 裝載**索引鍵。 如果此索引鍵不存在，然後依照下列步驟建立機碼：  
  
   1.  在上**編輯**功能表上，按一下**新增**，然後按一下 **金鑰**。  
  
   2.  型別**CLR 裝載**，然後按**ENTER**。  
  
4. 底下**CLR 裝載**機碼，請建立下列 DWORD 項目，以指示的值。  
  
   |DWORD 項目|預設值|建議值|  
   |-----------------|-------------------|-----------------------|  
   |MaxIOThreads|20|100|  
   |MaxWorkerThreads|25|100**重要事項：** 增加此值超過 100 可以裝載 BizTalk Server MessageBox 資料庫的 SQL Server 電腦的效能造成不良的影響。 發生此問題時，SQL Server 可能會發生鎖死的情況。 建議您使用此參數不增加超過 100 的值。|  
   |MinIOThreads|@shouldalert|25|  
   |MinWorkerThreads|@shouldalert|25|  
  
   > [!NOTE]  
   >  這些建議值會足以應付大部分的情況，但可能需要增加取決於在每個主控件執行個體中執行幾個配接器處理常式或協調流程。  
  
   > [!NOTE]  
   >  這些值會以隱含方式乘以伺服器上的處理器數目。 例如，將 MaxWorkerThreads 項目的值設為 100，就會有效將 4 CPU 伺服器上的值設為 400。  
  
5. 關閉 [登錄編輯程式]。  
  
6. 重新啟動 BizTalk 主控件執行個體。  
  
## <a name="disable-tracking-for-orchestrations-send-ports-receive-ports-and-pipelines-when-tracking-is-not-required"></a>停用追蹤的協調流程、 傳送埠、 接收埠及管線，不需要追蹤時  
 追蹤時產生的資料已寫入 MessageBox 資料庫，並以非同步方式移動到 BizTalk 追蹤資料庫的 BizTalk Server 中的額外負荷的效能。 如果追蹤不是一項業務需求，則會停用追蹤，以減少額外負荷，並提高效能。 如需設定追蹤的詳細資訊，請參閱 「 設定追蹤使用 BizTalk Server 管理主控台 」 在 BizTalk Server 在幫助[ http://go.microsoft.com/fwlink/?LinkID=106742 ](http://go.microsoft.com/fwlink/?LinkID=106742)。  
  
## <a name="decrease-the-purging-period-for-the-dta-purge-and-archive-job-from-7-days-to-2-days-in-high-throughput-scenarios"></a>DTA 清除與封存工作從 7 天 2 天在高輸送量情況下減少清除的期間  
 根據預設，在 BizTalk Server 中追蹤資料的清除間隔設為 7 天。 在高輸送量情況下，這可能會造成在追蹤資料庫中，最終會影響 MessageBox 和依次造成負面影響訊息處理輸送量的效能資料過多組建設定中。  
  
 在高輸送量情況下，減少硬性和軟性清除從預設的 7 天的間隔為 2 天。 如需有關設定清除間隔的詳細資訊，請參閱 < 如何以設定 DTA 清除和封存工作 > 在 BizTalk Server 在幫助[ http://go.microsoft.com/fwlink/?LinkID=104908 ](http://go.microsoft.com/fwlink/?LinkID=104908)。  
  
## <a name="install-the-latest-service-packs"></a>安裝最新的 service pack  
 應該安裝最新的 service pack，BizTalk Server 和.NET Framework，因為其中包含可以修正您可能會遇到效能問題的修正程式。  
  
## <a name="do-not-cluster-biztalk-hosts-unless-absolutely-necessary"></a>除非未叢集化 BizTalk 主控件絕對必要  
 雖然[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]與後續版本的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可讓您將 BizTalk 主控件設定為叢集資源，您應該只考慮這麼做，如果您需要提供無法跨多個 BizTalk 裝載資源的高可用性電腦。 因為範例中，使用 FTP 配接器的連接埠應該只能位於一個主控件執行個體，因為 FTP 通訊協定不提供檔案鎖定，不過，這會導致失敗會受益於叢集單一的點。 包含配接器，例如檔案、 SQL、 HTTP 或處理僅主機的主機可以在內部負載平衡跨機器，並不會受益於叢集。  
  
## <a name="performance-optimizations-in-the-biztalk-server-documentation"></a>在 BizTalk Server 文件中的效能最佳化  
 適用於從 BizTalk Server 文件，視下列建議：  
  
-   在 「 疑難排解 MessageBox 延遲問題 」 [http://go.microsoft.com/fwlink/?LinkId=114747](http://go.microsoft.com/fwlink/?LinkId=114747)  
  
-   在 「 識別效能瓶頸" [http://go.microsoft.com/fwlink/?LinkID=104418](http://go.microsoft.com/fwlink/?LinkID=104418)  
  
-   在 「 避免 DBNETLIB 例外狀況 」 [http://go.microsoft.com/fwlink/?LinkID=108787](http://go.microsoft.com/fwlink/?LinkID=108787)  
  
-   在 「 避免 TCP/IP 連接埠耗盡" [http://go.microsoft.com/fwlink/?LinkID=101610](http://go.microsoft.com/fwlink/?LinkID=101610)  
  
-   在 「 設定 EPM 執行緒集區大小 」 [http://go.microsoft.com/fwlink/?LinkId=114748](http://go.microsoft.com/fwlink/?LinkId=114748)