---
title: 複雜全域型別衍生 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fbf429d0-64f4-4c43-a5f7-e8af050803b9
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee4e6235af62b2c08c08382b897632d15e34e0cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231670"
---
# <a name="complex-global-type-derivation"></a><span data-ttu-id="922e8-102">複雜全域型別衍生</span><span class="sxs-lookup"><span data-stu-id="922e8-102">Complex Global Type Derivation</span></span>
<span data-ttu-id="922e8-103">XSD 有兩個類型的繼承：延伸模組與限制。</span><span class="sxs-lookup"><span data-stu-id="922e8-103">There are two types of inheritance in XSD: extension and restriction.</span></span> <span data-ttu-id="922e8-104">BizTalk 編輯器 」 可存取此 XSD 功能使用下列兩個**記錄**節點屬性：</span><span class="sxs-lookup"><span data-stu-id="922e8-104">BizTalk Editor provides access to this XSD functionality by using the following two **Record** node properties:</span></span>  
  
-   <span data-ttu-id="922e8-105">**基底資料型別**。</span><span class="sxs-lookup"><span data-stu-id="922e8-105">**Base Data Type**.</span></span> <span data-ttu-id="922e8-106">此屬性提供所有可做為基底資料型別的全域複雜型別與簡單型別的清單。</span><span class="sxs-lookup"><span data-stu-id="922e8-106">This property provides the list of all global complex types and simple types available for use as a base data type.</span></span> <span data-ttu-id="922e8-107">複雜全域型別可位在相同的結構描述或任何匯入的結構描述中。</span><span class="sxs-lookup"><span data-stu-id="922e8-107">The complex global types can be in the same schema or in any imported schema.</span></span>  
  
-   <span data-ttu-id="922e8-108">**由衍生**。</span><span class="sxs-lookup"><span data-stu-id="922e8-108">**Derived By**.</span></span> <span data-ttu-id="922e8-109">可使用此屬性來選擇由延伸模組衍生或由限制衍生。</span><span class="sxs-lookup"><span data-stu-id="922e8-109">This property is used to choose between deriving by extension or by restriction.</span></span> <span data-ttu-id="922e8-110">這個屬性會自動設定為**延伸**當您將**基底資料型別**清單中的任何類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="922e8-110">This property is automatically set to **Extension** when you set the **Base Data Type** property to any type in the list.</span></span> <span data-ttu-id="922e8-111">如果您將此屬性設定為 **（預設）**，任何在**基底資料型別**移除屬性，停用繼承節點。</span><span class="sxs-lookup"><span data-stu-id="922e8-111">If you set this property to **(Default)**, any type in the **Base Data Type** property is removed, disabling inheritance for the node.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="922e8-112">**內容類型**屬性也設定為自動**ComplexContent**使用的延伸模組或限制衍生時。</span><span class="sxs-lookup"><span data-stu-id="922e8-112">The **Content Type** property is also set automatically to **ComplexContent** when derivation by extension or restriction is being used.</span></span>  
  
 <span data-ttu-id="922e8-113">本節將更詳盡說明使用延伸模組和限制機制的複雜型別衍生。</span><span class="sxs-lookup"><span data-stu-id="922e8-113">This section explains complex type derivation by using the extension and restriction mechanisms in greater detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="922e8-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="922e8-114">In This Section</span></span>  
  
-   [<span data-ttu-id="922e8-115">使用延伸模組機制的複雜型別衍生</span><span class="sxs-lookup"><span data-stu-id="922e8-115">Complex Type Derivation Using the Extension Mechanism</span></span>](../core/complex-type-derivation-using-the-extension-mechanism.md)  
  
-   [<span data-ttu-id="922e8-116">使用限制機制的複雜型別衍生</span><span class="sxs-lookup"><span data-stu-id="922e8-116">Complex Type Derivation Using the Restriction Mechanism</span></span>](../core/complex-type-derivation-using-the-restriction-mechanism.md)