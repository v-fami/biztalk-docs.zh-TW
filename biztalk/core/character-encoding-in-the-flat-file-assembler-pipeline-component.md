---
title: 一般檔案組合器管線元件中的字元編碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Flat File Assembler [pipeline component], character encoding
- IBaseMessagePart.Charset property
- pipeline components, Flat File Assembler
- Codepage property
- XMLNorm.SourceCharset property
- XMLNorm.TargetCharset property
- Target Charset property
ms.assetid: 0cf3c0fd-f036-4190-83ce-9064ef4e823c
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af38855c81129cd4bafff50544f2aee15e6f3fab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232118"
---
# <a name="character-encoding-in-the-flat-file-assembler-pipeline-component"></a><span data-ttu-id="32dcb-102">一般檔案組合器管線元件中的字元編碼</span><span class="sxs-lookup"><span data-stu-id="32dcb-102">Character Encoding in the Flat File Assembler Pipeline Component</span></span>
<span data-ttu-id="32dcb-103">一般檔案組合器可用使用者指定的字元編碼產生訊息。</span><span class="sxs-lookup"><span data-stu-id="32dcb-103">The Flat File Assembler can produce messages in user-specified character encoding.</span></span> <span data-ttu-id="32dcb-104">您可以在數個層級中指定字元編碼：</span><span class="sxs-lookup"><span data-stu-id="32dcb-104">You can specify the character encoding at several levels:</span></span>  
  
-   <span data-ttu-id="32dcb-105">**結構描述。**</span><span class="sxs-lookup"><span data-stu-id="32dcb-105">**Schema.**</span></span> <span data-ttu-id="32dcb-106">設定**字碼頁**文件的一般檔案結構描述中的屬性。</span><span class="sxs-lookup"><span data-stu-id="32dcb-106">Set the **codepage** property in the flat file schema for the document.</span></span>  
  
-   <span data-ttu-id="32dcb-107">**元件。**</span><span class="sxs-lookup"><span data-stu-id="32dcb-107">**Component.**</span></span> <span data-ttu-id="32dcb-108">設定**目標字元集**管線設計師 」 中的元件屬性。</span><span class="sxs-lookup"><span data-stu-id="32dcb-108">Set the **Target Charset** component property in Pipeline Designer.</span></span>  
  
-   <span data-ttu-id="32dcb-109">**訊息。**</span><span class="sxs-lookup"><span data-stu-id="32dcb-109">**Message.**</span></span> <span data-ttu-id="32dcb-110">設定**XMLNorm.TargetCharset**在訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="32dcb-110">Set the **XMLNorm.TargetCharset** property on the message context.</span></span>  
  
 <span data-ttu-id="32dcb-111">在訊息內容中所設定的屬性值一律會覆寫在管線設計師中所設定的屬性值。</span><span class="sxs-lookup"><span data-stu-id="32dcb-111">The value of the property set on a message context always overrides the one set in Pipeline Designer.</span></span> <span data-ttu-id="32dcb-112">此外，一律在管線設計師 」 中設定的值會覆寫值設為**字碼頁**一般檔案文件結構描述中的屬性。</span><span class="sxs-lookup"><span data-stu-id="32dcb-112">Also, the value set in Pipeline Designer always overwrites the value set as a **codepage** property in a flat file document schema.</span></span>  
  
 <span data-ttu-id="32dcb-113">一般檔案組合器使用以下演算法以判斷將哪一種編碼用於輸出訊息：</span><span class="sxs-lookup"><span data-stu-id="32dcb-113">The Flat File Assembler uses the following algorithm to determine which encoding to use for an output message:</span></span>  
  
-   <span data-ttu-id="32dcb-114">如果**XMLNorm.TargetCharset**內容屬性設定，其值會用於編碼。</span><span class="sxs-lookup"><span data-stu-id="32dcb-114">If the **XMLNorm.TargetCharset** context property is set, its value is used for encoding.</span></span>  
  
-   <span data-ttu-id="32dcb-115">否則，如果**目標字元集**管線設計師 」 中的屬性已指定，則會使用該值。</span><span class="sxs-lookup"><span data-stu-id="32dcb-115">Otherwise, if the **Target charset** property in Pipeline Designer is specified, its value is used.</span></span>  
  
-   <span data-ttu-id="32dcb-116">否則，如果**字碼頁**一般檔案結構描述中的屬性已指定，則會使用該值。</span><span class="sxs-lookup"><span data-stu-id="32dcb-116">Otherwise, if the **codepage** property in the flat file schema is specified, its value is used.</span></span>  
  
-   <span data-ttu-id="32dcb-117">否則，如果**XMLNorm.SourceCharset**屬性已指定，則會使用該值。</span><span class="sxs-lookup"><span data-stu-id="32dcb-117">Otherwise, if the **XMLNorm.SourceCharset** property is specified, its value is used.</span></span>  
  
-   <span data-ttu-id="32dcb-118">或者，使用 "UTF-8"。</span><span class="sxs-lookup"><span data-stu-id="32dcb-118">Otherwise, "UTF-8" is used.</span></span> <span data-ttu-id="32dcb-119">請注意，使用 UTF-8 編碼時，一般檔案組合器管線元件不會在外寄訊息中加入位元順序標記。</span><span class="sxs-lookup"><span data-stu-id="32dcb-119">Note that the Flat File Assembler pipeline component does not put byte order mark on outgoing messages when UTF-8 encoding is used.</span></span>  
  
 <span data-ttu-id="32dcb-120">一般檔案組合器會將儲存編碼 BizTalk 訊息物件中的內文部分資訊**IBaseMessagePart.Charset**屬性。</span><span class="sxs-lookup"><span data-stu-id="32dcb-120">The Flat File Assembler saves encoding information on the body part of the BizTalk message object in the **IBaseMessagePart.Charset** property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32dcb-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32dcb-121">See Also</span></span>  
 <span data-ttu-id="32dcb-122">[一般檔案組合器管線元件](../core/flat-file-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="32dcb-122">[Flat File Assembler Pipeline Component](../core/flat-file-assembler-pipeline-component.md) </span></span>  
 <span data-ttu-id="32dcb-123">[如何設定一般檔案組合器管線元件](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="32dcb-123">[How to Configure the Flat File Assembler Pipeline Component](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="32dcb-124">管線 AssemblerDisassembler （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="32dcb-124">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)