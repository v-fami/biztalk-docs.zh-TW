---
title: "衝突的繫結屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b08c317e-a617-464b-9ee4-007fb41d99b2
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6202385127a676d1f2714b2c3644d135a3d6a7a1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="conflicting-binding-properties"></a><span data-ttu-id="d05a5-102">衝突的繫結屬性</span><span class="sxs-lookup"><span data-stu-id="d05a5-102">Conflicting binding properties</span></span>
## <a name="details"></a><span data-ttu-id="d05a5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d05a5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d05a5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d05a5-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d05a5-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d05a5-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="d05a5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d05a5-106">Event ID</span></span>|<span data-ttu-id="d05a5-107">0</span><span class="sxs-lookup"><span data-stu-id="d05a5-107">0</span></span>|  
|<span data-ttu-id="d05a5-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="d05a5-108">Event Source</span></span>|<span data-ttu-id="d05a5-109">0</span><span class="sxs-lookup"><span data-stu-id="d05a5-109">0</span></span>|  
|<span data-ttu-id="d05a5-110">元件</span><span class="sxs-lookup"><span data-stu-id="d05a5-110">Component</span></span>|<span data-ttu-id="d05a5-111">0</span><span class="sxs-lookup"><span data-stu-id="d05a5-111">0</span></span>|  
|<span data-ttu-id="d05a5-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d05a5-112">Symbolic Name</span></span>|<span data-ttu-id="d05a5-113">0</span><span class="sxs-lookup"><span data-stu-id="d05a5-113">0</span></span>|  
|<span data-ttu-id="d05a5-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d05a5-114">Message Text</span></span>|<span data-ttu-id="d05a5-115">衝突的繫結屬性： MsmqAuthenticationMode = {0}，而 MsmqProtectionLevel = \ {1 \} 無效。</span><span class="sxs-lookup"><span data-stu-id="d05a5-115">Conflicting binding properties: MsmqAuthenticationMode={0} and MsmqProtectionLevel={1} is invalid.</span></span> <span data-ttu-id="d05a5-116">變更其中一個來解決衝突的屬性</span><span class="sxs-lookup"><span data-stu-id="d05a5-116">Change one of the properties to resolve the conflict</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d05a5-117">說明</span><span class="sxs-lookup"><span data-stu-id="d05a5-117">Explanation</span></span>  
 <span data-ttu-id="d05a5-118">Wcf-netmsmq 傳輸的 MSMQ 保護層級屬性設定為**登**或**EncryptAndSign**無 MSMQ 驗證模式。</span><span class="sxs-lookup"><span data-stu-id="d05a5-118">The MSMQ protection level property of a WCF-NetMsmq transport was set to **Sign** or **EncryptAndSign** for the None MSMQ authentication mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d05a5-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d05a5-119">User Action</span></span>  
 <span data-ttu-id="d05a5-120">變更 MSMQ 保護層級或 MSMQ 驗證模式屬性，與 MSMQ 保護層級內容一致。</span><span class="sxs-lookup"><span data-stu-id="d05a5-120">Change the MSMQ protection level or the MSMQ authentication mode property to be consistent with the MSMQ protection level property.</span></span>  
  
1.  <span data-ttu-id="d05a5-121">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="d05a5-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="d05a5-122">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="d05a5-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="d05a5-123">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="d05a5-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="d05a5-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="d05a5-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="d05a5-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="d05a5-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="d05a5-126">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="d05a5-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="d05a5-127">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="d05a5-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="d05a5-128">在**Wcf-netmsmq 傳輸屬性**對話方塊中，按一下 [**安全性**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d05a5-128">In the **WCF-NetMsmq Transport Properties** dialog box, click the **Security** tab.</span></span>  
  
9. <span data-ttu-id="d05a5-129">請檢查 MSMQ 中的值**驗證模式**清單和**MSMQ 保護等級**清單。</span><span class="sxs-lookup"><span data-stu-id="d05a5-129">Check the values in the MSMQ **authentication mode** list and the **MSMQ protection level** list.</span></span>  
  
 <span data-ttu-id="d05a5-130">如需詳細資訊，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="d05a5-130">For further information, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="d05a5-131">如何設定 Wcf-netmsmq 傳送埠</span><span class="sxs-lookup"><span data-stu-id="d05a5-131">How to Configure a WCF-NetMsmq Send Port</span></span>](../core/how-to-configure-a-wcf-netmsmq-send-port.md)  
  
-   [<span data-ttu-id="d05a5-132">如何設定 Wcf-netmsmq 接收位置</span><span class="sxs-lookup"><span data-stu-id="d05a5-132">How to Configure a WCF-NetMsmq Receive Location</span></span>](../core/how-to-configure-a-wcf-netmsmq-receive-location.md)