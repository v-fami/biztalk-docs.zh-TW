---
title: "如何從傳送埠移除憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, certificates
- managing [send ports], certificates
- certificates, deleting
- deleting, certificates
ms.assetid: fd93a83f-c2aa-4de2-9996-4ca4ec6d4a4c
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5193b1b6003660aac0e0b427da0f0a338b56d8ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-certificate-from-a-send-port"></a><span data-ttu-id="737cd-102">如何從傳送埠移除憑證</span><span class="sxs-lookup"><span data-stu-id="737cd-102">How to Remove a Certificate from a Send Port</span></span>
<span data-ttu-id="737cd-103">本主題描述如何使用 BizTalk Server 管理主控台，從傳送埠移除安全性憑證。</span><span class="sxs-lookup"><span data-stu-id="737cd-103">This topic describes how to use the BizTalk Server Administration console to remove a security certificate from a send port.</span></span> <span data-ttu-id="737cd-104">這樣做之後，傳送埠就再也不會將訊息加密；訊息將會以純文字傳送。</span><span class="sxs-lookup"><span data-stu-id="737cd-104">When you do this, the send port will no longer encrypt messages; messages will be sent in clear text.</span></span> <span data-ttu-id="737cd-105">從傳送埠移除憑證並不會將它從憑證存放區中移除。</span><span class="sxs-lookup"><span data-stu-id="737cd-105">Removing a certificate from a send port does not remove it from the certificate store.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="737cd-106">應用程式開發人員可以使用此主題中的程序，在開發程序中從傳送埠移除安全性憑證。</span><span class="sxs-lookup"><span data-stu-id="737cd-106">The application developer can remove a security certificate from a send port during the development process by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="737cd-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="737cd-107">Prerequisites</span></span>  
 <span data-ttu-id="737cd-108">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="737cd-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="737cd-109">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="737cd-109">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-remove-a-certificate-from-a-send-port"></a><span data-ttu-id="737cd-110">從傳送埠移除憑證</span><span class="sxs-lookup"><span data-stu-id="737cd-110">To remove a certificate from a send port</span></span>  
  
1.  <span data-ttu-id="737cd-111">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="737cd-111">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="737cd-112">在主控台樹狀結構中，展開您要為其從傳送埠移除憑證的 BizTalk 群組與 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="737cd-112">In the console tree, expand the BizTalk group and the BizTalk application for which you want to remove a certificate from a send port.</span></span>  
  
3.  <span data-ttu-id="737cd-113">展開**傳送埠**，以滑鼠右鍵按一下傳送埠，按一下**屬性**，然後按一下 **憑證**。</span><span class="sxs-lookup"><span data-stu-id="737cd-113">Expand **Send Ports**, right-click the send port, click **Properties**, and then click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="737cd-114">按一下**移除憑證**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="737cd-114">Click **Remove certificate**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="737cd-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="737cd-115">See Also</span></span>  
 [<span data-ttu-id="737cd-116">建立和設定傳送埠</span><span class="sxs-lookup"><span data-stu-id="737cd-116">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)