---
title: 關於對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- file types, maps
- BizTalk Mapper
- maps, file type
- maps, about maps
- BizTalk Mapper, about BizTalk Mapper
- maps
ms.assetid: 512ef2b7-3d01-4fcf-bb38-de68ec608b07
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd27793be4f1b1d9fd2b404f9a2a3a678b7622b2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966279"
---
# <a name="about-maps"></a><span data-ttu-id="519d9-102">關於對應</span><span class="sxs-lookup"><span data-stu-id="519d9-102">About Maps</span></span>
<span data-ttu-id="519d9-103">您可使用 [BizTalk 對應工具]，利用連結和運算質定義輸入和輸出結構描述之間的關係。</span><span class="sxs-lookup"><span data-stu-id="519d9-103">Using BizTalk Mapper, you define the relationship between an input and an output schema by using links and functoids.</span></span> <span data-ttu-id="519d9-104">連結定義記錄或欄位的直接資料複本。</span><span class="sxs-lookup"><span data-stu-id="519d9-104">A link defines a direct data copy of a record or field.</span></span> <span data-ttu-id="519d9-105">連結可以直接連接項目到另一個結構描述，也可以建立與運算質的連接。</span><span class="sxs-lookup"><span data-stu-id="519d9-105">Links may directly connect to items in the other schema, or they may form connections to functoids.</span></span> <span data-ttu-id="519d9-106">運算質可執行複雜的資料操作，例如：</span><span class="sxs-lookup"><span data-stu-id="519d9-106">Functoids perform more complex data manipulations, such as:</span></span>  
  
- <span data-ttu-id="519d9-107">在來源結構描述中新增兩個欄位的值，並將結果複製到目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="519d9-107">Adding the value of two fields in the source schema and copying the result to the destination schema.</span></span>  
  
- <span data-ttu-id="519d9-108">將字元轉換為其 ASCII 格式。</span><span class="sxs-lookup"><span data-stu-id="519d9-108">Converting a character to its ASCII format.</span></span>  
  
- <span data-ttu-id="519d9-109">傳回重複記錄中欄位的平均值，並將結果複製到目的結構描述中的欄位。</span><span class="sxs-lookup"><span data-stu-id="519d9-109">Returning the average of a field in a repeating record and copying the result to a field in the destination schema.</span></span>  
  
  <span data-ttu-id="519d9-110">[BizTalk 對應工具] 會將對應儲存到副檔名為 .btm 的檔案中。</span><span class="sxs-lookup"><span data-stu-id="519d9-110">BizTalk Mapper stores maps in a file with a .btm extension.</span></span> <span data-ttu-id="519d9-111">檔案會儲存對應的設計資訊，例如代表運算質之圖示的位置、結構描述項目與運算質之間的連結，以及對應的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="519d9-111">The file saves design information about the map—the locations of icons representing functoids, the links between schema items and functoids, and other information about the map.</span></span> <span data-ttu-id="519d9-112">建置或編譯對應時，[BizTalk 對應工具] 會將對應的相關資訊轉換為對應的「可延伸樣式表語言轉換」(XSLT) 樣式表。</span><span class="sxs-lookup"><span data-stu-id="519d9-112">When you build or compile the map, BizTalk Mapper converts the information about the map into the corresponding Extensible Language Stylesheet Transformations (XSLT) stylesheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="519d9-113">[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 編譯器在單一專案中，所有字串總大小的限制為 16 MB。</span><span class="sxs-lookup"><span data-stu-id="519d9-113">The [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] compiler has a 16-megabyte limitation on the total size of all strings in a single project.</span></span> <span data-ttu-id="519d9-114">在編譯 BizTalk 專案時，編譯器會序列化結構描述、對應和協調流程以建立組件，這樣便會增加所有字串的總大小，進而可能超過限制。</span><span class="sxs-lookup"><span data-stu-id="519d9-114">While compiling BizTalk projects, the compiler serializes schemas, maps, and orchestrations for creating the assemblies, and this increases the total size of all strings, which may exceed the limitation.</span></span> <span data-ttu-id="519d9-115">若要解決這個問題，您可以將結構描述和/或對應放入不同的 Biztalk 專案 (通常在相同的方案之下) 來重新組織專案，讓每個專案中所有字串的總大小不超過 16 MB。</span><span class="sxs-lookup"><span data-stu-id="519d9-115">To resolve this issue, you can reorganize your project by putting schemas and/or maps into different Biztalk projects (Typically, under the same solution), such that  the total size of all strings in each project is less than 16 MB.</span></span>  
  
 <span data-ttu-id="519d9-116">您建立的對應可以轉換或轉譯資料，而這些對應可專用於單一交易夥伴，或是用於多個交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="519d9-116">The maps that you create can transform or translate data, and they can be specific to a single trading partner or be used with many trading partners.</span></span> <span data-ttu-id="519d9-117">本節中的主題介紹與對應結構描述相關的概念。</span><span class="sxs-lookup"><span data-stu-id="519d9-117">The topics in this section provide an introduction to the concepts involved in mapping schemas.</span></span> <span data-ttu-id="519d9-118">如需地圖的背景資訊，請參閱 <<c0> [ 對應](../core/maps.md)。</span><span class="sxs-lookup"><span data-stu-id="519d9-118">For background information about maps, see [Maps](../core/maps.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="519d9-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="519d9-119">In This Section</span></span>  
  
-   [<span data-ttu-id="519d9-120">對應中的連結</span><span class="sxs-lookup"><span data-stu-id="519d9-120">Links in Maps</span></span>](../core/links-in-maps.md)  
  
-   [<span data-ttu-id="519d9-121">對應中的運算質</span><span class="sxs-lookup"><span data-stu-id="519d9-121">Functoids in Maps</span></span>](../core/functoids-in-maps.md)  
  
-   [<span data-ttu-id="519d9-122">對應編譯和測試</span><span class="sxs-lookup"><span data-stu-id="519d9-122">Map Compilation and Testing</span></span>](../core/map-compilation-and-testing.md)