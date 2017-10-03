---
title: "系統結尾 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- trailers [SWIFT]
- SWIFT, trailers
ms.assetid: 2fd49be9-afe8-47c6-a613-fa469faa2126
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0a8c5b7be12a90aa2d31e828298cf7b95834036
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="system-trailers"></a>系統結尾
系統結尾會傳達額外或特殊 SWIFT 訊息有關的詳細資料。 若有任何第三個系統結尾沒有，請依下列順序發生。 剩餘的系統結尾可以任何順序出現。  
  
|結尾程式碼|名稱|  
|------------------|----------|  
|**CHK**|總和檢查碼|  
|**SYS**|系統會產生訊息|  
|**TNG**|訓練|  
|**PDM**|可能的重複訊息|  
|**DLM**|延遲的訊息|  
|**MRF**|訊息參考|  
  
-   **系統會產生訊息 (SYS) 結尾。** 系統訊息或服務的訊息，由 PLT 系統產生，其中有 SYS 結尾。 所有請求系統訊息的 01 的服務識別碼，包含要求的 MIR 且可能包含時間。  
  
     下列程式碼是 SYS 結尾格式的範例：  
  
    ```  
    {SYS:[<time><mir>]}  
    ```  
  
-   **測試與定型訊息 (TNG) 結尾。** TNG 結尾會強制 FIN 和 GPA 訊息 （具有 01 的服務識別項），由傳送或傳送至測試和定型邏輯終端機 (LT)。 這個結尾則具有標記，且沒有值。  
  
     下列程式碼是 TNG 結尾格式的範例：  
  
    ```  
    {TNG:}  
    ```  
  
-   **可能的重複發出 (PDE) 結尾。** 訊息的目的地會使用 PDE 結尾。 它只適用於 FIN 使用者的訊息 （01 的服務識別項），保留供銀行訊息的訊息類別。 系統可能包含多個 PDEs。 系統不確定的順序不會限制 （除了訊息最大長度） 數目。  
  
     系統會接受套用至使用者的系統訊息的格式正確 PDE 結尾，但不會處理它們。 這表示系統不會檢查原始訊息是否存在。 因此，系統可能會處理兩次傳送以 PDE 結尾的擷取要求，如果系統接收原始訊息。  
  
     下列程式碼是 PDE 結尾格式的範例：  
  
    ```  
    {PDE:[<time><mir>]}  
    where <time><mir> refers to the emission of the previous possible issue  
    ```  
  
-   **延遲的訊息 (DLM) 結尾。** DLM 結尾會加入至所有已超過其陳舊過時期間的 FIN 使用者的輸出訊息。 如果這個結尾出現在 GPA 或 FIN 系統訊息，您可以忽略它。 這個結尾則具有標記，且沒有值。  
  
     過時週期如下所示：  
  
    -   U = 15 分鐘  
  
    -   N = 100 分鐘  
  
     下列程式碼是 DLM 結尾格式的範例：  
  
    ```  
    {DLM:}  
    ```  
  
-   **可能的重複訊息 (PDM) 結尾。** 系統會新增 PDM 結尾 （GPA 和 FIN 01 的服務識別項） 的任何輸出訊息正在重新傳送，因為先前的傳遞可能無效。 如果系統 PLT 收到報表要求以 PDM 結尾時，回應會具有一般 PDM （不含選擇性傳遞參考）。 其他 PDMs 可能由於不成功的傳遞嘗試新增至使用者。  
  
     下列程式碼是 PDM 結尾格式的範例：  
  
    ```  
    {PDM:[<time><mor>]}  
    where <time> and the Message Output Reference <mor> are that of the previous attempt  
    ```  
  
-   **訊息參考 (MRF) 結尾。** MRF 結尾 MT 096 FIN 複製到中央機構訊息中指定原始使用者訊息的訊息的參考。  
  
     下列程式碼是 MRF 結尾格式的範例：  
  
    ```  
    {MRF:<date><full-time><mir>}  
    where <mir> is that of the original user message whose fields are copied in the MT 096 FIN  
    Copy to Central Institution Message  
    ```  
  
    > [!NOTE]
    >  MRF 結尾是特有 FIN 複本，而且會自動產生 MT 096 FIN 複本中央機構訊息中。 您只能識別 MT 097 是回應 MT 096 欄位 109 MT 096 FIN 複製的中央機構訊息中使用這個結尾。 MRF 的格式會隨時變更。  
  
## <a name="see-also"></a>另請參閱  
 [使用結構描述](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)