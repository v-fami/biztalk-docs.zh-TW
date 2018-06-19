---
title: 加入專案項目 |Microsoft 文件
description: 在 Visual Studio 中對 BizTalk Server 專案中加入協調流程、 結構描述、 對應和管線
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1b922d5-8ece-4e1a-a390-e6ae1222665a
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef998865a1851e546a3648b60e0141b3cd137c1b
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
ms.locfileid: "29710221"
---
# <a name="add-project-items"></a><span data-ttu-id="88d25-103">加入專案項目</span><span class="sxs-lookup"><span data-stu-id="88d25-103">Add Project Items</span></span>
<span data-ttu-id="88d25-104">在 BizTalk 專案系統的內容中，專案項目是設定的項目 (例如對應或結構描述)。</span><span class="sxs-lookup"><span data-stu-id="88d25-104">In the context of the BizTalk project system, a project item is a configured item, such as a map or schema.</span></span> <span data-ttu-id="88d25-105">BizTalk 應用程式包含一或多個協調流程、結構描述、對應及管線。</span><span class="sxs-lookup"><span data-stu-id="88d25-105">A BizTalk application might contain one or more orchestrations, schemas, maps, and pipelines.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88d25-106">當您將項目新增至專案時，因為句號是 .NET 命名空間的分隔符號，所以請不要在名稱中使用句號 (.)。</span><span class="sxs-lookup"><span data-stu-id="88d25-106">When you add an item to a project, do not use a period (.) in the name because a period is a separator for the .NET namespace.</span></span> <span data-ttu-id="88d25-107">如果您在項目名稱中使用句號，則項目的類型名稱會包含底線 (_)，而非句號。</span><span class="sxs-lookup"><span data-stu-id="88d25-107">If you use a period in the item name, the Type Name of the item will contain an underscore (_) instead of a period.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88d25-108">當將結構描述、 對應或管線新增到資料夾， **完整格式名稱** 屬性自動產生並包含命名空間和型別。</span><span class="sxs-lookup"><span data-stu-id="88d25-108">When you add a schema, map, or pipeline to a folder, the **Fully Qualified Name** property is automatically generated and includes the namespace and type.</span></span>  
  
