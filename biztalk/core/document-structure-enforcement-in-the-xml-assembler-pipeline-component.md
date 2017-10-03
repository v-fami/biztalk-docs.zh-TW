---
title: "文件結構強化 XML 組合器管線元件中的 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add XML declaration property
- pipeline components, XML Assembler
ms.assetid: c121ec4b-c02b-4626-a5be-2937500dbefa
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e46dbc613439b24403c66c345b9023151b409213
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="document-structure-enforcement-in-the-xml-assembler-pipeline-component"></a><span data-ttu-id="d7337-102">XML 組合器管線元件中的文件結構強化</span><span class="sxs-lookup"><span data-stu-id="d7337-102">Document Structure Enforcement in the XML Assembler Pipeline Component</span></span>
<span data-ttu-id="d7337-103">若文件或信封結構描述在 XML 組合器中明確地被參照，則 XML 組合器可確保只有其訊息類型符合於參考結構描述的文件才會經過處理。</span><span class="sxs-lookup"><span data-stu-id="d7337-103">If document or envelope schemas are explicitly referenced in the XML Assembler, the XML Assembler ensures that only documents with the message type corresponding to referenced schemas are processed.</span></span> <span data-ttu-id="d7337-104">即使所有其他文件可能具有已部署的結構描述，還是不會處理這些文件。</span><span class="sxs-lookup"><span data-stu-id="d7337-104">All the other documents are not processed even though a schema may be deployed for them.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7337-105">信封結構描述僅取自第一則訊息。</span><span class="sxs-lookup"><span data-stu-id="d7337-105">The envelope schema is taken from the first message only.</span></span> <span data-ttu-id="d7337-106">信封的屬性固定取自第一則訊息。</span><span class="sxs-lookup"><span data-stu-id="d7337-106">The properties for the envelope are always taken from the first message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7337-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7337-107">See Also</span></span>  
 <span data-ttu-id="d7337-108">[XML 組合器管線元件](../core/xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="d7337-108">[XML Assembler Pipeline Component](../core/xml-assembler-pipeline-component.md) </span></span>  
 <span data-ttu-id="d7337-109">[如何設定 XML 組合器管線元件](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="d7337-109">[How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="d7337-110">管線 AssemblerDisassembler （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="d7337-110">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)