---
title: "使用 SOAP 標頭 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP headers
- SOAP headers, about SOAP headers
- Web services, SOAP headers
ms.assetid: 816618ff-ecd8-4f12-b9a9-dbe4203411d8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0671dabe7547d3f55b937a1de58241a35cb70b39
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-soap-headers"></a><span data-ttu-id="a9540-102">使用 SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="a9540-102">Using SOAP Headers</span></span>
<span data-ttu-id="a9540-103">Microsoft BizTalk Server 支援已定義和未知的 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="a9540-103">Microsoft BizTalk Server provides support for defined and unknown SOAP headers.</span></span> <span data-ttu-id="a9540-104">已定義 SOAP 標頭是「Web 服務描述語言」(WSDL) 的標頭，已在 Web 服務中明確陳述。</span><span class="sxs-lookup"><span data-stu-id="a9540-104">Defined SOAP headers are headers in the Web Service Description Language (WSDL) that are explicity stated in the Web service.</span></span> <span data-ttu-id="a9540-105">未知 SOAP 標頭則是未在 Web 服務中明確陳述的 WSDL 標頭。</span><span class="sxs-lookup"><span data-stu-id="a9540-105">Unknown SOAP headers are headers that in the WSDL that are not explicity stated in the Web service.</span></span> <span data-ttu-id="a9540-106">如需有關使用 SOAP 標頭的詳細資訊，請參閱 < 使用 SOAP 標頭 」 中的 Microsoft.NET Framework 文件在[http://go.microsoft.com/fwlink/?LinkId=25363](http://go.microsoft.com/fwlink/?LinkId=25363)。</span><span class="sxs-lookup"><span data-stu-id="a9540-106">For more information about using SOAP headers, see "Using SOAP Headers" in the Microsoft .NET Framework documentation at [http://go.microsoft.com/fwlink/?LinkId=25363](http://go.microsoft.com/fwlink/?LinkId=25363).</span></span>  
  
 <span data-ttu-id="a9540-107">BizTalk Server 會為 Web 服務內每個已定義的 SOAP 標頭建立內容屬性。</span><span class="sxs-lookup"><span data-stu-id="a9540-107">BizTalk Server creates a context property for each defined SOAP header in the Web service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9540-108">已使用的 Web 服務僅支援已定義的 SOAP 標頭，使用 Web 服務時您不能設定未知標頭。</span><span class="sxs-lookup"><span data-stu-id="a9540-108">Consumed Web services support only defined SOAP headers.You cannot set unknown headers when consuming Web services.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a9540-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="a9540-109">In This Section</span></span>  
  
-   [<span data-ttu-id="a9540-110">SOAP 標頭與已使用的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="a9540-110">SOAP Headers with Consumed Web Services</span></span>](../core/soap-headers-with-consumed-web-services.md)  
  
-   [<span data-ttu-id="a9540-111">SOAP 標頭與已發佈的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="a9540-111">SOAP Headers with Published Web Services</span></span>](../core/soap-headers-with-published-web-services.md)