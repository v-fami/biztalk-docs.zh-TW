---
title: ESB 加入命名空間移除命名空間的元件和 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 21df1b21-b73c-4e31-a234-49a1a6b53cc7
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bcbe519cfd8c6796569da4de87f59fa6a16d8a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22296246"
---
# <a name="the-esb-add-namespace-and-remove-namespace-components"></a><span data-ttu-id="607e7-102">ESB 加入命名空間移除命名空間元件</span><span class="sxs-lookup"><span data-stu-id="607e7-102">The ESB Add Namespace and Remove Namespace Components</span></span>
<span data-ttu-id="607e7-103">許多公司時的 XML 技術的早期採用者時仍然新標準和共用文件很常見。</span><span class="sxs-lookup"><span data-stu-id="607e7-103">Many companies were early adopters of XML technologies at the time when standards were still emerging and document sharing was uncommon.</span></span> <span data-ttu-id="607e7-104">因此，它們並未嚴格強制執行包括唯一的根命名空間，這通常如此今天的需求。</span><span class="sxs-lookup"><span data-stu-id="607e7-104">Therefore, they did not strictly enforce the requirements for including unique root namespaces, which is usually the case today.</span></span>  
  
 <span data-ttu-id="607e7-105">不過，Microsoft BizTalk Server 會執行文件識別基礎的根節點的命名空間和根節點名稱的組合，因此沒有命名空間的根節點的文件很難進行全盤如果數個不同的文件型別使用相同的根節點名稱。</span><span class="sxs-lookup"><span data-stu-id="607e7-105">However, Microsoft BizTalk Server performs document identification based on a combination of the root node namespace and the root node name, so documents that have no namespace for the root node are difficult to positively identify if several different document types use the same root node name.</span></span>  
  
 <span data-ttu-id="607e7-106">新增命名空間和移除命名空間的元件，讓您可以將命名空間加入至文件時收到並移除命名空間與文件，在傳遞之前解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="607e7-106">The Add Namespace and Remove Namespace components solve this problem by making it possible to add namespaces to documents when they are received and to remove the namespace from the documents before they are delivered.</span></span> <span data-ttu-id="607e7-107">因此，文件可以位於預設命名空間中 （或幾種不同的文件類型的通用命名空間中） 時傳送及接收，但位於在 ESB 和 BizTalk 處理期間的暫時性唯一的根命名空間。</span><span class="sxs-lookup"><span data-stu-id="607e7-107">Therefore, documents can reside in the default namespace (or in a namespace common to several different document types) when they are sent and received but reside in a transient unique root namespace during processing within the ESB and BizTalk.</span></span>  
  
 <span data-ttu-id="607e7-108">整合舊有系統，而不是 XML 結構描述定義中使用文件類型定義 (DTD) 或使用舊版的 XML 剖析器無法建立包含根命名空間的文件時，也會很有用的元件。</span><span class="sxs-lookup"><span data-stu-id="607e7-108">The components are also useful when integrating legacy systems that use a Document Type Definition (DTD) instead of an XML Schema definition or that use legacy XML parsers that cannot create documents that contain a root namespace.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="607e7-109">安裝</span><span class="sxs-lookup"><span data-stu-id="607e7-109">Installation</span></span>  
 <span data-ttu-id="607e7-110">自動安裝 ESB 核心安裝**加入命名空間**和**移除命名空間**BizTalk Server 管線元件資料夾中的元件。</span><span class="sxs-lookup"><span data-stu-id="607e7-110">Installing the ESB Core automatically installs the **Add Namespace** and **Remove Namespace** components in the BizTalk Server Pipeline Components folder.</span></span>  
  
