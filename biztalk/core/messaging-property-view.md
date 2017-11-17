---
title: "傳訊屬性檢視 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking Profile Editor, message schemas
- message schemas, properties
- Messaging Property view [Tracking Profile Editor]
- Tracking Profile Editor, Messaging Property view
- message schemas, XML messages
ms.assetid: 80d040e9-d58b-41d1-b26d-19aff4d3126b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1be1498cd3766863b9f5b2e3a37ae419d4bafc8a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="messaging-property-view"></a><span data-ttu-id="7a27e-102">傳訊屬性檢視</span><span class="sxs-lookup"><span data-stu-id="7a27e-102">Messaging Property View</span></span>
<span data-ttu-id="7a27e-103">[傳訊屬性] 檢視會顯示與屬性相關聯的 XML 訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="7a27e-103">The Messaging Property view displays the schema of the XML message associated with the property.</span></span> <span data-ttu-id="7a27e-104">您可以從 [協調流程排程] 檢視中某些圖形的捷徑功能表存取該檢視。</span><span class="sxs-lookup"><span data-stu-id="7a27e-104">The view is available from the shortcut menu for some of the shapes in the Orchestration Schedule view.</span></span>  
  
## <a name="working-with-messaging-properties"></a><span data-ttu-id="7a27e-105">使用傳訊屬性</span><span class="sxs-lookup"><span data-stu-id="7a27e-105">Working with messaging properties</span></span>  
 <span data-ttu-id="7a27e-106">選取傳訊屬性檢視，請按一下**選取事件來源**按鈕，然後按一下**選取訊息屬性**功能表項目。</span><span class="sxs-lookup"><span data-stu-id="7a27e-106">You select your Messaging Property view by clicking the **Select Event Source** button and clicking the **Select Message Property** menu item.</span></span> <span data-ttu-id="7a27e-107">然後您可以選擇要從其中選取結構描述的訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="7a27e-107">You then choose a message property from which to select a schema.</span></span> <span data-ttu-id="7a27e-108">一旦選取結構描述後，您可以將項目從該結構描述拖曳到活動的資料項目資料夾，表示要由位於此動作的訊息中特定之 XPath 運算式擷取該特定資料。</span><span class="sxs-lookup"><span data-stu-id="7a27e-108">Once you select the schema, you can drag elements from this schema to the data item folders of the activity, thus indicating that you want to extract that particular data from specific XPath expressions inside the message at this action.</span></span>  
  
 <span data-ttu-id="7a27e-109">在協調流程排程檢視中，以滑鼠右鍵按一下含有訊息內容的圖形開啟訊息屬性檢視。</span><span class="sxs-lookup"><span data-stu-id="7a27e-109">You can open message property views from the Orchestration Schedule view by right-clicking a shape that contains a message payload.</span></span> <span data-ttu-id="7a27e-110">當快顯功能表開啟時，請按一下 [訊息內容] 功能表項目，以擷取與圖形相關聯的內容清單。</span><span class="sxs-lookup"><span data-stu-id="7a27e-110">This will open a context menu from which you can click the Message Payload menu item to retrieve a list of payloads associated with the shape.</span></span>  
  
 <span data-ttu-id="7a27e-111">可用的訊息屬性清單可能很長。</span><span class="sxs-lookup"><span data-stu-id="7a27e-111">The list of available message properties can be extensive.</span></span> <span data-ttu-id="7a27e-112">如果您知道您要搜尋的協調流程的名稱的一部分，您可以輸入在**中字串**文字方塊中，然後按一下**搜尋** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7a27e-112">If you know part of the name of the orchestration for which you are searching, you can type it in the **In String** text box and click the **Search** button.</span></span> <span data-ttu-id="7a27e-113">這樣就會只選取名稱中包含所輸入之部分字串的訊息屬性</span><span class="sxs-lookup"><span data-stu-id="7a27e-113">This will select only those message properties that contain the partial string you have entered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a27e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a27e-114">See Also</span></span>  
 <span data-ttu-id="7a27e-115">[什麼是事件來源檢視時？](../core/what-is-the-source-event-view.md) </span><span class="sxs-lookup"><span data-stu-id="7a27e-115">[What Is the Source Event View?](../core/what-is-the-source-event-view.md) </span></span>  
 [<span data-ttu-id="7a27e-116">追蹤設定檔編輯器</span><span class="sxs-lookup"><span data-stu-id="7a27e-116">Tracking Profile Editor</span></span>](../core/tracking-profile-editor.md)