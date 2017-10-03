---
title: "設定 TIBCO 企業訊息服務傳輸屬性的接收埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive ports, setting transport properties
- transport properties, setting for receive port
- setting transport properties, receive port
ms.assetid: bccddf84-d92e-469f-aa6f-4234c91a0be9
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d94229364e3bed8faaf1407603f17db76c70e6bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="setting-tibco-enterprise-message-service-transport-properties-for-the-receive-port"></a><span data-ttu-id="9ed0f-102">設定 TIBCO 企業訊息服務接收埠的傳輸屬性</span><span class="sxs-lookup"><span data-stu-id="9ed0f-102">Setting TIBCO Enterprise Message Service Transport Properties for the Receive Port</span></span>
<span data-ttu-id="9ed0f-103">如 TIBCO Enterprise Message System (EMS) 接收位置， **URL**和**目標命名空間**至 TIBCO EMS 系統是所需的組態值。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-103">For a TIBCO Enterprise Message System (EMS) receive location, the **URL** and **Target Namespace** to the TIBCO EMS System are the only configuration values required.</span></span>  
  
### <a name="to-specify-tibco-ems-transport-properties"></a><span data-ttu-id="9ed0f-104">指定 TIBCO EMS 傳輸屬性</span><span class="sxs-lookup"><span data-stu-id="9ed0f-104">To specify TIBCO EMS transport properties</span></span>  
  
1.  <span data-ttu-id="9ed0f-105">展開**系統定義**並輸入 TIBCO EMS 伺服器連線的所有必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-105">Expand the **System Definition** and enter all required information for connection to the TIBCO EMS server.</span></span>  
  
2.  <span data-ttu-id="9ed0f-106">展開**訊息處理**並輸入所有必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-106">Expand **Message Handling** and enter all required information.</span></span>  
  
    |<span data-ttu-id="9ed0f-107">參數</span><span class="sxs-lookup"><span data-stu-id="9ed0f-107">Parameter</span></span>|<span data-ttu-id="9ed0f-108">Description</span><span class="sxs-lookup"><span data-stu-id="9ed0f-108">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="9ed0f-109">**訊息選取器**</span><span class="sxs-lookup"><span data-stu-id="9ed0f-109">**Message Selector**</span></span>|<span data-ttu-id="9ed0f-110">只有在對目的地中的訊息評估此字串得到 True 時，才會接收訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-110">Messages are received only if this string evaluates to True with the message in the destination.</span></span><br /><br /> <span data-ttu-id="9ed0f-111">允許接收埠只接收內部標頭屬性與此欄位所述運算式相符的訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-111">Allows the receive port to retrieve only messages that contain header properties that match the expression described in this field.</span></span><br /><br /> <span data-ttu-id="9ed0f-112">訊息選取器的語法是以 SQL92 條件運算式語法的子集為基礎。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-112">The syntax of message selectors is based on a subset of the SQL92 conditional expression syntax.</span></span> <span data-ttu-id="9ed0f-113">TIBCO EMS 使用者指南含有此語法的完整說明。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-113">The syntax is fully described in the TIBCO EMS users guide.</span></span><br /><br /> <span data-ttu-id="9ed0f-114">例如，如果訊息中包含名為 NewsType 的標頭屬性，則接收埠只能擷取屬於 Sports 或 Editorial 類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-114">For example, if a message contains a header property name NewsType, a receive port can retrieve only those that are of type Sports or Editorial.</span></span>|  
    |<span data-ttu-id="9ed0f-115">**重試計數**</span><span class="sxs-lookup"><span data-stu-id="9ed0f-115">**Retry Count**</span></span>|<span data-ttu-id="9ed0f-116">傳輸的重試計數。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-116">The retry count for the transport.</span></span> <span data-ttu-id="9ed0f-117">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-117">Default value is 0.</span></span>|  
    |<span data-ttu-id="9ed0f-118">**重試間隔**</span><span class="sxs-lookup"><span data-stu-id="9ed0f-118">**Retry Interval**</span></span>|<span data-ttu-id="9ed0f-119">配接器進行重試之前所等候的時間。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-119">The period of time the adapter waits before initiating a retry.</span></span> <span data-ttu-id="9ed0f-120">預設值為五分鐘。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-120">Default value is five minutes.</span></span>|  
  
