---
title: 使用 BizTalk 編輯器建立結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03fac91b-5b67-4baf-968c-294c525d3018
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb9e4c6496f43a9602ad56bc0e095d98f2da90d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238934"
---
# <a name="create-schemas-using-biztalk-editor"></a><span data-ttu-id="707de-102">建立結構描述使用 BizTalk 編輯器</span><span class="sxs-lookup"><span data-stu-id="707de-102">Create Schemas Using BizTalk Editor</span></span>

## <a name="overview"></a><span data-ttu-id="707de-103">概觀</span><span class="sxs-lookup"><span data-stu-id="707de-103">Overview</span></span>
<span data-ttu-id="707de-104">BizTalk 編輯器是在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 環境中執行的工具。</span><span class="sxs-lookup"><span data-stu-id="707de-104">BizTalk Editor is a tool that runs within the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.</span></span> <span data-ttu-id="707de-105">您可以用它來建立、編輯和管理應用程式要使用的結構描述。</span><span class="sxs-lookup"><span data-stu-id="707de-105">You can use it to create, edit, and manage schemas for use with your application.</span></span> <span data-ttu-id="707de-106">BizTalk 編輯器會使用階層式記錄與欄位的圖形系統來代表執行個體訊息的結構，並使用 XML 結構描述定義 (XSD) 語言來儲存它定義的結構描述。</span><span class="sxs-lookup"><span data-stu-id="707de-106">BizTalk Editor uses its own graphical system of hierarchical records and fields to represent the structure of instance messages, and uses the XML Schema definition (XSD) language to store the schemas that it defines.</span></span> <span data-ttu-id="707de-107">不論執行個體訊息交換的格式為何，這都成立。</span><span class="sxs-lookup"><span data-stu-id="707de-107">This is true regardless of the format in which instance messages are exchanged.</span></span> <span data-ttu-id="707de-108">例如，假設您與交易夥伴交換一般檔案。</span><span class="sxs-lookup"><span data-stu-id="707de-108">For example, suppose that you exchange flat files with a trading partner.</span></span> <span data-ttu-id="707de-109">BizTalk Server 會處理這些一般檔案，它會將這些檔案轉換成 XML 格式，或是從 XML 格式轉換成一般檔案，以符合您在 BizTalk 編輯器中定義的 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="707de-109">As BizTalk Server processes those flat files, it converts them to and from an XML format that conforms to an XSD schema that you defined in BizTalk Editor.</span></span>  
  
 <span data-ttu-id="707de-110">您使用 BizTalk 編輯器所建立的結構描述可用於協調的商務程序中，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="707de-110">The schemas you create using BizTalk Editor can be used within an orchestrated business process, as shown in the following figure.</span></span>  
  
 ![](../core/media/ebiz-dev-busprcsh.gif "ebiz_dev_busprcsh")  
  
 <span data-ttu-id="707de-111">組合器與解譯器也會使用結構描述，將執行個體訊息從某個格式轉譯成另一個格式，例如，在一般檔案格式與 XML 之間進行轉譯。</span><span class="sxs-lookup"><span data-stu-id="707de-111">Schemas are also used by assemblers and disassemblers for translating instance messages from one format to another, such as between a flat file format and XML.</span></span> <span data-ttu-id="707de-112">結構描述在執行個體訊息轉換中也扮演著非常重要的角色，透過它，執行個體訊息中的資料可用以建構不同結構的執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="707de-112">Schemas also play an important role in instance message transformation, wherein the data in an instance message is used to construct an instance message with a different structure.</span></span> <span data-ttu-id="707de-113">新執行個體訊息在語意上可能會一樣 (例如，不同表示法的訂單)，或是它可能是不同、但為相關類型的執行個體訊息，其需要原始執行個體訊息內容中的部分或全部資料。</span><span class="sxs-lookup"><span data-stu-id="707de-113">The new instance message might be semantically equivalent, such as different representations of a purchase order, or it might be a different but related type of instance message that requires some or all of the data from the original instance message in its content.</span></span>  
  
 <span data-ttu-id="707de-114">將所有執行個體訊息轉譯成符合 XSD 結構描述之 XML 格式的重要理由，是為了簡化將訊息從某個結構轉換為另一個結構的程序。</span><span class="sxs-lookup"><span data-stu-id="707de-114">An important reason for translating all instance messages into an XML format that conforms to an XSD schema is to simplify the process of transforming a message from one structure into another structure.</span></span> <span data-ttu-id="707de-115">一般而言，訊息結構的語法雖然不同，但其語意是一樣的。</span><span class="sxs-lookup"><span data-stu-id="707de-115">Message structures are typically semantically equivalent despite their syntactic differences.</span></span> <span data-ttu-id="707de-116">例如，您和您的交易夥伴可能會以不同的結構來組織您們的訂單，但是它們所包含的基本資訊是相同的，可讓它們自動來回轉換。</span><span class="sxs-lookup"><span data-stu-id="707de-116">For example, you and your trading partner might structure your purchase orders differently, but the basic information they contain is the same, allowing them to be transformed back and forth automatically.</span></span> <span data-ttu-id="707de-117">透過先將所有的執行個體訊息轉換為對應 XSD 結構描述所決定的 XML 格式，執行個體訊息就可在 XML 與非 XML 格式之間來回轉譯，並從某個 XML 結構轉換為另一個結構。</span><span class="sxs-lookup"><span data-stu-id="707de-117">By first converting all instance messages into an XML format governed by a corresponding XSD schema, the instance messages can be translated back and forth between XML and non-XML formats, and transformed from one XML structure to another.</span></span> <span data-ttu-id="707de-118">如需有關執行個體訊息轉譯與執行個體訊息轉換之間差別的詳細資訊，請參閱[資料轉換](../core/data-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="707de-118">For more information about the distinction between instance message translation and instance message transformation, see [Data Transformation](../core/data-transformation.md).</span></span>  
  
 <span data-ttu-id="707de-119">在 Microsoft Visual Studio 環境中，BizTalk 編輯器的隨附工具是 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="707de-119">The companion tool to BizTalk Editor within the Microsoft Visual Studio environment is BizTalk Mapper.</span></span> <span data-ttu-id="707de-120">在您使用 BizTalk 編輯器來建立結構描述，以定義一組相關執行個體訊息的結構與格式後，就可以使用 BizTalk 對應工具，以圖形方式定義如何將符合某個結構描述的執行個體訊息 (來源執行個體訊息與結構描述) 轉換為符合另一個結構描述的執行個體 (目的執行個體訊息與結構描述)。</span><span class="sxs-lookup"><span data-stu-id="707de-120">After you use BizTalk Editor to create the schemas that define the structure and format of a pair of related instance messages, you use BizTalk Mapper to graphically define how to transform an instance message conforming to one schema (the source instance message and schema) into an instance message conforming to another schema (the destination instance message and schema).</span></span> <span data-ttu-id="707de-121">這類轉換的規格是使用可延伸樣式表語言轉換 (XSLT) 來實作，並保存為稱為對應的檔案。</span><span class="sxs-lookup"><span data-stu-id="707de-121">The specification of such transformations is implemented using Extensible Stylesheet Language Transformations (XSLT) and persisted as files called maps.</span></span> <span data-ttu-id="707de-122">如需 BizTalk 對應工具 」 的概念和程序資訊，請參閱[建立對應使用 BizTalk 對應工具](../core/creating-maps-using-biztalk-mapper.md)。</span><span class="sxs-lookup"><span data-stu-id="707de-122">For conceptual and procedural information about BizTalk Mapper, see [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md).</span></span> <span data-ttu-id="707de-123">如需 BizTalk 對應工具 」 屬性與運算質的參考資訊，請參閱**對應屬性參考**和**運算質參考**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  </span><span class="sxs-lookup"><span data-stu-id="707de-123">For reference information about BizTalk Mapper properties and functoids, see the **Map Property Reference** and **Functoid Reference**  [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="707de-124">使用 BizTalk 編輯器，您可以開啟未包含結構的空白結構描述、開啟現有 XSD 結構描述，或是從非 XSD 來源產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="707de-124">Using BizTalk Editor, you can open a blank schema that contains no structure, you can open an existing XSD schema, or you can generate a schema from a non-XSD source.</span></span> <span data-ttu-id="707de-125">當您從非 XSD 來源產生結構描述時，BizTalk 編輯器會解譯來源的結構並產生其 XSD 表示法的結構描述。</span><span class="sxs-lookup"><span data-stu-id="707de-125">When you generate a schema from a non-XSD source, BizTalk Editor interprets the structure of the source and produces a schema that is an XSD representation of it.</span></span> <span data-ttu-id="707de-126">您可以編輯出現在 BizTalk 編輯器結構描述樹狀結構檢視中的任何記錄與欄位，然後將該結構儲存為 BizTalk 結構描述。</span><span class="sxs-lookup"><span data-stu-id="707de-126">You can edit any records and fields that appear in the BizTalk Editor schema tree view, and then save the structure as a BizTalk schema.</span></span>  
  
 <span data-ttu-id="707de-127">使用鍵盤快速鍵在 「 BizTalk 編輯器 」 的相關資訊，請參閱[BizTalk 編輯器鍵盤快速鍵](../core/biztalk-editor-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="707de-127">For information about using the keyboard shortcuts for BizTalk Editor, see [BizTalk Editor Keyboard Shortcuts](../core/biztalk-editor-keyboard-shortcuts.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="707de-128">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="707de-128">Next steps</span></span>
  
-   [<span data-ttu-id="707de-129">規劃建立結構描述</span><span class="sxs-lookup"><span data-stu-id="707de-129">Planning for Schema Creation</span></span>](../core/planning-for-schema-creation.md)  
  
-   [<span data-ttu-id="707de-130">關於執行個體訊息</span><span class="sxs-lookup"><span data-stu-id="707de-130">About Instance Messages</span></span>](../core/about-instance-messages.md)  
  
-   [<span data-ttu-id="707de-131">關於結構描述</span><span class="sxs-lookup"><span data-stu-id="707de-131">About Schemas</span></span>](../core/about-schemas.md)  
  
-   [<span data-ttu-id="707de-132">使用 BizTalk 編輯器</span><span class="sxs-lookup"><span data-stu-id="707de-132">Using BizTalk Editor</span></span>](../core/using-biztalk-editor.md)  
  
-   [<span data-ttu-id="707de-133">建立結構描述</span><span class="sxs-lookup"><span data-stu-id="707de-133">Creating Schemas</span></span>](../core/creating-schemas.md)  
  
-   [<span data-ttu-id="707de-134">使用 BizTalk 一般檔案結構描述精靈建立結構描述</span><span class="sxs-lookup"><span data-stu-id="707de-134">Creating Schemas Using BizTalk Flat File Schema Wizard</span></span>](../core/creating-schemas-using-biztalk-flat-file-schema-wizard.md)  
  
-   [<span data-ttu-id="707de-135">測試結構描述</span><span class="sxs-lookup"><span data-stu-id="707de-135">Testing Schemas</span></span>](../core/testing-schemas.md)  
  
-   [<span data-ttu-id="707de-136">延伸 BizTalk 編輯器</span><span class="sxs-lookup"><span data-stu-id="707de-136">Extending BizTalk Editor</span></span>](../core/extending-biztalk-editor.md)  
  
-   [<span data-ttu-id="707de-137">建立結構描述時的考量</span><span class="sxs-lookup"><span data-stu-id="707de-137">Considerations When Creating Schemas</span></span>](../core/considerations-when-creating-schemas.md)  
  
-   [<span data-ttu-id="707de-138">結構描述的產生和驗證的已知的問題</span><span class="sxs-lookup"><span data-stu-id="707de-138">Known Issues with Schema Generation and Validation</span></span>](../core/known-issues-with-schema-generation-and-validation.md)