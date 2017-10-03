---
title: "表格驅動迴圈範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Table Extractor functoids, code sample
- Table Looping functoids
- Table Extractor functoids
- Table Looping functoids, about Table Looping functoids
- Table Extractor functoids, about Table Extractor functoids
- code samples, Table Looping functoids
- Table Looping functoids, code sample
- code samples, Table Extractor functoids
ms.assetid: d890bdb1-12a6-4001-9748-737b1f2bab79
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91e0710a8238075610d98b5897fdc7865f30190f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="table-driven-looping-example"></a><span data-ttu-id="52b2d-102">表格驅動迴圈範例</span><span class="sxs-lookup"><span data-stu-id="52b2d-102">Table-Driven Looping Example</span></span>
<span data-ttu-id="52b2d-103">本節將簡短描述對應使用**表格迴圈**和**表格抽選程式**運算質。</span><span class="sxs-lookup"><span data-stu-id="52b2d-103">This section briefly describes a map using the **Table Looping** and **Table Extractor** functoids.</span></span> <span data-ttu-id="52b2d-104">如需選取的詳細資訊，放置、 連結及設定運算質，請參閱[如何新增表格迴圈和表格擷取程式運算質至對應](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)。</span><span class="sxs-lookup"><span data-stu-id="52b2d-104">For detailed information about selecting, placing, linking, and configuring the functoids, see [How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md).</span></span>  
  
 <span data-ttu-id="52b2d-105">假設您有一個位址清單，需要用在需要有個別運送和帳單寄送地址的文件。</span><span class="sxs-lookup"><span data-stu-id="52b2d-105">Suppose you have a list of addresses that you need to use in a document requiring separate ship-to and bill-to addresses.</span></span> <span data-ttu-id="52b2d-106">這些位址的顯示方式可能會與下列程式碼類似。</span><span class="sxs-lookup"><span data-stu-id="52b2d-106">The addresses might appear like the following code.</span></span>  
  
```  
<ns0:Root xmlns:ns0="http://TableLoopingSample.Addresses">  
    <Address>  
        <Name>Kelly Focht</Name>  
        <Street>456 1st Ave</Street>  
        <City>Miami</City>  
        <State>FL</State>  
        <PostalCode>81406</PostalCode>  
    </Address>  
    <Address>  
        <Name>Wendy Wheeler</Name>  
        <Street>7890 Broadway</Street>  
        <City>Columbus</City>  
        <State>OH</State>  
        <PostalCode>46290</PostalCode>  
    </Address>  
</ns0:Root>  
```  
  
 <span data-ttu-id="52b2d-107">輸出可能採取的一種格式會是下列程式碼，雖然地址會重複，但是透過屬性所產生。</span><span class="sxs-lookup"><span data-stu-id="52b2d-107">One form the output could take would be the following code, duplicating the addresses but marking them with attributes.</span></span>  
  
```  
<ns0:Root xmlns:ns0="http://TableLoopingSample.POAddresses">  
    <Address Type="ShipTo">  
        <Name>Kelly Focht</Name>  
        <Street>456 1st Ave</Street>  
        <City>Miami</City>  
        <State>FL</State>  
        <PostalCode>81406</PostalCode>  
    </Address>  
    <Address Type="BillTo">  
        <Name>Kelly Focht</Name>  
        <Street>456 1st Ave</Street>  
        <City>Miami</City><State>FL</State>  
        <PostalCode>81406</PostalCode>  
    </Address>  
    <Address Type="ShipTo">  
        <Name>Wendy Wheeler</Name>  
        <Street>7890 Broadway</Street>  
        <City>Columbus</City>  
        <State>OH</State>  
        <PostalCode>46290</PostalCode>  
    </Address>  
    <Address Type="BillTo">  
        <Name>Wendy Wheeler</Name>  
        <Street>7890 Broadway</Street>  
        <City>Columbus</City>  
        <State>OH</State>  
        <PostalCode>46290</PostalCode>  
    </Address>  
</ns0:Root>  
```  
  
 <span data-ttu-id="52b2d-108">`The following figure shows a map using the`  **資料表****迴圈**`functoid and`**資料表****抽選程式**   `functoids to generate the desired output instance message.`</span><span class="sxs-lookup"><span data-stu-id="52b2d-108">`The following figure shows a map using the`  **Table** **Looping**  `functoid and`  **Table** **Extractor**  `functoids to generate the desired output instance message.`</span></span>  
  
 <span data-ttu-id="52b2d-109">![對應表格迴圈和表格擷取程式運算質](../core/media/tableloopingextractorfunctoid.gif "tableloopingextractorfunctoid")</span><span class="sxs-lookup"><span data-stu-id="52b2d-109">![Map the Table Looping and Table Extractor functoid](../core/media/tableloopingextractorfunctoid.gif "tableloopingextractorfunctoid")</span></span>  
