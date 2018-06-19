---
title: 自動登記和核准程序 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dfd3e72e-e28b-4ee3-bc4a-89ef3f64e6d5
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 333e1403ffd45f80a98d3eb17f5d3aa2b63c7798
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295622"
---
# <a name="the-auto-enlist-and-approval-process"></a><span data-ttu-id="4a96d-102">自動登記和核准程序</span><span class="sxs-lookup"><span data-stu-id="4a96d-102">The Auto-Enlist and Approval Process</span></span>
<span data-ttu-id="4a96d-103">您可以設定 ESB 管理入口網站，若要發行 Microsoft BizTalk Server 端點有兩種：</span><span class="sxs-lookup"><span data-stu-id="4a96d-103">You can configure the ESB Management Portal to publish Microsoft BizTalk Server endpoints in two ways:</span></span>  
  
-   <span data-ttu-id="4a96d-104">它可以透過其中系統管理員必須確認及核准註冊要求核准程序來設定。</span><span class="sxs-lookup"><span data-stu-id="4a96d-104">It can be configured through the approval process, where an administrator must confirm and approve the registration request.</span></span>  
  
-   <span data-ttu-id="4a96d-105">它可以設定使用自動發行，其中入口網站會自動發佈要求到通用描述、 探索與整合 (UDDI) 登錄而不需要系統管理員介入。</span><span class="sxs-lookup"><span data-stu-id="4a96d-105">It can be configured by using auto-publish, where the portal automatically publishes the request into the Universal Description, Discovery, and Integration (UDDI) registry without requiring administrator intervention.</span></span>  
  
 <span data-ttu-id="4a96d-106">下列兩個程序中所述，您也可以指定入口網站中，UDDI 整合功能的幾個其他的設定。</span><span class="sxs-lookup"><span data-stu-id="4a96d-106">You can also specify several other settings of the UDDI Integration features of the portal, as described in the following two procedures.</span></span>  
  
### <a name="to-configure-auto-approval-and-publishing-in-the-esb-management-portal"></a><span data-ttu-id="4a96d-107">若要在 ESB 管理入口網站中設定自動核准及發行</span><span class="sxs-lookup"><span data-stu-id="4a96d-107">To configure auto-approval and publishing in the ESB Management Portal</span></span>  
  
1.  <span data-ttu-id="4a96d-108">請確定您在入口網站使用的 BizTalk Server 系統管理員群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="4a96d-108">Make sure that you log on to the portal using an account that is a member of the BizTalk Server Administrators group.</span></span>  
  
2.  <span data-ttu-id="4a96d-109">指向**Admin**入口網站的主功能表上的索引標籤，然後按一下 [**登錄設定**開啟入口網站[登錄設定] 頁面](../esb-toolkit/registry-settings-page.md)。</span><span class="sxs-lookup"><span data-stu-id="4a96d-109">Point to the **Admin** tab on the portal main menu, and then click **Registry Settings** to open the portal [Registry Settings Page](../esb-toolkit/registry-settings-page.md).</span></span>  
  
3.  <span data-ttu-id="4a96d-110">若要啟用自動核准及發行，在頂端的文字方塊中輸入 UDDI 伺服器的 URL **UDDI 詳細資料**的頁面上，然後選取區段**使其自動發佈**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="4a96d-110">To enable auto-approval and publishing, type the URL of your UDDI server in the text box at the top of the **UDDI Details** section of the page, and then select the **AutoPublish** check box.</span></span>  
  
4.  <span data-ttu-id="4a96d-111">若要停用自動核准及發行，請清除**自動發行**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="4a96d-111">To disable auto-approval and publishing, clear the **Auto Publish** check box.</span></span>  
  
### <a name="to-configure-e-mail-and-registry-settings-for-the-uddi-integration-features"></a><span data-ttu-id="4a96d-112">若要設定電子郵件和登錄設定 UDDI 整合功能</span><span class="sxs-lookup"><span data-stu-id="4a96d-112">To configure e-mail and registry settings for the UDDI Integration features</span></span>  
  
1.  <span data-ttu-id="4a96d-113">請確定您在入口網站使用的 BizTalk Server 系統管理員帳戶的群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="4a96d-113">Make sure that you log on to the portal using an account that is a member of the BizTalk Server Administrators account group.</span></span>  
  
2.  <span data-ttu-id="4a96d-114">指向**Admin**入口網站的主功能表上的索引標籤，然後按一下 [**登錄設定**開啟入口網站[登錄設定] 頁面](../esb-toolkit/registry-settings-page.md)。</span><span class="sxs-lookup"><span data-stu-id="4a96d-114">Point to the **Admin** tab on the portal main menu, and then click **Registry Settings** to open the portal [Registry Settings Page](../esb-toolkit/registry-settings-page.md).</span></span>  
  
