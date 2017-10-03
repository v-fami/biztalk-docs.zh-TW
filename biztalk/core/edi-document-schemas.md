---
title: "EDI 文件結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc3a30b8-0686-4c06-985b-13f2c95f8e99
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db79e5e4421719a936f68c409c166f9eac38605c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="edi-document-schemas"></a>EDI 文件結構描述
文件結構描述定義了 EDI 交易文件類型的內文。  
  
## <a name="schema-delivery-and-setup"></a>結構描述傳遞和設定  
 傳送 EDI 文件結構描述中的自動解壓縮可執行檔的壓縮狀態[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\MicrosoftEdiXSDTemplates.exe。 自動解壓縮可執行檔可確保建立適當的資料夾結構 (根據各種編碼類型與版本/版次的子類型)。 可執行檔執行時，會將 EANCOM、 EDIFACT、 HIPAA 和 X12 結構描述可執行檔相同的目錄中的子資料夾。  
  
 預設結構描述命名空間為：  
  
-   對於 X12-`http://schemas.microsoft.com/BizTalk/EDI/X12/2006`  
  
-   對於 EDIFACT –`http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006`  
  
## <a name="schema-naming-convention"></a>結構描述命名慣例  
 X12 和 EDIFACT 編碼類型的命名慣例是\<編碼方式 > _\<版本 >\<版本 >\_\<Doctype >。 例如，用於 X12 864 文件類型 (版本 004、版次 01) 的 X12_00401_864.xsd 結構描述，以及用於 EDIFACT AUTHOR 文件類型 (版本 D01、版次 C) 的 EDIFACT_D01C_AUTHOR.xsd 結構描述。  
  
> [!NOTE]
>  EDIFACT 結構描述的結構描述名稱是區分大小寫的。 例如，EFACT_D98B_ORDERS 和 EFACT_d98B_Orders 是兩個不同的結構描述。  
  
## <a name="schema-contents"></a>結構描述內容  
 對於 X12 編碼文件，文件結構描述是以 ST 交易集標頭開始，並以 SE 交易集結尾結束。 對於 EDIFACT 編碼文件，則是以 UNH 訊息標頭開始，並以 UNT 訊息結尾結束。 結構描述會定義這些標頭和結尾的每個資料元素。  
  
 文件結構描述會接著定義交易集/訊息內的每個區段，以及這些區段內的資料元素。 例如，X12_00401_864.xsd 結構描述會定義 BMG 區段的 BMG01、BMG02 及 BMG03 元素。 結構描述會指定區段中複雜資料類型 (例如欄位順序、分隔符號類型，以及命名空間) 的特性。 如果有區段適用的欄位交互驗證規則，結構描述便會定義這些規則。 如需詳細資訊，請參閱[跨欄位區段驗證](../core/cross-field-segment-validation.md)。  
  
 結構描述會指定區段內各個資料元素的特性，例如簡單資料類型、最少發生次數、最小長度，以及最大長度。  
  
 如果在訊息類型中有迴圈，結構描述便會定義各個迴圈內的資料元素、迴圈的最少與最多發生次數，以及迴圈屬於已繫結或未繫結狀態。 結構描述也會定義區段的巢狀方式，以及迴圈屬於明確或是隱含狀態。  
  
## <a name="see-also"></a>另請參閱  
 [EDI 訊息結構](../core/edi-message-structure.md)   
 [EDI 訊息驗證](../core/edi-message-validation.md)