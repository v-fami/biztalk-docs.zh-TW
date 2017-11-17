---
title: "如何設定一般檔案組合器管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, Flat File Assembler
- Flat File Assembler [pipeline component], configuring
- messages, flat files
ms.assetid: 5af61bba-4eb2-4bb9-a655-394a76d08d3b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7fe9c7a0720db68d8e629410dd3f0a443a99d7a4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-flat-file-assembler-pipeline-component"></a><span data-ttu-id="d4ebb-102">如何設定一般檔案組合器管線元件</span><span class="sxs-lookup"><span data-stu-id="d4ebb-102">How to Configure the Flat File Assembler Pipeline Component</span></span>
<span data-ttu-id="d4ebb-103">一般檔案組合器管線元件用以在 XML 文件從伺服器傳送出去前，先將 XML 文件序列化成分隔式或序數一般檔案格式。</span><span class="sxs-lookup"><span data-stu-id="d4ebb-103">The Flat File Assembler pipeline component is used to serialize an XML document into delimited or positional flat file format before sending it out of the server.</span></span>  
  
### <a name="to-configure-the-properties-for-the-flat-file-assembler-pipeline-component"></a><span data-ttu-id="d4ebb-104">設定一般檔案組合器管線元件的屬性</span><span class="sxs-lookup"><span data-stu-id="d4ebb-104">To configure the properties for the Flat File Assembler pipeline component</span></span>  
  
1.  <span data-ttu-id="d4ebb-105">將一般檔案組合器管線元件拖曳至傳送管線的組合階段。</span><span class="sxs-lookup"><span data-stu-id="d4ebb-105">Drag the Flat File Assembler pipeline component into the Assemble stage of the send pipeline.</span></span>  
  
