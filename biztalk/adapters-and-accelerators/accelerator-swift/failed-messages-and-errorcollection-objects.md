---
title: 失敗訊息和 ErrorCollection 物件 |Microsoft 文件
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
ms.openlocfilehash: 65598ef44bfe3e34bd1695aa81bee368c5175793
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209230"
---
# <a name="failed-messages-and-errorcollection-objects"></a>失敗的訊息和 ErrorCollection 物件
除了失敗的訊息，以提升的屬性，而將[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]將失敗的訊息發佈到 MessageBox 資料庫與其他訊息*一部分*，稱為**ErrorSegment**. 此錯誤的組件包含的 XML 表示**ErrorCollection**物件。 A4SWIFT 解譯器會填入**ErrorCollection**在每個階段中訊息處理 （剖析，XML 驗證和商務規則引擎 (BRE) 驗證） 的物件。  
  
 **ErrorCollection**物件是集合*錯誤物件*，其中每個訊息處理期間代表特定的錯誤或失敗。 個別錯誤物件包含的詳細資訊 （例如訊息和失敗的描述中的位置） 的單一失敗。  
  
 如需有關**ErrorCollection**應用程式開發介面 (API) 和使用方式詳細資料，請參閱 ErrorCollection 類別。 如需有關個別錯誤物件的詳細資訊，請參閱 ErrorBase 類別 （錯誤物件的基底類別）、 BreValidationError 類別、 ParseError 類別和 XmlValidationError 類別。  
  
 此部分包含：  
  
-   [擷取和訊息修復擴充解決方案](../../adapters-and-accelerators/accelerator-swift/extending-the-solution-for-capture-and-message-repair.md)