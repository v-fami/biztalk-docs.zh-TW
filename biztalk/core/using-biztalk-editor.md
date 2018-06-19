---
title: 使用 [BizTalk 編輯器] |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 22021272-f028-4db3-ad8a-fb89a5340910
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bdb293e6255042a46ecef16855d723c38543310c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287894"
---
# <a name="using-biztalk-editor"></a><span data-ttu-id="bcac5-102">使用 BizTalk 編輯器</span><span class="sxs-lookup"><span data-stu-id="bcac5-102">Using BizTalk Editor</span></span>

## <a name="overview"></a><span data-ttu-id="bcac5-103">概觀</span><span class="sxs-lookup"><span data-stu-id="bcac5-103">Overview</span></span>
<span data-ttu-id="bcac5-104">「BizTalk 編輯器」位於 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Shell 中。</span><span class="sxs-lookup"><span data-stu-id="bcac5-104">BizTalk Editor resides within the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] shell.</span></span> <span data-ttu-id="bcac5-105">「BizTalk 編輯器」中的部分功能依賴 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Shell 的現有使用者介面項目。</span><span class="sxs-lookup"><span data-stu-id="bcac5-105">Some of the functionality within BizTalk Editor relies upon existing user interface elements within the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] shell.</span></span> <span data-ttu-id="bcac5-106">例如，使用**檔案**，**編輯**，和**檢視**功能表，如同您對其他開發中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bcac5-106">For example, you use the **File**, **Edit**, and **View** menus just as you would for other development within [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="bcac5-107">會提供此常用功能的相關資訊**協助**功能表。</span><span class="sxs-lookup"><span data-stu-id="bcac5-107">Information about this common functionality is available from the **Help** menu.</span></span>  
  
 <span data-ttu-id="bcac5-108">當您新增結構描述至 BizTalk 專案、在 BizTalk 專案中開啟現有結構描述 (.xsd 檔案) 或按一下 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 主編輯視窗中的索引標籤以重新啟動結構描述時，BizTalk 編輯器會變成作用中。</span><span class="sxs-lookup"><span data-stu-id="bcac5-108">BizTalk Editor becomes active when you add a new schema to a BizTalk project, when you open an existing schema (an .xsd file) within a BizTalk project, or when you reactivate a schema by clicking its tab in the main [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] editing window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bcac5-109">BizTalk 編輯器會使用 UTF-16 字元編碼，以儲存結構描述檔。</span><span class="sxs-lookup"><span data-stu-id="bcac5-109">BizTalk Editor saves schema files using utf-16 character encoding.</span></span>  

## <a name="views"></a><span data-ttu-id="bcac5-110">檢視</span><span class="sxs-lookup"><span data-stu-id="bcac5-110">Views</span></span>  
 <span data-ttu-id="bcac5-111">下圖顯示 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Shell 中的各種不同檢視，這些檢視是 BizTalk 編輯器的一部分。</span><span class="sxs-lookup"><span data-stu-id="bcac5-111">The following figure shows the various views within the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] shell that are part of BizTalk Editor.</span></span>  
  
 <span data-ttu-id="bcac5-112">![BizTalk 專案的不同部分](../core/media/differentpartsofbiztalkserver.gif "DifferentpartsofBizTalkServer")</span><span class="sxs-lookup"><span data-stu-id="bcac5-112">![Different Parts of BizTalk Project](../core/media/differentpartsofbiztalkserver.gif "DifferentpartsofBizTalkServer")</span></span>  
  
 <span data-ttu-id="bcac5-113">BizTalk 編輯器是由下列 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Shell 中的檢視以及其相關對話方塊所組成：</span><span class="sxs-lookup"><span data-stu-id="bcac5-113">BizTalk Editor consists of the following views within the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] shell and their associated dialog boxes:</span></span>  
  
