---
title: "EDI 支援中 BizTalk Server2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d4f50a9-fc55-400c-a63c-40b697425fea
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6162276e5e394bd17b75825535ddaf097a7f589c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="edi-support-in-biztalk-server"></a>BizTalk Server 中的 EDI 支援
不同的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 版本透過以下不同的功能和元件支援 EDI：  
  
|版本|提供 EDI 支援的元件/功能|  
|---|---|  
|[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]以及所有較新版本|原生 EDI 功能|  
|[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]|基底 EDI 配接器|  
|[!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)]|基底 EDI 配接器|  
|[!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]|原生 EDI 功能|  
  
## <a name="feature-set-comparison-chart"></a>功能集合比較表  
 下表顯示從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 版本中的 EDI 元件/功能所提供的 EDI 支援。 ‘Y’ 表示支援該功能，‘N’ 表示不支援該功能。  
  
|功能|[!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] - [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]|[!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] - [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]|[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]|BizTalk Server 2009|BizTalk Server 2010|註解|  
|---|---|---|---|---|---|---|  
|在交易集修改 ISA 區段|Y|N|Y|Y|Y|稍後在 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 中建立 TransactionSet 特有協議才提供這項支援。|  
|ISA11： 美國或其他標準類型|Y|N|Y|Y|Y|-|  
|ISA12： 交換控制版本|Y|N|Y|Y|Y|-|  
|ISA13： 交換控制編號 （遞增編號）|Y|N|Y|Y|Y|-|  
|ISA15： 測試或實際執行|Y|N|Y|Y|Y|-|  
|在文件/交易層級修改 GS 區段|Y|N|Y|Y|Y|-|  
|GS 傳送者/接收者識別碼可以是與 ISA 不同|Y|N|Y|Y|Y|-|  
|不同於 ISA 與 GS 輸出識別的輸入文件識別碼|Y|N|Y|Y|Y|-|  
|變更類型的文件的能力 GS01:|Y|N|Y|Y|Y|-|  
|GS04： 日期 （變更格式的能力）|N|N|Y|Y|Y|[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 及更新版本會包含可選取 CCYYMMDD 和 YYMMDD 日期格式的 UI|  
|GS05： 時間 （變更格式的能力）|N|N|Y|Y|Y|[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 及更新版本包含可選取 HHMM、HHMMSS 和 HHMMSSdd 時間格式的 UI|  
|GS06： 變更控制編號|Y|N|Y|Y|Y|-|  
|GS07： 代理程式碼|Y|N|Y|Y|Y|-|  
|GS08： 能夠放在標準版本|Y|N|Y|Y|Y|-|  
|覆寫 EDI 信封，在執行階段功能|N|N|N|Y|Y|-|  
|自訂 EDI 結構描述|Y|N|Y|Y|Y|-|  
|組織/合作對象設定|Y|Y (最小)|Y|Y|Y|[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 和 BizTalk Server 2009 可讓您根據範本建立合作對象。<br /><br /> BizTalk Server 2010 以更新版本將合作對象和協議分開處理，因此方式有變。 可讓建立協議範本為基礎。|  
|透過文件定義路由的 EDI 文件|Y|-|Y|Y|Y|-|  
|自動 997 交易夥伴|Y|Y|Y|Y|Y|在 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 和 BizTalk Server 2009 中透過合作對象專屬的組態提供這項支援。<br /><br /> 在 BizTalk Server 2010 及更新版本中透過商務設定檔專屬的組態提供這項支援。|  
|可信賴傳訊透過 997 輸出 EDI|Y|Y|Y|Y|Y|-|  
|EDIFACT 支援|Y|Y (最小)|Y|Y|Y|在 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 及更新版本中提供這項支援 (根據 ISO 9735 v4.1，D93 至 D05)|  
|X12 支援|Y|Y (最小)|Y|Y|Y|在 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 和更新版本中提供這項支援 (2040 到 5030)|  
|HIPAA 支援|N|Y (在[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)])|Y|Y|Y|中支援[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]為 Microsoft BizTalk Accelerator for HIPAA (BTAHIPAA) 3.3。 在 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 和更新版本中以部分原生 EDI 功能的形式提供這項支援。|  
|若要移除列舉值/程式碼清單的能力|Y|N|Y|Y|Y|在 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]和更新版本中由 Visual Studio/BizTalk 編輯器提供這項支援|  
|AS2 傳送/接收|N|N|Y|Y|Y|在 BizTalk Server 2009 和更新版本中，AS2 在 Crummond Certified 標準： 多個檔案附件支援、 檔案名稱保留支援和互通性。|  
|AS2 檔案名稱的保留|N|N|N|Y|Y|-|  
|AS2 可信賴傳訊|N|N|N|Y|Y|-|  
|可以移轉[!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]至 EDI 儲存機制的自訂 XDR EDI 結構描述|-|N|N|N|N|您必須將基底 EDI 應用程式移轉至 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 或 BizTalk Server 2009，然後使用「合作對象移轉」工具，將應用程式移轉至 BizTalk Server 2010 及更新版本。|  
|輸出批次處理 （累積多種交易類型，在單一交易中）|N|N|Y|Y|Y|BizTalk Server 2009 和更新版本支援讓每個商務設定檔擁有多個批次組態。|  
|輸入批次處理： 交換 XML （保留內送的 「 批次 」 交換） 或根據組態選項的交易集 XML|N|N|Y|Y|Y|在 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 和更新版本中，這是支援輸入-解除批次處理 (亦即將交換分割成個別交易集 XML) 以外的支援|  
|交換和交易集產生和驗證 Visual Studio 中於設計階段|N|N|Y|Y|Y|-|  
|TA1 （技術通知） 的產生和重新調整|N|N|Y|Y|Y|-|  
|選用的 EDI 和 XSD 驗證旗標|N|N|Y|Y|Y|-|  
|文件格式/定義 GS 層級|N|N|Y|Y|Y|-|  
  
## <a name="see-also"></a>另請參閱  
 [EDI 標準支援](../core/edi-standards-support.md)   
 [EDI 文件結構描述支援](../core/edi-document-schema-support.md)   
 [EDI 字元集支援](../core/edi-character-set-support.md)