---
title: 使用 Office 365 Outlook 電子郵件配接器 |Microsoft Docs
description: 傳送和接收訊息在 BizTalk Server 中，包括電子郵件、 行事曆和連絡人中使用 Office 365 Outlook 配接器的概觀
ms.custom: ''
ms.date: 06/19/2018
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: MandiOhlinger
ms.author: ribarua
manager: dougeby
ms.openlocfilehash: 2002ab6859a71a930ef9166f9b3a5a072ba77948
ms.sourcegitcommit: e7609c319b64ec20bf215d17aa5ac4f9dcae52ec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36946176"
---
# <a name="office-365-outlook-adapters-in-biztalk"></a><span data-ttu-id="f0d7f-103">在 BizTalk 中的 office 365 Outlook 配接器</span><span class="sxs-lookup"><span data-stu-id="f0d7f-103">Office 365 Outlook adapters in BizTalk</span></span>

## <a name="overview"></a><span data-ttu-id="f0d7f-104">概觀</span><span class="sxs-lookup"><span data-stu-id="f0d7f-104">Overview</span></span>
<span data-ttu-id="f0d7f-105">**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]功能套件 3**，您可以傳送和接收 BizTalk Server 和 Office 365 Outlook 的功能之間的訊息。</span><span class="sxs-lookup"><span data-stu-id="f0d7f-105">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 3**, you can send and receive messages between BizTalk Server and Office 365 Outlook features.</span></span> <span data-ttu-id="f0d7f-106">功能組件 3 包含下列配接器：</span><span class="sxs-lookup"><span data-stu-id="f0d7f-106">The following adapters are included in Feature Pack 3:</span></span>

- [<span data-ttu-id="f0d7f-107">Office 365 Outlook 電子郵件配接器</span><span class="sxs-lookup"><span data-stu-id="f0d7f-107">Office 365 Outlook Email adapter</span></span>](office365-mail-adapter.md)
- [<span data-ttu-id="f0d7f-108">Office 365 的 Outlook 行事曆配接器</span><span class="sxs-lookup"><span data-stu-id="f0d7f-108">Office 365 Outlook Calendar adapter</span></span>](office365-calendar-adapter.md)
- [<span data-ttu-id="f0d7f-109">Office 365 Outlook 連絡人配接器</span><span class="sxs-lookup"><span data-stu-id="f0d7f-109">Office 365 Outlook Contact adapter</span></span>](office365-contact-adapter.md)

## <a name="prerequisites"></a><span data-ttu-id="f0d7f-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="f0d7f-110">Prerequisites</span></span>

