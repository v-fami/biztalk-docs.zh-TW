---
title: "如何驗證訊息的活動狀態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities, verifying status
- PeopleSoft Integration Broker
- verifying message status in PeopleSoft
- messages, verifying status
ms.assetid: b8cee6f9-0f65-4228-a87a-3f3aca6182bf
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 872c1a1fcfcc905caf926c8299f56d49178a8448
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-verify-activity-status-of-a-message"></a><span data-ttu-id="bffc6-102">如何確認訊息的活動狀態</span><span class="sxs-lookup"><span data-stu-id="bffc6-102">How to Verify Activity Status of a Message</span></span>
<span data-ttu-id="bffc6-103">您可以使用 PeopleSoft Integration Broker 建立 PeopleSoft HTTP 主控件和連接埠，讓 PeopleSoft 傳送事件。</span><span class="sxs-lookup"><span data-stu-id="bffc6-103">You use the PeopleSoft Integration Broker to create a PeopleSoft HTTP Host and Port where PeopleSoft sends events.</span></span> <span data-ttu-id="bffc6-104">請依照下列步驟，確定訊息正在作用中，並且已路由傳送。</span><span class="sxs-lookup"><span data-stu-id="bffc6-104">You make sure that the message is active and routed by following these steps.</span></span>  
  
### <a name="to-verify-that-a-message-is-active-and-routed-correctly"></a><span data-ttu-id="bffc6-105">若要確認訊息正在作用中並已正確路由傳送</span><span class="sxs-lookup"><span data-stu-id="bffc6-105">To verify that a Message is active and routed correctly</span></span>  
  
1.  <span data-ttu-id="bffc6-106">按一下**啟動**，指向**程式**，指向  **PeopleSoft 應用程式名稱**，然後選取**應用程式設計工具**。</span><span class="sxs-lookup"><span data-stu-id="bffc6-106">Click **Start**, point to **Programs**, point to **PeopleSoft Application Name**, and then select **Application Designer**.</span></span>  
  
2.  <span data-ttu-id="bffc6-107">上**PeopleSoft sign-on**畫面上，輸入**使用者識別碼**和**密碼**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="bffc6-107">On the **PeopleSoft Sign-on** screen, enter the **User ID** and **Password**, and then click **OK**.</span></span>  
  
     ![](../core/media/psadapter-24-task-userpass.gif "PSAdapter_24_Task_UserPass")  
  
     ![](../core/media/psadapter-25-task-emptydesigner.gif "PSAdapter_25_Task_EmptyDesigner")  
  
3.  <span data-ttu-id="bffc6-108">在 應用程式設計工具中上,**檔案**功能表上，指向**開啟**，然後選取**訊息**。</span><span class="sxs-lookup"><span data-stu-id="bffc6-108">In the Application Designer, on the **File** menu, point to **Open**, and then select **Message**.</span></span>  
  
     ![](../core/media/psadapter-26-task-filemessage.gif "PSAdapter_26_Task_FileMessage")  
  
4.  <span data-ttu-id="bffc6-109">在**開啟定義**畫面上，在**名稱**欄位中，輸入`LOCATION_SYNC`，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="bffc6-109">In the **Open Definition** screen, in the **Name** field, enter `LOCATION_SYNC`, and then click **Open**.</span></span>  
  
     ![](../core/media/psadapter-27-task-locationsync.gif "PSAdapter_27_Task_LocationSync")  
  
5.  <span data-ttu-id="bffc6-110">在**定義符合選取準則**區段中，按兩下**LOCATION_SYNC**檢視內容的訊息。</span><span class="sxs-lookup"><span data-stu-id="bffc6-110">In the **Definitions matching selection criteria** section, double-click the **LOCATION_SYNC** message to view the properties.</span></span>  
  
     ![](../core/media/psadapter-28-task-locationproperties.gif "PSAdapter_28_Task_LocationProperties")  
  
