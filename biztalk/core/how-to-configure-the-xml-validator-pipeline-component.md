---
title: 如何設定 XML 驗證器管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML Validator [pipeline component]
- send pipelines, validating
- pipeline components, XML Validator
- receive pipelines, validating
ms.assetid: 3b3becaf-703c-4399-a5ed-e7082e31e6e9
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 821ad6a1353c0aa29866fd36fe84a7ea6317690b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248382"
---
# <a name="how-to-configure-the-xml-validator-pipeline-component"></a><span data-ttu-id="825ae-102">如何設定 XML 驗證器管線元件</span><span class="sxs-lookup"><span data-stu-id="825ae-102">How to Configure the XML Validator Pipeline Component</span></span>
<span data-ttu-id="825ae-103">XML 驗證器管線元件可用於傳送或接收管線中的任何階段 (除了解譯或組合階段)。</span><span class="sxs-lookup"><span data-stu-id="825ae-103">The XML Validator pipeline component can be used in any stage (except Disassemble or Assemble) in a send or receive pipeline.</span></span>  
  
### <a name="to-configure-the-properties-for-the-xml-validator-pipeline-component"></a><span data-ttu-id="825ae-104">設定 XML 驗證器管線元件的屬性</span><span class="sxs-lookup"><span data-stu-id="825ae-104">To configure the properties for the XML Validator pipeline component</span></span>  
  
1.  <span data-ttu-id="825ae-105">將 XML 驗證器管線元件拖曳至接收管線的驗證階段。</span><span class="sxs-lookup"><span data-stu-id="825ae-105">Drag the XML Validator pipeline component into the Validate stage of a receive pipeline.</span></span>  
  
2.  <span data-ttu-id="825ae-106">在 [屬性] 視窗中**管線元件屬性**區段中，進行下列設定。</span><span class="sxs-lookup"><span data-stu-id="825ae-106">In the Properties window, in the **Pipeline Component Properties** section, set the following.</span></span>  
  
    |<span data-ttu-id="825ae-107">使用</span><span class="sxs-lookup"><span data-stu-id="825ae-107">Use this</span></span>|<span data-ttu-id="825ae-108">動作</span><span class="sxs-lookup"><span data-stu-id="825ae-108">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="825ae-109">**文件結構描述**</span><span class="sxs-lookup"><span data-stu-id="825ae-109">**Document schemas**</span></span>|<span data-ttu-id="825ae-110">指示要套用到文件之結構描述的命名空間與類型名稱。</span><span class="sxs-lookup"><span data-stu-id="825ae-110">Indicates the namespace and typename of the schema or schemas to be applied to the document.</span></span> <span data-ttu-id="825ae-111">如需詳細資訊，請參閱[如何使用結構描述集合屬性編輯器](../core/how-to-use-the-schema-collection-property-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="825ae-111">For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md).</span></span> <span data-ttu-id="825ae-112">若未指定結構描述，則會使用訊息的目標命名空間和根項目名稱資訊，來進行執行階段結構描述探索。</span><span class="sxs-lookup"><span data-stu-id="825ae-112">If no schemas are specified, the run-time schema discovery will be done by using the message's target namespace and root element name information.</span></span> <span data-ttu-id="825ae-113">**注意：** 如果您指定兩個或多個結構描述，可能會收到 「 二或多個選取的結構描述共用相同的目標命名空間 」 的錯誤**文件結構描述**屬性。</span><span class="sxs-lookup"><span data-stu-id="825ae-113">**Note:**  You may receive a "Two or more of the selected schema share the same target namespace" error if you specify two or more schemas for the **Document schemas** property.</span></span> <br /><br /> <span data-ttu-id="825ae-114">預設值：空集合</span><span class="sxs-lookup"><span data-stu-id="825ae-114">Default value: Empty collection</span></span>|  
    |<span data-ttu-id="825ae-115">可復原交換處理</span><span class="sxs-lookup"><span data-stu-id="825ae-115">Recoverable Interchange Processing</span></span>|<span data-ttu-id="825ae-116">若為 "false" - 表示整個交換是將其視為一個單位加以驗證 (若任何包含的訊息失敗，就會擱置整個交換)。</span><span class="sxs-lookup"><span data-stu-id="825ae-116">When "false" - indicates that entire interchange is validated as a unit (if any contained message fails, entire interchange is suspended).</span></span><br /><br /> <span data-ttu-id="825ae-117">若為 "true" 時 - 表示交換中的訊息會由驗證器個別擷取，同時可能發生透過傳訊路徑或其他路徑的部分填入將會遭到擱置。</span><span class="sxs-lookup"><span data-stu-id="825ae-117">When "true" - indicates that messages within interchange are extracted individually by validator with possibility of some propagating through messaging pathway and others being suspended.</span></span><br /><br /> <span data-ttu-id="825ae-118">如需有關可復原交換處理的詳細資訊，請參閱[可復原交換處理](../core/recoverable-interchange-processing.md)。</span><span class="sxs-lookup"><span data-stu-id="825ae-118">For more information on recoverable interchange processing, see [Recoverable Interchange Processing](../core/recoverable-interchange-processing.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="825ae-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="825ae-119">See Also</span></span>  
 <span data-ttu-id="825ae-120">[XML 驗證器管線元件](../core/xml-validator-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="825ae-120">[XML Validator Pipeline Component](../core/xml-validator-pipeline-component.md) </span></span>  
 [<span data-ttu-id="825ae-121">設定原生管線元件</span><span class="sxs-lookup"><span data-stu-id="825ae-121">Configuring Native Pipeline Components</span></span>](../core/configuring-native-pipeline-components.md)