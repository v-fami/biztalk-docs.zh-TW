---
title: 需要未指定服務憑證指紋 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ca853667-83b5-41f2-9b54-8117b87e27d3
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6dc43d9ed50aaacd108b275063cf00d18aea743
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268558"
---
# <a name="required-service-certificate-thumbprint-not-specified"></a><span data-ttu-id="38e9f-102">未指定必要的服務憑證指紋</span><span class="sxs-lookup"><span data-stu-id="38e9f-102">Required service certificate thumbprint not specified</span></span>
## <a name="details"></a><span data-ttu-id="38e9f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="38e9f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="38e9f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="38e9f-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="38e9f-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="38e9f-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="38e9f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="38e9f-106">Event ID</span></span>|<span data-ttu-id="38e9f-107">0</span><span class="sxs-lookup"><span data-stu-id="38e9f-107">0</span></span>|  
|<span data-ttu-id="38e9f-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="38e9f-108">Event Source</span></span>|<span data-ttu-id="38e9f-109">0</span><span class="sxs-lookup"><span data-stu-id="38e9f-109">0</span></span>|  
|<span data-ttu-id="38e9f-110">元件</span><span class="sxs-lookup"><span data-stu-id="38e9f-110">Component</span></span>|<span data-ttu-id="38e9f-111">0</span><span class="sxs-lookup"><span data-stu-id="38e9f-111">0</span></span>|  
|<span data-ttu-id="38e9f-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="38e9f-112">Symbolic Name</span></span>|<span data-ttu-id="38e9f-113">0</span><span class="sxs-lookup"><span data-stu-id="38e9f-113">0</span></span>|  
|<span data-ttu-id="38e9f-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="38e9f-114">Message Text</span></span>|<span data-ttu-id="38e9f-115">未指定必要的服務憑證指紋</span><span class="sxs-lookup"><span data-stu-id="38e9f-115">Required service certificate thumbprint not specified</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="38e9f-116">說明</span><span class="sxs-lookup"><span data-stu-id="38e9f-116">Explanation</span></span>  
 <span data-ttu-id="38e9f-117">未設定服務的 WCF 傳送埠的安全性設定所需的憑證屬性。</span><span class="sxs-lookup"><span data-stu-id="38e9f-117">You did not set the Service certificate property required for the security settings of a WCF send port.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="38e9f-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="38e9f-118">User Action</span></span>  
 <span data-ttu-id="38e9f-119">您可以使用下列程序來設定服務憑證屬性。</span><span class="sxs-lookup"><span data-stu-id="38e9f-119">Use the following procedure to configure the Service certificate property.</span></span>  
  
#### <a name="to-configure-the-service-certificate-property"></a><span data-ttu-id="38e9f-120">若要設定服務憑證屬性</span><span class="sxs-lookup"><span data-stu-id="38e9f-120">To configure the Service certificate property</span></span>  
  
1.  <span data-ttu-id="38e9f-121">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="38e9f-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="38e9f-122">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="38e9f-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="38e9f-123">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="38e9f-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="38e9f-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="38e9f-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="38e9f-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="38e9f-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="38e9f-126">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="38e9f-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="38e9f-127">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="38e9f-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="38e9f-128">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**安全性**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="38e9f-128">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Security** tab.</span></span>  
  
9. <span data-ttu-id="38e9f-129">請確認**服務憑證**屬性設定。</span><span class="sxs-lookup"><span data-stu-id="38e9f-129">Ensure that the **Service certificate** property is configured.</span></span>  
  
 <span data-ttu-id="38e9f-130">如需有關憑證的詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="38e9f-130">For additional information on certificates, see the following resource:</span></span>  
  
-   [<span data-ttu-id="38e9f-131">WCF 配接器安裝憑證</span><span class="sxs-lookup"><span data-stu-id="38e9f-131">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)