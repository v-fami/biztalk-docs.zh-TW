---
title: "無法取得繫結型別的繫結延伸 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a7cfc81-7439-48f9-8cac-42b2419ecd9d
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79b649f69b7503f345f212aa5f014ce7b256148d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="unable-to-get-binding-type-for-binding-extension"></a><span data-ttu-id="f4b79-102">無法取得繫結延伸模組的繫結類型</span><span class="sxs-lookup"><span data-stu-id="f4b79-102">Unable to get binding type for binding extension</span></span>
## <a name="details"></a><span data-ttu-id="f4b79-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f4b79-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4b79-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f4b79-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f4b79-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f4b79-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="f4b79-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f4b79-106">Event ID</span></span>|<span data-ttu-id="f4b79-107">0</span><span class="sxs-lookup"><span data-stu-id="f4b79-107">0</span></span>|  
|<span data-ttu-id="f4b79-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="f4b79-108">Event Source</span></span>|<span data-ttu-id="f4b79-109">0</span><span class="sxs-lookup"><span data-stu-id="f4b79-109">0</span></span>|  
|<span data-ttu-id="f4b79-110">元件</span><span class="sxs-lookup"><span data-stu-id="f4b79-110">Component</span></span>|<span data-ttu-id="f4b79-111">0</span><span class="sxs-lookup"><span data-stu-id="f4b79-111">0</span></span>|  
|<span data-ttu-id="f4b79-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f4b79-112">Symbolic Name</span></span>|<span data-ttu-id="f4b79-113">0</span><span class="sxs-lookup"><span data-stu-id="f4b79-113">0</span></span>|  
|<span data-ttu-id="f4b79-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f4b79-114">Message Text</span></span>|<span data-ttu-id="f4b79-115">無法取得繫結型別的繫結延伸模組"{0}"。</span><span class="sxs-lookup"><span data-stu-id="f4b79-115">Unable to get binding type for binding extension "{0}".</span></span> <span data-ttu-id="f4b79-116">如果您的應用程式開啟時，已更新 machine.config，重新啟動您的應用程式，以收取變更。</span><span class="sxs-lookup"><span data-stu-id="f4b79-116">If machine.config was updated while your application was open, restart your application to pick up changes.</span></span> <span data-ttu-id="f4b79-117">請確認繫結延伸模組已註冊在 machine.config 中</span><span class="sxs-lookup"><span data-stu-id="f4b79-117">Verify the binding extension is registered in machine.config</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f4b79-118">說明</span><span class="sxs-lookup"><span data-stu-id="f4b79-118">Explanation</span></span>  
 <span data-ttu-id="f4b79-119">未正確設定 Wcf-custom 或 Wcf-customisolated 傳輸的自訂繫結延伸模組。</span><span class="sxs-lookup"><span data-stu-id="f4b79-119">A custom binding extension for a WCF-Custom or a WCF-CustomIsolated transport was not configured properly.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f4b79-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f4b79-120">User Action</span></span>  
 <span data-ttu-id="f4b79-121">若要解決這個錯誤會執行下列一或多個項目：</span><span class="sxs-lookup"><span data-stu-id="f4b79-121">To resolve this error do one or more of the following:</span></span>  
  
-   <span data-ttu-id="f4b79-122">請確定**machine.config 檔案**中**%WinDir%\Microsoft.NET\Framework\v4.0.30319\Config**具有\< **bindingExtensions** \>正確設定項目。</span><span class="sxs-lookup"><span data-stu-id="f4b79-122">Ensure the **machine.config file** in **%WinDir%\Microsoft.NET\Framework\v4.0.30319\Config** has the \<**bindingExtensions**\> element configured properly.</span></span>  
  
-   <span data-ttu-id="f4b79-123">在 Windows 檔案總管 中，移至**%WinDir%\Assembly**，並確定實作自訂繫結延伸模組的組件是否已正確安裝。</span><span class="sxs-lookup"><span data-stu-id="f4b79-123">In Windows Explorer, go to **%WinDir%\Assembly**, and make sure the assemblies implementing the custom binding extension are installed properly.</span></span>  
  
-   <span data-ttu-id="f4b79-124">Wcf-custom 配接器在 BizTalk 管理主控台中，重新啟動執行 WCF 傳輸主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="f4b79-124">For the WCF-Custom adapter, in the BizTalk Administration console, restart the host instance running the WCF transport.</span></span>  
  
-   <span data-ttu-id="f4b79-125">Wcf-customisolated 配接器在 IIS 管理主控台中，重新啟動裝載 WCF 傳輸的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="f4b79-125">For the WCF-CustomIsolated adapter, in the IIS Management console, restart the application pool hosting the WCF transport.</span></span>  
  
-   <span data-ttu-id="f4b79-126">開啟和關閉 BizTalk 管理主控台中，如果它已開啟</span><span class="sxs-lookup"><span data-stu-id="f4b79-126">Open and close the BizTalk Administration console if it was opened</span></span>  
  
 <span data-ttu-id="f4b79-127">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="f4b79-127">For further information, see the following resource:</span></span>  
  
-   [<span data-ttu-id="f4b79-128">如何啟用 WCF 擴充性點，WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="f4b79-128">How to Enable the WCF Extensibility Points with the WCF Adapters</span></span>](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md)