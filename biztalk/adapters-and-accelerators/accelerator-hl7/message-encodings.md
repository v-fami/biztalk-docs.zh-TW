---
title: 訊息編碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, encodings
- messages, code samples
- encoding [messages]
- code samples
ms.assetid: 360638c0-4094-428f-a7c7-306a5f95a6bf
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 013df4d29604e6dd7ce6d2e486612be303cc5898
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007087"
---
# <a name="message-encodings"></a><span data-ttu-id="ebfd1-102">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="ebfd1-102">Message Encodings</span></span>
<span data-ttu-id="ebfd1-103">不足以供 HL7 的順序定義訊息語意。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-103">It is not sufficient to define message semantics in order for HL7 to be useful.</span></span> <span data-ttu-id="ebfd1-104">一旦有尚未決定訊息的內容，標準就必須說明如何代表實際的介面中該內容。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-104">Once message content has been determined, the standard has to explain how to represent that content in an actual interface.</span></span> <span data-ttu-id="ebfd1-105">也就是說，必須有指定 「 訊息編碼方式 」。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-105">That is to say, there must be a specified "message encoding".</span></span> <span data-ttu-id="ebfd1-106">HL7 第 2 版支援兩種形式的訊息編碼方式、 自訂分隔符號為基礎的編碼方式，和使用 XML 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-106">HL7 Version 2 supports two forms of message encoding, a custom delimiter-based encoding, and an XML encoding.</span></span>  
  
 <span data-ttu-id="ebfd1-107">HL7 選擇原始分隔符號為基礎的編碼方式，減少訊息最大的大小。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-107">HL7 chose the original delimiter-based encoding to reduce the size of messages as much as possible.</span></span> <span data-ttu-id="ebfd1-108">例如，如果您比較資料結構的分隔符號區隔的結構，將每個項目放置在一組固定的位置中的項目時，分隔符號為基礎結構是如果） 訊息不包含一些項目，以及 b） 一些更實惠項目不會填滿所有允許的空間。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-108">For example, if you compare a data structure in which delimiters separate elements to a structure that positions each element in a fixed set of positions, the delimiter-based structure is far more economical if a) messages do not contain some elements, and b) some elements do not fill all the space allowed.</span></span> <span data-ttu-id="ebfd1-109">在分隔符號為基礎結構中唯一的額外負荷是本身的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-109">The only overhead in delimiter-based structures is the delimiters themselves.</span></span>  
  
 <span data-ttu-id="ebfd1-110">原始的 HL7 編碼方式會定義五個分隔符號，以宣告 MSH 區段中的每個訊息。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-110">The original HL7 encoding defines five delimiters, which each message declares within the MSH segment.</span></span> <span data-ttu-id="ebfd1-111">這些資訊表示：</span><span class="sxs-lookup"><span data-stu-id="ebfd1-111">These indicate:</span></span>  
  
- <span data-ttu-id="ebfd1-112">區段</span><span class="sxs-lookup"><span data-stu-id="ebfd1-112">Segments</span></span>  
  
- <span data-ttu-id="ebfd1-113">欄位</span><span class="sxs-lookup"><span data-stu-id="ebfd1-113">Fields</span></span>  
  
- <span data-ttu-id="ebfd1-114">Components</span><span class="sxs-lookup"><span data-stu-id="ebfd1-114">Components</span></span>  
  
- <span data-ttu-id="ebfd1-115">子元件</span><span class="sxs-lookup"><span data-stu-id="ebfd1-115">Subcomponents</span></span>  
  
