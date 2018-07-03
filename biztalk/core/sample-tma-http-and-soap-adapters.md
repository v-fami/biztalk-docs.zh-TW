---
title: TMA 範例： HTTP 和 SOAP 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, examples
- DFD, HTTP adapters
- security examples [TMA], SOAP adapters
- SOAP adapters, examples
- security examples [TMA], HTTP adapters
- examples, HTTP adapters
- DFD, SOAP adapter
- examples, SOAP adapters
- SOAP adapters, TMA
- HTTP adapters, TMA
ms.assetid: d9a40cff-92a1-4bc9-ae45-3a5857f70222
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd1b58a89ce123350ba3b6d7be0e665d4428429a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011479"
---
# <a name="sample-tma-http-and-soap-adapters"></a>TMA 範例： HTTP 和 SOAP 配接器
本主題提供威脅模型分析 (TMA) 的 HTTP 與 SOAP （Web 服務） 配接器實例的範例架構。 下圖顯示 HTTP 與 SOAP 配接器實例的範例架構。  
  
 **圖 1 HTTP/SOAP 配接器實例的範例架構**  
  
 ![範例 HTTP 或 SOAP 配接器的架構](../core/media/tdi-sec-refarch-http.gif "TDI_Sec_RefArch_HTTP")  
  
## <a name="step-1-collect-background-information-http-and-soap-adapters-scenario"></a>步驟 1： 收集背景資訊 （HTTP 與 SOAP 配接器實例）  
 本節提供範例架構的 HTTP 與 SOAP (Web 服務) 配接器實例的資料流程圖 (DFD)。  
  
 所有其他背景資訊是一樣的所有使用實例，而先前所述[如需範例案例的背景資訊](../core/background-information-for-sample-scenarios.md)。  
  
### <a name="data-flow-diagram"></a>資料流程圖  
 下圖顯示使用 HTTP 與 SOAP (Web 服務) 配接器時範例架構的 DFD。  
  
 **圖 2 HTTP/SOAP 配接器實例的範例架構 DFD**  
  
 ![範例架構 DFD](../core/media/tdi-sec-refarch-dfd-http.gif "TDI_Sec_RefArch_DFD_HTTP")  
  
 資料流程如下所示：  
  
1.  夥伴或客戶透過 HTTP、HTTPS 或 Web 服務傳送一個訊息。 此訊息會傳遞到防火牆 1 的 IP 位址。  
  
2.  防火牆 1 透過防火牆 2 使用反向 Proxy 來傳送訊息。  
  
3.  防火牆 2 將訊息傳遞至執行 HTTP 或 SOAP 接收配接器的外掛式主控件之 BizTalk Server。 外掛式主控件會處理訊息，並將它放入 MessageBox 資料庫。  
  
4.  訂閱該訊息的處理主控件執行個體會從 MessageBox 資料庫拾取此訊息、執行任何進一步的處理，然後將訊息放回 MessageBox 資料庫。  
  
5.  而擁有 HTTP 或 SOAP 傳送配接器的外掛式主控件之執行個體則會從 MessageBox 資料庫拾取訊息。 此訊息在傳送管線中經過任何最終處理，然後送回夥伴或客戶。  
  
6.  當訊息傳送給夥伴或客戶時，它會透過防火牆 2 與防火牆 1 使用反向 Proxy 來傳遞。  
  
## <a name="step-2-create-and-analyze-the-threat-model-http-and-soap-adapters-scenario"></a>步驟 2： 建立和分析威脅模型 （HTTP 與 SOAP 配接器實例）  
 本節提供我們為範例架構的 HTTP 與 SOAP (Web 服務) 配接器實例所做的 TMA 結果。  
  
- **識別進入點、 信任界限以及非固定格式的資料-** 請參閱稍早在步驟 1 中所述的背景資訊和[如需範例案例的背景資訊](../core/background-information-for-sample-scenarios.md)。  
  
- **建立一份已識別的威脅-** 我們針對 dfd 的所有項目使用下列類別來識別潛在威脅的案例： **S**假冒識別，請**T**ampering使用資料時， **R**否認，**我**資訊洩漏**D**拒絕服務，和**E**權限的身分。 下表列出當您使用 HTTP 與 SOAP 配接器從 BizTalk Server 傳送和接收訊息時，我們所識別的威脅清單。  
  
  **表 1 威脅的清單**  
  
