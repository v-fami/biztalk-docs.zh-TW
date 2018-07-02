---
title: 產生執行個體 (EDI) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 362b9803-4d4a-4d17-9ad6-439ec4c7d8aa
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82674b175ad1c408b6ddb9f7823427a550288e96
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999295"
---
# <a name="generating-an-instance-edi"></a><span data-ttu-id="7bd30-102">產生執行個體 (EDI)</span><span class="sxs-lookup"><span data-stu-id="7bd30-102">Generating an Instance (EDI)</span></span>
<span data-ttu-id="7bd30-103">您可以在設計階段從 EDI 結構描述產生訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="7bd30-103">You can generate a message instance from an EDI schema at design time.</span></span> <span data-ttu-id="7bd30-104">若要執行此動作，請在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境中使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 XML 工具延伸模組。</span><span class="sxs-lookup"><span data-stu-id="7bd30-104">To do so, you use the XML Tool extensions to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.</span></span>  
  
 <span data-ttu-id="7bd30-105">您可以產生完整的批次交換 (含交換和群組標頭) 或交易集 (不含交換和群組標頭)。</span><span class="sxs-lookup"><span data-stu-id="7bd30-105">You can generate either a complete batched interchange (with interchange and group headers) or a transaction set (without interchange and group headers).</span></span> <span data-ttu-id="7bd30-106">如果您執行此作業產生完整的交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會產生一個交換標頭、 群組，以針對每個結構描述，與每個群組的三個相同的交易集的檔案，每個結構描述。</span><span class="sxs-lookup"><span data-stu-id="7bd30-106">If you execute the operation to generate a complete interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will generate a file with one interchange header, a group for each schema, and three identical transaction sets per group for each schema.</span></span> <span data-ttu-id="7bd30-107">如果您執行此作業產生交易集，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會產生含有單一交易集的檔案。</span><span class="sxs-lookup"><span data-stu-id="7bd30-107">If you execute the operation to generate a transaction set, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will generate a file with a single transaction set.</span></span>  
  
 <span data-ttu-id="7bd30-108">若要產生完整的批次交換，您可以在批次結構描述上執行 generate-instance 命令。</span><span class="sxs-lookup"><span data-stu-id="7bd30-108">To generate a complete batched interchange, you execute the generate-instance command on the batch schema.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7bd30-109"> 在專案中，會偵測到的訊息結構描述，並會自動包含這些結構描述的交易集。</span><span class="sxs-lookup"><span data-stu-id="7bd30-109"> will detect the message schemas in the project, and will automatically include transaction sets for those schemas.</span></span>  
  
 <span data-ttu-id="7bd30-110">若要產生單一交易集，您可以在訊息結構描述上執行 generate-instance 命令。</span><span class="sxs-lookup"><span data-stu-id="7bd30-110">To generate a single transaction set, you execute the generate-instance command on a message schema.</span></span> <span data-ttu-id="7bd30-111">在此情況下，不需要將批次結構描述加入專案中。</span><span class="sxs-lookup"><span data-stu-id="7bd30-111">In this case, the batch schema does not need to be added to the project.</span></span> <span data-ttu-id="7bd30-112">產生的執行個體將不會包含交換或群組標頭，不過也因此您將需要手動加入它們，EDI 交換才能運作。</span><span class="sxs-lookup"><span data-stu-id="7bd30-112">The generated instance will not include an interchange or group header, however, so you will have to add those manually to have a functional EDI interchange.</span></span>  
  
 <span data-ttu-id="7bd30-113">當您產生執行個體，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]顯示的對話方塊，您可以在其中指定該執行個體，包括分隔符號和語法識別項中使用的組態。</span><span class="sxs-lookup"><span data-stu-id="7bd30-113">When you generate an instance, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] displays a dialog box in which you specify the configuration used in that instance, including separators and the syntax identifier.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7bd30-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="7bd30-114">Prerequisites</span></span>  
 <span data-ttu-id="7bd30-115">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="7bd30-115">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-generate-an-instance-of-a-batched-interchange"></a><span data-ttu-id="7bd30-116">產生批次交換的執行個體</span><span class="sxs-lookup"><span data-stu-id="7bd30-116">To generate an instance of a batched interchange</span></span>  
  
