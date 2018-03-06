---
title: "EDI 支援 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d4f50a9-fc55-400c-a63c-40b697425fea
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04cd9c14b9c3663bdf332155cc9824e1681ca7a6
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="edi-support-in-biztalk-server"></a>BizTalk Server 中的 EDI 支援
EDI 內建於 BizTalk Server 時，則選擇性元件安裝和設定 BizTalk Server。 
  
## <a name="feature-set-comparison-chart"></a>功能集合比較表  
 下表顯示 BizTalk Server 隨附的 EDI 支援。
  
|功能|註解|  
|---|---|
|在交易集修改 ISA 區段| 建立 TransactionSet 特有協議|  
|ISA11︰ 美國或其他標準類型| |  
|ISA12︰ 交換控制版本| |  
|ISA13︰ 交換控制編號 （遞增編號）| |  
|ISA15︰ 測試或實際執行| |  
|在文件/交易層級修改 GS 區段| |  
|GS 傳送者/接收者識別碼不可為與 ISA 不同| |  
|不同於 ISA 與 GS 輸出識別的輸入文件識別碼| |  
|GS01︰ 能夠變更的文件類型| |  
|GS04︰ 日期 （變更格式的能力）|包含可選取 CCYYMMDD 和 yymmdd 日期格式的 UI|  
|GS05︰ 時間 （變更格式的能力）|包含可選取 HHMM、 HHMMSS 和 HHMMSSdd 格式的 UI|  
|GS06︰ 變更控制編號| |  
|GS07︰ 代理程式碼| |  
|GS08︰ 能夠放在標準版本| |  
|若要覆寫在執行階段的 EDI 信封的能力| |  
|自訂 EDI 結構描述| |  
|組織/合作對象設定|建立個別的合作對象和協議。 也請建立範本為基礎的協議。|  
|透過文件定義路由 EDI 文件| |  
|交易夥伴的自動 997|特定商務設定檔組態|  
|可信賴傳訊透過 997 輸出 EDI| |  
|EDIFACT 支援|支援 D93 至 D05 ISO 9735 v4.1|  
|X12 支援|2040 到 5030|  
|HIPAA 支援| Microsoft BizTalk Accelerator for HIPAA (BTAHIPAA) 做為原生 EDI 功能的一部分|  
|移除列舉值/程式碼清單的能力|使用 Visual Studio/BizTalk 編輯器|  
|AS2 傳送/接收| AS2 是 Crummond Certified 標準： 多個檔案附件支援、 檔案名稱保留支援和互通性。|  
|AS2 檔案名稱保留| |  
|AS2 可信賴傳訊| |  
|輸出批次處理 （累積在單一交易中的多個交易類型）|支援多個批次組態的每個商務設定檔|  
|輸入批次處理： 交換 XML （保留內送的 「 批次 」 交換） 或根據組態選項的交易集 XML|也支援輸入-解除批次處理即將，亦即，交換分割成個別交易集 Xml|  
|交換和交易集產生和驗證 Visual Studio 中於設計階段| |  
|TA1 （技術通知） 的產生和重新調整| |  
|選用的 EDI 和 XSD 驗證旗標| |  
|文件格式/定義 GS 層級| |  
  
## <a name="see-also"></a>另請參閱  
 [EDI 標準支援](../core/edi-standards-support.md)   
 [EDI 文件結構描述支援](../core/edi-document-schema-support.md)   
 [EDI 字元集支援](../core/edi-character-set-support.md)