---
title: 如何啟用 ASP.NET 4.0 的已發佈 Web 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58646ff2-77a3-49dc-8593-f6e41d85d4f3
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e68b8eef114828ad181e83ce0c7acd70a5545e0d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254078"
---
# <a name="how-to-enable-aspnet-40-for-published-web-services"></a><span data-ttu-id="48b97-102">如何啟用 ASP.NET 4.0 的已發佈的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="48b97-102">How to Enable ASP.NET 4.0 for Published Web Services</span></span>
<span data-ttu-id="48b97-103">在 IIS 中設定的 ASP.Net 版本。</span><span class="sxs-lookup"><span data-stu-id="48b97-103">Set the ASP.Net version in IIS.</span></span>

<span data-ttu-id="48b97-104">BizTalk Server Web 服務發佈精靈依賴隨附 ASP.NET、.NET Framework 隨附的功能。</span><span class="sxs-lookup"><span data-stu-id="48b97-104">The BizTalk Server Web Services Publishing Wizard relies on functionality provided with ASP.NET, which is included with the .NET Framework.</span></span> <span data-ttu-id="48b97-105">ASP.Net 版本隨附於您選擇的.NET CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="48b97-105">The ASP.Net versions are included with the .NET CLR version you choose.</span></span> 

<span data-ttu-id="48b97-106">本主題說明如何變更.NET CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="48b97-106">This topic shows you how to change the .NET CLR version.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="48b97-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="48b97-107">Prerequisites</span></span>

<span data-ttu-id="48b97-108">IIS 隨附於**網頁伺服器 (IIS)** 作業系統中的角色。</span><span class="sxs-lookup"><span data-stu-id="48b97-108">IIS is included with the **Web Server (IIS)** role in the operating system.</span></span> <span data-ttu-id="48b97-109">當您安裝此角色時，也選取 ASP.NET 的較新版本。</span><span class="sxs-lookup"><span data-stu-id="48b97-109">When you install this role, also select the newer version of ASP.NET.</span></span> 
  
## <a name="update-an-application-pool"></a><span data-ttu-id="48b97-110">更新應用程式集區</span><span class="sxs-lookup"><span data-stu-id="48b97-110">Update an application pool</span></span>
  
1.  <span data-ttu-id="48b97-111">開啟**Internet Information Services (IIS) 管理員**:</span><span class="sxs-lookup"><span data-stu-id="48b97-111">Open **Internet Information Services (IIS) Manager**:</span></span>

    1. <span data-ttu-id="48b97-112">在**伺服器管理員**，選取**工具**。</span><span class="sxs-lookup"><span data-stu-id="48b97-112">In **Server Manager**, select **Tools**.</span></span>
    2. <span data-ttu-id="48b97-113">選取**Internet Information Services (IIS) 管理員**。</span><span class="sxs-lookup"><span data-stu-id="48b97-113">Select **Internet Information Services (IIS) Manager**.</span></span>
  
2.  <span data-ttu-id="48b97-114">展開伺服器名稱，然後選取**應用程式集區**。</span><span class="sxs-lookup"><span data-stu-id="48b97-114">Expand the server name, and select **Application Pools**.</span></span>  
  
3.  <span data-ttu-id="48b97-115">選取的應用程式集區，並開啟**基本設定**。</span><span class="sxs-lookup"><span data-stu-id="48b97-115">Select the app pool, and open the **Basic Settings**.</span></span>  
  
4. <span data-ttu-id="48b97-116">設定 **.NET CLR 版本**至較新版本，並選取**確定**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="48b97-116">Set the **.NET CLR version** to the newer version, and select **OK** to save your changes.</span></span>  

> [!NOTE]
> <span data-ttu-id="48b97-117">您也可以變更 web.config 檔案中的版本。</span><span class="sxs-lookup"><span data-stu-id="48b97-117">You can also change the version in the web.config file.</span></span>
 
## <a name="allow-the-aspnet-extension"></a><span data-ttu-id="48b97-118">允許 ASP.Net 延伸模組</span><span class="sxs-lookup"><span data-stu-id="48b97-118">Allow the ASP.Net extension</span></span>
  
1.  <span data-ttu-id="48b97-119">開啟**Internet Information Services (IIS) 管理員**:</span><span class="sxs-lookup"><span data-stu-id="48b97-119">Open **Internet Information Services (IIS) Manager**:</span></span>

    1. <span data-ttu-id="48b97-120">在**伺服器管理員**，選取**工具**。</span><span class="sxs-lookup"><span data-stu-id="48b97-120">In **Server Manager**, select **Tools**.</span></span>
    2. <span data-ttu-id="48b97-121">選取**Internet Information Services (IIS) 管理員**。</span><span class="sxs-lookup"><span data-stu-id="48b97-121">Select **Internet Information Services (IIS) Manager**.</span></span>
  
2.  <span data-ttu-id="48b97-122">選取伺服器名稱，然後按兩下**ISAPI 及 CGI 限制**。</span><span class="sxs-lookup"><span data-stu-id="48b97-122">Select the server name, and double-click **ISAPI and CGI Restrictions**.</span></span>  
  
3. <span data-ttu-id="48b97-123">確認 ASP.NET**允許**32 位元和 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="48b97-123">Confirm ASP.NET is **Allowed** for the 32-bit and 64-bit versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48b97-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48b97-124">See Also</span></span>  
 [<span data-ttu-id="48b97-125">規劃發佈 Web 服務</span><span class="sxs-lookup"><span data-stu-id="48b97-125">Planning for Publishing Web Services</span></span>](../core/planning-for-publishing-web-services2.md)