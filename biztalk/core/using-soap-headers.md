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
# <a name="using-soap-headers"></a>使用 SOAP 標頭
Microsoft BizTalk Server 支援已定義和未知的 SOAP 標頭。 已定義 SOAP 標頭是「Web 服務描述語言」(WSDL) 的標頭，已在 Web 服務中明確陳述。 未知 SOAP 標頭則是未在 Web 服務中明確陳述的 WSDL 標頭。 如需有關使用 SOAP 標頭的詳細資訊，請參閱 < 使用 SOAP 標頭 」 中的 Microsoft.NET Framework 文件在[http://go.microsoft.com/fwlink/?LinkId=25363](http://go.microsoft.com/fwlink/?LinkId=25363)。  
  
 BizTalk Server 會為 Web 服務內每個已定義的 SOAP 標頭建立內容屬性。  
  
> [!NOTE]
>  已使用的 Web 服務僅支援已定義的 SOAP 標頭，使用 Web 服務時您不能設定未知標頭。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [SOAP 標頭與已使用的 Web 服務](../core/soap-headers-with-consumed-web-services.md)  
  
-   [SOAP 標頭與已發佈的 Web 服務](../core/soap-headers-with-published-web-services.md)