---
title: 使用者結尾 |Microsoft Docs
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
ms.assetid: 340d9fc8-467b-4cba-b69f-eb761767deaa
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10bc0d4d0fcdb36311e0590d9ae04239db168ed7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010215"
---
# <a name="user-trailers"></a>使用者結尾
使用者結尾，除了 CHK 結尾是選擇性的存在時，會發生順序如下：  
  
|結尾程式碼|[屬性]|  
|------------------|----------|  
|MAC|訊息驗證碼|  
|PAC|專屬的驗證碼|  
|CHK|總和檢查碼|  
|TNG|訓練|  
|PDE|可能的重複發出|  
  
- **訊息驗證碼 (MAC) 結尾。** 允許接收使用者的驗證。 MAC 結尾後面的驗證結果。 此結尾是 FIN 應用程式中的大多數使用者的使用者訊息分類的必要步驟。  
  
   使用 「 FIN 複製 」 服務時，PAC 結尾 （如果有的話） 會遵循 MAC 結尾。 下列程式碼是 MAC 結尾的範例：  
  
  ```  
  {MAC:<authentication-result>}  
  where <authentication-result> = 8!h  
  ```  
  
- **專屬的驗證程式碼 (PAC) 結尾。** 使用雙重驗證選項時，才 FIN 複製服務使用 PAC 結尾。 如果有的話，區塊 5 FIN 使用者對使用者訊息會包含 PAC 結尾後面 MAC 結尾。 此結果計算的訊息，也就是 115，欄位的值的區塊 4 擷取的欄位，如果有的話，而\<驗證結果\>的雙重驗證 MAC 結尾複製服務。  
  
   如此一來，PAC 計算中包含結尾區塊的指標 （CrLf-） 和欄位的定義，如下所示：  
  
  - 前四個字元是 CrLf:  
  
  - 欄位和分隔符號都存在，也就是 32A: 20，:，依此類推。  
  
  - 所有的子欄位和分隔符號會出現。  
  
    下列程式碼是 PAC 結尾格式範例：  
  
  ```  
  {PAC:[<authentication-result>]}  
  where <authentication-result> is mandatory on input messages only and  
  <authentication-result> = 8!h  
  ```  
  
- **CHK （總和檢查碼） 結尾 （針對所有 FIN 訊息的必要項）**  
  
   CHK 結尾是所有 FIN 訊息的必要步驟，並計算根據收件者位址 (12 個字元，第九個字元取代*X*再加上文字區塊)。 這個後端項目可讓系統，並檢查訊息不會因為系統故障或未偵測到的傳輸錯誤而損毀 CBT。  
  
   下列程式碼是 CHK 結尾格式範例：  
  
  ```  
  {CHK:<checksum-result>}  
  where <checksum-result> = 12!h  
  ```  
  
## <a name="see-also"></a>另請參閱  
 [使用結構描述](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)