---
title: "無法辨識的訊息中的 XML 解譯器管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Allow Unrecognized Messages property
- XMLNorm.AllowUnrecognizedMessage property
- pipeline components, XML Disassembler
- XML Disassembler [pipeline component], unrecognized messages
ms.assetid: 5a6be3a8-0bac-426a-bf0b-5091191091de
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d82396002ff9d35484af5f0000dc3468c8ad37fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unrecognized-messages-in-the-xml-disassembler-pipeline-component"></a><span data-ttu-id="ca815-102">XML 解譯器管線元件中無法辨識的訊息</span><span class="sxs-lookup"><span data-stu-id="ca815-102">Unrecognized Messages in the XML Disassembler Pipeline Component</span></span>
<span data-ttu-id="ca815-103">XML 解譯器元件在以下情況中可能會將訊息當作「無法辨識」處理：</span><span class="sxs-lookup"><span data-stu-id="ca815-103">The XML Disassembler component may handle a message as "unrecognized" in the following cases:</span></span>  
  
-   <span data-ttu-id="ca815-104">已接收的 XML 訊息沒有內文、空的內文或內文中為空白資料。</span><span class="sxs-lookup"><span data-stu-id="ca815-104">An XML message is received with no body, an empty body, or empty data in the body.</span></span>  
  
-   <span data-ttu-id="ca815-105">XML 訊息已接收，但是沒有部署其結構描述。</span><span class="sxs-lookup"><span data-stu-id="ca815-105">An XML message is received but no schema is deployed for it.</span></span>  
  
 <span data-ttu-id="ca815-106">無法辨識的訊息會根據處理**允許無法辨識的訊息**屬性 (或在**XMLNorm.AllowUnrecognizedMessage**在訊息內容屬性)。</span><span class="sxs-lookup"><span data-stu-id="ca815-106">An unrecognized message is handled based on the **Allow Unrecognized Messages** property (or on the **XMLNorm.AllowUnrecognizedMessage** property on the message context).</span></span>  
  
 <span data-ttu-id="ca815-107">如果**允許無法辨識的訊息**設**True**，將發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="ca815-107">If **Allow Unrecognized Messages** is set to **True**, the following occurs:</span></span>  
  
-   <span data-ttu-id="ca815-108">沒有內文、空白/空值的內文，或內文中的資料為空白/空值的訊息會透過 XML 解譯器未經變更傳送出去。</span><span class="sxs-lookup"><span data-stu-id="ca815-108">A message with no body, an empty/null body, or with empty/null data in the body passes unchanged through the XML Disassembler.</span></span>  
  
-   <span data-ttu-id="ca815-109">沒有相關聯的已部署結構描述之 XML 文件會透過 XML 解譯器未經變更傳送出去。</span><span class="sxs-lookup"><span data-stu-id="ca815-109">An XML document with no associated deployed schema passes unchanged through the XML Disassembler.</span></span>  
  
-   <span data-ttu-id="ca815-110">無論是在元件屬性中明確參考結構描述或是在結構描述解析程序期間找到結構描述，具有相關聯的已部署結構描述之 XML 文件都是由 XML 解譯器處理。</span><span class="sxs-lookup"><span data-stu-id="ca815-110">An XML document that has a deployed schema associated with it is processed by the XML Disassembler regardless of whether the schema is explicitly referenced in a component property or found during the schema resolution process.</span></span>  
  
 <span data-ttu-id="ca815-111">如果**允許無法辨識的訊息**設**False**，將發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="ca815-111">If **Allow Unrecognized Messages** is set to **False**, the following occurs:</span></span>  
  
-   <span data-ttu-id="ca815-112">沒有內文、空白/空值的內文，或內文中的資料為空白/空值的訊息不會透過 XML 解譯器傳送出去。</span><span class="sxs-lookup"><span data-stu-id="ca815-112">A message with no body or an empty/null body or with empty/null data in the body is not passed through the XML Disassembler.</span></span>  
  
-   <span data-ttu-id="ca815-113">沒有相關聯的已部署結構描述之 XML 文件不會透過解譯器傳送出去。</span><span class="sxs-lookup"><span data-stu-id="ca815-113">An XML document that does not have a deployed schema associated with it is not passed through the disassembler.</span></span> <span data-ttu-id="ca815-114">如有可能，會報告錯誤並暫停訊息。</span><span class="sxs-lookup"><span data-stu-id="ca815-114">An error is reported and the message is suspended, if possible.</span></span>  
  
-   <span data-ttu-id="ca815-115">無論是在元件屬性中明確參考結構描述或是在結構描述解析程序期間找到結構描述，具有相關聯的已部署結構描述之 XML 文件都是由 XML 解譯器處理。</span><span class="sxs-lookup"><span data-stu-id="ca815-115">An XML document that has a deployed schema associated with it is processed by the XML Disassembler regardless of whether the schema is explicitly referenced in a component property or found during the schema resolution process.</span></span>  
  
 <span data-ttu-id="ca815-116">依照預設，XML 解譯器不允許無法辨識的訊息。</span><span class="sxs-lookup"><span data-stu-id="ca815-116">By default, the XML Disassembler does not allow unrecognized messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca815-117">不論 XML 解譯器不會處理非 XML 訊息**允許無法辨識的訊息**屬性設定。</span><span class="sxs-lookup"><span data-stu-id="ca815-117">Non-XML messages are not processed by the XML Disassembler regardless of the **Allow Unrecognized Messages** property setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca815-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca815-118">See Also</span></span>  
 <span data-ttu-id="ca815-119">[XML 解譯器管線元件](../core/xml-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="ca815-119">[XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="ca815-120">如何設定 XML 解譯器管線元件</span><span class="sxs-lookup"><span data-stu-id="ca815-120">How to Configure the XML Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)