---
title: 管理和監視 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92724f79-32bb-40d3-a0af-147aba00d87e
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b24c5bd1fcc1d2e81f50221c6c1e148d22394d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264462"
---
# <a name="management-and-monitoring"></a>管理與監控
在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 引擎上建置的每個應用程式都必須加以管理。 如何安裝新應用程式？ 有什麼可能的組態？ 現在系統內部發生了什麼問題？ 此部分針對這些工具回答以上問題。  
  
## <a name="installing-biztalk-server"></a>安裝 BizTalk Server  
 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含數個元件，且依賴 Windows 環境的多個方面。 請確定已備妥產品所需的正確版本，否則不容易正確安裝所有的產品元件。  
  
 安裝工作其實十分簡單。 從 BizTalk Server 2009 升級的作業會自動進行，且舊版組建的所有項目 (協調流程、對應等等) 都會繼續正常運作。 若要確定正確的環境存在，安裝新 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的系統管理員可以下載標準的 .CAB 檔或參考之前已下載的可用 .CAB 檔。 無論是哪一種情形，這個檔案都包含安裝產品所需的可轉散發元件。 這包含 Microsoft Data Access Components (MDAC) 與 Microsoft XML Parser (MSXML) 的正確版本、最新的安全性 Hot Fix 及其他需要的軟體。  
  
 之後此內容。封包檔已安裝，有兩個主要選項可安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]本身。 預設的方式，通常是何種開發人員建立[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境供自己使用，可能會安裝所有產品的元件，在單一帳戶之下一部電腦上。 程序開始後，開發人員只需在一旁觀看安裝進度即可。 在系統管理員設定生產[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中，相較之下，可以使用自訂組態選項。 這個選項可將產品部署在不同機器上，定義並使用不同帳戶及其他更詳細的組態。  
  
## <a name="creating-scalable-configurations"></a>建立可調整的組態  
 如果高可用性或備援不是需求，將整個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]引擎可以安裝在同一部電腦。 不過在某些情況下，這不是適當的解決方案。 可能引擎必須處理的訊息數目對於一台電腦來說太多，或者需要備援讓系統更可靠。 若要符合需求，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]數種方式可以部署引擎。  
  
 部署引擎的基礎概念是主控件的構思。 主控件可以包含各種項目，包括協調流程、配接器以及管線。 不過主控件只是邏輯的建構。 若要使用主控件，BizTalk Server 系統管理員必須建立主控件執行個體。 每一個主控件執行個體都是一個 Windows 程序，而且可以包含各種項目，如下圖所示。 如範例所示，機器 A 是兩個主控件執行個體的主控所。 一個包含接收配接器及接收管線，而另一個包含協調流程 P 及 Q。機器 B 只執行一個主控件執行個體，另包含兩個協調流程 P 及 Q。機器 C 和機器 A 一樣，是兩個執行個體的主控所，但是這兩個執行個體都不包含協調流程。 反之，每一個執行個體都包含不同的傳送管線和傳送配接器。 最後，電腦 D 儲存此組態中所有主控件執行個體使用的 MessageBox 資料庫。  
  
 ![](../core/media/understandingbts-09-hosts.gif "UnderstandingBTS_09_Hosts")  
  
 此範例說明多個使用主控件的方法。 比方說，因為這兩部電腦 A 和 B 是主要的協調流程 P 及 Q[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以自動載入這些協調流程根據可用性和目前的每部電腦上的負載平衡要求。 這可讓 BizTalk 應用程式視需要為高容量程序擴大效能。 同時請注意，機器 C 包含兩種不同處理外寄訊息的方法。 其中一個可能依賴標準[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配接器，例如 HTTP 配接器，而其他則使用自訂的配接器與特定的系統進行通訊。 在某些情況下，像這樣將所有輸出處理在單一電腦上組成群組是不錯的方法。 而且因為每一個主控件執行個體與其他每一個主控件執行個體隔離 (它們是不同的程序)，可以更安全地在個別的執行個體執行未完全信任的程式碼，例如新的自訂配接器。 即使此範例僅包含 MessageBox 資料庫的單一執行個體，您還是可以複製或叢集資料庫，避免建立單點的失敗。  
  
 最新版 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中引進的 BizTalk 應用程式抽象概念與主控件無關。 若是簡單的 BizTalk 應用程式，所有元件應會包含在單一主控件中，且都安裝在同一部電腦上。 不過在較複雜的案例中，組成應用程式的不同成品 (協調流程、配接器及管線等等) 可能會散佈在多台機器的多個主控件中，如上圖所示。 因此，將這些成品對應到實體機器的程序就不能依賴 BizTalk 應用程式的概念。  
  
## <a name="managing-applications"></a>管理應用程式  
 管理的主要工具[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]引擎是 BizTalk Server 管理主控台的 Microsoft Management Console (MMC) 嵌入式管理單元，提供使用者介面的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理員。 雖然此工具可提供系統管理員的多項功能，最重要的是進行三項作業的能力：  
  
-   **部署 BizTalk 應用程式。** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可讓系統管理員可以使用完整的 BizTalk 應用程式做為一個單位。 使用 BizTalk Server 管理主控台，系統管理員可以建立 BizTalk 應用程式，並將它部署至一或多個伺服器。  
  
-   **設定 BizTalk 應用程式。** 當開發人員建立協調流程時，大多使用邏輯術語。 若要定義如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]引擎將與其通訊特定應用程式，例如，開發人員可以選擇 HTTP 配接器，而不需擔心會用到特定 URL。 同樣地，開發人員可指定傳送管線應該包含可新增數位簽章到外寄訊息的元件，而不需擔心建立此簽章會使用到哪個金鑰。 不過要讓應用程式運作，還是必須指定這些細節。 BizTalk Server 管理主控台可讓系統管理員建立並修改這些組態。  
  
-   **監控 BizTalk 應用程式。** 使用**群組中樞**頁面上 BizTalk Server 管理主控台中，系統管理員可以監控 BizTalk 應用程式的作業。 群組中樞顯示這些應用程式的目前狀態的相關資訊，以及它們的應用程式可以檢查不同的方式。 不需要系統管理員的相關問題，比方說，搜尋**群組中樞**頁面使用色彩編碼的指示器來顯示這些問題。 這樣系統管理員可以更主動的進行應用程式監控。  
  
 BizTalk 管理主控台中，依賴[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]的管理資料庫，也提供其他服務。 系統管理員可在應用程式執行時動態新增電腦，並指定要指派給他們的主機。 不需關閉應用程式就可進行這些變更。 也可透過 Windows Management Instrumentation (WMI)，以程式設計的方式存取管理主控台的功能，讓系統管理員建立自動化管理功能的指令碼。  
  
## <a name="reporting-on-and-debugging-applications"></a>報告和偵錯應用程式  
 BizTalk 應用程式進行存取很多事： 傳送和接收訊息、 協調流程中處理訊息，與使用不同的通訊協定，以及其他各種系統溝通。 保存應用程式活動記錄非常有用，特別是在失敗發生時。 同樣地，具有偵錯協調流程及其他應用程式元件的方法也是同樣重要。 這兩種功能由在 群組中樞提供[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
-   群組中樞提供圖形介面來存取在引擎上執行的應用程式的相關資訊。 此資訊包含協調流程開始及結束的時間、協調流程中的每個圖形執行的時間、傳送及接收每個訊息的時間及這些訊息的內容等等。 開發人員或系統管理員甚至可以設定中斷點，讓協調流程在預先定義的地方停止並進行檢查。 群組中樞也可用來檢查封存的資料，尋找模式和趨勢的商務程序執行中。 此資訊對於偵錯、回答商務問題 (例如查驗訊息是否已傳送至客戶)，以及保留持續產生的統計值 (用於改進效能)，有很大的幫助。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 傳訊引擎](../core/the-biztalk-server-messaging-engine.md)   
安裝[BizTalk Server 2016](../install-and-config-guides/biztalk-server-2016-what-s-new-and-installation.md)或[BizTalk Server 2013 或 R2](../install-and-config-guides/biztalk-server-2013-and-2013-r2-what-s-new-install-and-upgrade.md)    
[設定 BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)  
 [部署和管理 BizTalk 應用程式](../core/deploying-and-managing-biztalk-applications.md)   
 [使用 [群組中樞] 頁面](../core/using-the-group-hub-page.md)