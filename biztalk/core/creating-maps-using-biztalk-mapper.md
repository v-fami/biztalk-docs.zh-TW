---
title: 使用 BizTalk 對應工具建立對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, maps
- maps, creating
- orchestrations, maps
- translations [maps]
- maps, about maps
- transformations [maps]
- maps
ms.assetid: 265e61d8-8cff-44c9-a717-8e895cb4b9bf
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c12da6732729052119bfcc7841424db6d0dcaff9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238334"
---
# <a name="creating-maps-using-biztalk-mapper"></a><span data-ttu-id="c7c6b-102">使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="c7c6b-102">Creating Maps Using BizTalk Mapper</span></span>
<span data-ttu-id="c7c6b-103">「BizTalk 對應工具」是在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 環境中執行的工具。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-103">BizTalk Mapper is a tool that runs within the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.</span></span> <span data-ttu-id="c7c6b-104">您可以使用 BizTalk 對應工具建立和編輯對應，以轉譯或轉換 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-104">BizTalk Mapper can be used to create and edit maps, which are used for translating or transforming xml messages.</span></span> <span data-ttu-id="c7c6b-105">對應可以用於協調流程 (如下圖所示)，也可以用於處理接收埠所接收的訊息，接著加以轉換然後透過傳送埠傳送出去。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-105">Maps are used in orchestrations, as the following figure suggest, and can also be used for processing messages received at a receive port, and then transforming the message to be sent via send port(s).</span></span>  
  
 <span data-ttu-id="c7c6b-106">![當對應的商務處理圖表。] (../core/media/ebiz-dev-busprcsg.gif "ebiz_dev_busprcsg")</span><span class="sxs-lookup"><span data-stu-id="c7c6b-106">![Business processing diagram with maps.](../core/media/ebiz-dev-busprcsg.gif "ebiz_dev_busprcsg")</span></span>  
<span data-ttu-id="c7c6b-107">商務處理中的對應</span><span class="sxs-lookup"><span data-stu-id="c7c6b-107">Maps in Business Processing</span></span>  
  
 <span data-ttu-id="c7c6b-108">對應可讓您轉譯和轉換訊息。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-108">Maps enable you to translate and to transform messages.</span></span> <span data-ttu-id="c7c6b-109">轉譯是將訊息從一種格式轉換為另一種格式的程序，例如將一般檔案轉換為 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-109">Translation is the process of converting a message from one format to another format, such as converting a flat file into an XML file.</span></span> <span data-ttu-id="c7c6b-110">轉換則是擷取某個訊息中的資訊，並將該資訊插入另一個訊息的程序。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-110">Transformation is the process of taking information from one message and inserting it in another message.</span></span> <span data-ttu-id="c7c6b-111">例如，您可以擷取採購單中的送貨和帳單地址，並將這些地址插入發票文件。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-111">For example, you might take shipping and billing addresses from a purchase order and insert them in an invoice document.</span></span>  
  
 <span data-ttu-id="c7c6b-112">「BizTalk 對應工具」使用專屬的圖示和連結圖形系統，代表從輸入執行個體訊息到輸出執行個體訊息的轉譯和轉換關係。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-112">BizTalk Mapper uses its own graphical system of icons and links to represent the translation and transformation of input instance messages to output instance messages.</span></span> <span data-ttu-id="c7c6b-113">對應工具使用與 BizTalk 編輯器相同的結構描述圖形表示法。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-113">Mapper uses the same graphical representation of schemas as BizTalk Editor.</span></span> <span data-ttu-id="c7c6b-114">「BizTalk 對應工具」會將其對應儲存為「可延伸樣式表語言轉換」(XSLT) 樣式表。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-114">BizTalk Mapper stores its maps as Extensible Stylesheet Language Transformations (XSLT) stylesheets.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7c6b-115">BizTalk 對應工具支援 XSLT 1.0。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-115">BizTalk Mapper supports XSLT 1.0.</span></span> <span data-ttu-id="c7c6b-116">在 [BizTalk 對應工具] 中不支援使用 XSLT 2.0。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-116">Using XSLT 2.0 in BizTalk Mapper is not supported.</span></span>  
  
 <span data-ttu-id="c7c6b-117">如需建立結構描述資訊，請參閱[建立結構描述使用 BizTalk 編輯器](../core/creating-schemas-using-biztalk-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-117">For information about creating schemas, see [Creating Schemas Using BizTalk Editor](../core/creating-schemas-using-biztalk-editor.md).</span></span> <span data-ttu-id="c7c6b-118">如需使用協調流程中的對應資訊，請參閱[協調流程使用協調流程設計師建立](../core/creating-orchestrations-using-orchestration-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-118">For information about using maps within orchestrations, see [Creating Orchestrations Using Orchestration Designer](../core/creating-orchestrations-using-orchestration-designer.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7c6b-119">對應的效能視對應的複雜度 (運算質的數目和類型)、輸入和輸出結構描述的大小、輸入訊息的大小以及您的硬體而異。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-119">The performance of a map depends on the complexity of the map - the number and type of functoids, size of input and output schemas, the size of the input message, and your hardware.</span></span>  
  
 <span data-ttu-id="c7c6b-120">使用 BizTalk 對應工具鍵盤快速鍵的相關資訊，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-120">For information about using the keyboard shortcuts for BizTalk Mapper, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7c6b-121">本節內容</span><span class="sxs-lookup"><span data-stu-id="c7c6b-121">In This Section</span></span>  
  
-   [<span data-ttu-id="c7c6b-122">規劃建立對應</span><span class="sxs-lookup"><span data-stu-id="c7c6b-122">Planning to Create Maps</span></span>](../core/planning-to-create-maps.md)  
  
-   [<span data-ttu-id="c7c6b-123">關於對應</span><span class="sxs-lookup"><span data-stu-id="c7c6b-123">About Maps</span></span>](../core/about-maps.md)  
  
-   [<span data-ttu-id="c7c6b-124">使用 BizTalk 對應工具</span><span class="sxs-lookup"><span data-stu-id="c7c6b-124">Using BizTalk Mapper</span></span>](../core/using-biztalk-mapper.md)  
  
-   [<span data-ttu-id="c7c6b-125">建立對應</span><span class="sxs-lookup"><span data-stu-id="c7c6b-125">Creating Maps</span></span>](../core/creating-maps.md)  
  
-   [<span data-ttu-id="c7c6b-126">編譯和測試對應</span><span class="sxs-lookup"><span data-stu-id="c7c6b-126">Compiling and Testing Maps</span></span>](../core/compiling-and-testing-maps.md)  
  
-   [<span data-ttu-id="c7c6b-127">地圖疑難排解</span><span class="sxs-lookup"><span data-stu-id="c7c6b-127">Troubleshooting Maps</span></span>](../core/troubleshooting-maps.md)