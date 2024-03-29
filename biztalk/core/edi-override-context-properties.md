---
title: EDI 覆寫內容屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d78cd56f-1e34-4503-8ee1-93b52137097f
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b66b9a2d6c2a601f40f276692ba53b732c95ec6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986567"
---
# <a name="edi-override-context-properties"></a>EDI 覆寫內容屬性
EdiOverride 全域屬性結構描述中的訊息內容屬性可用來覆寫在執行階段的 EDI 信封值。 在 edi-properties.xsd Microsoft.BizTalk.Edi.BaseArtifacts 組件中定義這些訊息內容屬性。 屬性的命名空間是 `http://schemas.microsoft.com/BizTalk/2006/edi-properties`。  
  
 EdiOverride 內容屬性也有在協調流程，只要 Microsoft.BizTalk.Edi.BaseArtifacts 組件的參考已新增至協調流程專案。  
  
|[屬性]|類型|描述|  
|----------|----------|-----------------|  
|OverrideEDIHeader|boolean|如果為 true，EDI 傳送管線會嘗試建構 EDI 信封使用 EdiOverride 屬性集合中的值。|  
|ISA01|string|授權資訊辨識符號 (X12)|  
|ISA02|string|授權資訊 (X12)|  
|ISA03|string|安全性資訊辨識符號 (X12)|  
|ISA04|string|安全性資訊 (X12)|  
|ISA05|string|交換傳送者辨識符號 (X12)|  
|ISA06|string|交換傳送者識別碼 (X12)|  
|ISA07|string|交換接收者辨識符號 (X12)|  
|ISA08|string|交換接收者識別碼 (X12)|  
|ISA09-|string|交換日期 (X12)<br /><br /> 此欄位應包含實際的日期值，而不是日期格式。|  
|ISA10|string|交換時間 (X12)<br /><br /> 此欄位應包含實際的時間值，而不是日期值。|  
|ISA11|string|交換控制標準識別項 (X12)|  
|ISA12|string|交換控制版本號碼 (X12)|  
|ISA13|string|交換控制編號 (X12)<br /><br /> 如果交換控制編號覆寫時，對應的交換結尾區段 (IEA) 將比對指定的值。|  
|ISA14|string|通知要求 (X12)|  
|ISA15|string|測試指示器 (X12)|  
|ISA16|string|元件元素分隔符號 (X12)|  
|GS01|string|功能識別項代碼 (X12)|  
|GS02|string|應用程式寄件者的程式碼 (X12)|  
|GS03|string|應用程式接收者的代碼 (X12)|  
|GS04|string|日期 (X12)<br /><br /> 此欄位應包含實際的日期值，而不是日期格式。<br /><br /> 此值應該是以 CCYYMMDD 或 YYMMDD 格式。 將使用提供的日期，即使在合作對象屬性中選取一個不同的格式提供日期。|  
|GS05|string|時間 (X12)<br /><br /> 此欄位應包含實際的時間值，而不是時間格式。<br /><br /> 此值應該是 HHMM、 HHMMSS 或 HHMMSSdd 格式。 即使的時間會比在合作對象屬性中選取一個不同的格式提供，則會使用提供的時間。|  
|GS06|string|群組控制編號 (X12)<br /><br /> 群組控制編號會覆寫時，GE 區段中的對應欄位將以符合指定的值。|  
|GS07|string|負責單位代碼 (X12)|  
|GS08|string|版本/版次/產業識別項代碼 (X12)|  
|ST02|string|交易集控制編號 (X12)<br /><br /> 如果交易集控制編號覆寫時，交易集結尾區段 (SE) 中對應的欄位將以符合這個值。|  
|所以 GenerateUNA|boolean|決定是否 EDI 傳送管線將會建立輸出的 EDIFACT 文件的 UNA 區段。<br /><br /> 如果 OverrideEdiHeader 為 true，所以 GenerateUNA 為 true，將會產生 UNA 區段。 如果 OverrideEdiHeader 為 true，而且產生 UNA 為 false，將會產生沒有 UNA 區段。<br /><br /> UNA 區段的值會依下列順序決定：<br /><br /> -EdiOverride 內容屬性，如果有 UNA 的所有屬性。<br />-如果不是所有的內容屬性都存在，並產生 UNA 區段已簽入合作對象屬性，內容屬性和合作對象屬性的組合。<br />-如果不是所有的內容屬性都存在，而且產生 UNA 區段未在合作對象屬性中，內容屬性和值的組合標準 UNA**附註：** 如果 OverrideEdiHeader 為 false，此欄位會有任何作用。|  
|UNA1|string|元件資料元素分隔符號 (EDIFACT)|  
|UNA2|string|資料元素分隔符號 (EDIFACT)|  
|UNA3|string|小數符號 (EDIFACT)|  
|UNA4|string|釋放字元 (EDIFACT)|  
|UNA5|string|重複分隔符號 (EDIFACT)|  
|UNA6|string|區段結束字元 (EDIFACT)|  
|UNA6Suffix|string|區段結束字元尾碼 (EDIFACT)|  
|UNB1_1|string|語法識別項 (EDIFACT)|  
|UNB1_2|string|語法版本號碼 (EDIFACT)|  
|UNB10|string|通訊協議識別碼 (EDIFACT)|  
|UNB11|string|測試指示符號 (EDIFACT)|  
|UNB2_1|string|寄件者識別碼 (EDIFACT)|  
|UNB2_2|string|協力廠商識別代碼辨識符號 (EDIFACT)|  
|UNB2_3|string|反向路由的位址 (EDIFACT)|  
|UNB3_1|string|收件者識別碼 (EDIFACT)|  
|UNB3_2|string|協力廠商識別代碼辨識符號 (EDIFACT)|  
|UNB3_3|string|路由的位址 (EDIFACT)|  
|UNB4_1|string|日期 (EDIFACT)<br /><br /> 此欄位應包含實際的日期值，而不是日期格式。|  
|UNB4_2|string|時間 (EDIFACT)<br /><br /> 此欄位應包含實際的時間值，而不是時間格式。|  
|UNB5|string|交換控制參考 (EDIFACT)<br /><br /> 交換控制參考會覆寫時，中的控制編號的交換結尾區段 (UNZ) 將比對指定的值。|  
|UNB6_1|string|收件者參考/密碼 (EDIFACT)|  
|UNB7|string|應用程式參考 (EDIFACT)|  
|UNB8|string|處理優先順序代碼 (EDIFACT)|  
|UNB9|string|通知要求 (EDIFACT)|  
|GenerateUNG|boolean|決定是否 EDI 傳送管線將會建立輸出的 EDIFACT 文件的 UNG 區段。<br /><br /> 如果 OverrideEdiHeader 為 true，而且 GenerateUNG 為 true，將會產生 UNG 區段。 如果 OverrideEdiHeader 為 true，且產生 UNG 為 false，就會不產生任何 UNG 區段。<br /><br /> UNG 區段的值會依下列順序決定：<br /><br /> -EdiOverride 內容屬性，如果存在 UNG 的所有屬性。<br />-如果不是所有的內容屬性都存在，並產生 UNG 區段已簽入合作對象屬性，內容屬性和合作對象屬性的組合。<br />-如果不是所有的內容屬性都存在，而且產生 UNG 區段未在合作對象屬性中，內容屬性和值的組合標準 UNA**附註：** 如果 OverrideEdiHeader 為 false，此欄位會有任何作用。|  
|UNG1|string|訊息群組識別碼 (EDIFACT)|  
|UNG2_1|string|應用程式傳送者識別碼 (EDIFACT)|  
|UNG2_2|string|識別代碼辨識符號 (EDIFACT)|  
|UNG3_1|string|應用程式收件者識別碼 (EDIFACT)|  
|UNG3_2|string|識別代碼辨識符號 (EDIFACT)|  
|UNG4_1|string|在日期的準備工作 (EDIFACT)<br /><br /> 此欄位應包含實際的日期值，而不是日期格式。|  
|UNG4_2|string|準備 (EDIFACT) 時間<br /><br /> 此欄位應包含實際的時間值，而不是時間格式。|  
|UNG5|string|群組參考編號 (EDIFACT)<br /><br /> 群組參考編號覆寫時，如果群組結尾區段 (UNE) 中對應的欄位將以符合指定的值。|  
|UNG6|string|控管單位自動程式碼 (EDIFACT)|  
|UNG7_1|string|訊息版本號碼 (EDIFACT)|  
|UNG7_2|string|訊息版次號碼 (EDIFACT)|  
|UNG7_3|string|關聯指定代碼 (EDIFACT)|  
|UNG8|string|應用程式密碼 (EDIFACT)|  
|UNH1|string|訊息參考編號 (EDIFACT)<br /><br /> 訊息參考編號會覆寫時，訊息結尾區段 (UNT) 中對應的欄位將以符合這個值。|  
  
