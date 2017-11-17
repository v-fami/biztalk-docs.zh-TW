---
title: "將憑證加入至伺服器的憑證存放區 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, adding to certificates store
- certificates store
ms.assetid: 075cfae8-dce7-46f7-9539-796f03229ea2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94661568108e5a1cc05140a97c933fb8d00e3c67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adding-certificates-to-the-certificates-store-on-the-server"></a><span data-ttu-id="3e450-102">將憑證新增到伺服器的憑證存放區</span><span class="sxs-lookup"><span data-stu-id="3e450-102">Adding Certificates to the Certificates Store on the Server</span></span>
<span data-ttu-id="3e450-103">使用下列步驟，將憑證加入至伺服器電腦上的憑證 （本機電腦） 存放區的 [其他人] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3e450-103">Use the following steps to add certificates to the Other People folder in the Certificates (Local Computer) store on the server computer.</span></span>  
  
### <a name="to-add-certificates-to-the-certificate-store"></a><span data-ttu-id="3e450-104">將憑證加入至憑證存放區</span><span class="sxs-lookup"><span data-stu-id="3e450-104">To add certificates to the certificate store</span></span>  
  
1.  <span data-ttu-id="3e450-105">按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk Accelerator for SWIFT**，然後按一下  **BizTalk Accelerator for SWIFT 管理主控台**。</span><span class="sxs-lookup"><span data-stu-id="3e450-105">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Accelerator for SWIFT**, and then click **BizTalk Accelerator for SWIFT Management Console**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3e450-106">如果您仍然可以從上一個程序 （新增憑證至用戶端的憑證存放區），您可以將它用於此程序開啟 MMC 視窗。</span><span class="sxs-lookup"><span data-stu-id="3e450-106">If you still have the MMC window open from the previous procedure (Adding Certificates to the Certificates Store on the Client), you can use it for this procedure.</span></span>  
  
2.  <span data-ttu-id="3e450-107">在 [系統管理主控台] 視窗中，依序展開**憑證 （本機電腦）**資料夾，然後展開**其他人**。</span><span class="sxs-lookup"><span data-stu-id="3e450-107">In the Administration Console window, expand the **Certificates (Local Computer)** folder, and then expand **Other People**.</span></span>  
  
3.  <span data-ttu-id="3e450-108">以滑鼠右鍵按一下**憑證**，指向 **所有工作**，然後按一下 **匯入**。</span><span class="sxs-lookup"><span data-stu-id="3e450-108">Right-click **Certificates**, point to **All Tasks**, and then click **Import**.</span></span>  
  
4.  <span data-ttu-id="3e450-109">在歡迎使用 憑證匯入精靈 頁面中，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="3e450-109">On the Welcome to the Certificate Import Wizard page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="3e450-110">在要匯入] 頁面的檔案，按一下 [**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="3e450-110">On the File to Import page, click **Browse**.</span></span>  
  
6.  <span data-ttu-id="3e450-111">在開啟的對話方塊中，移至您的憑證，選取的儲存位置的檔案位置**所有檔案**如**檔案類型**，選取您想要匯入，然後按一下 憑證**開啟**。</span><span class="sxs-lookup"><span data-stu-id="3e450-111">In the Open dialog box, move to the file location where you have saved your certificate, select **All Files** for **Files of Type**, select the certificate that you want to import, and then click **Open**.</span></span>  
  
7.  <span data-ttu-id="3e450-112">在要匯入] 頁面的檔案，按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="3e450-112">On the File to Import page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="3e450-113">在憑證存放區 頁面上，確認**將所有憑證都放入以下的存放區**已選取，確認**其他人**會顯示在**憑證存放區**方塊，然後再按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="3e450-113">On the Certificate Store page, verify that **Place all certificates in the following store** is selected, verify that **Other People** is displayed in the **Certificate Store** box, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="3e450-114">在 完成憑證匯入精靈 頁面上，按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="3e450-114">On the Completing the Certificate Import Wizard page, click **Finish**.</span></span>  
  
10. <span data-ttu-id="3e450-115">在表示成功的匯入憑證匯入精靈 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3e450-115">In the Certificate Import Wizard dialog box indicating a successful import, click **OK**.</span></span>  
  
11. <span data-ttu-id="3e450-116">重複步驟 3 到 10，您會使用訊息修復和新送出的所有其他憑證。</span><span class="sxs-lookup"><span data-stu-id="3e450-116">Repeat steps 3 through 10 for all other certificates that you will use in message repair and new submission.</span></span>