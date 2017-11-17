---
title: "XSD 的角色 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1fe08f6b-563f-4bae-a5be-551e487b2a6d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ad2f99b60de5ebb2a3cd7e102a2f3f7b787d1ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="role-of-xsd"></a><span data-ttu-id="9b676-102">XSD 的角色</span><span class="sxs-lookup"><span data-stu-id="9b676-102">Role of XSD</span></span>
<span data-ttu-id="9b676-103">XML 結構描述定義 (XSD) 語言提供在 BizTalk 中定義之訊息結構描述的基礎語法。</span><span class="sxs-lookup"><span data-stu-id="9b676-103">The XML Schema definition (XSD) language provides the underlying syntax of the message schemas defined within BizTalk.</span></span> <span data-ttu-id="9b676-104">雖然 BizTalk 編輯器和 BizTalk 對應工具中的樹狀檢視會使用記錄和欄位節點 (在其他類型節點之間) 之 BizTalk 特定的圖形階層，但其各自的屬性集 (如階層) 均是以 XSD 建構與保存。</span><span class="sxs-lookup"><span data-stu-id="9b676-104">Although the tree views in BizTalk Editor and BizTalk Mapper use a BizTalk-specific graphical hierarchy of record and field nodes (among other types of nodes), each with its own set of properties, such hierarchies are constructed and persisted as XSD.</span></span> <span data-ttu-id="9b676-105">BizTalk 編輯器會提供唯讀 XSD 檢視，您可以在其中看到建構為各種節點的 XSD 新增至樹狀檢視中之結構描述的圖形表示法中，或是從中移除，以及與那些節點相關之屬性值的變更。</span><span class="sxs-lookup"><span data-stu-id="9b676-105">BizTalk Editor provides a read-only XSD view in which you can see the XSD that is constructed as various nodes are added to or removed from the graphic representation of the schema in the tree view, and as the values of the properties associated with those nodes are changed.</span></span> <span data-ttu-id="9b676-106">雖然通常不需要了解 XSD 的細節即能以 BizTalk 編輯器成功建構簡單結構描述，但若您要在樹狀檢視中對結構描述階層進行變更時研究 XSD 變更，那麼您將要學習使用 XSD。</span><span class="sxs-lookup"><span data-stu-id="9b676-106">Although it is usually not necessary to understand the details of XSD to successfully construct simple schemas with BizTalk Editor, if you study the XSD changes as you make changes to the schema hierarchy in the tree view, you will learn to use XSD.</span></span>  
  
 <span data-ttu-id="9b676-107">XSD 中的結構描述註解功能 (BizTalk Server 所定義的大量註解集) 可有效地擴充 XSD，以支援表示非 XML 訊息 (如一般檔案) 的必要語法。</span><span class="sxs-lookup"><span data-stu-id="9b676-107">The schema annotation feature within XSD, with the extensive set of annotations defined by BizTalk Server, effectively allows XSD to be extended to support the necessary semantics for representing non-XML messages such as flat files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b676-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b676-108">See Also</span></span>  
 <span data-ttu-id="9b676-109">[在網站上的 XSD 資源](../core/xsd-resources-on-the-web.md) </span><span class="sxs-lookup"><span data-stu-id="9b676-109">[XSD Resources on the Web](../core/xsd-resources-on-the-web.md) </span></span>  
 [<span data-ttu-id="9b676-110">關於結構描述</span><span class="sxs-lookup"><span data-stu-id="9b676-110">About Schemas</span></span>](../core/about-schemas.md)