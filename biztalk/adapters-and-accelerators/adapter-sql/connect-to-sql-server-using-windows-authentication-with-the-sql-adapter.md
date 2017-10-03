---
title: "連接到 SQL Server 使用 Windows 驗證搭配 SQL 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45c54b2a-e056-496f-9f10-f19b6a3ca1a6
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db7d0cbe07155d09085091d995b524b3058c0bf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-sql-server-using-windows-authentication-with-the-sql-adapter"></a><span data-ttu-id="cf0a7-102">連接到 SQL Server 使用 Windows 驗證搭配 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="cf0a7-102">Connect to SQL Server using Windows Authentication with the SQL adapter</span></span>
<span data-ttu-id="cf0a7-103">[!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)]可讓配接器用戶端使用 Windows 驗證來建立與 SQL Server 的連線。</span><span class="sxs-lookup"><span data-stu-id="cf0a7-103">The [!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)] enables adapter clients to use Windows Authentication to establish a connection with SQL Server.</span></span> <span data-ttu-id="cf0a7-104">若要使用 Windows 驗證，配接器用戶端必須輸入空的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="cf0a7-104">To use Windows Authentication, adapter clients must enter an empty user name and password.</span></span> 

<span data-ttu-id="cf0a7-105">若要連接到 SQL Server 使用 Visual Studio 中的 Windows 驗證，請參閱[連接到 SQL Server 使用配接器服務增益集所使用的 Visual Studio 中](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md)。</span><span class="sxs-lookup"><span data-stu-id="cf0a7-105">To connect to SQL Server using Windows Authentication within Visual Studio, see [Connect to SQL Server in Visual Studio using the Consume Adapter Service Add-in](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md).</span></span>  
  
 <span data-ttu-id="cf0a7-106">若要讓配接器用戶端使用 Windows 驗證來連接到 SQL Server，請執行 SQL Server 的電腦上的使用者啟用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="cf0a7-106">To enable adapter clients to use Windows Authentication to connect to SQL Server, enable Windows Authentication for the user on the computer running SQL Server.</span></span>  

> [!TIP]
> <span data-ttu-id="cf0a7-107">如果您的 SQL Server 上未安裝 SQL Server Management Studio，您可以[下載 SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)，並安裝它。</span><span class="sxs-lookup"><span data-stu-id="cf0a7-107">If SQL Server Management Studio is not installed on your SQL Server, you can [Download SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms), and install it.</span></span> 
 
## <a name="add-the-user-in-sql-server"></a><span data-ttu-id="cf0a7-108">SQL Server 中新增使用者</span><span class="sxs-lookup"><span data-stu-id="cf0a7-108">Add the user in SQL Server</span></span>  
  
1.  <span data-ttu-id="cf0a7-109">開啟 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="cf0a7-109">Open SQL Server Management Studio.</span></span> <span data-ttu-id="cf0a7-110">在**連接到伺服器**，選取**Database Engine**，輸入您的 SQL**伺服器名稱**，並輸入管理員認證以連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="cf0a7-110">In **Connect to Server**, select **Database Engine**, enter your SQL **Server name**, and enter administrator credentials to connect to the server.</span></span>  

    <span data-ttu-id="cf0a7-111">選取 [連接]。</span><span class="sxs-lookup"><span data-stu-id="cf0a7-111">Select **Connect**.</span></span>
  
