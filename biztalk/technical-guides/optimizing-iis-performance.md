---
title: 最佳化 IIS 效能 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6722a2ee-3704-4aaa-9b0d-cef97bcb9a04
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad8db99f2f6d26b05960950376e30faaa5a2155d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971447"
---
# <a name="optimizing-iis-performance"></a>最佳化 IIS 效能
## <a name="apply-iis-configuration-options-to-improve-iis-performance"></a>套用 IIS 組態選項，以改善 IIS 效能  
 Internet Information Services (IIS) 會公開多個會影響 IIS 效能的組態參數。 本主題說明其中幾個參數，並提供一般指導方針來設定參數值，以改善 IIS 效能。  
  
### <a name="log-only-essential-information-or-completely-disable-iis-logging"></a>記錄重要的資訊，或完全停用 IIS 記錄  
 IIS 記錄應該最小化，或甚至在生產環境中停用。 若要停用記錄，請遵循下列步驟：  
  
1.  按一下 **開始**，指向**所有程式**，按一下 **系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.  
  
2.  中**連線**窗格中，按一下以展開**站台**，按一下以選取，您想要停用記錄，按一下以選取的網站**功能檢視**，然後按兩下**記錄**功能。  
  
3.  按一下 **停用**中**動作**窗格，即可停用此網站的記錄。  
  
### <a name="disable-iis-asp-debugging-in-production-environments"></a>停用在生產環境中的 IIS 的 ASP 偵錯  
 IIS 的 ASP 偵錯應該在生產環境中停用。 若要停用 IIS ASP 偵錯請遵循下列步驟： 在**連線**窗格中，按一下以展開**站台**，按一下以選取網站，您想要停用 ASP 偵錯，請按一下以選取**功能檢視**，然後按兩下**ASP**功能。 按一下以展開**編譯**，按一下以展開**偵錯屬性**，並確認兩者**啟用用戶端偵錯**並**啟用伺服器端偵錯**設定為**False**。  
  
1. 按一下 **開始**，指向**所有程式**，按一下 **系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.  
  
2. 中**連線**窗格中，按一下以展開**站台**，按一下以選取，您想要停用 ASP 偵錯，請按一下以選取的網站**功能檢視**，然後按兩下**ASP**功能。  
  
3. 按一下以展開**編譯**，按一下以展開**偵錯屬性**，並確認兩者**啟用用戶端偵錯**並**啟用伺服器端偵錯**設定為**False**。  
  
4. 如果有必要，請按一下**套用**中**動作**窗格。  
  
   停用偵錯 ASP.NET 應用程式和 Web 服務，藉由指定\<debug ="false"\> web 應用程式的 web.config 檔案中的一節。  
  
### <a name="tune-the-value-of-the-asp-threads-per-processor-limit-property"></a>調整每個處理器限制 ASP 的執行緒屬性的值  
 ASP**執行緒每個處理器限制**屬性會指定每個處理器的 IIS 建立的背景工作執行緒的數目上限。 增加值處理器限制每個執行緒，直到處理器使用率符合至少 50%，或更新版本。 這項設定可以大幅影響您的 Web 應用程式的延展性和伺服器的效能一般。 因為這個屬性會定義可以同時執行的 ASP 要求的數目上限，這項設定應該保持為預設值，除非您的 ASP 應用程式正在擴充外部元件呼叫。 在此情況下，您可能會增加處理器限制每個執行緒的值。 這樣做可讓要建立更多執行緒來處理更多的並行要求的伺服器。 處理器限制每個執行緒的預設值為 25。 這個屬性的最大建議的值為 100。  
  
 增加處理器限制每個執行緒的值請遵循下列步驟： 在**連線**窗格中，選取 web 伺服器，按一下以選取**功能檢視**，然後按兩下**ASP**功能。  
  
1. 按一下 **開始**，指向**所有程式**，按一下 **系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.  
  
2. 在**連線**窗格中，選取 web 伺服器，按一下以選取**功能檢視**，然後按兩下**ASP**功能。  
  
