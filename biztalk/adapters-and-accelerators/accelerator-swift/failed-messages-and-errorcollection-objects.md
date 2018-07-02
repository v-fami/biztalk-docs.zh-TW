---
title: 失敗訊息和 ErrorCollection 物件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- failed messages, ErrorCollection objects
- ErrorCollection objects
ms.assetid: 8a2ff3b5-d7a0-4595-8b74-3133e9e3a821
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4f9fd17807d9bc1b92b1eae1ac75662843c8e17
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993159"
---
# <a name="failed-messages-and-errorcollection-objects"></a>失敗的訊息和 ErrorCollection 物件
除了裝飾失敗的訊息，以提升的屬性，Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]將失敗的訊息發佈到 MessageBox 資料庫之附加訊息*一部分*，稱為**ErrorSegment**. 此錯誤的組件包含的 XML，代表**ErrorCollection**物件。 A4SWIFT 解譯器會填入**ErrorCollection**訊息處理 （剖析，XML 驗證和商務規則引擎 (BRE) 驗證） 的每個階段的物件。  
  
 **ErrorCollection**物件是集合*錯誤物件*，每一個都代表在訊息處理期間的特定錯誤或失敗。 個別錯誤物件包含單一的失敗 （例如訊息和失敗的描述中的位置） 相關的詳細資料。  
  
 如需詳細資訊**ErrorCollection**應用程式開發介面 (API) 和使用方式的詳細資訊，請參閱 ErrorCollection 類別。 如需有關個別錯誤物件的詳細資訊，請參閱 ErrorBase 類別 （錯誤物件的基底類別）、 BreValidationError 類別、 ParseError 類別和 XmlValidationError 類別。  
  
 此部分包含：  
  
-   [延伸 Capture 和 Message Repair 的解決方案](../../adapters-and-accelerators/accelerator-swift/extending-the-solution-for-capture-and-message-repair.md)