|威脅|描述|資產|影響|  
|------------|-----------------|-----------|------------|  
|傳送無限大小的訊息|惡意使用者可以傳送無限大小的訊息。|BizTalk Server 環境|拒絕服務|  
|傳送許多訊息至接收位置|惡意使用者可以傳送大量有效或無效的訊息，並灌爆應用程式。|BizTalk Server 環境|拒絕服務|  
|透過 HTTP 讀取訊息內文|惡意使用者可以在訊息從傳送者傳送到防火牆 1 的過程中攔截訊息，並且可以讀取訊息。|訊息內容|資訊洩露|  
|從訊息讀取使用者認證|若您使用基本驗證，而且訊息包含使用者認證，則惡意使用者可以存取該認證，並使用它們來存取應用程式。|使用者認證|資訊洩露<br /><br /> 權限提高|  
  
## <a name="step-3-review-threats-http-and-soap-adapters-scenario"></a>步驟 3： 檢視威脅 （HTTP 與 SOAP 配接器實例）  
 本節提供我們為範例架構的 HTTP 與 SOAP (Web 服務) 配接器實例所識別的威脅之風險分析結果。 主要威脅模型會議之後，我們已複查威脅，並使用下列影響類別來識別每個威脅的風險： **D**損害， **R**eproducibility， **E**xploitability， **A**受使用者並**D**iscoverability。  
  
 下表列出當您使用 HTTP 與 SOAP (Web 服務) 配接器從 BizTalk Server 傳送和接收訊息時，我們所識別的威脅之風險等級。  
  
 **表 2 威脅的風險等級**  
  
|威脅|影響|可能的損害|可複製性|利用性|受影響的使用者|發現性|風險暴露程度|  
|------------|------------|----------------------|---------------------|--------------------|--------------------|---------------------|-------------------|  
|傳送無限大小的訊息|拒絕服務|2|3|2|3|2|2.4|  
|傳送許多訊息至接收位置|拒絕服務|3|3|@shouldalert|3|3|2.6|  
|透過 HTTP 讀取訊息內文|資訊洩露|3|3|2|3|3|2.8|  
|從訊息讀取使用者認證|資訊洩露<br /><br /> 權限提高|3|3|2|3|2|2.6|  
  
## <a name="step-4-identify-mitigation-techniques-http-and-soap-adapters-scenario"></a>步驟 4： 識別防護技術 （HTTP 與 SOAP 配接器實例）  
 本節呈現我們在範例架構的 HTTP 與 SOAP (Web 服務) 配接器實例所識別的威脅之一些防護技術。  
  
 下表列出當您使用 HTTP 與 SOAP (Web 服務) 配接器從 BizTalk Server 傳送和接收訊息時，我們所識別的威脅之防護技術。  
  
 **表 3 防護技術及技術**  
  
|威脅|影響|風險暴露程度|防護技術|  
|------------|------------|-------------------|--------------------------------------------|  
|傳送無限大小的訊息|拒絕服務|2.4|限制每個 URL 的內送訊息之大小上限，並拒絕超過此上限的訊息。<br /><br /> 如需詳細資訊，請參閱 <<c0> [ 減少阻斷的服務攻擊](../core/mitigating-denial-of-service-attacks.md)。|  
|傳送許多訊息至接收位置|拒絕服務|2.6|SOAP 配接器利用 HTTP 來從 BizTalk Server 傳送和接收訊息。 因此，您必須遵循安全性建議來協助保護網際網路資訊服務 (IIS) 的安全。 若您使用 IIS，請確定您遵循 IIS 中對於如何設定應用程式隔離的建議。<br /><br /> 如需詳細資訊，請參閱 Microsoft TechNet 網站，在[ http://go.microsoft.com/fwlink/?LinkId=60951 ](http://go.microsoft.com/fwlink/?LinkId=60951)。<br /><br /> 使用用戶端驗證與合作對象解析，只處理有效且經過授權的訊息以限制處理的訊息數量。|  
|透過 HTTP 讀取訊息內文|資訊洩露|2.8|建議您使用 S/MIME 來協助保護 BizTalk Server 中往返訊息的安全。<br /><br /> 建議您使用「安全通訊端層」(SSL) 協助保護 BizTalk Server 中往返的資料傳輸之安全，以及保護分散在環境中的 BizTalk Server 伺服器元件之間的安全。|  
|從訊息讀取使用者認證|資訊洩露<br /><br /> 權限提高|2.6|當您使用基本驗證時，或當您不要在訊息層級使用加密時，建議您使用 SSL 來接收和傳送訊息，以確定未經授權的人員無法讀取使用者認證。|  
  
## <a name="see-also"></a>另請參閱  
 [威脅模型分析](../core/threat-model-analysis.md)   
 [威脅模型分析的範例案例](../core/sample-scenarios-for-threat-model-analysis.md)   
 [中小型公司的架構範例](../core/sample-architectures-for-small-medium-sized-companies.md)