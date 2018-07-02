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
# <a name="failed-messages-and-errorcollection-objects"></a><span data-ttu-id="51500-102">失敗的訊息和 ErrorCollection 物件</span><span class="sxs-lookup"><span data-stu-id="51500-102">Failed Messages and ErrorCollection Objects</span></span>
<span data-ttu-id="51500-103">除了裝飾失敗的訊息，以提升的屬性，Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]將失敗的訊息發佈到 MessageBox 資料庫之附加訊息*一部分*，稱為**ErrorSegment**.</span><span class="sxs-lookup"><span data-stu-id="51500-103">In addition to decorating a failed message with promoted properties, Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] publishes the failed message to the MessageBox database with an additional message *part*, called **ErrorSegment**.</span></span> <span data-ttu-id="51500-104">此錯誤的組件包含的 XML，代表**ErrorCollection**物件。</span><span class="sxs-lookup"><span data-stu-id="51500-104">This error part contains XML representing an **ErrorCollection** object.</span></span> <span data-ttu-id="51500-105">A4SWIFT 解譯器會填入**ErrorCollection**訊息處理 （剖析，XML 驗證和商務規則引擎 (BRE) 驗證） 的每個階段的物件。</span><span class="sxs-lookup"><span data-stu-id="51500-105">The A4SWIFT disassembler populates the **ErrorCollection** object during each stage of message processing (parsing, XML validation, and Business Rule Engine (BRE) validation).</span></span>  
  
 <span data-ttu-id="51500-106">**ErrorCollection**物件是集合*錯誤物件*，每一個都代表在訊息處理期間的特定錯誤或失敗。</span><span class="sxs-lookup"><span data-stu-id="51500-106">The **ErrorCollection** object is a collection of *error objects*, each of which represents a particular error or failure during message processing.</span></span> <span data-ttu-id="51500-107">個別錯誤物件包含單一的失敗 （例如訊息和失敗的描述中的位置） 相關的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="51500-107">The individual error objects contain details about a single failure (such as the location in the message and a description of the failure).</span></span>  
  
 <span data-ttu-id="51500-108">如需詳細資訊**ErrorCollection**應用程式開發介面 (API) 和使用方式的詳細資訊，請參閱 ErrorCollection 類別。</span><span class="sxs-lookup"><span data-stu-id="51500-108">For more information about the **ErrorCollection** application programming interface (API) and usage details, see ErrorCollection Class.</span></span> <span data-ttu-id="51500-109">如需有關個別錯誤物件的詳細資訊，請參閱 ErrorBase 類別 （錯誤物件的基底類別）、 BreValidationError 類別、 ParseError 類別和 XmlValidationError 類別。</span><span class="sxs-lookup"><span data-stu-id="51500-109">For more information about individual error objects, see ErrorBase Class (the base class for error objects), BreValidationError Class, ParseError Class, and XmlValidationError Class.</span></span>  
  
 <span data-ttu-id="51500-110">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="51500-110">This section contains:</span></span>  
  
-   [<span data-ttu-id="51500-111">延伸 Capture 和 Message Repair 的解決方案</span><span class="sxs-lookup"><span data-stu-id="51500-111">Extending the Solution for Capture and Message Repair</span></span>](../../adapters-and-accelerators/accelerator-swift/extending-the-solution-for-capture-and-message-repair.md)