---
title: 支援的配接器 XSD 項目類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00691a9e-434f-4baa-9a01-b6f452758ab3
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3992ecface8fafacb5e1e616c930178ad0ce33a7
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22279390"
---
# <a name="supported-adapter-xsd-element-types"></a>支援的配接器 XSD 項目類型
下表列出配接器架構支援的項目。 在組態結構描述中定義新的項目時，請使用下列任何類型取代以下範例中的 `string`：  
  
```  
<xs:element name="uri" type="xs:string">  
```  
  
|型別|XML 類型|UI 行為|其他特性|  
|----------|--------------|-----------------|---------------------|  
|string|無|僅限編輯方塊接受類型。|可限制最大/最小值的屬性|  
|normalizedString|無|僅限編輯方塊接受類型。|可限制最大/最小值的屬性|  
|integer|無|僅限編輯方塊接受類型。|可限制最大/最小值的屬性|  
|positiveInteger|無|僅限編輯方塊接受類型。|可限制最大/最小值的屬性|  
|negativeInteger|無|僅限編輯方塊接受類型。|可限制最大/最小值的屬性|  
|nonNegativeInteger|無|僅限編輯方塊接受類型。|可限制最大/最小值的屬性|  
|nonPositiveInteger|無|僅限編輯方塊接受類型。|可限制最大/最小值的屬性|  
|int|無|僅限編輯方塊接受類型。|可限制最大/最小值的屬性|  
|unsignedInt|無|僅限編輯方塊接受類型。|可限制最大/最小值的屬性|  
|long|無|僅限編輯方塊接受類型以及小數。|可限制最大/最小值的屬性|  
|unsignedLong|無|僅限編輯方塊接受類型以及小數。|可限制最大/最小值的屬性|  
|short|無|僅限編輯方塊接受類型。|可限制最大/最小值的屬性|  
|unsignedShort|無|僅限編輯方塊接受類型。|可限制最大/最小值的屬性|  
|decimal|無|僅限編輯方塊接受類型。|可限制最大/最小值的屬性|  
|float|無|僅限編輯方塊接受類型。|可限制最大/最小值的屬性|  
|double|無|僅限編輯方塊接受類型。|可限制最大/最小值的屬性|  
|boolean|無|填入布林值的下拉式清單。|無|  
|time|無|僅限編輯方塊接受類型。|無|  
|dateTime|無|僅限編輯方塊接受類型。 省略符號會在欄位區域結尾出現。 按一下省略符號，即出現日曆。|無|  
|date|無|僅限編輯方塊接受類型。 省略符號會在欄位區域結尾出現。 按一下省略符號，即出現日曆。|無|  
|gMonth|無|僅限編輯方塊接受類型。|這個值是字串，因此執行狀況可能不如預期。 請考慮改用具有保留月值之限制的 xsd:int 類型。|  
|gYear|無|僅限編輯方塊接受類型。|這個值是字串，因此執行狀況可能不如預期。 請考慮改用具有保留年值之限制的 xsd:int 類型。|  
|gYearMonth|無|僅限編輯方塊接受類型。|這個值是字串，因此執行狀況可能不如預期。 請考慮改用具有保留年和月值之限制的 xsd:int 類型。|  
|gDay|無|僅限編輯方塊接受類型。|這個值是字串，因此執行狀況可能不如預期。 請考慮改用具有保留日值之限制的 xsd:int 類型。|  
|gMonthDay|無|僅限編輯方塊接受類型。|這個值是字串，因此執行狀況可能不如預期。 請考慮改用具有保留月和日值之限制的 xsd:int 類型。|  
|名稱|無|僅限編輯方塊接受類型。|無|  
|NCName|無|僅限編輯方塊接受類型。|無|  
|anyURI|無|僅限編輯方塊接受類型。|無|  
|序列|"Sequence" 結構描述項目|無|無|  
|群組|無|可展開或摺疊群組中所有欄位的 "+" 或 "-" 符號。<br /><br /> 屬性頁右邊沒有編輯功能。|無|  
|檔案名稱|FileName|省略符號會在欄位區域結尾出現。 按一下省略符號和 **Windows FileOpen** 對話方塊隨即出現，讓您選取的檔案。|無|  
|資料夾名稱|FolderName|省略符號會在欄位區域結尾出現。 按一下省略符號和 **Windows 資料夾開啟** 會出現對話方塊讓您選取的資料夾。|無|  
|SSO 應用程式識別碼|SSOAppID|填入 SSO 應用程式清單的下拉式清單|無|  
|密碼|密碼|顯示 "*" 而非純文字的編輯方塊。|無|  
  
## <a name="see-also"></a>另請參閱  
 [配接器設計問題](../core/adapter-design-issues.md)