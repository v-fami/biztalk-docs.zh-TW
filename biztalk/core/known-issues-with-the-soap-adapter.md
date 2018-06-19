---
title: SOAP 配接器的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a3229d73-170d-42b7-bab9-12ae5f2d0fa7
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 671510c6901fc399580ab73018e67eadc86f7212
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262846"
---
# <a name="known-issues-with-the-soap-adapter"></a>SOAP 配接器的已知問題
本節包含可幫助您避免錯誤的資訊。  
  
## <a name="known-issues"></a>已知問題  
  
#### <a name="the-soap-adapter-experiences-poor-performance-or-generates-errors-under-load"></a>SOAP 配接器在負載下遭遇效能不佳的情況，或產生錯誤。  
  
##### <a name="problem"></a>問題  
 SOAP 配接器在負載下遭遇效能不佳的情況，或產生錯誤。  
  
##### <a name="cause"></a>原因  
 這個問題發生的原因，是因為 SOAP 配接器或影響 SOAP 配接器之相依性元件的預設組態選項未針對負載下的效能進行微調。  
  
##### <a name="resolution"></a>解決方案  
 若要解決此問題，請修改 SOAP 配接器或相依性元件 > 主題所述的組態選項[組態參數會影響配接器效能](../core/configuration-parameters-that-affect-adapter-performance.md)。  
  
#### <a name="the-mimesmime-encoder-and-decoder-pipeline-components-cannot-encode-and-decode-data-processed-by-the-soap-adapter"></a>MIME/SMIME 編碼器和解碼器管線元件無法編碼和解碼 SOAP 配接器所處理的資料  
  
##### <a name="problem"></a>問題  
 MIME/SMIME 編碼器和解碼器管線元件無法編碼和解碼 SOAP 配接器所處理的資料  
  
##### <a name="cause"></a>原因  
 這個問題發生的原因，是因為 SOAP 配接器在程序的配接器階段組合和解譯了 SOAP 訊息。  
  
##### <a name="resolution"></a>解決方案  
 若要解決這個問題，請使用安全通訊端層 (SSL) 確保通訊安全，以編碼 SOAP 配接器處理的訊息。 在傳送端，使用**用戶端憑證指紋**為了達成此目的的 SOAP 配接器屬性頁面中的屬性。 在接收端，您必須設定裝載 BizTalk Web 服務的虛擬目錄，以取得安全的 SSL 通訊。  
  
#### <a name="the-default-appdomain-hosting-the-soap-adapter-gets-unloaded-causing-the-host-process-to-hang"></a>裝載 SOAP 配接器的預設 AppDomain 卸載，造成主控件處理序沒有反應  
  
##### <a name="problem"></a>問題  
 裝載 SOAP 配接器的處理序沒有反應，造成此處理序中的所有其他 Web 服務也沒有反應。 這可能產生下列錯誤：  
  
 執行回應 （傳送） 管線失敗:"未知"來源:"未知"接收連接埠:: TwoWayLatencyLoopBack_RxPort"URI:"/ /twowaylatencyrxsoap/twowaylatencyws.asmx"原因： 嘗試存取未載入的 AppDomain。  
  
##### <a name="cause"></a>原因  
 SOAP 配接器在 IIS 處理序空間中執行。 如果 IIS AppPool 中有一個以上的 Web 服務存在，則每一個 Web 服務最後都會有它自己的 AppDomain。  
  
 根據預設，所有傳訊引擎物件會建立第一個 AppDomain 中 （也就是。 AppDomain 對應到第一個 Web 服務)。 如果第一個 Web 服務因為任何原因而停止作用一段時間，則 IIS 會卸載第一個 AppDomain。 當發生這個情況時，裝載處理序中的所有服務都會無法使用。  
  
##### <a name="resolution"></a>解決方案  
 若要避免卸載 AppDomain，請遵循下列程序：  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk Server** ，然後按一下  **BizTalk Server 管理**。  
  
2.  在**BizTalk Server 管理主控台**，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後按一下 **主機**。  
  
3.  從清單中的主機，必要的主機，以滑鼠右鍵按一下，然後按一下 **設定**。  
  
4.  在**BizTalk 設定儀表板**，檢查**外掛式配接器的預設應用程式定義域**下**一般** 索引標籤。  
  
 當您這樣做時，會在預設 AppDomain 中建立 BizTalk 傳訊引擎物件，而不是在其自己的 AppDomain 中建立。 因為預設 AppDomain 絕對不會卸載，所以此問題將不再發生。  
  
#### <a name="the-soap-adapter-fails-to-register"></a>SOAP 配接器無法註冊  
  
##### <a name="problem"></a>問題  
 當 BizTalk Server 嘗試註冊 SOAP (或 HTTP) 配接器時，可能發生下列錯誤。  
  
 "傳訊引擎無法註冊配接器 "SOAP"。 詳細資料: 「 註冊相同的程序內的多個介面卡型別不是支援的案例。 例如，HTTP 與 SOAP 接收配接器不能共存於相同的程序中"。  
  
 或  
  
 "傳訊引擎無法註冊配接器 "HTTP"。 詳細資料: 「 註冊相同的程序內的多個介面卡型別不是支援的案例。  例如，HTTP 與 SOAP 接收配接器不能共存於相同的程序中"。  
  
##### <a name="cause"></a>原因  
 當您在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] / IIS 6.x 上執行 [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 時，SOAP 和 HTTP 配接器無法在相同的處理序空間或應用程式集區中執行。  
  
##### <a name="resolution"></a>解決方案  
 如果安裝需要在相同的 Web 伺服器上使用 SOAP 和 HTTP 配接器，則必須針對每一個配接器建立個別的應用程式集區。  一旦建立之後，就會將每一個配接器的虛擬目錄指派給不同的應用程式集區。  
  
> [!NOTE]
>  這個問題不會發生在 Windows XP 上，因為在這些作業系統上，SOAP 和 HTTP 配接器是在 IIS 5.x 之下的不同處理序空間中執行。  SOAP 配接器在 aspnet_wp.exe 處理序中會當做 ASP.Net 應用程式來執行；  HTTP 配接器則是在 dllhost.exe 的專用處理序空間中執行。  因此，將這兩個配接器隔離，就可讓它們並行於相同的 Web 伺服器上執行。  
  
## <a name="see-also"></a>另請參閱  
 [SOAP 配接器疑難排解](../core/troubleshooting-the-soap-adapter.md)