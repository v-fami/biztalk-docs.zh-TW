---
title: "BizTalk Adapter for JD Edwards EnterpriseOne 的架構 |Microsoft 文件"
description: "在設計階段和執行的階段在 JD Edwards EnterpriseOne 配接器在 BizTalk 中，在設計階段和執行的階段，以及輸出的事件描述輸入的服務"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0441c5d2-6a46-45b6-8ab5-0bdac3590f56
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b495ee9a34cf464bd5cc11caed53c5df54948a49
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="architecture-of-biztalk-adapter-for-jd-edwards-enterpriseone"></a>BizTalk Adapter for JD Edwards EnterpriseOne 的架構
Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 可讓您存取 JD Edwards EnterpriseOne 商務功能。 JD Edwards EnterpriseOne 會使用名為 JDENet 的專屬傳訊架構，在用戶端與伺服器電腦之間通訊。 JDENet 是由 JAR 檔案 Connector.jar 和 Kernel.jar 中的 JD Edwards EnterpriseOne 連接器類別實作。 以 TCP/IP 做為傳輸通訊協定，與預設連接埠 6009 或 6010 來實作通訊。 此值設定為位置的描述，請參閱[將成品新增至 BizTalk 管理](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)。  
  
 下圖顯示 BizTalk Adapter for JD Edwards EnterpriseOne 的架構。  
  
 ![](../core/media/jd-enterpriseone-arch.gif "JD_EnterpriseOne_arch")  
  
## <a name="inbound-services-at-design-time"></a>設計階段的輸入服務  
  
-   在設計階段，您會建立連接埠、選取配接器並提供認證資訊，以連接至目標 JD Edwards EnterpriseOne 伺服器。 Visual Studio 開發環境會呼叫配接器架構，以要求此連接埠的設計階段資訊。 配接器會針對此連接埠使用 Browsingagent。  
  
-   在設計階段，BizTalk Server 會對配接器進行呼叫來要求資訊。  
  
-   Browsingagent 會將要求轉換成原生 JD Edwards EnterpriseOne 程式碼，再透過 ThinNet API 連線 (建立於 Connector.jar and Kernel.jar 中) 將要求傳輸至 JD Edwards EnterpriseOne。  
  
-   最初會傳回 JD Edwards EnterpriseOne 中模組的清單並傳輸至 Visual Studio 開發環境，以填入配接器精靈。  
  
-   您可以先顯示程式庫名稱，再顯示模組名稱，來逐漸展開階層。  
  
-   當您 選取特定模組時，您會看見模組內所有功能的結構描述 。 配接器會從 JD Edwards EnterpriseOne 取得必要資訊，而 Browsingagent 會建立結構描述。  
  
-   結構描述隨即新增至 BizTalk Server 專案協調流程。  
  
## <a name="inbound-services-at-run-time"></a>執行階段的輸入服務  
  
-   BizTalk Server 會呼叫配接器，以在特定連接埠上傳送訊息。  
  
-   執行階段代理程式會將 XML 轉換成原生 JDE 程式碼。  
  
-   執行階段代理程式會透過 ThinNet，將要求提交給傳送埠的傳輸屬性中所指定的 JD Edwards EnterpriseOne 系統。  
  
-   「主要商務功能」會在 JD Edwards EnterpriseOne 系統上執行，然後該系統會產生回應文件，指示執行成功或失敗以及商務功能所傳回的資料參數。  
  
-   傳送至 JD Edwards EnterpriseOne 的訊息是單一訊息、單一回覆架構。 系統無法同時處理多則訊息。  
  
-   透過 ThinNet 送回回應文件並轉換為 XML，然後再傳回給 BizTalk Server。  
  
## <a name="outbound-events-at-design-time"></a>設計階段的輸出事件  
  
-   無法以系統化方式建立事件中繼資料。  
  
-   必須將事件文件的摹本提供給 Visual Studio，以便產生結構描述並將之連同目標命名空間一起併入專案中。  
  
## <a name="outbound-events-at-run-time"></a>執行階段的輸出事件  
  
-   JD Edwards EnterpriseOne 伺服器中會建立檔案傳輸機制，以將結果產生的 XML 文件 (在事件完成時觸發) 傳輸至該電腦上的目標目錄。  
  
-   BizTalk Server 電腦有個對應磁碟機對應至 EnterpriseOne 伺服器上的該目錄。  
  
-   接收埠傳輸屬性會針對該對應磁碟機做好設定。 接收埠會接收由 EnterpriseOne 伺服器公佈至某個目錄的訊息。  
  
-   識別目標命名空間可確保將正確的訊息路由傳送至所設定的接收埠。  
  
-   接收埠會在 BizTalk Server 中提交 XML 文件。  
  
## <a name="more-good-stuff"></a>更多實用功能
[BizTalk Adapter for JD Edwards EnterpriseOne 中的安全性](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md)  
[建立應用程式成品](../core/developing-applications2.md)  
[匯入您的 JD Edwards EnterpriseOne 應用程式](../core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone.md)  
[使用 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling3.md)  
[疑難排解](../core/troubleshooting-jd-edwards-enterpriseone.md)  
