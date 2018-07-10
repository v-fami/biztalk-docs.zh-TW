---
title: 無法從憑證參考建立 X509CertificateIdentity |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a3acee8e-c035-4e58-8bfc-397885b4d185
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b991f9acb2b5cc193d24d36e1a5de8650e7af72b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988927"
---
# <a name="failed-to-create-x509certificateidentity-from-certificate-reference"></a><span data-ttu-id="bed7e-102">無法從憑證參考建立 X509CertificateIdentity</span><span class="sxs-lookup"><span data-stu-id="bed7e-102">Failed to create X509CertificateIdentity from certificate reference</span></span>
## <a name="details"></a><span data-ttu-id="bed7e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bed7e-103">Details</span></span>  

|                 |                                                                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="bed7e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bed7e-104">Product Name</span></span>   |                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                             |
| <span data-ttu-id="bed7e-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="bed7e-105">Product Version</span></span> |                                         [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                         |
|    <span data-ttu-id="bed7e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bed7e-106">Event ID</span></span>     |                                                                     <span data-ttu-id="bed7e-107">0</span><span class="sxs-lookup"><span data-stu-id="bed7e-107">0</span></span>                                                                      |
|  <span data-ttu-id="bed7e-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="bed7e-108">Event Source</span></span>   |                                                                     <span data-ttu-id="bed7e-109">0</span><span class="sxs-lookup"><span data-stu-id="bed7e-109">0</span></span>                                                                      |
|    <span data-ttu-id="bed7e-110">元件</span><span class="sxs-lookup"><span data-stu-id="bed7e-110">Component</span></span>    |                                                                     <span data-ttu-id="bed7e-111">0</span><span class="sxs-lookup"><span data-stu-id="bed7e-111">0</span></span>                                                                      |
|  <span data-ttu-id="bed7e-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bed7e-112">Symbolic Name</span></span>  |                                                                     <span data-ttu-id="bed7e-113">0</span><span class="sxs-lookup"><span data-stu-id="bed7e-113">0</span></span>                                                                      |
|  <span data-ttu-id="bed7e-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bed7e-114">Message Text</span></span>   | <span data-ttu-id="bed7e-115">無法從憑證參考建立 X509CertificateIdentity。</span><span class="sxs-lookup"><span data-stu-id="bed7e-115">Failed to create X509CertificateIdentity from certificate reference.</span></span> <span data-ttu-id="bed7e-116">(StoreName={0}, StoreLocation={1}, X509FindType={2}, FindValue="{3}")</span><span class="sxs-lookup"><span data-stu-id="bed7e-116">(StoreName={0}, StoreLocation={1}, X509FindType={2}, FindValue="{3}")</span></span> |

## <a name="explanation"></a><span data-ttu-id="bed7e-117">說明</span><span class="sxs-lookup"><span data-stu-id="bed7e-117">Explanation</span></span>  
 <span data-ttu-id="bed7e-118">此錯誤表示配接器無法建立 X509Certificate 結束點識別組態中指定。</span><span class="sxs-lookup"><span data-stu-id="bed7e-118">This error indicates the adapter failed to create the X509Certificate specified in the endpoint identity configuration.</span></span>  

## <a name="user-action"></a><span data-ttu-id="bed7e-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bed7e-119">User Action</span></span>  
 <span data-ttu-id="bed7e-120">您可以使用下列程序來驗證憑證參考設定。</span><span class="sxs-lookup"><span data-stu-id="bed7e-120">Use the following procedure to verify the certificate reference settings.</span></span>  

#### <a name="to-configure-the-certificate-reference-settings"></a><span data-ttu-id="bed7e-121">若要設定的憑證參考設定</span><span class="sxs-lookup"><span data-stu-id="bed7e-121">To configure the certificate reference settings</span></span>  

1. <span data-ttu-id="bed7e-122">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="bed7e-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="bed7e-123">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="bed7e-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  

3. <span data-ttu-id="bed7e-124">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="bed7e-124">Locate your application and then locate your transport.</span></span>  

4. <span data-ttu-id="bed7e-125">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="bed7e-125">Right-click the transport name.</span></span>  

5. <span data-ttu-id="bed7e-126">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="bed7e-126">Click **Properties**.</span></span>  

6. <span data-ttu-id="bed7e-127">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="bed7e-127">In the port **Type** list, select the correct port.</span></span>  

7. <span data-ttu-id="bed7e-128">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="bed7e-128">Click **Configure**.</span></span>  

8. <span data-ttu-id="bed7e-129">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bed7e-129">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **General** tab.</span></span>  

9. <span data-ttu-id="bed7e-130">在 **端點身分識別**區段中，按一下**編輯。**</span><span class="sxs-lookup"><span data-stu-id="bed7e-130">In the **Endpoint Identity** section, click **Edit.**</span></span>  

10. <span data-ttu-id="bed7e-131">在 **識別編輯器**對話方塊方塊中，請確認**憑證參考**設定是否有效。</span><span class="sxs-lookup"><span data-stu-id="bed7e-131">In the **Identity Editor** dialog box, ensure that the **Certificate Reference** settings are valid.</span></span>