6.  <span data-ttu-id="bffc6-111">在 應用程式設計工具中，以滑鼠右鍵按一下**LOCATION_TBL**，然後選取**訊息屬性**。</span><span class="sxs-lookup"><span data-stu-id="bffc6-111">In the Application Designer, right-click **LOCATION_TBL**, and select **Message Properties**.</span></span>  
  
     ![](../core/media/psadapter-29-task-loctionmenu.gif "PSAdapter_29_Task_LoctionMenu")  
  
7.  <span data-ttu-id="bffc6-112">在**訊息屬性**畫面上，按一下**使用** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bffc6-112">On the **Message Properties** screen, click the **Use** tab.</span></span>  
  
     <span data-ttu-id="bffc6-113">確認下列項目，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="bffc6-113">Verify the following, and then click **OK**.</span></span>  
  
    1.  <span data-ttu-id="bffc6-114">**訊息：** Active</span><span class="sxs-lookup"><span data-stu-id="bffc6-114">**Message:** Active</span></span>  
  
    2.  <span data-ttu-id="bffc6-115">**訊息通道：** ENTERPRISE_SETUP</span><span class="sxs-lookup"><span data-stu-id="bffc6-115">**Message Channel:** ENTERPRISE_SETUP</span></span>  
  
    3.  <span data-ttu-id="bffc6-116">**預設版本：** VERSION_1</span><span class="sxs-lookup"><span data-stu-id="bffc6-116">**Default Version:** VERSION_1</span></span>  
  
     ![](../core/media/psadapter-30-task-messageuse.gif "PSAdapter_30_Task_MessageUse")  
  
8.  <span data-ttu-id="bffc6-117">結束 [Application Designer]。</span><span class="sxs-lookup"><span data-stu-id="bffc6-117">Exit the Application Designer.</span></span>  
  
     <span data-ttu-id="bffc6-118">這會確定 PeopleSoft 中該訊息處於作用中狀態、使用 VERSION_1，並且流程會經由 ENTERPRISE_SETUP 通道。</span><span class="sxs-lookup"><span data-stu-id="bffc6-118">This makes sure that the Message is in an active state, uses VERSION_1, and flows through the ENTERPRISE_SETUP channel in PeopleSoft.</span></span>  
  
9. <span data-ttu-id="bffc6-119">設定 Integration.Gateway.properties 檔案，與 PeopleSoft 應用程式通訊。</span><span class="sxs-lookup"><span data-stu-id="bffc6-119">Configure the Integration.Gateway.properties file to communicate with the PeopleSoft application.</span></span>  
  
     <span data-ttu-id="bffc6-120">確認已設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="bffc6-120">Verify that the following properties are set:</span></span>  
  
    -   <span data-ttu-id="bffc6-121">**ig.isc.serverurl:** //server:9000</span><span class="sxs-lookup"><span data-stu-id="bffc6-121">**ig.isc.serverurl:** //server:9000</span></span>  
  
    -   <span data-ttu-id="bffc6-122">**ig.isc.userid:** PS 的識別碼</span><span class="sxs-lookup"><span data-stu-id="bffc6-122">**ig.isc.userid:** ID for PS</span></span>  
  
    -   <span data-ttu-id="bffc6-123">**ig.isc.password:** PS 的密碼</span><span class="sxs-lookup"><span data-stu-id="bffc6-123">**ig.isc.password:** Password for PS</span></span>  
  
    -   <span data-ttu-id="bffc6-124">**ig.isc.toolsrel:**特定版本</span><span class="sxs-lookup"><span data-stu-id="bffc6-124">**ig.isc.toolsrel:** Specific Release</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bffc6-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bffc6-125">See Also</span></span>  
 [<span data-ttu-id="bffc6-126">建立 PeopleSoft HTTP 主控件和連接埠</span><span class="sxs-lookup"><span data-stu-id="bffc6-126">Creating a PeopleSoft HTTP Host and Port</span></span>](../core/creating-a-peoplesoft-http-host-and-port.md)