---
title: "值對應運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Value Mapping functoids
- functoids, empty tags
- Concatenate functoids
ms.assetid: 3dd626fb-3bf6-4ede-9fd2-ddae5a54d178
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2bb8e89ed790fe9916efe69685ad667d9fe9403
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="value-mapping-functoid"></a><span data-ttu-id="f4944-102">值對應運算質</span><span class="sxs-lookup"><span data-stu-id="f4944-102">Value Mapping Functoid</span></span>
<span data-ttu-id="f4944-103">**值對應**運算質會傳回其第二個參數的值，如果第一個參數為 true。</span><span class="sxs-lookup"><span data-stu-id="f4944-103">The **Value Mapping** functoid returns the value of its second parameter if its first parameter is true.</span></span> <span data-ttu-id="f4944-104">運算質的一般用途是將欄位的屬性變更為記錄的屬性。</span><span class="sxs-lookup"><span data-stu-id="f4944-104">A common use of the functoid is to change the attributes of a field into the attributes of a record.</span></span> <span data-ttu-id="f4944-105">若要藉由將多個記錄轉換成單一記錄扁平化的輸入訊息的一部分，請使用[值對應 （簡維） 運算質](../core/value-mapping-flattening-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="f4944-105">To flatten a portion of an input message by converting multiple records into a single record, use the [Value Mapping (Flattening) Functoid](../core/value-mapping-flattening-functoid.md).</span></span>  
  
 <span data-ttu-id="f4944-106">下圖顯示具有對應**值對應**運算質用於記錄屬性變更欄位的屬性。</span><span class="sxs-lookup"><span data-stu-id="f4944-106">The following figure shows a map with the **Value Mapping** functoid used to change the attributes of a field into the attributes of a record.</span></span>  
  
 ![](../core/media/valuemappingfunctoid.gif "valuemappingfunctoid")  
<span data-ttu-id="f4944-107">值對應運算質對應</span><span class="sxs-lookup"><span data-stu-id="f4944-107">Value Mapping Functoid Map</span></span>  
  
 <span data-ttu-id="f4944-108">下列程式碼會顯示輸入執行個體訊息中其中成對的名稱和值會指派給**名稱**和**值**屬性。</span><span class="sxs-lookup"><span data-stu-id="f4944-108">The following code shows an input instance message in which pairs of names and values are assigned to **Name** and **Value** attributes.</span></span>  
  
```  
<ns0:Root xmlns:ns0="http://ValueMapping.WeatherIn">  
    <Record>  
        <Field Name="WindSpeed" Value="5"/>   
        <Field Name="Temperature" Value="20" />  
    </Record>  
    <Record>  
        <Field Name="WindSpeed" Value="15" />  
        <Field Name="Temperature" Value="18" />  
    </Record>  
</ns0:Root>  
```  
  
 <span data-ttu-id="f4944-109">上述對應可將此訊息轉換成一組，其中值會指派給不同記錄中具有對應名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="f4944-109">The preceding map can convert this message into one in which the values are assigned to attributes with the corresponding names in separate records.</span></span>  
  
```  
<ns0:Root xmlns:ns0="http://ValueMapping.WeatherOut">  
    <Record WindSpeed="5"/>  
    <Record Temperature="20"/>  
    <Record WindSpeed="15"/>  
    <Record Temperature="18"/>  
</ns0:Root>  
```  
  
 <span data-ttu-id="f4944-110">**等於**運算質會測試的值**名稱**屬性。</span><span class="sxs-lookup"><span data-stu-id="f4944-110">The **Equal** functoids test the values of the **Name** attribute.</span></span> <span data-ttu-id="f4944-111">第一個**等於**值的運算質會測試**名稱**為"WindSpeed"。</span><span class="sxs-lookup"><span data-stu-id="f4944-111">The first **Equal** functoid tests for the value of **Name** being "WindSpeed."</span></span> <span data-ttu-id="f4944-112">當**名稱**為"WindSpeed，"第一個**等於**運算質會傳回**True**。</span><span class="sxs-lookup"><span data-stu-id="f4944-112">When the **Name** is "WindSpeed," the first **Equal** functoid returns **True**.</span></span> <span data-ttu-id="f4944-113">這項目，接著，可讓**值對應**設定的值的運算質**WindSpeed**輸出執行個體訊息中的屬性。</span><span class="sxs-lookup"><span data-stu-id="f4944-113">This, in turn, allows the **Value Mapping** functoid to set the value of the **WindSpeed** attribute in the output instance message.</span></span>  
  
## <a name="suppressing-the-creation-of-empty-tags"></a><span data-ttu-id="f4944-114">抑制空白標記的建立</span><span class="sxs-lookup"><span data-stu-id="f4944-114">Suppressing the Creation of Empty Tags</span></span>  
 <span data-ttu-id="f4944-115">若要抑制空白標記，請使用值對應運算質來控制是否要建立標記。</span><span class="sxs-lookup"><span data-stu-id="f4944-115">To suppress empty tags, use the Value Mapping functoid to control if a tag gets created or not.</span></span> <span data-ttu-id="f4944-116">如果該值評估為 True，就會建立目的地欄位；否則，就不會建立目的地欄位。</span><span class="sxs-lookup"><span data-stu-id="f4944-116">If the value is evaluated to true, the destination field will be created; otherwise the destination field will not be created.</span></span> <span data-ttu-id="f4944-117">在迴圈案例中，請使用邏輯運算質，並將它連接到目的地記錄或欄位。</span><span class="sxs-lookup"><span data-stu-id="f4944-117">In a looping scenario, use a logical functoid and connect it to the destination record or field.</span></span> <span data-ttu-id="f4944-118">如果情況評估為 False，就不會建立標記。</span><span class="sxs-lookup"><span data-stu-id="f4944-118">If the condition is evaluated to false, the tag will not be created.</span></span> <span data-ttu-id="f4944-119">如需範例，請參閱[條件式迴圈](../core/conditional-looping.md)。</span><span class="sxs-lookup"><span data-stu-id="f4944-119">For an example, see [Conditional Looping](../core/conditional-looping.md).</span></span>  
  
## <a name="forcing-the-creation-of-empty-tags"></a><span data-ttu-id="f4944-120">強制空白標記的建立</span><span class="sxs-lookup"><span data-stu-id="f4944-120">Forcing the Creation of Empty Tags</span></span>  
 <span data-ttu-id="f4944-121">若要強制建立空白標記，您可以將值連結的目的地欄位的值屬性中**Concatenate**運算質到目的地欄位。</span><span class="sxs-lookup"><span data-stu-id="f4944-121">To force empty tags to be created, you can add a value in the Value property of the destination field or link a **Concatenate** functoid to the destination field.</span></span>  <span data-ttu-id="f4944-122">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，便可選取來強制產生空白標記"\<空白 >"在目的地欄位的 Value 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f4944-122">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], it is possible to force the generation of empty tags by selecting the "\<empty>" value in the Value property of the destination field.</span></span> <span data-ttu-id="f4944-123">在此情況下，該欄位會以空值建立。</span><span class="sxs-lookup"><span data-stu-id="f4944-123">In this case the field will be created with the empty value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4944-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4944-124">See Also</span></span>  
 <span data-ttu-id="f4944-125">[值對應 （簡維） 運算質](../core/value-mapping-flattening-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="f4944-125">[Value Mapping (Flattening) Functoid](../core/value-mapping-flattening-functoid.md) </span></span>  
 <span data-ttu-id="f4944-126">[如何新增值對應運算質至對應](../core/how-to-add-value-mapping-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="f4944-126">[How to Add Value Mapping Functoids to a Map](../core/how-to-add-value-mapping-functoids-to-a-map.md) </span></span>  
 [<span data-ttu-id="f4944-127">進階運算質</span><span class="sxs-lookup"><span data-stu-id="f4944-127">Advanced Functoids</span></span>](../core/advanced-functoids.md)