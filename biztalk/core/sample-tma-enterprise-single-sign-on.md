---
title: TMA 範例： 在企業單一登入 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security examples [TMA], SSO
- architecture, examples
- SSO, examples
- SSO, TMA
- DFD, SSO
- examples, SSO
- examples, TMA
ms.assetid: c2c15b1b-54f3-4d1a-b3d8-6679abd41ccb
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36848a6e2fa48dff20080bda8cc1f7f1d487d089
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995327"
---
# <a name="sample-tma-enterprise-single-sign-on"></a>TMA 範例： 在企業單一登入
本主題呈現範例架構的企業單一登入實例之威脅模型分析 (TMA)。  
  
 下圖顯示基本範例架構，其中包含企業單一登入實例。  
  
 **圖 1 包含企業單一登入實例的基本範例架構**  
  
 ![基底架構元件](../core/media/tdi-sec-refarch.gif "TDI_Sec_RefArch_")  
  
## <a name="step-1-collect-background-information-enterprise-single-sign-on-scenario"></a>步驟 1： 收集背景資訊 （企業單一登入實例）  
 本節提供當您將 Windows 認證對應到用來連線至後端網路的認證時，使用企業單一登入實例的資料流程圖 (DFD)。  
  
 所有其他背景資訊是一樣的所有使用實例，而先前所述[如需範例案例的背景資訊](../core/background-information-for-sample-scenarios.md)。  
  
