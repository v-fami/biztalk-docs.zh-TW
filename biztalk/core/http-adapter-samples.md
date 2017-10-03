---
title: "HTTP 配接器範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP adapters, examples
- examples, HTTP adapters
ms.assetid: 6796ea39-2947-45df-b228-1ecdb23a7ab8
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4eb20ba2a9dc91f9b8bd17442f8bd3e7986fcfa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="http-adapter-samples"></a><span data-ttu-id="2b3ac-102">HTTP 配接器範例</span><span class="sxs-lookup"><span data-stu-id="2b3ac-102">HTTP Adapter Samples</span></span>
<span data-ttu-id="2b3ac-103">本節包含的範例將示範使用 BizTalk HTTP 配接器時可使用的進階功能。</span><span class="sxs-lookup"><span data-stu-id="2b3ac-103">This section contains samples that illustrate advanced functionality when using the BizTalk HTTP Adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b3ac-104">執行此範例之前，您必須執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="2b3ac-104">Before running this sample, you need to do the following steps:</span></span>  
>   
>  1.  <span data-ttu-id="2b3ac-105">開啟 IIS、加入 ISAPI 及 CGI 限制：</span><span class="sxs-lookup"><span data-stu-id="2b3ac-105">Open IIS, add ISAPI and CGI restrictions:</span></span>  
>   
>      <span data-ttu-id="2b3ac-106">按一下左面板上的 [機器名稱]，再按一下右面板上的 [ISAPI 及 CGI 限制]，然後按一下 [加入 ISAPI 或 CGI 路徑]：</span><span class="sxs-lookup"><span data-stu-id="2b3ac-106">Click Machine Name on left panel, then click "ISAPI and CGI restrictions" on the right panel, then Add the ISAPI or CGI path:</span></span>  
>   
>      <span data-ttu-id="2b3ac-107">在 64 位元電腦上加入： C:\Program Files (x86) \Microsoft BizTalk Server\<版本 > \HttpReceive64\BTSHTTPReceive.dll</span><span class="sxs-lookup"><span data-stu-id="2b3ac-107">On a 64 bit machine add:   C:\Program Files (x86)\Microsoft BizTalk Server \<version>\HttpReceive64\BTSHTTPReceive.dll</span></span>  
>   
>      <span data-ttu-id="2b3ac-108">在 32 位元電腦上加入： C:\Program Files (x86) \Microsoft BizTalk Server\<版本 > \HttpReceive\BTSHTTPReceive.dll</span><span class="sxs-lookup"><span data-stu-id="2b3ac-108">On a 32 bit machine add:   C:\Program Files (x86)\Microsoft BizTalk Server \<version>\HttpReceive\BTSHTTPReceive.dll</span></span>  
>   
>      <span data-ttu-id="2b3ac-109">檢查允許的延伸模組路徑或執行。</span><span class="sxs-lookup"><span data-stu-id="2b3ac-109">Check allowed extension path or execute.</span></span>  
> 2.  <span data-ttu-id="2b3ac-110">按一下左面板上的 [HTTPRequestResponseSample]，再按一下中間面板上的 [處理常式對應]，然後按一下具有下列設定的 [新增指令碼對應]：</span><span class="sxs-lookup"><span data-stu-id="2b3ac-110">Click "HTTPRequestResponseSample" on left panel, then click "Handler Mapping" on middle panel, then click "Add script mapping” with the following setting:</span></span>  
>   
>      <span data-ttu-id="2b3ac-111">要求路徑：BTSHTTPReceive.dll</span><span class="sxs-lookup"><span data-stu-id="2b3ac-111">Request path:BTSHTTPReceive.dll</span></span>  
>   
>      <span data-ttu-id="2b3ac-112">可執行檔：</span><span class="sxs-lookup"><span data-stu-id="2b3ac-112">Executable:</span></span>  
>   
>      <span data-ttu-id="2b3ac-113">在 64 位元電腦上加入： C:\Program Files (x86) \Microsoft BizTalk Server\<版本 > \HttpReceive64\\</span><span class="sxs-lookup"><span data-stu-id="2b3ac-113">On 64 bit machine add:   C:\Program Files (x86)\Microsoft BizTalk Server \<version>\HttpReceive64\\</span></span>  
>   
>      <span data-ttu-id="2b3ac-114">在 32 位元電腦上加入： C:\Program Files (x86) \Microsoft BizTalk Server\<版本 > \HttpReceive\\</span><span class="sxs-lookup"><span data-stu-id="2b3ac-114">On 32 bit machine add:   C:\Program Files (x86)\Microsoft BizTalk Server \<version>\HttpReceive\\</span></span>  
>   
>      <span data-ttu-id="2b3ac-115">要求的限制：</span><span class="sxs-lookup"><span data-stu-id="2b3ac-115">Request restrictions:</span></span>  
>   
>      <span data-ttu-id="2b3ac-116">動詞命令： 文章</span><span class="sxs-lookup"><span data-stu-id="2b3ac-116">Verbs: POST</span></span>  
>   
>      <span data-ttu-id="2b3ac-117">存取：指令碼</span><span class="sxs-lookup"><span data-stu-id="2b3ac-117">Access: Script</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2b3ac-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="2b3ac-118">In This Section</span></span>  
  
-   [<span data-ttu-id="2b3ac-119">HTTPSolicitResponse</span><span class="sxs-lookup"><span data-stu-id="2b3ac-119">HTTPSolicitResponse</span></span>](../core/httpsolicitresponse.md)  
  
-   [<span data-ttu-id="2b3ac-120">HTTPRequestResponse</span><span class="sxs-lookup"><span data-stu-id="2b3ac-120">HTTPRequestResponse</span></span>](../core/httprequestresponse.md)