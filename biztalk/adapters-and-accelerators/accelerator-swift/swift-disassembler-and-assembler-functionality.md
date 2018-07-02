---
title: SWIFT 解譯器和組合器功能 |Microsoft Docs
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
ms.openlocfilehash: 4f9a01480c5d308ffa882b2457e26548f4b5e43b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992855"
---
# <a name="swift-disassembler-and-assembler-functionality"></a><span data-ttu-id="84148-102">SWIFT 解譯器和組合器功能</span><span class="sxs-lookup"><span data-stu-id="84148-102">SWIFT Disassembler and Assembler Functionality</span></span>
<span data-ttu-id="84148-103">SWIFT 解譯器可以執行下列工作中叫用時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收管線：</span><span class="sxs-lookup"><span data-stu-id="84148-103">The SWIFT disassembler can perform the following tasks when invoked in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] receive pipeline:</span></span>  
  
- <span data-ttu-id="84148-104">以動態方式找出的訊息類型，並解決文件結構描述。</span><span class="sxs-lookup"><span data-stu-id="84148-104">Dynamically discover the message type and resolve document schema.</span></span> <span data-ttu-id="84148-105">此啟用的單一的接收埠和管線來處理多個 SWIFT 的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="84148-105">This enables a single receive port and pipeline to handle multiple SWIFT message types.</span></span>  
  
- <span data-ttu-id="84148-106">剖析為 XML 的 SWIFT 的一般檔案。</span><span class="sxs-lookup"><span data-stu-id="84148-106">Parse a SWIFT flat file into XML.</span></span>  
  
- <span data-ttu-id="84148-107">叫用驗證讀取器執行 XML （結構描述） 驗證，例如資料類型的有效性、 資料格式或長度一致性檢查的 XML。</span><span class="sxs-lookup"><span data-stu-id="84148-107">Invoke the XML validating reader to perform XML (schema) validation, such as checking data type validity, data format, or length conformance.</span></span>  
  
- <span data-ttu-id="84148-108">叫用的 「 商務規則引擎 (BRE) 」，來執行 BRE 驗證，例如檢查一致性 SWIFT 網路規則，或執行其他複雜的驗證結構描述未實作。</span><span class="sxs-lookup"><span data-stu-id="84148-108">Invoke the Business Rule Engine (BRE) to perform BRE validation, such as checking conformance to SWIFT network rules or performing other complex validation that the schema does not implement.</span></span>  
  
- <span data-ttu-id="84148-109">將已剖析的 XML 訊息發佈到 MessageBox 資料庫的升級的內容屬性與序列化的錯誤集合 XML （提供剖析或驗證期間發生任何錯誤的相關資訊）。</span><span class="sxs-lookup"><span data-stu-id="84148-109">Publish a parsed XML message to the MessageBox database with promoted context properties and serialized error collection XML (providing information about any errors encountered during parsing or validation).</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="84148-110">如果解譯器在剖析期間發生嚴重失敗，解譯器會發佈訊息到 MessageBox 資料庫中的原生的一般檔案格式，而不是 XML。</span><span class="sxs-lookup"><span data-stu-id="84148-110">If the disassembler encounters fatal failures during parsing, the disassembler will publish the message to the MessageBox database in native flat file format rather than XML.</span></span>  
  
- <span data-ttu-id="84148-111">處理輸入批次，如下所示：</span><span class="sxs-lookup"><span data-stu-id="84148-111">Process inbound batches, as follows:</span></span>  
  
  -   <span data-ttu-id="84148-112">剖析，並保留批次的信封 （批次結尾中的 批次標頭）</span><span class="sxs-lookup"><span data-stu-id="84148-112">Parse and preserve batch envelopes (batch header, batch trailer)</span></span>  
  
  -   <span data-ttu-id="84148-113">剖析，並保留訊息信封 （訊息標頭，訊息結尾）</span><span class="sxs-lookup"><span data-stu-id="84148-113">Parse and preserve message envelopes (message header, message trailer)</span></span>  
  
  -   <span data-ttu-id="84148-114">剖析及驗證個別的批次中的 SWIFT 訊息</span><span class="sxs-lookup"><span data-stu-id="84148-114">Parse and validate SWIFT messages in the batch individually</span></span>  
  
  -   <span data-ttu-id="84148-115">個別將 SWIFT 的訊息發佈到 MessageBox 資料庫</span><span class="sxs-lookup"><span data-stu-id="84148-115">Publish SWIFT messages to the MessageBox database individually</span></span>  
  
  -   <span data-ttu-id="84148-116">將整個輸入批次發佈至 MessageBox 資料庫中，當作單一訊息 （輸入完全相同複本）</span><span class="sxs-lookup"><span data-stu-id="84148-116">Publish the entire inbound batch to the MessageBox database as a single message (exact copy of input)</span></span>  
  
  -   <span data-ttu-id="84148-117">升級用於排序或相互關聯訊息來自相同的批次的批次相關的內容屬性</span><span class="sxs-lookup"><span data-stu-id="84148-117">Promote batch-related context properties for sorting or correlating messages originating from the same batch</span></span>  
  
  <span data-ttu-id="84148-118">SWIFT 組合器可以執行時叫用 BizTalk 傳送管線中的下列工作：</span><span class="sxs-lookup"><span data-stu-id="84148-118">The SWIFT assembler can perform the following tasks when invoked in a BizTalk send pipeline:</span></span>  
  
- <span data-ttu-id="84148-119">以動態方式找出的訊息類型，並解決文件結構描述。</span><span class="sxs-lookup"><span data-stu-id="84148-119">Dynamically discover the message type and resolve the document schema.</span></span> <span data-ttu-id="84148-120">這可讓單一傳送埠和管線，以處理多個 SWIFT 訊息類型。</span><span class="sxs-lookup"><span data-stu-id="84148-120">This allows a single send port and pipeline to handle multiple SWIFT message types.</span></span>  
  
- <span data-ttu-id="84148-121">將剖析的 XML 序列化至 SWIFT 的一般檔案中。</span><span class="sxs-lookup"><span data-stu-id="84148-121">Serialize parsed XML into a SWIFT flat file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84148-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84148-122">See Also</span></span>  
 [<span data-ttu-id="84148-123">使用 SWIFT 解譯器和組合器</span><span class="sxs-lookup"><span data-stu-id="84148-123">Working with the SWIFT Disassembler and Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)