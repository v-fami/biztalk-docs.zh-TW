---
title: 如何新增命名空間範例適用於 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c76a90a9-5898-43b3-98af-ff546dd97153
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 212364030353001cae0589d4d7562641db4b77e6
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22294382"
---
# <a name="how-the-add-namespace-sample-works"></a><span data-ttu-id="70f91-102">如何新增命名空間範例的運作方式</span><span class="sxs-lookup"><span data-stu-id="70f91-102">How the Add Namespace Sample Works</span></span>
<span data-ttu-id="70f91-103">第二，第一個和第四個測試會使用**加入命名空間**元件位於 NamespaceSampleReceivePipeline 管線。</span><span class="sxs-lookup"><span data-stu-id="70f91-103">The first, second, and fourth tests use the **Add Namespace** component located in the NamespaceSampleReceivePipeline pipeline.</span></span> <span data-ttu-id="70f91-104">它會採用做為輸入的文件沒有命名空間的根節點上，如下所示：</span><span class="sxs-lookup"><span data-stu-id="70f91-104">It takes as input a document with no namespace on the root node, such as the following:</span></span>  
  
```  
<CanonicalOrder OrderID="OrderID_0" OrderDate="OrderDate_1" Status="Status_2">  
```  
  
 <span data-ttu-id="70f91-105">下表顯示設定的屬性值**加入命名空間**元件。</span><span class="sxs-lookup"><span data-stu-id="70f91-105">The following table shows the property values set for the **Add Namespace** component.</span></span>  
  
