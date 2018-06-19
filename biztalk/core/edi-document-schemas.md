---
title: EDI 文件結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc3a30b8-0686-4c06-985b-13f2c95f8e99
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b96089f7f76af1183f457202bb2e22b5be7f146
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968300"
---
# <a name="edi-document-schemas"></a><span data-ttu-id="7aac7-102">EDI 文件結構描述</span><span class="sxs-lookup"><span data-stu-id="7aac7-102">EDI Document Schemas</span></span>
<span data-ttu-id="7aac7-103">文件結構描述定義了 EDI 交易文件類型的內文。</span><span class="sxs-lookup"><span data-stu-id="7aac7-103">Document schemas define the body of an EDI transaction document type.</span></span>  
  
## <a name="schema-delivery-and-setup"></a><span data-ttu-id="7aac7-104">結構描述傳遞和設定</span><span class="sxs-lookup"><span data-stu-id="7aac7-104">Schema Delivery and Setup</span></span>  
 <span data-ttu-id="7aac7-105">傳送 EDI 文件結構描述中的自動解壓縮可執行檔的壓縮狀態[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\MicrosoftEdiXSDTemplates.exe。</span><span class="sxs-lookup"><span data-stu-id="7aac7-105">EDI document schemas are delivered in a compressed state in a self-extracting executable, [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\MicrosoftEdiXSDTemplates.exe.</span></span> <span data-ttu-id="7aac7-106">自動解壓縮可執行檔可確保建立適當的資料夾結構 (根據各種編碼類型與版本/版次的子類型)。</span><span class="sxs-lookup"><span data-stu-id="7aac7-106">The self-extracting executable ensures that an appropriate folder structure is created (per the encoding type and version/release sub types).</span></span> <span data-ttu-id="7aac7-107">可執行檔執行時，會將 EANCOM、 EDIFACT、 HIPAA 和 X12 結構描述可執行檔相同的目錄中的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="7aac7-107">When executed, the executable deposits EANCOM, EDIFACT, HIPAA, and X12 schemas into subfolders in the same directory as the executable.</span></span>  
  
 <span data-ttu-id="7aac7-108">預設結構描述命名空間為：</span><span class="sxs-lookup"><span data-stu-id="7aac7-108">The default schema namespaces are:</span></span>  
  
-   <span data-ttu-id="7aac7-109">對於 X12-`http://schemas.microsoft.com/BizTalk/EDI/X12/2006`</span><span class="sxs-lookup"><span data-stu-id="7aac7-109">For X12 – `http://schemas.microsoft.com/BizTalk/EDI/X12/2006`</span></span>  
  
-   <span data-ttu-id="7aac7-110">對於 EDIFACT –`http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006`</span><span class="sxs-lookup"><span data-stu-id="7aac7-110">For EDIFACT – `http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006`</span></span>  
  
## <a name="schema-naming-convention"></a><span data-ttu-id="7aac7-111">結構描述命名慣例</span><span class="sxs-lookup"><span data-stu-id="7aac7-111">Schema Naming Convention</span></span>  
 <span data-ttu-id="7aac7-112">X12 和 EDIFACT 編碼類型的命名慣例是\<編碼\>_\<版本\>\<發行\>\_\<Doctype\>。</span><span class="sxs-lookup"><span data-stu-id="7aac7-112">The naming convention for the X12 and EDIFACT encoding type is \<Encoding\>_\<Version\>\<Release\>\_\<Doctype\>.</span></span> <span data-ttu-id="7aac7-113">例如，用於 X12 864 文件類型 (版本 004、版次 01) 的 X12_00401_864.xsd 結構描述，以及用於 EDIFACT AUTHOR 文件類型 (版本 D01、版次 C) 的 EDIFACT_D01C_AUTHOR.xsd 結構描述。</span><span class="sxs-lookup"><span data-stu-id="7aac7-113">Examples are the X12_00401_864.xsd schema for the X12 864 document type (version 004, release 01) and the EDIFACT_D01C_AUTHOR.xsd schema for the EDIFACT AUTHOR document type (version D01, release C).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7aac7-114">EDIFACT 結構描述的結構描述名稱是區分大小寫的。</span><span class="sxs-lookup"><span data-stu-id="7aac7-114">The schema name of an EDIFACT schema is case-sensitive.</span></span> <span data-ttu-id="7aac7-115">例如，EFACT_D98B_ORDERS 和 EFACT_d98B_Orders 是兩個不同的結構描述。</span><span class="sxs-lookup"><span data-stu-id="7aac7-115">For example, EFACT_D98B_ORDERS and EFACT_d98B_Orders would be two different schemas.</span></span>  
  
## <a name="schema-contents"></a><span data-ttu-id="7aac7-116">結構描述內容</span><span class="sxs-lookup"><span data-stu-id="7aac7-116">Schema Contents</span></span>  
 <span data-ttu-id="7aac7-117">對於 X12 編碼文件，文件結構描述是以 ST 交易集標頭開始，並以 SE 交易集結尾結束。</span><span class="sxs-lookup"><span data-stu-id="7aac7-117">A document schema starts with the ST transaction set header and ends with the SE transaction set trailer for an X12-encoded document.</span></span> <span data-ttu-id="7aac7-118">對於 EDIFACT 編碼文件，則是以 UNH 訊息標頭開始，並以 UNT 訊息結尾結束。</span><span class="sxs-lookup"><span data-stu-id="7aac7-118">It starts with the UNH message header and ends with the UNT message trailer for an EDIFACT-encoded document.</span></span> <span data-ttu-id="7aac7-119">結構描述會定義這些標頭和結尾的每個資料元素。</span><span class="sxs-lookup"><span data-stu-id="7aac7-119">The schema defines each data element of these headers and trailers.</span></span>  
  
 <span data-ttu-id="7aac7-120">文件結構描述會接著定義交易集/訊息內的每個區段，以及這些區段內的資料元素。</span><span class="sxs-lookup"><span data-stu-id="7aac7-120">A document schema then defines each segment within the transaction set/message and the data elements within those segments.</span></span> <span data-ttu-id="7aac7-121">例如，X12_00401_864.xsd 結構描述會定義 BMG 區段的 BMG01、BMG02 及 BMG03 元素。</span><span class="sxs-lookup"><span data-stu-id="7aac7-121">For example, the X12_00401_864.xsd schema defines the BMG01, BMG02, and BMG03 elements of the BMG segments.</span></span> <span data-ttu-id="7aac7-122">結構描述會指定區段中複雜資料類型 (例如欄位順序、分隔符號類型，以及命名空間) 的特性。</span><span class="sxs-lookup"><span data-stu-id="7aac7-122">The schema specifies the characteristics of the segment's complex data type, such as the field order, delimiter type, and namespace.</span></span> <span data-ttu-id="7aac7-123">如果有區段適用的欄位交互驗證規則，結構描述便會定義這些規則。</span><span class="sxs-lookup"><span data-stu-id="7aac7-123">If there are cross-field validation rules for the segment, the schema defines the rules.</span></span> <span data-ttu-id="7aac7-124">如需詳細資訊，請參閱[跨欄位區段驗證](../core/cross-field-segment-validation.md)。</span><span class="sxs-lookup"><span data-stu-id="7aac7-124">For more information, see [Cross Field-Segment Validation](../core/cross-field-segment-validation.md).</span></span>  
  
 <span data-ttu-id="7aac7-125">結構描述會指定區段內各個資料元素的特性，例如簡單資料類型、最少發生次數、最小長度，以及最大長度。</span><span class="sxs-lookup"><span data-stu-id="7aac7-125">The schema specifies the characteristics of each data element within the segment, such as the simple data type, minimum occurrences, minimum length, and maximum length.</span></span>  
  
 <span data-ttu-id="7aac7-126">如果在訊息類型中有迴圈，結構描述便會定義各個迴圈內的資料元素、迴圈的最少與最多發生次數，以及迴圈屬於已繫結或未繫結狀態。</span><span class="sxs-lookup"><span data-stu-id="7aac7-126">If there is a loop in the message type, the schema defines the data elements within each loop, the minimum and maximum occurrences of the loop, and whether the loop is bounded or unbounded.</span></span> <span data-ttu-id="7aac7-127">結構描述也會定義區段的巢狀方式，以及迴圈屬於明確或是隱含狀態。</span><span class="sxs-lookup"><span data-stu-id="7aac7-127">The schema also defines nesting of a segment, and whether the loop is explicit or implicit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aac7-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="7aac7-128">See Also</span></span>  
 <span data-ttu-id="7aac7-129">[EDI 訊息結構](../core/edi-message-structure.md) </span><span class="sxs-lookup"><span data-stu-id="7aac7-129">[EDI Message Structure](../core/edi-message-structure.md) </span></span>  
 [<span data-ttu-id="7aac7-130">EDI 訊息驗證</span><span class="sxs-lookup"><span data-stu-id="7aac7-130">EDI Message Validation</span></span>](../core/edi-message-validation.md)