---
title: 驗證執行個體 (EDI) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0fe4e87-5ab4-41e4-8ceb-8f6cf40cae0b
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cceea8afe67f7e69b3ee842198d9a5373a972d04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288910"
---
# <a name="validating-an-instance-edi"></a><span data-ttu-id="6ba16-102">驗證執行個體 (EDI)</span><span class="sxs-lookup"><span data-stu-id="6ba16-102">Validating an Instance (EDI)</span></span>
<span data-ttu-id="6ba16-103">執行個體可以在設計階段時依據其 EDI 結構描述加以驗證。</span><span class="sxs-lookup"><span data-stu-id="6ba16-103">You can validate an instance against its EDI schema at design time.</span></span> <span data-ttu-id="6ba16-104">若要執行此動作，請在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境中使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 XML 工具延伸模組。</span><span class="sxs-lookup"><span data-stu-id="6ba16-104">To do so, you use the XML Tool extensions to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.</span></span> <span data-ttu-id="6ba16-105">進行驗證的執行個體可以是單一交易集 (不含交換和群組標頭)、包含單一交易集的交換 (含交換和群組標頭)，或是包含多個交易集的完整批次交換 (含交換和群組標頭)。</span><span class="sxs-lookup"><span data-stu-id="6ba16-105">The instance that you validate can be a single transaction set (without interchange and group headers), an interchange with a single transaction set (with interchange and group headers), or a complete batched interchange with multiple transaction sets (with interchange and group headers).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ba16-106">不支援 XML 保留交換的驗證作業，</span><span class="sxs-lookup"><span data-stu-id="6ba16-106">Validation of an XML preserved interchange is not supported.</span></span> <span data-ttu-id="6ba16-107">但支援 EDI 保留交換的驗證作業。</span><span class="sxs-lookup"><span data-stu-id="6ba16-107">However, validation of an EDI preserved interchange is supported.</span></span>  
  
 <span data-ttu-id="6ba16-108">這項驗證執行個體作業會執行 EDI 和 XSD 驗證。</span><span class="sxs-lookup"><span data-stu-id="6ba16-108">The validate-instance operation performs both EDI and XSD validation.</span></span>  
  
 <span data-ttu-id="6ba16-109">當您在驗證執行個體，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]顯示的對話方塊，您可以在其中指定要驗證該執行個體，包括分隔符號和語法識別項中的組態。</span><span class="sxs-lookup"><span data-stu-id="6ba16-109">When you validate an instance, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] displays a dialog box in which you specify the configuration to be validated in that instance, including separators and the syntax identifier.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6ba16-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="6ba16-110">Prerequisites</span></span>  
 <span data-ttu-id="6ba16-111">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="6ba16-111">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-validate-an-instance-against-its-schema"></a><span data-ttu-id="6ba16-112">若要依據具有的結構描述來驗證執行個體</span><span class="sxs-lookup"><span data-stu-id="6ba16-112">To validate an instance against its schema</span></span>  
  
1.  <span data-ttu-id="6ba16-113">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟專案。</span><span class="sxs-lookup"><span data-stu-id="6ba16-113">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open a project.</span></span>  
  
