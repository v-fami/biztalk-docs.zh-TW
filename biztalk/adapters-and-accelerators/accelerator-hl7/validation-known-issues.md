---
title: 驗證的已知問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- known issues, validating
- validating, known issues
ms.assetid: 136596f2-ee0f-4ea9-918c-3608f2ee1be3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73cc1caa3207901780a57e7b1213215217b73326
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010575"
---
# <a name="validation-known-issues"></a>驗證的已知問題
本節包含可協助您避免驗證錯誤的有用資訊。  
  
## <a name="disabling-xml-validation"></a>停用的 XML 驗證  
 驗證主體使用者分佈 旗標在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管控制 XML 內文驗證，而且不包含未預期的分隔符號與尾端分隔符號的驗證。 如果訊息沒有適當的分隔符號，訊息無法成功剖析。 如果訊息無法順利剖析，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]無法產生有效的中繼 XML。 停用 [驗證的主體使用者分佈] 旗標會產生下列：  
  
1.  空的必要的欄位。  
  
2.  未驗證的資料類型。  
  
3.  不會驗證區段結構 （不會驗證區段的順序）。  
  
## <a name="v2xml-acks-with-multiple-errors-will-fail-validation"></a>V2。有多個錯誤的 XML 通知將無法通過驗證  
 如果內送的 V2。XML 訊息包含多個錯誤，Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 剖析器可能會產生 V2。XML 通知 (ACK) 與 [錯誤] 欄位中的多個錯誤。 V2。XML 通知將無法通過驗證，因為 HL7 標準可讓您指定剖析器可以報告在 V2 中的一個錯誤。XML 通知錯誤的欄位。  
  
## <a name="two-parsing-errors-are-logged-when-messages-in-the-batch-inbatch-out-scenario-contain-validation-errors"></a>兩個剖析錯誤會記錄當批次中的訊息在批次出案例包含驗證錯誤  
 當第一個訊息批次中 / 批次出案例 （不含批次標頭中批次處理多個訊息） 包含驗證錯誤，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]記錄在事件記錄檔中的兩個錯誤。 第一個錯誤的批次中的第一個訊息並第二個錯誤與訊息的其餘部分。  
  
## <a name="restrictions-in-validating-field-length"></a>驗證欄位長度的限制  
 HL7 元件和子元件包括複雜資料型別相關聯的欄位。 HL7 規則指定的長度和欄位層級，而不是在元件/子元件層級的選用性。 比方說在 V2.4，HL7 控管 MSH3 是 HD 的資料型別和 180 個字元的最大長度。 HD 是 HD1 集現況、 HD2 集為 ST，以及 HD3 設為識別碼的複合資料類型 欄位長度限制表示三個元件 （包括兩個元件分隔符號） 中的資料應該要小於或等於 180。 不過，未指定三種資料類型的選用性;這表示所有或部分元件可能存在。 此外，ST 和 IS 的資料類型所定義的使用者，因此[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]無法留意長度散發，跨三個元件，因為它們通常是定義站台。  
  
 由於這些和其他的複雜度，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不會驗證欄位長度。 不過，您可以將長度限制在每個個別元件/子元件 （資料類型的簡單） 使用 「 BizTalk 編輯器中套用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 將會驗證這些在處理期間。  
  
## <a name="validation-of-batch-and-file-headerstrailers-are-affected-by-enabling-fragmentation"></a>啟用片段會影響批次和檔案的標頭/結尾的驗證  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 當 FHS3 欄位包含已啟用的分散程度的合作對象時，不會驗證批次和檔案的標頭/結尾。  
  
## <a name="see-also"></a>另請參閱  
 [已知問題](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)