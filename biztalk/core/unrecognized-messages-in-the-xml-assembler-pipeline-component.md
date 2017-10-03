---
title: "無法辨識的訊息，在 XML 組合器管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XMLNorm.AllowUnrecognizedMessage property
- XML Assembler [pipeline component], unrecognized messages
- pipeline components, XML Assembler
ms.assetid: dd98512a-33a4-4b2e-977e-1b3a30747c6a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6766554374413c3d1b6a3ce385f24d4046521c91
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unrecognized-messages-in-the-xml-assembler-pipeline-component"></a><span data-ttu-id="a6b84-102">XML 組合器管線元件中無法辨識的訊息</span><span class="sxs-lookup"><span data-stu-id="a6b84-102">Unrecognized Messages in the XML Assembler Pipeline Component</span></span>
<span data-ttu-id="a6b84-103">如果訊息發生下列情況，則 XML 組合器元件會將訊息視為「無法辨識」：</span><span class="sxs-lookup"><span data-stu-id="a6b84-103">The XML Assembler component treats a message as "unrecognized" if a message has:</span></span>  
  
-   <span data-ttu-id="a6b84-104">沒有內文部分。</span><span class="sxs-lookup"><span data-stu-id="a6b84-104">No body part.</span></span>  
  
-   <span data-ttu-id="a6b84-105">空的內文部分。</span><span class="sxs-lookup"><span data-stu-id="a6b84-105">An empty body part.</span></span>  
  
-   <span data-ttu-id="a6b84-106">內文部分中沒有資料。</span><span class="sxs-lookup"><span data-stu-id="a6b84-106">No data in the body part.</span></span>  
  
-   <span data-ttu-id="a6b84-107">未部署相關聯的結構描述。</span><span class="sxs-lookup"><span data-stu-id="a6b84-107">No associated schema deployed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6b84-108">非 XML 訊息一律視為無法辨識。</span><span class="sxs-lookup"><span data-stu-id="a6b84-108">Non-XML messages are always treated as unrecognized.</span></span>  
  
 <span data-ttu-id="a6b84-109">XML 組合器處理無法辨識的訊息的方式由**XMLNorm.AllowUnrecognizedMessage**訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="a6b84-109">The manner in which the XML Assembler handles an unrecognized message is controlled by the **XMLNorm.AllowUnrecognizedMessage** message context property.</span></span>  
  
 <span data-ttu-id="a6b84-110">當**XMLNorm.AllowUnrecognizedMessage**設**True**，XML 組合器處理 XML 文件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a6b84-110">When **XMLNorm.AllowUnrecognizedMessage** is set to **True**, the XML Assembler handles XML documents as follows:</span></span>  
  
-   <span data-ttu-id="a6b84-111">透過組合器並以原狀傳遞沒有內文部分或具有空白內容部分或空白資料的訊息。</span><span class="sxs-lookup"><span data-stu-id="a6b84-111">A message with no body part or with an empty body part or empty data in the body part passes unchanged through the assembler.</span></span>  
  
-   <span data-ttu-id="a6b84-112">透過組合器並以原狀傳遞未部署與其相關聯之結構描述的文件。</span><span class="sxs-lookup"><span data-stu-id="a6b84-112">A document that does not have a deployed schema associated with it passes unchanged through the assembler.</span></span>  
  
-   <span data-ttu-id="a6b84-113">不論是在元件屬性中明確參考結構描述，或是在結構描述解析程序期間找到結構描述，都會透過組合器來處理具有相關聯之部署結構描述的文件。</span><span class="sxs-lookup"><span data-stu-id="a6b84-113">A document with an associated deployed schema is processed by the assembler (regardless of whether the schema is explicitly referenced in a component property or found during the schema resolution process).</span></span>  
  
 <span data-ttu-id="a6b84-114">如果**XMLNorm.AllowUnrecognizedMessage**設**False**，XML 組合器處理 XML 文件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a6b84-114">If **XMLNorm.AllowUnrecognizedMessage** is set to **False**, the XML Assembler handles XML documents as follows:</span></span>  
  
-   <span data-ttu-id="a6b84-115">不會處理沒有內文部分或具有空白內容部分或空白資料的訊息。</span><span class="sxs-lookup"><span data-stu-id="a6b84-115">A message with no body part or with an empty body part or empty data in the body part is not processed.</span></span> <span data-ttu-id="a6b84-116">會報告錯誤，並擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="a6b84-116">An error is reported and the message is suspended.</span></span>  
  
-   <span data-ttu-id="a6b84-117">不會處理未部署與其相關聯之結構描述的訊息。</span><span class="sxs-lookup"><span data-stu-id="a6b84-117">A message that does not have a deployed schema associated with it is not processed.</span></span> <span data-ttu-id="a6b84-118">會報告錯誤，並擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="a6b84-118">An error is reported and the message is suspended.</span></span>  
  
-   <span data-ttu-id="a6b84-119">不論是在元件屬性中明確參考結構描述，或是在結構描述解析程序期間找到結構描述，都會透過組合器來處理具有相關聯之部署結構描述的文件。</span><span class="sxs-lookup"><span data-stu-id="a6b84-119">A document with an associated deployed schema is processed by the assembler (regardless of whether the schema is explicitly referenced in a component property or found during the schema resolution process).</span></span>  
  
-   <span data-ttu-id="a6b84-120">根據預設，XML 組合器元件不允許無法辨識的訊息 (也就是**XMLNorm.AllowUnrecognizedMessages**會被視為**False**如果未設定在訊息內容)。</span><span class="sxs-lookup"><span data-stu-id="a6b84-120">By default, the XML Assembler component does not allow unrecognized messages (that is, **XMLNorm.AllowUnrecognizedMessages** is considered **False** if it is not set on the message context).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6b84-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6b84-121">See Also</span></span>  
 <span data-ttu-id="a6b84-122">[XML 組合器管線元件](../core/xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="a6b84-122">[XML Assembler Pipeline Component](../core/xml-assembler-pipeline-component.md) </span></span>  
 <span data-ttu-id="a6b84-123">[如何設定 XML 組合器管線元件](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="a6b84-123">[How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="a6b84-124">管線 AssemblerDisassembler （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="a6b84-124">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)