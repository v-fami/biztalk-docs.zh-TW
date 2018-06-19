---
title: 如何設定 BizTalk Framework 解譯器管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components, BizTalk Framework Disassembler
- disassembly stage, pipelines
- receive pipelines, disassembly stage
- BizTalk Framework Disassembler [pipeline component], configuring
ms.assetid: a5599bcb-dbee-46a5-a91d-3c54f901cd30
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07fefb577e5322fa303a1a1476a976b453adb083
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249190"
---
# <a name="how-to-configure-the-biztalk-framework-disassembler-pipeline-component"></a><span data-ttu-id="f298d-102">如何設定 BizTalk Framework 解譯器管線元件</span><span class="sxs-lookup"><span data-stu-id="f298d-102">How to Configure the BizTalk Framework Disassembler Pipeline Component</span></span>
<span data-ttu-id="f298d-103">BizTalk Framework 解譯器管線元件應該在接收管線的「解譯」階段中使用。</span><span class="sxs-lookup"><span data-stu-id="f298d-103">The BizTalk Framework Disassembler pipeline component should be used in the Disassemble stage of a receive pipeline.</span></span>  
  
### <a name="to-configure-the-properties-for-the-biztalk-framework-disassembler-pipeline-component"></a><span data-ttu-id="f298d-104">設定 BizTalk Framework 解譯器管線元件的屬性</span><span class="sxs-lookup"><span data-stu-id="f298d-104">To configure the properties for the BizTalk Framework Disassembler pipeline component</span></span>  
  
1.  <span data-ttu-id="f298d-105">將 BizTalk Framework 解譯器管線元件拖曳至接收管線的「解譯」階段中。</span><span class="sxs-lookup"><span data-stu-id="f298d-105">Drag the BizTalk Framework Disassembler pipeline component into the Disassemble stage of a receive pipeline.</span></span>  
  
