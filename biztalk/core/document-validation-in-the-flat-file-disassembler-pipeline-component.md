---
title: 文件中的一般檔案解譯器管線元件的驗證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Validate Document Structure property
- FFDasm.ValidateDocumentStructure property
- Flat File Disassembler [pipeline component], validating documents
- pipeline components, Flat File Disassembler
ms.assetid: 8cd777e4-8aba-4c17-92e8-958e5dd57d09
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 120d4664f922a653d0d532ca25213f3cb60a4e67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239414"
---
# <a name="document-validation-in-the-flat-file-disassembler-pipeline-component"></a><span data-ttu-id="6a9bc-102">一般檔案解譯器管線元件中的文件驗證</span><span class="sxs-lookup"><span data-stu-id="6a9bc-102">Document Validation in the Flat File Disassembler Pipeline Component</span></span>
<span data-ttu-id="6a9bc-103">依照預設，「一般檔案解譯器」元件不會驗證它所處理的文件。</span><span class="sxs-lookup"><span data-stu-id="6a9bc-103">By default, the Flat File Disassembler component does not validate documents it processes.</span></span> <span data-ttu-id="6a9bc-104">不過，您可以將驗證設定**驗證文件結構**到元件上的屬性**True**，或藉由設定**FFDasm.ValidateDocumentStructure**訊息內容屬性來**True**。</span><span class="sxs-lookup"><span data-stu-id="6a9bc-104">However, you can turn validation on by setting the **Validate document structure** property on the component to **True**, or by setting the **FFDasm.ValidateDocumentStructure** message context property to **True**.</span></span> <span data-ttu-id="6a9bc-105">當文件驗證設定為執行時，「一般檔案解譯器」會驗證文件結構以及標頭與結尾結構，以確定它們符合文件、標頭與結尾結構描述。</span><span class="sxs-lookup"><span data-stu-id="6a9bc-105">When document validation is set to run, the Flat File Disassembler validates the document structure as well as the header and trailer structures to ensure that they conform to the document, header, and trailer schemas.</span></span>  
  
 <span data-ttu-id="6a9bc-106">一般檔案解譯器 」 可以移除空白欄位，而且會記錄何時**suppress_empty_nodes ="True"** 所指定**schemaInfo**一般檔案 XSD 結構描述中的註解。</span><span class="sxs-lookup"><span data-stu-id="6a9bc-106">The Flat File Disassembler can remove empty fields and records when **suppress_empty_nodes="True"** is specified by the **schemaInfo** annotation in the flat file XSD schema.</span></span> <span data-ttu-id="6a9bc-107">如果您使用**schemaInfo**註釋，如此一來，一般檔案解譯器會移除空的欄位和記錄，無論是否為選擇性。</span><span class="sxs-lookup"><span data-stu-id="6a9bc-107">If you use the **schemaInfo** annotation in this way, the Flat File Disassembler removes empty fields and records regardless of whether they are optional.</span></span> <span data-ttu-id="6a9bc-108">如果您使用 XML 驗證，這可能會造成驗證錯誤 (藉由設定一般檔案解譯器**驗證文件結構**屬性**True**或使用 XML 驗證器管線元件).</span><span class="sxs-lookup"><span data-stu-id="6a9bc-108">This may cause validation errors if you use XML validation (either by setting the Flat File Disassembler **Validate document structure** property to **True** or by using the XML Validator pipeline component).</span></span> <span data-ttu-id="6a9bc-109">若發生驗證錯誤，將擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="6a9bc-109">If a validation error occurs, the message is suspended.</span></span> <span data-ttu-id="6a9bc-110">如需 suppress_empty_nodes 屬性的詳細資訊，請參閱[其他一般檔案屬性](../core/additional-flat-file-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6a9bc-110">For more information about the suppress_empty_nodes property, see [Additional Flat File Properties](../core/additional-flat-file-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a9bc-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a9bc-111">See Also</span></span>  
 <span data-ttu-id="6a9bc-112">[一般檔案解譯器管線元件](../core/flat-file-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="6a9bc-112">[Flat File Disassembler Pipeline Component](../core/flat-file-disassembler-pipeline-component.md) </span></span>  
 <span data-ttu-id="6a9bc-113">[如何設定一般檔案解譯器管線元件](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="6a9bc-113">[How to Configure the Flat File Disassembler Pipeline Component](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="6a9bc-114">管線 AssemblerDisassembler （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="6a9bc-114">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)