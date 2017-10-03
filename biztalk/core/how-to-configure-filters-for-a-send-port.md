---
title: "如何設定傳送埠的篩選器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filters, configuring
- filters, send ports
- configuring, filters
- managing [send ports], configuring
- send ports, configuring
- send ports, filters
- managing [send ports], filters
ms.assetid: ad13ca8e-bb1d-4449-8163-49dd9d5d92f8
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7845b6189f86054ba9661ea450575a2dcfe47953
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-filters-for-a-send-port"></a><span data-ttu-id="5e409-102">如何設定傳送埠的篩選</span><span class="sxs-lookup"><span data-stu-id="5e409-102">How to Configure Filters for a Send Port</span></span>
<span data-ttu-id="5e409-103">本主題說明如何使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台來設定傳送埠的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="5e409-103">This topic describes how to use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to configure filters for a send port.</span></span> <span data-ttu-id="5e409-104">您可以使用篩選來建立簡單的傳訊或以內容為基礎的路由 (Content-Based Routing，CBR) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5e409-104">You can use filters to create simple messaging or content-based routing (CBR) applications.</span></span> <span data-ttu-id="5e409-105">篩選會設定訊息屬性或欄位的條件，以決定哪些訊息要路由至傳送埠。</span><span class="sxs-lookup"><span data-stu-id="5e409-105">A filter sets conditions for message properties or fields that determine which messages are routed to the send port.</span></span> <span data-ttu-id="5e409-106">篩選不會篩選協調流程路由至傳送埠的訊息。</span><span class="sxs-lookup"><span data-stu-id="5e409-106">A filter does not filter the messages that an orchestration routes to the send port.</span></span>  
  
 <span data-ttu-id="5e409-107">您可以使用運算子，建立一個或多個由訊息屬性、運算子以及依屬性驗證的值所組成的篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="5e409-107">You can create one or more filter expressions, which consist of a message property, an operator, and a value that is validated against the property by using the operator.</span></span>  
  
 <span data-ttu-id="5e409-108">例如，您可能建立如下的運算式：</span><span class="sxs-lookup"><span data-stu-id="5e409-108">For example, you might create an expression like the following:</span></span>  
  
 <span data-ttu-id="5e409-109">MSMQ.MsgID = 1</span><span class="sxs-lookup"><span data-stu-id="5e409-109">MSMQ.MsgID = 1</span></span>  
  
 <span data-ttu-id="5e409-110">依照這個篩選條件，傳送埠群組將只能訂閱 MSMQ 訊息識別碼為 1 的訊息。</span><span class="sxs-lookup"><span data-stu-id="5e409-110">With this filter, the send port group would only subscribe to messages having an MSMQ message ID of 1.</span></span>  
  
 <span data-ttu-id="5e409-111">您可以建立額外的運算式，並指定這些運算式與其他運算式之間有 AND 或 OR 關係，例如：</span><span class="sxs-lookup"><span data-stu-id="5e409-111">You can create additional expressions and specify that they have an AND or OR relationship with other expressions, for example:</span></span>  
  
 <span data-ttu-id="5e409-112">MSMQ.MsgID = 1 OR</span><span class="sxs-lookup"><span data-stu-id="5e409-112">MSMQ.MsgID = 1 OR</span></span>  
  
 <span data-ttu-id="5e409-113">SMTP.From = MyServer</span><span class="sxs-lookup"><span data-stu-id="5e409-113">SMTP.From = MyServer</span></span>  
  
 <span data-ttu-id="5e409-114">在此例中，傳送埠群組將會訂閱 MSMQ 訊息識別碼為 1 的或從名為 MyServer 的 SMTP 伺服器所傳送的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="5e409-114">In this case, the send port group would subscribe to all messages that have either an MSMQ message ID of 1 or that have been sent from the SMTP server named MyServer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e409-115">如果您在一個使用其他應用程式中之屬性結構描述的應用程式內建立傳送埠的篩選，然後再將此應用程式匯入至新的 BizTalk 群組，那麼您在安裝及啟動應用程式時，將不會收到結構描述遺失的警告，並且篩選功能也無法運作。</span><span class="sxs-lookup"><span data-stu-id="5e409-115">If you create a filter for a send port in one application that uses a property schema in another application, and then import the first application into a new BizTalk group, you will not receive a warning that the schema is missing, and filtering will not function when the application is installed and started.</span></span> <span data-ttu-id="5e409-116">在安裝沒有包含結構描述的應用程式之前，您可以先匯入包含結構描述的應用程式來修正問題。</span><span class="sxs-lookup"><span data-stu-id="5e409-116">You can correct the problem by importing the application that contains the schema before you install the application that does not contain the schema.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e409-117">應用程式開發人員可以使用此主題中的程序，在開發程序中設定傳送埠的篩選。</span><span class="sxs-lookup"><span data-stu-id="5e409-117">The application developer can configure filters for a send port during the development process by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5e409-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="5e409-118">Prerequisites</span></span>  
 <span data-ttu-id="5e409-119">若要執行這個主題中的程序，您必須使用「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="5e409-119">To perform the procedure in this topic, you must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span> <span data-ttu-id="5e409-120">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="5e409-120">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-filters-for-a-send-port"></a><span data-ttu-id="5e409-121">設定傳送埠的篩選</span><span class="sxs-lookup"><span data-stu-id="5e409-121">To configure filters for a send port</span></span>  
  
