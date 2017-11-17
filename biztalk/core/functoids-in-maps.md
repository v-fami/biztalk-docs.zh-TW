---
title: "在對應中的運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoids
- functoids, about functoids
- functoid types, Record Count
- functoid types, Looping
- Looping functoids
- functoids, categories
- functoid types, Addition
- Record Count functoids
ms.assetid: 10ee8b62-cb20-4d26-9d86-b6564f30c297
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 976af2faed27e6cae8a57d9c7c83308d0519d81d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="functoids-in-maps"></a><span data-ttu-id="56f4e-102">對應中的運算質</span><span class="sxs-lookup"><span data-stu-id="56f4e-102">Functoids in Maps</span></span>
<span data-ttu-id="56f4e-103">BizTalk 對應工具支援來源結構描述的記錄和欄位與目的結構描述中的複雜結構化轉換，從記錄和欄位。</span><span class="sxs-lookup"><span data-stu-id="56f4e-103">BizTalk Mapper supports complex structural transformations from records and fields in the source schema to records and fields in the destination schema.</span></span> <span data-ttu-id="56f4e-104">運算質透過使用預先定義的公式和特定值來執行計算，稱為引數。</span><span class="sxs-lookup"><span data-stu-id="56f4e-104">Functoids perform calculations by using predefined formulas and specific values, called arguments.</span></span> <span data-ttu-id="56f4e-105">會根據記錄和欄位的指定順序執行這些計算。</span><span class="sxs-lookup"><span data-stu-id="56f4e-105">These calculations are executed based on the designated order of the records and fields.</span></span>  
  
 <span data-ttu-id="56f4e-106">透過從工具箱選取運算質，將它拖曳到格線頁，再將它連結到來源結構描述和目的結構描述中的節點，您可以同時新增資料、修改日期或時間資訊、串連資料，或是執行其他作業。</span><span class="sxs-lookup"><span data-stu-id="56f4e-106">By selecting a functoid from the Toolbox, dragging it to the grid page, and linking it to nodes in the source schema and destination schema, data can be added together, date or time information can be modified, data can be concatenated, or other operations can be performed.</span></span> <span data-ttu-id="56f4e-107">例如，**加法**運算質會將值加入和**記錄計數**運算質會傳回執行個體訊息中的迴圈記錄總計數。</span><span class="sxs-lookup"><span data-stu-id="56f4e-107">For example, the **Addition** functoid adds values and the **Record Count** functoid returns the total count of a looping record in an instance message.</span></span> <span data-ttu-id="56f4e-108">您可以在 [工具箱] 中找到的運算質類別包括： 進階、 轉換、 累計、 資料庫、 日期 / 時間、 邏輯、 數學、 科學，以及字串。</span><span class="sxs-lookup"><span data-stu-id="56f4e-108">Categories of functoids that you can find in the Toolbox include: Advanced, Conversion, Cumulative, Database, Date/ Time, Logical, Mathematical, Scientific, and String.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56f4e-109">除了資料庫運算質之外，所有運算質皆為內嵌 C#。</span><span class="sxs-lookup"><span data-stu-id="56f4e-109">All functoids are inline C# except for the Database functoids.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56f4e-110">目的結構描述節點接受只能有一個輸入例外的運算質**迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="56f4e-110">Destination schema nodes accept only one input from a functoid with the exception of the **Looping** functoid.</span></span>  
  
 <span data-ttu-id="56f4e-111">本節主題描述如何移轉舊版本 BizTalk Server 的運算質、什麼是運算質、它們的用途，以及如何使用它們。</span><span class="sxs-lookup"><span data-stu-id="56f4e-111">The topics in this section describe how to migrate functoids from previous versions of BizTalk Server, what functoids are, what they do, and how to use them.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="56f4e-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="56f4e-112">In This Section</span></span>  
  
-   [<span data-ttu-id="56f4e-113">運算質類別</span><span class="sxs-lookup"><span data-stu-id="56f4e-113">Functoid Categories</span></span>](../core/functoid-categories.md)  
  
-   [<span data-ttu-id="56f4e-114">運算質輸入參數</span><span class="sxs-lookup"><span data-stu-id="56f4e-114">Functoid Input Parameters</span></span>](../core/functoid-input-parameters.md)  
  
-   [<span data-ttu-id="56f4e-115">基本運算質</span><span class="sxs-lookup"><span data-stu-id="56f4e-115">Basic Functoids</span></span>](../core/basic-functoids.md)  
  
-   [<span data-ttu-id="56f4e-116">進階運算質</span><span class="sxs-lookup"><span data-stu-id="56f4e-116">Advanced Functoids</span></span>](../core/advanced-functoids.md)  
  
-   [<span data-ttu-id="56f4e-117">串聯運算質</span><span class="sxs-lookup"><span data-stu-id="56f4e-117">Cascading Functoids</span></span>](../core/cascading-functoids.md)  
  
-   [<span data-ttu-id="56f4e-118">運算質屬性</span><span class="sxs-lookup"><span data-stu-id="56f4e-118">Functoid Properties</span></span>](../core/functoid-properties.md)  
  
-   [<span data-ttu-id="56f4e-119">移轉運算質</span><span class="sxs-lookup"><span data-stu-id="56f4e-119">Migrating Functoids</span></span>](../core/migrating-functoids.md)