* <span data-ttu-id="f0d7f-111">有[Office 365 帳戶](https://outlook.office365.com)</span><span class="sxs-lookup"><span data-stu-id="f0d7f-111">Have an [Office 365 account](https://outlook.office365.com)</span></span>
* <span data-ttu-id="f0d7f-112">安裝[Feature Pack 3](https://aka.ms/bts2016fp3) BizTalk 伺服器上</span><span class="sxs-lookup"><span data-stu-id="f0d7f-112">Install [Feature Pack 3](https://aka.ms/bts2016fp3) on your BizTalk Server</span></span>
* <span data-ttu-id="f0d7f-113">使用的帳戶是 SSO 系統管理員群組的成員，</span><span class="sxs-lookup"><span data-stu-id="f0d7f-113">Use an account that is a member of the SSO Administrators group</span></span>

## <a name="tms-overview"></a><span data-ttu-id="f0d7f-114">TMS 概觀</span><span class="sxs-lookup"><span data-stu-id="f0d7f-114">TMS overview</span></span>

<span data-ttu-id="f0d7f-115">BizTalk Server TMS 是重新整理 BizTalk 使用 Office 365 OAuth 權杖的服務。</span><span class="sxs-lookup"><span data-stu-id="f0d7f-115">BizTalk Server TMS is a service that refreshes the Office 365 OAuth tokens used by BizTalk.</span></span> <span data-ttu-id="f0d7f-116">它會重新整理這些權杖，以定期確保，權杖永遠保持有效。</span><span class="sxs-lookup"><span data-stu-id="f0d7f-116">It refreshes these tokens periodically, ensuring that the tokens always remain valid.</span></span> <span data-ttu-id="f0d7f-117">它會相依於企業單一登入服務 (ENT SSO)，並必須安裝在裝載主要密碼伺服器的電腦上。</span><span class="sxs-lookup"><span data-stu-id="f0d7f-117">It has a dependency on Enterprise Single Sign On service (ENT SSO), and must be installed on a computer that hosts the master secret server.</span></span> 

## <a name="install-biztalk-server-tms"></a><span data-ttu-id="f0d7f-118">安裝 BizTalk Server TMS</span><span class="sxs-lookup"><span data-stu-id="f0d7f-118">Install BizTalk Server TMS</span></span>

1. <span data-ttu-id="f0d7f-119">安裝[Feature Pack 3](https://aka.ms/bts2016fp3)。</span><span class="sxs-lookup"><span data-stu-id="f0d7f-119">Install [Feature Pack 3](https://aka.ms/bts2016fp3).</span></span>
2. <span data-ttu-id="f0d7f-120">在  `\Program Files (x86)\Microsoft BizTalk Server <your version>`，執行 BizTalkTMS.msi。</span><span class="sxs-lookup"><span data-stu-id="f0d7f-120">In `\Program Files (x86)\Microsoft BizTalk Server <your version>`, run BizTalkTMS.msi.</span></span>
3. <span data-ttu-id="f0d7f-121">輸入使用者名稱和密碼之使用者的 SSO 系統管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="f0d7f-121">Enter the username and password of a user that's a member of the SSO Administrators group.</span></span> 

![BizTalk Server TMS 安裝程式](../core/media/BizTalk-TMS.png)

## <a name="sign-in-to-office-365"></a><span data-ttu-id="f0d7f-123">登入 Office 365</span><span class="sxs-lookup"><span data-stu-id="f0d7f-123">Sign-in to Office 365</span></span>

<span data-ttu-id="f0d7f-124">當您要建立[傳送埠](how-to-create-a-send-port2.md)或是[接收位置](how-to-create-a-receive-location.md)在 BizTalk 管理中，您可以**登入...** 至 Office 365 帳戶：</span><span class="sxs-lookup"><span data-stu-id="f0d7f-124">When you're creating a [send port](how-to-create-a-send-port2.md) or [receive location](how-to-create-a-receive-location.md) in BizTalk Administration, you can **Sign-in...** to your Office 365 account:</span></span>

  ![Office 365 登入](../core/media/office365-signin.png)

<span data-ttu-id="f0d7f-126">您輸入 Office 365 的認證，並確認權限。</span><span class="sxs-lookup"><span data-stu-id="f0d7f-126">You enter the Office 365 credentials, and confirm permissions.</span></span> <span data-ttu-id="f0d7f-127">這些認證授權 BizTalk 連接並存取 Office 365 帳戶。</span><span class="sxs-lookup"><span data-stu-id="f0d7f-127">These credentials authorize BizTalk to connect to, and access the Office 365 account.</span></span> <span data-ttu-id="f0d7f-128">在下列範例中，您會看到 Office 365 Outlook 行事曆的權限：</span><span class="sxs-lookup"><span data-stu-id="f0d7f-128">In the following example, you see the permissions for Office 365 Outlook Calendar:</span></span>

  ![Office 365 行事曆權限](../core/media/office365-calendar-permissions.png)

## <a name="get-started"></a><span data-ttu-id="f0d7f-130">開始使用</span><span class="sxs-lookup"><span data-stu-id="f0d7f-130">Get started</span></span>
<span data-ttu-id="f0d7f-131">安裝 BizTalk Server TMS 之後，您即可建立成品，並開始使用配接器：</span><span class="sxs-lookup"><span data-stu-id="f0d7f-131">After BizTalk Server TMS is installed, you're ready to create the artifacts, and start using the adapters:</span></span>

- [<span data-ttu-id="f0d7f-132">Office 365 Outlook 電子郵件配接器</span><span class="sxs-lookup"><span data-stu-id="f0d7f-132">Office 365 Outlook Email adapter</span></span>](./office365-mail-adapter.md)
- [<span data-ttu-id="f0d7f-133">Office 365 的 Outlook 行事曆配接器</span><span class="sxs-lookup"><span data-stu-id="f0d7f-133">Office 365 Outlook Calendar adapter</span></span>](./office365-calendar-adapter.md)
- [<span data-ttu-id="f0d7f-134">Office 365 Outlook 連絡人配接器</span><span class="sxs-lookup"><span data-stu-id="f0d7f-134">Office 365 Outlook Contact adapter</span></span>](./office365-contact-adapter.md)
