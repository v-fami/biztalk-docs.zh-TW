---
title: 文件參考 URL 節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Document Reference URL nodes [Tracking Profile Editor]
- Tracking Profile Editor, node descriptions
- definition files [BAM], related documents
ms.assetid: 38c8ae50-ed56-451c-9549-db852d4770e5
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7939a7e74483b8df192530fd9da2deafeda0681
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238966"
---
# <a name="document-reference-url-nodes"></a><span data-ttu-id="f7124-102">Document Reference URL 節點</span><span class="sxs-lookup"><span data-stu-id="f7124-102">Document Reference URL Nodes</span></span>
<span data-ttu-id="f7124-103">Document Reference URL 節點存在於開發人員從知識工作者建立的觀察模型中匯入的活動定義檔。</span><span class="sxs-lookup"><span data-stu-id="f7124-103">Document Reference URL nodes exist in the activity definition file that the developer imports from the knowledge worker created observation model.</span></span> <span data-ttu-id="f7124-104">Document Reference URL 節點含有與此活動關聯之文件所在位置的參考。</span><span class="sxs-lookup"><span data-stu-id="f7124-104">Document Reference URL nodes contain references to a location that contains a document that is related to this activity.</span></span> <span data-ttu-id="f7124-105">這可以是任意類型的文件，例如，如果是代表訂單核准工作流程的活動，則 Document Reference URL 可能指向基礎訂單文件。</span><span class="sxs-lookup"><span data-stu-id="f7124-105">This can be any type of document, for example an activity that represents a purchase order approval work flow, the Document Reference URL might point to the underlying purchase order document.</span></span>  
  
## <a name="working-with-document-reference-url-nodes"></a><span data-ttu-id="f7124-106">使用 Document Reference URL 節點</span><span class="sxs-lookup"><span data-stu-id="f7124-106">Working with Document Reference URL nodes</span></span>  
 <span data-ttu-id="f7124-107">Document Reference URL 的資料來源通常是**MessageRefURL** BizTalk Server 系統屬性。</span><span class="sxs-lookup"><span data-stu-id="f7124-107">The data source for the Document Reference URL is typically the **MessageRefURL** BizTalk Server system property.</span></span> <span data-ttu-id="f7124-108">您也可以使用儲存 URL 的自訂結構描述，再從自訂結構描述將該屬性對應至 Document Reference URL。</span><span class="sxs-lookup"><span data-stu-id="f7124-108">You can also use custom schemas that store URLs and map the property to the Document Reference URL from the custom schema.</span></span>  
  
 <span data-ttu-id="f7124-109">Document Reference URL 的相關注意事項：</span><span class="sxs-lookup"><span data-stu-id="f7124-109">Items to note about Document Reference URLs:</span></span>  
  
-   <span data-ttu-id="f7124-110">您可以新增一或多個 Document Reference URL，但每個節點在活動中必須具有唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="f7124-110">You can add one or more Document Reference URLs, but each node must have unique name within the activity.</span></span>  
  
-   <span data-ttu-id="f7124-111">**MessageRefURL**填入 Document Reference URL 節點所需的屬性只能填入值，如果是 WSS、 FILE 和 FTP 傳輸配接器。</span><span class="sxs-lookup"><span data-stu-id="f7124-111">The **MessageRefURL** property needed to populate a Document Reference URL node is only populated with a value in the case of WSS, FILE, and FTP transport adapters.</span></span>  
  
-   <span data-ttu-id="f7124-112">雖然商務使用者可以從 BAM 入口網站檢視此參考，但是參考 URL 的主要用途是讓自訂使用者介面的開發人員能夠存取關聯的文件資訊，以便向使用者呈現這些資訊。</span><span class="sxs-lookup"><span data-stu-id="f7124-112">While business end-users can view this reference in the BAM portal, the primary purpose of the reference URL is to allow custom user interface developers to gain access to associated document information so that they can present it to the end user.</span></span>  <span data-ttu-id="f7124-113">如需檢視 BAM 入口網站中的文件參考的詳細資訊，請參閱[相關文件](../core/related-documents.md)。</span><span class="sxs-lookup"><span data-stu-id="f7124-113">For more information on viewing the document reference in the BAM portal, see [Related Documents](../core/related-documents.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7124-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7124-114">See Also</span></span>  
 [<span data-ttu-id="f7124-115">TPE 活動檢視節點</span><span class="sxs-lookup"><span data-stu-id="f7124-115">TPE Activity View Nodes</span></span>](../core/tpe-activity-view-nodes.md)