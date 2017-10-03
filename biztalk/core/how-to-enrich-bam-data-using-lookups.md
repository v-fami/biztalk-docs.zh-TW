---
title: "如何修飾 BAM 資料使用查閱 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: BAM, data lookups
ms.assetid: 8d10659e-97d6-4cd1-9b4d-307afd43c763
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43b42b42158bc3b3c179d624340a97a890072a17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enrich-bam-data-using-lookups"></a><span data-ttu-id="262d4-102">如何利用查閱修飾 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="262d4-102">How to Enrich BAM Data Using Lookups</span></span>
<span data-ttu-id="262d4-103">有時候，作業期間所提供的資料不盡然包含報表所需的一切。</span><span class="sxs-lookup"><span data-stu-id="262d4-103">There are cases in which the data that is available at operation time does not contain everything you need for reporting purposes.</span></span> <span data-ttu-id="262d4-104">例如，執行階段可能只提供 ProductID (產品識別碼) 卻沒有 ProductName (產品名稱)。</span><span class="sxs-lookup"><span data-stu-id="262d4-104">For example, you may have a ProductID but not a ProductName at runtime.</span></span> <span data-ttu-id="262d4-105">由於 BAM 活動代表的是與資料實際收集方式無關的抽象概念，活動理應如同報表最終呈現的資料也包含 "ProductName" 項目。</span><span class="sxs-lookup"><span data-stu-id="262d4-105">Since the BAM Activity represents an abstraction independent of how the data is actually collected, it should contain an item named as the final data that you want to see in the report "ProductName".</span></span> <span data-ttu-id="262d4-106">就像任何其他項目，您可以將此項目納入里程碑群組、持續時間、維度和量值等說明性質的概念中。</span><span class="sxs-lookup"><span data-stu-id="262d4-106">Just like any other item, you can use this in interpretive constructs such as milestone groups, durations, dimensions, and measures.</span></span> <span data-ttu-id="262d4-107">由於執行階段並未提供 ProductName，您必須額外取得足以執行查閱的若干資料，例如 ProductID。</span><span class="sxs-lookup"><span data-stu-id="262d4-107">Since the ProductName is not available at runtime, you must get some additional data that is sufficient for performing a lookup, such as the ProductID.</span></span>  
  
 <span data-ttu-id="262d4-108">您應該收集同一個資料行的資料，而非報表實際需要的資料。</span><span class="sxs-lookup"><span data-stu-id="262d4-108">You should collect the data in the same column, instead of the data that you need for reports.</span></span> <span data-ttu-id="262d4-109">例如，在執行階段應該收集 ProductID 而非 ProductName。</span><span class="sxs-lookup"><span data-stu-id="262d4-109">For example, you should collect the ProductID instead of ProductName at runtime.</span></span> <span data-ttu-id="262d4-110">如果還需要其他資料行，請在活動中建立其他項目，但切勿在任何檢視上使用這些項目。</span><span class="sxs-lookup"><span data-stu-id="262d4-110">If more columns are required, you may create more items in the activity but not use them in any View.</span></span>  
  
### <a name="to-enrich-bam-data-via-lookups"></a><span data-ttu-id="262d4-111">利用查閱修飾 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="262d4-111">To enrich BAM data via lookups</span></span>  
  
1.  <span data-ttu-id="262d4-112">部署 BAM 定義。</span><span class="sxs-lookup"><span data-stu-id="262d4-112">Deploy your BAM definition.</span></span>  
  
2.  <span data-ttu-id="262d4-113">在 SQL Server Management Studio 中，新增含有所需資料的伺服器做為遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="262d4-113">In SQL Server Management Studio, add the server that contains the data of interest as a remote server.</span></span>  
  
3.  <span data-ttu-id="262d4-114">找到名為 BAM_AN_`<View Name>` 的資料分析封裝。</span><span class="sxs-lookup"><span data-stu-id="262d4-114">Locate the data analysis package named BAM_AN_`<View Name>`.</span></span> <span data-ttu-id="262d4-115">以 SalesMgr 檢視為例，封裝的名稱即為 BAM_AN_SalesMgr。</span><span class="sxs-lookup"><span data-stu-id="262d4-115">For example if the view is SalesMgr, this will be BAM_AN_SalesMgr.</span></span>  
  
4.  <span data-ttu-id="262d4-116">設定顯示比例，將封裝的檢視放大 (譬如 100%)。</span><span class="sxs-lookup"><span data-stu-id="262d4-116">Set the zoom to magnify the view of the package (e.g. 100%)</span></span>  
  
5.  <span data-ttu-id="262d4-117">新增要在查閱中使用的 SQL 連線。</span><span class="sxs-lookup"><span data-stu-id="262d4-117">Add a SQL connection that you will be using in the lookups.</span></span>  
  
6.  <span data-ttu-id="262d4-118">找到位於「清理階段」步驟之後的轉換資料工作。</span><span class="sxs-lookup"><span data-stu-id="262d4-118">Locate the transform data task after the step "Cleanup Staging".</span></span> <span data-ttu-id="262d4-119">此處代表將資料從 PrimaryImport 移到 StarSchema 資料庫。</span><span class="sxs-lookup"><span data-stu-id="262d4-119">This is where you move the data from the PrimaryImport to the StarSchema database.</span></span> <span data-ttu-id="262d4-120">有兩個執行個體的這項工作 — 一個適用於已完成的活動，而另一個進行中。</span><span class="sxs-lookup"><span data-stu-id="262d4-120">There are two instances of this task—one for the completed activities, and another for the one that is in progress.</span></span> <span data-ttu-id="262d4-121">請將其餘所有步驟套用至這兩個工作。</span><span class="sxs-lookup"><span data-stu-id="262d4-121">Apply all the rest of the steps to both tasks.</span></span>  
  
