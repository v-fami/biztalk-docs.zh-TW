---
title: "SWIFT 結尾 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SWIFT Trailer schema
- schemas, SWIFT
- trailers [SWIFT]
- SWIFT, trailers
ms.assetid: b6d64584-0514-4c87-98c0-33755efc4695
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc3155ac21f55e7c61483b9287429f9b722f6a84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="swift-trailers"></a>SWIFT 結尾
每個 SWIFT 的訊息都有一或多個結尾所需的訊息交換和安全性需求。 系統結尾，如果適用的話，請遵循使用者結尾。 結尾區塊內的每一個結尾會顯示進一步的成對的大括號以分隔的子區塊內。 每一個子區塊的結尾類型，後面接著冒號的三個字母開頭。  
  
 SWIFT 結尾結構描述 (SWIFT Trailer.xsd) 包含下列格式：  
  
-   文字區塊結束分隔符號  
  
-   使用者結尾 （使用者和系統資訊）  
  
-   系統結尾  
  
 文字區塊的結束分隔符號是"-"}。 結尾區塊的開頭"{5:"。 結尾區塊的內容會包含使用者資訊 （總和檢查碼、 訊息驗證，專屬的驗證，等等） 和系統資訊 （延遲的訊息，訊息參考，可能重複的訊息，以及等等）。 SWIFT 所加入的結尾也提供第三個區塊，以分隔"{S"。 *SWIFT 使用者手冊*，「 尋找服務描述 」 主題，詳細說明區塊 5 的內容。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]不會驗證 s 區塊的內容  
  
 實際的 FIN 介面或 SWIFT 網路將附加至結尾。 如果訊息包含結尾時[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收訊息，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]帶有訊息結尾。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]不會引發錯誤，如果訊息不包含結尾時[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收訊息。 做為具標頭，所有的結尾項目，包括區塊本身，都是選擇性中[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。  
  
 此部分包含：  
  
-   [使用者結尾](../../adapters-and-accelerators/accelerator-swift/user-trailers.md)  
  
-   [系統結尾](../../adapters-and-accelerators/accelerator-swift/system-trailers.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用結構描述](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)