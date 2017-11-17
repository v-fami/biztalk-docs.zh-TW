---
title: "自訂檢視 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9084cc07-be98-4c57-afea-4fa369a38bad
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 184f49330374126f4afc0bd4bb376ea31a5ca681
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="custom-views"></a><span data-ttu-id="a69a2-102">自訂檢視</span><span class="sxs-lookup"><span data-stu-id="a69a2-102">Custom Views</span></span>
<span data-ttu-id="a69a2-103">自訂檢視，通常是唯讀視窗控制項物件 (衍生自**System.Windows.Forms.Control**)，提供用來代表自訂的檔案或支援的檔案類型的顯示格式中的結構描述擴充功能BizTalk 編輯器延伸模組。</span><span class="sxs-lookup"><span data-stu-id="a69a2-103">A custom view is typically a read-only window control object (derived from **System.Windows.Forms.Control**), and is provided by an extension to represent the schema in a display format customized for the type of file or files supported by the BizTalk Editor extension.</span></span> <span data-ttu-id="a69a2-104">延伸模組可實作多個自訂檢視，不過，它並不需要任何自訂檢視。</span><span class="sxs-lookup"><span data-stu-id="a69a2-104">An extension can implement multiple custom views, though it need not have any custom view.</span></span>  
  
 <span data-ttu-id="a69a2-105">自訂檢視會在與 XSD 檢視相同的「BizTalk 編輯器」窗格中顯示為額外的檢視，可使用檢視下方的索引標籤來存取。</span><span class="sxs-lookup"><span data-stu-id="a69a2-105">A custom view is displayed as an additional view in the same BizTalk Editor pane as the XSD view, accessible by using tabs at the bottom of the views.</span></span> <span data-ttu-id="a69a2-106">例如，「一般檔案延伸模組」新增一個標記為「一般檔案」索引標籤的檢視。</span><span class="sxs-lookup"><span data-stu-id="a69a2-106">For example, the Flat File Extension adds a new view with a tab labeled Flat File.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a69a2-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a69a2-107">See Also</span></span>  
 [<span data-ttu-id="a69a2-108">延伸 BizTalk 編輯器</span><span class="sxs-lookup"><span data-stu-id="a69a2-108">Extending BizTalk Editor</span></span>](../core/extending-biztalk-editor.md)