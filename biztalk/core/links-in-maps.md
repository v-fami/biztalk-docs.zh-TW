---
title: "對應中的連結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoid types, Looping
- Looping functoids
- maps, links
- BizTalk Mapper, links
ms.assetid: 3db77b8d-7b86-4c00-99a0-0513aff9b56b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a32d2a9ef07cf2d79037d7983e49b26c6cfe5e81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="links-in-maps"></a><span data-ttu-id="120cb-102">對應中的連結</span><span class="sxs-lookup"><span data-stu-id="120cb-102">Links in Maps</span></span>
<span data-ttu-id="120cb-103">連結指定將輸入執行個體訊息中項目或屬性的資料複製到輸出執行個體中項目或屬性的基本功能。</span><span class="sxs-lookup"><span data-stu-id="120cb-103">Links specify the basic function of copying data from an element or attribute in an input instance message to an element or attribute in an output instance.</span></span> <span data-ttu-id="120cb-104">在設計階設建立來源與目的結構描述中的記錄與欄位之間的連結。</span><span class="sxs-lookup"><span data-stu-id="120cb-104">You create links between records and fields in the source and destination schemas at design time.</span></span> <span data-ttu-id="120cb-105">如此一來會在執行階段從符合來源結構描述的輸入執行個體訊息，建立符合目的結構描述的輸出執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="120cb-105">This drives the creation, at run time, of an output instance message conforming to the destination schema from an input instance message conforming to the source schema.</span></span>  
  
 <span data-ttu-id="120cb-106">BizTalk 對應工具支援一對一連結與一對多連結。</span><span class="sxs-lookup"><span data-stu-id="120cb-106">BizTalk Mapper supports one-to-one links and one-to-many links.</span></span> <span data-ttu-id="120cb-107">例如，連結可以連接來源結構描述的單一記錄或欄位與目的結構描述的單一記錄或欄位。</span><span class="sxs-lookup"><span data-stu-id="120cb-107">For example, a link can connect a single record or field from the source schema to a single record or field in the destination schema.</span></span> <span data-ttu-id="120cb-108">連結也可以連接來源結構描述的單一記錄或欄位與目的結構描述的多個記錄或欄位。</span><span class="sxs-lookup"><span data-stu-id="120cb-108">A link can also connect a single record or field from the source schema to multiple records or fields in the destination schema.</span></span>  
  
 <span data-ttu-id="120cb-109">連結也可以將來源結構描述的多個記錄或欄位連結到運算質，然後再連接到目的結構描述的單一 (或多個) 記錄和 (或) 欄位。</span><span class="sxs-lookup"><span data-stu-id="120cb-109">Links can also connect multiple records or fields from the source schema to a functoid, which then connects to a single (or multiple) record(s) and/or field(s) in the destination schema.</span></span> <span data-ttu-id="120cb-110">一般而言，多個來源記錄或欄位與單一目的記錄或欄位的直接連結不是有效的，而且會產生警告。</span><span class="sxs-lookup"><span data-stu-id="120cb-110">In general, direct links from multiple source records or fields to a single destination record or field are not valid and produce a warning.</span></span> <span data-ttu-id="120cb-111">一個例外狀況是**迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="120cb-111">One exception to this is the **Looping** functoid.</span></span> <span data-ttu-id="120cb-112">如需有關**迴圈**運算質，請參閱[迴圈 」 運算質](../core/looping-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="120cb-112">For more information about the **Looping** functoid, see [Looping Functoid](../core/looping-functoid.md).</span></span>  
  
 <span data-ttu-id="120cb-113">本節中的主題描述 BizTalk 對應工具中建立和使用連結的相關概念。</span><span class="sxs-lookup"><span data-stu-id="120cb-113">The topics in this section describe concepts related to creating and working with links in BizTalk Mapper.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="120cb-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="120cb-114">In This Section</span></span>  
  
-   [<span data-ttu-id="120cb-115">連結類型</span><span class="sxs-lookup"><span data-stu-id="120cb-115">Types of Links</span></span>](../core/types-of-links.md)  
  
-   [<span data-ttu-id="120cb-116">建立連結</span><span class="sxs-lookup"><span data-stu-id="120cb-116">Creating Links</span></span>](../core/creating-links.md)  
  
-   [<span data-ttu-id="120cb-117">設定連結</span><span class="sxs-lookup"><span data-stu-id="120cb-117">Configuring Links</span></span>](../core/configuring-links.md)  
  
-   [<span data-ttu-id="120cb-118">記錄對記錄連結</span><span class="sxs-lookup"><span data-stu-id="120cb-118">Record-to-Record Linking</span></span>](../core/record-to-record-linking.md)  
  
-   [<span data-ttu-id="120cb-119">連結和從 Any 項目與 anyAttribute 節點</span><span class="sxs-lookup"><span data-stu-id="120cb-119">Links To and From the Any Element and anyAttribute Nodes</span></span>](../core/links-to-and-from-the-any-element-and-anyattribute-nodes.md)  
  
-   [<span data-ttu-id="120cb-120">編譯器指示詞和連結</span><span class="sxs-lookup"><span data-stu-id="120cb-120">Compiler Directives and Links</span></span>](../core/compiler-directives-and-links.md)