2.  <span data-ttu-id="6ba16-114">在 [方案總管] 中，將訊息執行個體的所有必要結構描述加入至該專案中。</span><span class="sxs-lookup"><span data-stu-id="6ba16-114">In Solution Explorer, add to the project all schemas required for the message instance.</span></span>  
  
    1.  <span data-ttu-id="6ba16-115">若要驗證不含交換和群組標頭的單一交易集，請加入該交易集的文件結構描述。</span><span class="sxs-lookup"><span data-stu-id="6ba16-115">If you are validating a single transaction set without interchange and group headers, add the document schema for that transaction set.</span></span>  
  
    2.  <span data-ttu-id="6ba16-116">如果您要驗證單一交易集的交換，將加入專案之交易的結構描述以及訊息所使用的編碼類型的批次結構描述 (Edifact_BatchSchema.xsd 或 X12_BatchSchema.xsd 中的[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_\Xsd Schema\EDI)。</span><span class="sxs-lookup"><span data-stu-id="6ba16-116">If you are validating an interchange with a single transaction set, add to the project the schema for the transaction and the batch schema for the type of encoding used for the message (either Edifact_BatchSchema.xsd or X12_BatchSchema.xsd in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI).</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6ba16-117">批次結構描述才能驗證信封執行個體。</span><span class="sxs-lookup"><span data-stu-id="6ba16-117">The batch schema is required to validate the envelope of the instance.</span></span> <span data-ttu-id="6ba16-118">如果您是使用訊息結構描述，則會不會驗證信封。</span><span class="sxs-lookup"><span data-stu-id="6ba16-118">If you were to use only the message schema, the envelope would not be validated.</span></span>  
  
    3.  <span data-ttu-id="6ba16-119">如果您要驗證包含多個交易集的批次的交換，加入至專案的結構描述的每個交易集群組中的訊息執行個體，以及訊息所使用的編碼類型的批次結構描述 (任一 Edifact_BatchSchema.xsd 或在 X12_BatchSchema.xsd [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI)。</span><span class="sxs-lookup"><span data-stu-id="6ba16-119">If you are validating a batched interchange with multiple transaction sets, add to the project the schemas for each transaction set group in the message instance, and the batch schema for the type of encoding used for the message (either Edifact_BatchSchema.xsd or X12_BatchSchema.xsd in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI).</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6ba16-120">如果您有自訂的服務結構描述，這時除了文件 (交易集) 結構描述和可能需要的批次結構描述之外，您還必須將該自訂服務結構描述加入至 BizTalk 專案中。</span><span class="sxs-lookup"><span data-stu-id="6ba16-120">If you have customized the service schema, you will have to include the custom service schema in the BizTalk project, in addition to the document (transaction set) schema(s) and if necessary, the batch schema.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6ba16-121">您不一定要建置專案才能驗證執行個體。</span><span class="sxs-lookup"><span data-stu-id="6ba16-121">You do not have to build the project to validate an instance.</span></span>  
  
3.  <span data-ttu-id="6ba16-122">在 [方案總管] 中，顯示結構描述的屬性頁，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6ba16-122">Display the property page for the schema in Solution Explorer, as follows:</span></span>  
  
    1.  <span data-ttu-id="6ba16-123">如果您要驗證單一交易集，以滑鼠右鍵按一下該交易集，文件結構描述，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6ba16-123">If you are validating a single transaction set, right-click the document schema for that transaction set, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="6ba16-124">如果您要驗證單一交易集的交換或包含多個交易集的批次的交換，批次結構描述 （Edifact_BatchSchema.xsd 或 X12_BatchSchema.xsd 結構描述），以滑鼠右鍵按一下，然後按一下**屬性**.</span><span class="sxs-lookup"><span data-stu-id="6ba16-124">If you are validating an interchange with a single transaction set or a batched interchange with multiple transaction sets, right-click the batch schema (Edifact_BatchSchema.xsd or X12_BatchSchema.xsd schema), and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="6ba16-125">針對結構描述中，[屬性] 視窗中的**輸入執行個體檔案名稱**輸入您要驗證，或瀏覽至檔案、 選取它，然後按一下訊息執行個體的路徑與名稱**確定**。</span><span class="sxs-lookup"><span data-stu-id="6ba16-125">In Properties window for the schema, for **Input Instance Filename** enter the name and path of the message instance that you want to validate, or browse to the file, select it, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="6ba16-126">如**驗證執行個體輸入類型**，輸入要驗證的檔案類型：**原生**EDI 檔案或**XML**的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="6ba16-126">For **Validate Instance Input Type**, enter the type of the file to be validate: **Native** for a EDI file or **XML** for an XML file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6ba16-127">不支援 XML 保留交換的驗證作業，</span><span class="sxs-lookup"><span data-stu-id="6ba16-127">Validation of an XML preserved interchange is not supported.</span></span> <span data-ttu-id="6ba16-128">如果您選取 XML for**驗證執行個體輸入類型**屬性驗證保留的交換時，作業將會失敗，且會傳回任何項目。</span><span class="sxs-lookup"><span data-stu-id="6ba16-128">If you select XML for the **Validate Instance Input Type** property when validating a preserved interchange, the operation will fail and nothing will be returned.</span></span> <span data-ttu-id="6ba16-129">不過，如果您選取**原生**如**驗證執行個體輸入類型**時驗證保留的交換，則作業會成功。</span><span class="sxs-lookup"><span data-stu-id="6ba16-129">However, if you select **Native** for the **Validate Instance Input Type** when validating a preserved interchange, the operation will succeed.</span></span>  
  
6.  <span data-ttu-id="6ba16-130">以滑鼠右鍵按一下訊息結構描述 （Edifact_BatchSchema.xsd 或 X12_BatchSchema.xsd 若驗證單一交易集的交換或批次的交換），然後按一下**驗證執行個體**。</span><span class="sxs-lookup"><span data-stu-id="6ba16-130">Right-click the message schema (Edifact_BatchSchema.xsd or X12_BatchSchema.xsd if validating an interchange with a single transaction set or a batched interchange) and then click **Validate Instance**.</span></span>  
  
7.  <span data-ttu-id="6ba16-131">在**EDI 執行個體屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6ba16-131">In the **EDI Instance Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="6ba16-132">如果您的執行個體應該使用重複分隔符號，請選取**重複分隔符號**。</span><span class="sxs-lookup"><span data-stu-id="6ba16-132">If your instance should use a repetition separator, select **Repetition separator**.</span></span>  
  
    2.  <span data-ttu-id="6ba16-133">如果您的執行個體應該使用尾端分隔符號，請選取**是**如**使用尾端分隔符號**。</span><span class="sxs-lookup"><span data-stu-id="6ba16-133">If your instance should use trailing delimiters, select **Yes** for **Use trailing delimiters**.</span></span>  
  
    3.  <span data-ttu-id="6ba16-134">如果您的執行個體應該使用字元集以外**基本**，選取**擴充**或**Unicode**中**語法識別項**。</span><span class="sxs-lookup"><span data-stu-id="6ba16-134">If your instance should use a character set other than **Basic**, select **Extended** or **Unicode** in **Syntax identifier**.</span></span>  
  
    4.  <span data-ttu-id="6ba16-135">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="6ba16-135">Click **OK**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6ba16-136">**EDI 執行個體屬性**對話方塊可能會出現在您按一下之後的第二次**確定**。</span><span class="sxs-lookup"><span data-stu-id="6ba16-136">The **EDI Instance Properties** dialog box might appear a second time after you have clicked **OK**.</span></span> <span data-ttu-id="6ba16-137">如果是的話，按一下**確定**一次。</span><span class="sxs-lookup"><span data-stu-id="6ba16-137">If so, click **OK** again.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6ba16-138">**EDI 執行個體屬性**對話方塊將會填入已執行的上一個驗證執行個體作業中使用相同的登入的使用者相同的值。</span><span class="sxs-lookup"><span data-stu-id="6ba16-138">The **EDI Instance Properties** dialog box will be populated with the same values used in the last validate-instance operation that was run for the same logged-in user.</span></span>  
  
8.  <span data-ttu-id="6ba16-139">請確認有在訊息**輸出**視窗指出作業成功。</span><span class="sxs-lookup"><span data-stu-id="6ba16-139">Verify that there is a message in the **Output** window indicating that the operation succeeded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ba16-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ba16-140">See Also</span></span>  
 <span data-ttu-id="6ba16-141">[使用設計階段 XML 工具](../core/using-design-time-xml-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6ba16-141">[Using Design-Time XML Tools](../core/using-design-time-xml-tools.md) </span></span>  
 [<span data-ttu-id="6ba16-142">產生執行個體 (EDI)</span><span class="sxs-lookup"><span data-stu-id="6ba16-142">Generating an Instance (EDI)</span></span>](../core/generating-an-instance-edi.md)