### <a name="data-flow-diagram"></a>資料流程圖  
 下圖顯示企業單一登入實例的 DFD。  
  
 **圖 2 企業單一登入案例 DFD**  
  
 ![供企業單機登的 DFD&#45;上](../core/media/tdi-sec-refarch-dfd-sso.gif "TDI_Sec_RefArch_DFD_SSO")  
  
 資料流程如下所示：  
  
1.  使用者或應用程式以 Windows 認證登入。  
  
2.  企業單一登入使用 Windows 認證來要求後端網路的認證。  
  
3.  企業單一登入將 Windows 認證對應到 SSO 資料庫中儲存的後端認證。  
  
4.  企業單一登入會擷取後端認證，然後使用它們將使用者或應用程式連接到後端網路。  
  
## <a name="step-2-create-and-analyze-the-threat-model-enterprise-single-sign-on-scenario"></a>步驟 2： 建立和分析威脅模型 （企業單一登入實例）  
 本節提供我們為範例架構的企業單一登入實例所做的 TMA 結果。  
  
- **識別進入點、 信任界限以及資料流**-請參閱稍早在步驟 1 中及中所述的背景資訊[如需範例案例的背景資訊](../core/background-information-for-sample-scenarios.md)。  
  
- **建立一份已識別威脅**-我們針對 dfd 的所有項目使用下列類別來識別潛在威脅的案例： **S**假冒識別，請**T**ampering使用資料時， **R**否認，**我**資訊洩漏**D**拒絕服務，和**E**權限的身分。 下表列出當您使用企業單一登入 (SSO) 從 BizTalk Server 傳送和接收訊息時，我們所識別的威脅清單。  
  
  **資料表 1 的已識別的威脅清單**  
  
|威脅|描述|資產|影響|  
|------------|-----------------|-----------|------------|  
|主要密碼伺服器是單一失敗點|若惡意使用者危害主要密碼伺服器，SSO 電腦就無法加密認證 (但可以繼續解密認證)。|BizTalk Server 與 SSO 環境|拒絕服務|  
|惡意使用者可以欺騙用戶端或伺服器|若用戶端或伺服器執行 Windows，而沒有 NTLM 驗證，則惡意使用者可以欺騙用戶端或伺服器。|BizTalk Server 與 SSO 環境|偽造識別<br /><br /> 竄改資料<br /><br /> 否認性<br /><br /> 資訊洩露<br /><br /> 拒絕服務<br /><br /> 權限提高|  
|當資料從伺服器傳送到另一部伺服器時，惡意使用者可以修改資料|伺服器之間的通訊是純文字，惡意使用者可以在資料傳送時讀取資料。|data|竄改資料<br /><br /> 資訊洩露|  
  
## <a name="step-3-review-threats-enterprise-single-sign-on-scenario"></a>步驟 3： 檢視威脅 （企業單一登入實例）  
 本節提供我們為範例架構的企業單一登入 (SSO) 實例識別的威脅所執行之風險分析結果。 主要威脅模型會議之後，我們已複查威脅，並使用下列影響類別來識別每個威脅的風險： **D**損害， **R**eproducibility， **E**xploitability， **A**受使用者，以及**D**iscoverability。  
  
 下表列出當您使用企業單一登入從 BizTalk Server 傳送和接收訊息時，我們所識別的威脅之風險等級。  
  
 **表 2 已識別的威脅的風險等級**  
  
|威脅|影響|可能的損害|可複製性|利用性|受影響的使用者|發現性|風險暴露程度|  
|------------|------------|----------------------|---------------------|--------------------|--------------------|---------------------|-------------------|  
|主要密碼伺服器是單一失敗點|拒絕服務|2|3|2|@shouldalert|2|2|  
|惡意使用者可以欺騙用戶端或伺服器|偽造識別<br /><br /> 竄改資料<br /><br /> 否認性<br /><br /> 資訊洩露<br /><br /> 拒絕服務<br /><br /> 權限提高|3|2|2|2|@shouldalert|2|  
|當資料從伺服器傳送到另一部伺服器時，惡意使用者可以修改資料|竄改資料<br /><br /> 資訊洩露|3|@shouldalert|@shouldalert|2|@shouldalert|1.6|  
  
## <a name="step-4-identify-mitigation-techniques-enterprise-single-sign-on-scenario"></a>步驟 4： 識別防護技術 （企業單一登入實例）  
 本節呈現我們在範例架構的企業單一登入實例所識別的威脅之一些防護技術。  
  
 下表列出您使用企業單一登入時所識別的威脅之防護技術。  
  
 **表 3 防護技術及技術**  
  
|威脅|影響|風險暴露程度|防護技術|  
|------------|------------|-------------------|--------------------------------------------|  
|主要密碼伺服器是單一失敗點|拒絕服務|2|使用主動-被動叢集組態的主要密碼伺服器。<br /><br /> 如需有關如何叢集主要密碼伺服器的詳細資訊，請參閱[高可用性的企業單一登入](../core/high-availability-for-enterprise-single-sign-on.md)。|  
|惡意使用者可以欺騙用戶端或伺服器|偽造識別<br /><br /> 竄改資料<br /><br /> 否認性<br /><br /> 資訊洩露<br /><br /> 拒絕服務<br /><br /> 權限提高|2|若您的網路支援 Kerberos 驗證，您應該註冊所有 SSO 伺服器。 當您在主要密碼伺服器與 SSO 資料庫之間使用 Kerberos 驗證時，需在 SSO 資料庫所在的 SQL Server 上設定服務主要名稱 (SPN)。<br /><br /> 如需如何設定服務主體名稱的詳細資訊，請參閱 Microsoft TechNet 網站，在[ http://go.microsoft.com/fwlink/?LinkId=61374 ](http://go.microsoft.com/fwlink/?LinkId=61374)。|  
|當資料從伺服器傳送到另一部伺服器時，惡意使用者可以修改資料|竄改資料<br /><br /> 資訊洩露|1.6|在所有 SSO 伺服器與 SSO 資料庫之間使用網際網路通訊協定安全性 (IPsec) 或「安全通訊端層」(SSL)。<br /><br /> 如需有關 SSL 的詳細資訊，請參閱 Microsoft 說明及支援網站，在[ http://go.microsoft.com/fwlink/?LinkID=189708 ](http://go.microsoft.com/fwlink/?LinkID=189708)。<br /><br /> 如需如何在所有 SSO 伺服器與 SSO 資料庫之間使用 SSL 的詳細資訊，請參閱[如何啟用 SSO 的 SSL](../core/how-to-enable-ssl-for-sso.md)。|  
  
## <a name="see-also"></a>另請參閱  
 [威脅模型分析](../core/threat-model-analysis.md)   
 [威脅模型分析的範例案例](../core/sample-scenarios-for-threat-model-analysis.md)   
 [中小型公司的架構範例](../core/sample-architectures-for-small-medium-sized-companies.md)