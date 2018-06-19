---
title: '範例 TMA: FTP 配接器 |Microsoft 文件'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, examples
- examples, FTP adapters
- security examples [TMA], FTP adapters
- FTP adapters, TMA
- DFD, FTP adapters
ms.assetid: c648f84a-c83a-44f0-adc9-a3f98b597506
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b88f01eadc2fcadf6592e61b38203bb09e69b547
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271958"
---
# <a name="sample-tma-ftp-adapter"></a>範例 TMA: FTP 配接器
本主題呈現範例架構的 FTP 配接器實例之威脅模型分析 (TMA)。  
  
 下圖顯示 FTP 配接器實例的範例架構。  
  
 **圖 1 FTP 配接器實例的範例架構**  
  
 ![範例架構的 FTP 配接器](../core/media/tdi-sec-refarch-ftp.gif "TDI_Sec_RefArch_FTP")  
  
## <a name="step-1-collect-background-information-ftp-adapter-scenario"></a>步驟 1： 收集背景資訊 （FTP 配接器實例）  
 本節提供範例架構的 FTP 配接器實例之資料流程圖 (DFD)。  
  
 所有其他背景資訊也適用於所有使用實例，並為先前所述[範例實例的背景資訊](../core/background-information-for-sample-scenarios.md)。  
  
### <a name="data-flow-diagram"></a>資料流程圖  
 下圖顯示使用 FTP 配接器時範例架構的 DFD。  
  
 **圖 2 FTP 配接器實例的範例架構 DFD**  
  
 ![FTP 配接器的 DFD](../core/media/tdi-sec-refarch-dfd-ftp.gif "TDI_Sec_RefArch_DFD_FTP")  
  
 資料流程如下所示：  
  
1.  夥伴或客戶傳送一個訊息給 FTP 伺服器。 此訊息會傳遞到防火牆 1 的 IP 位址。  
  
2.  防火牆 1 接收訊息，再將它傳遞到位於網際網路周邊網路的 FTP 伺服器中。  
  
3.  FTP 接收配接器的內含式主控件的執行個體，定期輪詢 FTP 伺服器的新訊息 (透過防火牆 2)。 在它發現新訊息之後，它會擷取訊息，執行任何初始處理，然後將訊息放入 MessageBox 資料庫中。  
  
4.  訂閱該訊息的處理主控件執行個體會從 MessageBox 資料庫拾取此訊息、執行任何進一步的處理，然後將訊息放回 MessageBox 資料庫。  
  
5.  而擁有 FTP 傳送配接器的內含式主控件的執行個體則會從 MessageBox 資料庫拾取訊息。 此訊息在傳送管線中經過任何最終處理，然後透過防火牆 2 傳送到 FTP 伺服器。  
  
6.  然後 FTP 伺服器透過防火牆 1 將訊息送回給夥伴或客戶。  
  
## <a name="step-2-create-and-analyze-the-threat-model-ftp-adapter-scenario"></a>步驟 2： 建立和分析威脅模型 （FTP 配接器實例）  
 本節提供我們為範例架構的 FTP 配接器實例所做的 TMA 結果。  
  
-   **識別進入點、 信任界限以及的資料流-** 請參閱稍早在步驟 1 中及中所述的背景資訊[範例實例的背景資訊](../core/background-information-for-sample-scenarios.md)。  
  
-   **建立一份識別的威脅-** 我們針對 dfd 的所有項目使用下列分類來識別潛在的威脅： **S**假冒識別， **T**ampering 取代資料， **R**epudiation，**我**若資訊洩漏、 **D**拒絕服務，以及**E**身分權限。 下表列出當您使用 FTP 配接器從 BizTalk Server 傳送和接收訊息時，我們所識別的威脅。  
  
 **表 1 已識別的威脅的清單**  
  
|威脅|Description|資產|影響|  
|------------|-----------------|-----------|------------|  
|FTP 通訊協定並不安全|FTP 通訊協定使用者識別碼與密碼會以純文字傳送。 而惡意使用者可以監控網路以存取認證。 資料會被洩露。|使用者認證|偽造識別<br /><br /> 竄改資料<br /><br /> 資訊洩露|  
|FTP 伺服器容易受到未經授權的 DHCP 伺服器攻擊|若 URI 不包含使用者的密碼，而是指定於處理常式上，則在執行階段才會從處理常式將密碼傳送到 FTP 伺服器。 若是有欺詐的 FTP 伺服器監聽驗證呼叫，它就可能以此方式偷取密碼。 其中一個解決方案是在處理常式層級啟用/停用使用密碼。|FTP 伺服器|偽造識別<br /><br /> 竄改資料<br /><br /> 資訊洩露|  
  
## <a name="step-3-review-threats-ftp-adapter-scenario"></a>步驟 3： 檢視威脅 （FTP 配接器實例）  
 本節提供針對範例架構的 FTP 配接器實例已識別出的威脅，我們所執行的風險分析結果。 主要威脅模型會議之後，我們已複查威脅，並使用下列影響類別來識別每個威脅的風險： **D**損害潛在， **R**eproducibility， **E**xploitability， **A**受使用者和**D**iscoverability。  
  
 下表列出當您使用 FTP 配接器從 BizTalk Server 傳送和接收訊息時，我們所識別的威脅之風險等級。  
  
 **表 2 已識別的威脅的風險等級**  
  
|威脅|影響|可能的損害|可複製性|利用性|受影響的使用者|發現性|風險暴露程度|  
|------------|------------|----------------------|---------------------|--------------------|--------------------|---------------------|-------------------|  
|FTP 通訊協定並不安全|偽造識別<br /><br /> 竄改資料<br /><br /> 資訊洩露|9|9|2|10|5|7|  
|FTP 伺服器容易受到未經授權的 DHCP 伺服器攻擊|偽造識別<br /><br /> 竄改資料<br /><br /> 資訊洩露|5|5|2|10|5|5.4|  
  
## <a name="step-4-identify-mitigation-techniques-ftp-adapter-scenario"></a>步驟 4： 識別防護技術 （FTP 配接器實例）  
 本節呈現我們在範例架構的 FTP 配接器實例所識別的威脅之一些防護技術。  
  
 下表列出當您使用 FTP 配接器從 BizTalk Server 傳送和接收訊息時，我們所識別的威脅之防護技術。  
  
 **表 3 防護技術和技術**  
  
|威脅|影響|風險暴露程度|防護技術|  
|------------|------------|-------------------|--------------------------------------------|  
|FTP 通訊協定並不安全|偽造識別<br /><br /> 竄改資料<br /><br /> 資訊洩露|7|FTP 配接器必須用於安全的環境中，而且要透過安全線路使用。|  
|FTP 伺服器容易受到未經授權的 DHCP 伺服器攻擊|偽造識別<br /><br /> 竄改資料<br /><br /> 資訊洩露|5.4|建議您將遠端 FTP 伺服器放在安全的位置。 您必須確定此伺服器的實體和網路安全性，讓未經授權 DHCP 伺服器的攻擊降至最低。|  
  
## <a name="see-also"></a>另請參閱  
 [威脅模型分析](../core/threat-model-analysis.md)   
 [威脅模型分析的範例案例](../core/sample-scenarios-for-threat-model-analysis.md)   
 [小型與中型公司的範例架構](../core/sample-architectures-for-small-medium-sized-companies.md)