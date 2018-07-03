---
title: 累計運算質 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0549867-e0e4-4cdb-aae0-cadc99088e03
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7dffa6448511eca4d101423dbe356b82ff38aebb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004391"
---
# <a name="cumulative-functoids"></a><span data-ttu-id="eedc8-102">累計運算質</span><span class="sxs-lookup"><span data-stu-id="eedc8-102">Cumulative Functoids</span></span>

## <a name="overview"></a><span data-ttu-id="eedc8-103">概觀</span><span class="sxs-lookup"><span data-stu-id="eedc8-103">Overview</span></span>
<span data-ttu-id="eedc8-104">**累計**運算質會減少一系列的值設為單一的值，例如總和、 串連的字串或平均。</span><span class="sxs-lookup"><span data-stu-id="eedc8-104">**Cumulative** functoids reduce a series of values to a single value such as a sum, a concatenated string, or an average.</span></span>  

 <span data-ttu-id="eedc8-105">所有**累計**運算質都接受兩個輸入參數：</span><span class="sxs-lookup"><span data-stu-id="eedc8-105">All **Cumulative** functoids accept two input parameters:</span></span>  

1. <span data-ttu-id="eedc8-106">要累計的值。</span><span class="sxs-lookup"><span data-stu-id="eedc8-106">The value to accumulate.</span></span> <span data-ttu-id="eedc8-107">此值是所有數字**累計**以外的運算質**累計串連**運算質預期字串值。</span><span class="sxs-lookup"><span data-stu-id="eedc8-107">This value is numeric for all **Cumulative** functoids except the **Cumulative Concatenate** functoid which expects a string value.</span></span> <span data-ttu-id="eedc8-108">值的連結，通常是從**Field 屬性**，**欄位項目**，或**記錄**節點 (使用其**混合**屬性設定為  **，則為 true**)。</span><span class="sxs-lookup"><span data-stu-id="eedc8-108">The value is a link, often from a **Field Attribute**, **Field Element**, or **Record** node (with its **Mixed** property set to **True**).</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="eedc8-109">如果沒有上階**記錄**迴圈中的結構描述樹狀結構節點、 使用**累計**運算質不需要。</span><span class="sxs-lookup"><span data-stu-id="eedc8-109">If none of the ancestor **Record** nodes in the schema tree are looping, using a **Cumulative** functoid is unnecessary.</span></span>  

2. <span data-ttu-id="eedc8-110">累計此值的範圍。</span><span class="sxs-lookup"><span data-stu-id="eedc8-110">The scope within which the value is accumulated.</span></span> <span data-ttu-id="eedc8-111">此引數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="eedc8-111">This argument is optional.</span></span> <span data-ttu-id="eedc8-112">此引數指示要累計的值所必須緊密相關的程度。</span><span class="sxs-lookup"><span data-stu-id="eedc8-112">The argument indicates how closely related the specified values must be to be accumulated.</span></span>  

   <span data-ttu-id="eedc8-113">下表顯示範圍參數值及其效果：</span><span class="sxs-lookup"><span data-stu-id="eedc8-113">The following table shows the values for the scoping parameter and its effect:</span></span>  

