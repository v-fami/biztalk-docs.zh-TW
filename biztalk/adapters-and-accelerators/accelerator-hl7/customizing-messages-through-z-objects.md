---
title: 自訂訊息透過 Z 物件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, Z objects
- customizing, messages
- Z objects, customizing messages
- customizing, Z objects
- messages, customizing
ms.assetid: 5bf514f8-d270-42d9-80fa-f10a6f6a20ad
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e01e5f106c690d506364dd2040702cdad0c3adcc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204478"
---
# <a name="customizing-messages-through-z-objects"></a><span data-ttu-id="538ae-102">自訂訊息透過 Z 物件</span><span class="sxs-lookup"><span data-stu-id="538ae-102">Customizing Messages through Z Objects</span></span>
<span data-ttu-id="538ae-103">請務必識別，因為可能會 HL7 為完整，並不會處理的每一組介面夥伴的特定需求。</span><span class="sxs-lookup"><span data-stu-id="538ae-103">It is important to recognize that, as comprehensive as HL7 may be, it does not address all the particular requirements of every set of interface partners.</span></span> <span data-ttu-id="538ae-104">可能會在其中應用程式的特定資料需求超出資料 HL7 提供的定義。</span><span class="sxs-lookup"><span data-stu-id="538ae-104">There will be times in which the specific data requirements of an application go beyond the data definitions that HL7 provides.</span></span> <span data-ttu-id="538ae-105">HL7 提供介面的開發人員時，可以使用他們的資料需要超越標準的方法。</span><span class="sxs-lookup"><span data-stu-id="538ae-105">HL7 has provided methods that interface developers can use when their data needs go beyond the standard.</span></span> <span data-ttu-id="538ae-106">不幸的是，也有一些的時間，其中 HL7 介面的實作器執行未完全掌握 standard、 內容和任一誤用預先存在的內容或只要將新資料加入至現有的區段。</span><span class="sxs-lookup"><span data-stu-id="538ae-106">Unfortunately, there are also times in which the implementers of HL7 interfaces do not fully grasp the contents of the standard, and either misuse pre-existing content or simply add new material to existing segments.</span></span>  
  
 <span data-ttu-id="538ae-107">HL7 標準呼叫支援自訂 （或當地語系化） 「 Z 物件 」，因為其名稱開頭為字母"Z"。</span><span class="sxs-lookup"><span data-stu-id="538ae-107">HL7 standards call the supported customization (or localizations) "Z objects", because their names begin with the letter "Z".</span></span> <span data-ttu-id="538ae-108">您可以執行兩種類型的自訂 HL7 訊息上： 宣告和未宣告。</span><span class="sxs-lookup"><span data-stu-id="538ae-108">You can perform two types of customizations on HL7 messages: declared and undeclared.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="538ae-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="538ae-109">In This Section</span></span>  
  
-   [<span data-ttu-id="538ae-110">宣告的自訂項目</span><span class="sxs-lookup"><span data-stu-id="538ae-110">Declared Customizations</span></span>](../../adapters-and-accelerators/accelerator-hl7/declared-customizations.md)  
  
-   [<span data-ttu-id="538ae-111">未宣告的自訂項目</span><span class="sxs-lookup"><span data-stu-id="538ae-111">Undeclared Customizations</span></span>](../../adapters-and-accelerators/accelerator-hl7/undeclared-customizations.md)