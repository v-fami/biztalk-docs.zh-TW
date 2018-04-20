---
title: 迴圈運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19886ccb-4642-48a4-b93e-563640ea828b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ce2b66fd796708a0e8b24ee05e3a0b043af6808
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="looping-functoid"></a><span data-ttu-id="2e242-102">迴圈運算質</span><span class="sxs-lookup"><span data-stu-id="2e242-102">Looping Functoid</span></span>

## <a name="overview--example"></a><span data-ttu-id="2e242-103">概觀 （& s) 範例</span><span class="sxs-lookup"><span data-stu-id="2e242-103">Overview & example</span></span>
<span data-ttu-id="2e242-104">**迴圈** 運算質結合多個記錄或欄位在來源結構描述至目的結構描述中的單一記錄。</span><span class="sxs-lookup"><span data-stu-id="2e242-104">The **Looping** functoid combines multiple records or fields in the source schema into a single record in the destination schema.</span></span>  
  
 <span data-ttu-id="2e242-105">下圖顯示 **迴圈**運算質在對應中用來結合位址從兩個不同調查收集到單一主要地址清單。</span><span class="sxs-lookup"><span data-stu-id="2e242-105">The following figure shows a **Looping**functoid used in a map to combine addresses collected from two different surveys into a single master address list.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e242-106">**迴圈** 和 **值對應 （簡維）** 運算質不應在一起。</span><span class="sxs-lookup"><span data-stu-id="2e242-106">The **Looping** and **Value Mapping (Flattening)** functoids should not be used together.</span></span> <span data-ttu-id="2e242-107">如果一起使用，就會產生編譯的對應，假設沒有來源迴圈相依性的目標節點下方的 **迴圈** 運算質。</span><span class="sxs-lookup"><span data-stu-id="2e242-107">If both are used together, it results in a compiled map that assumed there is no source looping dependency for the target nodes that are below the **Looping** functoid.</span></span>  
  
 <span data-ttu-id="2e242-108">![迴圈運算質用法的對應。] (../core/media/loopingfunctoid.gif "loopingfunctoid")</span><span class="sxs-lookup"><span data-stu-id="2e242-108">![Map illustrating the use of the looping functoid.](../core/media/loopingfunctoid.gif "loopingfunctoid")</span></span>  
  
 <span data-ttu-id="2e242-109">**FoodSurvey** 和 **[flowersurvey]** 將來源結構描述的迴圈記錄對應至迴圈 **位址** 記錄目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="2e242-109">The **FoodSurvey** and **FlowerSurvey** looping records of the source schema are mapped to the looping **Address** record of the destination schema.</span></span> <span data-ttu-id="2e242-110">如果輸入執行個體訊息有三個 **FoodSurvey** 記錄和兩個 **[flowersurvey]** 記錄 **迴圈**運算質結合這些元件，以建立五個 **位址** 輸出執行個體訊息中的記錄。</span><span class="sxs-lookup"><span data-stu-id="2e242-110">If an input instance message has three **FoodSurvey** records and two **FlowerSurvey** records, the **Looping**functoid combines these to create five **Address** records in the output instance message.</span></span>  
  
 <span data-ttu-id="2e242-111">以下程式碼為範例輸入執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="2e242-111">The following code is a sample input instance message.</span></span>  
  
```  
<ns0:Surveys xmlns:ns0="http://LoopingFunctoid.Surveys">  
    <FoodSurvey Name="Karin Zimprich" Address="345 N 63rd St" City="Boston" State="MA" PostalCode="07485" />  
    <FoodSurvey Name="Wendy Wheeler" Address="7890 Broadway" City="Columbus" State="OH" PostalCode="46290" />  
    <FoodSurvey Name="Florian Voss" Address="1234 Main St" City="Denver" State="CO" PostalCode="97402" />  
    <FlowerSurvey Name="Kelly Focht" Address="456 1st Ave" City="Miami" State="FL" PostalCode="81406" />  
    <FlowerSurvey Name="Jim Kim" Address="567 2nd Ave" City="Seattle" State="WA" PostalCode="98103" />  
</ns0:Surveys>  
```  
  
 <span data-ttu-id="2e242-112">此輸入執行個體訊息會產生下列輸出執行個體訊息時由前面的圖中的對應。</span><span class="sxs-lookup"><span data-stu-id="2e242-112">This input instance message produces the following output instance message when processed by the map in the preceding figure.</span></span>  
  
