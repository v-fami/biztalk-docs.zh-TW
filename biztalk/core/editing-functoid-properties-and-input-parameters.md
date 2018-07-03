---
title: 編輯運算質屬性和輸入的參數 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 257f92d7-8196-4c7c-98de-819996270e43
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e95e6d3c4c026038c8118bff3a00e6ddde824df
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982375"
---
# <a name="editing-functoid-properties-and-input-parameters"></a><span data-ttu-id="d519e-102">編輯運算質屬性和輸入參數</span><span class="sxs-lookup"><span data-stu-id="d519e-102">Editing Functoid Properties and Input Parameters</span></span>
<span data-ttu-id="d519e-103">運算質屬性可分為下列幾類：</span><span class="sxs-lookup"><span data-stu-id="d519e-103">Functoid properties can be categorized as follows:</span></span>  
  
- <span data-ttu-id="d519e-104">**標籤**並**輸入參數**。</span><span class="sxs-lookup"><span data-stu-id="d519e-104">**Label** and **Input parameters**.</span></span> <span data-ttu-id="d519e-105">這兩個屬性為讀取/寫入屬性，且所有運算質都有這些屬性。</span><span class="sxs-lookup"><span data-stu-id="d519e-105">These two properties are read/write and are available for all functoids.</span></span> <span data-ttu-id="d519e-106">**標籤**屬性提供一個機制，提供運算質，而這有助於維護對應的特定執行個體的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="d519e-106">The **Label** property provides a mechanism for providing a descriptive name for a particular instance of a functoid, which may help in maintaining maps.</span></span> <span data-ttu-id="d519e-107">**輸入參數**屬性會提供存取權**設定\<運算質\>運算質**對話方塊中，運算質組態中扮演重要的角色。</span><span class="sxs-lookup"><span data-stu-id="d519e-107">The **Input parameters** property provides access to the **Configure \<Functoid\> Functoid** dialog box, which plays a central role in functoid configuration.</span></span>  
  
- <span data-ttu-id="d519e-108">**指令碼**並**表格迴圈格線**。</span><span class="sxs-lookup"><span data-stu-id="d519e-108">**Script** and **Table Looping Grid**.</span></span> <span data-ttu-id="d519e-109">這兩個屬性提供存取權僅適用於的對話方塊**Scripting**並**表格迴圈**運算質，分別。</span><span class="sxs-lookup"><span data-stu-id="d519e-109">These two properties provide access to dialog boxes that are only applicable to the **Scripting** and **Table Looping** functoids, respectively.</span></span> <span data-ttu-id="d519e-110">這些對話方塊分別是**設定指令碼處理運算質** 對話方塊中，**設定表格迴圈運算質** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d519e-110">These dialog boxes are the **Configure Scripting Functoid** dialog box and the **Configure Table Looping Functoid** dialog box.</span></span>  
  
- <span data-ttu-id="d519e-111">**名稱**，**幫助**，**最大輸入參數**，和**最小輸入參數**。</span><span class="sxs-lookup"><span data-stu-id="d519e-111">**Name**, **Help**, **Maximum Input Parameters**, and **Minimum Input Parameters**.</span></span> <span data-ttu-id="d519e-112">這四個屬性提供參考資訊，且永遠為唯讀。</span><span class="sxs-lookup"><span data-stu-id="d519e-112">These four are informational and always read-only.</span></span>  
  
  <span data-ttu-id="d519e-113">如需這些運算質屬性的概念資訊，請參閱[運算質屬性](../core/functoid-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d519e-113">For conceptual information about these functoid properties, see [Functoid Properties](../core/functoid-properties.md).</span></span>  
  
  <span data-ttu-id="d519e-114">本節提供使用，並特別修改，屬性的運算質，包括設定運算質，設定指令碼的輸入的參數的一般指示的逐步指示**指令碼處理**運算質，並設定表格格線**表格迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="d519e-114">This section provides step-by-step instructions for working with, and specifically modifying, the properties of functoids, including general instructions for configuring input parameters for functoids, configuring script for the **Scripting** functoid, and configuring table grid for the **Table Looping** functoid.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d519e-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="d519e-115">In This Section</span></span>  
  
-   [<span data-ttu-id="d519e-116">如何設定運算質輸入參數</span><span class="sxs-lookup"><span data-stu-id="d519e-116">How to Configure Functoid Input Parameters</span></span>](../core/how-to-configure-functoid-input-parameters.md)  
  
-   [<span data-ttu-id="d519e-117">How to Configure the Scripting Functoid</span><span class="sxs-lookup"><span data-stu-id="d519e-117">How to Configure the Scripting Functoid</span></span>](../core/how-to-configure-the-scripting-functoid.md)  
  
-   [<span data-ttu-id="d519e-118">如何設定表格迴圈和表格擷取程式運算質</span><span class="sxs-lookup"><span data-stu-id="d519e-118">How to Configure the Table Looping and Table Extractor Functoids</span></span>](../core/how-to-configure-the-table-looping-and-table-extractor-functoids.md)  
  
-   [<span data-ttu-id="d519e-119">如何加上標籤與註解的運算質</span><span class="sxs-lookup"><span data-stu-id="d519e-119">How to Label and Comment a Functoid</span></span>](../core/how-to-label-and-comment-a-functoid.md)