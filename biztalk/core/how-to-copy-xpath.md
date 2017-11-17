---
title: "如何複製 XPath |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 404599d4-0fb3-4c7c-91e6-1295d9d0965e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb282c5c32d8da62a9da6d7a9c900c798e44eee7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-xpath"></a><span data-ttu-id="7fb34-102">如何複製 XPath</span><span class="sxs-lookup"><span data-stu-id="7fb34-102">How to Copy XPath</span></span>
<span data-ttu-id="7fb34-103">XML 結構描述定義 (XSD) 語言提供在 BizTalk Server 中定義之訊息結構描述的基礎語法。</span><span class="sxs-lookup"><span data-stu-id="7fb34-103">The XML Schema definition (XSD) language provides the underlying syntax of the message schemas defined within BizTalk Server.</span></span> <span data-ttu-id="7fb34-104">雖然 BizTalk 對應工具中的樹狀檢視會使用記錄和欄位節點 (在其他類型節點之間) 之 BizTalk 特定的圖形階層，但其各自的屬性集 (如階層) 均是以 XSD 建構與保存。</span><span class="sxs-lookup"><span data-stu-id="7fb34-104">Although the tree views in BizTalk Mapper use a BizTalk-specific graphical hierarchy of record and field nodes (among other types of nodes), each with its own set of properties, such hierarchies are constructed and persisted as XSD.</span></span>  
  
 <span data-ttu-id="7fb34-105">在分佈於多個格線頁的複雜對應案例中，尋找結構描述節點的父節點並不容易。</span><span class="sxs-lookup"><span data-stu-id="7fb34-105">In scenarios where maps are complex and span across grid pages, locating the parent of a schema node can be difficult.</span></span> <span data-ttu-id="7fb34-106">在此情況下可以使用 XSD 路徑。</span><span class="sxs-lookup"><span data-stu-id="7fb34-106">The XSD path will be of use here.</span></span> <span data-ttu-id="7fb34-107">您可以使用 XSD 路徑來取得結構描述節點深度的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7fb34-107">You can use the XSD path to get information about the depth of schema nodes.</span></span> <span data-ttu-id="7fb34-108">此外，您也可以在其他格線頁重複使用此路徑以識別關係。</span><span class="sxs-lookup"><span data-stu-id="7fb34-108">Also, you can reuse this path in another grid page to identify the relationship.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7fb34-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="7fb34-109">Prerequisites</span></span>  
 <span data-ttu-id="7fb34-110">這些指示需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="7fb34-110">These instructions require that BizTalk Mapper is running.</span></span>  
  
### <a name="to-copy-the-xsd-path-xpath"></a><span data-ttu-id="7fb34-111">複製 XSD 路徑 (XPath)</span><span class="sxs-lookup"><span data-stu-id="7fb34-111">To copy the XSD path (XPath)</span></span>  
  
1.  <span data-ttu-id="7fb34-112">以滑鼠右鍵按一下結構描述 節點，您想要的 XSD 路徑，然後按一下**複製 XPath**。</span><span class="sxs-lookup"><span data-stu-id="7fb34-112">Right-click the schema node for which you want the XSD path, and then click **Copy XPath**.</span></span>  
  
2.  <span data-ttu-id="7fb34-113">開啟文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="7fb34-113">Open a text editor.</span></span> <span data-ttu-id="7fb34-114">在 [編輯] 功能表上，按一下 [貼上]。</span><span class="sxs-lookup"><span data-stu-id="7fb34-114">On the **Edit** menu, click **Paste**.</span></span> <span data-ttu-id="7fb34-115">您現在可以看到 XSD 路徑。</span><span class="sxs-lookup"><span data-stu-id="7fb34-115">You can now see the XSD path.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7fb34-116">或者，您可以按下 CTRL+V 以在文字編輯器中貼上路徑。</span><span class="sxs-lookup"><span data-stu-id="7fb34-116">Alternatively, you can press CTRL+V to paste the path in a text editor.</span></span>  
  
     <span data-ttu-id="7fb34-117">下面的程式碼顯示所選取結構描述節點的 XSD 路徑。</span><span class="sxs-lookup"><span data-stu-id="7fb34-117">The code below displays the XSD path for the selected schema node.</span></span>  
  
    ```  
    /*[local-name()='<Schema>']/*[local-name()='Shipment']/*[local-name()='DataCollection']  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7fb34-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fb34-118">See Also</span></span>  
 <span data-ttu-id="7fb34-119">[使用 BizTalk 對應工具中的增強的功能](../core/using-enhanced-features-in-biztalk-mapper.md) </span><span class="sxs-lookup"><span data-stu-id="7fb34-119">[Using Enhanced Features in BizTalk Mapper](../core/using-enhanced-features-in-biztalk-mapper.md) </span></span>  
 <span data-ttu-id="7fb34-120">[如何取代結構描述](../core/how-to-replace-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="7fb34-120">[How to Replace Schemas](../core/how-to-replace-schemas.md) </span></span>  
 <span data-ttu-id="7fb34-121">[如何展開和摺疊結構描述樹狀結構](https://msdn.microsoft.com/library/ee253802(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="7fb34-121">[How to Expand and Collapse the Schema Trees](https://msdn.microsoft.com/library/ee253802(v=bts.10).aspx)</span></span>