```  
<ns0:MasterAddresses xmlns:ns0="http://LoopingFunctoid.MasterAddresses">  
    <Address Name="Karin Zimprich" Street="345 N 63rd St" City="Boston" State="MA" PostalCode="07458"/>  
    <Address Name="Wendy Wheeler" Street="7890 Broadway" City="Columbus" State="OH" PostalCode="46290"/>  
    <Address Name="Florian Voss" Street="1234 Main St" City="Denver" State="CO" PostalCode="97402"/>  
    <Address Name="Kelly Focht" Street="456 1st Ave" City="Miami" State="FL" PostalCode="81406"/>  
    <Address Name="Jim Kim" Street="567 2nd Ave" City="Seattle" State="WA" PostalCode="98103"/>  
</ns0:MasterAddresses>  
```  
  
 <span data-ttu-id="2e242-113">**FoodSurvey** 和 **[flowersurvey]** 訊息位址已結合。</span><span class="sxs-lookup"><span data-stu-id="2e242-113">The **FoodSurvey** and **FlowerSurvey** message addresses have been combined.</span></span> <span data-ttu-id="2e242-114">結合的訊息不會指出每個位址的來源。</span><span class="sxs-lookup"><span data-stu-id="2e242-114">The combined message does not indicate the source of each address.</span></span> <span data-ttu-id="2e242-115">如果您想要追蹤來源，加入 **來源** 屬性設定為 **位址** 記錄 **MasterAddress** 結構描述和對應的常數值。</span><span class="sxs-lookup"><span data-stu-id="2e242-115">If you want to track the source, add a **Source** attribute to the **Address** record of the **MasterAddress** schema and map a constant value.</span></span> <span data-ttu-id="2e242-116">若要設定此值，連線 **FoodSurvey** 欄位至新 **來源** 欄位。</span><span class="sxs-lookup"><span data-stu-id="2e242-116">To set this value, connect the **FoodSurvey** field to the new **Source** field.</span></span> <span data-ttu-id="2e242-117">在連接器一行，修改 **連結屬性** & #124; **編譯器** & #124; **來源連結** 「 複製名稱 」 的屬性。</span><span class="sxs-lookup"><span data-stu-id="2e242-117">On the connector line, modify the **Link Properties** &#124; **Compiler** &#124; **Source Links** property to "Copy name".</span></span> <span data-ttu-id="2e242-118">重複此程序 **[flowersurvey]** 欄位。</span><span class="sxs-lookup"><span data-stu-id="2e242-118">Repeat this process for the **FlowerSurvey** field.</span></span> <span data-ttu-id="2e242-119">從上述程序重新處理輸入訊息會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2e242-119">Reprocessing the input message from above yields the following output:</span></span>  
  
```  
<ns0:MasterAddresses xmlns:ns0="http://LoopingFunctoid.MasterAddresses">  
    <Address Name="Karin Zimprich" Street="345 N 63rd St" City="Boston" State="MA" PostalCode="07458" Source="FoodSurvey"/>  
    <Address Name="Wendy Wheeler" Street="7890 Broadway" City="Columbus" State="OH" PostalCode="46290" Source="FoodSurvey"/>  
    <Address Name="Florian Voss" Street="1234 Main St" City="Denver" State="CO" PostalCode="97402" Source="FoodSurvey"/>  
    <Address Name="Kelly Focht" Street="456 1st Ave" City="Miami" State="FL" PostalCode="81406" Source="FlowerSurvey"/>  
    <Address Name="Jim Kim" Street="567 2nd Ave" City="Seattle" State="WA" PostalCode="98103" Source="FlowerSurvey"/>  
</ns0:MasterAddresses>  
```  

