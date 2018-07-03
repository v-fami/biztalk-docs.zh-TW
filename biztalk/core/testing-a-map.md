---
title: 測試對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 265afd62-3c1d-4b9a-9f51-176b9b079241
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ad35dd513375f8221ed909fd7f353fc5e6673c7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983935"
---
# <a name="testing-a-map"></a><span data-ttu-id="98ae9-102">測試對應</span><span class="sxs-lookup"><span data-stu-id="98ae9-102">Testing a Map</span></span>
<span data-ttu-id="98ae9-103">您可以在設計階段測試 EDI 專案中的對應。</span><span class="sxs-lookup"><span data-stu-id="98ae9-103">You can test a map in an EDI project at design time.</span></span> <span data-ttu-id="98ae9-104">若要執行此動作，請在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境中使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 XML 工具延伸模組。</span><span class="sxs-lookup"><span data-stu-id="98ae9-104">To do so, you use the XML Tool extensions to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.</span></span> <span data-ttu-id="98ae9-105">本主題描述如何設定和使用**測試對應**XML 工具延伸模組的功能。</span><span class="sxs-lookup"><span data-stu-id="98ae9-105">This topic describes how to set up and use the **Test Map** feature of the XML Tool extension.</span></span>  
  
 <span data-ttu-id="98ae9-106">您可透過指定來源文件和指定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將儲存所產生執行個體 (與虛構資料) 的資料夾來測試對應。</span><span class="sxs-lookup"><span data-stu-id="98ae9-106">You test a map by specifying a source document and specifying a folder where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will save a generated instance (with fictitious data).</span></span> <span data-ttu-id="98ae9-107">您必須設定分隔符號，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將用以處理來源文件，並產生目的文件，以根據 EDI 結構描述。</span><span class="sxs-lookup"><span data-stu-id="98ae9-107">You need to set the delimiters that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to process the source document and generate the destination document according to EDI schemas.</span></span> <span data-ttu-id="98ae9-108">這適用於所有值**TestMap**輸入對應的屬性頁中的屬性：**產生的執行個體**， **XML**，或**原生**。</span><span class="sxs-lookup"><span data-stu-id="98ae9-108">This is true for all values of the **TestMap** input property in the map's property pages: **Generate Instance**, **XML**, or **Native**.</span></span> <span data-ttu-id="98ae9-109">它適用於**產生的執行個體**因為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]必須知道要用來產生執行個體的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="98ae9-109">It is true for **Generate Instance** because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] needs to know what delimiters to use to generate the instance.</span></span> <span data-ttu-id="98ae9-110">它適用於**XML**或是**原生**因為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]必須知道如何解譯原生的一般檔案或 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="98ae9-110">It is true for **XML** or **Native** because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] needs to know how to interpret the native flat file or the XML file.</span></span> <span data-ttu-id="98ae9-111">您也需要設定的分隔符號，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會使用產生的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="98ae9-111">You also need to set the delimiters that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use when generating the output file.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="98ae9-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="98ae9-112">Prerequisites</span></span>  
 <span data-ttu-id="98ae9-113">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="98ae9-113">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-test-a-map"></a><span data-ttu-id="98ae9-114">測試對應</span><span class="sxs-lookup"><span data-stu-id="98ae9-114">To test a map</span></span>  
  
1. <span data-ttu-id="98ae9-115">在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]、 新增您想要加入專案中，測試對應及對應的來源和目的地結構描述加入專案。</span><span class="sxs-lookup"><span data-stu-id="98ae9-115">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], add the map that you want to test to a project, and add the source and destination schemas for that map to the project.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="98ae9-116">您不必建置專案來測試對應。</span><span class="sxs-lookup"><span data-stu-id="98ae9-116">You do not have to build the project to test the map.</span></span>  
  
2. <span data-ttu-id="98ae9-117">以滑鼠右鍵按一下地圖，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="98ae9-117">Right-click the map and click **Properties**.</span></span>  
  
3. <span data-ttu-id="98ae9-118">在 **屬性**視窗中，將**驗證 TestMap 輸入**來 **，則為 True**如果您想要驗證輸入的檔，針對來源結構描述。</span><span class="sxs-lookup"><span data-stu-id="98ae9-118">In the **Properties** window, set **Validate TestMap Input** to **True** if you want to validate the input file against the source schema.</span></span> <span data-ttu-id="98ae9-119">設定**驗證 TestMap 輸出**要 **，則為 True**如果您想要驗證輸出檔，針對目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="98ae9-119">Set **Validate TestMap Output** to **True** if you want to validate the output file against the destination schema.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="98ae9-120">如果您在測試對應與**TestMap 輸入**屬性設定為**原生**並**驗證 TestMap 輸入**並**驗證 TestMap 輸出**屬性設定為**False**，仍然會進行驗證。</span><span class="sxs-lookup"><span data-stu-id="98ae9-120">If you test a map with the **TestMap Input** property set to **Native** and the **Validate TestMap Input** and **Validate TestMap Output** properties set to **False**, validation will still be performed.</span></span> <span data-ttu-id="98ae9-121">這是因為原生格式的輸入的檔案將轉換成 XML 格式，和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會針對驗證 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="98ae9-121">This occurs because the native-formatted input file will be converted into XML format, and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will validate the XML against the schema.</span></span> <span data-ttu-id="98ae9-122">如果輸入的執行個體中有驗證問題，請驗證機制仍然會公佈錯誤，即使**驗證 TestMap 輸入**並**驗證 TestMap 輸出**屬性會設為 **，則為 false**。</span><span class="sxs-lookup"><span data-stu-id="98ae9-122">If there are validation issues in the input instance, the validation mechanism will post errors, even though the **Validate TestMap Input** and **Validate TestMap Output** properties are set to **False**.</span></span>  
  
