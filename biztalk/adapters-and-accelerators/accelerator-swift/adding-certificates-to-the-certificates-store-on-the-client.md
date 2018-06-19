---
title: 正在將憑證加入至用戶端的憑證存放區 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates, adding to certificates store
- certificates store
ms.assetid: 9e2722ee-dd6f-4b14-9796-2f2157e8cad2
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48a2e01fa60eccc8a6a0f06f4cf1f9fafb3f982b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209494"
---
# <a name="adding-certificates-to-the-certificates-store-on-the-client"></a><span data-ttu-id="9f23c-102">將憑證新增至用戶端的憑證存放區</span><span class="sxs-lookup"><span data-stu-id="9f23c-102">Adding Certificates to the Certificates Store on the Client</span></span>
<span data-ttu-id="9f23c-103">使用下列步驟，將憑證加入至每個用戶端電腦上的憑證存放區的個人資料夾。</span><span class="sxs-lookup"><span data-stu-id="9f23c-103">Use the following steps to add certificates to the Personal folder in the certificates store on each client computer.</span></span> <span data-ttu-id="9f23c-104">必須將憑證加入至 憑證-目前使用者存放區中的個人資料夾。</span><span class="sxs-lookup"><span data-stu-id="9f23c-104">The certificates must be added to the Personal folder in the Certificates - Current User store.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9f23c-105">如果您的憑證不透過散發企業信任憑證授權單位，您必須匯入到用戶端電腦上的憑證授權單位的根憑證。</span><span class="sxs-lookup"><span data-stu-id="9f23c-105">If your certificates are not distributed via an enterprise trusted Certification Authority, you must import the Certification Authority's root certificate onto the client computer(s).</span></span> <span data-ttu-id="9f23c-106">否則，您的個人憑證將無法運作。</span><span class="sxs-lookup"><span data-stu-id="9f23c-106">Otherwise, your personal certificates will not work.</span></span> <span data-ttu-id="9f23c-107">憑證授權單位的憑證匯入到信任的根憑證授權單位資料夾中的 憑證 （本機電腦） 節點。</span><span class="sxs-lookup"><span data-stu-id="9f23c-107">Import the Certification Authority's certificate into the Trusted Root Certification Authorities folder in the Certificates (Local Computer) node.</span></span>  
  
### <a name="to-add-certificates-to-the-certificate-store"></a><span data-ttu-id="9f23c-108">將憑證加入至憑證存放區</span><span class="sxs-lookup"><span data-stu-id="9f23c-108">To add certificates to the certificate store</span></span>  
  
1.  <span data-ttu-id="9f23c-109">按一下 **[開始]**，然後按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-109">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="9f23c-110">輸入**mmc**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-110">Enter **mmc**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="9f23c-111">在 Console1 對話方塊中，按一下**檔案**，然後按一下 **新增/移除嵌入式管理單元**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-111">In the Console1 dialog box, click **File**, and then click **Add/Remove Snap-in**.</span></span>  
  
3.  <span data-ttu-id="9f23c-112">在 [新增/移除嵌入式管理單元] 對話方塊中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-112">In the Add/Remove Snap-in dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="9f23c-113">在 新增獨立嵌入式管理單元 對話方塊中，按一下**憑證**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-113">In the Add Standalone Snap-in dialog box, click **Certificates**, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="9f23c-114">在 憑證嵌入式管理單元對話方塊中，按一下**我的使用者帳戶**，然後按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-114">In the Certificates snap-in dialog box, click **My user account**, and then click **Finish**.</span></span>  
  
6.  <span data-ttu-id="9f23c-115">在 新增獨立嵌入式管理單元 對話方塊中，按一下**憑證**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-115">In the Add Standalone Snap-in dialog box, click **Certificates**, and then click **Add**.</span></span>  
  
7.  <span data-ttu-id="9f23c-116">在 憑證嵌入式管理單元對話方塊中，按一下**電腦帳戶**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-116">In the Certificates snap-in dialog box, click **Computer account**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="9f23c-117">在 [選取電腦] 對話方塊中，請確定**本機電腦**已選取，然後按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-117">In the Select Computer dialog box, make sure **Local computer** is selected, and then click **Finish**.</span></span>  
  
9. <span data-ttu-id="9f23c-118">在 [新增獨立嵌入式管理單元] 對話方塊中，按一下**關閉**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-118">In the Add Standalone Snap-in dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="9f23c-119">在 [新增/移除嵌入式管理單元] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-119">In the Add/Remove Snap-in dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="9f23c-120">在**主控台根目錄**窗格中的 [Console1] 對話方塊中，展開**憑證-目前使用者**資料夾。</span><span class="sxs-lookup"><span data-stu-id="9f23c-120">In the **Console Root** pane of the Console1 dialog box, expand the **Certificates - Current User** folders.</span></span>  
  
12. <span data-ttu-id="9f23c-121">在下**憑證-目前使用者**，依序展開**個人**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-121">Under **Certificates - Current User**, expand **Personal**.</span></span>  
  
13. <span data-ttu-id="9f23c-122">以滑鼠右鍵按一下**憑證**，指向 **所有工作**，然後按一下 **匯入**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-122">Right-click **Certificates**, point to **All Tasks**, and then click **Import**.</span></span>  
  
14. <span data-ttu-id="9f23c-123">在歡迎使用 憑證匯入精靈 頁面中，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-123">On the Welcome to the Certificate Import Wizard page, click **Next**.</span></span>  
  
15. <span data-ttu-id="9f23c-124">在要匯入] 頁面的檔案，按一下 [**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-124">On the File to Import page, click **Browse**.</span></span>  
  
16. <span data-ttu-id="9f23c-125">在開啟的對話方塊中，移至您的憑證，選取的儲存位置的檔案位置**所有檔案**如**檔案類型**，選取您想要匯入，然後按一下 憑證**開啟**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-125">In the Open dialog box, move to the file location where you have saved your certificate, select **All Files** for **Files of Type**, select the certificate that you want to import, and then click **Open**.</span></span>  
  
17. <span data-ttu-id="9f23c-126">在要匯入] 頁面的檔案，按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-126">On the File to Import page, click **Next**.</span></span>  
  
18. <span data-ttu-id="9f23c-127">在憑證存放區 頁面上，確認**將所有憑證都放入以下的存放區**已選取，確認**個人**會顯示在**憑證存放區**方塊，然後再按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-127">On the Certificate Store page, verify that **Place all certificates in the following store** is selected, verify that **Personal** is displayed in the **Certificate Store** box, and then click **Next**.</span></span>  
  
19. <span data-ttu-id="9f23c-128">在 完成憑證匯入精靈 頁面上，按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-128">On the Completing the Certificate Import Wizard page, click **Finish**.</span></span>  
  
20. <span data-ttu-id="9f23c-129">在表示成功的匯入憑證匯入精靈 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="9f23c-129">In the Certificate Import Wizard dialog box indicating a successful import, click **OK**.</span></span>  
  
21. <span data-ttu-id="9f23c-130">重複步驟 13 到 20，您會使用訊息修復和新送出的所有其他憑證。</span><span class="sxs-lookup"><span data-stu-id="9f23c-130">Repeat steps 13 through 20 for all other certificates that you will use in message repair and new submission.</span></span>