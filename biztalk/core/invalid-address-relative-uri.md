---
title: 無效的位址 (相對 uri) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a953f3e-3768-4e61-8f25-ea958a5a701a
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd362112a8edff37650aaa83da9c6ab33d0d697a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37017396"
---
# <a name="invalid-address-relative-uri"></a><span data-ttu-id="a1596-102">無效的位址 (相對 uri)</span><span class="sxs-lookup"><span data-stu-id="a1596-102">Invalid address (relative uri)</span></span>
## <a name="details"></a><span data-ttu-id="a1596-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a1596-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="a1596-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a1596-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="a1596-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="a1596-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="a1596-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a1596-106">Event ID</span></span>     |                                        <span data-ttu-id="a1596-107">000</span><span class="sxs-lookup"><span data-stu-id="a1596-107">000</span></span>                                         |
|  <span data-ttu-id="a1596-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="a1596-108">Event Source</span></span>   |                                         <span data-ttu-id="a1596-109">0</span><span class="sxs-lookup"><span data-stu-id="a1596-109">0</span></span>                                          |
|    <span data-ttu-id="a1596-110">元件</span><span class="sxs-lookup"><span data-stu-id="a1596-110">Component</span></span>    |                                         <span data-ttu-id="a1596-111">0</span><span class="sxs-lookup"><span data-stu-id="a1596-111">0</span></span>                                          |
|  <span data-ttu-id="a1596-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a1596-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="a1596-113">0</span><span class="sxs-lookup"><span data-stu-id="a1596-113">0</span></span>                                          |
|  <span data-ttu-id="a1596-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a1596-114">Message Text</span></span>   |                  <span data-ttu-id="a1596-115">無效的位址配置;必須是"{0}」 配置。</span><span class="sxs-lookup"><span data-stu-id="a1596-115">Invalid address scheme; expecting "{0}" scheme.</span></span>                   |
  
## <a name="explanation"></a><span data-ttu-id="a1596-116">說明</span><span class="sxs-lookup"><span data-stu-id="a1596-116">Explanation</span></span>  
 <span data-ttu-id="a1596-117">您未提供的外掛式的 WCF 接收位置的語式正確的相對位址。</span><span class="sxs-lookup"><span data-stu-id="a1596-117">You did not provide an isolated WCF receive location with a well-formed relative address.</span></span> <span data-ttu-id="a1596-118">比方說， http://localhost/svc 無法運作，因為相對位址。</span><span class="sxs-lookup"><span data-stu-id="a1596-118">For example, http://localhost/svc will not work as a relative address.</span></span> <span data-ttu-id="a1596-119">您無法設定的位址屬性的外掛式 WCF 接收位置的絕對位址。</span><span class="sxs-lookup"><span data-stu-id="a1596-119">You cannot set the Address property of the isolated WCF receive location to a absolute address.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a1596-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a1596-120">User Action</span></span>  
 <span data-ttu-id="a1596-121">您可以使用下列程序來設定接收位置位址。</span><span class="sxs-lookup"><span data-stu-id="a1596-121">Use the following procedure to configure the receive location address.</span></span>  
  
#### <a name="to-configure-the-receive-location-address"></a><span data-ttu-id="a1596-122">若要設定接收位置位址</span><span class="sxs-lookup"><span data-stu-id="a1596-122">To configure the receive location address</span></span>  
  
1. <span data-ttu-id="a1596-123">按一下 **開始**，按一下**所有程式**，按一下 **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** ，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="a1596-123">Click **Start**, click **All Programs**, click **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="a1596-124">在 [主控台根目錄中，展開**BizTalk Server 管理]**，展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="a1596-124">In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3. <span data-ttu-id="a1596-125">找出您的應用程式，並尋找您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="a1596-125">Locate your application and the locate your transport.</span></span>  
  
4. <span data-ttu-id="a1596-126">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="a1596-126">Right-click the transport name.</span></span>  
  
5. <span data-ttu-id="a1596-127">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="a1596-127">Click **Properties**.</span></span>  
  
6. <span data-ttu-id="a1596-128">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="a1596-128">In the port **Type** list, select the correct port.</span></span>  
  
7. <span data-ttu-id="a1596-129">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="a1596-129">Click **Configure**.</span></span>  
  
8. <span data-ttu-id="a1596-130">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a1596-130">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **General** tab.</span></span>  
  
9. <span data-ttu-id="a1596-131">在 **位址 (URI)** 文字方塊中，變更地址，使其開始以正斜線 （"/"）。</span><span class="sxs-lookup"><span data-stu-id="a1596-131">In the **Address (URI)** text box, change the address so that it starts with a forward slash ("/").</span></span>  
  
   <span data-ttu-id="a1596-132">如需有關接收位置，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="a1596-132">For additional information on receive locations, see the following resources:</span></span>  
  
-   [<span data-ttu-id="a1596-133">如何設定 Wcf-customisolated 接收位置</span><span class="sxs-lookup"><span data-stu-id="a1596-133">How to Configure a WCF-CustomIsolated Receive Location</span></span>](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [<span data-ttu-id="a1596-134">如何設定 Wcf-wshttp 接收位置</span><span class="sxs-lookup"><span data-stu-id="a1596-134">How to Configure a WCF-WSHttp Receive Location</span></span>](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [<span data-ttu-id="a1596-135">如何設定 Wcf-basichttp 接收位置</span><span class="sxs-lookup"><span data-stu-id="a1596-135">How to Configure a WCF-BasicHttp Receive Location</span></span>](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)