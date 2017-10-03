---
title: "訊息驗證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, messages
- messages, validating
ms.assetid: 720ab16a-7ab4-4741-9951-9ab10a2c4c24
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 940b6aa811cbee845b287c09a66c4b9753313ee0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-validation"></a>訊息驗證
針對傳入和傳出 HL7 訊息與 HL7 2.X 接收和傳送管線進行的驗證訊息。 您可以設定驗證只有 MSH （標頭） 區段，或整個訊息本文。 此外，便可驗證的結構描述的唯一當地語系化版本。 透過定義唯一的命名空間值，和使用此命名空間值 （在合作對象層級） 的 HL7 訊息組態和目標命名空間屬性，定義訊息的實際結構描述內完成此作業。 在執行階段， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會使用命名空間和結構描述的根參考 屬性的組合，來選取適當的結構描述的訊息剖析和驗證。  
  
 剖析器和序列化程式來執行驗證的設定與訊息相關聯的合作對象為基礎。 其他合作對象設定，包括批次、 通知和訊息標頭的覆寫會影響剖析或序列化程式執行驗證的方式。  
  
> [!NOTE]
>  序列化程式會執行一系列的步驟，包括 （如果適用） 標頭覆寫從 MSH 對應，以及執行 XML 驗證。 如果標頭覆寫和驗證處理程序同時啟用，且標頭覆寫程序的標頭欄位中輸入值不正確，訊息將無法通過驗證，即使訊息通過主體驗證。  
  
## <a name="see-also"></a>另請參閱  
 [MSH 覆寫](../../adapters-and-accelerators/accelerator-hl7/msh-override.md)