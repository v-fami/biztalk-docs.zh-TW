---
title: 無效的位址 (相對 uri 需要斜線 (&quot;-&quot;)) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1376f924-f119-4ba8-9be1-eea7ba5f3eb6
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa1c43d4a86af788c67ea59c7bf0ca7dea43da39
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257566"
---
# <a name="invalid-address-relative-uri-needs-slash-quot-quot"></a><span data-ttu-id="fea96-102">無效的位址 (相對 uri 需要斜線 (&quot;-&quot;))</span><span class="sxs-lookup"><span data-stu-id="fea96-102">Invalid address (relative uri needs slash (&quot;-&quot;))</span></span>
## <a name="details"></a><span data-ttu-id="fea96-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fea96-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fea96-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="fea96-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="fea96-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="fea96-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="fea96-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fea96-106">Event ID</span></span>|<span data-ttu-id="fea96-107">0</span><span class="sxs-lookup"><span data-stu-id="fea96-107">0</span></span>|  
|<span data-ttu-id="fea96-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="fea96-108">Event Source</span></span>|<span data-ttu-id="fea96-109">0</span><span class="sxs-lookup"><span data-stu-id="fea96-109">0</span></span>|  
|<span data-ttu-id="fea96-110">元件</span><span class="sxs-lookup"><span data-stu-id="fea96-110">Component</span></span>|<span data-ttu-id="fea96-111">0</span><span class="sxs-lookup"><span data-stu-id="fea96-111">0</span></span>|  
|<span data-ttu-id="fea96-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="fea96-112">Symbolic Name</span></span>|<span data-ttu-id="fea96-113">0</span><span class="sxs-lookup"><span data-stu-id="fea96-113">0</span></span>|  
|<span data-ttu-id="fea96-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="fea96-114">Message Text</span></span>|<span data-ttu-id="fea96-115">無效的位址。必須是相對 uri 開頭為斜線 （"/"）</span><span class="sxs-lookup"><span data-stu-id="fea96-115">Invalid address; expecting relative uri starting with slash ("/")</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fea96-116">說明</span><span class="sxs-lookup"><span data-stu-id="fea96-116">Explanation</span></span>  
 <span data-ttu-id="fea96-117">您未提供為外掛式的 WCF 接收位置與格式不正確的相對位址。</span><span class="sxs-lookup"><span data-stu-id="fea96-117">You did not provide an isolated WCF receive location with a well-formed relative address.</span></span> <span data-ttu-id="fea96-118">例如，http://localhost/svc 將無法運作為相對位址。</span><span class="sxs-lookup"><span data-stu-id="fea96-118">For example, http://localhost/svc will not work as a relative address.</span></span> <span data-ttu-id="fea96-119">您無法將設定的位址屬性的外掛式 WCF 接收位置的絕對位址。</span><span class="sxs-lookup"><span data-stu-id="fea96-119">You cannot set the Address property of the isolated WCF receive location to a absolute address.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fea96-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="fea96-120">User Action</span></span>  
 <span data-ttu-id="fea96-121">您可以使用下列程序來設定地址。</span><span class="sxs-lookup"><span data-stu-id="fea96-121">Use the following procedure to configure an address.</span></span>  
  
#### <a name="to-configure-an-address"></a><span data-ttu-id="fea96-122">若要設定的位址</span><span class="sxs-lookup"><span data-stu-id="fea96-122">To configure an address</span></span>  
  
1.  <span data-ttu-id="fea96-123">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** ，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="fea96-123">Click **Start**, click **All Programs**, click **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="fea96-124">在 主控台根目錄中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="fea96-124">In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="fea96-125">找出您的應用程式，並找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="fea96-125">Locate your application and locate your transport.</span></span>  
  
4.  <span data-ttu-id="fea96-126">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="fea96-126">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="fea96-127">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="fea96-127">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="fea96-128">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="fea96-128">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="fea96-129">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="fea96-129">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="fea96-130">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fea96-130">In the **WCF [***transport type***] Transport Properties** dialog box, click the **General** tab.</span></span>  
  
9. <span data-ttu-id="fea96-131">在**位址 (URI)** 文字方塊中，變更地址。</span><span class="sxs-lookup"><span data-stu-id="fea96-131">In the **Address (URI)** text box, change the address.</span></span> <span data-ttu-id="fea96-132">舉例來說，語式正確的相對位址是 /path/service.svc。</span><span class="sxs-lookup"><span data-stu-id="fea96-132">An example of a well-formed relative address is /path/service.svc.</span></span>  
  
 <span data-ttu-id="fea96-133">如需有關接收位置，請參閱下列內容：</span><span class="sxs-lookup"><span data-stu-id="fea96-133">For additional information on receive locations, see the following:</span></span>  
  
-   [<span data-ttu-id="fea96-134">如何設定 Wcf-customisolated 接收位置</span><span class="sxs-lookup"><span data-stu-id="fea96-134">How to Configure a WCF-CustomIsolated Receive Location</span></span>](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [<span data-ttu-id="fea96-135">如何設定 Wcf-wshttp 接收位置</span><span class="sxs-lookup"><span data-stu-id="fea96-135">How to Configure a WCF-WSHttp Receive Location</span></span>](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [<span data-ttu-id="fea96-136">如何設定 Wcf-basichttp 接收位置</span><span class="sxs-lookup"><span data-stu-id="fea96-136">How to Configure a WCF-BasicHttp Receive Location</span></span>](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)