---
title: WCF 用戶端必須允許模擬使用單一登入 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b5b9f294-4d8a-4a12-91e8-8d325db7c420
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2d5ebfc9853f10417c1d2ad2c41a0d2531ff6de
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971471"
---
# <a name="wcf-client-must-allow-impersonation-to-use-single-sign-on"></a><span data-ttu-id="6360e-102">WCF 用戶端必須允許模擬使用單一登入</span><span class="sxs-lookup"><span data-stu-id="6360e-102">WCF client must allow impersonation to use Single Sign-On</span></span>
## <a name="details"></a><span data-ttu-id="6360e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6360e-103">Details</span></span>  

|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="6360e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6360e-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="6360e-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="6360e-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="6360e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6360e-106">Event ID</span></span>     |                                         <span data-ttu-id="6360e-107">0</span><span class="sxs-lookup"><span data-stu-id="6360e-107">0</span></span>                                          |
|  <span data-ttu-id="6360e-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="6360e-108">Event Source</span></span>   |                                         <span data-ttu-id="6360e-109">0</span><span class="sxs-lookup"><span data-stu-id="6360e-109">0</span></span>                                          |
|    <span data-ttu-id="6360e-110">元件</span><span class="sxs-lookup"><span data-stu-id="6360e-110">Component</span></span>    |                                         <span data-ttu-id="6360e-111">0</span><span class="sxs-lookup"><span data-stu-id="6360e-111">0</span></span>                                          |
|  <span data-ttu-id="6360e-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6360e-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="6360e-113">0</span><span class="sxs-lookup"><span data-stu-id="6360e-113">0</span></span>                                          |
|  <span data-ttu-id="6360e-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6360e-114">Message Text</span></span>   |           <span data-ttu-id="6360e-115">WCF 用戶端必須允許模擬使用單一登入</span><span class="sxs-lookup"><span data-stu-id="6360e-115">The WCF client must allow impersonation to use Single Sign-On</span></span>            |

## <a name="explanation"></a><span data-ttu-id="6360e-116">說明</span><span class="sxs-lookup"><span data-stu-id="6360e-116">Explanation</span></span>  
 <span data-ttu-id="6360e-117">在 接收位置中啟用單一登入 (SSO)，但 WCF 用戶端不允許模擬。</span><span class="sxs-lookup"><span data-stu-id="6360e-117">Single Sign-On (SSO) is enabled in the receive location but the WCF client does not allow impersonation.</span></span>  

## <a name="user-action"></a><span data-ttu-id="6360e-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6360e-118">User Action</span></span>  
 <span data-ttu-id="6360e-119">請確定叫用服務的 WCF 用戶端允許模擬。</span><span class="sxs-lookup"><span data-stu-id="6360e-119">Ensure that the WCF client invoking the service allows impersonation.</span></span>  

1. <span data-ttu-id="6360e-120">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="6360e-120">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="6360e-121">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="6360e-121">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  

3. <span data-ttu-id="6360e-122">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="6360e-122">Locate your application and then locate your transport.</span></span>  

4. <span data-ttu-id="6360e-123">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="6360e-123">Right-click the transport name.</span></span>  

5. <span data-ttu-id="6360e-124">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="6360e-124">Click **Properties**.</span></span>  

6. <span data-ttu-id="6360e-125">在 連接埠**型別**清單中，選取**Wcf-custom** (或**WCF CustomIsolate**)。</span><span class="sxs-lookup"><span data-stu-id="6360e-125">In the port **Type** list, select **WCF-Custom** (or **WCF-CustomIsolate**).</span></span>  

7. <span data-ttu-id="6360e-126">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="6360e-126">Click **Configure**.</span></span>  

8. <span data-ttu-id="6360e-127">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**行為**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6360e-127">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Behavior** tab.</span></span>  

9. <span data-ttu-id="6360e-128">在 **行為**區段中，按一下**ServiceAuthorization**。</span><span class="sxs-lookup"><span data-stu-id="6360e-128">In the **Behavior** section, click **ServiceAuthorization**.</span></span> <span data-ttu-id="6360e-129">在 **組態**區段中，屬性**ImpersonateCallerForAllOperations**應該設定為 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="6360e-129">In the **Configuration** section, the property **ImpersonateCallerForAllOperations** should be set to **True**.</span></span>  

10. <span data-ttu-id="6360e-130">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**其他**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6360e-130">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Other** tab.</span></span>  

11. <span data-ttu-id="6360e-131">在認證章節中，選取選項**使用單一登入**。</span><span class="sxs-lookup"><span data-stu-id="6360e-131">In the Credentials sections, select the option **Use Single Sign-On**.</span></span>
