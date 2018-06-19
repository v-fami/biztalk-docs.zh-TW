---
title: 如何還原主要密碼 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b331c9c5-ca90-4a05-b3f6-59db88bf73dc
caps.latest.revision: 3
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 5e640f2762ed9f9cc03a7795062c98a6aa76a59d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "30250946"
---
# <a name="how-to-restore-the-master-secret"></a><span data-ttu-id="b3621-102">如何還原主要密碼</span><span class="sxs-lookup"><span data-stu-id="b3621-102">How to Restore the Master Secret</span></span>
<span data-ttu-id="b3621-103">資料復原程序的一部分，您可能必須還原主要密碼，才能重複使用現有的資料。</span><span class="sxs-lookup"><span data-stu-id="b3621-103">As part of data recovery procedures, you might have to restore the master secret to reuse existing data.</span></span> <span data-ttu-id="b3621-104">若要執行這項工作中，您必須登入主要密碼伺服器使用的是 Windows 系統管理員和單一登入 (SSO) 系統管理員的帳戶。</span><span class="sxs-lookup"><span data-stu-id="b3621-104">To perform this task, you must log on to the master secret server by using an account that is both a Windows administrator and a Single Sign-On (SSO) administrator.</span></span>  
  
### <a name="to-restore-the-master-secret-using-the-mmc-snap-in"></a><span data-ttu-id="b3621-105">若要使用 MMC 嵌入式管理單元還原主要密碼</span><span class="sxs-lookup"><span data-stu-id="b3621-105">To restore the master secret using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="b3621-106">按一下**啟動**，指向 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="b3621-106">Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="b3621-107">在 ENTSSO Microsoft Management Console (MMC) 嵌入式管理單元的範圍窗格中，展開 **企業單一登入**節點。</span><span class="sxs-lookup"><span data-stu-id="b3621-107">In the scope pane of the ENTSSO Microsoft Management Console (MMC) Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="b3621-108">以滑鼠右鍵按一下**系統**，然後按一下 **還原主要密碼**。</span><span class="sxs-lookup"><span data-stu-id="b3621-108">Right-click **System**, and then click **Restore Master Secret**.</span></span>  
  
### <a name="to-restore-the-master-secret-using-the-command-line"></a><span data-ttu-id="b3621-109">使用命令列還原主要密碼</span><span class="sxs-lookup"><span data-stu-id="b3621-109">To restore the master secret using the command line</span></span>  
  
1.  <span data-ttu-id="b3621-110">在**啟動**功能表上，按一下 **程式**，然後按一下 **附屬應用程式**。</span><span class="sxs-lookup"><span data-stu-id="b3621-110">On the **Start** menu, click **Programs**, and then click **Accessories**.</span></span> <span data-ttu-id="b3621-111">以滑鼠右鍵按一下 **命令提示字元**, ，然後按一下  **執行身分...**。</span><span class="sxs-lookup"><span data-stu-id="b3621-111">Right-click **Command Prompt**, and then click **Run As…**.</span></span>  
  
2.  <span data-ttu-id="b3621-112">選取適當的系統管理員，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="b3621-112">Select the appropriate Administrator, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="b3621-113">在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="b3621-113">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="b3621-114">預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="b3621-114">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="b3621-115">型別`ssoconfig –restoresecret <restore file>`，其中*\<還原檔案 >* 是儲存主要密碼的檔案名稱與路徑。</span><span class="sxs-lookup"><span data-stu-id="b3621-115">Type `ssoconfig –restoresecret <restore file>`, where *\<restore file>* is the path and name of the file where the master secret is stored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3621-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3621-116">See Also</span></span>  
 <span data-ttu-id="b3621-117">[如何產生主要密碼](../esso/how-to-generate-the-master-secret.md) </span><span class="sxs-lookup"><span data-stu-id="b3621-117">[How to Generate the Master Secret](../esso/how-to-generate-the-master-secret.md) </span></span>  
 <span data-ttu-id="b3621-118">[如何備份主要密碼](../esso/how-to-back-up-the-master-secret.md) </span><span class="sxs-lookup"><span data-stu-id="b3621-118">[How to Back Up the Master Secret](../esso/how-to-back-up-the-master-secret.md) </span></span>  
 <span data-ttu-id="b3621-119">[主要密碼伺服器](../esso/master-secret-server.md) </span><span class="sxs-lookup"><span data-stu-id="b3621-119">[Master Secret Server](../esso/master-secret-server.md) </span></span>  
 [<span data-ttu-id="b3621-120">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="b3621-120">Managing the Master Secret</span></span>](../esso/managing-the-master-secret.md)