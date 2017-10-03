---
title: "範例 TMA: BizTalk 訊息佇列配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security examples [TMA], MSMQ adapters
- architecture, examples
- MSMQ adapters, TMA
- DFD, MSMQ adapters
- MSMQ adapters, data flow
ms.assetid: 15b4a540-2fcd-4668-b4b4-757f23ebd83e
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91f37c57c24bdd37c0f2cc0399a797050228aa54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sample-tma-biztalk-message-queuing-adapter"></a>範例 TMA: BizTalk 訊息佇列配接器
本主題呈現範例架構的 BizTalk 訊息佇列配接器實例之威脅模型分析 (TMA)。  
  
## <a name="step-1-collect-background-information-biztalk-message-queuing-adapter-scenario"></a>步驟 1： 收集背景資訊 （BizTalk 訊息佇列配接器實例）  
 本節提供範例架構的 BizTalk 訊息佇列配接器實例之資料流程圖 (DFD)。 下圖顯示 HTTP 與 SOAP 配接器實例的範例架構。  
  
 **圖 1 的 BizTalk 訊息佇列配接器實例的範例架構**  
  
 ![BizTalk 訊息佇列的範例架構](../core/media/tdi-sec-refarch-msmq.gif "TDI_Sec_RefArch_MSMQ")  
  
 所有其他背景資訊也適用於所有使用實例，並為先前所述[範例實例的背景資訊](../core/background-information-for-sample-scenarios.md)。  
  
### <a name="data-flow-diagram"></a>資料流程圖  
 下圖顯示使用 BizTalk 訊息佇列配接器時範例架構的 DFD。  
  
 **圖 2 BizTalk 訊息佇列配接器實例的範例架構 DFD**  
  
 ![BizTalk 訊息佇列的範例架構](../core/media/tdi-sec-refarch-dfd-msmq.gif "TDI_Sec_RefArch_DFD_MSMQ")  
  
 資料流程如下所示：  
  
1.  夥伴使用訊息佇列或 BizTalk 訊息佇列來傳送一個訊息。 此訊息會以適當格式封裝，並在網路上傳送。 若您使用 Active Directory，此訊息會通過一系列訊息佇列路由器，直到它抵達正確的目的地 (執行 BizTalk 訊息佇列接收配接器的主控件執行個體之 BizTalk Server)。  
  
2.  BizTalk 訊息佇列接收配接器的內含式主控件的執行個體會從訊息佇列路由器 (透過防火牆 2) 定期接收訊息，並執行任何初始處理，還有傳送網路通訊協定所定義的正確網路回應，以及將訊息放入 MessageBox 資料庫中。  
  
3.  訂閱該訊息的處理主控件執行個體會從 MessageBox 資料庫拾取此訊息、執行任何進一步的處理，然後將訊息放回 MessageBox 資料庫。  
  
4.  而擁有 BizTalk 訊息佇列傳送配接器的內含式主控件之執行個體則會從 MessageBox 資料庫拾取訊息。 此訊息在傳送管線中經過任何最終處理，然後穿過防火牆 2 並透過網路將訊息送回夥伴或應用程式。  
  
## <a name="step-2-create-and-analyze-the-threat-model-biztalk-message-queuing-adapter-scenario"></a>步驟 2： 建立和分析威脅模型 （BizTalk 訊息佇列配接器實例）  
 本節提供我們為範例架構的 BizTalk 訊息佇列配接器所做的 TMA 結果。  
  
-   **識別進入點、 信任界限以及的資料流-**請參閱稍早在步驟 1 中及中所述的背景資訊[範例實例的背景資訊](../core/background-information-for-sample-scenarios.md)。  
  
-   **建立一份識別的威脅-**我們針對 dfd 的所有項目使用下列分類來識別潛在的威脅： **S**假冒識別， **T**ampering 取代資料， **R**epudiation，**我**若資訊洩漏、 **D**拒絕服務，以及**E**身分權限。 下表列出當您使用 BizTalk 訊息佇列配接器從 BizTalk Server 傳送和接收訊息時，我們所識別的威脅。  
  
 **表 1 已識別的威脅的清單**  
  
|威脅|Description|資產|影響|  
|------------|-----------------|-----------|------------|  
|傳送許多訊息至接收位置|惡意使用者可以傳送大量有效或無效的訊息，並灌爆應用程式。|BizTalk Server 環境|拒絕服務|  
|訊息標頭在網路上無礙地傳遞|當訊息從佇列移至 BizTalk 訊息佇列接收配接器時，訊息標頭是在無危險狀態，但惡意使用者可能讀取和修改標頭。|訊息標頭|竄改資料<br /><br /> 資訊洩露|  
|未經授權的使用者可以透過網路連線到執行 BizTalk 訊息佇列主控件的 BizTalk Server|您可以使用判別存取控制清單 (DACL) 來限制存取 BizTalk 訊息佇列接收位置。 因此，能夠連線到執行 BizTalk 訊息佇列接收配接器主控件執行個體之 BizTalk Server 與連接埠 1801 的任何人，都可以傳送訊息到 BizTalk 訊息佇列接收位置。|BizTalk Server 環境|否認性<br /><br /> 竄改資料<br /><br /> 資訊洩露<br /><br /> 拒絕服務<br /><br /> 權限提高|  
|惡意使用者可以在 BizTalk Server 收到訊息之前竄改訊息|惡意使用者可以在訊息傳輸時攔截訊息，並加以修改。|訊息內文|竄改資料<br /><br /> 資訊洩露|  
  
