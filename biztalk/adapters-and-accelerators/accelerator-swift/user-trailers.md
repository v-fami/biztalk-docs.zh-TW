---
title: "使用者結尾 |Microsoft 文件"
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
ms.assetid: 340d9fc8-467b-4cba-b69f-eb761767deaa
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4dc2d7f2a3dd21d35bb33fa625f59aa27c04e656
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="user-trailers"></a>使用者結尾
使用者的結尾，除了 CHK 結尾是選擇性的存在時，依下列順序發生：  
  
|結尾程式碼|名稱|  
|------------------|----------|  
|MAC|訊息驗證碼|  
|PAC|專屬的驗證碼|  
|CHK|總和檢查碼|  
|TNG|訓練|  
|PDE|可能的重複發出|  
  
-   **訊息驗證碼 (MAC) 結尾。** 可讓接收的使用者驗證。 MAC 結尾後面驗證結果。 這個結尾會強制 FIN 應用程式中的大部分使用者的訊息分類。  
  
     使用 FIN 複製服務時，PAC 結尾 （如果有的話） 會遵循 MAC 結尾。 下列程式碼是 MAC 結尾的範例：  
  
    ```  
    {MAC:<authentication-result>}  
    where <authentication-result> = 8!h  
    ```  
  
-   **專屬的驗證程式碼 (PAC) 尾端。** PAC 結尾被使用雙重驗證選項時，才使用 FIN 複製服務。 區塊 5 FIN 使用者的訊息包含 MAC 結尾之後立即 PAC 結尾，如果有的話。 如果有的話，此結果計算上擷取的區塊 4 115，欄位的值，訊息的欄位和\<驗證結果 > MAC 結尾複製服務使用雙重驗證。  
  
     如此一來，end 區塊的指標 （CrLf-） 納入 PAC 計算，且在定義欄位，如下所示：  
  
    -   前四個字元都是 CrLf:  
  
    -   欄位和分隔符號都存在，也就是 32A: 20，:，依此類推。  
  
    -   所有的子欄位和分隔符號會呈現。  
  
     下列程式碼是 PAC 結尾格式的範例：  
  
    ```  
    {PAC:[<authentication-result>]}  
    where <authentication-result> is mandatory on input messages only and  
    <authentication-result> = 8!h  
    ```  
  
-   **CHK （總和檢查碼） 結尾的所有 FIN 訊息 （必要項）**  
  
     CHK 結尾會強制所有 FIN 訊息，並計算根據收件者位址 (12 個字元的第九個字元取代*X*再加上文字區塊)。 系統中，並檢查訊息不會因系統發生問題或未偵測到的傳輸錯誤而損毀 CBT，可讓此結尾。  
  
     下列程式碼是 CHK 結尾格式的範例：  
  
    ```  
    {CHK:<checksum-result>}  
    where <checksum-result> = 12!h  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [使用結構描述](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)