3.  <span data-ttu-id="9ed0f-121">展開**伺服器連線定義**並輸入所有必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-121">Expand the **Server Connection Definition** and enter all required information.</span></span>  
  
    |<span data-ttu-id="9ed0f-122">參數</span><span class="sxs-lookup"><span data-stu-id="9ed0f-122">Parameter</span></span>|<span data-ttu-id="9ed0f-123">Description</span><span class="sxs-lookup"><span data-stu-id="9ed0f-123">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="9ed0f-124">**目的地**</span><span class="sxs-lookup"><span data-stu-id="9ed0f-124">**Destination**</span></span>|<span data-ttu-id="9ed0f-125">必要設定。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-125">Mandatory setting.</span></span> <span data-ttu-id="9ed0f-126">定義目的地的名稱與類型。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-126">Defines the name and type of the destination.</span></span> <span data-ttu-id="9ed0f-127">使用下列格式定義佇列或主題：Queue[queue.name] 或 Topic[topic.name]。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-127">Defines the queue or topic with the following format: Queue[queue.name] or Topic[topic.name].</span></span>|  
    |<span data-ttu-id="9ed0f-128">**通訊埠編號**</span><span class="sxs-lookup"><span data-stu-id="9ed0f-128">**Port Number**</span></span>|<span data-ttu-id="9ed0f-129">TIBCO EMS 伺服器所收聽的連接埠。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-129">Port on which the TIBCO EMS server listens.</span></span>|  
    |<span data-ttu-id="9ed0f-130">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="9ed0f-130">**Server Name**</span></span>|<span data-ttu-id="9ed0f-131">必要設定。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-131">Mandatory setting.</span></span> <span data-ttu-id="9ed0f-132">裝載 TIBCO EMS 伺服器的系統名稱。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-132">Name of the system hosting the TIBCO EMS server.</span></span>|  
  
4.  <span data-ttu-id="9ed0f-133">提供使用單一登入 (SSO) 的認證。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-133">Provide credentials using Single Sign-On (SSO).</span></span>  
  
     <span data-ttu-id="9ed0f-134">有兩種方法可以用來存取 TIBCO EMS 系統。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-134">There are two methods that you can use to access the TIBCO EMS system.</span></span> <span data-ttu-id="9ed0f-135">您可以使用「認證」(使用者名稱與密碼參數) 或「單一登入」。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-135">You can use Credentials (user name and password parameters) or Single Sign-On.</span></span>  
  
    -   <span data-ttu-id="9ed0f-136">選取**是**中**使用 SSO**使用單一登入。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-136">Select **Yes** in **Use SSO** to use Single Sign-On.</span></span>  
  
    -   <span data-ttu-id="9ed0f-137">在清單中選取分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-137">Select an affiliate application in the list.</span></span>  
  
         <span data-ttu-id="9ed0f-138">由企業單一登入工具所建立的分支機構應用程式代表如 TIBCO EMS 之類的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-138">An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as TIBCO EMS.</span></span> <span data-ttu-id="9ed0f-139">Microsoft BizTalk Adapter for TIBCO EMS 會使用應用程式使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-139">Microsoft BizTalk Adapter for TIBCO EMS uses the credentials of an application user.</span></span> <span data-ttu-id="9ed0f-140">這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 資料庫中擷取所得。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-140">These credentials are retrieved from the SSO database for the server system for a specified affiliate application.</span></span>  
  
         <span data-ttu-id="9ed0f-141">如需如何建立分支機構應用程式的詳細資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications5.md)。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-141">For more information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications5.md).</span></span>  
  
5.  <span data-ttu-id="9ed0f-142">展開**使用者認證**輸入**使用者名**和**密碼**來存取 TIBCO EMS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-142">Expand **User Credentials** and enter the **User Name** and **Password** to access the TIBCO EMS server.</span></span>  
  
    |<span data-ttu-id="9ed0f-143">參數</span><span class="sxs-lookup"><span data-stu-id="9ed0f-143">Parameter</span></span>|<span data-ttu-id="9ed0f-144">Description</span><span class="sxs-lookup"><span data-stu-id="9ed0f-144">Description</span></span>|  
    |---------------|-----------------|  
    |`Password`|<span data-ttu-id="9ed0f-145">用來與 TIBCO EMS 精靈通訊的使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-145">The user’s password that is used to communicate with a TIBCO EMS daemon.</span></span><br /><br /> <span data-ttu-id="9ed0f-146">如果您未選取**使用 SSO**，您必須設定為 BizTalk Adapter for TIBCO EMS 才能與 TIBCO EMS 精靈通訊的認證參數。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-146">If you did not select **Use SSO**, you must set credential parameters for BizTalk Adapter for TIBCO EMS to communicate with a TIBCO EMS daemon.</span></span>|  
    |`User Name`|<span data-ttu-id="9ed0f-147">用來與 TIBCO EMS 精靈通訊的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-147">Name of a user that is used to communicate with a TIBCO EMS daemon.</span></span><br /><br /> <span data-ttu-id="9ed0f-148">如果您未選取**使用 SSO**，您必須設定為 BizTalk Adapter for TIBCO EMS 才能與 TIBCO EMS 精靈通訊的認證參數。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-148">If you did not select **Use SSO**, you must set credential parameters for BizTalk Adapter for TIBCO EMS to communicate with a TIBCO EMS daemon.</span></span>|  
  
6.  <span data-ttu-id="9ed0f-149">按一下**套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="9ed0f-149">Click **Apply**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed0f-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ed0f-150">See Also</span></span>  
 <span data-ttu-id="9ed0f-151">[建立傳送埠](../core/creating-send-ports1.md) </span><span class="sxs-lookup"><span data-stu-id="9ed0f-151">[Creating Send Ports](../core/creating-send-ports1.md) </span></span>  
 [<span data-ttu-id="9ed0f-152">建立 TIBCO Enterprise Message Service 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="9ed0f-152">Creating TIBCO Enterprise Message Service Receive Handlers</span></span>](../core/creating-tibco-enterprise-message-service-receive-handlers.md)