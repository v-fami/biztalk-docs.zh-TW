---
title: SWIFT 結尾 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SWIFT Trailer schema
- schemas, SWIFT
- trailers [SWIFT]
- SWIFT, trailers
ms.assetid: b6d64584-0514-4c87-98c0-33755efc4695
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1457c05b37c3f5b1dfcc5887c1a3f6ce27fcb0d4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004839"
---
# <a name="swift-trailers"></a>SWIFT 結尾
每個 SWIFT 的訊息有一或多個結尾所需的訊息交換和安全性需求。 系統結尾，如果適用的話，請遵循使用者結尾。 每個後端的結尾區塊內的項目會出現在 subblock，以進一步的成對的大括號分隔。 每個 subblock 的後端項目類型，後面接著冒號的三個字母開頭。  
  
 SWIFT 結尾結構描述 (SWIFT Trailer.xsd) 包含下列格式：  
  
- 文字區塊的結束分隔符號  
  
- 使用者結尾 （使用者和系統資訊）  
  
- 系統結尾  
  
  文字區塊的結束分隔符號是"-"}。 結尾區塊的開頭 「 {5:"。 結尾區塊的內容會包含使用者資訊 （總和檢查碼、 訊息驗證、 專屬的驗證，等等） 和系統資訊 （延遲的訊息、 參考訊息、 可能的重複訊息，等等）。 新增 SWIFT 的結尾也提供第三個區塊，以分隔的"{s:"。 *SWIFT 使用者手冊*，「 FIN 服務說明 」 主題，詳細說明區塊 5 的內容。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] 不會驗證 s 區塊的內容  
  
  實際的 FIN 介面或 SWIFT 網路附加的結尾。 如果訊息包含結尾時[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收訊息，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]帶有訊息結尾。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] 不會引發錯誤，如果訊息不包含結尾時[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收訊息。 做為標頭與結尾的項目，包括區塊本身，都選擇性在[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。  
  
  此部分包含：  
  
- [使用者結尾](../../adapters-and-accelerators/accelerator-swift/user-trailers.md)  
  
- [系統結尾](../../adapters-and-accelerators/accelerator-swift/system-trailers.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用結構描述](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)