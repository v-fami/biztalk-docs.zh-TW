---
title: "索引運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Max Occurs property
- Index functoids, about Index functoids
- Index functoids
ms.assetid: 0c8ba427-881c-4b1f-92b9-61992d2a29df
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a22881e7694fee872b7820b8b99157ef2cf20170
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="index-functoid"></a><span data-ttu-id="728f1-102">索引運算質</span><span class="sxs-lookup"><span data-stu-id="728f1-102">Index Functoid</span></span>
<span data-ttu-id="728f1-103">**索引**運算質可讓您從中選取一系列的記錄中的特定記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="728f1-103">The **Index** functoid enables you to select information from a specific record in a series of records.</span></span> <span data-ttu-id="728f1-104">每個**索引**運算質均收集單一欄位的資訊。</span><span class="sxs-lookup"><span data-stu-id="728f1-104">Each **Index** functoid collects information from a single field.</span></span>  
  
 <span data-ttu-id="728f1-105">輸入檔案中的特定記錄通常會發生多次。</span><span class="sxs-lookup"><span data-stu-id="728f1-105">Certain records typically occur many times in an input file.</span></span> <span data-ttu-id="728f1-106">例如，在氣象報告中， **DailySummary**項目可能會發生多次。</span><span class="sxs-lookup"><span data-stu-id="728f1-106">For example, in a weather report, the **DailySummary** element might occur many times.</span></span> <span data-ttu-id="728f1-107">**DailySummary**項目可能包含溫度、 氣壓以及風速等屬性。</span><span class="sxs-lookup"><span data-stu-id="728f1-107">The **DailySummary** element might include attributes for the temperature, the barometric pressure, and the wind speed.</span></span> <span data-ttu-id="728f1-108">下列程式碼為氣象報告範例。</span><span class="sxs-lookup"><span data-stu-id="728f1-108">The following code is an example of a weather report.</span></span>  
  
```  
<ns0:WeatherReport xmlns:ns0="http://IndexFunctoid.WeatherReport">  
    <DailySummary Pressure="80" Windspeed="10" Temperature="20" />  
    <DailySummary Pressure="78" Windspeed="20" Temperature="23" />  
    <DailySummary Pressure="77" Windspeed="16" Temperature="24" />  
</ns0:WeatherReport>  
```  
  
 <span data-ttu-id="728f1-109">基礎結構描述， **Max Occurs**屬性**DailySummary**記錄會設定為 [unbounded]，表示週期性或迴圈記錄。</span><span class="sxs-lookup"><span data-stu-id="728f1-109">In the underlying schema, the **Max Occurs** property for the **DailySummary** record would be set to unbounded to indicate a recurring or looping record.</span></span> <span data-ttu-id="728f1-110">「BizTalk 對應工具」會將此記錄編譯為迴圈。</span><span class="sxs-lookup"><span data-stu-id="728f1-110">BizTalk Mapper compiles this record as a loop.</span></span>  
  
 <span data-ttu-id="728f1-111">假設您想要收集氣象資訊的前兩個**DailySummary**氣象報告的記錄。</span><span class="sxs-lookup"><span data-stu-id="728f1-111">Suppose you want to collect weather information for the first two **DailySummary** records of the weather report.</span></span> <span data-ttu-id="728f1-112">在 BizTalk 對應工具中，每個屬性**DailySummary**內送來源結構描述的記錄可以連線到**索引**運算質。</span><span class="sxs-lookup"><span data-stu-id="728f1-112">In BizTalk Mapper, each attribute from the **DailySummary** record of the incoming source schema can be connected to an **Index** functoid.</span></span> <span data-ttu-id="728f1-113">接著，每個**索引**運算質可以指定**DailySummary**要向資訊記錄： 第一個或第二個。</span><span class="sxs-lookup"><span data-stu-id="728f1-113">In turn, each **Index** functoid can specify the **DailySummary** record from which to draw the information: the first or second.</span></span> <span data-ttu-id="728f1-114">**索引**運算質就可以連接至目的結構描述的適當欄位。</span><span class="sxs-lookup"><span data-stu-id="728f1-114">The **Index** functoids can then be connected to the appropriate fields of the destination schema.</span></span>  
  
 <span data-ttu-id="728f1-115">下圖顯示**索引**以此方式使用的運算質。</span><span class="sxs-lookup"><span data-stu-id="728f1-115">The following figure shows **Index** functoids used in this way.</span></span>  
  
 <span data-ttu-id="728f1-116">![](../core/media/ebiz-prog-map-index.gif "ebiz_prog_map_index")</span><span class="sxs-lookup"><span data-stu-id="728f1-116">![](../core/media/ebiz-prog-map-index.gif "ebiz_prog_map_index")</span></span>  