<span data-ttu-id="52b2d-110">表格迴圈和擷取程式運算質</span><span class="sxs-lookup"><span data-stu-id="52b2d-110">TableLooping and Extractor Functoids</span></span>  
  
 <span data-ttu-id="52b2d-111">請注意，**表格迴圈**輸入和輸出結構描述中的記錄層級項目運算質的連結。</span><span class="sxs-lookup"><span data-stu-id="52b2d-111">Notice that the **Table Looping** functoid links to the record-level element in both the input and output schemas.</span></span> <span data-ttu-id="52b2d-112">該連結可確保封入結構的建立，並因而在記錄內建立項目。</span><span class="sxs-lookup"><span data-stu-id="52b2d-112">The link ensures the creation of the enclosing structure and, thus, the creation of the elements within the record.</span></span> <span data-ttu-id="52b2d-113">也請注意，有一個**表格抽選程式**運算質的輸出結構描述中的每個欄位。</span><span class="sxs-lookup"><span data-stu-id="52b2d-113">Also notice that there is one **Table Extractor** functoid for each field in the output schema.</span></span>  
  
 <span data-ttu-id="52b2d-114">輸入結構描述中的記錄連結是中的第一個參數**設定\<運算質 > 運算質** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="52b2d-114">The link to the record in the input schema is the first parameter in the **Configure \<Functoid> Functoid**dialog box.</span></span>  
  
 <span data-ttu-id="52b2d-115">第二個參數是運算質之格線資料表中的資料行數目： 各一個資料行地址類型、 名稱、 街道、 縣 （市）、 狀態和郵遞區號。</span><span class="sxs-lookup"><span data-stu-id="52b2d-115">The second parameter is the number of columns in the grid table of the functoid: one column each for the address type, name, street, city, state, and postal code.</span></span> <span data-ttu-id="52b2d-116">而在第二個參數後面的是可能出現在格線資料表中的所有值清單。</span><span class="sxs-lookup"><span data-stu-id="52b2d-116">Following the second parameter is a list of all of the values that may appear in the grid table.</span></span> <span data-ttu-id="52b2d-117">這些包含地址類型 ("ShipTo"、"BillTo") 的字串常數，以及地址欄位的連結。</span><span class="sxs-lookup"><span data-stu-id="52b2d-117">These include string constants for the address type ("ShipTo", "BillTo"), as well as links to the fields of the address.</span></span> <span data-ttu-id="52b2d-118">請注意，地址欄位的連結會具有名稱。</span><span class="sxs-lookup"><span data-stu-id="52b2d-118">Notice that the links to the address fields have names.</span></span> <span data-ttu-id="52b2d-119">命名對應中的連結可以簡化資料表的建構。</span><span class="sxs-lookup"><span data-stu-id="52b2d-119">Naming the links in the map simplifies constructing the table.</span></span> <span data-ttu-id="52b2d-120">否則，完整路徑會出現在**設定表格迴圈運算質** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="52b2d-120">Otherwise, full paths appear in the **Configure Table Looping Functoid** dialog box.</span></span>  
  
 <span data-ttu-id="52b2d-121">設定之後**表格迴圈**運算質，您可以建構資料表使用**設定表格迴圈運算質** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="52b2d-121">After you have configured the **Table Looping** functoid, you can construct the table using the **Configure Table Looping Functoid** dialog box.</span></span> <span data-ttu-id="52b2d-122">[] 對話方塊出現時按一下省略符號 (**...**) 相關聯的按鈕**表格迴圈格線**屬性**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="52b2d-122">The dialog appears when you click the ellipsis (**…**) button associated with the **Table Looping Grid** property in the **Properties** window.</span></span>  
  
 <span data-ttu-id="52b2d-123">請注意，有六個資料行中所指定**設定表格迴圈運算質**對話方塊： 輸出結構描述中每個欄位的一個資料行。</span><span class="sxs-lookup"><span data-stu-id="52b2d-123">Notice that there are six columns as specified in the **Configure Table Looping Functoid** dialog: one column for each field in the output schema.</span></span> <span data-ttu-id="52b2d-124">下拉式清單會顯示可能的值中的第三個以及下列參數所指定的欄位中，為**設定表格迴圈運算質**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="52b2d-124">The dropdown shows the possible values for a field, also as specified by the third and following parameters in the **Configure Table Looping Functoid** dialog.</span></span> <span data-ttu-id="52b2d-125">資料表具有兩個資料列，且在輸出結構描述中的每個記錄類型都會一個資料列。</span><span class="sxs-lookup"><span data-stu-id="52b2d-125">The table has two rows, one for each type of record in the output schema.</span></span> <span data-ttu-id="52b2d-126">因為有兩個資料列，所以此對應會為每個輸入記錄產生兩個記錄。</span><span class="sxs-lookup"><span data-stu-id="52b2d-126">Because there are two rows, this map produces two records for every input record.</span></span> <span data-ttu-id="52b2d-127">如果有四個資料列，則每個輸入記錄都會有四個輸出記錄。</span><span class="sxs-lookup"><span data-stu-id="52b2d-127">If there were four rows, there would be four output records for each input record.</span></span>  
  
 <span data-ttu-id="52b2d-128">做為**表格迴圈**運算質採用每一筆記錄時，會從記錄中，值的資料表中填入並再一次將一個資料列傳**表格抽選程式**運算質。</span><span class="sxs-lookup"><span data-stu-id="52b2d-128">As the **Table Looping** functoid takes each record, it fills in the table with the values from the record, and then sends one row at a time to the **Table Extractor** functoids.</span></span> <span data-ttu-id="52b2d-129">**表格抽選程式**運算質每個資料表資料列中擷取一個值，並將它傳遞至輸出執行個體訊息中的連結欄位。</span><span class="sxs-lookup"><span data-stu-id="52b2d-129">The **Table Extractor** functoids each extract one value from the table row and pass it on to the linked field in the output instance message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52b2d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52b2d-130">See Also</span></span>  
 <span data-ttu-id="52b2d-131">[表格迴圈運算質](../core/table-looping-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="52b2d-131">[Table Looping Functoid](../core/table-looping-functoid.md) </span></span>  
 <span data-ttu-id="52b2d-132">[表格抽選程式運算質](../core/table-extractor-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="52b2d-132">[Table Extractor Functoid](../core/table-extractor-functoid.md) </span></span>  
 <span data-ttu-id="52b2d-133">[表格驅動迴圈組態](../core/table-driven-looping-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="52b2d-133">[Table-Driven Looping Configuration](../core/table-driven-looping-configuration.md) </span></span>  
 <span data-ttu-id="52b2d-134">[如何新增表格迴圈和表格擷取程式運算質至對應](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="52b2d-134">[How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="52b2d-135">[進階運算質](../core/advanced-functoids.md) </span><span class="sxs-lookup"><span data-stu-id="52b2d-135">[Advanced Functoids](../core/advanced-functoids.md) </span></span>  
 <span data-ttu-id="52b2d-136">[索引運算質](../core/index-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="52b2d-136">[Index Functoid](../core/index-functoid.md) </span></span>  
 <span data-ttu-id="52b2d-137">[反覆項目運算質](../core/iteration-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="52b2d-137">[Iteration Functoid](../core/iteration-functoid.md) </span></span>  
 <span data-ttu-id="52b2d-138">[迴圈運算質](../core/looping-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="52b2d-138">[Looping Functoid](../core/looping-functoid.md) </span></span>  
 [<span data-ttu-id="52b2d-139">記錄計數運算質</span><span class="sxs-lookup"><span data-stu-id="52b2d-139">Record Count Functoid</span></span>](../core/record-count-functoid.md)