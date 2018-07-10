---
title: 交易式要求-回應接收位置不支援 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6c89b619-280c-4ab5-b6aa-06b14a075f8e
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ddcc173a751fb104e86047f3f2e59be8524f7ab9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022724"
---
# <a name="transactional-request-response-receive-location-is-not-supported"></a><span data-ttu-id="f1243-102">交易式要求-回應接收位置不支援</span><span class="sxs-lookup"><span data-stu-id="f1243-102">Transactional request-response receive location is not supported</span></span>
## <a name="details"></a><span data-ttu-id="f1243-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f1243-103">Details</span></span>  

|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="f1243-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f1243-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="f1243-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f1243-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="f1243-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f1243-106">Event ID</span></span>     |                                         <span data-ttu-id="f1243-107">0</span><span class="sxs-lookup"><span data-stu-id="f1243-107">0</span></span>                                          |
|  <span data-ttu-id="f1243-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="f1243-108">Event Source</span></span>   |                                         <span data-ttu-id="f1243-109">0</span><span class="sxs-lookup"><span data-stu-id="f1243-109">0</span></span>                                          |
|    <span data-ttu-id="f1243-110">元件</span><span class="sxs-lookup"><span data-stu-id="f1243-110">Component</span></span>    |                                         <span data-ttu-id="f1243-111">0</span><span class="sxs-lookup"><span data-stu-id="f1243-111">0</span></span>                                          |
|  <span data-ttu-id="f1243-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f1243-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="f1243-113">0</span><span class="sxs-lookup"><span data-stu-id="f1243-113">0</span></span>                                          |
|  <span data-ttu-id="f1243-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f1243-114">Message Text</span></span>   |         <span data-ttu-id="f1243-115">交易式要求-回應接收位置不支援。</span><span class="sxs-lookup"><span data-stu-id="f1243-115">Transactional request-response receive location is not supported.</span></span>          |

## <a name="explanation"></a><span data-ttu-id="f1243-116">說明</span><span class="sxs-lookup"><span data-stu-id="f1243-116">Explanation</span></span>  
 <span data-ttu-id="f1243-117">此錯誤表示交易已設定來啟用應用程式的 WCF 要求-回應接收位置。</span><span class="sxs-lookup"><span data-stu-id="f1243-117">This error indicates that the transaction was set to be enabled for a WCF request-response receive location.</span></span> <span data-ttu-id="f1243-118">不支援交易在 BizTalk 中針對要求-回應接收位置，因為 message box 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f1243-118">Transactions are not supported in BizTalk for a request-response receive location due to the message box database.</span></span>  

## <a name="user-action"></a><span data-ttu-id="f1243-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f1243-119">User Action</span></span>  
 <span data-ttu-id="f1243-120">標準的 WCF 配接器，請移至 設定要求-回應的程式碼會接收位置。</span><span class="sxs-lookup"><span data-stu-id="f1243-120">For the standard WCF adapters, go to the code configuring the request-response receive location.</span></span> <span data-ttu-id="f1243-121">請確認**EnableTransaction**的 XML 資料中的項目**TransportTypeData**屬性**ITransportInfo**介面設定為**False**.</span><span class="sxs-lookup"><span data-stu-id="f1243-121">Ensure that the **EnableTransaction** element in the XML data for the **TransportTypeData** property of the **ITransportInfo** interface is set to **False**.</span></span>  

 <span data-ttu-id="f1243-122">Wcf-custom 配接器：</span><span class="sxs-lookup"><span data-stu-id="f1243-122">For the WCF-Custom adapters:</span></span>  

1. <span data-ttu-id="f1243-123">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="f1243-123">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="f1243-124">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="f1243-124">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.</span></span>  

3. <span data-ttu-id="f1243-125">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="f1243-125">Locate your application and then locate your transport.</span></span>  

4. <span data-ttu-id="f1243-126">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="f1243-126">Right-click the transport name.</span></span>  

5. <span data-ttu-id="f1243-127">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="f1243-127">Click **Properties**.</span></span>  

6. <span data-ttu-id="f1243-128">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="f1243-128">In the port **Type** list, select the correct port.</span></span>  

7. <span data-ttu-id="f1243-129">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="f1243-129">Click **Configure**.</span></span>  

8. <span data-ttu-id="f1243-130">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**繫結**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f1243-130">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Binding** tab.</span></span>  

9. <span data-ttu-id="f1243-131">請確定 transactionFlow 屬性設定為**False**。</span><span class="sxs-lookup"><span data-stu-id="f1243-131">Ensure that the transactionFlow property is set to **False**.</span></span>
