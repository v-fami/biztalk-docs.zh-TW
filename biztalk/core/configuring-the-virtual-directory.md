---
title: "設定虛擬目錄 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- virtual directory, configuring
- configuring virtual directory
ms.assetid: 548e3bee-66bc-424c-895d-e8672a3d6301
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a879fe776956c290fb895c7f0feb39b6088e268
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-virtual-directory"></a><span data-ttu-id="5dfdf-102">設定虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="5dfdf-102">Configuring the Virtual Directory</span></span>
<span data-ttu-id="5dfdf-103">此主題說明設定虛擬目錄與為使用者驗證應用程式的程序。</span><span class="sxs-lookup"><span data-stu-id="5dfdf-103">This topic shows the procedures for configuring the virtual directory and verifying the application for a user.</span></span>  
  
## <a name="configuring-the-directory"></a><span data-ttu-id="5dfdf-104">設定目錄</span><span class="sxs-lookup"><span data-stu-id="5dfdf-104">Configuring the Directory</span></span>  
  
#### <a name="to-configure-the-virtual-directory"></a><span data-ttu-id="5dfdf-105">設定虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="5dfdf-105">To configure the virtual directory</span></span>  
  
1.  <span data-ttu-id="5dfdf-106">在 %systemdrive%，建立設定為虛擬目錄的資料夾。</span><span class="sxs-lookup"><span data-stu-id="5dfdf-106">On the %systemdrive%, create a folder to be configured as a virtual directory.</span></span>  
  
2.  <span data-ttu-id="5dfdf-107">按一下**啟動**，指向 **程式**，按一下**系統管理工具**，然後按一下**網際網路資訊服務 (IIS) 管理員**。</span><span class="sxs-lookup"><span data-stu-id="5dfdf-107">Click **Start**, point to **Programs**, click **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.</span></span>  
  
3.  <span data-ttu-id="5dfdf-108">展開**\<伺服器名稱 >** ，然後展開 **網站**。</span><span class="sxs-lookup"><span data-stu-id="5dfdf-108">Expand **\<server name>** and then expand **Sites**.</span></span>  
  
4.  <span data-ttu-id="5dfdf-109">以滑鼠右鍵按一下**Default Web Site**按一下**新增虛擬目錄**。</span><span class="sxs-lookup"><span data-stu-id="5dfdf-109">Right-click **Default Web Site** and click **Add Virtual Directory**.</span></span>  
  
5.  <span data-ttu-id="5dfdf-110">在**新增虛擬目錄**對話方塊方塊中，輸入別名。</span><span class="sxs-lookup"><span data-stu-id="5dfdf-110">In the **Add Virtual Directory** dialog box, type the alias.</span></span>  
  
6.  <span data-ttu-id="5dfdf-111">輸入步驟 1 中建立之資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="5dfdf-111">Type the path of the folder created in step 1.</span></span> <span data-ttu-id="5dfdf-112">或者，按一下**（...）**瀏覽至資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="5dfdf-112">Alternatively, click **(…)** to browse to the folder location.</span></span>  
  
7.  <span data-ttu-id="5dfdf-113">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="5dfdf-113">Click **OK**.</span></span> <span data-ttu-id="5dfdf-114">資料夾會顯示在**Default Web Site**資料夾。</span><span class="sxs-lookup"><span data-stu-id="5dfdf-114">The folder is displayed under the **Default Web Site** folder.</span></span>  
  
8.  <span data-ttu-id="5dfdf-115">以滑鼠右鍵按一下資料夾，然後按一下**轉換成應用程式**。</span><span class="sxs-lookup"><span data-stu-id="5dfdf-115">Right-click the folder and click **Convert to Application**.</span></span>  
  
9. <span data-ttu-id="5dfdf-116">在**新增應用程式**對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="5dfdf-116">In the **Add Application** dialog box, click **OK**.</span></span> <span data-ttu-id="5dfdf-117">資料夾會轉換成應用程式 （您可以看到在圖示 – 從資料夾圖示的網站 圖示以變更）。</span><span class="sxs-lookup"><span data-stu-id="5dfdf-117">The folder is converted to an application (you can see the change in the icon – from a folder icon to the Web site icon).</span></span>  
  
## <a name="verifying-an-application-for-a-user"></a><span data-ttu-id="5dfdf-118">為使用者驗證應用程式</span><span class="sxs-lookup"><span data-stu-id="5dfdf-118">Verifying an Application for a User</span></span>  
 <span data-ttu-id="5dfdf-119">網際網路資訊服務 (IIS) 應用程式會以高隔離等級執行；因此，您必須使用下列程序，確認應用程式可在 BizTalk Server Isolated Host Users 群組中之使用者的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="5dfdf-119">Internet Information Services (IIS) applications run in high isolation; therefore, you must verify that the application can run in the context of a user in the BizTalk Server Isolated Host Users group by using the following procedure.</span></span>  
  
#### <a name="to-verify-an-application-for-a-user"></a><span data-ttu-id="5dfdf-120">為使用者驗證應用程式</span><span class="sxs-lookup"><span data-stu-id="5dfdf-120">To verify an application for a user</span></span>  
  
1.  <span data-ttu-id="5dfdf-121">在控制台中開啟**系統管理工具**，然後按一下 **元件服務**。</span><span class="sxs-lookup"><span data-stu-id="5dfdf-121">In Control Panel, open **Administrative Tools**, and then click **Component Services**.</span></span>  
  
2.  <span data-ttu-id="5dfdf-122">瀏覽至 COM + 應用程式中**元件服務**。</span><span class="sxs-lookup"><span data-stu-id="5dfdf-122">Navigate to the COM+ application in **Component Services**.</span></span>  
  
3.  <span data-ttu-id="5dfdf-123">以滑鼠右鍵按一下 COM + 應用程式，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="5dfdf-123">Right-click the COM+ application, and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="5dfdf-124">按一下**識別**及變更此 COM + 應用程式執行 BizTalk Server 群組的成員使用者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="5dfdf-124">Click **Identify** and change the identity under which this COM+ application runs to a user that is a member of a BizTalk Server group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dfdf-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5dfdf-125">See Also</span></span>  
 [<span data-ttu-id="5dfdf-126">使用單一登入</span><span class="sxs-lookup"><span data-stu-id="5dfdf-126">Using Single Sign-On</span></span>](../core/using-single-sign-on3.md)