2.  <span data-ttu-id="cf0a7-112">在**物件總管] 中**，依序展開 [SQL Server**安全性**，以滑鼠右鍵按一下**登入**，然後選取**新登入**。</span><span class="sxs-lookup"><span data-stu-id="cf0a7-112">In **Object Explorer**, expand the SQL Server, expand **Security**, right-click **Logins**, and then select **New Login**.</span></span>  
  
3.  <span data-ttu-id="cf0a7-113">如**登入名稱**，輸入中的 Windows 使用者名稱`domain\username`格式。</span><span class="sxs-lookup"><span data-stu-id="cf0a7-113">For the **Login name**, enter the Windows user name in the `domain\username` format.</span></span>  

    > [!NOTE]
    >* <span data-ttu-id="cf0a7-114">當此配接器使用 BizTalk 中，您輸入時，則登入名稱是主控件執行個體帳戶的身分識別。</span><span class="sxs-lookup"><span data-stu-id="cf0a7-114">When using this adapter with BizTalk, then the login name you enter, is the identity of the host instance account.</span></span>  
    >
    >* <span data-ttu-id="cf0a7-115">.NET 程式碼中使用此配接器，當您輸入時，登入名稱是該處理序的識別。</span><span class="sxs-lookup"><span data-stu-id="cf0a7-115">When using this adapter in .NET code, then the login name you enter, is the identity for that process.</span></span>
  
4.  <span data-ttu-id="cf0a7-116">選取**使用者對應**（左的窗格）。</span><span class="sxs-lookup"><span data-stu-id="cf0a7-116">Select **User Mapping** (left pane).</span></span> <span data-ttu-id="cf0a7-117">選取要與使用者相關聯的資料庫。</span><span class="sxs-lookup"><span data-stu-id="cf0a7-117">Select a database to associate with the user.</span></span> <span data-ttu-id="cf0a7-118">在一般 BizTalk 使用者應該與下列資料庫相關聯：</span><span class="sxs-lookup"><span data-stu-id="cf0a7-118">A typical BizTalk user should be associated with the following databases:</span></span> 

* <span data-ttu-id="cf0a7-119">BizTalkDTADb</span><span class="sxs-lookup"><span data-stu-id="cf0a7-119">BizTalkDTADb</span></span>
* <span data-ttu-id="cf0a7-120">BizTalkMgmtDb</span><span class="sxs-lookup"><span data-stu-id="cf0a7-120">BizTalkMgmtDb</span></span>
* <span data-ttu-id="cf0a7-121">BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="cf0a7-121">BizTalkMsgBoxDb</span></span>
* <span data-ttu-id="cf0a7-122">BTAHL7</span><span class="sxs-lookup"><span data-stu-id="cf0a7-122">BTAHL7</span></span>
* <span data-ttu-id="cf0a7-123">SSODB</span><span class="sxs-lookup"><span data-stu-id="cf0a7-123">SSODB</span></span>

5. <span data-ttu-id="cf0a7-124">在**資料庫角色成員資格，對**方塊中，選取**db_owner**所有 BizTalk 資料庫。</span><span class="sxs-lookup"><span data-stu-id="cf0a7-124">In the **Database role membership for** box, select **db_owner** for all the BizTalk databases.</span></span>  

    > [!NOTE]
    > <span data-ttu-id="cf0a7-125">[伺服器和 SQL Server 中的資料庫角色](https://msdn.microsoft.com/library/bb669065.aspx)的角色提供良好的資訊。</span><span class="sxs-lookup"><span data-stu-id="cf0a7-125">[Server and Database Roles in SQL Server](https://msdn.microsoft.com/library/bb669065.aspx) provides good info on the roles.</span></span> 
  
6.  <span data-ttu-id="cf0a7-126">選取 [確定] 儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="cf0a7-126">Select **OK** to save your changes.</span></span>
  
 <span data-ttu-id="cf0a7-127">加入使用者之後，使用者可以連接和驗證至 SQL Server 使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]、 記錄以空白的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="cf0a7-127">After you have added the user, the user can connect and authenticate to SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], logging in with a blank username and password.</span></span>  



## <a name="see-also"></a><span data-ttu-id="cf0a7-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf0a7-128">See Also</span></span>  
 [<span data-ttu-id="cf0a7-129">建立 SQL Server 的連接</span><span class="sxs-lookup"><span data-stu-id="cf0a7-129">Create a connection to SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/create-a-connection-to-sql-server.md)