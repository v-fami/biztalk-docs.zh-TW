---
title: SWIFT 解譯器和組合器功能 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- disassembler, about disassembler
- assembler, about assembler
- assembler, functionality
- disassembler, functionality
ms.assetid: d4fc092e-586d-4360-921d-151af66b8bc1
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0109979fbb9bf61fc0e1be833061b2a15b470690
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214038"
---
# <a name="swift-disassembler-and-assembler-functionality"></a><span data-ttu-id="57ca4-102">SWIFT 解譯器和組合器功能</span><span class="sxs-lookup"><span data-stu-id="57ca4-102">SWIFT Disassembler and Assembler Functionality</span></span>
<span data-ttu-id="57ca4-103">SWIFT 反組譯工具可以執行下列工作中叫用時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收管線：</span><span class="sxs-lookup"><span data-stu-id="57ca4-103">The SWIFT disassembler can perform the following tasks when invoked in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] receive pipeline:</span></span>  
  
-   <span data-ttu-id="57ca4-104">以動態方式找出的訊息類型，並解決文件結構描述。</span><span class="sxs-lookup"><span data-stu-id="57ca4-104">Dynamically discover the message type and resolve document schema.</span></span> <span data-ttu-id="57ca4-105">這樣做可讓的單一接收埠和管線來處理多個 SWIFT 訊息類型。</span><span class="sxs-lookup"><span data-stu-id="57ca4-105">This enables a single receive port and pipeline to handle multiple SWIFT message types.</span></span>  
  
-   <span data-ttu-id="57ca4-106">剖析為 XML 的 SWIFT 的一般檔案。</span><span class="sxs-lookup"><span data-stu-id="57ca4-106">Parse a SWIFT flat file into XML.</span></span>  
  
-   <span data-ttu-id="57ca4-107">叫用驗證讀取器執行 XML （結構描述） 驗證，例如資料類型的有效性，資料格式或長度一致性檢查的 XML。</span><span class="sxs-lookup"><span data-stu-id="57ca4-107">Invoke the XML validating reader to perform XML (schema) validation, such as checking data type validity, data format, or length conformance.</span></span>  
  
-   <span data-ttu-id="57ca4-108">叫用來執行 BRE 驗證，例如，檢查符合 SWIFT 網路規則或執行其他複雜的驗證結構描述不會實作商務規則引擎 (BRE)。</span><span class="sxs-lookup"><span data-stu-id="57ca4-108">Invoke the Business Rule Engine (BRE) to perform BRE validation, such as checking conformance to SWIFT network rules or performing other complex validation that the schema does not implement.</span></span>  
  
-   <span data-ttu-id="57ca4-109">將剖析的 XML 訊息發佈到 MessageBox 資料庫的升級的內容屬性與序列化的錯誤集合 XML （以提供資訊進行剖析或驗證期間發生的錯誤）。</span><span class="sxs-lookup"><span data-stu-id="57ca4-109">Publish a parsed XML message to the MessageBox database with promoted context properties and serialized error collection XML (providing information about any errors encountered during parsing or validation).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="57ca4-110">如果解譯器在剖析期間發生嚴重失敗，解譯器將會發佈訊息至 MessageBox 資料庫，在原生的一般檔案格式，而不是 XML。</span><span class="sxs-lookup"><span data-stu-id="57ca4-110">If the disassembler encounters fatal failures during parsing, the disassembler will publish the message to the MessageBox database in native flat file format rather than XML.</span></span>  
  
-   <span data-ttu-id="57ca4-111">處理輸入批次，如下所示：</span><span class="sxs-lookup"><span data-stu-id="57ca4-111">Process inbound batches, as follows:</span></span>  
  
    -   <span data-ttu-id="57ca4-112">剖析和保留批次的信封 （批次標頭、 批次結尾）</span><span class="sxs-lookup"><span data-stu-id="57ca4-112">Parse and preserve batch envelopes (batch header, batch trailer)</span></span>  
  
    -   <span data-ttu-id="57ca4-113">剖析，並保留訊息信封 （訊息標頭、 訊息結尾）</span><span class="sxs-lookup"><span data-stu-id="57ca4-113">Parse and preserve message envelopes (message header, message trailer)</span></span>  
  
    -   <span data-ttu-id="57ca4-114">剖析及驗證 SWIFT 訊息批次中個別</span><span class="sxs-lookup"><span data-stu-id="57ca4-114">Parse and validate SWIFT messages in the batch individually</span></span>  
  
    -   <span data-ttu-id="57ca4-115">個別將 SWIFT 訊息發佈到 MessageBox 資料庫</span><span class="sxs-lookup"><span data-stu-id="57ca4-115">Publish SWIFT messages to the MessageBox database individually</span></span>  
  
    -   <span data-ttu-id="57ca4-116">發佈至 MessageBox 資料庫的整個輸入批次當做單一訊息 （輸入的完全相同複本）</span><span class="sxs-lookup"><span data-stu-id="57ca4-116">Publish the entire inbound batch to the MessageBox database as a single message (exact copy of input)</span></span>  
  
    -   <span data-ttu-id="57ca4-117">升級適用於排序或來自相同的批次的訊息相互關聯的批次相關的內容屬性</span><span class="sxs-lookup"><span data-stu-id="57ca4-117">Promote batch-related context properties for sorting or correlating messages originating from the same batch</span></span>  
  
 <span data-ttu-id="57ca4-118">SWIFT 組譯工具可以執行時叫用 BizTalk 傳送管線中的下列工作：</span><span class="sxs-lookup"><span data-stu-id="57ca4-118">The SWIFT assembler can perform the following tasks when invoked in a BizTalk send pipeline:</span></span>  
  
-   <span data-ttu-id="57ca4-119">以動態方式找出的訊息類型，並解決文件結構描述。</span><span class="sxs-lookup"><span data-stu-id="57ca4-119">Dynamically discover the message type and resolve the document schema.</span></span> <span data-ttu-id="57ca4-120">這可讓單一傳送埠和管線來處理多個 SWIFT 訊息類型。</span><span class="sxs-lookup"><span data-stu-id="57ca4-120">This allows a single send port and pipeline to handle multiple SWIFT message types.</span></span>  
  
-   <span data-ttu-id="57ca4-121">將剖析的 XML 序列化為 SWIFT 的一般檔案。</span><span class="sxs-lookup"><span data-stu-id="57ca4-121">Serialize parsed XML into a SWIFT flat file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ca4-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57ca4-122">See Also</span></span>  
 [<span data-ttu-id="57ca4-123">SWIFT 解譯器和組合器</span><span class="sxs-lookup"><span data-stu-id="57ca4-123">Working with the SWIFT Disassembler and Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)