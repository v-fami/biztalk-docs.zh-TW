---
title: 如何設定驗證選項的接收埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [receive ports], configuring
- authenticating, configuring
- managing [receive ports], authenticating
- receive ports, configuring
- configuring, authenticating
- configuring, receive ports
- authenticating, receive ports
ms.assetid: ce213ef0-ae91-47cf-84bf-0f86cc684bce
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 012ec38ef3d9acf53c7293c668b17cd85c6c738d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248806"
---
# <a name="how-to-configure-authentication-options-for-a-receive-port"></a><span data-ttu-id="4466b-102">如何設定接收埠的驗證選項</span><span class="sxs-lookup"><span data-stu-id="4466b-102">How to Configure Authentication Options for a Receive Port</span></span>
<span data-ttu-id="4466b-103">本主題描述如何使用 BizTalk Server 管理主控台來設定接收埠的訊息驗證選項。</span><span class="sxs-lookup"><span data-stu-id="4466b-103">This topic describes how to use the BizTalk Server Administration console to configure message authentication options for a receive port.</span></span> <span data-ttu-id="4466b-104">這些選項會在設定合作對象解析驗證後生效。</span><span class="sxs-lookup"><span data-stu-id="4466b-104">These options take effect when party resolution authentication is configured.</span></span> <span data-ttu-id="4466b-105">選項包括：</span><span class="sxs-lookup"><span data-stu-id="4466b-105">The options are:</span></span>  
  
-   <span data-ttu-id="4466b-106">**沒有驗證。**</span><span class="sxs-lookup"><span data-stu-id="4466b-106">**No authentication.**</span></span> <span data-ttu-id="4466b-107">如果選取此選項，接收埠將會讓訊息通過，而不檢查訊息認證。</span><span class="sxs-lookup"><span data-stu-id="4466b-107">If this option is selected, the receive port will pass the message through without checking for message credentials.</span></span>  
  
-   <span data-ttu-id="4466b-108">**如果驗證失敗時，捨棄訊息。**</span><span class="sxs-lookup"><span data-stu-id="4466b-108">**Drop messages if authentication fails.**</span></span> <span data-ttu-id="4466b-109">如果選取此選項，接收埠將會使用「合作對象」解析來檢查訊息認證，並且在驗證失敗時捨棄該訊息。</span><span class="sxs-lookup"><span data-stu-id="4466b-109">If this option is selected, the receive port will check message credentials using Party resolution and discard the message if authentication fails.</span></span>  
  
-   <span data-ttu-id="4466b-110">**驗證失敗時保留訊息。**</span><span class="sxs-lookup"><span data-stu-id="4466b-110">**Keep messages if authentication fails.**</span></span> <span data-ttu-id="4466b-111">如果選取此選項，接收埠將會使用「合作對象」解析來檢查訊息認證，並且在驗證失敗時，將該訊息保留在擱置的佇列中。</span><span class="sxs-lookup"><span data-stu-id="4466b-111">If this option is selected, the receive port will check message credentials using Party resolution and keep the message in the suspended queue if authentication fails.</span></span>  
  
 <span data-ttu-id="4466b-112">如需建立和設定合作對象的指示，請參閱[如何建立合作對象](http://msdn.microsoft.com/library/f6feca1d-bc83-4fb6-981d-26c9e0d53044)。</span><span class="sxs-lookup"><span data-stu-id="4466b-112">For instructions on creating and configuring a party, see [How to Create a Party](http://msdn.microsoft.com/library/f6feca1d-bc83-4fb6-981d-26c9e0d53044).</span></span> <span data-ttu-id="4466b-113">如需合作對象解析驗證的詳細資訊，請參閱[驗證訊息的傳送者](../core/authenticating-the-sender-of-a-message.md)和[輸入訊息驗證](../core/inbound-message-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="4466b-113">For more information about party resolution authentication, see [Authenticating the Sender of a Message](../core/authenticating-the-sender-of-a-message.md) and [Inbound Message Authentication](../core/inbound-message-authentication.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4466b-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="4466b-114">Prerequisites</span></span>  
 <span data-ttu-id="4466b-115">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="4466b-115">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="4466b-116">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="4466b-116">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-authentication-options-for-a-receive-port"></a><span data-ttu-id="4466b-117">設定接收埠的驗證選項</span><span class="sxs-lookup"><span data-stu-id="4466b-117">To configure authentication options for a receive port</span></span>  
  
1.  <span data-ttu-id="4466b-118">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="4466b-118">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="4466b-119">在主控台樹狀結構中，展開您要為其設定接收埠驗證的 BizTalk 群組和 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4466b-119">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure authentication for a receive port.</span></span>  
  
3.  <span data-ttu-id="4466b-120">按一下**接收埠**，接收埠，以滑鼠右鍵按一下，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="4466b-120">Click **Receive Ports**, right-click the receive port, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="4466b-121">在**驗證**區段中，選取的選項，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4466b-121">In the **Authentication** section, select the option you want, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4466b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4466b-122">See Also</span></span>  
 [<span data-ttu-id="4466b-123">管理接收埠</span><span class="sxs-lookup"><span data-stu-id="4466b-123">Managing Receive Ports</span></span>](../core/managing-receive-ports.md)