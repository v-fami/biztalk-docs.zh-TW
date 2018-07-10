---
title: 必要的屬性繫結類型未指定 (R2) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c8e45783-6454-44e2-867e-e30092725f51
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9851095ec9fac42faae4af149d0023d4b65ea05
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022860"
---
# <a name="required-property-binding-type-not-specified-r2"></a><span data-ttu-id="8092d-102">未指定必要的繫結類型屬性 (R2)</span><span class="sxs-lookup"><span data-stu-id="8092d-102">Required property binding type not specified (R2)</span></span>
## <a name="details"></a><span data-ttu-id="8092d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8092d-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="8092d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8092d-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="8092d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="8092d-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="8092d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8092d-106">Event ID</span></span>     |                                         <span data-ttu-id="8092d-107">0</span><span class="sxs-lookup"><span data-stu-id="8092d-107">0</span></span>                                          |
|  <span data-ttu-id="8092d-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="8092d-108">Event Source</span></span>   |                                         <span data-ttu-id="8092d-109">0</span><span class="sxs-lookup"><span data-stu-id="8092d-109">0</span></span>                                          |
|    <span data-ttu-id="8092d-110">元件</span><span class="sxs-lookup"><span data-stu-id="8092d-110">Component</span></span>    |                                         <span data-ttu-id="8092d-111">0</span><span class="sxs-lookup"><span data-stu-id="8092d-111">0</span></span>                                          |
|  <span data-ttu-id="8092d-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8092d-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="8092d-113">0</span><span class="sxs-lookup"><span data-stu-id="8092d-113">0</span></span>                                          |
|  <span data-ttu-id="8092d-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8092d-114">Message Text</span></span>   |                    <span data-ttu-id="8092d-115">未指定必要的繫結類型屬性</span><span class="sxs-lookup"><span data-stu-id="8092d-115">Required property Binding Type not specified</span></span>                    |
  
## <a name="explanation"></a><span data-ttu-id="8092d-116">說明</span><span class="sxs-lookup"><span data-stu-id="8092d-116">Explanation</span></span>  
 <span data-ttu-id="8092d-117">設定 WCF-Custom 或 WCF-CustomIsolated 傳輸時，您未設定 [繫結類型] 屬性。</span><span class="sxs-lookup"><span data-stu-id="8092d-117">You did not set the Binding Type property when configuring a WCF-Custom or a WCF-CustomIsolated transport.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8092d-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8092d-118">User Action</span></span>  
 <span data-ttu-id="8092d-119">您可以使用下列程序來設定繫結類型屬性。</span><span class="sxs-lookup"><span data-stu-id="8092d-119">Use the following procedure to configure the binding type property.</span></span>  
  
#### <a name="to-configure-the-binding-type-property"></a><span data-ttu-id="8092d-120">若要設定的繫結類型屬性</span><span class="sxs-lookup"><span data-stu-id="8092d-120">To configure the binding type property</span></span>  
  
1. <span data-ttu-id="8092d-121">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="8092d-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="8092d-122">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="8092d-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3. <span data-ttu-id="8092d-123">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="8092d-123">Locate your application and then locate your transport.</span></span>  
  
4. <span data-ttu-id="8092d-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="8092d-124">Right-click the transport name.</span></span>  
  
5. <span data-ttu-id="8092d-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="8092d-125">Click **Properties**.</span></span>  
  
6. <span data-ttu-id="8092d-126">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="8092d-126">In the port **Type** list, select the correct port.</span></span>  
  
7. <span data-ttu-id="8092d-127">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="8092d-127">Click **Configure**.</span></span>  
  
8. <span data-ttu-id="8092d-128">在 [ **WCF-[**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**繫結**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8092d-128">In the **WCF--[**<em>transport type</em>**] Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="8092d-129">中指定值**繫結的型別**清單。</span><span class="sxs-lookup"><span data-stu-id="8092d-129">Specify a value in the **Binding Type** list.</span></span>  
  
   <span data-ttu-id="8092d-130">如需有關如何設定繫結的詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="8092d-130">For additional information on configuring binding, see the following resources:</span></span>  
  
-   [<span data-ttu-id="8092d-131">如何設定 Wcf-customisolated 接收位置</span><span class="sxs-lookup"><span data-stu-id="8092d-131">How to Configure a WCF-CustomIsolated Receive Location</span></span>](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [<span data-ttu-id="8092d-132">如何設定 Wcf-custom 接收位置</span><span class="sxs-lookup"><span data-stu-id="8092d-132">How to Configure a WCF-Custom Receive Location</span></span>](../core/how-to-configure-a-wcf-custom-receive-location.md)  
  
-   [<span data-ttu-id="8092d-133">如何設定 Wcf-custom 傳送埠</span><span class="sxs-lookup"><span data-stu-id="8092d-133">How to Configure a WCF-Custom Send Port</span></span>](../core/how-to-configure-a-wcf-custom-send-port.md)