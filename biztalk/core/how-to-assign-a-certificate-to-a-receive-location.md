---
title: 如何將憑證指派給接收位置 |Microsoft Docs
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
ms.assetid: 54ae300e-62c5-480f-a9b7-e5c3457a0f80
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 094b49aba2e55e20ad32304f5b700126a2322d75
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995311"
---
# <a name="how-to-assign-a-certificate-to-a-receive-location"></a><span data-ttu-id="d8030-102">如何將憑證指派給接收位置</span><span class="sxs-lookup"><span data-stu-id="d8030-102">How to Assign a Certificate to a Receive Location</span></span>
<span data-ttu-id="d8030-103">本主題說明如何使用「BizTalk Server管理」主控台，將安全性憑證指派給接收位置。</span><span class="sxs-lookup"><span data-stu-id="d8030-103">This topic describes how to use the BizTalk Server Administration console to assign a security certificate to a receive location.</span></span> <span data-ttu-id="d8030-104">您只能在雙向接收位置上執行此程序。</span><span class="sxs-lookup"><span data-stu-id="d8030-104">You can perform this procedure on a two-way receive location only.</span></span> <span data-ttu-id="d8030-105">憑證必須存在於執行 BizTalk Server 之電腦的「其他人」憑證存放區，否則無法處理與此接收位置相關的訊息，並且會有錯誤列入記錄。</span><span class="sxs-lookup"><span data-stu-id="d8030-105">The certificate must exist in the Other People certificate store on the computer running BizTalk Server, or messages associated with this receive location will not be processed, and errors will be logged.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d8030-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="d8030-106">Prerequisites</span></span>  
 <span data-ttu-id="d8030-107">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="d8030-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="d8030-108">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="d8030-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-assign-a-certificate-to-a-receive-location"></a><span data-ttu-id="d8030-109">若要將憑證指派給接收位置</span><span class="sxs-lookup"><span data-stu-id="d8030-109">To assign a certificate to a receive location</span></span>  
  
1. <span data-ttu-id="d8030-110">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="d8030-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="d8030-111">在主控台樹狀結構中，展開您要為其指派憑證給接收位置的 BizTalk 群組與 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8030-111">In the console tree, expand the BizTalk group and the BizTalk application for which you want to assign a certificate to a receive location.</span></span>  
  
3. <span data-ttu-id="d8030-112">依序展開**接收位置**，以滑鼠右鍵按一下接收位置，按一下**屬性**，然後按一下**憑證**。</span><span class="sxs-lookup"><span data-stu-id="d8030-112">Expand **Receive Locations**, right-click the receive location, click **Properties**, and then click **Certificate**.</span></span>  
  
4. <span data-ttu-id="d8030-113">如果憑證存在本機電腦上，按一下**瀏覽**，瀏覽至您想要指派給此憑證的接收位置，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d8030-113">If the certificate exists on the local computer, click **Browse**, browse to the certificate that you want to assign to this receive location, and then click **OK**.</span></span> <span data-ttu-id="d8030-114">否則，略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="d8030-114">Otherwise, skip this step.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="d8030-115">如果您是從遠端電腦執行此作業，請確定憑證不僅存在於本機電腦，也存在於執行 BizTalk Server 的電腦。</span><span class="sxs-lookup"><span data-stu-id="d8030-115">If you are performing this operation from a remote computer, make sure that the certificate exists on the computer running BizTalk Server, and not only on the local computer.</span></span> <span data-ttu-id="d8030-116">否則，接收位置將無法處理訊息。</span><span class="sxs-lookup"><span data-stu-id="d8030-116">Otherwise, the receive location will not be able to process messages.</span></span>  
  
5. <span data-ttu-id="d8030-117">如果憑證不存在的本機電腦上，在**指紋**方塊中輸入或貼上憑證指紋，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d8030-117">If the certificate does not exist on the local computer, in the **Thumbprint** box, type or paste the certificate thumbprint, and then click **OK**.</span></span> <span data-ttu-id="d8030-118">憑證指紋的格式為 HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH，其中 H 是十六進位數字。</span><span class="sxs-lookup"><span data-stu-id="d8030-118">The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8030-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8030-119">See Also</span></span>  
 [<span data-ttu-id="d8030-120">管理接收位置</span><span class="sxs-lookup"><span data-stu-id="d8030-120">Managing Receive Locations</span></span>](../core/managing-receive-locations.md)