## <a name="how-it-works"></a><span data-ttu-id="607e7-111">運作方式</span><span class="sxs-lookup"><span data-stu-id="607e7-111">How It Works</span></span>  
 <span data-ttu-id="607e7-112">新增命名空間元件會將指定的命名空間加入至 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="607e7-112">The Add Namespace component adds a specified namespace to an XML document.</span></span> <span data-ttu-id="607e7-113">此元件可以新增至文件的單一命名空間。</span><span class="sxs-lookup"><span data-stu-id="607e7-113">The component can add only a single namespace to a document.</span></span> <span data-ttu-id="607e7-114">使用新增命名空間元件上已經有根節點的命名空間的文件並不支援的案例，所以單一的唯一命名空間都只需要。</span><span class="sxs-lookup"><span data-stu-id="607e7-114">Using the Add Namespace component on a document that already has a root node namespace is not a supported scenario because a single unique namespace is all that is required.</span></span>  
  
 <span data-ttu-id="607e7-115">元件沒有命名空間感知，而且不會保存任何命名空間值。</span><span class="sxs-lookup"><span data-stu-id="607e7-115">The components are not namespace-aware and do not persist any of the namespace values.</span></span> <span data-ttu-id="607e7-116">不過，加入命名空間元件會比較要求的訊息的現有命名空間中的命名空間，而且只會傳回原始訊息至管線如果兩者相符。</span><span class="sxs-lookup"><span data-stu-id="607e7-116">However, the Add Namespace component compares the requested namespace in the existing namespace of the message and simply returns the original message to the pipeline if they match.</span></span>  
  
 <span data-ttu-id="607e7-117">開發人員在接收管線或傳送管線中包括新增的命名空間元件，並設定適當的屬性。</span><span class="sxs-lookup"><span data-stu-id="607e7-117">Developers include the Add Namespace component in a receive pipeline or a send pipeline and set the appropriate properties.</span></span> <span data-ttu-id="607e7-118">在執行階段執行下列驗證：</span><span class="sxs-lookup"><span data-stu-id="607e7-118">The following validation is performed at run time:</span></span>  
  
-   <span data-ttu-id="607e7-119">**Xpath**屬性或**NamespaceBase**屬性必須包含的值。</span><span class="sxs-lookup"><span data-stu-id="607e7-119">The **XPaths** property or the **NamespaceBase** property must contain a value.</span></span>  
  
-   <span data-ttu-id="607e7-120">**分隔符號**屬性可以包含有效的字元 (例如 **/** 或 **\\** ) 或空字串。</span><span class="sxs-lookup"><span data-stu-id="607e7-120">The **Separator** property can contain only valid characters (such as **/** or **\\**) or an empty string.</span></span>  
  
-   <span data-ttu-id="607e7-121">**NamespacePrefix**屬性值不可為保留值的其中一個 (**ns0**至**ns6**)，而且必須是英數。</span><span class="sxs-lookup"><span data-stu-id="607e7-121">The **NamespacePrefix** property value cannot be one of the reserved values (**ns0** to **ns6**) and must be alpha numeric.</span></span>  
  
 <span data-ttu-id="607e7-122">這些規則的任何變化會導致元件在執行階段發生例外狀況、 擱置訊息 (標示為**暫止 – 繼續**)，並在 Windows 應用程式事件記錄檔中寫入項目。</span><span class="sxs-lookup"><span data-stu-id="607e7-122">Any variation from these rules causes the component to throw an exception at run time, suspend the message (marked as **Suspended – Resumable**), and write an entry in Windows Application Event Log.</span></span>  
  
 <span data-ttu-id="607e7-123">移除命名空間 」 元件從 XML 文件中移除所有的根命名空間。</span><span class="sxs-lookup"><span data-stu-id="607e7-123">The Remove Namespace component removes all root namespaces from an XML document.</span></span> <span data-ttu-id="607e7-124">元件可以移除單一文件的命名空間數目受限於可用來保存在處理期間的目前節點的實體記憶體。</span><span class="sxs-lookup"><span data-stu-id="607e7-124">The number of namespaces that the component can remove from a single document is constrained by the physical memory available to hold the current node during processing.</span></span> <span data-ttu-id="607e7-125">不過，元件會使用標準的 BizTalk Server 2009 管線訊息串流處理程序，將只在文件中的目前節點載入至記憶體，而不必載入整個文件。</span><span class="sxs-lookup"><span data-stu-id="607e7-125">However, the component uses standard BizTalk Server 2009 pipeline message streaming processes and loads only the current node in the document into memory instead of loading the entire document.</span></span>  
  
 <span data-ttu-id="607e7-126">移除命名空間元件也重新編碼指定的編碼方式的文件 (**ascii、 unicode/utf16，** 或**utf8**)，並可以從資料流，開始移除位元組順序標記 (BOM)，若必要項。</span><span class="sxs-lookup"><span data-stu-id="607e7-126">The Remove Namespace component also re-encodes the document to the specified encoding (**ascii, unicode/utf16,** or **utf8**) and can remove the Byte Order Mark (BOM) from the beginning of the stream, if required.</span></span>  
  
