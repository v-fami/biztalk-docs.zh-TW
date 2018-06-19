---
title: 內容屬性檢視 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking Profile Editor, message schemas
- Context Property view [Tracking Profile Editor]
- Tracking Profile Editor, Context Property view
- message schemas, XML messages
ms.assetid: 17a21b86-995c-4dc2-9a3c-1309837d0b9b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84a0f3a1d507e1440f67cd5f9e4afa18bff0b52a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22237878"
---
# <a name="context-property-view"></a><span data-ttu-id="319a1-102">內容屬性檢視</span><span class="sxs-lookup"><span data-stu-id="319a1-102">Context Property View</span></span>
<span data-ttu-id="319a1-103">[內容屬性] 檢視會顯示與屬性相關聯的 XML 訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="319a1-103">The Context Property view displays the schema of the XML message associated with the property.</span></span> <span data-ttu-id="319a1-104">您可以從 [協調流程排程] 檢視中某些圖形的捷徑功能表存取該檢視。</span><span class="sxs-lookup"><span data-stu-id="319a1-104">The view is available from the shortcut menu for some of the shapes in the Orchestration Schedule view.</span></span>  
  
## <a name="working-with-the-context-property-view"></a><span data-ttu-id="319a1-105">使用內容屬性檢視</span><span class="sxs-lookup"><span data-stu-id="319a1-105">Working with the Context Property view</span></span>  
 <span data-ttu-id="319a1-106">選取內容屬性檢視，請按一下**選取事件來源**按鈕，然後按一下**選取內容屬性**功能表項目。</span><span class="sxs-lookup"><span data-stu-id="319a1-106">You select your Context Property view by clicking the **Select Event Source** button and clicking the **Select Context Property** menu item.</span></span> <span data-ttu-id="319a1-107">接著從已知的內容屬性清單中選擇內容屬性，以載入該屬性的結構描述。</span><span class="sxs-lookup"><span data-stu-id="319a1-107">You then choose a context property from the list of known context properties to load the schema for that property.</span></span> <span data-ttu-id="319a1-108">一旦選取屬性後，您可以將項目從關聯的結構描述拖曳到活動的資料項目資料夾，表示要由位於此動作的訊息中特定之 XPath 運算式擷取該資料。</span><span class="sxs-lookup"><span data-stu-id="319a1-108">Once you select the property, you can drag elements from the associated schema to the data item folders of the activity, thus indicating you want to extract that data from specific XPath expression inside the message at this action.</span></span>  
  
 <span data-ttu-id="319a1-109">在協調流程排程檢視中，以滑鼠右鍵按一下含有內容屬性的圖形亦可開啟內容屬性檢視。</span><span class="sxs-lookup"><span data-stu-id="319a1-109">You can open context property views from the orchestration schedule view by right-clicking a shape that contains a context property.</span></span> <span data-ttu-id="319a1-110">這會開啟內容功能表，您可從中按一下**內容屬性結構描述**功能表項目，來擷取與圖形相關聯的內容屬性的清單。</span><span class="sxs-lookup"><span data-stu-id="319a1-110">This will open a context menu from which you can click the **Context Property Schema** menu item to retrieve a list of context properties associated with the shape.</span></span>  
  
 <span data-ttu-id="319a1-111">可用的內容屬性清單可能很長。</span><span class="sxs-lookup"><span data-stu-id="319a1-111">The list of available context properties can be extensive.</span></span> <span data-ttu-id="319a1-112">如果您知道您要搜尋的屬性名稱的一部分，您可以輸入在**中字串**文字方塊中，然後按一下**搜尋** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="319a1-112">If you know part of the name of the property for which you are searching, you can type it in the **In String** text box and click the **Search** button.</span></span> <span data-ttu-id="319a1-113">這樣就會只選取名稱中包含所輸入之部分字串的屬性。</span><span class="sxs-lookup"><span data-stu-id="319a1-113">This will select only those properties that contain the partial string you have entered.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="319a1-114">當您選擇經由 [內容屬性] 檢視進行對應時，可能的屬性結構描述清單將會是 BizTalk Server 安裝中已設定之每個屬性結構描述的完整清單。</span><span class="sxs-lookup"><span data-stu-id="319a1-114">When you choose to map from the Context Properties view, the list of potential property schemas is a complete list of every property schema configured in your BizTalk Server installation.</span></span>  <span data-ttu-id="319a1-115">請務必注意，所呈現的結構描述未能判別目前執行中的處理程序，使用了哪些 BizTalk Server 功能。</span><span class="sxs-lookup"><span data-stu-id="319a1-115">You must aware that the schemas presented are not sensitive to which features in BizTalk Server are used by the running process on which you are working.</span></span> <span data-ttu-id="319a1-116">例如，您可以從 [內容屬性] 對應所提供的結構描述清單中選取 SOAP 屬性的結構描述，但是執行中的處理程序本身可能不使用 SOAP。</span><span class="sxs-lookup"><span data-stu-id="319a1-116">For example, you can select a schema for SOAP properties from the list of schemas offered when mapping from Context Properties, but the running process itself may not use SOAP.</span></span> <span data-ttu-id="319a1-117">經由未使用的屬性所對應的任何 BAM 活動項目，將導致 BAM 擷取到空值或空白資料。</span><span class="sxs-lookup"><span data-stu-id="319a1-117">Any BAM activity item mapped from an unused property results in null or empty data being captured by BAM.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="319a1-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="319a1-118">See Also</span></span>  
 <span data-ttu-id="319a1-119">[什麼是事件來源檢視時？](../core/what-is-the-source-event-view.md) </span><span class="sxs-lookup"><span data-stu-id="319a1-119">[What Is the Source Event View?](../core/what-is-the-source-event-view.md) </span></span>  
 [<span data-ttu-id="319a1-120">追蹤設定檔編輯器</span><span class="sxs-lookup"><span data-stu-id="319a1-120">Tracking Profile Editor</span></span>](../core/tracking-profile-editor.md)