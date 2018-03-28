---
title: 如何還原主要密碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [Master Secret server], restoring
- Master Secret server, restoring
- restoring, Master Secret server
ms.assetid: 68e133c5-4591-4d76-9a3b-c9564ff1aa60
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9241c8d9c5f6e41f47199211d0215c16526951d6
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-restore-the-master-secret"></a><span data-ttu-id="604f5-102">如何還原主要密碼</span><span class="sxs-lookup"><span data-stu-id="604f5-102">How to Restore the Master Secret</span></span>
<span data-ttu-id="604f5-103">您必須還原主要密碼，才能重新使用現有的資料，這是資料回復程序的一部分。</span><span class="sxs-lookup"><span data-stu-id="604f5-103">As part of data recovery procedures, you may need to restore the master secret to re-use existing data.</span></span> <span data-ttu-id="604f5-104">要執行此作業，您必須使用同時是 Windows 管理員和 SSO 系統管理員的帳戶，登入主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="604f5-104">In order to perform this task, you must log on to the master secret server with an account that is both a Windows administrator and an SSO administrator.</span></span>  
  
### <a name="to-restore-the-master-secret-using-the-mmc-snap-in"></a><span data-ttu-id="604f5-105">若要使用 MMC 嵌入式管理單元還原主要密碼</span><span class="sxs-lookup"><span data-stu-id="604f5-105">To restore the master secret using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="604f5-106">在 **[開始]** 功能表上，依序按一下 **[所有程式]**及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。</span><span class="sxs-lookup"><span data-stu-id="604f5-106">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="604f5-107">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="604f5-107">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="604f5-108">以滑鼠右鍵按一下 **系統**, ，然後按一下  **還原密碼**。</span><span class="sxs-lookup"><span data-stu-id="604f5-108">Right-click **System**, and then click **Restore Secret**.</span></span>  
  
### <a name="to-restore-the-master-secret-using-the-command-line"></a><span data-ttu-id="604f5-109">使用命令列還原主要密碼</span><span class="sxs-lookup"><span data-stu-id="604f5-109">To restore the master secret using the command line</span></span>  
  
1.  <span data-ttu-id="604f5-110">在 **啟動**  功能表上，按一下  **所有程式**, ，然後按一下  **附屬應用程式**。</span><span class="sxs-lookup"><span data-stu-id="604f5-110">On the **Start** menu, click **All Programs**, and then click **Accessories**.</span></span> <span data-ttu-id="604f5-111">以滑鼠右鍵按一下 **命令提示字元**, ，然後按一下  **執行身分...**。</span><span class="sxs-lookup"><span data-stu-id="604f5-111">Right-click **Command Prompt**, and then click **Run As…**.</span></span>  
  
2.  <span data-ttu-id="604f5-112">選取適當的系統管理員，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="604f5-112">Select the appropriate Administrator, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="604f5-113">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="604f5-113">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="604f5-114">預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="604f5-114">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="604f5-115">型別**ssoconfig – restoreSecret\<還原檔案\>**，其中**\<還原檔案\>**是主要密碼所在的檔案名稱與路徑儲存。</span><span class="sxs-lookup"><span data-stu-id="604f5-115">Type **ssoconfig –restoreSecret \<restore file\>**, where **\<restore file\>** is the path and name of the file where the master secret is stored.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="604f5-116">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="604f5-116">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="604f5-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="604f5-117">See Also</span></span>  
 <span data-ttu-id="604f5-118">[如何產生主要密碼](../core/how-to-generate-the-master-secret.md) </span><span class="sxs-lookup"><span data-stu-id="604f5-118">[How to Generate the Master Secret](../core/how-to-generate-the-master-secret.md) </span></span>  
 <span data-ttu-id="604f5-119">[如何備份主要密碼](../core/how-to-back-up-the-master-secret.md) </span><span class="sxs-lookup"><span data-stu-id="604f5-119">[How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md) </span></span>  
 <span data-ttu-id="604f5-120">[主要密碼伺服器](../core/master-secret-server.md) </span><span class="sxs-lookup"><span data-stu-id="604f5-120">[Master Secret Server](../core/master-secret-server.md) </span></span>  
 [<span data-ttu-id="604f5-121">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="604f5-121">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)