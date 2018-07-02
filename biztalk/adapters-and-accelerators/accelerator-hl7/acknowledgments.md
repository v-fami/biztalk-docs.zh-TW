---
title: 通知 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, acknowledgements
- parties, acknowledgements
- acknowledgements, about acknowledgements
- acknowledgements, messages
- acknowledgements, parties
ms.assetid: d25352a4-bae9-4de9-a504-2339bea25c4a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46dedd4f2173fd4a3ad36c272963334b4ce66a20
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969783"
---
# <a name="acknowledgments"></a>致謝
您在使用 Microsoft BizTalk Accelerator for HL7 的合作對象層級設定 HL7 通知 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 組態總管。 通知會套用到合作對象的傳送 HL7 訊息透過接收位置 （可能是 MLLP 配接器） 和 HL7 2.X 接收管線。 當訊息完成剖析和驗證，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可以建立包含驗證程序的結果 （成功或錯誤） 的通知訊息。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 可以在下列其中一種傳回通知訊息。 如果原始的傳送合作對象送出原始訊息透過雙向接收埠組態[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳回通知訊息，透過該原始的連接埠位置。 如果原始的傳送埠送出原始訊息透過單向接收埠，則[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將通知訊息提交至 MessageBox 資料庫，並將它使用的訂用帳戶模型傳遞。[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 執行合作對象關聯的接收訊息處理會自動根據 HL7 訊息 (MSH 3.1) 的傳送端的 [應用程式] 欄位內的值。  
  
## <a name="see-also"></a>另請參閱  
 [訊息流程](../../adapters-and-accelerators/accelerator-hl7/message-flow.md)