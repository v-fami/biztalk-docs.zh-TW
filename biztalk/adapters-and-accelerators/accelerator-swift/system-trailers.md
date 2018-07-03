---
title: 系統結尾 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- trailers [SWIFT]
- SWIFT, trailers
ms.assetid: 2fd49be9-afe8-47c6-a613-fa469faa2126
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d991125654e04167b026aa98c62c8ffdc7b2b8e2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006015"
---
# <a name="system-trailers"></a>系統結尾
系統結尾會傳達額外或特殊 SWIFT 的訊息的詳細資料。 如果有任何第三個系統結尾會出現，以下列順序發生。 其餘系統結尾可以任何順序出現。  
  
|結尾程式碼|[屬性]|  
|------------------|----------|  
|**CHK**|總和檢查碼|  
|**SYS**|系統產生的訊息|  
|**TNG**|訓練|  
|**PDM**|可能的重複訊息|  
|**DLM**|延遲的訊息|  
|**MRF**|訊息參考|  
  
- **系統會產生訊息 (SYS) 結尾。** 系統訊息或服務的訊息，由 PLT 系統產生，有 SYS 結尾。 所有請求服務識別碼為 01 的系統訊息，包含要求的 MIR，而且可能包含的時間。  
  
   下列程式碼是 SYS 結尾格式範例：  
  
  ```  
  {SYS:[<time><mir>]}  
  ```  
  
- **測試與定型訊息 (TNG) 結尾。** TNG 結尾是 FIN 和 GPA 訊息 （具有 01 的服務識別項） 傳送，或傳遞至測試和訓練邏輯終端機 (LT) 的必要步驟。 此結尾則具有標記，且沒有值。  
  
   下列程式碼是 TNG 結尾格式範例：  
  
  ```  
  {TNG:}  
  ```  
  
- **可能的重複發出 (PDE) 結尾。** 訊息的目的地會使用 PDE 結尾。 它只適用於 FIN 使用者對使用者的訊息 （01 的服務識別項），保留銀行訊息的訊息分類。 系統可能包含多個 PDEs。 系統不確定的順序不限制數目 （除了訊息最大長度）。  
  
   系統會接受套用至使用者對系統訊息的格式正確 PDE 結尾，但不會處理它們。 這表示系統不會檢查原始訊息是否存在。 因此，系統可能會處理兩次以 PDE 結尾傳送擷取要求，如果系統接收原始訊息。  
  
   下列程式碼是 PDE 結尾格式範例：  
  
  ```  
  {PDE:[<time><mir>]}  
  where <time><mir> refers to the emission of the previous possible issue  
  ```  
  
- **延遲的訊息 (DLM) 結尾。** DLM 結尾會新增至所有已超過其過時期的 FIN 使用者對使用者輸出訊息。 如果此結尾會出現在 GPA 或 FIN 系統訊息，您可以忽略它。 此結尾則具有標記，且沒有值。  
  
   過時週期如下所示：  
  
  - U = 15 分鐘  
  
  - N = 100 分鐘  
  
    下列程式碼是 DLM 結尾格式範例：  
  
  ```  
  {DLM:}  
  ```  
  
- **可能的重複訊息 (PDM) 結尾。** PDM 結尾加入輸出訊息 （GPA 和服務識別碼為 01 的 FIN） 系統正在重新傳送，因為先前的傳遞可能無效。 如果系統 PLT 收到報表要求以 PDM 結尾時，回應會具有純文字的 PDM （不含選擇性傳遞參考）。 其他 PDMs 可能由於不成功的傳遞嘗試新增至使用者。  
  
   下列程式碼是 PDM 結尾格式範例：  
  
  ```  
  {PDM:[<time><mor>]}  
  where <time> and the Message Output Reference <mor> are that of the previous attempt  
  ```  
  
- **訊息參考 (MRF) 結尾。** MRF 結尾 MT 096 FIN 複本集中的機構訊息中指定原始使用者訊息的訊息的參考。  
  
   下列程式碼是 MRF 結尾格式範例：  
  
  ```  
  {MRF:<date><full-time><mir>}  
  where <mir> is that of the original user message whose fields are copied in the MT 096 FIN  
  Copy to Central Institution Message  
  ```  
  
  > [!NOTE]
  >  MRF 結尾是特有 FIN 複製，而且會自動產生 MT 096 FIN 複本集中的機構訊息中。 只有，您可以使用欄位 109 的 MT 096 FIN 複製到中央的機構訊息中此結尾來識別要 MT 097 是回應 MT 096。 MRF 的格式可能會變更。  
  
## <a name="see-also"></a>另請參閱  
 [使用結構描述](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)