2.  <span data-ttu-id="f298d-106">在 [屬性] 視窗中**管線元件屬性**區段中，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="f298d-106">In the Properties window, in the **Pipeline Component Properties** section, do the following.</span></span>  
  
    |<span data-ttu-id="f298d-107">使用</span><span class="sxs-lookup"><span data-stu-id="f298d-107">Use this</span></span>|<span data-ttu-id="f298d-108">動作</span><span class="sxs-lookup"><span data-stu-id="f298d-108">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f298d-109">**允許無法辨識的訊息**</span><span class="sxs-lookup"><span data-stu-id="f298d-109">**Allow unrecognized message**</span></span>|<span data-ttu-id="f298d-110">指出是否允許沒有可辨識結構描述的訊息通過解譯器。</span><span class="sxs-lookup"><span data-stu-id="f298d-110">Indicates whether to allow messages that do not have a recognized schema to be passed through the disassembler.</span></span><br /><br /> <span data-ttu-id="f298d-111">預設值： **False**</span><span class="sxs-lookup"><span data-stu-id="f298d-111">Default value: **False**</span></span>|  
    |<span data-ttu-id="f298d-112">**文件結構描述**</span><span class="sxs-lookup"><span data-stu-id="f298d-112">**Document schemas**</span></span>|<span data-ttu-id="f298d-113">指示要套用到文件之結構描述的命名空間與類型名稱。</span><span class="sxs-lookup"><span data-stu-id="f298d-113">Indicates the namespace and typename of the schema or schemas to be applied to the document.</span></span> <span data-ttu-id="f298d-114">如需詳細資訊，請參閱[如何使用結構描述集合屬性編輯器](../core/how-to-use-the-schema-collection-property-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="f298d-114">For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md).</span></span><br /><br /> <span data-ttu-id="f298d-115">此屬性中指定的結構描述應該要有唯一的目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="f298d-115">Schemas specified in this property should have unique target namespaces.</span></span> <span data-ttu-id="f298d-116">若任何結構描述擁有相同的命名空間，則驗證文件執行個體可能無法如預期運作。</span><span class="sxs-lookup"><span data-stu-id="f298d-116">If any of the schemas have the same namespace, the validation of the document instances may not work as expected.</span></span> <span data-ttu-id="f298d-117">若結構描述必須擁有相同的命名空間，則您應該為各結構描述個別建立管線，然後為每一個 BizTalk Framework 解譯器管線元件指定一個結構描述，或者您也可以使用一個管線，但不將任何結構描述指定為 BizTalk Framework 解譯器管線元件的參數。</span><span class="sxs-lookup"><span data-stu-id="f298d-117">If schemas must have the same namespace, you should either create a separate pipeline for each schema and specify one schema per BizTalk Framework Disassembler pipeline component or use one pipeline but do not specify any schemas as parameters for the BizTalk Framework Disassembler pipeline component.</span></span><br /><br /> <span data-ttu-id="f298d-118">預設值：空集合</span><span class="sxs-lookup"><span data-stu-id="f298d-118">Default value: Empty collection</span></span>|  
    |<span data-ttu-id="f298d-119">**信封結構描述**</span><span class="sxs-lookup"><span data-stu-id="f298d-119">**Envelope schemas**</span></span>|<span data-ttu-id="f298d-120">指示要套用到信封之結構描述的命名空間與類型名稱。</span><span class="sxs-lookup"><span data-stu-id="f298d-120">Indicates the namespace and typename of the schema or schemas to be applied to the envelope.</span></span> <span data-ttu-id="f298d-121">如需詳細資訊，請參閱[如何使用結構描述集合屬性編輯器](../core/how-to-use-the-schema-collection-property-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="f298d-121">For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md).</span></span><br /><br /> <span data-ttu-id="f298d-122">此屬性中指定的結構描述應該要有唯一的目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="f298d-122">Schemas specified in this property should have unique target namespaces.</span></span> <span data-ttu-id="f298d-123">若任何結構描述擁有相同的命名空間，則驗證文件執行個體可能無法如預期運作。</span><span class="sxs-lookup"><span data-stu-id="f298d-123">If any of the schemas have the same namespace, the validation of the document instances may not work as expected.</span></span> <span data-ttu-id="f298d-124">若結構描述必須擁有相同的命名空間，則您應該為各結構描述個別建立管線，然後為每一個 BizTalk Framework 解譯器管線元件指定一個結構描述，或者您也可以使用一個管線，但不將任何結構描述指定為 BizTalk Framework 解譯器管線元件的參數。</span><span class="sxs-lookup"><span data-stu-id="f298d-124">If schemas must have the same namespace, you should either create a separate pipeline for each schema and specify one schema per BizTalk Framework Disassembler pipeline component or use one pipeline but do not specify any schemas as parameters for the BizTalk Framework Disassembler pipeline component.</span></span><br /><br /> <span data-ttu-id="f298d-125">預設值：空集合</span><span class="sxs-lookup"><span data-stu-id="f298d-125">Default value: Empty collection</span></span>|  
    |<span data-ttu-id="f298d-126">**驗證文件結構**</span><span class="sxs-lookup"><span data-stu-id="f298d-126">**Validate document structure**</span></span>|<span data-ttu-id="f298d-127">當**True**，執行驗證的組譯工具，包括信封內送訊息。</span><span class="sxs-lookup"><span data-stu-id="f298d-127">When **True**, performs a validation of the incoming message to the disassembler, including the envelopes.</span></span> <span data-ttu-id="f298d-128">**注意：** 時**True**，如果您指定兩個或多個結構描述，可能會收到 「 二或多個選取的結構描述共用相同的目標命名空間 」 的錯誤**文件結構描述**或**信封結構描述**屬性。</span><span class="sxs-lookup"><span data-stu-id="f298d-128">**Note:**  When **True**, you may receive a "Two or more of the selected schema share the same target namespace" error if you specify two or more schemas for the **Document schemas** or **Envelope schemas** properties.</span></span> <br /><br /> <span data-ttu-id="f298d-129">預設值： **False**</span><span class="sxs-lookup"><span data-stu-id="f298d-129">Default value: **False**</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f298d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f298d-130">See Also</span></span>  
 <span data-ttu-id="f298d-131">[BizTalk Framework 解譯器管線元件](../core/biztalk-framework-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="f298d-131">[BizTalk Framework Disassembler Pipeline Component](../core/biztalk-framework-disassembler-pipeline-component.md) </span></span>  
 <span data-ttu-id="f298d-132">[設定原生管線元件](../core/configuring-native-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="f298d-132">[Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md) </span></span>  
 <span data-ttu-id="f298d-133">[管線 AssemblerDisassembler （BizTalk Server 範例資料夾）](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md) </span><span class="sxs-lookup"><span data-stu-id="f298d-133">[Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md) </span></span>  
 [<span data-ttu-id="f298d-134">設定原生管線元件</span><span class="sxs-lookup"><span data-stu-id="f298d-134">Configuring Native Pipeline Components</span></span>](../core/configuring-native-pipeline-components.md)