|<span data-ttu-id="eedc8-114">範圍參數值</span><span class="sxs-lookup"><span data-stu-id="eedc8-114">Scoping Parameter Value</span></span>|<span data-ttu-id="eedc8-115">效果</span><span class="sxs-lookup"><span data-stu-id="eedc8-115">Effect</span></span>|  
|-----------------------------|------------|  
|<span data-ttu-id="eedc8-116">0 (零)</span><span class="sxs-lookup"><span data-stu-id="eedc8-116">0 (zero)</span></span>|<span data-ttu-id="eedc8-117">累計整個執行個體訊息的值。</span><span class="sxs-lookup"><span data-stu-id="eedc8-117">Accumulate the value over the entire instance message.</span></span> <span data-ttu-id="eedc8-118">預設值。</span><span class="sxs-lookup"><span data-stu-id="eedc8-118">The default.</span></span>|  
|<span data-ttu-id="eedc8-119">1 (一)</span><span class="sxs-lookup"><span data-stu-id="eedc8-119">1 (one)</span></span>|<span data-ttu-id="eedc8-120">以相同父項目累計項目值或屬性值。</span><span class="sxs-lookup"><span data-stu-id="eedc8-120">Accumulate the value of element or attribute values with the same parent element.</span></span>|  
|<span data-ttu-id="eedc8-121">2</span><span class="sxs-lookup"><span data-stu-id="eedc8-121">2</span></span>|<span data-ttu-id="eedc8-122">以相同父父代項目累計項目值或屬性值。</span><span class="sxs-lookup"><span data-stu-id="eedc8-122">Accumulate the value of element or attribute values with the same grandparent element.</span></span>|  
|<span data-ttu-id="eedc8-123">3 或以上</span><span class="sxs-lookup"><span data-stu-id="eedc8-123">3 or greater</span></span>|<span data-ttu-id="eedc8-124">累計依據先前模式逐步擴大範圍的項目值或屬性值 (父父父代、父父父父代等)。</span><span class="sxs-lookup"><span data-stu-id="eedc8-124">Accumulate the value of element or attribute values of progressively wider scope following the preceding pattern (great-grandparent, great-great-grandparent, etc.).</span></span>|  

## <a name="example"></a><span data-ttu-id="eedc8-125">範例</span><span class="sxs-lookup"><span data-stu-id="eedc8-125">Example</span></span>  
 <span data-ttu-id="eedc8-126">使用的範例**累計**運算質可能成本加總訂單。</span><span class="sxs-lookup"><span data-stu-id="eedc8-126">An example of using a **Cumulative** functoid might be summing costs across a purchase order.</span></span> <span data-ttu-id="eedc8-127">下列程式碼為訂單範例。</span><span class="sxs-lookup"><span data-stu-id="eedc8-127">The following code is an example of a purchase order.</span></span>  

```  
<ns0:PurchaseOrder xmlns:ns0="http://CumulativeFunctoid.PurchaseOrder">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <LineItems>  
        <Item>  
            <Product>Laptop Computer</Product>  
            <Description>Thin profile laptop</Description>  
            <Price>1999.95</Price>  
            <Quantity>1</Quantity>  
        </Item>  
        <Item>  
            <Product>Monitor Swipes</Product>  
            <Description>Disposable monitor swipes</Description>  
            <Price>3.95</Price>  
            <Quantity>10</Quantity>  
        </Item>  
    </LineItems>  
</ns0:PurchaseOrder>  
```  

 <span data-ttu-id="eedc8-128">**Max Occurs**屬性**項目**記錄，當然會**unbounded**。</span><span class="sxs-lookup"><span data-stu-id="eedc8-128">The **Max Occurs** property for the **Item** record would, of course, be **unbounded**.</span></span> <span data-ttu-id="eedc8-129">這表示 [Item] 記錄會重複，而 BizTalk 對應工具將此記錄編譯成迴圈。</span><span class="sxs-lookup"><span data-stu-id="eedc8-129">This indicates that the item record loops, and BizTalk Mapper compiles this record as a loop.</span></span>  

 <span data-ttu-id="eedc8-130">下圖顯示對應，使用**乘法**運算質並**累計總和**彙總的項目記錄的運算質，從內送訂單，並將結果輸出**POTotal**欄位：</span><span class="sxs-lookup"><span data-stu-id="eedc8-130">The following figure shows a map using a **Multiplication** functoid and a **Cumulative Sum** functoid to aggregate item records from an incoming purchase order and output the results in the **POTotal** field:</span></span>  

 <span data-ttu-id="eedc8-131">![顯示使用 「 累計總和 」 運算質的對應。] (../core/media/cumulativefunctoids.gif "cumulativefunctoids")</span><span class="sxs-lookup"><span data-stu-id="eedc8-131">![Map showing usage of the cumulative sum functoid.](../core/media/cumulativefunctoids.gif "cumulativefunctoids")</span></span>  


 <span data-ttu-id="eedc8-132">此對應使用先前的資料與預設範圍參數值 0 (零) 產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="eedc8-132">The map produces the following output with the preceding data and with the default scoping parameter value, 0 (zero):</span></span>  