2.  <span data-ttu-id="d4ebb-106">在 [屬性] 視窗中**管線元件屬性**區段中，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="d4ebb-106">In the Properties window, in the **Pipeline Component Properties** section, do the following.</span></span>  
  
    |<span data-ttu-id="d4ebb-107">使用</span><span class="sxs-lookup"><span data-stu-id="d4ebb-107">Use this</span></span>|<span data-ttu-id="d4ebb-108">動作</span><span class="sxs-lookup"><span data-stu-id="d4ebb-108">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d4ebb-109">**文件結構描述**</span><span class="sxs-lookup"><span data-stu-id="d4ebb-109">**Document schema**</span></span>|<span data-ttu-id="d4ebb-110">選取將訊息從 XML 格式序列化成一般檔案文件格式的一般檔案文件結構描述。</span><span class="sxs-lookup"><span data-stu-id="d4ebb-110">Select a flat file document schema to use for serializing the message from XML to the flat file format.</span></span> <span data-ttu-id="d4ebb-111">若未指定結構描述，則會使用執行階段結構描述探索。</span><span class="sxs-lookup"><span data-stu-id="d4ebb-111">If no schema is specified, run-time schema discovery is done.</span></span> <span data-ttu-id="d4ebb-112">在 BizTalk 編輯器中可以建立一般檔案文件結構描述。</span><span class="sxs-lookup"><span data-stu-id="d4ebb-112">You can create the flat file document schema in BizTalk Editor.</span></span><br /><br /> <span data-ttu-id="d4ebb-113">預設值：無</span><span class="sxs-lookup"><span data-stu-id="d4ebb-113">Default value: None</span></span>|  
    |<span data-ttu-id="d4ebb-114">**標頭結構描述**</span><span class="sxs-lookup"><span data-stu-id="d4ebb-114">**Header schema**</span></span>|<span data-ttu-id="d4ebb-115">選取做為一般檔案訊息標頭部分的結構描述。</span><span class="sxs-lookup"><span data-stu-id="d4ebb-115">Select a schema for the header part of the flat file message.</span></span> <span data-ttu-id="d4ebb-116">標頭結構描述也可以在名為訊息內容屬性中指定**HeaderSpecName** xmlnorm 命名空間之下。</span><span class="sxs-lookup"><span data-stu-id="d4ebb-116">A header schema can also be specified in the message context property named **HeaderSpecName** under the xmlnorm namespace.</span></span> <span data-ttu-id="d4ebb-117">在此狀況下，它將覆寫管線設計師中指定的標頭結構描述。</span><span class="sxs-lookup"><span data-stu-id="d4ebb-117">In this case, it will override the header schema specified in Pipeline Designer.</span></span><br /><br /> <span data-ttu-id="d4ebb-118">使用 BizTalk 編輯器可以建立一般檔案訊息標頭部分的結構描述。</span><span class="sxs-lookup"><span data-stu-id="d4ebb-118">You can create the schema for the header part of the flat file message with BizTalk Editor.</span></span><br /><br /> <span data-ttu-id="d4ebb-119">預設值：無</span><span class="sxs-lookup"><span data-stu-id="d4ebb-119">Default value: None</span></span>|  
    |<span data-ttu-id="d4ebb-120">**保留位元順序標記**</span><span class="sxs-lookup"><span data-stu-id="d4ebb-120">**Preserve byte order mark**</span></span>|<span data-ttu-id="d4ebb-121">指定組合器元件所產生的文件是否要加上位元順序標記 (BOM)。</span><span class="sxs-lookup"><span data-stu-id="d4ebb-121">Specifies whether to add a byte order mark (BOM) to the document produced by the assembler component.</span></span><br /><br /> <span data-ttu-id="d4ebb-122">預設值： **False**</span><span class="sxs-lookup"><span data-stu-id="d4ebb-122">Default Value: **False**</span></span>|  
    |<span data-ttu-id="d4ebb-123">**目標字元集**</span><span class="sxs-lookup"><span data-stu-id="d4ebb-123">**Target charset**</span></span>|<span data-ttu-id="d4ebb-124">指定將用來為外寄訊息編碼的目標字元集。</span><span class="sxs-lookup"><span data-stu-id="d4ebb-124">Specifies the target character set used for encoding of outgoing messages.</span></span><br /><br /> <span data-ttu-id="d4ebb-125">預設值：無</span><span class="sxs-lookup"><span data-stu-id="d4ebb-125">Default value: None</span></span>|  
    |<span data-ttu-id="d4ebb-126">**結尾結構描述**</span><span class="sxs-lookup"><span data-stu-id="d4ebb-126">**Trailer schema**</span></span>|<span data-ttu-id="d4ebb-127">選取作為一般檔案訊息結尾部分的結構描述。</span><span class="sxs-lookup"><span data-stu-id="d4ebb-127">Select a schema for the trailer part of the flat file message.</span></span> <span data-ttu-id="d4ebb-128">使用 BizTalk 編輯器可以建立一般檔案訊息結尾部分的結構描述。</span><span class="sxs-lookup"><span data-stu-id="d4ebb-128">You can create the schema for the trailer part of the flat file message in BizTalk Editor.</span></span><br /><br /> <span data-ttu-id="d4ebb-129">預設值：無</span><span class="sxs-lookup"><span data-stu-id="d4ebb-129">Default value: None</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4ebb-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4ebb-130">See Also</span></span>  
 <span data-ttu-id="d4ebb-131">[一般檔案組合器管線元件](../core/flat-file-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="d4ebb-131">[Flat File Assembler Pipeline Component](../core/flat-file-assembler-pipeline-component.md) </span></span>  
 <span data-ttu-id="d4ebb-132">[設定原生管線元件](../core/configuring-native-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="d4ebb-132">[Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md) </span></span>  
 <span data-ttu-id="d4ebb-133">[XML 和一般檔案屬性結構描述與屬性](../core/xml-and-flat-file-property-schema-and-properties.md) </span><span class="sxs-lookup"><span data-stu-id="d4ebb-133">[XML and Flat File Property Schema and Properties](../core/xml-and-flat-file-property-schema-and-properties.md) </span></span>  
 [<span data-ttu-id="d4ebb-134">管線 AssemblerDisassembler （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="d4ebb-134">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)