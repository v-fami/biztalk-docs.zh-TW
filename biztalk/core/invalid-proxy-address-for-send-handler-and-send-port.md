---
title: 無效的 proxy 位址 （用於傳送處理常式和傳送埠） |Microsoft 文件
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
ms.openlocfilehash: d33af2f4fa068294c38ecb4146cd1f8d05d68aea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257814"
---
# <a name="invalid-proxy-address-for-send-handler-and-send-port"></a><span data-ttu-id="3ad81-102">無效的 proxy 位址 （用於傳送處理常式和傳送埠）</span><span class="sxs-lookup"><span data-stu-id="3ad81-102">Invalid proxy address (for send handler and send port)</span></span>
## <a name="details"></a><span data-ttu-id="3ad81-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3ad81-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3ad81-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3ad81-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="3ad81-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="3ad81-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="3ad81-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3ad81-106">Event ID</span></span>|<span data-ttu-id="3ad81-107">0</span><span class="sxs-lookup"><span data-stu-id="3ad81-107">0</span></span>|  
|<span data-ttu-id="3ad81-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="3ad81-108">Event Source</span></span>|<span data-ttu-id="3ad81-109">0</span><span class="sxs-lookup"><span data-stu-id="3ad81-109">0</span></span>|  
|<span data-ttu-id="3ad81-110">元件</span><span class="sxs-lookup"><span data-stu-id="3ad81-110">Component</span></span>|<span data-ttu-id="3ad81-111">0</span><span class="sxs-lookup"><span data-stu-id="3ad81-111">0</span></span>|  
|<span data-ttu-id="3ad81-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3ad81-112">Symbolic Name</span></span>|<span data-ttu-id="3ad81-113">0</span><span class="sxs-lookup"><span data-stu-id="3ad81-113">0</span></span>|  
|<span data-ttu-id="3ad81-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3ad81-114">Message Text</span></span>|<span data-ttu-id="3ad81-115">無效的 proxy 位址： {0}</span><span class="sxs-lookup"><span data-stu-id="3ad81-115">Invalid proxy address: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3ad81-116">說明</span><span class="sxs-lookup"><span data-stu-id="3ad81-116">Explanation</span></span>  
 <span data-ttu-id="3ad81-117">未提供 WCF 傳送處理常式或 WCF 傳送埠具有有效的 proxy 位址。</span><span class="sxs-lookup"><span data-stu-id="3ad81-117">You did not provide a WCF send handler or a WCF send port with a valid proxy address.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3ad81-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3ad81-118">User Action</span></span>  
 <span data-ttu-id="3ad81-119">您可以使用下列程序來設定 proxy 位址。</span><span class="sxs-lookup"><span data-stu-id="3ad81-119">Use the following procedure to configure a proxy address.</span></span>  
  
#### <a name="to-configure-a-proxy-address"></a><span data-ttu-id="3ad81-120">若要設定的 proxy 位址</span><span class="sxs-lookup"><span data-stu-id="3ad81-120">To configure a proxy address</span></span>  
  
1.  <span data-ttu-id="3ad81-121">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** ，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="3ad81-121">Click **Start**, click **All Programs**, click **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="3ad81-122">在 主控台根目錄中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="3ad81-122">In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="3ad81-123">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="3ad81-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="3ad81-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="3ad81-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="3ad81-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="3ad81-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="3ad81-126">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="3ad81-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="3ad81-127">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="3ad81-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="3ad81-128">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [ **Proxy** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3ad81-128">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Proxy** tab.</span></span>  
  
9. <span data-ttu-id="3ad81-129">確認中的 proxy 位址**Proxy 設定**區段已正確設定。</span><span class="sxs-lookup"><span data-stu-id="3ad81-129">Verify that the proxy address in the **Proxy settings** section is configured properly.</span></span>  
  
 <span data-ttu-id="3ad81-130">如需有關傳送埠與傳送處理常式的詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="3ad81-130">For additional information on send ports and send handlers, see the following resources:</span></span>  
  
-   [<span data-ttu-id="3ad81-131">如何設定 Wcf-wshttp 傳送埠</span><span class="sxs-lookup"><span data-stu-id="3ad81-131">How to Configure a WCF-WSHttp Send Port</span></span>](../core/how-to-configure-a-wcf-wshttp-send-port.md)  
  
-   [<span data-ttu-id="3ad81-132">如何設定 Wcf-basichttp 傳送埠</span><span class="sxs-lookup"><span data-stu-id="3ad81-132">How to Configure a WCF-BasicHttp Send Port</span></span>](http://msdn.microsoft.com/library/acdb50fa-57fe-4657-9561-b6b2f4919c7f)  
  
-   [<span data-ttu-id="3ad81-133">如何設定 Wcf-basichttp 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="3ad81-133">How to Configure a WCF-BasicHttp Send Handler</span></span>](http://msdn.microsoft.com/library/18dcc616-4732-42f8-bd64-e55a5ebbaa49)  
  
-   [<span data-ttu-id="3ad81-134">如何設定 Wcf-wshttp 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="3ad81-134">How to Configure a WCF-WSHttp Send Handler</span></span>](../core/how-to-configure-a-wcf-wshttp-send-handler.md)  
  
-   [<span data-ttu-id="3ad81-135">如何設定 Wcf-custom 傳送埠</span><span class="sxs-lookup"><span data-stu-id="3ad81-135">How to Configure a WCF-Custom Send Port</span></span>](../core/how-to-configure-a-wcf-custom-send-port.md)