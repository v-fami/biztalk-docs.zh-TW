---
title: 如何設定每個執行個體管線屬性的接收位置 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, properties
- receive locations, configuring
- managing [pipelines], properties
- managing [pipelines], receive locations
- managing [receive locations], pipelines
- managing [pipelines], configuring
- pipelines, receive locations
- pipelines, configuring
- receive locations, pipelines
- managing [receive locations], configuring
ms.assetid: e1ed3b10-2f39-479b-a3e6-22b4b2872192
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e14483c5d17d968fc79126c65506720b501b6da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248838"
---
# <a name="how-to-configure-per-instance-pipeline-properties-for-a-receive-location"></a><span data-ttu-id="2f46b-102">如何設定接收位置的個別執行個體管線屬性</span><span class="sxs-lookup"><span data-stu-id="2f46b-102">How to Configure Per-instance Pipeline Properties for a Receive Location</span></span>
<span data-ttu-id="2f46b-103">本主題描述如何在將管線部署到 BizTalk 群組後，使用 BizTalk Server 管理主控台來設定接收位置的管線屬性。</span><span class="sxs-lookup"><span data-stu-id="2f46b-103">This topic describes how to use the BizTalk Server Administration console to configure pipeline properties for a receive location after the pipeline has been deployed into a BizTalk group.</span></span> <span data-ttu-id="2f46b-104">您所做的變更只會覆寫這個接收位置的預設管線屬性，因此您也可以為 BizTalk 群組中的每個接收位置設定不同的管線屬性。</span><span class="sxs-lookup"><span data-stu-id="2f46b-104">Changes that you make overwrite the default pipeline properties for this receive location only, so if you want, you can configure different pipeline properties for each receive location in the BizTalk group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2f46b-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="2f46b-105">Prerequisites</span></span>  
 <span data-ttu-id="2f46b-106">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="2f46b-106">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="2f46b-107">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="2f46b-107">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f46b-108">當您使用每個執行個體管線屬性設定的值時**DocumentSpecNames** XML 解譯器元件的管線、 指定的文件結構描述和管線中的屬性必須定義相同專案中。</span><span class="sxs-lookup"><span data-stu-id="2f46b-108">When using per-instance pipeline properties to set the value for the **DocumentSpecNames** property in the XML disassembler component of a pipeline, the specified document schema and the pipeline must be defined in the same project.</span></span>  
  
### <a name="to-configure-per-instance-pipeline-properties-for-a-receive-location"></a><span data-ttu-id="2f46b-109">設定接收位置的個別執行個體管線屬性</span><span class="sxs-lookup"><span data-stu-id="2f46b-109">To configure per-instance pipeline properties for a receive location</span></span>  
  
1.  <span data-ttu-id="2f46b-110">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="2f46b-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="2f46b-111">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開包含該接收位置，這是要設定管線屬性中，展開 BizTalk 群組**應用程式**，然後按一下展開包含該接收位置的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f46b-111">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the receive location for which to configure pipeline properties, expand **Applications**, and then expand the application containing the receive location.</span></span>  
  
3.  <span data-ttu-id="2f46b-112">按一下**接收位置**資料夾中，以滑鼠右鍵按一下接收位置，然後**屬性**。</span><span class="sxs-lookup"><span data-stu-id="2f46b-112">Click the **Receive Locations** folder, right-click the receive location, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="2f46b-113">按一下右邊的省略符號 （...）**接收管線**方塊。</span><span class="sxs-lookup"><span data-stu-id="2f46b-113">Click the ellipsis (…) to the right of the **Receive Pipeline** box.</span></span>  
  
5.  <span data-ttu-id="2f46b-114">設定的屬性，然後按**確定**。</span><span class="sxs-lookup"><span data-stu-id="2f46b-114">Configure the properties you want, and then click **OK**.</span></span> <span data-ttu-id="2f46b-115">如需詳細資訊，請按一下**協助**內容 頁面上。</span><span class="sxs-lookup"><span data-stu-id="2f46b-115">For more information, click **Help** on the properties page.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="2f46b-116">請確定您已輸入管線屬性的正確資訊。</span><span class="sxs-lookup"><span data-stu-id="2f46b-116">Make sure that you enter correct information for pipelines properties.</span></span> <span data-ttu-id="2f46b-117">如果輸入無效的值 (例如，輸入字串而非數字)，將會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="2f46b-117">If you enter an invalid value, for example a string rather than a number, it will generate an error.</span></span>  
  
6.  <span data-ttu-id="2f46b-118">如果這是要求-回應接收位置，按一下右邊的省略符號 （...）**傳送管線**方塊。</span><span class="sxs-lookup"><span data-stu-id="2f46b-118">If this is a request-response receive location, click the ellipsis (…) to the right of the **Send Pipeline** box.</span></span>  
  
7.  <span data-ttu-id="2f46b-119">設定的屬性，然後按**確定**兩次。</span><span class="sxs-lookup"><span data-stu-id="2f46b-119">Configure the properties you want, and then click **OK** twice.</span></span> <span data-ttu-id="2f46b-120">如需詳細資訊，請按一下**協助**內容 頁面上。</span><span class="sxs-lookup"><span data-stu-id="2f46b-120">For more information, click **Help** on the properties page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f46b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f46b-121">See Also</span></span>  
 <span data-ttu-id="2f46b-122">[管理管線](../core/managing-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="2f46b-122">[Managing Pipelines](../core/managing-pipelines.md) </span></span>  
 <span data-ttu-id="2f46b-123">[建立和設定傳送埠](../core/creating-and-configuring-send-ports.md) </span><span class="sxs-lookup"><span data-stu-id="2f46b-123">[Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md) </span></span>  
 [<span data-ttu-id="2f46b-124">管理接收位置</span><span class="sxs-lookup"><span data-stu-id="2f46b-124">Managing Receive Locations</span></span>](../core/managing-receive-locations.md)