---
title: 如何驗證訊息的活動狀態 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- activities, verifying status
- PeopleSoft Integration Broker
- verifying message status in PeopleSoft
- messages, verifying status
ms.assetid: b8cee6f9-0f65-4228-a87a-3f3aca6182bf
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8af3a77b9bb169e394571444c7eb7e3984f7f7c3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013039"
---
# <a name="how-to-verify-activity-status-of-a-message"></a><span data-ttu-id="60069-102">如何確認訊息的活動狀態</span><span class="sxs-lookup"><span data-stu-id="60069-102">How to Verify Activity Status of a Message</span></span>
<span data-ttu-id="60069-103">您可以使用 PeopleSoft Integration Broker 建立 PeopleSoft HTTP 主控件和連接埠，讓 PeopleSoft 傳送事件。</span><span class="sxs-lookup"><span data-stu-id="60069-103">You use the PeopleSoft Integration Broker to create a PeopleSoft HTTP Host and Port where PeopleSoft sends events.</span></span> <span data-ttu-id="60069-104">請依照下列步驟，確定訊息正在作用中，並且已路由傳送。</span><span class="sxs-lookup"><span data-stu-id="60069-104">You make sure that the message is active and routed by following these steps.</span></span>  
  
### <a name="to-verify-that-a-message-is-active-and-routed-correctly"></a><span data-ttu-id="60069-105">若要確認訊息正在作用中並已正確路由傳送</span><span class="sxs-lookup"><span data-stu-id="60069-105">To verify that a Message is active and routed correctly</span></span>  
  
1. <span data-ttu-id="60069-106">按一下 **開始**，指向**程式**，指向**PeopleSoft 應用程式名稱**，然後選取**應用程式設計工具**。</span><span class="sxs-lookup"><span data-stu-id="60069-106">Click **Start**, point to **Programs**, point to **PeopleSoft Application Name**, and then select **Application Designer**.</span></span>  
  
2. <span data-ttu-id="60069-107">上**PeopleSoft 登入**畫面上，輸入**使用者識別碼**並**密碼**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="60069-107">On the **PeopleSoft Sign-on** screen, enter the **User ID** and **Password**, and then click **OK**.</span></span>  
  
    <span data-ttu-id="60069-108">![](../core/media/psadapter-24-task-userpass.gif "PSAdapter_24_Task_UserPass")</span><span class="sxs-lookup"><span data-stu-id="60069-108">![](../core/media/psadapter-24-task-userpass.gif "PSAdapter_24_Task_UserPass")</span></span>  
  
    <span data-ttu-id="60069-109">![](../core/media/psadapter-25-task-emptydesigner.gif "PSAdapter_25_Task_EmptyDesigner")</span><span class="sxs-lookup"><span data-stu-id="60069-109">![](../core/media/psadapter-25-task-emptydesigner.gif "PSAdapter_25_Task_EmptyDesigner")</span></span>  
  
3. <span data-ttu-id="60069-110">在 應用程式設計工具中，在**檔案**功能表上，指向**開啟**，然後選取**訊息**。</span><span class="sxs-lookup"><span data-stu-id="60069-110">In the Application Designer, on the **File** menu, point to **Open**, and then select **Message**.</span></span>  
  
    <span data-ttu-id="60069-111">![](../core/media/psadapter-26-task-filemessage.gif "PSAdapter_26_Task_FileMessage")</span><span class="sxs-lookup"><span data-stu-id="60069-111">![](../core/media/psadapter-26-task-filemessage.gif "PSAdapter_26_Task_FileMessage")</span></span>  
  
4. <span data-ttu-id="60069-112">在 **開啟定義**畫面上，在**名稱**欄位中，輸入`LOCATION_SYNC`，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="60069-112">In the **Open Definition** screen, in the **Name** field, enter `LOCATION_SYNC`, and then click **Open**.</span></span>  
  
    <span data-ttu-id="60069-113">![](../core/media/psadapter-27-task-locationsync.gif "PSAdapter_27_Task_LocationSync")</span><span class="sxs-lookup"><span data-stu-id="60069-113">![](../core/media/psadapter-27-task-locationsync.gif "PSAdapter_27_Task_LocationSync")</span></span>  
  
5. <span data-ttu-id="60069-114">在 **定義符合選取準則**區段中，按兩下**LOCATION_SYNC**來檢視屬性的訊息。</span><span class="sxs-lookup"><span data-stu-id="60069-114">In the **Definitions matching selection criteria** section, double-click the **LOCATION_SYNC** message to view the properties.</span></span>  
  
    <span data-ttu-id="60069-115">![](../core/media/psadapter-28-task-locationproperties.gif "PSAdapter_28_Task_LocationProperties")</span><span class="sxs-lookup"><span data-stu-id="60069-115">![](../core/media/psadapter-28-task-locationproperties.gif "PSAdapter_28_Task_LocationProperties")</span></span>  
  