## <a name="using-the-add-namespace-and-remove-namespace-components"></a><span data-ttu-id="607e7-127">使用新增命名空間移除命名空間元件</span><span class="sxs-lookup"><span data-stu-id="607e7-127">Using the Add Namespace and Remove Namespace Components</span></span>  
 <span data-ttu-id="607e7-128">開發人員可能會在下列情況下使用新增的命名空間元件：</span><span class="sxs-lookup"><span data-stu-id="607e7-128">Developers might use the Add Namespace component in any of the following circumstances:</span></span>  
  
-   <span data-ttu-id="607e7-129">內送的訊息有沒有根命名空間。</span><span class="sxs-lookup"><span data-stu-id="607e7-129">The inbound message has no root namespace.</span></span>  
  
-   <span data-ttu-id="607e7-130">內送的訊息使用項目資料或屬性的資料來描述訊息類型。</span><span class="sxs-lookup"><span data-stu-id="607e7-130">The inbound message uses element data or attribute data to describe the message type.</span></span>  
  
-   <span data-ttu-id="607e7-131">描述訊息類型的資料是一致且可使用 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="607e7-131">The data describing the message type is consistent and available using XPath queries.</span></span>  
  
 <span data-ttu-id="607e7-132">新增命名空間和移除命名空間的元件可以位於任何接收管線或傳送管線的階段。</span><span class="sxs-lookup"><span data-stu-id="607e7-132">The Add Namespace and Remove Namespace components can reside in any stage of a receive pipeline or a send pipeline.</span></span> <span data-ttu-id="607e7-133">您可以鏈結元件，如果需要，如同您用來變更文件的根命名空間移除命名空間元件後面加入命名空間元件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="607e7-133">You can chain instances of the component if required, such as if you are using the Remove Namespace component followed by the Add Namespace component to change the root namespace of a document.</span></span>  
  
 <span data-ttu-id="607e7-134">如果您有多個接收位置，都需要這些元件使用時，您可以建立單一管線，並使用 BizTalk Server 「 每一執行個體 」 元件設定以設定元件屬性每個執行個體傳送或接收管線。</span><span class="sxs-lookup"><span data-stu-id="607e7-134">If you have multiple receive locations that require the use of these components, you can create a single pipeline and use the BizTalk Server "per instance" component configuration to set the component properties for each instance of the send or receive pipeline.</span></span> <span data-ttu-id="607e7-135">使用 BizTalk Server 2009，您可以設定屬性的管線以每個執行個體為基礎，這表示您可以重複單一管線使用跨多個接收位置，並可能有不同的元件屬性，每個執行個體。</span><span class="sxs-lookup"><span data-stu-id="607e7-135">Using BizTalk Server 2009, you can set properties on a per-instance basis for pipelines, which means that you can reuse a single pipeline across multiple receive locations and perhaps have different component properties for each instance.</span></span> <span data-ttu-id="607e7-136">這是可讓系統管理員不需要變更程式碼或重新部署使用 BizTalk Server 管理主控台變更執行階段設定。</span><span class="sxs-lookup"><span data-stu-id="607e7-136">This is a run-time setting that allows administrators to make the change using the BizTalk Server Administration Console without requiring changes to the code or redeployment.</span></span>  
  
## <a name="component-properties"></a><span data-ttu-id="607e7-137">元件屬性</span><span class="sxs-lookup"><span data-stu-id="607e7-137">Component Properties</span></span>  
 <span data-ttu-id="607e7-138">新增命名空間元件會公開五個公用屬性：</span><span class="sxs-lookup"><span data-stu-id="607e7-138">The Add Namespace component exposes five public properties:</span></span>  
  
-   <span data-ttu-id="607e7-139">**NamespacePrefix**。</span><span class="sxs-lookup"><span data-stu-id="607e7-139">**NamespacePrefix**.</span></span> <span data-ttu-id="607e7-140">這是之間插入命名空間前置詞**xmlns:** 部分，並在下列的等號 （=）。</span><span class="sxs-lookup"><span data-stu-id="607e7-140">This is the prefix of the namespace, inserted between the **xmlns:** part and the following equals sign ( = ).</span></span> <span data-ttu-id="607e7-141">若要避免與標準的 BizTalk 結構描述命名空間前置詞衝突，請避免使用值**ns0**透過**ns9**。</span><span class="sxs-lookup"><span data-stu-id="607e7-141">To avoid conflicts with standard BizTalk Schema namespace prefixes, avoid using the values **ns0** through **ns9**.</span></span>  
  
