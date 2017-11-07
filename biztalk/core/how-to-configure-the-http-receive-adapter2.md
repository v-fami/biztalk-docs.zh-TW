---
title: "如何設定 HTTP 接收 Adapter2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP receive adapter, configuring
- configuring HTTP receive adapter
ms.assetid: dd26fd57-90d8-4ffe-b56f-8de55ecc6f68
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed6e40036308aa872a2d6ba23da8209ee9f80cfc
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-configure-the-http-receive-adapter"></a><span data-ttu-id="f032e-102">如何設定 HTTP 接收配接器</span><span class="sxs-lookup"><span data-stu-id="f032e-102">How to Configure the HTTP Receive Adapter</span></span>
<span data-ttu-id="f032e-103">您可以使用 HTTP 接收配接器，將訊息提交至 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="f032e-103">You can use the HTTP receive adapter to submit messages to BizTalk Server.</span></span> <span data-ttu-id="f032e-104">HTTP 接收配接器是裝載於 IIS 程序中的 Internet Information Services (IIS) ISAPI 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="f032e-104">The HTTP receive adapter is an Internet Information Services (IIS) ISAPI extension that is hosted in the IIS process.</span></span>  
  
### <a name="to-configure-the-http-receive-adapter"></a><span data-ttu-id="f032e-105">若要設定 HTTP 接收配接器</span><span class="sxs-lookup"><span data-stu-id="f032e-105">To configure the HTTP receive adapter</span></span>  
  
1.  <span data-ttu-id="f032e-106">將 HTTP 接收配接器 (BTSHTTPReceive.dll) 從 **\<BizTalk2010 > \HttpReceive >**包含單一登入 (SSO) 專案的資料夾 (例如， **< Adapter_install > \biztalk2010\SSO\mySSODemo**)。</span><span class="sxs-lookup"><span data-stu-id="f032e-106">Copy the HTTP receive adapter (BTSHTTPReceive.dll) from **\<BizTalk2010>\HttpReceive>** to the folder containing your Single Sign-On (SSO) project (for example, **<Adapter_install>\biztalk2010\SSO\mySSODemo**).</span></span>  
  
    1.  <span data-ttu-id="f032e-107">新增網頁服務延伸模組 mySSODemo。</span><span class="sxs-lookup"><span data-stu-id="f032e-107">Add a new Web service extension mySSODemo.</span></span>  
  
    2.  <span data-ttu-id="f032e-108">瀏覽至 <BizTalk_install>\HttpReceive，然後將其中的 HTTP 接收配接器複製到您的 SSO 專案所在的資料夾，例如，</span><span class="sxs-lookup"><span data-stu-id="f032e-108">Browse to and copy <BizTalk_install>\HttpReceive to the folder containing your SSO project, for example,</span></span>  
  
         <span data-ttu-id="f032e-109"><Adapter_install>\biztalk2010\SSO\mySSODemo\BTSHTTPReceive.dll。</span><span class="sxs-lookup"><span data-stu-id="f032e-109"><Adapter_install>\biztalk2010\SSO\mySSODemo\BTSHTTPReceive.dll.</span></span>  
  
    3.  <span data-ttu-id="f032e-110">將 mySSODemo 網頁服務延伸的狀態**允許**。</span><span class="sxs-lookup"><span data-stu-id="f032e-110">Set status of mySSODemo Web service extension to **Allowed**.</span></span>  
  
2.  <span data-ttu-id="f032e-111">重新啟動 IIS 以確定所有變更均生效。</span><span class="sxs-lookup"><span data-stu-id="f032e-111">Restart IIS to ensure that all changes are in effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f032e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f032e-112">See Also</span></span>  
 [<span data-ttu-id="f032e-113">在配接器的安全性</span><span class="sxs-lookup"><span data-stu-id="f032e-113">Security in the adapter</span></span>](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)