7.  <span data-ttu-id="262d4-122">按一下轉換。</span><span class="sxs-lookup"><span data-stu-id="262d4-122">Click the transformation.</span></span>  
  
8.  <span data-ttu-id="262d4-123">選取 [查閱]；使用查閱連接新增 "LookupProductByID" 查閱 (請參閱《SQL 線上叢書》以瞭解何謂查閱)。</span><span class="sxs-lookup"><span data-stu-id="262d4-123">Select Lookups; add your lookup "LookupProductByID" using the lookup connection (see SQL books online for lookups).</span></span> <span data-ttu-id="262d4-124">例如，如果查閱是只含有 ProductID 和 ProductName 資料行的 "LookupProduct" 資料表，查閱的文字即為：</span><span class="sxs-lookup"><span data-stu-id="262d4-124">If for example the lookup is a simple table "LookupProduct", the with columns ProductID and ProductName, the text of the lookup will be:</span></span>  
  
    ```  
    SELECT ProductName  
    FROM   LookupProduct  
    WHERE ProductID=?  
    ```  
  
9. <span data-ttu-id="262d4-125">按一下 [轉換] 索引標籤。刪除預設的資料轉換 "Transform"，再另外建立 ActiveX 轉換。</span><span class="sxs-lookup"><span data-stu-id="262d4-125">Click the Transformations tab. Delete the default data transformation "Transform", and create ActiveX transformation instead.</span></span> <span data-ttu-id="262d4-126">按一下 [來源資料行]，然後加入所有的資料行。</span><span class="sxs-lookup"><span data-stu-id="262d4-126">Click Source Columns and add all columns.</span></span> <span data-ttu-id="262d4-127">按一下 [目的地資料行]，然後加入所有的資料行。</span><span class="sxs-lookup"><span data-stu-id="262d4-127">Click Destination Columns and add all columns.</span></span>  
  
10. <span data-ttu-id="262d4-128">按一下 [一般] 索引標籤，再按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="262d4-128">Click the General tab, and then Properties.</span></span> <span data-ttu-id="262d4-129">這樣就會自動產生執行一般複製轉換的指令碼，如下所示：</span><span class="sxs-lookup"><span data-stu-id="262d4-129">This results in automatic generation of a script that performs the trivial copy transformation as shown:</span></span>  
  
    ```  
    Function Main()  
       ...  
       DTSDestination("ProductName") = DTSSource("ProductName")  
       ...  
       Main = DTSTransformStat_OK  
    End Function  
    ```  
  
11. <span data-ttu-id="262d4-130">依照下列方式，使用查閱變更其值：</span><span class="sxs-lookup"><span data-stu-id="262d4-130">Change the value by using the lookup as shown:</span></span>  
  
    ```  
    Function Main()  
       ...  
       DTSDestination("Product")= _  
                      DTSLookups( "LookupProductByID" ).Execute(  _                                  DTSSource("Product"))  
       ...  
       Main = DTSTransformStat_OK  
    End Function  
    ```  
  
12. <span data-ttu-id="262d4-131">儲存後執行封裝。</span><span class="sxs-lookup"><span data-stu-id="262d4-131">Save and then run the package.</span></span>  
  
13. <span data-ttu-id="262d4-132">確定最終的 OLAP Cube 包含正確的資料。</span><span class="sxs-lookup"><span data-stu-id="262d4-132">Ensure that the correct data ends up in the OLAP cube.</span></span> <span data-ttu-id="262d4-133">請將封裝另存為 VBScript 或結構化儲存體檔案，因為封裝中除了 BAM 自動產生的步驟外，還包含您所自訂的程式碼。</span><span class="sxs-lookup"><span data-stu-id="262d4-133">You should save the package as VBScript or a structured storage file, because it contains your custom code, not just the auto-generated steps from BAM.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="262d4-134">查閱僅適用於透過 DTS 和 OLAP 所執行的排程報表。</span><span class="sxs-lookup"><span data-stu-id="262d4-134">The lookup works only for the scheduled reports that you perform with DTS and OLAP.</span></span> <span data-ttu-id="262d4-135">如果您還需要其他資料，而非僅限於即時彙總所收集的資料，則必須先擷取資料再呼叫 BAM API。</span><span class="sxs-lookup"><span data-stu-id="262d4-135">If you need different data than what is collected in the real-time aggregation, then you must retrieve the data before calling the BAM API.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="262d4-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="262d4-136">See Also</span></span>  
 <span data-ttu-id="262d4-137">[使用商務活動監控](../core/using-business-activity-monitoring.md) </span><span class="sxs-lookup"><span data-stu-id="262d4-137">[Using Business Activity Monitoring](../core/using-business-activity-monitoring.md) </span></span>  
 [<span data-ttu-id="262d4-138">部署當地語系化的 BAM XML 檔案</span><span class="sxs-lookup"><span data-stu-id="262d4-138">Deploying Localized BAM XML Files</span></span>](../core/deploying-localized-bam-xml-files.md)