-   <span data-ttu-id="bcac5-114">**結構描述樹狀結構。**</span><span class="sxs-lookup"><span data-stu-id="bcac5-114">**Schema Tree.**</span></span> <span data-ttu-id="bcac5-115">此檢視位於主左邊[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]編輯視窗。</span><span class="sxs-lookup"><span data-stu-id="bcac5-115">This view is on the left side of the main [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] editing window.</span></span> <span data-ttu-id="bcac5-116">您可以藉由在此檢視中建置描述結構描述定義的訊息之結構的樹狀結構，主動建構結構描述。</span><span class="sxs-lookup"><span data-stu-id="bcac5-116">You actively construct your schema in this view by building up the tree structure that describes the structure of the message that the schema defines.</span></span> <span data-ttu-id="bcac5-117">如需 BizTalk 結構描述結構描述樹狀結構檢視中的呈現方式的詳細資訊，請參閱[BizTalk 結構描述的表示法](../core/biztalk-representation-of-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="bcac5-117">For more information about how BizTalk schemas are represented in the schema tree view, see [BizTalk Representation of Schemas](../core/biztalk-representation-of-schemas.md).</span></span>  
  
-   <span data-ttu-id="bcac5-118">**XSD 檢視。**</span><span class="sxs-lookup"><span data-stu-id="bcac5-118">**XSD View.**</span></span> <span data-ttu-id="bcac5-119">此檢視位於主右邊[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]編輯視窗。</span><span class="sxs-lookup"><span data-stu-id="bcac5-119">This view is on the right side of the main [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] editing window.</span></span> <span data-ttu-id="bcac5-120">它所顯示的 XML 結構描述定義 (XSD) 語言結構，會呈現您正在結構描述樹狀結構檢視中建構的結構描述。</span><span class="sxs-lookup"><span data-stu-id="bcac5-120">It shows the XML Schema definition (XSD) language structure that represents the schema you are constructing in the schema tree view.</span></span> <span data-ttu-id="bcac5-121">此為唯讀檢視，可用來協助您適應您所建立之結構描述的 XSD 語法。</span><span class="sxs-lookup"><span data-stu-id="bcac5-121">This view is read-only and is provided to help you become accustomed to the XSD syntax of the schema you are creating.</span></span> <span data-ttu-id="bcac5-122">您可以依照您的慣用設定來調整檢視的分隔方式，呈現僅能看見 XSD 檢視的狀態。</span><span class="sxs-lookup"><span data-stu-id="bcac5-122">If you prefer, you can adjust the view splitter so that the XSD view only barely visible.</span></span>  
  
-   <span data-ttu-id="bcac5-123">**方案總管 中。**</span><span class="sxs-lookup"><span data-stu-id="bcac5-123">**Solution Explorer.**</span></span> <span data-ttu-id="bcac5-124">此檢視位於右邊[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]殼層。</span><span class="sxs-lookup"><span data-stu-id="bcac5-124">This view is on the right side of the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] shell.</span></span> <span data-ttu-id="bcac5-125">其中會顯示 BizTalk 專案和所包含的各種項目。</span><span class="sxs-lookup"><span data-stu-id="bcac5-125">It shows the BizTalk project and the various items it contains.</span></span> <span data-ttu-id="bcac5-126">使用 [方案總管] 可將新的和現有的結構描述加入專案，以及開啟已經是專案一部分的結構描述。</span><span class="sxs-lookup"><span data-stu-id="bcac5-126">Use Solution Explorer to add new and existing schemas to the project, and to open schemas that are already part of the project.</span></span> <span data-ttu-id="bcac5-127">例如，若要建立新的結構描述，以滑鼠右鍵按一下方案總管] 視窗中的 BizTalk 專案中，按一下**新增**，按一下 [**新項目**，然後使用**加入新項目**對話方塊方塊，即可命名和建立新的結構描述。</span><span class="sxs-lookup"><span data-stu-id="bcac5-127">For example, to create a new schema, right-click the BizTalk project in the Solution Explorer window, click **Add**, click **New Item**, and then use the **Add New Item** dialog box to name and create a new schema.</span></span>  
  
-   [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="bcac5-128">  **屬性視窗。**</span><span class="sxs-lookup"><span data-stu-id="bcac5-128">  **Properties window.**</span></span> <span data-ttu-id="bcac5-129">您可以使用此視窗，來檢查和設定大部分的結構描述和節點屬性。</span><span class="sxs-lookup"><span data-stu-id="bcac5-129">You use this view to examine and set most of the schema and node properties.</span></span> <span data-ttu-id="bcac5-130">當您在結構描述樹狀結構檢視中選取節點，或在 [方案總管] 視窗中選取結構描述時，該節點或結構描述的對應屬性會使用標準 Visual Studio 範例，顯示於 [屬性] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="bcac5-130">When you select a node in the schema tree view, or select a schema in the Solution Explorer window, the corresponding properties of that node or schema are displayed in the Properties window using the standard Visual Studio paradigms.</span></span> <span data-ttu-id="bcac5-131">例如，屬性會分組成不同類別，並可根據這些類別或字母順序來顯示。</span><span class="sxs-lookup"><span data-stu-id="bcac5-131">For example, the properties are grouped into categories, and can be displayed according to these categories or alphabetically.</span></span> <span data-ttu-id="bcac5-132">如需不同的屬性，就可以選取不同類型的節點或結構描述集合的詳細資訊，請參閱**結構描述屬性參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="bcac5-132">For detailed information about the different sets of properties that are available when different types of nodes, or the schema, are selected, see the **Schema Property Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="bcac5-133">除了這些檢視之外，您可以與許多對話方塊互動。</span><span class="sxs-lookup"><span data-stu-id="bcac5-133">In addition to these views, you can interact with several dialog boxes.</span></span> <span data-ttu-id="bcac5-134">當您在編輯複雜的屬性 (例如集合) 時，通常會開啟這些對話方塊。</span><span class="sxs-lookup"><span data-stu-id="bcac5-134">You usually open these dialog boxes when you are editing a complex property such as a collection.</span></span>  
  
 <span data-ttu-id="bcac5-135">本節將提供 BizTalk 編輯器中可用之檢視、命令和快速鍵的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bcac5-135">This section provides information about the views, commands, and shortcut keys available in BizTalk Editor.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="bcac5-136">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="bcac5-136">Next steps</span></span> 
  
-   [<span data-ttu-id="bcac5-137">如何管理結構描述樹狀檢視</span><span class="sxs-lookup"><span data-stu-id="bcac5-137">How to Manage the Schema Tree View</span></span>](../core/how-to-manage-the-schema-tree-view.md)  
  
-   [<span data-ttu-id="bcac5-138">如何管理 XSD 檢視</span><span class="sxs-lookup"><span data-stu-id="bcac5-138">How to Manage the XSD View</span></span>](../core/how-to-manage-the-xsd-view.md)  
  
-   <span data-ttu-id="bcac5-139">[如何管理 [屬性] 視窗](../core/how-to-manage-the-properties-window.md)</span><span class="sxs-lookup"><span data-stu-id="bcac5-139">[How to Manage the Properties Window](../core/how-to-manage-the-properties-window.md)</span></span>  
  
-   [<span data-ttu-id="bcac5-140">如何管理其他 Visual Studio 視窗</span><span class="sxs-lookup"><span data-stu-id="bcac5-140">How to Manage Other Visual Studio Windows</span></span>](../core/how-to-manage-other-visual-studio-windows.md)  
  
-   [<span data-ttu-id="bcac5-141">使用 BizTalk 編輯器命令</span><span class="sxs-lookup"><span data-stu-id="bcac5-141">Using BizTalk Editor Commands</span></span>](../core/using-biztalk-editor-commands.md)  
  
-   [<span data-ttu-id="bcac5-142">使用大型結構描述</span><span class="sxs-lookup"><span data-stu-id="bcac5-142">Working with Large Schemas</span></span>](../core/working-with-large-schemas.md)