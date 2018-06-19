---
title: 如何移除憑證，以從接收位置 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates, receive locations
- receive locations, certificates
- managing [receive locations], certificates
ms.assetid: 717d41bf-4260-4df4-9d0a-07243bb9b12c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e70cd846c364d52544bf8504d42132dd35fe65d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254534"
---
# <a name="how-to-remove-a-certificate-from-a-receive-location"></a><span data-ttu-id="08277-102">如何從接收位置移除憑證</span><span class="sxs-lookup"><span data-stu-id="08277-102">How to Remove a Certificate from a Receive Location</span></span>
<span data-ttu-id="08277-103">本主題說明如何使用 BizTalk Server管理主控台，從接收位置移除安全性憑證。</span><span class="sxs-lookup"><span data-stu-id="08277-103">This topic describes how to use the BizTalk Server Administration console to remove a security certificate from a receive location.</span></span> <span data-ttu-id="08277-104">這樣做之後，接收位置就不再將訊息加密；訊息將會以純文字傳送。</span><span class="sxs-lookup"><span data-stu-id="08277-104">When you do this, the receive location will no longer encrypt messages; messages will be sent in clear text.</span></span> <span data-ttu-id="08277-105">從接收位置移除憑證並不會將它從憑證存放區中移除。</span><span class="sxs-lookup"><span data-stu-id="08277-105">Removing a certificate from a receive location does not remove it from the certificate store.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="08277-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="08277-106">Prerequisites</span></span>  
 <span data-ttu-id="08277-107">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="08277-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="08277-108">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="08277-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-remove-a-certificate-from-a-receive-location"></a><span data-ttu-id="08277-109">若要從接收位置移除憑證</span><span class="sxs-lookup"><span data-stu-id="08277-109">To remove a certificate from a receive location</span></span>  
  
1.  <span data-ttu-id="08277-110">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="08277-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="08277-111">在主控台樹狀結構中，展開您要為其從接收位置移除憑證的 BizTalk 群組與 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="08277-111">In the console tree, expand the BizTalk group and the BizTalk application for which you want to remove a certificate from a receive location.</span></span>  
  
3.  <span data-ttu-id="08277-112">展開**接收位置**，以滑鼠右鍵按一下接收位置，按一下**屬性**，然後按一下 **憑證**。</span><span class="sxs-lookup"><span data-stu-id="08277-112">Expand **Receive Locations**, right-click the receive location, click **Properties**, and then click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="08277-113">按一下**移除憑證**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="08277-113">Click **Remove certificate**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08277-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08277-114">See Also</span></span>  
 [<span data-ttu-id="08277-115">管理接收位置</span><span class="sxs-lookup"><span data-stu-id="08277-115">Managing Receive Locations</span></span>](../core/managing-receive-locations.md)