|<span data-ttu-id="70f91-106">屬性</span><span class="sxs-lookup"><span data-stu-id="70f91-106">Property</span></span>|<span data-ttu-id="70f91-107">型別</span><span class="sxs-lookup"><span data-stu-id="70f91-107">Type</span></span>|<span data-ttu-id="70f91-108">Value</span><span class="sxs-lookup"><span data-stu-id="70f91-108">Value</span></span>|  
|--------------|----------|-----------|  
|<span data-ttu-id="70f91-109">ExtractionNodeXPath</span><span class="sxs-lookup"><span data-stu-id="70f91-109">ExtractionNodeXPath</span></span>|<span data-ttu-id="70f91-110">靜態</span><span class="sxs-lookup"><span data-stu-id="70f91-110">Static</span></span>|<span data-ttu-id="70f91-111">(空的)</span><span class="sxs-lookup"><span data-stu-id="70f91-111">(empty)</span></span>|  
|<span data-ttu-id="70f91-112">NamespaceBase</span><span class="sxs-lookup"><span data-stu-id="70f91-112">NamespaceBase</span></span>|<span data-ttu-id="70f91-113">靜態</span><span class="sxs-lookup"><span data-stu-id="70f91-113">Static</span></span>|http://schemas.microsoft.biztalk.esb.test.com/test|  
|<span data-ttu-id="70f91-114">NamespacePrefix</span><span class="sxs-lookup"><span data-stu-id="70f91-114">NamespacePrefix</span></span>|<span data-ttu-id="70f91-115">靜態</span><span class="sxs-lookup"><span data-stu-id="70f91-115">Static</span></span>|<span data-ttu-id="70f91-116">esbTest</span><span class="sxs-lookup"><span data-stu-id="70f91-116">esbTest</span></span>|  
|<span data-ttu-id="70f91-117">分隔符號</span><span class="sxs-lookup"><span data-stu-id="70f91-117">Separator</span></span>|<span data-ttu-id="70f91-118">靜態</span><span class="sxs-lookup"><span data-stu-id="70f91-118">Static</span></span>|/|  
|<span data-ttu-id="70f91-119">XPath</span><span class="sxs-lookup"><span data-stu-id="70f91-119">XPaths</span></span>|<span data-ttu-id="70f91-120">動態</span><span class="sxs-lookup"><span data-stu-id="70f91-120">Dynamic</span></span>|<span data-ttu-id="70f91-121">/CanonicalOrder/@OrderID&#124;/CanonicalOrder/@OrderDate</span><span class="sxs-lookup"><span data-stu-id="70f91-121">/CanonicalOrder/@OrderID&#124;/CanonicalOrder/@OrderDate</span></span>|  
  
 <span data-ttu-id="70f91-122">表所示的屬性設定會導致元件執行兩個 XPath 查詢來搜尋 XML 文件/CanonicalOrder/@OrderID和/CanonicalOrder/@OrderDate(兩個指定的查詢**Xpath**屬性，以 「 管道 」 分隔字元）。</span><span class="sxs-lookup"><span data-stu-id="70f91-122">The property settings shown in the table cause the component to search the XML document by executing the two XPath queries /CanonicalOrder/@OrderID and /CanonicalOrder/@OrderDate (the two queries specified for the **XPaths** property, separated by a "pipe" character).</span></span> <span data-ttu-id="70f91-123">這些查詢將傳回的值**OrderID**和**OrderDate**屬性的根節點的文件; 在此範例中，兩個值是"OrderID_0"和"OrderDate_1"。</span><span class="sxs-lookup"><span data-stu-id="70f91-123">These queries return the values of the **OrderID** and **OrderDate** attributes of the root node of the document; in this example, the two values are "OrderID_0" and "OrderDate_1".</span></span>  
  
 <span data-ttu-id="70f91-124">元件會使用這些值，並在其他內容的值，建構新的根命名空間。</span><span class="sxs-lookup"><span data-stu-id="70f91-124">The component then uses these values, and the values of the other properties, to construct the new root namespace.</span></span> <span data-ttu-id="70f91-125">它結合了**NamespaceBase**、 **NamespacePrefix**、**分隔符號**，並以下列格式的兩個 XPath 查詢中的值：</span><span class="sxs-lookup"><span data-stu-id="70f91-125">It combines the **NamespaceBase**, the **NamespacePrefix**, the **Separator**, and the values from the two XPath queries in the following format:</span></span>  
  
```  
xmlns:{NamespacePrefix}="{NamespaceBase}{Separator}{XPaths[1]}{Seperator}  
                         {XPaths[2]}{Separator}...{XPaths[n]}"  
```  
  
 <span data-ttu-id="70f91-126">這會產生新的命名空間，如下所示：</span><span class="sxs-lookup"><span data-stu-id="70f91-126">This produces the new namespace, as shown here:</span></span>  
  
```  
xmlns:esbTest="http://schemas.microsoft.biztalk.esb.test.com/test  
               /OrderID_0/OrderDate_1"  
```  
  
 <span data-ttu-id="70f91-127">因此，更新的文件處理後**NamespaceSampleReceivePipeline**管線如下所示：</span><span class="sxs-lookup"><span data-stu-id="70f91-127">Therefore, the updated document after processing by the **NamespaceSampleReceivePipeline** pipeline is the following:</span></span>  
  
```  
<esbTest:CanonicalOrder xmlns:esbTest=  
    "http://schemas.microsoft.biztalk.esb.test.com/test/OrderID_0  
    /OrderDate_1" OrderID="OrderID_0" OrderDate="OrderDate_1"   
    Status="Status_2">  
```  
  
## <a name="using-the-extractionnodexpath-property"></a><span data-ttu-id="70f91-128">使用 ExtractionNodeXPath 屬性</span><span class="sxs-lookup"><span data-stu-id="70f91-128">Using the ExtractionNodeXPath Property</span></span>  
 <span data-ttu-id="70f91-129">根據預設，**加入命名空間**加入命名空間和前置詞資訊時，元件會使用訊息內的 XML 文件的根項目。</span><span class="sxs-lookup"><span data-stu-id="70f91-129">By default, the **Add Namespace** component uses the root element of the XML document within the message when adding namespace and prefix information.</span></span> <span data-ttu-id="70f91-130">如果您想要使用的 XML 文件子集做為訊息主體 （在某些案例中信封或一部分的輸入文件具有相關性有用），您可以設定**ExtractionNodeXPath**強制屬性**加入命名空間**来搜尋指定的項目，用於產生訊息的元件。</span><span class="sxs-lookup"><span data-stu-id="70f91-130">If you want to use only a subset of the XML document as the message body (useful in certain envelope scenarios or when only a portion of an inbound document has relevance), you can set the **ExtractionNodeXPath** property to force the **Add Namespace** component to seek the specified element for use as the resultant message.</span></span> <span data-ttu-id="70f91-131">例如，如果您知道 CanonicalOrder 訊息將會有一個**OrderDetails**取用者，其包含此訊息相關的項目，您可以設定**ExtractionNodeXPath**屬性，以指定的路徑**OrderDetails**項目。</span><span class="sxs-lookup"><span data-stu-id="70f91-131">For example, if you know that a received CanonicalOrder message will have only one **OrderDetails** element that is relevant for consumers of this message contained within it, you can set the **ExtractionNodeXPath** property to specify the path to the **OrderDetails** element.</span></span> <span data-ttu-id="70f91-132">您可以查看加入透過擷取至通過測試稍早所述的程序的範例。</span><span class="sxs-lookup"><span data-stu-id="70f91-132">You can see an example of this process in the Add Via Extraction to Pass-through test described earlier.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70f91-133">**ExtractionNodeXPath**屬性必須傳回只有一個元素的 XPath。</span><span class="sxs-lookup"><span data-stu-id="70f91-133">The **ExtractionNodeXPath** property must be an XPath that returns only one element.</span></span> <span data-ttu-id="70f91-134">元件將會引發例外狀況，如果結果不是元素或 XPath 查詢傳回多個項目。</span><span class="sxs-lookup"><span data-stu-id="70f91-134">The component will raise an exception if the result is not an element or if the XPath query returns more than one element.</span></span>