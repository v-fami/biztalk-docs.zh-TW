---
title: 使用任意文字的字元編碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a69dffe1-3fb2-4902-a9a2-093f3ea7b11f
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02294e089eef6fa541f7e5bbcd2864c6f1bf023d
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "25961636"
---
# <a name="encoding-characters-using-free-text"></a>使用任意文字的字元編碼
從開始[!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)]，「 FreeText"可用欄位或區段中。 無法剖析 「 FreeText"欄位/區段中的資料。  
  
## <a name="what-you-need-to-know"></a>您需要知道  
  
||行為|範例|  
|-|--------------|-------------|  
|~: 重複分隔符號|在欄位中，重複 （~） 會被視為重複分隔符號。 在非可用的區段中，重複 （~） 會被視為重複分隔符號。 可用的區段中，重複 （~） 會被視為任意文字，無法新增重複的一部分。|在下列範例中，FRE 是可用的區段。 它可以有任意文字，為任何字元包括 ~。 任何其他的重複項目 （~） 不會被視為重複分隔符號，並會被視為任意文字內容。 驗證成功，即使可用區段的子系是不可重複，且包含重複 （~）。 FRE 範例：<br /><br /> **FRE&#124; Foo （& s) ^&#124;Foo （& s) ^&#124;Foo （& s) ^&#124;Foo （& s) ^ ~ Foo （& s) ^&#124;Foo （& s) ^&#124;Foo （& s) ^&#124;Foo （& s) ^**<br /><br /> 在下列範例中，EVN4 定義為任意文字因為它包含*&^*。 當 「&#124;"分隔符號時，它會被視為目前的可用文字的結尾。 EVN 範例：<br /><br /> **EVN&#124;&#124;&#124;&#124;Foo （& s) ^ Foo （& s) ^ Foo （& s) ^ Foo （& s) ^ Foo （& s) ^&#124;&#124;**<br /><br /> 在下列範例中，EVN5 的第一個子系會定義為任意文字因為它包含*&*。 當"^"分隔符號時，它會被視為目前的可用文字的結尾。 EVN5 範例：<br /><br /> **EVN&#124; &#124; &#124; &#124; &#124; Foo & Foo & Foo Foo & Foo & ^5.2&#124;**<br /><br /> 在下列範例中，5.2.1 章和 5.2.2 章不可有任何分隔符號為任意文字，即使它結構描述中定義為 FreeText。 5.2.1 章和 5.2.2 章的範例：<br /><br /> **EVN&#124; &#124; &#124; &#124; &#124; Foo1 ^5.2.1 章 & 5.2.2 章&#124;**<br /><br /> 在下列範例中，假設 EVN4 可以重複，且是任意文字的類型。 *Foo1 & ^* 會被視為第一個重複和*Foo2 （& s) ^* 會被視為第二個重複。 如果不是可重複 EVN4 (MaxOccurs = 1)，則驗證會失敗，如果它包含 ~，即使它是任意文字型別 （非自由文字欄位的情況下類似）。 EVN4 範例：<br /><br /> **EVN &#124; &#124; &#124; &#124; Foo1 （& s) ^ ~ Foo2 （& s) ^&#124;&#124;**|  
|&#124;： 欄位的分隔符號|如果可用的區段的區段標記的後面遺漏欄位分隔符號，則驗證成功。|在下列範例中，FRE 是任意文字型別。 可用的文字內容可以 FRE 含，區段標記之後，立即啟動 「&#124;"欄位分隔符號。 這兩個範例會成功：<br /><br /> **FREabc** <br /> **FRE&#124;abc**<br /><br /> 在下列範例中，驗證會成功：<br /><br /> 輸入的訊息 DASM: **FRE&#124;abcd**<br />輸出來源 DASM:  **\<SegmentData\>&#124;abcd\</SegmentData\>**<br />從 ASM 輸出： **FRE&#124;abcd**<br /><br /> 輸入的訊息 DASM: **FREabcd**<br />輸出來源 DASM:  **\<SegmentData\>abcd\</SegmentData\>**<br />從 ASM 輸出： **FREabcd**|  
|父子式選擇性|父子式選擇性的驗證規則仍然適用。|假設是選擇性的父系，且其中一個子系是必要的然後：<br /><br /> -如果沒有任何其他子系和必要的子系尚未擴展，訊息驗證會成功。<br />-如果已填入至少一個子系，則強制性子應該也會填入。 否則，訊息驗證會失敗。<br /><br /> 在下列範例中，為選擇性欄位 1。 其*1.a*子是選擇性，而且是任意文字型別。 其*1.b*是必要的子系：<br /><br /> **xyz&#124;1.a^1.b&#124;2**<br /><br /> 在下列範例訊息中， *dfssdf**&** sdf*會被視為一個單一項目-1.a。 剖析器會檢查 1.b 是否存在。 當 *&#124;* 會達到，假設 1.b 就不會填入，且訊息驗證失敗：<br /><br /> **xyz&#124;dfssdf & sdf&#124;2**|  
|MSH、 FSH，以及 BSH 區段|任意文字會忽略所有的欄位。 這些區段對應至標頭區段。 驗證即使它像平常一樣，它們會定義為 任意文字。||  
|\\： 逸出字元|如果有偶數的項目中的"\"，則驗證會成功 （即使它們是不連續）。 如果有奇數，則驗證失敗。 相同的行為會繼續針對非任意文字欄位。 任意文字欄位，便無法驗證數目;它會視為任意文字內容。||  
  
 [訊息分隔符號](../../adapters-and-accelerators/accelerator-hl7/message-delimiters.md)提供這些範例中的分隔符號的詳細資訊。  
  
## <a name="using-free-text"></a>使用任意文字  
  
1.  在 Visual Studio 中的專案，開啟結構描述。  
  
2.  以滑鼠右鍵按一下記錄，選取**插入結構描述節點**，選取**子欄位項目**。  
  
3.  在內容中，選取**資料型別**，然後選取**任意文字 (SimpleType)**。  
  
## <a name="see-also"></a>另請參閱  
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)