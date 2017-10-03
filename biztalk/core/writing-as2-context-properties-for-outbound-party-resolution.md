---
title: "撰寫 AS2 內容屬性的輸出合作對象解析 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 808d63d9-076d-4eed-8420-aee12b130fee
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c89804c42554825e387d01ff592e3a628e8225b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="writing-as2-context-properties-for-outbound-party-resolution"></a><span data-ttu-id="d8db9-102">撰寫 AS2 內容屬性以執行輸出合作對象解析</span><span class="sxs-lookup"><span data-stu-id="d8db9-102">Writing AS2 Context Properties for Outbound Party Resolution</span></span>
<span data-ttu-id="d8db9-103">透過 AS2To 內容屬性或 `Http.UserHttpHeaders` 內容屬性中的 AS2To 屬性，便可以執行輸出 AS2 訊息的協議解析。</span><span class="sxs-lookup"><span data-stu-id="d8db9-103">Agreement resolution of outbound AS2 message can be performed using the AS2To context property or the AS2To property in the `Http.UserHttpHeaders` context property.</span></span> <span data-ttu-id="d8db9-104">不過，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在收到 AS2 訊息時，並不會將 AS2To 屬性寫至內容。</span><span class="sxs-lookup"><span data-stu-id="d8db9-104">However, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not write the AS2To property to the context upon receiving an AS2 message.</span></span> <span data-ttu-id="d8db9-105">如果您想對 AS2To 或 UserHttpHeaders 內容屬性執行協議解析，必須撰寫自訂協調流程或自訂管線元件。</span><span class="sxs-lookup"><span data-stu-id="d8db9-105">If you want to perform agreement resolution on the AS2To or UserHttpHeaders context property, you have to write a custom orchestration or a custom pipeline component to do so.</span></span> <span data-ttu-id="d8db9-106">只有在傳送埠未連結至協議時，才需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="d8db9-106">This is required only if the send port is not linked to the agreement.</span></span>  
  
 <span data-ttu-id="d8db9-107">若是自訂協調流程，您可以使用下列程式碼，將 AS2-To 附加至現有 `Http.UserHttpHeaders` 內容屬性的開頭：</span><span class="sxs-lookup"><span data-stu-id="d8db9-107">In a custom orchestration, you can append AS2-To to the beginning of the existing `Http.UserHttpHeaders` context property using the following code:</span></span>  
  
```  
Message_1(Http.UserHttpHeaders) = “AS2-To: MyPartner\r\n” + Message_1(Http.UserHttpHeaders);  
```  
  
 <span data-ttu-id="d8db9-108">若是自訂管線元件，則可以使用下列程式碼，將 AS2-To 附加至現有 `Http.UserHttpHeaders` 內容屬性的開頭。</span><span class="sxs-lookup"><span data-stu-id="d8db9-108">In a custom pipeline component, you can append AS2-To to the beginning of the existing `Http.UserHttpHeaders` context property using the following code.</span></span> <span data-ttu-id="d8db9-109">您必須先將 AS2-To 附加至 `Http.UserHttpHeaders` 內容屬性，As2Encoder 元件才能處理訊息。</span><span class="sxs-lookup"><span data-stu-id="d8db9-109">You need to append AS2-To to `Http.UserHttpHeaders` context property before the message is processed by the As2Encoder component.</span></span>  
  
```  
string strName="UserHttpHeaders";  
string strValue = "AS2-To: MyPartner\r\n" + (string)baseMessage.Context.Read(strName, "http://schemas.microsoft.com/BizTalk/2003/http-properties");  
baseMessage.Context.Write(strName, "http://schemas.microsoft.com/BizTalk/2003/http-properties", strValue);  
```  
  
 <span data-ttu-id="d8db9-110">如需有關升級`EDIIntAS.AS2To`屬性或`BTS.UseHttpHeaders`屬性至內容，請參閱中的 「 升級 AS2 標頭內容屬性 」[透過 FILE 傳送埠傳送 AS2 訊息](../core/sending-an-as2-message-over-a-file-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="d8db9-110">For more information on promoting the `EDIIntAS.AS2To` property or the `BTS.UseHttpHeaders` property to the context, see "Promoting AS2 Header Context Properties" in the [Sending an AS2 Message over a FILE Send Port](../core/sending-an-as2-message-over-a-file-send-port.md).</span></span>  
  
 <span data-ttu-id="d8db9-111">您可以加入要寫入 http 標頭的自訂管線元件的程式碼。UserHttpHeaders 內容屬性至訊息，請參閱[透過 FILE 傳送埠傳送 AS2 訊息](../core/sending-an-as2-message-over-a-file-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="d8db9-111">For code that you can add to a custom pipeline component to write the headers from the HTTP.UserHttpHeaders context property into the message, see [Sending an AS2 Message over a FILE Send Port](../core/sending-an-as2-message-over-a-file-send-port.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8db9-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8db9-112">See Also</span></span>  
 [<span data-ttu-id="d8db9-113">開發和設定 BizTalk Server AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="d8db9-113">Developing and Configuring BizTalk Server AS2 Solutions</span></span>](../core/developing-and-configuring-biztalk-server-as2-solutions.md)