<span data-ttu-id="728f1-117">索引運算質範例</span><span class="sxs-lookup"><span data-stu-id="728f1-117">Index Functoid Example</span></span>  
  
 <span data-ttu-id="728f1-118">若要取得的第一天的每日摘要資訊，請上限設定三個**索引**運算質的索引值設為 1。</span><span class="sxs-lookup"><span data-stu-id="728f1-118">To get the daily summary information for the first day, the upper set of three **Index** functoids have their index values set to 1.</span></span> <span data-ttu-id="728f1-119">若要取得第二天的每日摘要資訊，較低設定三個**索引**運算質的索引值設為 2。</span><span class="sxs-lookup"><span data-stu-id="728f1-119">To get the daily summary information for the second day, the lower set of three **Index** functoids have their index values set to 2.</span></span>  
  
 <span data-ttu-id="728f1-120">**索引**運算質使用**設定\<運算質\>運算質**對話方塊，即可設定其輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="728f1-120">**Index** functoids use the **Configure \<Functoid\> Functoid** dialog box to set their input parameters.</span></span> <span data-ttu-id="728f1-121">第一個輸入參數會識別在來源結構描述中迴圈記錄內的欄位。</span><span class="sxs-lookup"><span data-stu-id="728f1-121">The first input parameter identifies a field within a looping record in the source schema.</span></span> <span data-ttu-id="728f1-122">第二個及後續的輸入參數會指定特定的記錄。</span><span class="sxs-lookup"><span data-stu-id="728f1-122">The second and succeeding input parameters specify the particular record.</span></span> <span data-ttu-id="728f1-123">您可以指定多個索引值以選取巢狀重複結構中的記錄。</span><span class="sxs-lookup"><span data-stu-id="728f1-123">You can specify multiple index values to select a record within nested repeating structures.</span></span> <span data-ttu-id="728f1-124">最內層結構的索引值為第二個參數。</span><span class="sxs-lookup"><span data-stu-id="728f1-124">The index value for the innermost structure is the second parameter.</span></span> <span data-ttu-id="728f1-125">下一個最外層結構的索引值為第三個參數等等。</span><span class="sxs-lookup"><span data-stu-id="728f1-125">The index value for the next outermost structure would be the third parameter, and so on.</span></span> <span data-ttu-id="728f1-126">例如，假設上述**DailySummary**內的資料已**WeeklyData**記錄。</span><span class="sxs-lookup"><span data-stu-id="728f1-126">For example, suppose that the preceding **DailySummary** records were inside **WeeklyData** records.</span></span> <span data-ttu-id="728f1-127">擷取**不足的壓力**從第一個**DailySummary**中第二個**WeeklyData**、 第二個參數會是 1 和第三個參數為 2。</span><span class="sxs-lookup"><span data-stu-id="728f1-127">To retrieve the **Pressure** from the first **DailySummary** in the second **WeeklyData**, the second parameter would be 1 and the third parameter would be 2.</span></span>  
  
 <span data-ttu-id="728f1-128">請注意，此範例假設**不足的壓力**欄位不會重複。</span><span class="sxs-lookup"><span data-stu-id="728f1-128">Notice that this example assumes the **Pressure** field does not repeat.</span></span> <span data-ttu-id="728f1-129">如果欄位重複，索引會關閉 — 計數會從**不足的壓力** 欄位中，而非**每日摘要**。</span><span class="sxs-lookup"><span data-stu-id="728f1-129">If the field did repeat, the indices would be off—the count would begin with the **Pressure** field, rather than the **Daily Summary**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="728f1-130">雖然索引順序輸入參數通常為常數，但可以使用來源結構描述中節點的連結。</span><span class="sxs-lookup"><span data-stu-id="728f1-130">Although an index sequence input parameter is typically a constant, it is possible to use a link from a node in the source schema.</span></span> <span data-ttu-id="728f1-131">若此連結來自迴圈記錄，且不是第一個輸入參數的父項，則索引順序輸入值來自輸入執行個體訊息中節點的第一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="728f1-131">If this link comes from a looping record that is not a parent of the first input parameter, the index sequence input value comes from the first instance of the node in the input instance message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="728f1-132">索引順序輸入值一律與來源文件中的目前內容相關。</span><span class="sxs-lookup"><span data-stu-id="728f1-132">The value of the index sequence input is always in relation to the current context in the source document.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="728f1-133">**索引**運算質必須為許多索引值，與欄位層級到根節點底下的第一個層級的父節點。</span><span class="sxs-lookup"><span data-stu-id="728f1-133">An **Index** functoid must have as many index values as there are parent nodes from the field level to the first level below the root node.</span></span> <span data-ttu-id="728f1-134">例如，在多個氣象報告執行個體訊息中，需要兩個索引值。</span><span class="sxs-lookup"><span data-stu-id="728f1-134">For example, in the multiple weather report instance message, two index values are required.</span></span> <span data-ttu-id="728f1-135">在單一氣象報告執行個體訊息中，僅需要一個索引值。</span><span class="sxs-lookup"><span data-stu-id="728f1-135">In the single weather report instance message, only one index value is required.</span></span> <span data-ttu-id="728f1-136">若未設定必要的索引值數目**索引**運算質建立根據符合第一個輸入的參數的來源執行個體訊息中的第一個節點的輸出**索引**運算質。</span><span class="sxs-lookup"><span data-stu-id="728f1-136">Failure to set the required number of index values of an **Index** functoid creates output based on the first node in the source instance message that matches the first input parameter of the **Index** functoid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="728f1-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="728f1-137">See Also</span></span>  
 <span data-ttu-id="728f1-138">[如何新增索引運算質至對應](../core/how-to-add-index-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="728f1-138">[How to Add Index Functoids to a Map](../core/how-to-add-index-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="728f1-139">[進階運算質](../core/advanced-functoids.md) </span><span class="sxs-lookup"><span data-stu-id="728f1-139">[Advanced Functoids](../core/advanced-functoids.md) </span></span>  
 <span data-ttu-id="728f1-140">[反覆項目運算質](../core/iteration-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="728f1-140">[Iteration Functoid](../core/iteration-functoid.md) </span></span>  
 [<span data-ttu-id="728f1-141">記錄計數運算質</span><span class="sxs-lookup"><span data-stu-id="728f1-141">Record Count Functoid</span></span>](../core/record-count-functoid.md)