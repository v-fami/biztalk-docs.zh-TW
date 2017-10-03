---
title: "如何設定虛擬目錄 |Microsoft 文件"
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
- applications, verifying for users
- verifying applications for users
ms.assetid: 3da16524-8238-426a-88f8-434be5992e13
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b1461ac2ea0ef9cfee71965fc2cc800d617d1d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-virtual-directory"></a><span data-ttu-id="a1f1d-102">如何設定虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="a1f1d-102">How to Configure the Virtual Directory</span></span>
<span data-ttu-id="a1f1d-103">此主題說明設定虛擬目錄與為使用者驗證應用程式的程序。</span><span class="sxs-lookup"><span data-stu-id="a1f1d-103">This topic describes the procedures for configuring the virtual directory and verifying the application for a user.</span></span>  
  
### <a name="to-configure-the-virtual-directory"></a><span data-ttu-id="a1f1d-104">設定虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="a1f1d-104">To configure the virtual directory</span></span>  
  
1.  <span data-ttu-id="a1f1d-105">在 %systemdrive%，建立設定為虛擬目錄的資料夾。</span><span class="sxs-lookup"><span data-stu-id="a1f1d-105">On the %systemdrive%, create a folder to be configured as a virtual directory.</span></span>  
  
2.  <span data-ttu-id="a1f1d-106">按一下**啟動**，指向 **程式**，按一下**系統管理工具**，然後按一下**網際網路資訊服務 (IIS) 管理員**。</span><span class="sxs-lookup"><span data-stu-id="a1f1d-106">Click **Start**, point to **Programs**, click **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.</span></span>  
  
3.  <span data-ttu-id="a1f1d-107">展開**\<伺服器名稱 >** ，然後展開 **網站**。</span><span class="sxs-lookup"><span data-stu-id="a1f1d-107">Expand **\<server name>** and then expand **Sites**.</span></span>  
  
4.  <span data-ttu-id="a1f1d-108">以滑鼠右鍵按一下**Default Web Site**按一下**新增虛擬目錄**。</span><span class="sxs-lookup"><span data-stu-id="a1f1d-108">Right-click **Default Web Site** and click **Add Virtual Directory**.</span></span>  
  
5.  <span data-ttu-id="a1f1d-109">在**新增虛擬目錄**對話方塊方塊中，輸入別名。</span><span class="sxs-lookup"><span data-stu-id="a1f1d-109">In the **Add Virtual Directory** dialog box, type the alias.</span></span>  
  
6.  <span data-ttu-id="a1f1d-110">輸入步驟 1 中建立之資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="a1f1d-110">Type the path of the folder created in step 1.</span></span> <span data-ttu-id="a1f1d-111">或者，按一下**（...）**瀏覽至資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="a1f1d-111">Alternatively, click **(…)** to browse to the folder location.</span></span>  
  
7.  <span data-ttu-id="a1f1d-112">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a1f1d-112">Click **OK**.</span></span> <span data-ttu-id="a1f1d-113">資料夾會顯示在**Default Web Site**資料夾。</span><span class="sxs-lookup"><span data-stu-id="a1f1d-113">The folder is displayed under the **Default Web Site** folder.</span></span>  
  
8.  <span data-ttu-id="a1f1d-114">以滑鼠右鍵按一下資料夾，然後按一下**轉換成應用程式**。</span><span class="sxs-lookup"><span data-stu-id="a1f1d-114">Right-click the folder and click **Convert to Application**.</span></span>  
  
9. <span data-ttu-id="a1f1d-115">在**新增應用程式**對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="a1f1d-115">In the **Add Application** dialog box, click **OK**.</span></span> <span data-ttu-id="a1f1d-116">資料夾會轉換成應用程式 （您可以看到在圖示 – 從資料夾圖示的網站 圖示以變更）。</span><span class="sxs-lookup"><span data-stu-id="a1f1d-116">The folder is converted to an application (you can see the change in the icon – from a folder icon to the Web site icon).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f1d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1f1d-117">See Also</span></span>  
 [<span data-ttu-id="a1f1d-118">使用單一登入</span><span class="sxs-lookup"><span data-stu-id="a1f1d-118">Using Single Sign-On</span></span>](../core/using-single-sign-on2.md)