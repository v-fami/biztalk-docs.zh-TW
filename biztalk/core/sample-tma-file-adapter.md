---
title: TMA 範例： File 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, examples
- DFD, File adapters
- File adapters, TMA
- examples, File adapters
- security examples [TMA], File adapters
ms.assetid: bcb862c0-fe02-4335-8b59-242d28049e3f
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8422ae5d3829efc036c85f90fca80ca8f976289
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982847"
---
# <a name="sample-tma-file-adapter"></a>TMA 範例： File 配接器
本主題呈現範例架構的 File 配接器實例之威脅模型分析 (TMA)。 下圖顯示 File 配接器實例的範例架構。  
  
 **圖 1 的 File 配接器實例的範例架構**  
  
 ![範例檔案配接器的架構](../core/media/tdi-sec-refarch-file.gif "TDI_Sec_RefArch_File")  
  
## <a name="step-1-collect-background-information-file-adapter-scenario"></a>步驟 1： 收集背景資訊 （File 配接器實例）  
 本節提供範例架構的 FILE 配接器實例之資料流程圖 (DFD)。  
  
 所有其他背景資訊是一樣的所有使用實例，而先前所述[如需範例案例的背景資訊](../core/background-information-for-sample-scenarios.md)。  
  
### <a name="data-flow-diagram"></a>資料流程圖  
 下圖顯示使用 File 配接器時範例架構的 DFD。  
  
 **圖 2 範例架構的 File 配接器實例的 DFD**  
  
 ![範例架構 DFD](../core/media/tdi-sec-refarch-dfd-file.gif "TDI_Sec_RefArch_DFD_FILE_")  
  
 資料流程如下所示：  
  
1.  夥伴將訊息 (透過防火牆 1) 放入內部網路周邊網路的檔案伺服器中。  
  
2.  FILE 接收配接器的內含式主控件的執行個體，定期輪詢檔案伺服器的新訊息 (透過防火牆 2)。 在它發現新訊息之後，它會擷取訊息，執行任何初始處理，然後將訊息放入 MessageBox 資料庫中。  
  
3.  訂閱該訊息的處理主控件執行個體會從 MessageBox 資料庫拾取此訊息、執行任何進一步的處理，然後將訊息放回 MessageBox 資料庫。  
  
4.  而擁有 FILE 傳送配接器的內含式主控件的執行個體則會從 MessageBox 資料庫拾取訊息。 此訊息在傳送管線中經過任何最終處理，然後透過防火牆 2 傳送到檔案伺服器。  
  
5.  夥伴從檔案伺服器拾取訊息。  
  
## <a name="step-2-create-and-analyze-the-threat-model-file-adapter-scenario"></a>步驟 2： 建立和分析威脅模型 （File 配接器實例）  
 本節提供我們為範例架構的 FILE 配接器實例所做的 TMA 結果。  
  
- **識別進入點、 信任界限以及非固定格式的資料-** 查看背景資訊稍早所述 」 收集背景資訊的 File 配接器實例 」 和 「 所有案例的背景資訊 」。  
  
- **建立一份已識別的威脅-** 我們針對 dfd 的所有項目使用下列類別來識別潛在威脅的案例： **S**假冒識別，請**T**ampering使用資料時， **R**否認，**我**資訊洩漏**D**拒絕服務，和**E**權限的身分。 下表列出當您使用 File 配接器傳送和接收 BizTalk Server 訊息時識別的威脅。  
  
  **表 1 識別的威脅清單**  
  
|威脅|描述|資產|影響|  
|------------|-----------------|-----------|------------|  
|未經授權的使用者可以從檔案放置資料夾擷取訊息|若您尚未設定 FILE 配接器使用的資料夾之強式判別存取控制清單 (DACL)，未經授權的使用者就可以在檔案接收位置放置訊息，或從檔案傳送位置拾取訊息。|訊息內文|竄改資料<br /><br /> 資訊洩露|  
|未經授權的使用者可以提交訊息到 BizTalk Server|若使用者擁有 BizTalk Server 拾取訊息的檔案資料夾之寫入權限，則未經授權的使用者可以提交訊息到 BizTalk Server。|訊息內文|拒絕服務<br /><br /> 權限提高|  
  
## <a name="step-3-review-threats-file-adapter-scenario"></a>步驟 3： 檢視威脅 （File 配接器實例）  
 本節提供針對範例架構的 FILE 配接器實例已識別出的威脅，我們所執行的風險分析結果。 主要威脅模型會議之後，我們已複查威脅，並使用下列影響類別來識別每個威脅的風險： **D**損害， **R**eproducibility， **E**xploitability， **A**受使用者並**D**iscoverability。  
  
 下表列出當您使用 FILE 配接器從 BizTalk Server 傳送和接收訊息時，我們所識別的威脅之風險等級。  
  
 **表 2 已識別的威脅的風險等級**  
  
|威脅|影響|可能的損害|可複製性|利用性|受影響的使用者|發現性|風險暴露程度|  
|------------|------------|----------------------|---------------------|--------------------|--------------------|---------------------|-------------------|  
|未經授權的使用者可以從檔案放置資料夾擷取訊息|竄改資料<br /><br /> 資訊洩露|4|7|5|4|6|5.2|  
|未經授權的使用者可以提交訊息到 BizTalk Server|拒絕服務<br /><br /> 權限提高|4|7|5|4|5|5.2|  
  
## <a name="step-4-identify-mitigation-techniques-file-adapter-scenario"></a>步驟 4： 識別防護技術 （File 配接器實例）  
 本節呈現我們在範例架構的 FILE 配接器實例所識別的威脅之一些防護技術。  
  
 下表列出當您使用 FILE 配接器從 BizTalk Server 傳送和接收訊息時，我們所識別的威脅之防護技術。  
  
 **表 3 防護技術及技術**  
  
|威脅|影響|風險暴露程度|防護技術|  
|------------|------------|-------------------|--------------------------------------------|  
|未經授權的使用者可以從檔案放置資料夾擷取訊息|竄改資料<br /><br /> 資訊洩露|5.2|對於 BizTalk Server 拾取訊息的資料夾，請使用強式判別存取控制清單 (DACL)，如下所示：<br /><br /> -對於執行接收配接器的主控件的主控件執行個體的服務帳戶，請設定讀取、 寫入、 刪除檔案，以及刪除的目錄的檔案接收位置拾取訊息的子資料夾和檔案權限。<br />-針對外部使用者或放置檔案至此資料夾的應用程式中，設定寫入權限。<br />-若為 BizTalk 系統管理員群組中，設定完整控制權。<br /><br /> 對於 BizTalk Server 放置訊息的資料夾，請使用強式 DACL，如下所示：<br /><br /> -對於執行傳送配接器的主控件的主控件執行個體的服務帳戶，請設定寫入權限。<br />-若為外部使用者或應用程式放置檔案至此資料夾，讀取權限集。<br />-若為 BizTalk 系統管理員群組中，設定完整控制權。|  
|未經授權的使用者可以提交訊息到 BizTalk Server|拒絕服務<br /><br /> 權限提高|5.2|依稍早所示設定接收位置放置目錄中的強式 DACL。|  
  
## <a name="see-also"></a>另請參閱  
 [威脅模型分析](../core/threat-model-analysis.md)   
 [威脅模型分析的範例案例](../core/sample-scenarios-for-threat-model-analysis.md)   
 [中小型公司的架構範例](../core/sample-architectures-for-small-medium-sized-companies.md)