---
title: 訊息驗證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- validating, messages
- messages, validating
ms.assetid: 720ab16a-7ab4-4741-9951-9ab10a2c4c24
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b4c94b7a7122572724060b2a45447699e15c1a0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970191"
---
# <a name="message-validation"></a>訊息驗證
針對傳入和傳出 HL7 訊息使用 HL7 2.X 接收和傳送管線進行的驗證訊息。 您可以設定驗證只有 MSH （標頭） 區段，或整個訊息本文。 此外，就可以針對唯一的當地語系化版本的結構描述進行驗證。 您完成定義唯一的命名空間值，並使用此 HL7 傳訊組態 （在合作對象層級） 和實際的結構描述定義訊息的目標命名空間屬性內的命名空間值。 在執行階段，Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 使用命名空間和結構描述根參考屬性的組合來選取適當的結構描述的訊息剖析和驗證。  
  
 剖析器和序列化程式來執行與訊息相關聯的合作對象的設定為基礎的驗證。 其他合作對象設定，包括批次、 通知和訊息標頭的覆寫會影響剖析或序列化程式執行驗證的方式。  
  
> [!NOTE]
>  序列化程式會執行一系列的步驟，包括 （如果適用） 標頭覆寫從 MSH 對應，以及執行 XML 驗證。 如果標頭覆寫和驗證處理程序同時啟用，且標頭覆寫程序的標頭欄位中輸入值不正確，訊息將無法通過驗證，即使訊息傳遞內文驗證。  
  
## <a name="see-also"></a>另請參閱  
 [MSH 覆寫](../../adapters-and-accelerators/accelerator-hl7/msh-override.md)