---
title: SOAP 配接器組態和調整參數 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [SOAP adapters], tuning
- SOAP adapters, tuning
ms.assetid: 73c175aa-16b9-4620-b303-9092ae29af21
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be6a71938876ad932a58d369abe40d7c8b073f72
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277342"
---
# <a name="soap-adapter-configuration-and-tuning-parameters"></a><span data-ttu-id="6e474-102">SOAP 配接器組態和調整參數</span><span class="sxs-lookup"><span data-stu-id="6e474-102">SOAP Adapter Configuration and Tuning Parameters</span></span>
<span data-ttu-id="6e474-103">您可透過在根 BizTalk Server 安裝目錄的 BTSNTSvc.exe 組態檔建立一個項目，以設定 SOAP 配接器為特定目的地伺服器開啟的並行連線數目。</span><span class="sxs-lookup"><span data-stu-id="6e474-103">You can configure the number of concurrent connections that the SOAP adapter opens for a particular destination server by making an entry in the BTSNTSvc.exe.config file that is located in the root BizTalk Server installation directory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e474-104">若 HTTP 和 SOAP 配接器傳送訊息至相同的目的地 HTTP 伺服器，此屬性就會套用至 HTTP 和 SOAP 配接器。</span><span class="sxs-lookup"><span data-stu-id="6e474-104">This property will be applied to both HTTP and SOAP adapters if they send messages to the same destination HTTP server.</span></span> <span data-ttu-id="6e474-105">“maxconnnection”屬性的預設值為 2，可為所有 URI 的“maxconnection”屬性設定的最大值為 20。</span><span class="sxs-lookup"><span data-stu-id="6e474-105">The default value for the “maxconnnection” property is 2, the maximum value that can be set for the “maxconnection” property for all URIs is 20.</span></span>  
  
 <span data-ttu-id="6e474-106">下列是連線上限屬性的組態範例。</span><span class="sxs-lookup"><span data-stu-id="6e474-106">The following is an example of the configuration for the maximum connections property:</span></span>  
  
```  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "20" />  
      <add address = "http://www.northwind.com" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e474-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e474-107">See Also</span></span>  
 <span data-ttu-id="6e474-108">[設定 SOAP 配接器](../core/configuring-the-soap-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="6e474-108">[Configuring the SOAP Adapter](../core/configuring-the-soap-adapter.md) </span></span>  
 [<span data-ttu-id="6e474-109">HTTP 配接器組態和調整參數</span><span class="sxs-lookup"><span data-stu-id="6e474-109">HTTP Adapter Configuration and Tuning Parameters</span></span>](../core/http-adapter-configuration-and-tuning-parameters.md)