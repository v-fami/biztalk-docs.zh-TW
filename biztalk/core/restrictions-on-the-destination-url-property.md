---
title: "目的地 URL 屬性的限制 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [HTTP adapters], restrictions
- HTTP adapters, restrictions
ms.assetid: 982a5122-e43d-4730-a8b9-ceb1ff88638c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0788b693027fb803b121b1b732cb3ee126897e7b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="restrictions-on-the-destination-url-property"></a><span data-ttu-id="4fa78-102">目的地 URL 屬性的限制</span><span class="sxs-lookup"><span data-stu-id="4fa78-102">Restrictions on the Destination URL Property</span></span>
<span data-ttu-id="4fa78-103">目的地 URL 是指定 HTTP 伺服器位址的字串，您在這裡使用 HTTP 通訊協定來傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="4fa78-103">The destination URL is a string that specifies the address of the HTTP server where you want to send messages using the HTTP protocol.</span></span>  
  
 <span data-ttu-id="4fa78-104">下列規則與限制適用於目的地 URL 屬性：</span><span class="sxs-lookup"><span data-stu-id="4fa78-104">The following rules and restrictions apply to the destination URL property:</span></span>  
  
-   <span data-ttu-id="4fa78-105">您必須永遠以下列格式指定目的地 URL 屬性：</span><span class="sxs-lookup"><span data-stu-id="4fa78-105">You must always specify the destination URL property in the following format:</span></span>  
  
     <span data-ttu-id="4fa78-106">http [s]://\<主機 > [:\<連接埠 >] [/\<路徑 > [/\<檔案 > [？\<查詢字串 >]]]</span><span class="sxs-lookup"><span data-stu-id="4fa78-106">http[s]://\<host>[:\<port>][/\<path>[/\<file>[?\<query-string>]]]</span></span>  
  
-   <span data-ttu-id="4fa78-107">整個字串不一定是 URI 編碼。</span><span class="sxs-lookup"><span data-stu-id="4fa78-107">The whole string may or may not be URI encoded.</span></span>  
  
-   <span data-ttu-id="4fa78-108">整個字串，除了查詢字串中，不能包含任何下列字元： \< >: \ &#124;" ?</span><span class="sxs-lookup"><span data-stu-id="4fa78-108">The whole string, except the query string, cannot contain any of the following characters: \< > : \ &#124; " ?</span></span> <span data-ttu-id="4fa78-109">*.</span><span class="sxs-lookup"><span data-stu-id="4fa78-109">*.</span></span>  
  
-   <span data-ttu-id="4fa78-110">屬性不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="4fa78-110">The property is not case-sensitive.</span></span>  
  
-   <span data-ttu-id="4fa78-111">字串長度不能超過 256 個字元。</span><span class="sxs-lookup"><span data-stu-id="4fa78-111">The length of the string must not exceed 256 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa78-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fa78-112">See Also</span></span>  
 [<span data-ttu-id="4fa78-113">設定 HTTP 傳送埠</span><span class="sxs-lookup"><span data-stu-id="4fa78-113">Configuring an HTTP Send Port</span></span>](../core/configuring-an-http-send-port.md)