6. <span data-ttu-id="60069-116">在 應用程式設計工具中，以滑鼠右鍵按一下**location_tbl**，然後選取**訊息屬性**。</span><span class="sxs-lookup"><span data-stu-id="60069-116">In the Application Designer, right-click **LOCATION_TBL**, and select **Message Properties**.</span></span>  
  
    <span data-ttu-id="60069-117">![](../core/media/psadapter-29-task-loctionmenu.gif "PSAdapter_29_Task_LoctionMenu")</span><span class="sxs-lookup"><span data-stu-id="60069-117">![](../core/media/psadapter-29-task-loctionmenu.gif "PSAdapter_29_Task_LoctionMenu")</span></span>  
  
7. <span data-ttu-id="60069-118">在 [**訊息屬性**畫面上，按一下**使用**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="60069-118">On the **Message Properties** screen, click the **Use** tab.</span></span>  
  
    <span data-ttu-id="60069-119">確認下列項目，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="60069-119">Verify the following, and then click **OK**.</span></span>  
  
   1. <span data-ttu-id="60069-120">**訊息：** Active</span><span class="sxs-lookup"><span data-stu-id="60069-120">**Message:** Active</span></span>  
  
   2. <span data-ttu-id="60069-121">**訊息通道：** ENTERPRISE_SETUP</span><span class="sxs-lookup"><span data-stu-id="60069-121">**Message Channel:** ENTERPRISE_SETUP</span></span>  
  
   3. <span data-ttu-id="60069-122">**預設版本：** VERSION_1</span><span class="sxs-lookup"><span data-stu-id="60069-122">**Default Version:** VERSION_1</span></span>  
  
      <span data-ttu-id="60069-123">![](../core/media/psadapter-30-task-messageuse.gif "PSAdapter_30_Task_MessageUse")</span><span class="sxs-lookup"><span data-stu-id="60069-123">![](../core/media/psadapter-30-task-messageuse.gif "PSAdapter_30_Task_MessageUse")</span></span>  
  
8. <span data-ttu-id="60069-124">結束 [Application Designer]。</span><span class="sxs-lookup"><span data-stu-id="60069-124">Exit the Application Designer.</span></span>  
  
    <span data-ttu-id="60069-125">這會確定 PeopleSoft 中該訊息處於作用中狀態、使用 VERSION_1，並且流程會經由 ENTERPRISE_SETUP 通道。</span><span class="sxs-lookup"><span data-stu-id="60069-125">This makes sure that the Message is in an active state, uses VERSION_1, and flows through the ENTERPRISE_SETUP channel in PeopleSoft.</span></span>  
  
9. <span data-ttu-id="60069-126">設定 Integration.Gateway.properties 檔案，與 PeopleSoft 應用程式通訊。</span><span class="sxs-lookup"><span data-stu-id="60069-126">Configure the Integration.Gateway.properties file to communicate with the PeopleSoft application.</span></span>  
  
     <span data-ttu-id="60069-127">確認已設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="60069-127">Verify that the following properties are set:</span></span>  
  
    -   <span data-ttu-id="60069-128">**ig.isc.serverurl:** //server:9000</span><span class="sxs-lookup"><span data-stu-id="60069-128">**ig.isc.serverurl:** //server:9000</span></span>  
  
    -   <span data-ttu-id="60069-129">**ig.isc.userid:** PS 的識別碼</span><span class="sxs-lookup"><span data-stu-id="60069-129">**ig.isc.userid:** ID for PS</span></span>  
  
    -   <span data-ttu-id="60069-130">**ig.isc.password:** PS 的密碼</span><span class="sxs-lookup"><span data-stu-id="60069-130">**ig.isc.password:** Password for PS</span></span>  
  
    -   <span data-ttu-id="60069-131">**ig.isc.toolsrel:** 特定版本</span><span class="sxs-lookup"><span data-stu-id="60069-131">**ig.isc.toolsrel:** Specific Release</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60069-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60069-132">See Also</span></span>  
 [<span data-ttu-id="60069-133">建立 PeopleSoft HTTP 主控件和連接埠</span><span class="sxs-lookup"><span data-stu-id="60069-133">Creating a PeopleSoft HTTP Host and Port</span></span>](../core/creating-a-peoplesoft-http-host-and-port.md)