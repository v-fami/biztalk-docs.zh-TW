---
title: 基底和通用結構描述 |Microsoft Docs
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
ms.openlocfilehash: 6b7f8f86e4b74b84cef556ae95bc6255d8575237
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012567"
---
# <a name="base-and-common-schemas"></a><span data-ttu-id="b8703-102">基底和通用結構描述</span><span class="sxs-lookup"><span data-stu-id="b8703-102">Base and Common Schemas</span></span>
<span data-ttu-id="b8703-103">Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]已實作的記錄和組成個別的訊息結構描述不同的結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="b8703-103">Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] has implemented the records and elements that comprise individual message schemas in separate schemas.</span></span> <span data-ttu-id="b8703-104">此方法提供單一位置來提供更新的欄位和隔絕這類變更的訊息結構描述的格式。</span><span class="sxs-lookup"><span data-stu-id="b8703-104">This approach provides a single location to provide updates for fields and formats, insulating the message schema from such changes.</span></span>  
  
 <span data-ttu-id="b8703-105">基底結構描述 (**SWIFT 基底 Types.xsd**) 包含訊息結構描述參考的通用記錄及項目定義。</span><span class="sxs-lookup"><span data-stu-id="b8703-105">The base schema (**SWIFT Base Types.xsd**) contains the common record and element definitions that the message schemas reference.</span></span> <span data-ttu-id="b8703-106">常見的記錄] 和 [項目定義對應至 SWIFT FIN 訊息欄位。</span><span class="sxs-lookup"><span data-stu-id="b8703-106">The common record and element definitions correspond to the SWIFT FIN message fields.</span></span> <span data-ttu-id="b8703-107">您要使用的訊息結構描述的任何專案中加入此結構描述。</span><span class="sxs-lookup"><span data-stu-id="b8703-107">You need to add this schema to any project that uses the message schema.</span></span> <span data-ttu-id="b8703-108">基底結構描述會涵蓋常見的函式，與規則，並定義 A4SWIFT 驗證適當的訊息執行個體所使用的格式。</span><span class="sxs-lookup"><span data-stu-id="b8703-108">The base schema covers the rules and common functions, and defines the formats that A4SWIFT uses to validate the appropriate message instances.</span></span> <span data-ttu-id="b8703-109">SWIFT 基底 Types.xsd 結構描述會定義 XSD **simpleType**和 SWIFT 欄位的複雜元素。</span><span class="sxs-lookup"><span data-stu-id="b8703-109">The SWIFT Base Types.xsd schema defines XSD **simpleType** and complex elements for SWIFT fields.</span></span> <span data-ttu-id="b8703-110">已定義 SWIFT **simpleType**所有基底欄位的詳細資訊，例如數量、 速率、 價格以及等等，SWIFT 使用中的許多欄位的項目。</span><span class="sxs-lookup"><span data-stu-id="b8703-110">SWIFT has defined **simpleType** elements for all base fields, such as the Amount, Rate, Price, and so on, which SWIFT uses in many of the fields.</span></span> <span data-ttu-id="b8703-111">SWIFT 基底 Types.xsd 結構描述也會定義 XSD 包含許多自訂欄位的複雜項目**simpleTypes**結構描述中定義。</span><span class="sxs-lookup"><span data-stu-id="b8703-111">The SWIFT Base Types.xsd schema also defines XSD complex elements for fields that include many of the custom **simpleTypes** defined in the schema.</span></span> <span data-ttu-id="b8703-112">例如， **BankIdentifierCode**銀行代碼、 國家/地區代碼、 區碼和分支程式碼，會使用複雜的項目。</span><span class="sxs-lookup"><span data-stu-id="b8703-112">For example, the **BankIdentifierCode** complex element uses Bank Code, Country Code, Area Code, and Branch Code.</span></span> <span data-ttu-id="b8703-113">使用者可以加入新**simpleTypes**和複雜的項目鏡像 SWIFT 的欄位，且可修改現有的型別。</span><span class="sxs-lookup"><span data-stu-id="b8703-113">Users can add new **simpleTypes** and complex elements that mirror SWIFT fields and can modify existing types.</span></span> <span data-ttu-id="b8703-114">您應該要特別注意，不過，當您修改現有的型別，因為 商務規則引擎 (BRE) 驗證 和 XML 驗證功能必須依賴這些定義的類型。</span><span class="sxs-lookup"><span data-stu-id="b8703-114">You should take care, however, when you modify existing types, because the Business Rule Engine (BRE) Validation and XML Validation features are dependent upon these defined types.</span></span>  
  
 <span data-ttu-id="b8703-115">常見的結構描述 (**SWIFT 常見資料 Types.xsd**) 基底結構描述中定義的適當欄位的字元集。</span><span class="sxs-lookup"><span data-stu-id="b8703-115">The common schema (**SWIFT Common Data Types.xsd**) defines the character sets appropriate to the fields in the base schema.</span></span> <span data-ttu-id="b8703-116">SWIFT 定義這些字元集中，依照*SWIFT 使用者手冊*。</span><span class="sxs-lookup"><span data-stu-id="b8703-116">SWIFT defines these character sets, as referenced in the *SWIFT User Handbook*.</span></span> <span data-ttu-id="b8703-117">您也需要將常見的結構描述新增至您的結構描述專案。</span><span class="sxs-lookup"><span data-stu-id="b8703-117">You also need to add the common schema to your schema projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8703-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8703-118">See Also</span></span>  
 [<span data-ttu-id="b8703-119">使用結構描述</span><span class="sxs-lookup"><span data-stu-id="b8703-119">Working with Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)