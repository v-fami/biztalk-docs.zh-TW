---
title: 一般檔案組合器管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components, Flat File Assembler
- Flat File Assembler [pipeline component]
ms.assetid: 3c851771-55b2-4d21-9291-d707dd66837c
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 385b1f8ea6c2ce707069cde522ea2f6712290be7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245862"
---
# <a name="flat-file-assembler-pipeline-component"></a><span data-ttu-id="3cd9e-102">一般檔案組合器管線元件</span><span class="sxs-lookup"><span data-stu-id="3cd9e-102">Flat File Assembler Pipeline Component</span></span>
<span data-ttu-id="3cd9e-103">一般檔案組合器將個別文件組合成一批檔案，並可以選擇是否在上面加入標頭或結尾 (或兩者)。</span><span class="sxs-lookup"><span data-stu-id="3cd9e-103">A Flat File Assembler combines individual documents into a batch and optionally adds a header or trailer (or both) to it.</span></span> <span data-ttu-id="3cd9e-104">如需一般檔案的詳細資訊，請參閱[具有分隔記錄的一般檔案訊息](../core/flat-file-messages-with-delimited-records.md)。</span><span class="sxs-lookup"><span data-stu-id="3cd9e-104">For more information about flat files, see [Flat File Messages with Delimited Records](../core/flat-file-messages-with-delimited-records.md).</span></span> <span data-ttu-id="3cd9e-105">另請參閱[具有位置記錄的一般檔案訊息](../core/flat-file-messages-with-positional-records.md)。</span><span class="sxs-lookup"><span data-stu-id="3cd9e-105">Also see [Flat File Messages with Positional Records](../core/flat-file-messages-with-positional-records.md).</span></span>  
  
 <span data-ttu-id="3cd9e-106">一般檔案組合器管線元件不會驗證內送的 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="3cd9e-106">The Flat File Assembler pipeline component does not validate the incoming XML message.</span></span> <span data-ttu-id="3cd9e-107">若要確認 XML 驗證，請在傳送管線的預先組合階段中包含 XML 驗證器元件。</span><span class="sxs-lookup"><span data-stu-id="3cd9e-107">To ensure XML validation, include the XML Validator component in the Pre-Assemble stage of the send pipeline.</span></span>  
  
 <span data-ttu-id="3cd9e-108">一般檔案組合器管線元件僅支援 Microsoft .NET Framework 所支援的轉換。</span><span class="sxs-lookup"><span data-stu-id="3cd9e-108">The Flat File Assembler pipeline component only supports conversions supported by the Microsoft .NET Framework.</span></span> <span data-ttu-id="3cd9e-109">寫入自訂文字撰寫程式可以進行任何其他的轉換。</span><span class="sxs-lookup"><span data-stu-id="3cd9e-109">Any additional conversion can be done by writing to a custom text writer.</span></span>  
  
 <span data-ttu-id="3cd9e-110">設定一般檔案組合器管線元件的相關資訊，請參閱[如何設定一般檔案組合器管線元件](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="3cd9e-110">For information about configuring the Flat File Assembler pipeline component, see [How to Configure the Flat File Assembler Pipeline Component](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3cd9e-111">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，您無法將訊息組合到單一交換中。</span><span class="sxs-lookup"><span data-stu-id="3cd9e-111">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you cannot assemble messages into one interchange.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3cd9e-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="3cd9e-112">In This Section</span></span>  
  
-   [<span data-ttu-id="3cd9e-113">一般檔案組合器管線元件中的字元編碼</span><span class="sxs-lookup"><span data-stu-id="3cd9e-113">Character Encoding in the Flat File Assembler Pipeline Component</span></span>](../core/character-encoding-in-the-flat-file-assembler-pipeline-component.md)  
  
-   [<span data-ttu-id="3cd9e-114">一般檔案組合器管線元件中的文件結構強化</span><span class="sxs-lookup"><span data-stu-id="3cd9e-114">Document Structure Enforcement in the Flat File Assembler Pipeline Component</span></span>](../core/document-structure-enforcement-in-the-flat-file-assembler-pipeline-component.md)  
  
-   [<span data-ttu-id="3cd9e-115">保留一般檔案組合器管線元件中的分隔符號</span><span class="sxs-lookup"><span data-stu-id="3cd9e-115">Retaining Delimiters in the Flat File Assembler Pipeline Component</span></span>](../core/retaining-delimiters-in-the-flat-file-assembler-pipeline-component.md)