3. 按一下以展開**限制內容**下方**行為**，按一下 **執行緒每個處理器限制**，輸入所需的值**執行緒每個處理器限制** ，按一下 **套用**中**動作**窗格。  
  
   如需有關如何修改中的屬性\<限制\>元素的 IIS 7.5/7.0 \<asp\>項目，請參閱[ASP 限制\<限制\>](http://go.microsoft.com/fwlink/?LinkId=157483) (http://go.microsoft.com/fwlink/?LinkId=157483).  
  
> [!NOTE]  
>  這個屬性只能套用在伺服器層級，因為此屬性的修改會影響在伺服器執行的所有網站。  
  
### <a name="tune-the-value-of-the-asp-queue-length-property"></a>微調 ASP Queue Length 屬性的值  
 微調此屬性的目標是要確保良好的回應時間降至最低 ASP 要求佇列已滿時，伺服器頻率將 HTTP 503 （伺服器忙碌中） 錯誤傳送給用戶端。 如果 ASP Queue Length 屬性的值太低時，伺服器會傳送 HTTP 503 錯誤，以較高頻率。 如果 ASP Queue Length 屬性的值太高，使用者可能會察覺到伺服器沒有回應時事實上其要求正在等候佇列中。 從佇列觀看高流量的時段中，您應該分辨出 web 要求的尖峰和離峰期的模式。 請記下的尖峰值，並將尖峰值的正上方的 ASP Queue Length 屬性值。 使用佇列來處理短期需求高峰，請確定回應時間和節流系統，以避免多載時持續，就會發生未預期的尖峰。 如果您沒有適用於調整的 ASP Queue Length 屬性的資料，很好的起點會將佇列一對一比率設為執行緒總數。 例如，如果每個處理器限制 ASP 的執行緒屬性設定為 25，且您有四個處理器 (4 * 25 = 100 執行緒)、 ASP Queue Length 屬性設定為 100，及從該處微調。  
  
 若要增加佇列長度的值屬性，請遵循下列步驟：  
  
1. 按一下 **開始**，指向**所有程式**，按一下 **系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.  
  
2. 在**連線**窗格中，選取 Web 伺服器，按一下以選取**功能檢視**，然後按兩下**ASP**功能。  
  
3. 按一下以展開**限制內容**下方**行為**，按一下 **佇列長度**，輸入所需的值**佇列長度**，然後按一下 **套用**中**動作**窗格。  
  
   如需有關如何修改中的屬性\<限制\>元素的 IIS 7.5/7.0 \<asp\>項目，請參閱[ASP 限制\<限制\>](http://go.microsoft.com/fwlink/?LinkId=157483) (http://go.microsoft.com/fwlink/?LinkId=157483).  
  
> [!NOTE]  
>  這個屬性只能套用在伺服器層級，因為此屬性的修改會影響在伺服器執行的所有網站。  
  
### <a name="tune-the-maxpoolthreads-registry-entry"></a>微調 MaxPoolThreads 登錄項目  
 此設定會指定每個處理器建立的集區執行緒的數目。 執行緒集區監看的網路要求和處理內送要求。 MaxPoolThreads 計數不包含 ISAPI 應用程式所耗用的執行緒。 一般而言，您不應建立 20 個以上的執行緒，每個處理器。 MaxPoolThreads 是位於 HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\InetInfo\Parameters\，預設值為 4 的 REG_DWORD 登錄項目。  
  
### <a name="disable-wcf-services-tracing"></a>停用追蹤的 WCF 服務  
 若要停用追蹤在生產環境中的 WCF 服務使用組態編輯器工具 (SvcConfigEditor.exe)。 如需有關組態編輯器工具的詳細資訊，請參閱[組態編輯器工具 (SvcConfigEditor.exe)](http://go.microsoft.com/fwlink/?LinkID=127070) (http://go.microsoft.com/fwlink/?LinkID=127070)。  
  
### <a name="configure-aspnet-20-maxconcurrentrequests-for-iis-7570-integrated-mode"></a>設定 ASP.NET 2.0 MaxConcurrentRequests 針對 IIS 7.5/7.0 整合模式  
 當 ASP.NET 2.0 裝載在 IIS 7.5/7.0 整合模式中時，使用的執行緒的處理方式與在 IIS 7.5/7.0 中傳統模式。 當 ASP.NET 2.0 裝載在 IIS 7.5 整合模式中時，ASP.NET 2.0 會限制並行執行要求，而非並行執行要求的執行緒數目的數目。 同步的情況下，這間接會限制數目的執行緒因為要求的數目會與執行緒的數目相同。 但非同步案例中，要求和執行緒的數目可能會非常不同，因為您可能有更多的要求，比執行緒。 當您執行 ASP.NET 2.0 上 IIS 7.5 整合模式中時，會忽略 minFreeThreads 和 88n,minlocalrequestfreethreads 的 machine.config 中的"h"項目。 IIS 7.5 整合模式中，名為 MaxConcurrentRequestsPerCPU 內 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0 DWORD 會判斷每一 CPU 的並行要求數目。 根據預設，登錄機碼不存在，因此每一 CPU 的要求數目限制為 12 個。 .NET framework 3.5 SP1 包含 v2.0 二進位檔的支援設定的 IIS 應用程式集區透過 aspnet.config 檔案更新。 此設定僅適用於整合式模式 （傳統/ISAPI 模式會忽略這些設定）。新的 aspnet.config 組態區段，使用預設值如下：  
  
```  
<system.web>  
   <applicationPool maxConcurrentRequestsPerCPU="12" maxConcurrentThreadsPerCPU="0" requestQueueLimit="5000"/>  
</system.web>  
```  
  
 在 IIS 7.5 整合模式下，maxWorkerThreads 和 maxIoThreads 參數中的 < processModel 」 一節，machine.config 檔案不會用來控管本身，執行要求的數目，但它們仍用來控管的 CLR 執行緒集區大小使用 ASP.NET。 當 machine.config 的 < processModel 」 一節會有"autoConfig = true"（這是預設值），這可讓應用程式集區最多 100 個背景工作執行緒 (MaxWorkerThreads) 每個邏輯 CPU。 因此商用伺服器含有 2 個雙核心 Cpu 一般會有 400 MaxWorkerThreads。 這應該足以應付最嚴苛的應用程式。  
  
 如需在 IIS 7.5 上設定 ASP.NET 執行緒用法的詳細資訊，請參閱[Thomas Marquardt 部落格上的 IIS 7.0 上的 ASP.NET 執行緒用法](http://go.microsoft.com/fwlink/?LinkId=157518)(http://go.microsoft.com/fwlink/?LinkId=157518)。  
  
### <a name="configure-aspnet-4-maxconcurrentrequests-for-iis-7570-integrated-mode"></a>設定 ASP.NET 4 MaxConcurrentRequests 針對 IIS 7.5/7.0 整合模式  
 使用.NET Framework 4，maxConcurrentRequestsPerCPU 的預設值為 5000，這是一個非常大的數字，因此將允許足夠的同時執行的非同步要求。 如需詳細資訊，請參閱 < [ \<applicationPool\>項目 （Web 設定）](http://go.microsoft.com/fwlink/?LinkID=205339) (http://go.microsoft.com/fwlink/?LinkID=205339)。  
  
 IIS 7.5/7.0 整合模式中，名為 MaxConcurrentRequestsPerCPU 內 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\4.0.30319.0 DWORD 會判斷每一 CPU 的並行要求數目。 根據預設值，登錄機碼不存在，因此每一 CPU 的要求數目限制為 5000。  
  
### <a name="enable-iis-http-compression"></a>啟用 IIS HTTP 壓縮  
 若要更有效率地使用可用的頻寬，可讓 IIS HTTP 壓縮。 HTTP 壓縮 」 提供啟用壓縮的瀏覽器與 IIS 之間更快的傳輸時間，不論是否從本機儲存體或 UNC 資源會提供您的內容。  
  
-   **若要設定 Web 伺服器層級的壓縮：**  
  
    1.  按一下 **開始**，指向**所有程式**，按一下 **系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.  
  
    2.  在**連線**窗格中，選取 Web 伺服器，按一下以選取**功能檢視**，然後按兩下**壓縮**功能。  
  
    3.  設定所要的壓縮選項，然後按一下 **套用**中**動作**窗格。  
  
-   **若要在網站層級設定壓縮：**  
  
    1.  按一下 **開始**，指向**所有程式**，按一下 **系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.  
  
    2.  在**連線**窗格中，按一下以展開**站台**，按一下以選取，您想要設定壓縮，請按一下以選取的網站**功能檢視**，和然後按兩下**壓縮**功能。  
  
    3.  設定所要的壓縮選項，然後按一下 **套用**中**動作**窗格。  
  
## <a name="see-also"></a>另請參閱  
 [最佳化效能](../technical-guides/optimizing-performance.md)