```  
<ns0:SummedPO xmlns:ns0="http://CumulativeFunctoid.SummedPO">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <POTotal>2039.45</POTotal>  
</ns0:SummedPO>  
```  

 <span data-ttu-id="eedc8-133">在此範例中，所有**項目**記錄之下**LineItems**記錄都參與累計，範圍參數的預設值表示累計整個訊息的值。</span><span class="sxs-lookup"><span data-stu-id="eedc8-133">In this example, all the **Item** records under the **LineItems** record participate in the accumulation—the default for the scoping parameter indicates accumulating the values across the entire message.</span></span> <span data-ttu-id="eedc8-134">**價格**並**Quantity**欄位傳送到**乘法**運算質。</span><span class="sxs-lookup"><span data-stu-id="eedc8-134">The **Price** and **Quantity** fields are sent to a **Multiplication** functoid.</span></span> <span data-ttu-id="eedc8-135">輸出**乘法**運算質會變成輸入**累計總和**運算質。</span><span class="sxs-lookup"><span data-stu-id="eedc8-135">The output of the **Multiplication** functoid becomes the input to the **Cumulative Sum** functoid.</span></span> <span data-ttu-id="eedc8-136">輸出**累計總和**運算質是累計的值為**項目**記錄會周遊輸入的訂單中。</span><span class="sxs-lookup"><span data-stu-id="eedc8-136">The output of the **Cumulative Sum** functoid is the accumulated value as the **Item** records are traversed in the input purchase order.</span></span>  

> [!NOTE]
>  <span data-ttu-id="eedc8-137">輸入的累計彙總發生在父記錄，由此產生輸入連結。</span><span class="sxs-lookup"><span data-stu-id="eedc8-137">The cumulative aggregation of input takes place over the parent record from which the input link originates.</span></span> <span data-ttu-id="eedc8-138">即使**累計**運算質從另一個運算質取得其輸入，累計彙總都會經由輸入連結的父記錄輸入到運算質**累計**運算質。</span><span class="sxs-lookup"><span data-stu-id="eedc8-138">Even when the **Cumulative** functoid gets its input from another functoid, the cumulative aggregation takes place over the parent record of the input links to the functoid that serves as input to the **Cumulative** functoid.</span></span>  

 <span data-ttu-id="eedc8-139">將範圍參數變更為 1 (一) 並稍微修改輸出結構描述，得到類似下面的輸出：</span><span class="sxs-lookup"><span data-stu-id="eedc8-139">Changing the scoping parameter to 1 (one) and modifying the output schema slightly, yields output like the following:</span></span>  

```  
<ns0:SummedPO xmlns:ns0="http://CumulativeFunctoid.SummedPO">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <ItemTotal>1999.95</ItemTotal>  
    <ItemTotal>39.5</ItemTotal>  
</ns0:SummedPO>  
```  

 <span data-ttu-id="eedc8-140">將範圍參數設為 1 (一) 表示以相同父項累計項目或屬性的值。</span><span class="sxs-lookup"><span data-stu-id="eedc8-140">Setting the scoping parameter to 1 (one) indicates accumulating values for elements or attributes with the same parent.</span></span> <span data-ttu-id="eedc8-141">以下**價格**並**數量**欄位具有**項目**當做父代，以便針對每個運算質加總的值**項目**。</span><span class="sxs-lookup"><span data-stu-id="eedc8-141">Here the **Price** and **Quantity** fields have **Item** as a parent so that the functoid sums values for each individual **Item**.</span></span>  

 <span data-ttu-id="eedc8-142">若將範圍參數設為 2，則此運算質會以相同父父代累計項目或屬性的值。</span><span class="sxs-lookup"><span data-stu-id="eedc8-142">If the scoping parameter is 2, the functoid accumulates values for elements or attributes with the same grandparent.</span></span> <span data-ttu-id="eedc8-143">祖系**價格**並**Quantity**欄位是**LineItems**記錄。</span><span class="sxs-lookup"><span data-stu-id="eedc8-143">The grandparent of the **Price** and **Quantity** fields is the **LineItems** record.</span></span> <span data-ttu-id="eedc8-144">因為只有一個**LineItems**記錄執行個體訊息中，結果就是使用預設值：</span><span class="sxs-lookup"><span data-stu-id="eedc8-144">Because there is only one **LineItems** record in the instance message, the result is the same as using the default value:</span></span>  

