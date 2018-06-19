---
title: 無法匯出組態 |Microsoft 文件
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
ms.openlocfilehash: 0bd7f27a2779819fff934008cc9924dfe01e6064
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286846"
---
# <a name="unable-to-export-configuration"></a><span data-ttu-id="49153-102">無法匯出組態</span><span class="sxs-lookup"><span data-stu-id="49153-102">Unable to export configuration</span></span>
## <a name="details"></a><span data-ttu-id="49153-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="49153-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="49153-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="49153-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="49153-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="49153-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="49153-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="49153-106">Event ID</span></span>|<span data-ttu-id="49153-107">0</span><span class="sxs-lookup"><span data-stu-id="49153-107">0</span></span>|  
|<span data-ttu-id="49153-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="49153-108">Event Source</span></span>|<span data-ttu-id="49153-109">0</span><span class="sxs-lookup"><span data-stu-id="49153-109">0</span></span>|  
|<span data-ttu-id="49153-110">元件</span><span class="sxs-lookup"><span data-stu-id="49153-110">Component</span></span>|<span data-ttu-id="49153-111">0</span><span class="sxs-lookup"><span data-stu-id="49153-111">0</span></span>|  
|<span data-ttu-id="49153-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="49153-112">Symbolic Name</span></span>|<span data-ttu-id="49153-113">0</span><span class="sxs-lookup"><span data-stu-id="49153-113">0</span></span>|  
|<span data-ttu-id="49153-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="49153-114">Message Text</span></span>|<span data-ttu-id="49153-115">無法匯出組態檔"{0}"</span><span class="sxs-lookup"><span data-stu-id="49153-115">Unable to export configuration to file "{0}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="49153-116">說明</span><span class="sxs-lookup"><span data-stu-id="49153-116">Explanation</span></span>  
 <span data-ttu-id="49153-117">某些必要的屬性未正確指定，例如位址 (URI) 和繫結類型。</span><span class="sxs-lookup"><span data-stu-id="49153-117">Some required properties were not correctly specified, such as Address (URI) and Binding Type.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="49153-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="49153-118">User Action</span></span>  
 <span data-ttu-id="49153-119">您可以使用下列程序來驗證屬性正確無誤。</span><span class="sxs-lookup"><span data-stu-id="49153-119">Use the following procedure to verify properties are correct.</span></span>  
  
#### <a name="to-verify-properties"></a><span data-ttu-id="49153-120">若要確認屬性</span><span class="sxs-lookup"><span data-stu-id="49153-120">To verify properties</span></span>  
  
1.  <span data-ttu-id="49153-121">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="49153-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="49153-122">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="49153-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="49153-123">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="49153-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="49153-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="49153-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="49153-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="49153-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="49153-126">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="49153-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="49153-127">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="49153-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="49153-128">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**匯入/匯出**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="49153-128">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Import/Export** tab.</span></span>  
  
9. <span data-ttu-id="49153-129">按一下 **[匯出]**。</span><span class="sxs-lookup"><span data-stu-id="49153-129">Click **Export**.</span></span>  
  
10. <span data-ttu-id="49153-130">請確定已正確指定必要的屬性。</span><span class="sxs-lookup"><span data-stu-id="49153-130">Ensure the required properties have been correctly specified.</span></span> <span data-ttu-id="49153-131">配置的位址 (URI) 必須正確地符合繫結型別。</span><span class="sxs-lookup"><span data-stu-id="49153-131">The scheme of the Address (URI) must correctly match the Binding type.</span></span>