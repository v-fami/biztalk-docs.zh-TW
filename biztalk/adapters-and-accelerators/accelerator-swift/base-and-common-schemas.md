---
title: 基底和常見的結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- base schemas
- schemas, common schemas
- schemas, base schemas
- common schemas
ms.assetid: 60eb24f6-cc4f-4c6d-ab15-9e3a6b4ed376
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88ca51abfcdbfe965bc3da8deeb97f72df736903
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209174"
---
# <a name="base-and-common-schemas"></a><span data-ttu-id="383c6-102">基底和常見的結構描述</span><span class="sxs-lookup"><span data-stu-id="383c6-102">Base and Common Schemas</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="383c6-103">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]已實作的記錄和組成個別的訊息結構描述不同的結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="383c6-103"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] has implemented the records and elements that comprise individual message schemas in separate schemas.</span></span> <span data-ttu-id="383c6-104">這個方法會提供單一位置，以提供更新的欄位和隔離這類變更的訊息結構描述的格式。</span><span class="sxs-lookup"><span data-stu-id="383c6-104">This approach provides a single location to provide updates for fields and formats, insulating the message schema from such changes.</span></span>  
  
 <span data-ttu-id="383c6-105">基底結構描述 (**SWIFT 基底 Types.xsd**) 包含的訊息結構描述參考一般記錄和項目定義。</span><span class="sxs-lookup"><span data-stu-id="383c6-105">The base schema (**SWIFT Base Types.xsd**) contains the common record and element definitions that the message schemas reference.</span></span> <span data-ttu-id="383c6-106">一般記錄和項目定義對應至 SWIFT FIN 訊息欄位。</span><span class="sxs-lookup"><span data-stu-id="383c6-106">The common record and element definitions correspond to the SWIFT FIN message fields.</span></span> <span data-ttu-id="383c6-107">您需要將這個結構描述加入至任何使用訊息結構描述的專案。</span><span class="sxs-lookup"><span data-stu-id="383c6-107">You need to add this schema to any project that uses the message schema.</span></span> <span data-ttu-id="383c6-108">基底結構描述的規則和一般函數，涵蓋了，並定義 A4SWIFT 用來驗證適當的訊息執行個體的格式。</span><span class="sxs-lookup"><span data-stu-id="383c6-108">The base schema covers the rules and common functions, and defines the formats that A4SWIFT uses to validate the appropriate message instances.</span></span> <span data-ttu-id="383c6-109">SWIFT 基底 Types.xsd 結構描述會定義 XSD **simpleType**和 SWIFT 欄位的複雜項目。</span><span class="sxs-lookup"><span data-stu-id="383c6-109">The SWIFT Base Types.xsd schema defines XSD **simpleType** and complex elements for SWIFT fields.</span></span> <span data-ttu-id="383c6-110">已定義 SWIFT **simpleType**元素的所有基底欄位的詳細資訊，例如金額、 速率、 價格以及等等，SWIFT 使用中的許多欄位。</span><span class="sxs-lookup"><span data-stu-id="383c6-110">SWIFT has defined **simpleType** elements for all base fields, such as the Amount, Rate, Price, and so on, which SWIFT uses in many of the fields.</span></span> <span data-ttu-id="383c6-111">SWIFT 基底 Types.xsd 結構描述也會定義可包含許多自訂的欄位，XSD 複雜的項目**simpleTypes**結構描述中定義。</span><span class="sxs-lookup"><span data-stu-id="383c6-111">The SWIFT Base Types.xsd schema also defines XSD complex elements for fields that include many of the custom **simpleTypes** defined in the schema.</span></span> <span data-ttu-id="383c6-112">例如， **BankIdentifierCode**銀行代碼、 國家/地區代碼、 區碼和分支程式碼，會使用複雜的項目。</span><span class="sxs-lookup"><span data-stu-id="383c6-112">For example, the **BankIdentifierCode** complex element uses Bank Code, Country Code, Area Code, and Branch Code.</span></span> <span data-ttu-id="383c6-113">使用者可以加入新**simpleTypes**和複雜的項目鏡像 SWIFT 的欄位，且可修改現有的類型。</span><span class="sxs-lookup"><span data-stu-id="383c6-113">Users can add new **simpleTypes** and complex elements that mirror SWIFT fields and can modify existing types.</span></span> <span data-ttu-id="383c6-114">您應該格外謹慎，不過，當您修改現有的型別，因為商務規則引擎 (BRE) 驗證 」 和 「 XML 驗證功能相依於這些定義的型別。</span><span class="sxs-lookup"><span data-stu-id="383c6-114">You should take care, however, when you modify existing types, because the Business Rule Engine (BRE) Validation and XML Validation features are dependent upon these defined types.</span></span>  
  
 <span data-ttu-id="383c6-115">常見的結構描述 (**SWIFT 常見資料 Types.xsd**) 基底結構描述中定義適當的欄位的字元集。</span><span class="sxs-lookup"><span data-stu-id="383c6-115">The common schema (**SWIFT Common Data Types.xsd**) defines the character sets appropriate to the fields in the base schema.</span></span> <span data-ttu-id="383c6-116">SWIFT 定義中參考這些字元集， *SWIFT 使用者手冊*。</span><span class="sxs-lookup"><span data-stu-id="383c6-116">SWIFT defines these character sets, as referenced in the *SWIFT User Handbook*.</span></span> <span data-ttu-id="383c6-117">您也需要將通用的結構描述新增至您的結構描述專案。</span><span class="sxs-lookup"><span data-stu-id="383c6-117">You also need to add the common schema to your schema projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="383c6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="383c6-118">See Also</span></span>  
 [<span data-ttu-id="383c6-119">使用結構描述</span><span class="sxs-lookup"><span data-stu-id="383c6-119">Working with Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)