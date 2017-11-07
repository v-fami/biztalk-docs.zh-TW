---
title: "JD Edwards OneWorld 的架構 |Microsoft 文件"
description: "在設計階段和執行的階段在 JD Edwards OneWorld 配接器在 BizTalk 中，在設計階段和執行的階段，以及輸出的事件描述輸入的服務"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9200a090-a587-4b60-9447-d281580f2078
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f866e5d72e392136d19c155785aaf6b71db2ce3
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="architecture-of-jd-edwards-oneworld"></a>JD Edwards OneWorld 的結構
Microsoft BizTalk Adapter for JD Edwards OneWorld 提供對 JD Edwards OneWorld 商務功能的存取 。 JD Edwards OneWorld 會使用名為 JDENet 的專屬傳訊架構進行用戶端與伺服器電腦之間的通訊。 JDENet 是由 JAR 檔案 Connector.jar 和 Kernel.jar 中的 JD Edwards OneWorld 連接器類別實作。 以 TCP/IP 做為傳輸通訊協定，與預設連接埠 6009 或 6010 來實作通訊。 此值設定為位置的描述，請參閱[將成品新增至 BizTalk 管理](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)。  
  
 **BizTalk Adapter for JD Edwards OneWorld 的架構**  
  
 ![](../core/media/jdedadapter-01-architecture.gif "JDEdAdapter_01_Architecture")  
  
 呼叫 JD Edwards OneWorld 商務功能需要兩個訊息：  
  
-   第一個訊息會以處理商務功能的伺服器位置來回應。 這會透過一組資料表呼叫中執行查閱*物件組態對應 (OCM)*。  
  
-   第二個訊息會將格式化的訊息緩衝區 (含有要與 JD Edwards OneWorld 之間往返傳遞的參數) 傳送至適當的伺服器，然後等待回覆。 緩衝區是根據基礎 C + + 結構 (struct) 的 typedef 進行格式化。  
  
## <a name="inbound-services-at-design-time"></a>設計階段的輸入服務  
  
-   在設計階段，您會建立連接埠、選取配接器，並提供連接至目標 JD Edwards OneWorld 伺服器所需的認證資訊。 Visual Studio 開發環境會呼叫配接器架構，以要求此連接埠的設計階段資訊。 BizTalk Adapter for JD Edwards OneWorld 則會針對此連接埠使用 Browsingagent。  
  
-   在設計階段，BizTalk Server 會對配接器進行呼叫來要求資訊。  
  
-   Browsingagent 會將要求轉換為 JD Edwards OneWorld 機器碼，然後透過 ThinNet API 連線 (以 Connector.jar 和 Kernel.jar 建立) 將要求傳輸至 JD Edwards OneWorld。  
  
-   自訂商務功能透過 BTSREL 安裝來安裝： 它會公開主要商務功能。  
  
-   一開始會傳回 JD Edwards OneWorld 中的模組清單並將此清單傳輸至 Visual Studio，而 Visual Studio 會將此清單填入「配接器精靈」。  
  
-   您可以展開階層，以顯示程式庫名稱和模組名稱。  
  
-   當您 選取特定模組時，您會看見模組內所有功能的結構描述 。 配接器會從 JD Edwards OneWorld 取得必要資訊，而 Browsingagent 會建立結構描述。  
  
-   結構描述隨即新增至 BizTalk Server 專案協調流程。  
  
## <a name="inbound-services-at-run-time"></a>執行階段的輸入服務  
  
-   BizTalk Server 會呼叫 BizTalk Adapter for JD Edwards OneWorld，以在特定連接埠上傳送訊息。  
  
-   執行階段代理程式會將 XML 轉換成 JD Edwards 機器碼。  
  
-   執行階段代理程式會透過 ThinNet 將要求提交至在傳送埠的傳輸屬性中指定的 JD Edwards 企業系統。  
  
-   主要商務功能會在 JD Edwards 系統上執行，而該系統會接著產生回應文件，指出執行成功與否以及此商務功能所傳回的資料參數。  
  
-   傳送至 JD Edwards OneWorld 的訊息是單一訊息、單一回覆架構。 系統無法同時處理多則訊息。  
  
-   透過 ThinNet 送回回應文件並轉換為 XML，然後再傳回給 BizTalk Server。  
  
## <a name="outbound-events-at-design-time"></a>設計階段的輸出事件  
  
-   無法以系統化方式建立事件中繼資料。  
  
-   必須將事件文件的摹本提供給 Visual Studio，以便產生結構描述並將之連同目標命名空間一起併入專案中。  
  
## <a name="outbound-events-at-run-time"></a>執行階段的輸出事件  
  
-   JD Edwards 企業伺服器中會建立檔案傳輸機制，以將結果產生的 XML 文件 (在事件完成時觸發) 傳輸至該伺服器上的目標目錄。  
  
-   BizTalk Server 電腦有個對應磁碟機會對應至企業伺服器上的該目錄。  
  
-   接收埠傳輸屬性會針對該對應磁碟機做好設定。 接收埠會 接收由企業伺服器公佈至目錄的訊息 。  
  
-   識別的目標命名空間可確保會將正確的訊息路由傳送至所設定的接收埠。  
  
-   接收埠會將 XML 文件提交至 BizTalk Server。  
  
## <a name="see-also"></a>另請參閱  
 [將成品新增至 BizTalk 管理](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)   
 [規劃和架構](../core/planning-and-architecture17.md)