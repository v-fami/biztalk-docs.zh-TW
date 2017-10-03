---
title: "資料類型轉換的屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, data type conversion
- MQBYTE property [MQSeries adapters]
- MQLONG property [MQSeries adapters]
- MQCHAR property [MQSeries adapters]
- configuring [MQSeries adapters], data type conversion
ms.assetid: 5b81eab0-f7a1-42f3-b212-a211b2893fd5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3705f1d0a20a48f0683a15588891ef3fe60889cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="data-type-conversion-of-properties"></a><span data-ttu-id="c9190-102">屬性的資料類型轉換</span><span class="sxs-lookup"><span data-stu-id="c9190-102">Data Type Conversion of Properties</span></span>
<span data-ttu-id="c9190-103">MQSeries 訊息中的標頭屬性是包含在訊息本身的資料結構。</span><span class="sxs-lookup"><span data-stu-id="c9190-103">Header properties in an MQSeries message are data structures contained in the message itself.</span></span> <span data-ttu-id="c9190-104">MQSeries 配接器在傳送和接收訊息時，會自動驗證和轉換 MQSeries 訊息標頭中的特定值。</span><span class="sxs-lookup"><span data-stu-id="c9190-104">The MQSeries adapter automatically validates and converts certain values in MQSeries message headers when sending and receiving messages.</span></span>  
  
 <span data-ttu-id="c9190-105">下表描述 MQSeries 資料型別及其驗證和轉換。</span><span class="sxs-lookup"><span data-stu-id="c9190-105">The following table describes the MQSeries data types and their validation and conversion.</span></span>  
  
|<span data-ttu-id="c9190-106">MQSeries 資料型別</span><span class="sxs-lookup"><span data-stu-id="c9190-106">MQSeries data type</span></span>|<span data-ttu-id="c9190-107">驗證和轉換</span><span class="sxs-lookup"><span data-stu-id="c9190-107">Validation and conversion</span></span>|  
|------------------------|-------------------------------|  
|<span data-ttu-id="c9190-108">MQLONG</span><span class="sxs-lookup"><span data-stu-id="c9190-108">MQLONG</span></span>|<span data-ttu-id="c9190-109">MQSeries 會執行驗證。</span><span class="sxs-lookup"><span data-stu-id="c9190-109">MQSeries performs the validation.</span></span> <span data-ttu-id="c9190-110">轉換為長整數。</span><span class="sxs-lookup"><span data-stu-id="c9190-110">Converts to a long integer.</span></span> <span data-ttu-id="c9190-111">無法有效避免訊息移至 MQSeries 佇列的值。</span><span class="sxs-lookup"><span data-stu-id="c9190-111">Values that are not valid prevent the message from going to the MQSeries queue.</span></span>|  
|<span data-ttu-id="c9190-112">MQCHAR</span><span class="sxs-lookup"><span data-stu-id="c9190-112">MQCHAR</span></span>|<span data-ttu-id="c9190-113">轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="c9190-113">Converts to a string.</span></span>|  
|<span data-ttu-id="c9190-114">MQBYTE</span><span class="sxs-lookup"><span data-stu-id="c9190-114">MQBYTE</span></span>|<span data-ttu-id="c9190-115">轉換為包含字元 0-9 和 a-f 或 A-F 的字串，代表數字的十六進位值。</span><span class="sxs-lookup"><span data-stu-id="c9190-115">Converts to a string that contains the characters 0-9 and a-f or A-F, representing the hexadecimal value of the number.</span></span>|  
  
 <span data-ttu-id="c9190-116">許多 MQSeries 屬性都是 32 位元 (4 位元組) 不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="c9190-116">Many of the MQSeries properties are 32-bit (4-byte) unsigned integers.</span></span> <span data-ttu-id="c9190-117">因為**uint**不是 Common Language Specification (CLS)-標準的類型，您必須將它們指派給**物件**型別才能在.NET 方法中使用它們。</span><span class="sxs-lookup"><span data-stu-id="c9190-117">Because **uint** is not a Common Language Specification (CLS)-compliant type, you must assign them to **object** types before using them in .NET methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9190-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9190-118">See Also</span></span>  
 <span data-ttu-id="c9190-119">[MQSeries 配接器屬性](../core/mqseries-adapter-properties.md) </span><span class="sxs-lookup"><span data-stu-id="c9190-119">[MQSeries Adapter Properties](../core/mqseries-adapter-properties.md) </span></span>  
 <span data-ttu-id="c9190-120">[與 BizTalk Server 相關的屬性](../core/properties-related-to-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="c9190-120">[Properties Related to BizTalk Server](../core/properties-related-to-biztalk-server.md) </span></span>  
 [<span data-ttu-id="c9190-121">MQSeries 內容屬性</span><span class="sxs-lookup"><span data-stu-id="c9190-121">MQSeries Context Properties</span></span>](../core/mqseries-context-properties.md)