```  
<ns0:SummedPO xmlns:ns0="http://CumulativeFunctoid.SummedPO">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <POTotal>2039.45</POTotal>  
</ns0:SummedPO>  
```  

> [!NOTE]
>  <span data-ttu-id="eedc8-145">累計運算質 (除了**累計字串**運算質) 忽略非數值輸入。</span><span class="sxs-lookup"><span data-stu-id="eedc8-145">Cumulative functoids (except for the **Cumulative String** functoid) ignore non-numeric input.</span></span> <span data-ttu-id="eedc8-146">例如，輸入值 "three" 會被忽略。</span><span class="sxs-lookup"><span data-stu-id="eedc8-146">For example, an input value of "three" is ignored.</span></span>  

 <span data-ttu-id="eedc8-147">**累計平均**，**累計最小值**，並**累計最大值**運算質的行為類似於**累計總和**運算質。</span><span class="sxs-lookup"><span data-stu-id="eedc8-147">The **Cumulative Average**, **Cumulative Minimum**, and **Cumulative Maximum** functoids behave similarly to the **Cumulative Sum** functoid.</span></span> <span data-ttu-id="eedc8-148">**累計字串**串連字串，而不是彙總數值。</span><span class="sxs-lookup"><span data-stu-id="eedc8-148">The **Cumulative String** concatenates strings rather than aggregating numeric values.</span></span>  

## <a name="available-functoids"></a><span data-ttu-id="eedc8-149">可用的運算質</span><span class="sxs-lookup"><span data-stu-id="eedc8-149">Available functoids</span></span>

 <span data-ttu-id="eedc8-150">**累計**運算質為：</span><span class="sxs-lookup"><span data-stu-id="eedc8-150">The **Cumulative** functoids are:</span></span> 

* <span data-ttu-id="eedc8-151">累計平均</span><span class="sxs-lookup"><span data-stu-id="eedc8-151">Cumulative Average</span></span>
* <span data-ttu-id="eedc8-152">累計串連</span><span class="sxs-lookup"><span data-stu-id="eedc8-152">Cumulative Concatenate</span></span>
* <span data-ttu-id="eedc8-153">累計最大值</span><span class="sxs-lookup"><span data-stu-id="eedc8-153">Cumulative Maximum</span></span>
* <span data-ttu-id="eedc8-154">累計最小值</span><span class="sxs-lookup"><span data-stu-id="eedc8-154">Cumulative Minimum</span></span>
* <span data-ttu-id="eedc8-155">累計總和</span><span class="sxs-lookup"><span data-stu-id="eedc8-155">Cumulative Sum</span></span>

<span data-ttu-id="eedc8-156">更多詳細資料，這些運算質上[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="eedc8-156">More details on these functoids are [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="eedc8-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eedc8-157">See Also</span></span>  
- [<span data-ttu-id="eedc8-158">如何新增基本運算質至對應</span><span class="sxs-lookup"><span data-stu-id="eedc8-158">How to Add Basic Functoids to a Map</span></span>](../core/how-to-add-basic-functoids-to-a-map.md)   
- <span data-ttu-id="eedc8-159">**累計運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="eedc8-159">**Cumulative Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