3.  <span data-ttu-id="4a96d-115">編輯程式頂端的文字方塊中的 UDDI 伺服器的 URL **UDDI 詳細資料**頁面區段。</span><span class="sxs-lookup"><span data-stu-id="4a96d-115">Edit the URL of your UDDI server in the text box at the top of the **UDDI Details** section of the page.</span></span> <span data-ttu-id="4a96d-116">預設 「 UDDI 服務是本機 Microsoft UDDI 服務。</span><span class="sxs-lookup"><span data-stu-id="4a96d-116">The default UDDI service is the local Microsoft UDDI service.</span></span>  
  
4.  <span data-ttu-id="4a96d-117">選取**匿名**核取方塊，如果您想要在入口網站中存取的 UDDI 伺服器時，使用匿名驗證。</span><span class="sxs-lookup"><span data-stu-id="4a96d-117">Select the **Anonymous** check box if you want the portal to use anonymous authentication when accessing the UDDI server.</span></span>  
  
5.  <span data-ttu-id="4a96d-118">如果您想要在入口網站以電子郵件時 UDDI 發行通知您要求正在等待核准，請選取**啟用通知**中核取方塊**電子郵件通知**頁面區段。</span><span class="sxs-lookup"><span data-stu-id="4a96d-118">If you want the portal to notify you by e-mail when a UDDI publishing request is awaiting approval, select the **Notification Enabled** check box in the **Email Notification** section of the page.</span></span> <span data-ttu-id="4a96d-119">然後輸入您的電子郵件伺服器、 傳遞電子郵件地址、 適當的 「 寄件者 」 電子郵件地址、 郵件主旨和訊息內文的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4a96d-119">Then enter the details of your e-mail server, the address for delivery of e-mail messages, an appropriate "from" e-mail address, the message subject, and the message body.</span></span>  
  
6.  <span data-ttu-id="4a96d-120">輸入系統管理員的連絡人名稱和電子郵件地址 UDDI 的回條要求中的電子郵件訊息**預設設定**頁面區段。</span><span class="sxs-lookup"><span data-stu-id="4a96d-120">Enter the administrator contact name and e-mail address for the receipt of UDDI request e-mail messages in the **Default Settings** section of the page.</span></span>  
  
### <a name="to-approve-or-decline-a-registration-request-as-an-administrator"></a><span data-ttu-id="4a96d-121">若要核准或拒絕登錄要求，以系統管理員</span><span class="sxs-lookup"><span data-stu-id="4a96d-121">To approve or decline a registration request as an administrator</span></span>  
  
1.  <span data-ttu-id="4a96d-122">請確定您登入入口網站使用的 BizTalk Server 系統管理員群組成員的帳戶。</span><span class="sxs-lookup"><span data-stu-id="4a96d-122">Make sure that you log into the portal using an account that is a member of the BizTalk Server Administrators group.</span></span>  
  
2.  <span data-ttu-id="4a96d-123">指向**登錄**入口網站的主功能表上的索引標籤，然後按一下 **管理暫止要求**開啟入口網站[管理擱置的要求頁面](../esb-toolkit/manage-pending-requests-page.md)。</span><span class="sxs-lookup"><span data-stu-id="4a96d-123">Point to the **Registry** tab on the portal main menu, and then click **Manage Pending Requests** to open the portal [Manage Pending Requests Page](../esb-toolkit/manage-pending-requests-page.md).</span></span>  
  
3.  <span data-ttu-id="4a96d-124">若要核准的暫止要求，請按一下**核准**旁該要求清單中的圖示 （核取記號）。</span><span class="sxs-lookup"><span data-stu-id="4a96d-124">To approve a pending request, click the **Approve** icon (the check mark) next to that request in the list.</span></span>  
  
4.  <span data-ttu-id="4a96d-125">若要拒絕擱置要求時，按一下**拒絕**旁該要求清單中的圖示 （交叉標記）。</span><span class="sxs-lookup"><span data-stu-id="4a96d-125">To reject a pending request, click the **Reject** icon (the cross mark) next to that request in the list.</span></span>  
  
5.  <span data-ttu-id="4a96d-126">若要檢視擱置中要求的詳細資訊，請按一下**檢視詳細資料**圖示 （放大鏡） 若要開啟[登錄詳細資料頁面](../esb-toolkit/registry-details-page.md)。</span><span class="sxs-lookup"><span data-stu-id="4a96d-126">To view details of a pending request, click the **View Details** icon (the magnifying glass) to open the [Registry Details Page](../esb-toolkit/registry-details-page.md).</span></span> <span data-ttu-id="4a96d-127">您可以發佈、 刪除或更新此頁面中的要求。</span><span class="sxs-lookup"><span data-stu-id="4a96d-127">You can publish, delete, or update the request in this page.</span></span>  
  
6.  <span data-ttu-id="4a96d-128">若要檢閱要求的狀態，並查看先前的要求清單按一下**檢視要求記錄**連結。</span><span class="sxs-lookup"><span data-stu-id="4a96d-128">To review the requests status and see a list of previous requests, click the **View Request History** link.</span></span>