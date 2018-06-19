---
title: 如何指派憑證給傳送埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates, assigning
- managing [send ports], certificates
- assigning certificates
- certificates, send ports
ms.assetid: ba9e9c8b-f5b6-4fee-9e89-31b0f1df6ed4
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec19c845c6b0cfb5d19bd7a961fe9ddfbcf2a3d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247478"
---
# <a name="how-to-assign-a-certificate-to-a-send-port"></a><span data-ttu-id="163eb-102">如何指派憑證給傳送埠</span><span class="sxs-lookup"><span data-stu-id="163eb-102">How to Assign a Certificate to a Send Port</span></span>
<span data-ttu-id="163eb-103">本主題描述如何使用 BizTalk Server 管理主控台來指派安全性憑證給傳送埠。</span><span class="sxs-lookup"><span data-stu-id="163eb-103">This topic describes how to use the BizTalk Server Administration console to assign a security certificate to a send port.</span></span> <span data-ttu-id="163eb-104">憑證必須存在於執行 BizTalk Server 之電腦的「其他人」憑證存放區，否則無法處理與此傳送埠相關的訊息，並且會有錯誤列入記錄。</span><span class="sxs-lookup"><span data-stu-id="163eb-104">The certificate must exist in the Other People certificate store on the computer running BizTalk Server, or messages associated with this send port will not be processed, and errors will be logged.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="163eb-105">應用程式開發人員可以使用此主題中的程序，在開發程序中指派安全性憑證給傳送埠。</span><span class="sxs-lookup"><span data-stu-id="163eb-105">The application developer can assign a security certificate to a send port during the development process by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="163eb-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="163eb-106">Prerequisites</span></span>  
 <span data-ttu-id="163eb-107">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="163eb-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="163eb-108">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="163eb-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-assign-a-certificate-to-a-send-port"></a><span data-ttu-id="163eb-109">指派憑證給傳送埠</span><span class="sxs-lookup"><span data-stu-id="163eb-109">To assign a certificate to a send port</span></span>  
  
1.  <span data-ttu-id="163eb-110">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="163eb-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="163eb-111">在主控台樹狀結構中，展開您要為其指派憑證給傳送埠的 BizTalk 群組與 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="163eb-111">In the console tree, expand the BizTalk group and the BizTalk application for which you want to assign a certificate to a send port.</span></span>  
  
3.  <span data-ttu-id="163eb-112">展開**傳送埠**，以滑鼠右鍵按一下傳送埠，按一下**屬性**，然後按一下 **憑證**。</span><span class="sxs-lookup"><span data-stu-id="163eb-112">Expand **Send Ports**, right-click the send port, click **Properties**, and then click **Certificate**.</span></span>  
  
4.  <span data-ttu-id="163eb-113">如果憑證存在於本機電腦上，按一下**瀏覽**，瀏覽至您想要指派給這個傳送埠，然後按一下 憑證**確定**。</span><span class="sxs-lookup"><span data-stu-id="163eb-113">If the certificate exists on the local computer, click **Browse**, browse to the certificate that you want to assign to this send port, and then click **OK**.</span></span> <span data-ttu-id="163eb-114">否則，略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="163eb-114">Otherwise, skip this step.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="163eb-115">即使憑證存在於本機電腦，執行 BizTalk Server 的電腦 (如果是兩台不同的電腦) 上也必須有這個憑證，傳送埠才能夠處理訊息。</span><span class="sxs-lookup"><span data-stu-id="163eb-115">Even if the certificate exists on the local computer, it must also exist on the computer running BizTalk Server, if different, before the send port will be able to process messages.</span></span>  
  
5.  <span data-ttu-id="163eb-116">如果憑證不存在於本機電腦上**指紋**方塊中輸入或貼上憑證指紋，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="163eb-116">If the certificate does not exist on the local computer, in the **Thumbprint** box, type or paste the certificate thumbprint, and then click **OK**.</span></span> <span data-ttu-id="163eb-117">憑證指紋的格式為 HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH，其中 H 是十六進位數字。</span><span class="sxs-lookup"><span data-stu-id="163eb-117">The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="163eb-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="163eb-118">See Also</span></span>  
 [<span data-ttu-id="163eb-119">建立和設定傳送埠</span><span class="sxs-lookup"><span data-stu-id="163eb-119">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)