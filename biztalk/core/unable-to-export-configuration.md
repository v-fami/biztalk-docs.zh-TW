---
title: 無法匯出設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64f09af4-00a0-47cb-889e-d9aeb7266eb2
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5bb3eb733dcf7c7199282ad4e5512e8d590e8c41
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018780"
---
# <a name="unable-to-export-configuration"></a><span data-ttu-id="cec32-102">無法匯出設定</span><span class="sxs-lookup"><span data-stu-id="cec32-102">Unable to export configuration</span></span>
## <a name="details"></a><span data-ttu-id="cec32-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cec32-103">Details</span></span>  

|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="cec32-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cec32-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="cec32-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="cec32-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="cec32-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cec32-106">Event ID</span></span>     |                                         <span data-ttu-id="cec32-107">0</span><span class="sxs-lookup"><span data-stu-id="cec32-107">0</span></span>                                          |
|  <span data-ttu-id="cec32-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="cec32-108">Event Source</span></span>   |                                         <span data-ttu-id="cec32-109">0</span><span class="sxs-lookup"><span data-stu-id="cec32-109">0</span></span>                                          |
|    <span data-ttu-id="cec32-110">元件</span><span class="sxs-lookup"><span data-stu-id="cec32-110">Component</span></span>    |                                         <span data-ttu-id="cec32-111">0</span><span class="sxs-lookup"><span data-stu-id="cec32-111">0</span></span>                                          |
|  <span data-ttu-id="cec32-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cec32-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="cec32-113">0</span><span class="sxs-lookup"><span data-stu-id="cec32-113">0</span></span>                                          |
|  <span data-ttu-id="cec32-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cec32-114">Message Text</span></span>   |                    <span data-ttu-id="cec32-115">無法將組態匯出到檔案 」{0}"</span><span class="sxs-lookup"><span data-stu-id="cec32-115">Unable to export configuration to file "{0}"</span></span>                    |

## <a name="explanation"></a><span data-ttu-id="cec32-116">說明</span><span class="sxs-lookup"><span data-stu-id="cec32-116">Explanation</span></span>  
 <span data-ttu-id="cec32-117">某些必要的屬性未正確指定，例如位址 (URI) 和繫結類型。</span><span class="sxs-lookup"><span data-stu-id="cec32-117">Some required properties were not correctly specified, such as Address (URI) and Binding Type.</span></span>  

## <a name="user-action"></a><span data-ttu-id="cec32-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cec32-118">User Action</span></span>  
 <span data-ttu-id="cec32-119">您可以使用下列程序來確認屬性正確無誤。</span><span class="sxs-lookup"><span data-stu-id="cec32-119">Use the following procedure to verify properties are correct.</span></span>  

#### <a name="to-verify-properties"></a><span data-ttu-id="cec32-120">若要確認屬性</span><span class="sxs-lookup"><span data-stu-id="cec32-120">To verify properties</span></span>  

1. <span data-ttu-id="cec32-121">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="cec32-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="cec32-122">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="cec32-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  

3. <span data-ttu-id="cec32-123">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="cec32-123">Locate your application and then locate your transport.</span></span>  

4. <span data-ttu-id="cec32-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="cec32-124">Right-click the transport name.</span></span>  

5. <span data-ttu-id="cec32-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="cec32-125">Click **Properties**.</span></span>  

6. <span data-ttu-id="cec32-126">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="cec32-126">In the port **Type** list, select the correct port.</span></span>  

7. <span data-ttu-id="cec32-127">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="cec32-127">Click **Configure**.</span></span>  

8. <span data-ttu-id="cec32-128">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**匯入/匯出**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cec32-128">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Import/Export** tab.</span></span>  

9. <span data-ttu-id="cec32-129">按一下 **[匯出]**。</span><span class="sxs-lookup"><span data-stu-id="cec32-129">Click **Export**.</span></span>  

10. <span data-ttu-id="cec32-130">請確定已正確指定所需的屬性。</span><span class="sxs-lookup"><span data-stu-id="cec32-130">Ensure the required properties have been correctly specified.</span></span> <span data-ttu-id="cec32-131">配置的位址 (URI) 必須正確地符合繫結類型。</span><span class="sxs-lookup"><span data-stu-id="cec32-131">The scheme of the Address (URI) must correctly match the Binding type.</span></span>
