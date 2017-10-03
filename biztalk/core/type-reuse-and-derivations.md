---
title: "重複使用和衍生類型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 240145ea-be41-40ce-8edd-3d4d00e2baec
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2982fdf5e46f813669ff74b513615637aa699bd4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="type-reuse-and-derivations"></a><span data-ttu-id="fa450-102">類型重複使用和衍生</span><span class="sxs-lookup"><span data-stu-id="fa450-102">Type Reuse and Derivations</span></span>
<span data-ttu-id="fa450-103">在 XML 結構描述定義 (XSD) 語言中，複雜的全域類型所提供的機制，可用於定義能在您結構描述中不同位置重複使用、甚至重新定義的結構化資料類型。</span><span class="sxs-lookup"><span data-stu-id="fa450-103">Within XML Schema definition (XSD) language, complex global types provide a mechanism for defining a structured data type that can be reused, and potentially redefined, at various locations within your schema.</span></span> <span data-ttu-id="fa450-104">最典型的範例或許是包括名稱、街道、城市、州等等的地址結構。</span><span class="sxs-lookup"><span data-stu-id="fa450-104">Perhaps the most classic example is an address structure that includes a name, street, city, state, and so on.</span></span> <span data-ttu-id="fa450-105">更進一步而言，名稱本身可能是包括姓氏、中間名和名字字串的結構。</span><span class="sxs-lookup"><span data-stu-id="fa450-105">Further, the name itself might be a structure that includes first, middle, and last name strings.</span></span> <span data-ttu-id="fa450-106">若這個複雜結構是全域定義，則您可以在結構描述的多個位置中使用它，如送貨地址和帳單地址。</span><span class="sxs-lookup"><span data-stu-id="fa450-106">If this complex structure is defined globally, you can use it in multiple locations within your schema, such as for both a shipping address and a billing address.</span></span>  
  
 <span data-ttu-id="fa450-107">XSD 也提供從某個類型衍生另一個類型的機制。</span><span class="sxs-lookup"><span data-stu-id="fa450-107">XSD also provides mechanisms for deriving one type from another.</span></span> <span data-ttu-id="fa450-108">這包括簡單內容類型和複雜內容類型。</span><span class="sxs-lookup"><span data-stu-id="fa450-108">This includes both simple content types and complex content types.</span></span> <span data-ttu-id="fa450-109">例如，可以從簡單字串類型 (如 xs:string) 衍生出新的類型，如此新類型僅會允許少數特定字串做為合法值。</span><span class="sxs-lookup"><span data-stu-id="fa450-109">For example, a new type can be derived from a simple string type (such as, xs:string) such that the new type allows only a few particular strings as legal values.</span></span> <span data-ttu-id="fa450-110">此類型的衍生在 XSD 中被視為由限制衍生，因為衍生類型所允許之值的限制會比基礎類型所允許的值還多。</span><span class="sxs-lookup"><span data-stu-id="fa450-110">This type of derivation is known within XSD as derivation by restriction because the values allowed by the derived type are more restrictive than the values allowed by the base type.</span></span>  
  
 <span data-ttu-id="fa450-111">涉及複雜類型的衍生範例可以在先前建議的地址型別中看到。</span><span class="sxs-lookup"><span data-stu-id="fa450-111">An example of a derivation involving a complex type can be seen in the address type previously suggested.</span></span> <span data-ttu-id="fa450-112">假設地址型別是指定為搭配特定國家/地區的地址，其中國家/地區本身已假設是在地址中。</span><span class="sxs-lookup"><span data-stu-id="fa450-112">Suppose that the address type is designed to accommodate the addresses within a particular country/region, where the country/region itself is assumed in the address.</span></span> <span data-ttu-id="fa450-113">若要延伸此種地址型別以處理國際地址，您可以從原始地址型別衍生出新的型別，然後將額外的資訊 (如國家/地區) 包括在衍生型別中。</span><span class="sxs-lookup"><span data-stu-id="fa450-113">To extend such an address type to handle international addresses, you can derive a new type from the original address type and then include additional information in the derived type, such as the country/region.</span></span> <span data-ttu-id="fa450-114">此型別的衍生在 XSD 中被視為由擴充衍生，因為衍生型別擴充了基礎型別。</span><span class="sxs-lookup"><span data-stu-id="fa450-114">This type of derivation is known within XSD as derivation by extension because the derived type has extended the base type.</span></span>  
  
 <span data-ttu-id="fa450-115">本節將描述型別重複使用，以及使用衍生重新定義重複使用型別的方式。</span><span class="sxs-lookup"><span data-stu-id="fa450-115">This section describes type reuse and the ways in which you can use derivation to redefine types as they are reused.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa450-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="fa450-116">In This Section</span></span>  
  
-   [<span data-ttu-id="fa450-117">複雜全域型別定義和命名</span><span class="sxs-lookup"><span data-stu-id="fa450-117">Complex Global Type Definition and Naming</span></span>](../core/complex-global-type-definition-and-naming.md)  
  
-   [<span data-ttu-id="fa450-118">使用複雜全域型別的方式</span><span class="sxs-lookup"><span data-stu-id="fa450-118">Ways to Use Complex Global Types</span></span>](../core/ways-to-use-complex-global-types.md)  
  
-   [<span data-ttu-id="fa450-119">簡單型別衍生</span><span class="sxs-lookup"><span data-stu-id="fa450-119">Simple Type Derivation</span></span>](../core/simple-type-derivation.md)