---
title: "無法從憑證參考建立 x509certificateidentity。 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3acee8e-c035-4e58-8bfc-397885b4d185
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c6bb03698010d667b27334f17fa7270de845c68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="failed-to-create-x509certificateidentity-from-certificate-reference"></a><span data-ttu-id="ddb22-102">無法從憑證參考建立 x509certificateidentity。</span><span class="sxs-lookup"><span data-stu-id="ddb22-102">Failed to create X509CertificateIdentity from certificate reference</span></span>
## <a name="details"></a><span data-ttu-id="ddb22-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ddb22-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ddb22-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ddb22-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ddb22-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="ddb22-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="ddb22-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ddb22-106">Event ID</span></span>|<span data-ttu-id="ddb22-107">0</span><span class="sxs-lookup"><span data-stu-id="ddb22-107">0</span></span>|  
|<span data-ttu-id="ddb22-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="ddb22-108">Event Source</span></span>|<span data-ttu-id="ddb22-109">0</span><span class="sxs-lookup"><span data-stu-id="ddb22-109">0</span></span>|  
|<span data-ttu-id="ddb22-110">元件</span><span class="sxs-lookup"><span data-stu-id="ddb22-110">Component</span></span>|<span data-ttu-id="ddb22-111">0</span><span class="sxs-lookup"><span data-stu-id="ddb22-111">0</span></span>|  
|<span data-ttu-id="ddb22-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ddb22-112">Symbolic Name</span></span>|<span data-ttu-id="ddb22-113">0</span><span class="sxs-lookup"><span data-stu-id="ddb22-113">0</span></span>|  
|<span data-ttu-id="ddb22-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ddb22-114">Message Text</span></span>|<span data-ttu-id="ddb22-115">無法建立 x509certificateidentity。 從 憑證參考。</span><span class="sxs-lookup"><span data-stu-id="ddb22-115">Failed to create X509CertificateIdentity from certificate reference.</span></span> <span data-ttu-id="ddb22-116">(StoreName = {0}、 StoreLocation = \ {1 \} X509FindType = \ {2 \} FindValue ="\ {3\}")</span><span class="sxs-lookup"><span data-stu-id="ddb22-116">(StoreName={0}, StoreLocation={1}, X509FindType={2}, FindValue="{3}")</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ddb22-117">說明</span><span class="sxs-lookup"><span data-stu-id="ddb22-117">Explanation</span></span>  
 <span data-ttu-id="ddb22-118">此錯誤表示配接器無法建立端點身分識別組態中指定的 X509Certificate。</span><span class="sxs-lookup"><span data-stu-id="ddb22-118">This error indicates the adapter failed to create the X509Certificate specified in the endpoint identity configuration.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ddb22-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ddb22-119">User Action</span></span>  
 <span data-ttu-id="ddb22-120">您可以使用下列程序來驗證憑證參考設定。</span><span class="sxs-lookup"><span data-stu-id="ddb22-120">Use the following procedure to verify the certificate reference settings.</span></span>  
  
#### <a name="to-configure-the-certificate-reference-settings"></a><span data-ttu-id="ddb22-121">若要設定的憑證參考設定</span><span class="sxs-lookup"><span data-stu-id="ddb22-121">To configure the certificate reference settings</span></span>  
  
1.  <span data-ttu-id="ddb22-122">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="ddb22-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="ddb22-123">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="ddb22-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="ddb22-124">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="ddb22-124">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="ddb22-125">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="ddb22-125">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="ddb22-126">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="ddb22-126">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="ddb22-127">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="ddb22-127">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="ddb22-128">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="ddb22-128">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="ddb22-129">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ddb22-129">In the **WCF [***transport type***] Transport Properties** dialog box, click the **General** tab.</span></span>  
  
9. <span data-ttu-id="ddb22-130">在**端點身分識別**區段中，按一下**編輯。**</span><span class="sxs-lookup"><span data-stu-id="ddb22-130">In the **Endpoint Identity** section, click **Edit.**</span></span>  
  
10. <span data-ttu-id="ddb22-131">在**識別編輯器**對話方塊方塊中，確定**憑證參考**設定是否有效。</span><span class="sxs-lookup"><span data-stu-id="ddb22-131">In the **Identity Editor** dialog box, ensure that the **Certificate Reference** settings are valid.</span></span>