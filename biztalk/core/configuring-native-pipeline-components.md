---
title: 設定原生管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Pipeline Designer, pipeline components
- pipeline components, configuring
- Pipeline Designer, code sample
- IPersistPropertyBag interface
ms.assetid: a3332a60-8cd6-43fa-9ecf-e1e54e71fef7
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94475334395f8c360bbb636cfa9cbadcf3bf4fe3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233174"
---
# <a name="configuring-native-pipeline-components"></a><span data-ttu-id="13085-102">設定原生管線元件</span><span class="sxs-lookup"><span data-stu-id="13085-102">Configuring Native Pipeline Components</span></span>
<span data-ttu-id="13085-103">管線元件能在設計階段時顯示其自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="13085-103">Pipeline components can expose their own custom properties at design time.</span></span> <span data-ttu-id="13085-104">任何在元件中定義的公用屬性將於「管線設計師」中呈現，只要該屬性的讀取和寫入存取子已經實作即可。</span><span class="sxs-lookup"><span data-stu-id="13085-104">Any public property defined in the component will be rendered in Pipeline Designer providing that read and write accessors for that property are implemented.</span></span> <span data-ttu-id="13085-105">「管線設計師」將根據它們的宣告來顯示元件屬性；例如，若屬性宣告為唯讀，在「管線設計師」中也會如此顯示。</span><span class="sxs-lookup"><span data-stu-id="13085-105">Pipeline Designer will display the component properties in accordance with their declaration; for example, if the property is declared as read-only, it will be displayed as such in Pipeline Designer.</span></span>  
  
 <span data-ttu-id="13085-106">自訂管線元件必須實作**IPersistPropertyBag**介面，讓建立這些自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="13085-106">Custom pipeline components must implement the **IPersistPropertyBag** interface to enable the creation of these custom properties.</span></span> <span data-ttu-id="13085-107">建立具有屬性**IPersistPropertyBag**介面可以在 Microsoft [屬性] 視窗中設定[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，就和原生管線元件的所有屬性一樣。</span><span class="sxs-lookup"><span data-stu-id="13085-107">Properties created with the **IPersistPropertyBag** interface can be set in the Properties window of Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], just like all the properties of the native pipeline components.</span></span> <span data-ttu-id="13085-108">在本節中包含各管線元件的設定程序。</span><span class="sxs-lookup"><span data-stu-id="13085-108">This section contains procedures for configuring each of the included pipeline components.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13085-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="13085-109">In This Section</span></span>  
  
-   [<span data-ttu-id="13085-110">如何設定原生管線元件</span><span class="sxs-lookup"><span data-stu-id="13085-110">How to Configure Native Pipeline Components</span></span>](../core/how-to-configure-native-pipeline-components.md)  
  
-   [<span data-ttu-id="13085-111">如何設定 BizTalk Framework 組合器管線元件</span><span class="sxs-lookup"><span data-stu-id="13085-111">How to Configure the BizTalk Framework Assembler Pipeline Component</span></span>](../core/how-to-configure-the-biztalk-framework-assembler-pipeline-component.md)  
  
-   [<span data-ttu-id="13085-112">如何設定 BizTalk Framework 解譯器管線元件</span><span class="sxs-lookup"><span data-stu-id="13085-112">How to Configure the BizTalk Framework Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md)  
  
-   [<span data-ttu-id="13085-113">BizTalk Framework 結構描述和屬性</span><span class="sxs-lookup"><span data-stu-id="13085-113">BizTalk Framework Schema and Properties</span></span>](../core/biztalk-framework-schema-and-properties.md)  
  
-   [<span data-ttu-id="13085-114">如何設定一般檔案組合器管線元件</span><span class="sxs-lookup"><span data-stu-id="13085-114">How to Configure the Flat File Assembler Pipeline Component</span></span>](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)  
  
-   [<span data-ttu-id="13085-115">如何設定一般檔案解譯器管線元件</span><span class="sxs-lookup"><span data-stu-id="13085-115">How to Configure the Flat File Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)  
  
-   [<span data-ttu-id="13085-116">如何設定 MIME SMIME 解碼器管線元件</span><span class="sxs-lookup"><span data-stu-id="13085-116">How to Configure the MIME-SMIME Decoder Pipeline Component</span></span>](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)  
  
-   [<span data-ttu-id="13085-117">如何設定 MIME SMIME 編碼器管線元件</span><span class="sxs-lookup"><span data-stu-id="13085-117">How to Configure the MIME-SMIME Encoder Pipeline Component</span></span>](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)  
  
-   [<span data-ttu-id="13085-118">MIME SMIME 屬性結構描述和屬性</span><span class="sxs-lookup"><span data-stu-id="13085-118">MIME-SMIME Property Schema and Properties</span></span>](../core/mime-smime-property-schema-and-properties.md)  
  
-   [<span data-ttu-id="13085-119">如何設定合作對象解析管線元件</span><span class="sxs-lookup"><span data-stu-id="13085-119">How to Configure the Party Resolution Pipeline Component</span></span>](../core/how-to-configure-the-party-resolution-pipeline-component.md)  
  
-   [<span data-ttu-id="13085-120">如何設定 XML 組合器管線元件</span><span class="sxs-lookup"><span data-stu-id="13085-120">How to Configure the XML Assembler Pipeline Component</span></span>](../core/how-to-configure-the-xml-assembler-pipeline-component.md)  
  
-   [<span data-ttu-id="13085-121">如何設定 XML 解譯器管線元件</span><span class="sxs-lookup"><span data-stu-id="13085-121">How to Configure the XML Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)  
  
-   [<span data-ttu-id="13085-122">XML 和一般檔案屬性結構描述與屬性</span><span class="sxs-lookup"><span data-stu-id="13085-122">XML and Flat File Property Schema and Properties</span></span>](../core/xml-and-flat-file-property-schema-and-properties.md)  
  
-   [<span data-ttu-id="13085-123">如何設定 XML 驗證器管線元件</span><span class="sxs-lookup"><span data-stu-id="13085-123">How to Configure the XML Validator Pipeline Component</span></span>](../core/how-to-configure-the-xml-validator-pipeline-component.md)