-   <span data-ttu-id="607e7-142">**NamespaceBase**。</span><span class="sxs-lookup"><span data-stu-id="607e7-142">**NamespaceBase**.</span></span> <span data-ttu-id="607e7-143">這是將前置詞中的值所產生的結果的命名空間的靜態區段**分隔符號**和**Xpath**屬性。</span><span class="sxs-lookup"><span data-stu-id="607e7-143">This is the static section of the namespace that will prefix the result generated by the values in the **Separator** and **XPaths** properties.</span></span>  
  
-   <span data-ttu-id="607e7-144">**ExtractionNodeXPath**。</span><span class="sxs-lookup"><span data-stu-id="607e7-144">**ExtractionNodeXPath**.</span></span> <span data-ttu-id="607e7-145">這是解析為包含您想要用於產生的組件的命名空間的項目或屬性值的文件中的單一元素的 XPath 陳述式。</span><span class="sxs-lookup"><span data-stu-id="607e7-145">This is an XPath statement that resolves to a single element in the document that contains the element or attribute values you want to use for the generated parts of the namespace.</span></span>  
  
-   <span data-ttu-id="607e7-146">**Xpath**。</span><span class="sxs-lookup"><span data-stu-id="607e7-146">**XPaths**.</span></span> <span data-ttu-id="607e7-147">這是管道 (**&#124;** ) 分隔的清單，用來擷取每個元件會結合以形成的命名空間的 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="607e7-147">This is a pipe (**&#124;** ) delimited list of XPath queries used to extract each of the components that will combine to form the namespace.</span></span>  
  
-   <span data-ttu-id="607e7-148">**分隔符號**。</span><span class="sxs-lookup"><span data-stu-id="607e7-148">**Separator**.</span></span> <span data-ttu-id="607e7-149">這是要使用的命名空間區段之間的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="607e7-149">This is the separator to use between the namespace segments.</span></span> <span data-ttu-id="607e7-150">最常見的值是正斜線 ( **/**  )，但可以是空字串，如果所需。</span><span class="sxs-lookup"><span data-stu-id="607e7-150">The most common value is a forward slash (**/** ), but it can be an empty string, if required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="607e7-151">所有的 XML 節點，例如元素和屬性名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="607e7-151">All XML nodes, such as element and attribute names, are case sensitive.</span></span>  
  
 <span data-ttu-id="607e7-152">移除命名空間元件會公開兩個公用屬性：</span><span class="sxs-lookup"><span data-stu-id="607e7-152">The Remove Namespace component exposes two public properties:</span></span>  
  
-   <span data-ttu-id="607e7-153">**編碼**。</span><span class="sxs-lookup"><span data-stu-id="607e7-153">**Encoding**.</span></span> <span data-ttu-id="607e7-154">這是編碼輸出訊息時，下列值之一： **ascii、 unicode/utf16，** 或**utf8**。</span><span class="sxs-lookup"><span data-stu-id="607e7-154">This is the encoding for the output message, one of the following values: **ascii, unicode/utf16,** or **utf8**.</span></span>  
  
-   <span data-ttu-id="607e7-155">**RemoveByteOrderMark**。</span><span class="sxs-lookup"><span data-stu-id="607e7-155">**RemoveByteOrderMark**.</span></span> <span data-ttu-id="607e7-156">這是布林值屬性，指出元件是否應該移除位元組順序標記 (通常**0xEFBB、 0xBFFFFE，** 或**0xFEFF**) 從 XML 文件資料流的開頭。</span><span class="sxs-lookup"><span data-stu-id="607e7-156">This is a Boolean property that indicates whether the component should remove the byte order mark (usually **0xEFBB, 0xBFFFFE,** or **0xFEFF**) from the beginning of the XML document stream.</span></span>  
  
 <span data-ttu-id="607e7-157">如需如何使用這些元件的範例，請參閱[安裝及執行 「 命名空間元件 」 範例](../esb-toolkit/installing-and-running-the-namespace-component-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="607e7-157">For an example of how to use these components, see [Installing and Running the Namespace Component Sample](../esb-toolkit/installing-and-running-the-namespace-component-sample.md).</span></span>