1.  <span data-ttu-id="5e409-122">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="5e409-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="5e409-123">在主控台樹狀結構中，展開您要為其設定傳送埠篩選的 BizTalk 群組與 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5e409-123">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure send port filters.</span></span>  
  
3.  <span data-ttu-id="5e409-124">展開**傳送埠**，以滑鼠右鍵按一下傳送埠，按一下**屬性**，然後按一下 **篩選**。</span><span class="sxs-lookup"><span data-stu-id="5e409-124">Expand **Send Ports**, right-click the send port, click **Properties**, and then click **Filters**.</span></span>  
  
4.  <span data-ttu-id="5e409-125">下表中所述，設定篩選器，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="5e409-125">Configure filters as described in the following table, and then click **OK**.</span></span>  
  
    |<span data-ttu-id="5e409-126">使用</span><span class="sxs-lookup"><span data-stu-id="5e409-126">Use this</span></span>|<span data-ttu-id="5e409-127">動作</span><span class="sxs-lookup"><span data-stu-id="5e409-127">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="5e409-128">**Delete**</span><span class="sxs-lookup"><span data-stu-id="5e409-128">**Delete**</span></span>|<span data-ttu-id="5e409-129">按一下以刪除選取的篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="5e409-129">Click to delete the selected filter expression.</span></span>|  
    |<span data-ttu-id="5e409-130">**上移**</span><span class="sxs-lookup"><span data-stu-id="5e409-130">**Move Up**</span></span>|<span data-ttu-id="5e409-131">按一下以將篩選條件運算式序列中選取的屬性往上移。</span><span class="sxs-lookup"><span data-stu-id="5e409-131">Click to move the selected property ahead in the filter expression sequence.</span></span>|  
    |<span data-ttu-id="5e409-132">**下移**</span><span class="sxs-lookup"><span data-stu-id="5e409-132">**Move Down**</span></span>|<span data-ttu-id="5e409-133">按一下以將篩選條件運算式序列中選取的屬性往下移。</span><span class="sxs-lookup"><span data-stu-id="5e409-133">Click to move the selected property down in the filter expression sequence.</span></span>|  
    |<span data-ttu-id="5e409-134">**屬性**</span><span class="sxs-lookup"><span data-stu-id="5e409-134">**Property**</span></span>|<span data-ttu-id="5e409-135">在清單中按一下要在此篩選運算式中使用的訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="5e409-135">In the list, click a message property to use in this filter expression.</span></span>|  
    |<span data-ttu-id="5e409-136">**運算子**</span><span class="sxs-lookup"><span data-stu-id="5e409-136">**Operator**</span></span>|<span data-ttu-id="5e409-137">輸入或選取運算式的運算子。</span><span class="sxs-lookup"><span data-stu-id="5e409-137">Type or select the operator for the expression.</span></span>|  
    |<span data-ttu-id="5e409-138">**值**</span><span class="sxs-lookup"><span data-stu-id="5e409-138">**Value**</span></span>|<span data-ttu-id="5e409-139">輸入值以驗證屬性。</span><span class="sxs-lookup"><span data-stu-id="5e409-139">Type the value to validate against the property.</span></span> <span data-ttu-id="5e409-140">接受的值類型依屬性類型的不同而不同。</span><span class="sxs-lookup"><span data-stu-id="5e409-140">The accepted value type varies according to the type of property.</span></span> <span data-ttu-id="5e409-141">若要查看某個屬性接受的值類型，請將滑鼠停留在該屬性上方。</span><span class="sxs-lookup"><span data-stu-id="5e409-141">To see what type of value is accepted for a property, hover your mouse over the property.</span></span> <span data-ttu-id="5e409-142">可接受的值如下：Int: (Integer) 這必須是整數值。</span><span class="sxs-lookup"><span data-stu-id="5e409-142">Acceptable values are as follows: Int: (Integer) This must be a whole number.</span></span> <span data-ttu-id="5e409-143">String：字元字串。</span><span class="sxs-lookup"><span data-stu-id="5e409-143">String: A character string.</span></span> <span data-ttu-id="5e409-144">dateTime：以 .NET 支援的格式表示的日期和 (或) 時間。</span><span class="sxs-lookup"><span data-stu-id="5e409-144">dateTime: A date and/or time in .NET-supported format.</span></span> <span data-ttu-id="5e409-145">如需有關 .NET 所支援的時間格式詳細資訊，請參閱「.NET Frameworks 說明」中的＜DateTimeFormatInfo 類別＞。</span><span class="sxs-lookup"><span data-stu-id="5e409-145">For more information about .NET-supported time formats, see "DateTimeFormatInfo Class" in .NET Frameworks Help.</span></span>|  
    |<span data-ttu-id="5e409-146">**群組依據**</span><span class="sxs-lookup"><span data-stu-id="5e409-146">**Group by**</span></span>|<span data-ttu-id="5e409-147">選取**和**或**或**來表示這與篩選條件運算式彼此之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="5e409-147">Select **And** or **Or** to indicate the relationship between this and other filter expressions.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e409-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e409-148">See Also</span></span>  
 [<span data-ttu-id="5e409-149">建立和設定傳送埠</span><span class="sxs-lookup"><span data-stu-id="5e409-149">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)