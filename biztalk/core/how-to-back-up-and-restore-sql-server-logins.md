---
title: 如何備份和還原 SQL Server 登入 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 847c3a3d-0d97-415b-893e-4ba173085bae
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54fa6a51a27f82add8a96c613e36f5ed7ce88e87
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248550"
---
# <a name="how-to-back-up-and-restore-sql-server-logins"></a><span data-ttu-id="aeba3-102">如何備份和還原 SQL Server 登入</span><span class="sxs-lookup"><span data-stu-id="aeba3-102">How to Back Up and Restore SQL Server Logins</span></span>
<span data-ttu-id="aeba3-103">備份和還原 BizTalk Server 相關聯的 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="aeba3-103">Back up and restore SQL Server logins associated with BizTalk Server.</span></span>  
  
## <a name="biztalk-server-sql-server-security-logins"></a><span data-ttu-id="aeba3-104">BizTalk Server SQL Server 安全性登入</span><span class="sxs-lookup"><span data-stu-id="aeba3-104">BizTalk Server SQL Server Security Logins</span></span>  
 <span data-ttu-id="aeba3-105">下面所列的 SQL Server 安全性登入是 BizTalk Server 相關聯。</span><span class="sxs-lookup"><span data-stu-id="aeba3-105">The SQL Server security logins listed below are associated with BizTalk Server.</span></span> <span data-ttu-id="aeba3-106">您可能與您所建立的 BizTalk Server 應用程式相關聯的其他登入。</span><span class="sxs-lookup"><span data-stu-id="aeba3-106">You may have additional logins associated with the BizTalk Server applications you have created.</span></span> <span data-ttu-id="aeba3-107">您需要備份登入，並將 BizTalk Server 資料庫移到新的伺服器或 SQL Server 的新執行個體時還原它們。</span><span class="sxs-lookup"><span data-stu-id="aeba3-107">You need to back up the logins and restore them when moving the BizTalk Server databases to a new server or new instance of SQL Server.</span></span>  
  
-   <span data-ttu-id="aeba3-108">BizTalk 應用程式使用者</span><span class="sxs-lookup"><span data-stu-id="aeba3-108">BizTalk Application Users</span></span>  
  
-   <span data-ttu-id="aeba3-109">BizTalk 外掛式主控件使用者</span><span class="sxs-lookup"><span data-stu-id="aeba3-109">BizTalk Isolated Host Users</span></span>  
  
-   <span data-ttu-id="aeba3-110">BizTalk Server 系統管理員</span><span class="sxs-lookup"><span data-stu-id="aeba3-110">BizTalk Server Administrators</span></span>  
  
-   <span data-ttu-id="aeba3-111">BizTalk Server 操作員</span><span class="sxs-lookup"><span data-stu-id="aeba3-111">BizTalk Server Operators</span></span>  
  
-   <span data-ttu-id="aeba3-112">SSO 系統管理員</span><span class="sxs-lookup"><span data-stu-id="aeba3-112">SSO Administrators</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="aeba3-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="aeba3-113">Prerequisites</span></span>  
<span data-ttu-id="aeba3-114">您必須是成員**管理員**您備份並還原登入的 SQL Server 上的安全性角色。</span><span class="sxs-lookup"><span data-stu-id="aeba3-114">You must be a member of the **Administrators** security role on the SQL Server where you backup and restore the logins.</span></span>  
  
## <a name="back-up-a-login-using-a-script"></a><span data-ttu-id="aeba3-115">備份使用指令碼的登入</span><span class="sxs-lookup"><span data-stu-id="aeba3-115">Back up a login using a script</span></span>  
  
1.  <span data-ttu-id="aeba3-116">開啟**SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="aeba3-116">Open **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="aeba3-117">展開**安全性**，並展開的清單**登入**。</span><span class="sxs-lookup"><span data-stu-id="aeba3-117">Expand **Security**, and expand the list of **Logins**.</span></span>  
  
3.  <span data-ttu-id="aeba3-118">以滑鼠右鍵按一下您想要建立的備份指令碼，然後選取 登的入**以指令碼登入**。</span><span class="sxs-lookup"><span data-stu-id="aeba3-118">Right-click the login you want to create a backup script for, and then select **Script Login as**.</span></span>  
  
4.  <span data-ttu-id="aeba3-119">選取**CREATE 至**，然後選取其中一個**新增查詢編輯器視窗**，**檔案**，或**剪貼簿**選取指令碼的目的地。</span><span class="sxs-lookup"><span data-stu-id="aeba3-119">Select **CREATE To**, and then select one of **New Query Editor Window**, **File**, or **Clipboard** to select a destination for the script.</span></span> <span data-ttu-id="aeba3-120">通常，目的地是檔案之 **.sql**延伸模組。</span><span class="sxs-lookup"><span data-stu-id="aeba3-120">Typically, the destination is a file with a **.sql** extension.</span></span>  
  
5.  <span data-ttu-id="aeba3-121">重複此程序步驟 3 從每個登入您想要編寫指令碼。</span><span class="sxs-lookup"><span data-stu-id="aeba3-121">Repeat this procedure from Step 3 for each login you want to script.</span></span> <span data-ttu-id="aeba3-122">清單，請參閱 BizTalk Server 的相關登入，以便判斷哪些登入，您需要指令碼。</span><span class="sxs-lookup"><span data-stu-id="aeba3-122">Refer to the list of BizTalk Server related logins to determine which logins you need to script.</span></span>  
  
## <a name="restore-a-login-from-a-script"></a><span data-ttu-id="aeba3-123">從指令碼還原登入</span><span class="sxs-lookup"><span data-stu-id="aeba3-123">Restore a login from a script</span></span>  
  
1.  <span data-ttu-id="aeba3-124">開啟**SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="aeba3-124">Open **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="aeba3-125">在**檔案**功能表上，**開啟**包含已編寫指令碼的登入的檔案。</span><span class="sxs-lookup"><span data-stu-id="aeba3-125">On the **File** menu, **Open** the file containing the scripted login.</span></span>  
  
3.  <span data-ttu-id="aeba3-126">執行建立登入指令碼。</span><span class="sxs-lookup"><span data-stu-id="aeba3-126">Execute the script to create the login.</span></span>