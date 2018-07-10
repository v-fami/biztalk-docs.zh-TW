---
title: 無法建立身分識別 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 531f1057-1b6d-40ae-bf2f-a36baf4e0341
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 203257b261bba176b0a768da8242dad45366a923
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998111"
---
# <a name="failed-to-create-identity"></a><span data-ttu-id="98f12-102">無法建立身分識別</span><span class="sxs-lookup"><span data-stu-id="98f12-102">Failed to create identity</span></span>
## <a name="details"></a><span data-ttu-id="98f12-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="98f12-103">Details</span></span>  

|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="98f12-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="98f12-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="98f12-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="98f12-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="98f12-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="98f12-106">Event ID</span></span>     |                                         <span data-ttu-id="98f12-107">0</span><span class="sxs-lookup"><span data-stu-id="98f12-107">0</span></span>                                          |
|  <span data-ttu-id="98f12-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="98f12-108">Event Source</span></span>   |                                         <span data-ttu-id="98f12-109">0</span><span class="sxs-lookup"><span data-stu-id="98f12-109">0</span></span>                                          |
|    <span data-ttu-id="98f12-110">元件</span><span class="sxs-lookup"><span data-stu-id="98f12-110">Component</span></span>    |                                         <span data-ttu-id="98f12-111">0</span><span class="sxs-lookup"><span data-stu-id="98f12-111">0</span></span>                                          |
|  <span data-ttu-id="98f12-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="98f12-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="98f12-113">0</span><span class="sxs-lookup"><span data-stu-id="98f12-113">0</span></span>                                          |
|  <span data-ttu-id="98f12-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="98f12-114">Message Text</span></span>   |      <span data-ttu-id="98f12-115">此錯誤表示配接器無法建立端點身分識別。</span><span class="sxs-lookup"><span data-stu-id="98f12-115">This error indicates the adapter failed to create the endpoint identity.</span></span>      |

## <a name="explanation"></a><span data-ttu-id="98f12-116">說明</span><span class="sxs-lookup"><span data-stu-id="98f12-116">Explanation</span></span>  
 <span data-ttu-id="98f12-117">此錯誤表示配接器無法建立端點身分識別。</span><span class="sxs-lookup"><span data-stu-id="98f12-117">This error indicates the adapter failed to create the endpoint identity.</span></span>  

## <a name="user-action"></a><span data-ttu-id="98f12-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="98f12-118">User Action</span></span>  
 <span data-ttu-id="98f12-119">您可以使用下列程序來設定的端點身分識別。</span><span class="sxs-lookup"><span data-stu-id="98f12-119">Use the following procedure to configure the endpoint identity.</span></span>  

#### <a name="to-configure-the-endpoint-identity"></a><span data-ttu-id="98f12-120">若要設定的端點身分識別</span><span class="sxs-lookup"><span data-stu-id="98f12-120">To configure the endpoint identity</span></span>  

1. <span data-ttu-id="98f12-121">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="98f12-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="98f12-122">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="98f12-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  

3. <span data-ttu-id="98f12-123">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="98f12-123">Locate your application and then locate your transport.</span></span>  

4. <span data-ttu-id="98f12-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="98f12-124">Right-click the transport name.</span></span>  

5. <span data-ttu-id="98f12-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="98f12-125">Click **Properties**.</span></span>  

6. <span data-ttu-id="98f12-126">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="98f12-126">In the port **Type** list, select the correct port.</span></span>  

7. <span data-ttu-id="98f12-127">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="98f12-127">Click **Configure**.</span></span>  

8. <span data-ttu-id="98f12-128">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="98f12-128">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **General** tab.</span></span>  

9. <span data-ttu-id="98f12-129">在 **端點身分識別**區段中，按一下**編輯**。</span><span class="sxs-lookup"><span data-stu-id="98f12-129">In the **Endpoint Identity** section, click **Edit**.</span></span>  

10. <span data-ttu-id="98f12-130">在 **識別編輯器**對話方塊方塊中，確認設定是否有效。</span><span class="sxs-lookup"><span data-stu-id="98f12-130">In the **Identity Editor** dialog box, ensure that the settings are valid.</span></span>