## <a name="relationships-with-nodes"></a><span data-ttu-id="2e242-120">與節點關聯性</span><span class="sxs-lookup"><span data-stu-id="2e242-120">Relationships with nodes</span></span>

 <span data-ttu-id="2e242-121">在節點之間的關聯性影響行為的 **迴圈** 運算質。</span><span class="sxs-lookup"><span data-stu-id="2e242-121">Relationships among nodes affect the behavior of the **Looping** functoid.</span></span> <span data-ttu-id="2e242-122">例如，連結的子節點和其來源結構描述中的父系 **迴圈** 運算質可防止在目的節點建立。</span><span class="sxs-lookup"><span data-stu-id="2e242-122">For example, linking both a child node and its parent in the source schema to the **Looping** functoid prevents the destination node from being created.</span></span>  
  
 <span data-ttu-id="2e242-123">運算質也會受來源節點間的關係影響。</span><span class="sxs-lookup"><span data-stu-id="2e242-123">Functoids are also affected by the relationships among source nodes.</span></span> <span data-ttu-id="2e242-124">將運算質連接至來源節點的非同層級子欄位 **迴圈** 運算質可能會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="2e242-124">Connecting a functoid to non-sibling child fields of source nodes of the **Looping** functoid may produce unexpected results.</span></span> <span data-ttu-id="2e242-125">比方說，使用 **字串串連** 運算質結合 **FoodSurvey** 名稱 欄位和 **flowersurvey** 的地址名稱欄位中的 位址 欄位 **MasterAddress** 會產生下列輸出執行個體訊息︰</span><span class="sxs-lookup"><span data-stu-id="2e242-125">For example, using the **String Concatenate** functoid to combine the **FoodSurvey** Name field and **FlowerSurvey** Address field into the Address Name field in **MasterAddress** would produce the following output instance message:</span></span>  
  
```  
<ns0:MasterAddresses xmlns:ns0="http://LoopingFunctoid.MasterAddresses">  
    <Address Street="345 N 63rd St" City="Boston" State="MA" PostalCode="07458"/>  
    <Address Street="7890 Broadway" City="Columbus" State="OH" PostalCode="46290"/>  
    <Address Street="1234 Main St" City="Denver" State="CO" PostalCode="97402"/>  
    <Address Name="Kelly Focht" Street="456 1st Ave" City="Miami" State="FL" PostalCode="81406"/>  
    <Address Name="Jim Kim" Street="567 2nd Ave" City="Seattle" State="WA" PostalCode="98103"/>  
</ns0:MasterAddresses>  
```  
  
 <span data-ttu-id="2e242-126">請注意如何 **名稱** 欄位缺少 **FoodSurvey** 來源訊息卻存在 **[flowersurvey]** 來源訊息。</span><span class="sxs-lookup"><span data-stu-id="2e242-126">Notice how the **Name** field is missing for **FoodSurvey** source messages but is present for **FlowerSurvey** source messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2e242-127">將運算質連接至來源節點的子欄位 **迴圈** 運算質可能會產生非預期的結果，如果來源節點不是同層級。</span><span class="sxs-lookup"><span data-stu-id="2e242-127">Connecting a functoid to child fields of source nodes of the **Looping** functoid may produce unexpected results if the source nodes are not siblings.</span></span>  
  
 <span data-ttu-id="2e242-128">**迴圈** 運算質是功能強大的建構，可用來建立條件式迴圈，並將結構描述對應到類別目錄。</span><span class="sxs-lookup"><span data-stu-id="2e242-128">The **Looping** functoid is a powerful construct that you can use to create conditional loops and to map schemas to catalogs.</span></span> <span data-ttu-id="2e242-129">也有一些重疊的效果 **迴圈** 運算質路徑，您需要列入考量。</span><span class="sxs-lookup"><span data-stu-id="2e242-129">There are also some effects of overlapping **Looping** functoid paths you need to take into account.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2e242-130">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="2e242-130">Next steps</span></span>
  
-   [<span data-ttu-id="2e242-131">條件式迴圈</span><span class="sxs-lookup"><span data-stu-id="2e242-131">Conditional Looping</span></span>](../core/conditional-looping.md)  
  
-   [<span data-ttu-id="2e242-132">目錄的一般結構描述</span><span class="sxs-lookup"><span data-stu-id="2e242-132">Flat Schema to Catalog</span></span>](../core/flat-schema-to-catalog.md)  
  
-   [<span data-ttu-id="2e242-133">迴圈路徑</span><span class="sxs-lookup"><span data-stu-id="2e242-133">Loop Paths</span></span>](../core/loop-paths.md)  
  
## <a name="see-also"></a><span data-ttu-id="2e242-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e242-134">See Also</span></span>  
 <span data-ttu-id="2e242-135">**表格迴圈運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="2e242-135">**Table Looping Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>