- <span data-ttu-id="ebfd1-116">重複 （的欄位、 元件或子元件）</span><span class="sxs-lookup"><span data-stu-id="ebfd1-116">Repetition (of a field, component, or subcomponent)</span></span>  
  
  <span data-ttu-id="ebfd1-117">請注意，因為編碼方式的重要層面是分隔符號，您必須定義它們第一次。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-117">Note that since delimiters are a fundamental aspect of the encoding, you must define them first.</span></span> <span data-ttu-id="ebfd1-118">這麼做的結果是，可能會有任何子子分隔符號。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-118">One result of this is that there can be no sub-sub-delimiter.</span></span> <span data-ttu-id="ebfd1-119">有時候，這項限制的效果不幸的設計新的資料類型。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-119">At times, this limitation has unfortunate effects upon the design of new data types.</span></span>  
  
  <span data-ttu-id="ebfd1-120">在 2003 年 6 月中，HL7 發佈 HL7 第 2 版、 XML 編碼的語法、 Release 1。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-120">In June 2003, HL7 published HL7 Version 2, XML Encoding Syntax, Release 1.</span></span> <span data-ttu-id="ebfd1-121">此標準定義 HL7 版本 2.3.1 和 2.4 訊息的替代編碼規則，並提供一個機制，來決定替代的編碼規則的後續 HL7 2.X 版。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-121">This standard defines alternate encoding rules for HL7 Version 2.3.1 and 2.4 messages, and provides a mechanism for determining alternate encoding rules for subsequent HL7 2.X versions.</span></span> <span data-ttu-id="ebfd1-122">基本上，這個新的標準第 2.3.1 版和 V2.4 抽象訊息、 區段、 欄位和資料類型會定義 XML 項目標記，並建立規則來定義所需的任何新的結構，建立第 2 版的後續版本標準的標記。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-122">In essence, this new standard defines XML element tags for the Version 2.3.1 and V2.4 abstract messages, segments, fields, and data types, and creates rules for defining the tags needed for any new structures created for subsequent versions of the Version 2 standard.</span></span> <span data-ttu-id="ebfd1-123">定義這項標準的程序會導致一系列的 2.4 及 2.5 版本的增強功能。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-123">The process of defining this standard led to a series of improvements in versions 2.4 and 2.5.</span></span> <span data-ttu-id="ebfd1-124">會發生這種情況是因為您不必處理基礎的標準中某些傳統模稜兩可會造成 XML 標記的建立。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-124">This happened because creation of XML tags led to the need to address some longstanding ambiguities in the underlying standard.</span></span> <span data-ttu-id="ebfd1-125">如此一來，a） 定義完善的訊息結構的程式碼所建立，表示觸發程序事件，b） 重複的區段的抽象訊息使用的群組已正式識別和指定，相關聯的抽象訊息中的變化和 c) 在本機定義的資料類型，CM 已取代更特定的類型。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-125">As a result, a) well-defined message structure codes were created to indicate variations in the abstract messages associated with trigger events, b) repeating groups of segments with an abstract message were formally identified and named, and c) the locally defined data type, CM was replaced with more specific types.</span></span>  
  
  <span data-ttu-id="ebfd1-126">例如，以下是使用傳統管道分隔格式的簡單的通知訊息：</span><span class="sxs-lookup"><span data-stu-id="ebfd1-126">For example, the following is a simple acknowledgment message using the traditional pipe delimited format:</span></span>  
  
```  
MSH|^~\&|LAB|767543|ADT|767543|199003141304-0500||ACK^^ACK|XX3657|P|2.4  
MSA|AR|ZZ9380  
ERR|PID^1^16^103&Table value not found&HL70357  
```  
  
 <span data-ttu-id="ebfd1-127">相反地，以下是相同的訊息，表示為 XML 文件：</span><span class="sxs-lookup"><span data-stu-id="ebfd1-127">By contrast, the following is the same message represented as an XML document:</span></span>  
  
```  
<ACK  
xmlns="urn:hl7-org:v2xml"  
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
xsi:schemaLocation="urn:hl7-org:v2xml ACK.xsd">  
   <MSH>  
      <MSH.1>|</MSH.1>  
      <MSH.2>^~\&</MSH.2>  
      <MSH.3>  
         <HD.1>LAB</HD.1>  
      </MSH.3>  
      <MSH.4>  
         <HD.1>767543</HD.1>  
      </MSH.4>  
      <MSH.5>  
         <HD.1>ADT</HD.1>  
      </MSH.5>  
      <MSH.6>  
         <HD.1>767543</HD.1>  
      </MSH.6>  
      <MSH.7>  
         <TS.1>199003141304-0500</TS.1>  
      </MSH.7>  
      <MSH.9>  
         <MSG.1>ACK</MSG.1>  
         <MSG.3>ACK</MSG.3>  
      </MSH.9>  
      <MSH.10>XX3657</MSH.10>  
      <MSH.11>  
         <PT.1>P</PT.1>  
      </MSH.11>  
      <MSH.12>  
         <VID.1>2.4</VID.1>  
      </MSH.12>  
   </MSH>  
   <MSA>  
      <MSA.1>AR</MSA.1>  
      <MSA.2>ZZ9380</MSA.2>  
   </MSA>  
   <ERR>  
      <ERR.1>  
         <ELD.1>PID</ELD.1>  
         <ELD.2>1</ELD.2>  
         <ELD.3>16</ELD.3>  
         <ELD.4>  
            <CE.1>103</CE.1>  
            <CE.2>Table value not found</CE.2>  
            <CE.3>HL70357</CE.3>  
         </ELD.4>  
      </ERR.1>  
   </ERR>  
</ACK>  
```  
  
 <span data-ttu-id="ebfd1-128">Microsoft BizTalk Accelerator for HL7 的下列函式 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援這些需求：</span><span class="sxs-lookup"><span data-stu-id="ebfd1-128">The following functions of Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) support these requirements:</span></span>  
  
-   <span data-ttu-id="ebfd1-129">分隔的管道和 XML 編碼方式的支援。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-129">Support of pipe delimited and XML encoding.</span></span>  
  
-   <span data-ttu-id="ebfd1-130">支援的 XML 和管道之間的轉譯會分隔編碼。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-130">Support of translation between XML and pipe delimited encodings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebfd1-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebfd1-131">See Also</span></span>  
 <span data-ttu-id="ebfd1-132">[處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="ebfd1-132">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="ebfd1-133">[訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="ebfd1-133">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="ebfd1-134">使用 HL7 2.X 結構描述</span><span class="sxs-lookup"><span data-stu-id="ebfd1-134">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)