---
title: 需要未指定的用戶端憑證指紋 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19307bdb-29d7-4a79-9472-dda24dd8b263
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17eb34655ab0acd379e493540f8cd0922e5d8be9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269366"
---
# <a name="required-client-certificate-thumbprint-not-specified"></a><span data-ttu-id="0aff8-102">未指定必要的用戶端憑證指紋</span><span class="sxs-lookup"><span data-stu-id="0aff8-102">Required client certificate thumbprint not specified</span></span>
## <a name="details"></a><span data-ttu-id="0aff8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0aff8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0aff8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0aff8-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0aff8-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="0aff8-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="0aff8-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0aff8-106">Event ID</span></span>|<span data-ttu-id="0aff8-107">0</span><span class="sxs-lookup"><span data-stu-id="0aff8-107">0</span></span>|  
|<span data-ttu-id="0aff8-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="0aff8-108">Event Source</span></span>|<span data-ttu-id="0aff8-109">0</span><span class="sxs-lookup"><span data-stu-id="0aff8-109">0</span></span>|  
|<span data-ttu-id="0aff8-110">元件</span><span class="sxs-lookup"><span data-stu-id="0aff8-110">Component</span></span>|<span data-ttu-id="0aff8-111">0</span><span class="sxs-lookup"><span data-stu-id="0aff8-111">0</span></span>|  
|<span data-ttu-id="0aff8-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0aff8-112">Symbolic Name</span></span>|<span data-ttu-id="0aff8-113">0</span><span class="sxs-lookup"><span data-stu-id="0aff8-113">0</span></span>|  
|<span data-ttu-id="0aff8-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0aff8-114">Message Text</span></span>|<span data-ttu-id="0aff8-115">未指定必要的用戶端憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="0aff8-115">Required client certificate thumbprint not specified.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0aff8-116">說明</span><span class="sxs-lookup"><span data-stu-id="0aff8-116">Explanation</span></span>  
 <span data-ttu-id="0aff8-117">未設定用戶端憑證所需的 WCF 傳送埠的安全性設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="0aff8-117">You did not set the Client certificate property required for the security settings of a WCF send port.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0aff8-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0aff8-118">User Action</span></span>  
 <span data-ttu-id="0aff8-119">使用下列程序來設定 WCF 的安全性設定傳送埠。</span><span class="sxs-lookup"><span data-stu-id="0aff8-119">Use the following procedure to configure security settings of a WCF send port.</span></span>  
  
#### <a name="to-configure-security-settings"></a><span data-ttu-id="0aff8-120">若要設定安全性設定</span><span class="sxs-lookup"><span data-stu-id="0aff8-120">To configure security settings</span></span>  
  
1.  <span data-ttu-id="0aff8-121">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="0aff8-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="0aff8-122">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="0aff8-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="0aff8-123">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="0aff8-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="0aff8-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="0aff8-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="0aff8-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="0aff8-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="0aff8-126">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="0aff8-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="0aff8-127">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="0aff8-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="0aff8-128">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**安全性**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0aff8-128">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Security** tab.</span></span>  
  
9. <span data-ttu-id="0aff8-129">請確認**用戶端憑證**屬性設定。</span><span class="sxs-lookup"><span data-stu-id="0aff8-129">Ensure that the **Client certificate** property is configured.</span></span>  
  
 <span data-ttu-id="0aff8-130">如需有關憑證的詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="0aff8-130">For additional information on certificates, see the following resource:</span></span>  
  
-   [<span data-ttu-id="0aff8-131">WCF 配接器安裝憑證</span><span class="sxs-lookup"><span data-stu-id="0aff8-131">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)