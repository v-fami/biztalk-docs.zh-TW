---
title: MQSeries 配接器安全性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, MQSeries adapters
- MQSeries adapters, security
ms.assetid: 0bd82c21-6b77-4a66-a4e9-4a91ba4a56c4
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08d5228dab8463c2ad5dc7f9d9347899d4c41a67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263198"
---
# <a name="security-with-the-mqseries-adapter"></a><span data-ttu-id="e1d74-102">使用 MQSeries 配接器安全性</span><span class="sxs-lookup"><span data-stu-id="e1d74-102">Security with the MQSeries adapter</span></span>

<span data-ttu-id="e1d74-103">MQSeries 配接器安全性是從保護 BizTalk 與 MQSeries 伺服器的安全開始。</span><span class="sxs-lookup"><span data-stu-id="e1d74-103">MQSeries adapter security begins with securing your BizTalk and MQSeries servers.</span></span> <span data-ttu-id="e1d74-104">如需保護 BizTalk Server 的資訊，請參閱[安全和保護資料](secure-and-protect-your-biztalk-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="e1d74-104">For information about securing BizTalk Server, see [Secure and protect your data](secure-and-protect-your-biztalk-messages.md).</span></span> <span data-ttu-id="e1d74-105">如需 MQSeries Server 安全性的詳細資訊，請參閱 IBM MQSeries Server 文件。</span><span class="sxs-lookup"><span data-stu-id="e1d74-105">For information about MQSeries Server security, see the IBM MQSeries Server documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1d74-106">配接器會自動為 BizTalk Server 與 MQSeries Server 之間傳送和接收的訊息使用封包私密性。</span><span class="sxs-lookup"><span data-stu-id="e1d74-106">The adapter automatically uses packet privacy for sending and receiving messages between BizTalk Server and MQSeries Server.</span></span>  

## <a name="adapter-security"></a><span data-ttu-id="e1d74-107">配接器安全性</span><span class="sxs-lookup"><span data-stu-id="e1d74-107">Adapter security</span></span>  
 <span data-ttu-id="e1d74-108">安全地使用配接器本身需要注意四個部分：</span><span class="sxs-lookup"><span data-stu-id="e1d74-108">Using the adapter itself securely requires attention to four areas:</span></span>  
  
-   <span data-ttu-id="e1d74-109">選擇 MQSAgent 的應用程式識別與成員</span><span class="sxs-lookup"><span data-stu-id="e1d74-109">Choosing the application identity and members for MQSAgent</span></span>  
  
-   <span data-ttu-id="e1d74-110">使用配接器控制 BizTalk Server 帳戶</span><span class="sxs-lookup"><span data-stu-id="e1d74-110">Controlling the BizTalk Server accounts using the adapter</span></span>  
  
-   <span data-ttu-id="e1d74-111">保護佇列建立指令碼的安全</span><span class="sxs-lookup"><span data-stu-id="e1d74-111">Securing the queue creation scripts</span></span>  
  
-   <span data-ttu-id="e1d74-112">適當地使用**SSO 分支機構應用程式**屬性</span><span class="sxs-lookup"><span data-stu-id="e1d74-112">Making appropriate use of the **SSO Affiliate Application** property</span></span>  
  
 <span data-ttu-id="e1d74-113">在組態期間指派給應用程式識別的帳戶不能是系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="e1d74-113">The account assigned to the application identity during configuration should not be an administrator account.</span></span> <span data-ttu-id="e1d74-114">此帳戶應該具備基本的必要權限—MQSeries 佇列的讀取和寫入權限。</span><span class="sxs-lookup"><span data-stu-id="e1d74-114">Rather, the account should have the minimum required privileges—read and write access to the MQSeries queues.</span></span>  
  
 <span data-ttu-id="e1d74-115">請確定您只指派使用該配接器的 BizTalk Server 帳戶給 MQSAgent 角色。</span><span class="sxs-lookup"><span data-stu-id="e1d74-115">Make sure that you assign only BizTalk Server accounts using the adapter to the MQSAgent role.</span></span>  
  
 <span data-ttu-id="e1d74-116">當使用在佇列定義程序期間建立的匯出指令碼時，將指令碼保存在安全的區域。</span><span class="sxs-lookup"><span data-stu-id="e1d74-116">When using exported scripts created during the queue definition process, keep the scripts in a secure area.</span></span> <span data-ttu-id="e1d74-117">只有使用指令碼的系統管理員才能擁有存取權。</span><span class="sxs-lookup"><span data-stu-id="e1d74-117">Only administrators using the scripts should have access.</span></span>  
  
 <span data-ttu-id="e1d74-118">如果您的應用程式使用 MQCIH 與 MQIIH 標頭屬性將使用者認證放在輸出訊息，請**SSO 分支機構應用程式**屬性**傳輸屬性**頁面。</span><span class="sxs-lookup"><span data-stu-id="e1d74-118">If your application uses MQCIH and MQIIH header properties to put user credentials in outbound messages, use the **SSO Affiliate Application** property on the **Transport Properties** page.</span></span> <span data-ttu-id="e1d74-119">如需有關這個屬性的詳細資訊，請參閱[如何設定 MQSeries 配接器接收位置和傳送埠](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="e1d74-119">For more information about this property, see [How to Configure MQSeries Adapter Receive Locations and Send Ports](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d74-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1d74-120">See Also</span></span>  
 <span data-ttu-id="e1d74-121">[MQSeries 配接器的結構](../core/structure-of-the-mqseries-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="e1d74-121">[Structure of the MQSeries Adapter](../core/structure-of-the-mqseries-adapter.md) </span></span>  
 [<span data-ttu-id="e1d74-122">何謂 MQSeries 配接器？</span><span class="sxs-lookup"><span data-stu-id="e1d74-122">What Is the MQSeries Adapter?</span></span>](../core/what-is-the-mqseries-adapter.md)