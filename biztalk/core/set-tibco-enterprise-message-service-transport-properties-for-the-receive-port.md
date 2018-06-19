---
redirect_url: /biztalk/core/creating-tibco-enterprise-message-service-receive-handlers/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: 1a32564f9e0e9e81624b39ab0ba156e76b109497
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24014037"
---
# <a name="setting-tibco-enterprise-message-service-transport-properties-for-the-receive-port"></a><span data-ttu-id="7d2cd-101">設定 TIBCO 企業訊息服務接收埠的傳輸屬性</span><span class="sxs-lookup"><span data-stu-id="7d2cd-101">Setting TIBCO Enterprise Message Service Transport Properties for the Receive Port</span></span>
<span data-ttu-id="7d2cd-102">如 TIBCO Enterprise Message System (EMS) 接收位置， **URL**和**目標命名空間**至 TIBCO EMS 系統是所需的組態值。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-102">For a TIBCO Enterprise Message System (EMS) receive location, the **URL** and **Target Namespace** to the TIBCO EMS System are the only configuration values required.</span></span>  
  
### <a name="to-specify-tibco-ems-transport-properties"></a><span data-ttu-id="7d2cd-103">指定 TIBCO EMS 傳輸屬性</span><span class="sxs-lookup"><span data-stu-id="7d2cd-103">To specify TIBCO EMS transport properties</span></span>  
  
1.  <span data-ttu-id="7d2cd-104">展開**系統定義**並輸入 TIBCO EMS 伺服器連線的所有必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-104">Expand the **System Definition** and enter all required information for connection to the TIBCO EMS server.</span></span>  
  
2.  <span data-ttu-id="7d2cd-105">展開**訊息處理**並輸入所有必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-105">Expand **Message Handling** and enter all required information.</span></span>  
  
    |<span data-ttu-id="7d2cd-106">參數</span><span class="sxs-lookup"><span data-stu-id="7d2cd-106">Parameter</span></span>|<span data-ttu-id="7d2cd-107">Description</span><span class="sxs-lookup"><span data-stu-id="7d2cd-107">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="7d2cd-108">**訊息選取器**</span><span class="sxs-lookup"><span data-stu-id="7d2cd-108">**Message Selector**</span></span>|<span data-ttu-id="7d2cd-109">只有在對目的地中的訊息評估此字串得到 True 時，才會接收訊息。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-109">Messages are received only if this string evaluates to True with the message in the destination.</span></span><br /><br /> <span data-ttu-id="7d2cd-110">允許接收埠只接收內部標頭屬性與此欄位所述運算式相符的訊息。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-110">Allows the receive port to retrieve only messages that contain header properties that match the expression described in this field.</span></span><br /><br /> <span data-ttu-id="7d2cd-111">訊息選取器的語法是以 SQL92 條件運算式語法的子集為基礎。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-111">The syntax of message selectors is based on a subset of the SQL92 conditional expression syntax.</span></span> <span data-ttu-id="7d2cd-112">TIBCO EMS 使用者指南含有此語法的完整說明。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-112">The syntax is fully described in the TIBCO EMS users guide.</span></span><br /><br /> <span data-ttu-id="7d2cd-113">例如，如果訊息中包含名為 NewsType 的標頭屬性，則接收埠只能擷取屬於 Sports 或 Editorial 類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-113">For example, if a message contains a header property name NewsType, a receive port can retrieve only those that are of type Sports or Editorial.</span></span>|  
    |<span data-ttu-id="7d2cd-114">**重試計數**</span><span class="sxs-lookup"><span data-stu-id="7d2cd-114">**Retry Count**</span></span>|<span data-ttu-id="7d2cd-115">傳輸的重試計數。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-115">The retry count for the transport.</span></span> <span data-ttu-id="7d2cd-116">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-116">Default value is 0.</span></span>|  
    |<span data-ttu-id="7d2cd-117">**重試間隔**</span><span class="sxs-lookup"><span data-stu-id="7d2cd-117">**Retry Interval**</span></span>|<span data-ttu-id="7d2cd-118">配接器進行重試之前所等候的時間。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-118">The period of time the adapter waits before initiating a retry.</span></span> <span data-ttu-id="7d2cd-119">預設值為五分鐘。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-119">Default value is five minutes.</span></span>|  
  
