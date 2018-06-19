---
title: 相互關聯類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- correlation sets, correlation types
- correlation types, correlation sets
- correlation types
- validating, correlation types
- correlation types, about correlation types
- correlation types, validating
ms.assetid: 1aa5ca5c-c37d-4091-9f5d-331a6b202d4e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3da5fad8cb4edc1d6a528f481616b4f10efb71d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22237774"
---
# <a name="correlation-types"></a><span data-ttu-id="323c1-102">相互關聯類型</span><span class="sxs-lookup"><span data-stu-id="323c1-102">Correlation Types</span></span>
<span data-ttu-id="323c1-103">每個相互關聯集根據**相互關聯類型**，這是直接的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="323c1-103">Each correlation set is based on a **correlation type**, which is simply a list of properties.</span></span> <span data-ttu-id="323c1-104">這些屬性可以是資料屬性 (存在於訊息本身中)，也可以是內容屬性 (描述與訊息中傳遞之資料無關的系統或訊息詳細資料)。</span><span class="sxs-lookup"><span data-stu-id="323c1-104">These properties might be data properties, which are found in the message itself, or context properties, which describe details of the system or messages that are unrelated to the data being conveyed in the message.</span></span>  
  
 <span data-ttu-id="323c1-105">您可以在一個以上的相互關聯集中使用相互關聯類型。</span><span class="sxs-lookup"><span data-stu-id="323c1-105">You can use a correlation type in more than one correlation set.</span></span> <span data-ttu-id="323c1-106">如果您必須在相互關聯類型中的不同屬性值上相互關聯，則必須建立新的相互關聯集 (每個相互關聯集只能初始化一次)。</span><span class="sxs-lookup"><span data-stu-id="323c1-106">If you need to correlate on different values for the properties in a correlation type, you must create a new correlation set—each correlation set can be initialized only once.</span></span>  
  
 <span data-ttu-id="323c1-107">您可以升級屬性結構描述中的屬性，宣告訊息中的某個屬性可由您的協調流程存取。</span><span class="sxs-lookup"><span data-stu-id="323c1-107">You can promote properties in a property schema to declare that certain properties in a message are accessible to your orchestration.</span></span> <span data-ttu-id="323c1-108">如需詳細資訊，請參閱[升級屬性](../core/promoting-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="323c1-108">For more information, see [Promoting Properties](../core/promoting-properties.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="323c1-109">未設定的系統定義屬性**BTS。CorrelationToken**與每個訊息相關聯。</span><span class="sxs-lookup"><span data-stu-id="323c1-109">Do not set the system-defined property **BTS.CorrelationToken** that is associated with each message.</span></span> <span data-ttu-id="323c1-110">引擎會在相互關聯訊息中使用這個屬性，加以設定可能導致協調流程遺失訊息。</span><span class="sxs-lookup"><span data-stu-id="323c1-110">This is used by the engine in correlating messages, and setting it could result in your orchestration losing messages.</span></span>  
  
## <a name="validating-message-correlation-on-send-actions"></a><span data-ttu-id="323c1-111">驗證傳送動作上的訊息相互關聯</span><span class="sxs-lookup"><span data-stu-id="323c1-111">Validating Message Correlation on Send Actions</span></span>  
 <span data-ttu-id="323c1-112">您可以驗證您從協調流程所傳送之訊息的屬性，確保該訊息能反映其相互關聯集中的屬性。</span><span class="sxs-lookup"><span data-stu-id="323c1-112">You can validate the properties of a message that you send from your orchestration to ensure that it reflects the properties in its correlation set.</span></span> <span data-ttu-id="323c1-113">根據預設，會停用此項驗證。</span><span class="sxs-lookup"><span data-stu-id="323c1-113">By default, this validation is disabled.</span></span> <span data-ttu-id="323c1-114">如需如何啟用此功能的資訊，請參閱[協調流程引擎的執行階段驗證](../core/runtime-validation-for-the-orchestration-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="323c1-114">For information on how to enable it, see [Runtime Validation for the Orchestration Engine](../core/runtime-validation-for-the-orchestration-engine.md).</span></span>