---
title: "如何設定 HTTP 接收 Adapter1 |Microsoft 文件"
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
ms.assetid: e7dbfed3-9dd8-49c9-90b6-a655d7c5446f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed6907a96c3c961a4df7d076ba9307f44627bfa2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-http-receive-adapter"></a><span data-ttu-id="92238-102">如何設定 HTTP 接收配接器</span><span class="sxs-lookup"><span data-stu-id="92238-102">How to Configure the HTTP Receive Adapter</span></span>
<span data-ttu-id="92238-103">您可以使用 HTTP 接收配接器，將訊息提交至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92238-103">You can use the HTTP receive adapter to submit messages to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="92238-104">HTTP 接收配接器是裝載於 IIS 程序中的 Internet Information Services (IIS) ISAPI 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="92238-104">The HTTP receive adapter is an Internet Information Services (IIS) ISAPI extension that is hosted in the IIS process.</span></span>  
  
### <a name="to-configure-the-http-receive-adapter"></a><span data-ttu-id="92238-105">若要設定 HTTP 接收配接器</span><span class="sxs-lookup"><span data-stu-id="92238-105">To configure the HTTP receive adapter</span></span>  
  
1.  <span data-ttu-id="92238-106">將 HTTP 接收配接器 (BTSHTTPReceive.dll) 從 **\<BizTalk > \HttpReceive >**至資料夾包含您的單一登入 (SSO) 專案，例如：</span><span class="sxs-lookup"><span data-stu-id="92238-106">Copy the HTTP receive adapter (BTSHTTPReceive.dll) from **\<BizTalk>\HttpReceive>** to the folder that contains your Single Sign-On (SSO) project, for example:</span></span>  
  
     <span data-ttu-id="92238-107">**< Adapter_install > \biztalk\SSO\mySSODemo**</span><span class="sxs-lookup"><span data-stu-id="92238-107">**<Adapter_install>\biztalk\SSO\mySSODemo**</span></span>  
  
    1.  <span data-ttu-id="92238-108">新增網頁服務延伸模組 mySSODemo。</span><span class="sxs-lookup"><span data-stu-id="92238-108">Add a new Web service extension mySSODemo.</span></span>  
  
    2.  <span data-ttu-id="92238-109">找出並複製**< BizTalk_install > \HttpReceive**至資料夾包含您的 SSO 專案，例如：</span><span class="sxs-lookup"><span data-stu-id="92238-109">Locate and copy **<BizTalk_install>\HttpReceive** to the folder that contains your SSO project, for example:</span></span>  
  
         <span data-ttu-id="92238-110">**< Adapter_install > \biztalk\SSO\mySSODemo\BTSHTTPReceive.dll。**</span><span class="sxs-lookup"><span data-stu-id="92238-110">**<Adapter_install>\biztalk\SSO\mySSODemo\BTSHTTPReceive.dll.**</span></span>  
  
    3.  <span data-ttu-id="92238-111">將 mySSODemo 網頁服務延伸狀態**允許**。</span><span class="sxs-lookup"><span data-stu-id="92238-111">Set the status of mySSODemo Web service extension to **Allowed**.</span></span>  
  
2.  <span data-ttu-id="92238-112">重新啟動 IIS 以套用所有變更。</span><span class="sxs-lookup"><span data-stu-id="92238-112">Restart IIS to apply all changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92238-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92238-113">See Also</span></span>  
 [<span data-ttu-id="92238-114">使用單一登入</span><span class="sxs-lookup"><span data-stu-id="92238-114">Using Single Sign-On</span></span>](../core/using-single-sign-on2.md)