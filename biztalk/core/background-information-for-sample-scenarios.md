---
title: "背景資訊的範例案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security examples [TMA], background information
- DFD
- TMA, examples
ms.assetid: f9518fe7-9892-44f5-8e05-fe48bdb5161a
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13dbb247e42116d5b308170d5ef365ed9f20d793
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="background-information-for-sample-scenarios"></a>範例實例的背景資訊
本主題包含本節中實例的背景資訊。  
  
## <a name="background-for-all-scenarios"></a>所有實例的背景  
 在召開主要威脅模型會議之前，我們先收集下列背景資訊。 此資訊適用於我們為範例架構識別的所有使用實例：  
  
-   架構的界限與範圍  
  
-   信任與不信任元件之間的界限  
  
-   每個元件的組態與管理模型  
  
-   其他元件與應用程式的相關假設  
  
### <a name="boundaries-and-scope-of-the-architecture"></a>架構的界限與範圍  
  
-   防火牆 2 協助從環境中的周邊網路與任何其他網域 (例如公司網域或其他應用程式的網域)，來保護電子商務網域中的伺服器與應用程式。  
  
-   防火牆 2 路由所有輸入與輸出流量至電子商務網域。  
  
-   存取 BizTalk Server 環境的所有使用者群組與帳戶都必須是電子商務網域中的全域群組。  
  
-   限制主控件執行個體服務帳戶的存取；僅限放置訊息在檔案、SQL 或訊息佇列接收伺服器的任何應用程式；以及 BizTalk Server、企業單一登入 (SSO) 與 Windows 的系統管理員。  
  
### <a name="boundaries-between-trusted-and-untrusted-companies"></a>信任與不信任公司之間的界限  
  
-   防火牆 2 路由所有輸入與輸出流量至電子商務網域。  
  
-   使用不同的 BizTalk 主控件做為 BizTalk Server 中應用程式之間的安全性界限。  
  
-   只有當您信任應用程式中的程式碼時才使用信任的主控件 (例如，不要在信任的主控件中執行協力廠商元件)。  
  
### <a name="configuration-and-administration-model-for-each-component"></a>每個元件的組態與管理模型  
 **組態模型：**  
  
-   BizTalk Server 執行階段元件只安裝在 BizTalk Server 上。  
  
-   主要密碼伺服器沒有其他元件。  
  
-   SQL Server 包含所有 BizTalk Server 資料庫。  
  
-   周邊網路中的伺服器沒有任何 BizTalk Server 元件。  
  
-   管理用戶端是用來管理電子商務網域中的所有伺服器。  
  
 **系統管理模型：**  
  
-   系統管理員從桌上型 (或膝上型) 電腦連接到擁有管理工具的電腦 (使用「終端服務」或「遠端桌面」連線)。 系統管理員連接到擁有管理工具的電腦之後，系統管理員便可使用 BizTalk 管理工具，來管理網域中所有的伺服器與應用程式。  
  
### <a name="assumptions-about-other-components-and-applications"></a>其他元件與應用程式的相關假設  
 與 BizTalk Server 環境互動的所有其他應用程式與元件在電子商務網域以外的網域中 (例如在周邊網路)。 從那些應用程式與元件往返 BizTalk Server 環境的流量都會通過防火牆 2。  
  
 BizTalk Server 的任何協力廠商應用程式都來自信任的廠商。  
  
### <a name="data-flow-diagrams"></a>資料流程圖  
 每個使用實例的背景資訊的最終項目是資料流程圖 (DFD)。 DFD 說明資料如何通過此架構。 每個實例都有不同的 DFD。 在此文件中，資料流程圖包含下圖所示的項目。  
  
 **圖 1 DFD 的項目**  
  
 ![DFD 的項目](../core/media/tdi-sec-dfd-legend.gif "TDI_Sec_DFD_Legend")  
  
## <a name="background-for-adapter-scenarios"></a>配接器實例的背景  
 在範例架構中，我們根據您可用的一些配接器來識別下列使用實例：  
  
-   HTTP 與 SOAP (Web 服務) 配接器實例  
  
-   BizTalk 訊息佇列配接器實例  
  
-   FILE 配接器實例  
  
-   FTP 配接器實例  
  
 對於每個實例，我們遵循下列步驟來完成威脅模型分析：  
  
-   收集背景資訊  
  
-   建立和分析威脅模型  
  
-   檢視威脅  
  
-   識別防護技巧與技術  
  
 對於每個實例，我們已經嘗試開發各種攻擊可能代表的一般威脅層級的評比等級。 不過，您所在的環境或經驗可能讓您覺得特定的威脅應該不同於我們所提供的評比等級。 至於所有的安全性實例，您自己所擁有的資料對於決定威脅層級是最可信的，所以建議您使用我們的分析與結果做為指南，進行自己的分析。  
  
 背景資訊，除了資料流程圖 (DFD) 之外，也適用於所有使用實例。 下一節將顯示每個實例的 DFD。  
  
## <a name="see-also"></a>另請參閱  
 [威脅模型分析](../core/threat-model-analysis.md)   
 [威脅模型分析的範例案例](../core/sample-scenarios-for-threat-model-analysis.md)   
 [安全性規劃](../core/planning-for-security.md)   
 [小型與中型公司的範例架構](../core/sample-architectures-for-small-medium-sized-companies.md)