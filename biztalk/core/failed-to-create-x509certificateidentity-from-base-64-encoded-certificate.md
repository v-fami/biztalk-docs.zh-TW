---
title: 無法從 base-64 編碼憑證建立 X509CertificateIdentity |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13112bd-e0e8-4b49-ad2f-ea82b2e8162f
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00d92c9ca3f7de567de915241d5950f5b93c06da
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995239"
---
# <a name="failed-to-create-x509certificateidentity-from-base-64-encoded-certificate"></a><span data-ttu-id="f0934-102">無法從 Base-64 編碼憑證建立 X509CertificateIdentity。</span><span class="sxs-lookup"><span data-stu-id="f0934-102">Failed to create X509CertificateIdentity from base-64 encoded certificate</span></span>
## <a name="details"></a><span data-ttu-id="f0934-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f0934-103">Details</span></span>  

|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="f0934-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f0934-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="f0934-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f0934-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="f0934-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f0934-106">Event ID</span></span>     |                                         <span data-ttu-id="f0934-107">0</span><span class="sxs-lookup"><span data-stu-id="f0934-107">0</span></span>                                          |
|  <span data-ttu-id="f0934-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="f0934-108">Event Source</span></span>   |                                         <span data-ttu-id="f0934-109">0</span><span class="sxs-lookup"><span data-stu-id="f0934-109">0</span></span>                                          |
|    <span data-ttu-id="f0934-110">元件</span><span class="sxs-lookup"><span data-stu-id="f0934-110">Component</span></span>    |                                         <span data-ttu-id="f0934-111">0</span><span class="sxs-lookup"><span data-stu-id="f0934-111">0</span></span>                                          |
|  <span data-ttu-id="f0934-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f0934-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="f0934-113">0</span><span class="sxs-lookup"><span data-stu-id="f0934-113">0</span></span>                                          |
|  <span data-ttu-id="f0934-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f0934-114">Message Text</span></span>   |     <span data-ttu-id="f0934-115">無法從 Base-64 編碼憑證建立 X509CertificateIdentity。</span><span class="sxs-lookup"><span data-stu-id="f0934-115">Failed to create X509CertificateIdentity from base-64 encoded certificate</span></span>      |

## <a name="explanation"></a><span data-ttu-id="f0934-116">說明</span><span class="sxs-lookup"><span data-stu-id="f0934-116">Explanation</span></span>  
 <span data-ttu-id="f0934-117">此錯誤表示配接器因為無效的憑證設定，而無法建立 X509Certificate 結束點識別。</span><span class="sxs-lookup"><span data-stu-id="f0934-117">This error indicates the adapter failed to create the X509Certificate endpoint identity because of an invalid certificate setting.</span></span>  

## <a name="user-action"></a><span data-ttu-id="f0934-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f0934-118">User Action</span></span>  
 <span data-ttu-id="f0934-119">使用下列程序來設定憑證。</span><span class="sxs-lookup"><span data-stu-id="f0934-119">Use the following procedure to configure certificates.</span></span>  

#### <a name="to-configure-certificates"></a><span data-ttu-id="f0934-120">若要設定憑證</span><span class="sxs-lookup"><span data-stu-id="f0934-120">To configure certificates</span></span>  

1. <span data-ttu-id="f0934-121">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="f0934-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="f0934-122">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="f0934-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  

3. <span data-ttu-id="f0934-123">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="f0934-123">Locate your application and then locate your transport.</span></span>  

4. <span data-ttu-id="f0934-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="f0934-124">Right-click the transport name.</span></span>  

5. <span data-ttu-id="f0934-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="f0934-125">Click **Properties**.</span></span>  

6. <span data-ttu-id="f0934-126">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="f0934-126">In the port **Type** list, select the correct port.</span></span>  

7. <span data-ttu-id="f0934-127">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="f0934-127">Click **Configure**.</span></span>  

8. <span data-ttu-id="f0934-128">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**安全性**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f0934-128">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Security** tab.</span></span>  

9. <span data-ttu-id="f0934-129">確保設定正確**用戶端憑證指紋**並**的服務憑證指紋**。</span><span class="sxs-lookup"><span data-stu-id="f0934-129">Ensure that the settings are correct for the **Client Certificate Thumbprint** and the **Service Certificate Thumbprint**.</span></span>