3.  <span data-ttu-id="7d2cd-120">展開**伺服器連線定義**並輸入所有必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-120">Expand the **Server Connection Definition** and enter all required information.</span></span>  
  
    |<span data-ttu-id="7d2cd-121">參數</span><span class="sxs-lookup"><span data-stu-id="7d2cd-121">Parameter</span></span>|<span data-ttu-id="7d2cd-122">Description</span><span class="sxs-lookup"><span data-stu-id="7d2cd-122">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="7d2cd-123">**目的地**</span><span class="sxs-lookup"><span data-stu-id="7d2cd-123">**Destination**</span></span>|<span data-ttu-id="7d2cd-124">必要設定。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-124">Mandatory setting.</span></span> <span data-ttu-id="7d2cd-125">定義目的地的名稱與類型。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-125">Defines the name and type of the destination.</span></span> <span data-ttu-id="7d2cd-126">使用下列格式定義佇列或主題：Queue[queue.name] 或 Topic[topic.name]。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-126">Defines the queue or topic with the following format: Queue[queue.name] or Topic[topic.name].</span></span>|  
    |<span data-ttu-id="7d2cd-127">**通訊埠編號**</span><span class="sxs-lookup"><span data-stu-id="7d2cd-127">**Port Number**</span></span>|<span data-ttu-id="7d2cd-128">TIBCO EMS 伺服器所收聽的連接埠。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-128">Port on which the TIBCO EMS server listens.</span></span>|  
    |<span data-ttu-id="7d2cd-129">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="7d2cd-129">**Server Name**</span></span>|<span data-ttu-id="7d2cd-130">必要設定。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-130">Mandatory setting.</span></span> <span data-ttu-id="7d2cd-131">裝載 TIBCO EMS 伺服器的系統名稱。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-131">Name of the system hosting the TIBCO EMS server.</span></span>|  
  
4.  <span data-ttu-id="7d2cd-132">提供使用單一登入 (SSO) 的認證。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-132">Provide credentials using Single Sign-On (SSO).</span></span>  
  
     <span data-ttu-id="7d2cd-133">有兩種方法可以用來存取 TIBCO EMS 系統。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-133">There are two methods that you can use to access the TIBCO EMS system.</span></span> <span data-ttu-id="7d2cd-134">您可以使用「認證」(使用者名稱與密碼參數) 或「單一登入」。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-134">You can use Credentials (user name and password parameters) or Single Sign-On.</span></span>  
  
    -   <span data-ttu-id="7d2cd-135">選取**是**中**使用 SSO**使用單一登入。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-135">Select **Yes** in **Use SSO** to use Single Sign-On.</span></span>  
  
    -   <span data-ttu-id="7d2cd-136">在清單中選取分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-136">Select an affiliate application in the list.</span></span>  
  
         <span data-ttu-id="7d2cd-137">由企業單一登入工具所建立的分支機構應用程式代表如 TIBCO EMS 之類的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-137">An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as TIBCO EMS.</span></span> <span data-ttu-id="7d2cd-138">Microsoft BizTalk Adapter for TIBCO EMS 會使用應用程式使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-138">Microsoft BizTalk Adapter for TIBCO EMS uses the credentials of an application user.</span></span> <span data-ttu-id="7d2cd-139">這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 資料庫中擷取所得。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-139">These credentials are retrieved from the SSO database for the server system for a specified affiliate application.</span></span>  
  
         <span data-ttu-id="7d2cd-140">如需如何建立分支機構應用程式的詳細資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications5.md)。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-140">For more information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications5.md).</span></span>  
  
5.  <span data-ttu-id="7d2cd-141">展開**使用者認證**輸入**使用者名**和**密碼**來存取 TIBCO EMS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-141">Expand **User Credentials** and enter the **User Name** and **Password** to access the TIBCO EMS server.</span></span>  
  
    |<span data-ttu-id="7d2cd-142">參數</span><span class="sxs-lookup"><span data-stu-id="7d2cd-142">Parameter</span></span>|<span data-ttu-id="7d2cd-143">Description</span><span class="sxs-lookup"><span data-stu-id="7d2cd-143">Description</span></span>|  
    |---------------|-----------------|  
    |`Password`|<span data-ttu-id="7d2cd-144">用來與 TIBCO EMS 精靈通訊的使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-144">The user’s password that is used to communicate with a TIBCO EMS daemon.</span></span><br /><br /> <span data-ttu-id="7d2cd-145">如果您未選取**使用 SSO**，您必須設定為 BizTalk Adapter for TIBCO EMS 才能與 TIBCO EMS 精靈通訊的認證參數。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-145">If you did not select **Use SSO**, you must set credential parameters for BizTalk Adapter for TIBCO EMS to communicate with a TIBCO EMS daemon.</span></span>|  
    |`User Name`|<span data-ttu-id="7d2cd-146">用來與 TIBCO EMS 精靈通訊的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-146">Name of a user that is used to communicate with a TIBCO EMS daemon.</span></span><br /><br /> <span data-ttu-id="7d2cd-147">如果您未選取**使用 SSO**，您必須設定為 BizTalk Adapter for TIBCO EMS 才能與 TIBCO EMS 精靈通訊的認證參數。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-147">If you did not select **Use SSO**, you must set credential parameters for BizTalk Adapter for TIBCO EMS to communicate with a TIBCO EMS daemon.</span></span>|  
  
6.  <span data-ttu-id="7d2cd-148">按一下**套用**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="7d2cd-148">Click **Apply**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d2cd-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d2cd-149">See Also</span></span>  
  [<span data-ttu-id="7d2cd-150">建立 TIBCO Enterprise Message Service 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="7d2cd-150">Creating TIBCO Enterprise Message Service Receive Handlers</span></span>](../core/creating-tibco-enterprise-message-service-receive-handlers.md)