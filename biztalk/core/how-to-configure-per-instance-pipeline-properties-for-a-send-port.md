---
title: 如何設定傳送埠的每個執行個體管線屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, properties
- managing [pipelines], properties
- configuring, send ports
- configuring, pipelines
- managing [pipelines], configuring
- managing [send ports], pipelines
- managing [send ports], configuring
- send ports, pipelines
- pipelines, configuring
ms.assetid: c58faa9e-0dfb-458b-8f1b-d3c91bce0436
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d1d49f0c6f54341c14cb14c38cc0de7fefaa9a9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990999"
---
# <a name="how-to-configure-per-instance-pipeline-properties-for-a-send-port"></a><span data-ttu-id="14c39-102">如何設定傳送埠的個別執行個體管線屬性</span><span class="sxs-lookup"><span data-stu-id="14c39-102">How to Configure Per-Instance Pipeline Properties for a Send Port</span></span>
<span data-ttu-id="14c39-103">本主題描述如何在將管線部署到 BizTalk 群組後，使用 BizTalk Server 管理主控台來設定傳送埠的管線屬性。</span><span class="sxs-lookup"><span data-stu-id="14c39-103">This topic describes how to use the BizTalk Server Administration console to configure pipeline properties for a send port after the pipeline has been deployed into a BizTalk group.</span></span> <span data-ttu-id="14c39-104">您所做的變更只會覆寫這個傳送埠的預設管線屬性，因此您也可以為 BizTalk 群組中的每個傳送埠設定不同的管線屬性。</span><span class="sxs-lookup"><span data-stu-id="14c39-104">Changes that you make overwrite the default pipeline properties for this send port only, so if you want, you can configure different pipeline properties for each send port in the BizTalk group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="14c39-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="14c39-105">Prerequisites</span></span>  
 <span data-ttu-id="14c39-106">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="14c39-106">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="14c39-107">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="14c39-107">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14c39-108">使用每個執行個體管線屬性設定的值時**DocumentSpecNames** XML 解譯器元件的管線，指定的文件結構描述和管線中的屬性必須定義相同的專案中。</span><span class="sxs-lookup"><span data-stu-id="14c39-108">When using per-instance pipeline properties to set the value for the **DocumentSpecNames** property in the XML disassembler component of a pipeline, the specified document schema and the pipeline must be defined in the same project.</span></span>  
  
### <a name="to-configure-per-instance-pipeline-properties-for-a-send-port"></a><span data-ttu-id="14c39-109">設定傳送埠的個別執行個體管線屬性</span><span class="sxs-lookup"><span data-stu-id="14c39-109">To configure per-instance pipeline properties for a send port</span></span>  
  
1. <span data-ttu-id="14c39-110">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="14c39-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="14c39-111">在主控台樹狀目錄中，依序展開**BizTalk Server 管理]**，展開包含您要設定管線屬性中，展開 [傳送埠的 BizTalk 群組**應用程式**，然後展開包含該傳送埠的應用程式。</span><span class="sxs-lookup"><span data-stu-id="14c39-111">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the send port for which you want to configure pipeline properties, expand **Applications**, and then expand the application containing the send port.</span></span>  
  
3. <span data-ttu-id="14c39-112">按一下 **傳送埠**資料夾中，以滑鼠右鍵按一下傳送埠，然後**屬性**。</span><span class="sxs-lookup"><span data-stu-id="14c39-112">Click the **Send Ports** folder, right-click the send port, and then click **Properties**.</span></span>  
  
4. <span data-ttu-id="14c39-113">按一下省略符號 (**...**) 按鈕右邊**的傳送管線** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="14c39-113">Click the ellipsis (**…**) button to the right of the **Send Pipeline** box.</span></span>  
  
5. <span data-ttu-id="14c39-114">設定的屬性，然後按**確定**。</span><span class="sxs-lookup"><span data-stu-id="14c39-114">Configure the properties you want, and then click **OK**.</span></span> <span data-ttu-id="14c39-115">按一下 **協助**如需詳細資訊的 內容 頁面上。</span><span class="sxs-lookup"><span data-stu-id="14c39-115">Click **Help** on the properties page for more information.</span></span>  
  
   > [!IMPORTANT]
   >  <span data-ttu-id="14c39-116">請確定您已輸入管線屬性的正確資訊。</span><span class="sxs-lookup"><span data-stu-id="14c39-116">Make sure that you enter correct information for pipelines properties.</span></span> <span data-ttu-id="14c39-117">如果輸入無效的值 (例如，輸入字串而非數字)，將會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="14c39-117">If you enter an invalid value, for example a string rather than a number, it will generate an error.</span></span>  
  
6. <span data-ttu-id="14c39-118">如果這是請求-回應傳送埠時，按一下省略符號 (**...**) 按鈕右邊**接收管線** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="14c39-118">If this is a solicit-response send port, click the ellipsis (**…**) button to the right of the **Receive Pipeline** box.</span></span>  
  
7. <span data-ttu-id="14c39-119">設定的屬性，然後按**確定**兩次。</span><span class="sxs-lookup"><span data-stu-id="14c39-119">Configure the properties you want, and then click **OK** twice.</span></span> <span data-ttu-id="14c39-120">按一下 **協助**如需詳細資訊的 內容 頁面上。</span><span class="sxs-lookup"><span data-stu-id="14c39-120">Click **Help** on the properties page for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14c39-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14c39-121">See Also</span></span>  
 <span data-ttu-id="14c39-122">[管理管線](../core/managing-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="14c39-122">[Managing Pipelines](../core/managing-pipelines.md) </span></span>  
 <span data-ttu-id="14c39-123">[建立和設定傳送埠](../core/creating-and-configuring-send-ports.md) </span><span class="sxs-lookup"><span data-stu-id="14c39-123">[Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md) </span></span>  
 [<span data-ttu-id="14c39-124">管理接收位置</span><span class="sxs-lookup"><span data-stu-id="14c39-124">Managing Receive Locations</span></span>](../core/managing-receive-locations.md)