4. <span data-ttu-id="98ae9-123">設定**TestMap 輸入**要**原生**為副檔名為.edi 的輸入檔。</span><span class="sxs-lookup"><span data-stu-id="98ae9-123">Set **TestMap Input** to **Native** for an input file that has an .edi extension.</span></span> <span data-ttu-id="98ae9-124">將它設定為**XML**如果它具有.xml 副檔名。</span><span class="sxs-lookup"><span data-stu-id="98ae9-124">Set it to **XML** if it has an .xml extension.</span></span> <span data-ttu-id="98ae9-125">設定**TestMap 輸入**要**產生的執行個體**有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]產生輸入執行個體，而不是您以手動方式指定輸入執行個體。</span><span class="sxs-lookup"><span data-stu-id="98ae9-125">Set **TestMap Input** to **Generate Instance** to have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generate an input instance, rather than you designating an input instance manually.</span></span>  
  
5. <span data-ttu-id="98ae9-126">設定**TestMap Output**要**原生**的副檔名為.edi 的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="98ae9-126">Set **TestMap Output** to **Native** for an output file that has an .edi extension.</span></span> <span data-ttu-id="98ae9-127">將它設定為**XML**如果它具有.xml 副檔名。</span><span class="sxs-lookup"><span data-stu-id="98ae9-127">Set it to **XML** if it has an .xml extension.</span></span>  
  
6. <span data-ttu-id="98ae9-128">針對**TestMap Input Instance**，瀏覽至您想要用來測試對應，請選取它，輸入執行個體，然後**開啟**。</span><span class="sxs-lookup"><span data-stu-id="98ae9-128">For **TestMap Input Instance**, browse to the input instance that you want to be used to test the map, select it, and then **Open**.</span></span> <span data-ttu-id="98ae9-129">如果您想要將此屬性保留空白，將**TestMap 輸入**要**產生的執行個體**。</span><span class="sxs-lookup"><span data-stu-id="98ae9-129">If you want to leave this property blank, set **TestMap Input** to **Generate Instance**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="98ae9-130">您不必指定輸入執行個體**TestMap Input Instance**或設定**TestMap 輸入**來**產生執行個體**。</span><span class="sxs-lookup"><span data-stu-id="98ae9-130">You have to either designate an input instance for **TestMap Input Instance** or set **TestMap Input** to **Generate Instance**.</span></span> <span data-ttu-id="98ae9-131">如果沒有，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="98ae9-131">If not, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will generate an error.</span></span>  
  
7. <span data-ttu-id="98ae9-132">針對**TestMap 輸出執行個體**，瀏覽至您想要儲存輸出執行個體，輸入輸出執行個體的名稱，然後按一下位置**儲存**。</span><span class="sxs-lookup"><span data-stu-id="98ae9-132">For **TestMap Output Instance**, browse to the location you want to save the output instance at, enter a name for the output instance, and then click **Save**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="98ae9-133">如果您未指定輸出執行個體，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將會建立輸出檔、 將輸出檔案放入資料夾，並指出檔案名稱和路徑。</span><span class="sxs-lookup"><span data-stu-id="98ae9-133">If you do not designate an output instance, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will create an output file, place the output file into a folder, and indicate the file name and path.</span></span>  
  
8. <span data-ttu-id="98ae9-134">以滑鼠右鍵按一下您要測試，然後再按一下的地圖**測試對應**。</span><span class="sxs-lookup"><span data-stu-id="98ae9-134">Right-click the map you are testing, and then click **Test Map**.</span></span>  
  
9. <span data-ttu-id="98ae9-135">在 X12 **EDI 執行個體屬性**對話方塊方塊中，請確定所有屬性都是一致的輸入和輸出執行個體的設定。</span><span class="sxs-lookup"><span data-stu-id="98ae9-135">In the X12 **EDI Instance Properties** dialog box, make sure that all properties are consistent with the settings for the input and output instances.</span></span>  
  
   > [!NOTE]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="98ae9-136"> 將會顯示**EDI 執行個體屬性**對話方塊在 TestMap 處理期間，兩次： 一次解譯輸入的訊息執行個體，一次產生輸出訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="98ae9-136"> will display the **EDI Instance Properties** dialog box twice during the TestMap process: once for interpreting the input message instance and once for generating the output message instance.</span></span> <span data-ttu-id="98ae9-137">不過，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可能會顯示對話方塊兩次以上，而且可以顯示對話方塊中，針對非 EDI 結構描述。</span><span class="sxs-lookup"><span data-stu-id="98ae9-137">However, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] may display the dialog box more than just twice and may display the dialog box for non-EDI schema.</span></span> <span data-ttu-id="98ae9-138">如果是的話，按一下**確定**以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="98ae9-138">If so, click **OK** to close the dialog box.</span></span>  
  
10. <span data-ttu-id="98ae9-139">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="98ae9-139">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98ae9-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98ae9-140">See Also</span></span>  
 [<span data-ttu-id="98ae9-141">使用設計階段 XML 工具</span><span class="sxs-lookup"><span data-stu-id="98ae9-141">Using Design-Time XML Tools</span></span>](../core/using-design-time-xml-tools.md)