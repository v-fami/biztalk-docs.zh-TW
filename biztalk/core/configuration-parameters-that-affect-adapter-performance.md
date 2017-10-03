---
title: "影響配接器效能的組態參數 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90bbb9fb-0b31-45f0-a54c-7b2025e653b9
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46bbb5a1c796149f762ce438aed7df5c256bf465
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuration-parameters-that-affect-adapter-performance"></a>影響配接器效能的組態參數
本節說明可能影響 BizTalk Server 配接器效能的組態設定。  
  
## <a name="clr-hosting-thread-values-for-the-host"></a>主控件的 CLR 裝載執行緒值  
 由於 Windows 執行緒是 Windows 程序可使用的最基本可執行單位，所以為與 BizTalk 主控件執行個體關聯的 .NET 執行緒集區配置足夠的執行緒，以避免執行緒不足，是很重要的。 若發生執行緒不足，就沒有足夠的執行緒可用來執行要求的工作，而導致效能受到負面影響。 同時，應該小心避免配置更多執行緒相關聯的主機，而不是必要的.NET 執行緒集區。 配置過多執行緒給與主控件關聯的 .NET 執行緒集區可能會增加內容切換，而導致整體效能也受到負面影響。 Windows 核心從執行一個執行緒切換到不同的執行緒，而造成 CPU 頻繁作業時，會發生內容切換。  
  
 請在 BizTalk Server 設定儀表板中設定適當的值，修改與 BizTalk 主控件執行個體關聯的 .NET 執行緒集區中可用的 Windows 執行緒數目。 如需有關如何修改.NET CLR 值的詳細資訊，請參閱[如何修改.NET CLR 設定](http://msdn.microsoft.com/library/ff629681\(v=BTS.70\).aspx)。  
  
## <a name="aspnet-settings-that-can-impact-http-or-soap-adapter-performance"></a>可能影響 HTTP 或 SOAP 配接器效能的 ASP.NET 設定  
 下列設定可以套用至 ASP.NET 應用程式裝載 Web 應用程式的 HTTP 或 SOAP 配接器進行通訊。 在裝載 Web 應用程式伺服器的 web.config 或 machine.config 檔中設定這些參數。 請修改這些設定，以配合您 HTTP 或 SOAP 配接器傳送埠所產生的負載。 如需有關這些設定的詳細資訊，請參閱[競爭、 效能不佳和死結，當您從 ASP.NET 應用程式的 Web 服務要求](http://go.microsoft.com/fwlink/p/?LinkId=196842)。  
  
|**參數**|**組態檔區段**|**預設值**|**建議的值**|  
|-------------------|---------------------------------------|-----------------------|---------------------------|  
|**minFreeThreads**<br /><br /> 允許執行新要求的最低可用執行緒數目。 ASP.NET 會為需要更多執行緒才能完成處理的要求，保留這個數目的可用執行緒。|\<httpRuntime >|8|88 * 裝載 Web 應用程式之伺服器上的處理器數目。|  
|**minFreeLocalRequestFreeThreads**<br /><br /> ASP.NET 為允許執行新的本機要求，所保留的最低可用執行緒數目。 這個執行緒數目是為來自本機主機的要求所保留，以防有些要求在處理期間發出子要求至本機主機。 這麼一來便能避免遞迴重新進入 Web 伺服器的可能死結。|\<httpRuntime >|4|76 * 裝載 Web 應用程式的伺服器上的處理器數目。|  
|**executionTimeout**<br /><br /> 指示由 ASP.NET 自動關閉之前允許執行要求的秒數上限。|\<httpRuntime >|90|90|  
|**maxconnection**<br /><br /> 決定特定 IP 位址可執行的連線數目。|\<connectionManagement >|2<br /><br /> 此設定的值為 2，符合 HTTP 1.1 規格的 IETF RFC 且適合使用者實例，但並未針對高輸送量最佳化。|12 * 裝載 Web 應用程式的伺服器上的處理器數目。|  
|**maxWorkerThreads**<br /><br /> 設定每一 CPU 用於處理序的最大工作者執行緒數量。|\<processModel >|20|100**附註：**這個值會以隱含方式乘以伺服器上的處理器數目。|  
|**minWorkerThreads**|\<processModel >|1|**maxWorkerThreads** / 2**附註：** minWorkerThreads 參數不是預設組態檔中。 您必須自行新增。 **注意：**這個值會以隱含方式乘以伺服器上的處理器數目。|  
|**maxIoThreads**<br /><br /> 由 ASP.NET 使用，以限制完成執行緒使用的數目。|\<processModel >|20|100<br /><br /> 此值會以隱含的方式乘以伺服器上的處理器數目。|  
  
 如果裝載 Web 服務的電腦執行 ASP.NET 2.0 或更新版本，則您可以將**autoConfig = true**自動設定以下設定，以達到最佳的 Machine.config 檔案的 processModel 區段中根據機器組態的效能：  
  
-   **MaxWorkerThreads**屬性。  
  
-   **MaxIoThreads**屬性。  
  
-   **MinFreeThreads** httpRuntime 項目的屬性。  
  
-   **MinLocalRequestFreeThreads** httpRuntime 項目的屬性。  
  
-   **MaxConnection**屬性\<connectionManagement > 項目 （網路設定） 項目。  
  
> [!NOTE]
>  **ProcessModel**區段可以設定只有在 Machine.config 檔案內，而且會影響所有伺服器執行的 ASP.NET 應用程式。  
  
 如需有關**processModel** machine.config 檔案的項目，請參閱 Microsoft MSDN 網站，網址[http://go.microsoft.com/fwlink/p/?LinkId=62307](http://go.microsoft.com/fwlink/p/?LinkId=62307)。  
  
## <a name="registry-setting-that-governs-the-tcp-window-size"></a>管理 TCP 視窗大小的登錄設定  
 以下登錄設定可控制 TCP 視窗大小，也就是連線期間可緩衝的接收資料數量 (以位元組為單位)。 如果此參數為設為最佳值，則配接器效能可能會受到負面影響。 請實作此登錄設定，增加 TCP 視窗大小。  
  
> [!WARNING]
>  不當使用「登錄編輯程式」可能會導致嚴重的問題，甚至必須重新安裝作業系統。 Microsoft 不保證可以解決您不當使用「登錄編輯程式」所導致的問題。 您必須自行負擔使用「登錄編輯程式」的風險。 在修改登錄前，請務必備份登錄，並確認您瞭解在問題發生時如何還原備份。  
  
 若要增加預設的 TCP 視窗大小，請遵循下列步驟：  
  
1.  按一下 **[開始]**、按一下 **[執行]**、輸入 **regedit.exe**，然後按一下 **[確定]** 以啟動「登錄編輯程式」。  
  
     瀏覽至**HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\\**  
  
2.  在下**參數**索引鍵，以指示的值建立下列 DWORD 項目。  
  
    |DWORD 項目|預設值|建議值|  
    |-----------------|-------------------|-----------------------|  
    |**TcpWindowSize**<br /><br /> 此設定會決定電腦的最大 TCP 接收視窗大小。 接收視窗指定傳送者不需收到通知就可傳送的位元組數目。 一般而言，較大的接收視窗可透過高頻寬網路改善效能。|17520|設定為的乙太網路最大區段大小 (MSS) 1460 上限為 64240 的倍數。 若使用的是 Windows 縮放，則設定為上限 65535。|  
  
    > [!NOTE]
    >  您必須重新啟動電腦，這些變更才會生效。  
  
3.  關閉 [登錄編輯程式]。  
  
## <a name="see-also"></a>另請參閱  
 [效能和容量規劃](../core/performance-and-capacity-planning.md)