## <a name="orchestrations"></a><span data-ttu-id="88d25-109">協調流程</span><span class="sxs-lookup"><span data-stu-id="88d25-109">Orchestrations</span></span>  
 <span data-ttu-id="88d25-110">協調流程是一種以 XLANG/s 語言表示商務程序的方法。</span><span class="sxs-lookup"><span data-stu-id="88d25-110">An orchestration is a representation of a business process expressed in the XLANG/s language.</span></span> <span data-ttu-id="88d25-111">XLANG/s 可用來補充現有程序性語言的不足，例如 Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] 與 Microsoft [!INCLUDE[btsVBNet](../includes/btsvbnet-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="88d25-111">XLANG/s can be used to complement existing procedural languages such as Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] and Microsoft [!INCLUDE[btsVBNet](../includes/btsvbnet-md.md)].</span></span>  
  
 <span data-ttu-id="88d25-112">您可以使用協調流程設計師來建立您要併入 BizTalk 專案的協調流程。</span><span class="sxs-lookup"><span data-stu-id="88d25-112">You can use Orchestration Designer to create the orchestrations that you want to include in a BizTalk project.</span></span> <span data-ttu-id="88d25-113">所有您在協調流程設計師中所建立的協調流程都會以 .odx 為副檔名。</span><span class="sxs-lookup"><span data-stu-id="88d25-113">All orchestrations that you create in Orchestration Designer have an .odx file extension.</span></span>  
  
## <a name="schemas"></a><span data-ttu-id="88d25-114">結構描述</span><span class="sxs-lookup"><span data-stu-id="88d25-114">Schemas</span></span>  
 <span data-ttu-id="88d25-115">結構描述是文件或訊息之結構的定義。</span><span class="sxs-lookup"><span data-stu-id="88d25-115">A schema is the definition of the structure for a document or message.</span></span> <span data-ttu-id="88d25-116">因為結構描述是與結構內的記錄和欄位相關，所以會包含屬性資訊。</span><span class="sxs-lookup"><span data-stu-id="88d25-116">It contains property information as it pertains to the records and fields within the structure.</span></span> <span data-ttu-id="88d25-117">在適當的情況下，結構描述可以包含多個子結構描述。</span><span class="sxs-lookup"><span data-stu-id="88d25-117">If appropriate, a schema can contain multiple subschemas.</span></span>  
  
 <span data-ttu-id="88d25-118">您可以使用 BizTalk 編輯器來匯入、編輯或建立結構描述。</span><span class="sxs-lookup"><span data-stu-id="88d25-118">You can use BizTalk Editor to import, edit, or create schemas.</span></span> <span data-ttu-id="88d25-119">接著，您可以使用您建立的結構描述在 BizTalk 對應工具中產生對應。</span><span class="sxs-lookup"><span data-stu-id="88d25-119">You can then use the schemas that you create to generate maps in BizTalk Mapper.</span></span> <span data-ttu-id="88d25-120">所有您使用 BizTalk 編輯器儲存的結構描述都是以 .xsd 為副檔名。</span><span class="sxs-lookup"><span data-stu-id="88d25-120">All schemas that you save by using BizTalk Editor have an .xsd file extension.</span></span>  
  
 <span data-ttu-id="88d25-121">如需結構描述和 BizTalk 編輯器的詳細資訊，請參閱[建立結構描述使用 BizTalk 編輯器](../core/creating-schemas-using-biztalk-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="88d25-121">For more information about schemas and BizTalk Editor, see [Creating Schemas Using BizTalk Editor](../core/creating-schemas-using-biztalk-editor.md).</span></span>  
  
## <a name="maps"></a><span data-ttu-id="88d25-122">地圖</span><span class="sxs-lookup"><span data-stu-id="88d25-122">Maps</span></span>  
 <span data-ttu-id="88d25-123">對應是一種 XML 檔案，負責定義不同結構描述中之記錄與欄位間的對應。</span><span class="sxs-lookup"><span data-stu-id="88d25-123">A map is an XML file that defines the correspondence between the records and fields in one schema and the records and fields in another schema.</span></span> <span data-ttu-id="88d25-124">您可根據產業標準、非產業標準 (例如內部標準或已知問題) 或現有檔案來建立對應。</span><span class="sxs-lookup"><span data-stu-id="88d25-124">You create maps based on industry standards, non-industry standards (such as internal standards or legacy issues), or existing files.</span></span> <span data-ttu-id="88d25-125">當您想要將接收或傳送的資料從某種格式轉換成另一種格式時，就要建立對應。</span><span class="sxs-lookup"><span data-stu-id="88d25-125">You create maps when you want to transform data that you receive or send from one format to another.</span></span> <span data-ttu-id="88d25-126">您可以使用 BizTalk 對應工具來建立您要併入 BizTalk 專案的對應。</span><span class="sxs-lookup"><span data-stu-id="88d25-126">You can use BizTalk Mapper to create maps that you include in a BizTalk project.</span></span> <span data-ttu-id="88d25-127">所有您在 BizTalk 對應工具中儲存的對應都是以 .btm 為副檔名。</span><span class="sxs-lookup"><span data-stu-id="88d25-127">All maps that you save in BizTalk Mapper have a .btm file extension.</span></span> <span data-ttu-id="88d25-128">如需 BizTalk 對應工具的詳細資訊，請參閱[建立對應使用 BizTalk 對應工具](../core/creating-maps-using-biztalk-mapper.md)。</span><span class="sxs-lookup"><span data-stu-id="88d25-128">For more information about BizTalk Mapper, see [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md).</span></span>  
  
## <a name="pipelines"></a><span data-ttu-id="88d25-129">管線</span><span class="sxs-lookup"><span data-stu-id="88d25-129">Pipelines</span></span>  
 <span data-ttu-id="88d25-130">您可以使用「管線設計師」來建立傳送管線和接收管線。</span><span class="sxs-lookup"><span data-stu-id="88d25-130">You can use Pipeline Designer to create receive and send pipelines.</span></span> <span data-ttu-id="88d25-131">管線是一種軟體基礎結構，定義及連結一或多個階段來處理由 BizTalk Server 傳送或接收訊息。</span><span class="sxs-lookup"><span data-stu-id="88d25-131">A pipeline is a software infrastructure that defines and links one or more stages for processing messages received or sent by BizTalk Server.</span></span> <span data-ttu-id="88d25-132">管線會以特定的順序實作這些階段，並包含諸如編碼或解碼、組譯或反組譯以及加密或解密等函式。</span><span class="sxs-lookup"><span data-stu-id="88d25-132">The pipelines implement the stages in a specific order and include functions such as encoding or decoding, assembling or disassembling, and encrypting or decrypting.</span></span>  
  
 <span data-ttu-id="88d25-133">BizTalk 專案中所包含的預設管線參考只能處理 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="88d25-133">The default pipeline references included in a BizTalk project can process only XML documents.</span></span> <span data-ttu-id="88d25-134">如果您想要處理一般檔案、EDI 文件或其他檔案類型，則必須適當地建立新的管線。</span><span class="sxs-lookup"><span data-stu-id="88d25-134">If you want to process flat files, EDI documents, or other file types, you must create new pipelines as appropriate.</span></span> <span data-ttu-id="88d25-135">所有使用管線設計師所建立的管線都是以 .btp 為副檔名。</span><span class="sxs-lookup"><span data-stu-id="88d25-135">All pipelines created with Pipeline Designer have a .btp extension.</span></span> <span data-ttu-id="88d25-136">如需管線和管線設計師 」 的詳細資訊，請參閱[管線使用管線設計師建立](../core/creating-pipelines-using-pipeline-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="88d25-136">For more information about pipelines and Pipeline Designer, see [Creating Pipelines Using Pipeline Designer](../core/creating-pipelines-using-pipeline-designer.md).</span></span>  
  
## <a name="valid-files-for-biztalk-projects"></a><span data-ttu-id="88d25-137">BizTalk 專案的有效檔案</span><span class="sxs-lookup"><span data-stu-id="88d25-137">Valid Files for BizTalk Projects</span></span>  
 <span data-ttu-id="88d25-138">當您搭配使用 BizTalk 專案時，您可以包含許多不同的檔案 (例如 HTML 檔案、XML 檔案、接收管線檔案和結構描述檔案)。</span><span class="sxs-lookup"><span data-stu-id="88d25-138">When you work with a BizTalk project, you can include many different files, such as HTML files, XML files, receive pipeline files, and schema files.</span></span> <span data-ttu-id="88d25-139">與 BizTalk Server 組件可以包含任何 Visual Studio 建置系統所支援的物件。</span><span class="sxs-lookup"><span data-stu-id="88d25-139">With BizTalk Server, the assembly can contain any object supported by the Visual Studio build system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88d25-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88d25-140">See Also</span></span>  
 [<span data-ttu-id="88d25-141">使用 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="88d25-141">Working with BizTalk Projects</span></span>](../core/working-with-biztalk-projects.md)