1. <span data-ttu-id="7bd30-117">在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟專案。</span><span class="sxs-lookup"><span data-stu-id="7bd30-117">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open a project.</span></span> <span data-ttu-id="7bd30-118">在 [方案總管] 中，針對您要讓訊息結構描述包含的每一種交易集類型，新增訊息結構描述至專案。</span><span class="sxs-lookup"><span data-stu-id="7bd30-118">Add a message schema to the project in Solution Explorer for each type of transaction set that you want in the message instance.</span></span> <span data-ttu-id="7bd30-119">新增至專案的編碼類型的批次結構描述： Edifact_BatchSchema.xsd 或 X12_BatchSchema.xsd。</span><span class="sxs-lookup"><span data-stu-id="7bd30-119">Add the batch schema for the type of encoding to the project: either Edifact_BatchSchema.xsd or X12_BatchSchema.xsd.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="7bd30-120">批次結構描述位於[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7bd30-120">The batch schemas are located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI folder.</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="7bd30-121">您不必建置專案來產生執行個體。</span><span class="sxs-lookup"><span data-stu-id="7bd30-121">You do not have to build the project to generate an instance.</span></span>  
  
2. <span data-ttu-id="7bd30-122">以滑鼠右鍵按一下方案總管 中的批次結構描述，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="7bd30-122">Right-click the batch schema in Solution Explorer, and then click **Properties**.</span></span>  
  
3. <span data-ttu-id="7bd30-123">在 **屬性**視窗中，將**產生的執行個體輸出類型**來**原生**或**XML**。</span><span class="sxs-lookup"><span data-stu-id="7bd30-123">In the **Properties** window, set **Generate Instance Output Type** to **Native** or **XML**.</span></span> <span data-ttu-id="7bd30-124">選取**原生**將會提示產生副檔名為.txt 的一般檔案。</span><span class="sxs-lookup"><span data-stu-id="7bd30-124">Selecting **Native** will prompt generation of a flat file with a .txt extension.</span></span> <span data-ttu-id="7bd30-125">選取**XML**將會提示產生 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="7bd30-125">Selecting **XML** will prompt generation of an XML file.</span></span>  
  
4. <span data-ttu-id="7bd30-126">針對**輸出執行個體檔案名稱**、 輸入名稱或瀏覽至檔案以及選取的檔案。</span><span class="sxs-lookup"><span data-stu-id="7bd30-126">For **Output Instance Filename**, enter a name or browse to a file and select the file.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="7bd30-127">如果您未針對輸出執行個體名稱輸入值，則會自動選取一個值。</span><span class="sxs-lookup"><span data-stu-id="7bd30-127">If you do not enter a value for the output instance filename, one will be chosen for you.</span></span> <span data-ttu-id="7bd30-128">檔案名稱將會顯示在 [輸出] 視窗的[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7bd30-128">The filename will be displayed in the Output window of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="7bd30-129">如果您選取現有的檔案，則現有檔案的內容將會取代為此作業產生的內容。</span><span class="sxs-lookup"><span data-stu-id="7bd30-129">If you select an existing file, the contents of the existing file will be replaced with the content generated by this operation.</span></span>  
  
5. <span data-ttu-id="7bd30-130">以滑鼠右鍵按一下 批次結構描述，然後按一下**產生的執行個體**。</span><span class="sxs-lookup"><span data-stu-id="7bd30-130">Right-click the batch schema and then click **Generate Instance**.</span></span>  
  
6. <span data-ttu-id="7bd30-131">在  **EDI 執行個體屬性**對話方塊中，選取分隔符號、 識別碼和其他設定選項以用於該執行個體，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="7bd30-131">In the **EDI Instance Properties** dialog box, select the separators, identifiers, and other configuration options to be used in that instance, and then click **OK**.</span></span>  
  
7. <span data-ttu-id="7bd30-132">確認作業從事**輸出**視窗。</span><span class="sxs-lookup"><span data-stu-id="7bd30-132">Verify that the operation worked in the **Output** window.</span></span>  
  
8. <span data-ttu-id="7bd30-133">若要檢視檔案，請按**控制**，然後按一下在連結**輸出**視窗。</span><span class="sxs-lookup"><span data-stu-id="7bd30-133">To view the file, press **Control** and click the link in the **Output** window.</span></span> [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="7bd30-134"> 在 [BizTalk 編輯器] 視窗中，將會顯示檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="7bd30-134"> will display the contents of the file in the BizTalk Editor window.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="7bd30-135">產生時包含 837I、 837 D 或 837p 的執行個體，GS08 的值會不正確地設定為 00401。</span><span class="sxs-lookup"><span data-stu-id="7bd30-135">When generating an instance that contains an 837I, 837D, or 837P, the value of GS08 will be incorrectly set to 00401.</span></span> <span data-ttu-id="7bd30-136">如需詳細資訊，請參閱 <<c0> [ 已知問題與 EDI 解決方案的 XML 工具搭配](../core/known-issues-with-xml-tools-used-with-edi-solutions.md)。</span><span class="sxs-lookup"><span data-stu-id="7bd30-136">For more information, see [Known Issues with XML Tools Used with EDI Solutions](../core/known-issues-with-xml-tools-used-with-edi-solutions.md).</span></span>  
  
### <a name="to-generate-an-instance-of-a-transaction-set"></a><span data-ttu-id="7bd30-137">產生交易集執行個體</span><span class="sxs-lookup"><span data-stu-id="7bd30-137">To generate an instance of a transaction set</span></span>  
  
1. <span data-ttu-id="7bd30-138">在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟專案。</span><span class="sxs-lookup"><span data-stu-id="7bd30-138">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open a project.</span></span> <span data-ttu-id="7bd30-139">針對要產生其執行個體的交易集類型新增結構描述。</span><span class="sxs-lookup"><span data-stu-id="7bd30-139">Add the schema for the type of transaction set that you want to generate an instance for.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="7bd30-140">您不必新增批次結構描述至專案，以產生交易集的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7bd30-140">You do not have to add the batch schema to the project to generate an instance of a transaction set.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="7bd30-141">您不必建置專案來產生執行個體。</span><span class="sxs-lookup"><span data-stu-id="7bd30-141">You do not have to build the project to generate an instance.</span></span>  
  
2. <span data-ttu-id="7bd30-142">以滑鼠右鍵按一下方案總管 中的訊息結構描述，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="7bd30-142">Right-click the message schema in Solution Explorer, and then click **Properties**.</span></span>  
  
3. <span data-ttu-id="7bd30-143">在 [屬性] 視窗中，設定**產生的執行個體輸出類型**要**原生**或是**XML**。</span><span class="sxs-lookup"><span data-stu-id="7bd30-143">In the Properties window, set **Generate Instance Output Type** to **Native** or **XML**.</span></span> <span data-ttu-id="7bd30-144">選取**原生**將會提示產生副檔名為.txt 的一般檔案。</span><span class="sxs-lookup"><span data-stu-id="7bd30-144">Selecting **Native** will prompt generation of a flat file with a .txt extension.</span></span> <span data-ttu-id="7bd30-145">選取**XML**將會提示產生 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="7bd30-145">Selecting **XML** will prompt generation of an XML file.</span></span>  
  
4. <span data-ttu-id="7bd30-146">針對**輸出執行個體檔案名稱**、 輸入名稱或瀏覽至檔案以及選取的檔案。</span><span class="sxs-lookup"><span data-stu-id="7bd30-146">For **Output Instance Filename**, enter a name or browse to a file and select the file.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="7bd30-147">如果您未針對輸出執行個體名稱輸入值，則會自動選取一個值。</span><span class="sxs-lookup"><span data-stu-id="7bd30-147">If you do not enter a value for the output instance filename, one will be chosen for you.</span></span> <span data-ttu-id="7bd30-148">檔案名稱將會顯示在**輸出**窗口[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7bd30-148">The filename will be displayed in the **Output** window of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="7bd30-149">如果您選取現有的檔案，則現有檔案的內容將會取代為此作業產生的內容。</span><span class="sxs-lookup"><span data-stu-id="7bd30-149">If you select an existing file, the contents of the existing file will be replaced with the content generated by this operation.</span></span>  
  
5. <span data-ttu-id="7bd30-150">以滑鼠右鍵按一下訊息結構描述，然後按一下**產生的執行個體**。</span><span class="sxs-lookup"><span data-stu-id="7bd30-150">Right-click the message schema and then click **Generate Instance**.</span></span>  
  
6. <span data-ttu-id="7bd30-151">在  **EDI 執行個體屬性**對話方塊中選取的組態選項，您想要，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="7bd30-151">In the **EDI Instance Properties** dialog box, select the configuration options that you want, and then click **OK**.</span></span>  
  
7. <span data-ttu-id="7bd30-152">確認中的訊息**輸出**指出作業成功的視窗。</span><span class="sxs-lookup"><span data-stu-id="7bd30-152">Verify that there is a message in the **Output** window indicating that the operation succeeded.</span></span>  
  
8. <span data-ttu-id="7bd30-153">若要檢視檔案，請按**控制**並按一下 [輸出] 視窗中的連結。</span><span class="sxs-lookup"><span data-stu-id="7bd30-153">To view the file, press **Control** and click the link in the Output window.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7bd30-154"> 在 [BizTalk 編輯器] 視窗中，將會顯示檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="7bd30-154"> will display the contents of the file in the BizTalk Editor window.</span></span>  
  
9. <span data-ttu-id="7bd30-155">若要讓 EDI 訊息運作，請在文字編輯器中新增交換和群組標頭至訊息。</span><span class="sxs-lookup"><span data-stu-id="7bd30-155">To make a functional EDI message, add the interchange and group headers to the message in a text editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bd30-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bd30-156">See Also</span></span>  
 <span data-ttu-id="7bd30-157">[使用設計階段 XML 工具](../core/using-design-time-xml-tools.md) </span><span class="sxs-lookup"><span data-stu-id="7bd30-157">[Using Design-Time XML Tools](../core/using-design-time-xml-tools.md) </span></span>  
 [<span data-ttu-id="7bd30-158">驗證執行個體 (EDI)</span><span class="sxs-lookup"><span data-stu-id="7bd30-158">Validating an Instance (EDI)</span></span>](../core/validating-an-instance-edi.md)