## <a name="edioverride-context-property-usage"></a>EDIOverride 內容屬性使用方式  
 如果**OverrideEdiHeader**內容屬性為 true 時，EDIOverride 內容屬性中指定的值將用來建立外寄訊息的 EDI 信封。 如果 EDIOverride 內容屬性會不指定任何值，將會使用對應的合作對象或全域屬性。  
  
 EDIOverride 內容屬性所指定值必須符合 X12 或 EDIFACT 標準以及任何服務結構描述延伸模組有效。  
  
- 欄位應該包含有效的值，該欄位的類型，包括服務結構描述的擴充功能。  
  
- 控制編號必須是有效的型別，但不是需要是以現有的合作對象設定的序列中下一步。  
  
- 日期和時間欄位應該包含日期和時間值，並會根據相關的 EDI 標準有效，即使值格式不符合合作對象設定中定義的格式。  
  
  單一交易或批次 EDI 傳送管線所傳送的訊息時，只支援某些 EDIOverride 內容屬性。 下表列出支援的內容屬性以取得每個訊息類型：  
  
|正在傳送的 EDI 交易|支援的 EDIOverride 內容屬性|  
|--------------------------------|----------------------------------------------|  
|單一交易集|-所有的 Isa<br />-所有 GSs<br />-ST02<br />-所以 GenerateUNA<br />-所有 UNAs<br />-所有 UNBs<br />-GenerateUNG<br />-所有 UNGs<br />-UNH1|  
|批次處理協調流程所發行的批次交易集或發行的 EDI 接收管線的批次輸入批次輸出交易集|-所有的 Isa<br />-GS04<br />-GS05<br />-所以 GenerateUNA<br />-所有 UNAs<br />-所有 UNBs<br />-GenerateUNG<br />-UNG4.1<br />-UNG4.2|  
  
 也可以將 EDIOverride 內容屬性套用至將會批次處理的訊息，但批次處理協調流程只支援 ST01 和 UNH1 EDIOverride 內容屬性。  
  
## <a name="see-also"></a>另請參閱  
 [開發和設定 BizTalk Server EDI 解決方案](../core/developing-and-configuring-biztalk-server-edi-solutions.md)