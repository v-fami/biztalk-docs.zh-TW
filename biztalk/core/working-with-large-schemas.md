---
title: "使用大型結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8348036d-6edb-46a3-badd-0223cfe0a92f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5c5ef679070009b5dfb5fdd403d238cfe243cb2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-large-schemas"></a><span data-ttu-id="fbc2a-102">使用大型結構描述</span><span class="sxs-lookup"><span data-stu-id="fbc2a-102">Working with Large Schemas</span></span>
<span data-ttu-id="fbc2a-103">當結構描述變得非常大，您可能發現重新整理 XSD 檢視的速度變慢，且使用者介面的其他方面也可能大受影響。</span><span class="sxs-lookup"><span data-stu-id="fbc2a-103">When your schemas become very large, you may find that refreshing the XSD view is increasingly slow and that the response of other aspects of the user interface can be impacted as well.</span></span> <span data-ttu-id="fbc2a-104">此問題解決方法是關閉自動重新整理功能，並改為使用手動**重新整理**XSD 檢視要定期重新整理 XSD 檢視中的連結。</span><span class="sxs-lookup"><span data-stu-id="fbc2a-104">The solution to this issue is to turn off the auto-refresh feature and instead use the manual **Refresh** link in the XSD view to periodically refresh the XSD view.</span></span> <span data-ttu-id="fbc2a-105">逐步說明如何開啟的自動重新整理功能關閉，請參閱 < 開啟及關閉開啟自動重新整理 XSD 檢視的 「 程序中[管理 XSD 檢視](../core/how-to-manage-the-xsd-view.md)。</span><span class="sxs-lookup"><span data-stu-id="fbc2a-105">For step-by-step instructions about how turn the auto-refresh feature on an off, see the procedure "To turn automatic refresh of the XSD view on and off" in [Managing the XSD View](../core/how-to-manage-the-xsd-view.md).</span></span>  
  
 <span data-ttu-id="fbc2a-106">效能也可能變慢的大型結構描述具有多個根附加至**結構描述**節點。</span><span class="sxs-lookup"><span data-stu-id="fbc2a-106">Performance may also be slow in large schemas with multiple roots attached to the **schema** node.</span></span> <span data-ttu-id="fbc2a-107">設定**根參考**屬性可能會增加使用者介面中的效能。</span><span class="sxs-lookup"><span data-stu-id="fbc2a-107">Setting the **Root Reference** property may increase performance in the user interface.</span></span> <span data-ttu-id="fbc2a-108">設定**根參考**改善效能，因為編譯器會在所有根結構描述建立 C# 類別。</span><span class="sxs-lookup"><span data-stu-id="fbc2a-108">Setting **Root Reference** improves performance because the compiler creates C# classes for all root schemas.</span></span> <span data-ttu-id="fbc2a-109">單一根節點表示建立較少類別。</span><span class="sxs-lookup"><span data-stu-id="fbc2a-109">A single root means the creation of fewer classes.</span></span>  
  
 <span data-ttu-id="fbc2a-110">**驗證執行個體**可能會出現在使用者介面變慢，因為會一律對驗證結構描述驗證執行個體之前。</span><span class="sxs-lookup"><span data-stu-id="fbc2a-110">**Validate Instance** may appear slow in the user interface because a validation is always done on the schema before validating the instance.</span></span> <span data-ttu-id="fbc2a-111">結構描述驗證僅發生在使用者介面。</span><span class="sxs-lookup"><span data-stu-id="fbc2a-111">Schema validation occurs only in the user interface.</span></span> <span data-ttu-id="fbc2a-112">設定**根參考**屬性也可以改善使用者介面效能在此情況下。</span><span class="sxs-lookup"><span data-stu-id="fbc2a-112">Setting the **Root Reference** property also improves user interface performance in this case.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc2a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbc2a-113">See Also</span></span>  
 [<span data-ttu-id="fbc2a-114">使用 BizTalk 編輯器</span><span class="sxs-lookup"><span data-stu-id="fbc2a-114">Using BizTalk Editor</span></span>](../core/using-biztalk-editor.md)