## <a name="step-3-review-threats-biztalk-message-queuing-adapter-scenario"></a>步驟 3： 檢視威脅 （BizTalk 訊息佇列配接器實例）  
 本節提供針對範例架構的 BizTalk 訊息佇列配接器實例已識別出的威脅，我們所執行的風險分析結果。 主要威脅模型會議之後，我們已複查威脅，並使用下列影響類別來識別每個威脅的風險： **D**損害潛在， **R**eproducibility， **E**xploitability， **A**受使用者和**D**iscoverability。  
  
 下表列出當您使用 BizTalk 訊息佇列配接器從 BizTalk Server 傳送和接收訊息時，我們所識別的威脅之風險等級。  
  
 **表 2 已識別的威脅的風險等級**  
  
|威脅|影響|可能的損害|可複製性|利用性|受影響的使用者|發現性|風險暴露程度|  
|------------|------------|----------------------|---------------------|--------------------|--------------------|---------------------|-------------------|  
|傳送許多訊息至接收位置|拒絕服務|8|7|7|7|5|6.8|  
|訊息標頭在網路上無礙地傳遞|竄改資料<br /><br /> 資訊洩露|8|10|8|3|5|6.8|  
|未經授權的使用者可以透過網路連線到執行 BizTalk 訊息佇列主控件的 BizTalk Server|否認性<br /><br /> 竄改資料<br /><br /> 資訊洩露<br /><br /> 拒絕服務<br /><br /> 權限提高|8|10|9|9|9|9|  
|惡意使用者可以在 BizTalk Server 收到訊息之前竄改訊息|竄改資料<br /><br /> 資訊洩露|5|7|6|5|7|6|  
  
## <a name="step-4-identify-mitigation-techniques-biztalk-message-queuing-adapter-scenario"></a>步驟 4： 識別防護技術 （BizTalk 訊息佇列配接器實例）  
 本節呈現我們在範例架構的 BizTalk 訊息佇列配接器實例所識別的威脅之一些防護技術。  
  
 下表列出當您使用 BizTalk 訊息佇列配接器從 BizTalk Server 傳送和接收訊息時，我們所識別的威脅之防護技術。  
  
 **表 3 防護技術和技術**  
  
|威脅|影響|風險暴露程度|防護技術|  
|------------|------------|-------------------|--------------------------------------------|  
|傳送許多訊息至接收位置|拒絕服務|6.8|在需要驗證模式中使用 BizTalk 訊息佇列配接器。 設定**要求 MSMQ 驗證**接收位置上的旗標和**需要驗證 （捨棄訊息）**接收埠上。<br /><br /> 設定 BizTalk 訊息佇列為需要認證驗證。 此行為發生於配接器層級，而且不同於 BizTalk 管線的「合作對象解析」元件。 若已設定，則內送訊息會包含公用憑證。 這是 BizTalk 訊息佇列唯一可用的用戶端驗證模式。 若要使用此用戶端驗證模式，您必須使用 Active Directory 整合模式安裝 BizTalk 訊息佇列。 當您使用這項功能時，請記得選取**需要驗證**核取方塊，在屬性對話方塊中，BizTalk 訊息佇列接收位置。|  
|訊息標頭在網路上無礙地傳遞|竄改資料<br /><br /> 資訊洩露|6.8|使用網際網路通訊協定安全性 (IPsec) 協助保護在伺服器之間傳遞的訊息內文與訊息標頭。|  
|未經授權的使用者可以透過網路連線到執行 BizTalk 訊息佇列主控件的 BizTalk Server|否認性<br /><br /> 竄改資料<br /><br /> 資訊洩露<br /><br /> 拒絕服務<br /><br /> 權限提高|9|建立擁有「合作對象解析」管線元件的自訂管線，然後設定「合作對象解析」元件使用「傳送者識別碼」(SID) 來解析合作對象。 設定**依憑證解析合作對象**屬性**False**，而**依 SID 解析合作對象**屬性**True**。 如需詳細資訊，請參閱[合作對象解析管線元件](../core/party-resolution-pipeline-component.md)。<br /><br /> 在 接收埠中，設定**驗證**屬性**必要 （捨棄訊息）**。|  
|惡意使用者可以在 BizTalk Server 收到訊息之前竄改訊息|竄改資料<br /><br /> 資訊洩露|6|使用通訊協定層級的驗證來確定訊息在傳輸時未遭到修改。 若要使用通訊協定層級的驗證，您必須在電子商務網域中擁有訊息佇列路由器。 設定 BizTalk Server 如下：<br /><br /> -在**BizTalk 傳訊**頁面上的 Configuration Manager 中，提供路由器的名稱。<br />-若為接收埠中，設定**驗證**屬性**必要 （捨棄訊息）**或**必要 （保留訊息）**。<br />-若為傳送處理常式上**一般**索引標籤的**MSMQ 路由器**名稱方塊中，輸入訊息佇列路由器的名稱。<br />-傳送埠，請選取**使用 MSMQ 驗證**。|  
  
## <a name="see-also"></a>另請參閱  
 [威脅模型分析](../core/threat-model-analysis.md)   
 [威脅模型分析的範例案例](../core/sample-scenarios-for-threat-model-analysis.md)   
 [小型與中型公司的範例架構](../core/sample-architectures-for-small-medium-sized-companies.md)