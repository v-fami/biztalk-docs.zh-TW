---
title: 無效的 proxy 位址 （適用於傳送處理常式和傳送埠） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ccedd23e-7d44-4419-b519-e04511e1f176
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f509676b17a04fdbe0f0934225b5dc64546fed8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973543"
---
# <a name="invalid-proxy-address-for-send-handler-and-send-port"></a><span data-ttu-id="1c5a9-102">無效的 proxy 位址 （適用於傳送處理常式和傳送埠）</span><span class="sxs-lookup"><span data-stu-id="1c5a9-102">Invalid proxy address (for send handler and send port)</span></span>
## <a name="details"></a><span data-ttu-id="1c5a9-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1c5a9-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="1c5a9-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1c5a9-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="1c5a9-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="1c5a9-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="1c5a9-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1c5a9-106">Event ID</span></span>     |                                         <span data-ttu-id="1c5a9-107">0</span><span class="sxs-lookup"><span data-stu-id="1c5a9-107">0</span></span>                                          |
|  <span data-ttu-id="1c5a9-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="1c5a9-108">Event Source</span></span>   |                                         <span data-ttu-id="1c5a9-109">0</span><span class="sxs-lookup"><span data-stu-id="1c5a9-109">0</span></span>                                          |
|    <span data-ttu-id="1c5a9-110">元件</span><span class="sxs-lookup"><span data-stu-id="1c5a9-110">Component</span></span>    |                                         <span data-ttu-id="1c5a9-111">0</span><span class="sxs-lookup"><span data-stu-id="1c5a9-111">0</span></span>                                          |
|  <span data-ttu-id="1c5a9-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1c5a9-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="1c5a9-113">0</span><span class="sxs-lookup"><span data-stu-id="1c5a9-113">0</span></span>                                          |
|  <span data-ttu-id="1c5a9-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1c5a9-114">Message Text</span></span>   |                             <span data-ttu-id="1c5a9-115">無效的 proxy 位址： {0}</span><span class="sxs-lookup"><span data-stu-id="1c5a9-115">Invalid proxy address: {0}</span></span>                             |
  
## <a name="explanation"></a><span data-ttu-id="1c5a9-116">說明</span><span class="sxs-lookup"><span data-stu-id="1c5a9-116">Explanation</span></span>  
 <span data-ttu-id="1c5a9-117">您未提供 WCF 傳送處理常式] 或 [WCF 傳送有效的 proxy 位址的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="1c5a9-117">You did not provide a WCF send handler or a WCF send port with a valid proxy address.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1c5a9-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1c5a9-118">User Action</span></span>  
 <span data-ttu-id="1c5a9-119">您可以使用下列程序來設定 proxy 位址。</span><span class="sxs-lookup"><span data-stu-id="1c5a9-119">Use the following procedure to configure a proxy address.</span></span>  
  
#### <a name="to-configure-a-proxy-address"></a><span data-ttu-id="1c5a9-120">若要設定的 proxy 位址</span><span class="sxs-lookup"><span data-stu-id="1c5a9-120">To configure a proxy address</span></span>  
  
1. <span data-ttu-id="1c5a9-121">按一下 **開始**，按一下**所有程式**，按一下  **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** ，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="1c5a9-121">Click **Start**, click **All Programs**, click **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="1c5a9-122">在 [主控台根目錄中，展開**BizTalk Server 管理]**，展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="1c5a9-122">In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3. <span data-ttu-id="1c5a9-123">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="1c5a9-123">Locate your application and then locate your transport.</span></span>  
  
4. <span data-ttu-id="1c5a9-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="1c5a9-124">Right-click the transport name.</span></span>  
  
5. <span data-ttu-id="1c5a9-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="1c5a9-125">Click **Properties**.</span></span>  
  
6. <span data-ttu-id="1c5a9-126">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="1c5a9-126">In the port **Type** list, select the correct port.</span></span>  
  
7. <span data-ttu-id="1c5a9-127">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="1c5a9-127">Click **Configure**.</span></span>  
  
8. <span data-ttu-id="1c5a9-128">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [ **Proxy** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1c5a9-128">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Proxy** tab.</span></span>  
  
9. <span data-ttu-id="1c5a9-129">確認中的 proxy 位址**Proxy 設定**區段的設定正確。</span><span class="sxs-lookup"><span data-stu-id="1c5a9-129">Verify that the proxy address in the **Proxy settings** section is configured properly.</span></span>  
  
   <span data-ttu-id="1c5a9-130">如需有關傳送埠與傳送處理常式的詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="1c5a9-130">For additional information on send ports and send handlers, see the following resources:</span></span>  
  
-   [<span data-ttu-id="1c5a9-131">如何設定 Wcf-wshttp 傳送埠</span><span class="sxs-lookup"><span data-stu-id="1c5a9-131">How to Configure a WCF-WSHttp Send Port</span></span>](../core/how-to-configure-a-wcf-wshttp-send-port.md)  
  
-   [<span data-ttu-id="1c5a9-132">如何設定 Wcf-basichttp 傳送埠</span><span class="sxs-lookup"><span data-stu-id="1c5a9-132">How to Configure a WCF-BasicHttp Send Port</span></span>](http://msdn.microsoft.com/library/acdb50fa-57fe-4657-9561-b6b2f4919c7f)  
  
-   [<span data-ttu-id="1c5a9-133">如何設定 Wcf-basichttp 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="1c5a9-133">How to Configure a WCF-BasicHttp Send Handler</span></span>](http://msdn.microsoft.com/library/18dcc616-4732-42f8-bd64-e55a5ebbaa49)  
  
-   [<span data-ttu-id="1c5a9-134">如何設定 Wcf-wshttp 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="1c5a9-134">How to Configure a WCF-WSHttp Send Handler</span></span>](../core/how-to-configure-a-wcf-wshttp-send-handler.md)  
  
-   [<span data-ttu-id="1c5a9-135">如何設定 Wcf-custom 傳送埠</span><span class="sxs-lookup"><span data-stu-id="1c5a9-135">How to Configure a WCF-Custom Send Port</span></span>](../core/how-to-configure-a-wcf-custom-send-port.md)