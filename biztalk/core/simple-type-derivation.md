---
title: 簡單型別衍生 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43932a0-039c-4211-82c0-087bae186145
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1b1904c96c2786abad283db7133a9755c8743d6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998495"
---
# <a name="simple-type-derivation"></a><span data-ttu-id="7e0af-102">簡單型別衍生</span><span class="sxs-lookup"><span data-stu-id="7e0af-102">Simple Type Derivation</span></span>
<span data-ttu-id="7e0af-103">XML 結構描述定義 (XSD) 語言提供數種機制，來定義，如下所示為基礎的現有的簡單型別衍生的簡單類型的變化：</span><span class="sxs-lookup"><span data-stu-id="7e0af-103">XML Schema definition (XSD) language provides several mechanisms for defining variations of simple types, based on derivations of existing simple types, as follows:</span></span>  
  
- <span data-ttu-id="7e0af-104">**限制**。</span><span class="sxs-lookup"><span data-stu-id="7e0af-104">**Restriction**.</span></span> <span data-ttu-id="7e0af-105">使用限制機制的簡單型別衍生包含對該類型可能值的限制引用。</span><span class="sxs-lookup"><span data-stu-id="7e0af-105">Simple type derivation by using the restriction mechanism involves the introduction of restrictions to the possible values for that type.</span></span> <span data-ttu-id="7e0af-106">這類的範例有數字類型的最小和/或最大值，或是字串類型的最小和最大長度。</span><span class="sxs-lookup"><span data-stu-id="7e0af-106">Examples are minimum and/or maximum values for numeric types, or a minimum and maximum length for string types.</span></span>  
  
- <span data-ttu-id="7e0af-107">**清單**。</span><span class="sxs-lookup"><span data-stu-id="7e0af-107">**List**.</span></span> <span data-ttu-id="7e0af-108">使用清單機制的簡單型別衍生允許將執行個體訊息中的單一屬性或項目值定義為包含特定類型的空格分隔的值清單。</span><span class="sxs-lookup"><span data-stu-id="7e0af-108">Simple type derivation by using the list mechanism allows a single attribute or element value in an instance message to be defined as consisting of a list of space-separated values of a particular type.</span></span>  
  
- <span data-ttu-id="7e0af-109">**等位**。</span><span class="sxs-lookup"><span data-stu-id="7e0af-109">**Union**.</span></span> <span data-ttu-id="7e0af-110">使用聯集機制的簡單型別衍生允許將執行個體訊息中的單一屬性或項目值定義為數個指定類型的其中一個之單一值。</span><span class="sxs-lookup"><span data-stu-id="7e0af-110">Simple type derivation by using the union mechanism allows a single attribute or element value in an instance message to be defined as a single value of one of several specified types.</span></span>  
  
  <span data-ttu-id="7e0af-111">本節更詳細地描述這些簡單型別衍生，包括如何在 [屬性] 視窗中設定適當的節點屬性以定義這些衍生，以及對應的 XSD 之建構方式。</span><span class="sxs-lookup"><span data-stu-id="7e0af-111">This section describes these simple type derivations in more detail, including how to define these derivations by setting the appropriate node properties in the Properties window, as well as how the corresponding XSD is constructed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7e0af-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="7e0af-112">In This Section</span></span>  
  
-   [<span data-ttu-id="7e0af-113">使用限制機制的簡單類型衍生</span><span class="sxs-lookup"><span data-stu-id="7e0af-113">Simple Type Derivation Using the Restriction Mechanism</span></span>](../core/simple-type-derivation-using-the-restriction-mechanism.md)  
  
-   [<span data-ttu-id="7e0af-114">使用清單機制的簡單類型衍生</span><span class="sxs-lookup"><span data-stu-id="7e0af-114">Simple Type Derivation Using the List Mechanism</span></span>](../core/simple-type-derivation-using-the-list-mechanism.md)  
  
-   [<span data-ttu-id="7e0af-115">使用聯集機制的簡單類型衍生</span><span class="sxs-lookup"><span data-stu-id="7e0af-115">Simple Type Derivation Using the Union Mechanism</span></span>](../core/simple-type-derivation-using-the-union-mechanism.md)