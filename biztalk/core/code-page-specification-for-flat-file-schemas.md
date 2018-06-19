---
title: 程式碼頁規格，如一般檔案結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 825e75f1-893c-4c61-b566-f893d732a907
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64d5cfbc960346e702ed0d4a39ca74bbc4b3634c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232262"
---
# <a name="code-page-specification-for-flat-file-schemas"></a><span data-ttu-id="86b04-102">一般檔案結構描述的字碼頁規格</span><span class="sxs-lookup"><span data-stu-id="86b04-102">Code Page Specification for Flat File Schemas</span></span>

## <a name="overview"></a><span data-ttu-id="86b04-103">概觀</span><span class="sxs-lookup"><span data-stu-id="86b04-103">Overview</span></span>
<span data-ttu-id="86b04-104">中的值**字碼頁**屬性用來建立的反組譯碼和組件的一般檔案文件期間所使用的編碼物件。</span><span class="sxs-lookup"><span data-stu-id="86b04-104">The value in the **Code Page** property is used to create an encoding object that is used during the disassembly and assembly of flat file documents.</span></span> <span data-ttu-id="86b04-105">這個編碼物件允許一般檔案剖析器將輸入一般檔案文件的原生編碼主轉換為 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在內部使用的正規化 UTF-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="86b04-105">This encoding object allows the flat file parser to convert the native encoding of an inbound flat file document into the normalized UTF-8 encoding that is used internally by Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="86b04-106">這個編碼物件也允許一般檔案序列化程式將內部 UTF-8 編碼轉換回一般檔案文件的原生編碼。</span><span class="sxs-lookup"><span data-stu-id="86b04-106">The encoding object also allows the flat file serializer to convert the internal UTF-8 encoding back into the native encoding of the flat file document.</span></span>  
  
 <span data-ttu-id="86b04-107">設定**字碼頁**屬性扮演重要的是，但不是唯一，角色中決定一般檔案商務文件所使用的字元編碼配置。</span><span class="sxs-lookup"><span data-stu-id="86b04-107">The setting of the **Code Page** property plays an important, but not exclusive, role in determining the character encoding scheme used by your flat file business documents.</span></span> <span data-ttu-id="86b04-108">您必須考慮由一般檔案解譯器解譯輸入一般檔案訊息的方式，以及一般檔案組合器將字元編碼為轉譯至一般檔案格式之輸出訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="86b04-108">You must consider how inbound flat file messages are interpreted by the flat file disassembler as well as how the flat file assembler will encode characters as outbound messages are translated into flat file format.</span></span>  

## <a name="character-encoding"></a><span data-ttu-id="86b04-109">字元編碼</span><span class="sxs-lookup"><span data-stu-id="86b04-109">Character encoding</span></span>  
 <span data-ttu-id="86b04-110">在決定如何處理指定執行個體訊息之字元編碼的方式時，有多個因素扮演重要的角色，如下所示：</span><span class="sxs-lookup"><span data-stu-id="86b04-110">There are multiple factors that play a role in determining how character encoding for a given instance message is handled, as follows:</span></span>  
  
-   <span data-ttu-id="86b04-111">當解譯一般檔案執行個體訊息時，會使用下列演算法來決定並保留編碼資訊：</span><span class="sxs-lookup"><span data-stu-id="86b04-111">When disassembling a flat file instance message, the following algorithm is used to determine and preserve encoding information:</span></span>  
  
    1.  <span data-ttu-id="86b04-112">如果**Charset**在訊息內文部分是設定，則會使用該值。</span><span class="sxs-lookup"><span data-stu-id="86b04-112">If the **Charset** in the Message body part is set, its value is used.</span></span>  
  
    2.  <span data-ttu-id="86b04-113">否則，如果信封 （或文件） 結構描述指定使用程式碼頁面**字碼頁**使用屬性，其值。</span><span class="sxs-lookup"><span data-stu-id="86b04-113">Otherwise, if the envelope (or document) schema specifies a code page using the **Code Page** property, its value is used.</span></span>  
  
    3.  <span data-ttu-id="86b04-114">或者，若位元順序標記存在，則會使用它的值。</span><span class="sxs-lookup"><span data-stu-id="86b04-114">Otherwise, if a byte order mark is present, its value is used.</span></span>  
  
    4.  <span data-ttu-id="86b04-115">或者，使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="86b04-115">Otherwise, assume UTF-8.</span></span>  
  
-   <span data-ttu-id="86b04-116">當組合一般檔案執行個體訊息時，會使用下列演算法來決定供解碼使用的字元集：</span><span class="sxs-lookup"><span data-stu-id="86b04-116">When assembling a flat file instance message, the following algorithm is used to determine the character set to use for decoding:</span></span>  
  
-   <span data-ttu-id="86b04-117">如果**XMLNorm.TargetCharset**訊息內容屬性設定，則會使用該值。</span><span class="sxs-lookup"><span data-stu-id="86b04-117">If the **XMLNorm.TargetCharset** message context property is set, its value is used.</span></span>  
  
-   <span data-ttu-id="86b04-118">否則，如果 **[TargetCharset**組譯工具 （設計階段） 屬性設定，則會使用該值。</span><span class="sxs-lookup"><span data-stu-id="86b04-118">Otherwise, if the **TargetCharset** assembler (design-time) property is set, its value is used.</span></span>  
  
-   <span data-ttu-id="86b04-119">否則，如果信封 （或文件） 結構描述指定使用程式碼頁面**字碼頁**使用屬性，其值。</span><span class="sxs-lookup"><span data-stu-id="86b04-119">Otherwise, if the envelope (or document) schema specifies a code page using the **Code Page** property, its value is used.</span></span>  
  
    1.  <span data-ttu-id="86b04-120">否則，如果**SourceCharset**訊息內容屬性設定，則會使用該值。</span><span class="sxs-lookup"><span data-stu-id="86b04-120">Otherwise, if the **SourceCharset** message context property is set, its value is used.</span></span>  
  
    2.  <span data-ttu-id="86b04-121">或者，使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="86b04-121">Otherwise, use UTF-8.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86b04-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86b04-122">See Also</span></span>  
 <span data-ttu-id="86b04-123">**考量當建立一般檔案訊息結構描述**和**字碼頁 （一般檔案結構描述中的節點屬性）**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="86b04-123">**Considerations When Creating Flat File Message Schemas** and **Code Page (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>