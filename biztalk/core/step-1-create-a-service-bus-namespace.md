---
title: 步驟 1： 建立服務匯流排命名空間 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ede1ac50-bbfb-4aeb-8217-1877ae218f89
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4d7630316f72fd63bac5ce7127b5451683e2f97
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276758"
---
# <a name="step-1-create-a-service-bus-namespace"></a><span data-ttu-id="6f1bd-102">步驟 1： 建立服務匯流排命名空間</span><span class="sxs-lookup"><span data-stu-id="6f1bd-102">Step 1: Create a Service Bus Namespace</span></span>
<span data-ttu-id="6f1bd-103">在此步驟中，您會建立[!INCLUDE[winazure](../includes/winazure-md.md)][!INCLUDE[sb](../includes/sb-md.md)]命名空間。</span><span class="sxs-lookup"><span data-stu-id="6f1bd-103">In this step, you create a [!INCLUDE[winazure](../includes/winazure-md.md)][!INCLUDE[sb](../includes/sb-md.md)] namespace.</span></span> <span data-ttu-id="6f1bd-104">您將使用此命名空間來裝載接收來自 Salesforce 的商機通知的轉送端點。</span><span class="sxs-lookup"><span data-stu-id="6f1bd-104">You will use this namespace to host a relay endpoint for receiving opportunity notifications from Salesforce.</span></span> <span data-ttu-id="6f1bd-105">稍後在建立此方案，您會使用這個轉送端點來接收通知訊息至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。</span><span class="sxs-lookup"><span data-stu-id="6f1bd-105">Later in the process of creating this solution, you will use this relay endpoint to receive the notification message into a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system.</span></span>  
  
### <a name="to-create-a-includesbincludessb-mdmd-namespace"></a><span data-ttu-id="6f1bd-106">若要建立[!INCLUDE[sb](../includes/sb-md.md)]命名空間</span><span class="sxs-lookup"><span data-stu-id="6f1bd-106">To create a [!INCLUDE[sb](../includes/sb-md.md)] namespace</span></span>  
  
1.  <span data-ttu-id="6f1bd-107">登入[http://manage.windowsazure.com](http://manage.windowsazure.com)使用您的 Microsoft 帳戶。</span><span class="sxs-lookup"><span data-stu-id="6f1bd-107">Log on to [http://manage.windowsazure.com](http://manage.windowsazure.com) using your Microsoft account.</span></span>  
  
2.  <span data-ttu-id="6f1bd-108">在頁面底部，按一下**新增**，**應用程式服務**， **Service Bus 轉送**，然後**快速建立**。</span><span class="sxs-lookup"><span data-stu-id="6f1bd-108">At the bottom of the page, click **New**, **App Services**, **Service Bus Relay**, and then **Quick Create**.</span></span>  
  
3.  <span data-ttu-id="6f1bd-109">輸入的命名空間為`BtsSalesforce`，然後選取最接近您目前的地理位置區域。</span><span class="sxs-lookup"><span data-stu-id="6f1bd-109">Enter the namespace as `BtsSalesforce` and select a region closest to your current geographical location.</span></span> <span data-ttu-id="6f1bd-110">按一下**建立轉送**。</span><span class="sxs-lookup"><span data-stu-id="6f1bd-110">Click **Create a Relay**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="6f1bd-111">此命名空間必須是全域唯一的。</span><span class="sxs-lookup"><span data-stu-id="6f1bd-111">This namespace must be globally unique.</span></span> <span data-ttu-id="6f1bd-112">因此，您必須使用在本教學課程提到以外的命名空間。</span><span class="sxs-lookup"><span data-stu-id="6f1bd-112">So, you must use a namespace other than one mentioned in this tutorial.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6f1bd-113">請注意，轉送不會建立作業的一部分，此命名空間。</span><span class="sxs-lookup"><span data-stu-id="6f1bd-113">Note that the relay is not created as part of the operation, only the namespace is.</span></span> <span data-ttu-id="6f1bd-114">當我們設定的接收位置的轉送端點建立稍後在本教學課程**Sb-messaging**配接器。</span><span class="sxs-lookup"><span data-stu-id="6f1bd-114">The relay endpoint is created later in this tutorial when we configure a receive location for the **SB-Messaging** adapter.</span></span>  
  
4.  <span data-ttu-id="6f1bd-115">建立命名空間之後，狀態也設為**Active**。</span><span class="sxs-lookup"><span data-stu-id="6f1bd-115">After the namespace is created, the status is set to **Active**.</span></span> <span data-ttu-id="6f1bd-116">作用中狀態之後，您可以選取的命名空間，然後按一下**便捷鍵**頁面以取得詳細資料，如何連接到底部**BtsSalesforce**命名空間，包括值**預設使用者**和**預設金鑰**。</span><span class="sxs-lookup"><span data-stu-id="6f1bd-116">Once the status is active, you can select the namespace and click **Access Key** at the bottom of the page to get details on how to connect to the **BtsSalesforce** namespace, including the values for **Default User** and **Default Key**.</span></span> <span data-ttu-id="6f1bd-117">稍後在本教學課程中，您將需要這些詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6f1bd-117">You will need these details later in the tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f1bd-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f1bd-118">See Also</span></span>  
 [<span data-ttu-id="6f1bd-119">教學課程 6： 與 Salesforce 整合 BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="6f1bd-119">Tutorial 6: Integrating BizTalk Server 2013 with Salesforce</span></span>](Tutorial:%20Integrating%20BizTalk%20Server%202013%20with%20Salesforce.md)