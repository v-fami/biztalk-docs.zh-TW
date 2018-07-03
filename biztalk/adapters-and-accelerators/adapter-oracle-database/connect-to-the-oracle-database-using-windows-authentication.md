---
title: 連接到 Oracle 資料庫使用 Windows 驗證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73b42a1b-1105-4278-bf8a-62cf0cffb08f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c984a62275c58f50b0c360a5f46040a6022b459
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007751"
---
# <a name="connect-to-the-oracle-database-using-windows-authentication"></a><span data-ttu-id="0e852-102">連接到 Oracle 資料庫使用 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="0e852-102">Connect to the Oracle Database Using Windows Authentication</span></span>
<span data-ttu-id="0e852-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]可讓配接器用戶端使用 Windows 驗證來建立與 Oracle 資料庫的連線。</span><span class="sxs-lookup"><span data-stu-id="0e852-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] enables adapter clients to use Windows Authentication to establish a connection with the Oracle database.</span></span> <span data-ttu-id="0e852-104">若要使用 Windows 驗證時，配接器用戶端必須指定"/"的使用者名稱與保留密碼空白。</span><span class="sxs-lookup"><span data-stu-id="0e852-104">To use Windows Authentication, the adapter clients must specify “/” for user name and leave the password blank.</span></span> <span data-ttu-id="0e852-105">如需有關如何連接到 Oracle 資料庫使用 Windows 驗證的詳細資訊，請參閱 <<c0> [ 連接到 Oracle 資料庫，在 Visual Studio 中使用 取用配接器服務](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md)。</span><span class="sxs-lookup"><span data-stu-id="0e852-105">For more information about connecting to the Oracle database using Windows Authentication, see [Connect to Oracle Database in Visual Studio using the Consume Adapter Service](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md).</span></span>  
  
 <span data-ttu-id="0e852-106">若要啟用使用 Windows 驗證來連接到 Oracle 資料庫配接器用戶端，您必須執行的 Oracle 資料庫的電腦上執行下列工作。</span><span class="sxs-lookup"><span data-stu-id="0e852-106">To enable adapter clients to use Windows Authentication to connect to an Oracle database, you must perform the following tasks on the computer running the Oracle database.</span></span>  
  
1. <span data-ttu-id="0e852-107">請確定`sqlnet.ora`上的用戶端和伺服器，可在檔案`ORACLE_BASE\ORACLE_HOME\network\admin\sqlnet.ora`，具有下列項目：</span><span class="sxs-lookup"><span data-stu-id="0e852-107">Make sure that the `sqlnet.ora` file on both the client and the server, available under `ORACLE_BASE\ORACLE_HOME\network\admin\sqlnet.ora`, has the following entry:</span></span>  
  
   ```  
   SQLNET.AUTHENTICATION_SERVICES= (NTS)  
   ```  
  
2. <span data-ttu-id="0e852-108">以 sysdba 身分連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0e852-108">Connect to the Oracle database as SYSDBA.</span></span>  
  
3. <span data-ttu-id="0e852-109">建立為 Oracle 資料庫中的外部使用者的 Windows 使用者。</span><span class="sxs-lookup"><span data-stu-id="0e852-109">Create the Windows user as an external user in the Oracle database.</span></span> <span data-ttu-id="0e852-110">請注意，使用者名稱必須是大寫。</span><span class="sxs-lookup"><span data-stu-id="0e852-110">Note that the user name must be in upper case.</span></span>  
  
   ```  
   CREATE USER “OPS$<DOMAIN_NAME>\<USER_NAME\>” IDENTIFIED EXTERNALLY;  
   ```  
  
4. <span data-ttu-id="0e852-111">授與權限給使用者。</span><span class="sxs-lookup"><span data-stu-id="0e852-111">Grant privileges to the user.</span></span>  
  
   ```  
   GRANT CONNECT,RESOURCE TO “OPS$<DOMAIN_NAME>\<USER_NAME\>”;  
   ```  
  
5. <span data-ttu-id="0e852-112">若要啟用新建立的使用者，登入使用 Windows 驗證，來存取 Oracle 資料庫成品中，您可以變更使用者的結構描述 SCOTT 結構描述。</span><span class="sxs-lookup"><span data-stu-id="0e852-112">To enable the newly created user, logging in using Windows Authentication, to access the Oracle database artifacts, you can change the user’s schema to the SCOTT schema.</span></span> <span data-ttu-id="0e852-113">您可以將下列 SQL 命令加入 scott 變更使用者的預設結構描述，當使用者登入的登入指令碼。</span><span class="sxs-lookup"><span data-stu-id="0e852-113">You can add the following SQL command to the logon script that changes the user’s default schema to SCOTT when the user logs on.</span></span>  
  
   ```  
   alter session set current_schema=SCOTT;  
   ```  
  
6. <span data-ttu-id="0e852-114">即使您變更使用者的結構描述為 SCOTT 結構描述時，您將仍然無法查看同時瀏覽並產生中繼資料所使用的 Oracle 資料庫成品[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0e852-114">Even though you changed the schema of the user to the SCOTT schema, you will still not be able to see the Oracle database artifacts while browsing and generating metadata using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="0e852-115">這是因為新建立的使用者沒有 SCOTT 結構描述的權限。</span><span class="sxs-lookup"><span data-stu-id="0e852-115">This is because the newly created user does not have permissions for the SCOTT schema.</span></span> <span data-ttu-id="0e852-116">請確定您提供給新建立的使用者，SCOTT 結構描述權限。</span><span class="sxs-lookup"><span data-stu-id="0e852-116">Make sure you provided permission for the SCOTT schema to the newly created user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e852-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e852-117">See Also</span></span>  
 <span data-ttu-id="0e852-118">[設定 Oracle 用戶端，Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="0e852-118">[Configure the Oracle Client for the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md) </span></span>  
[<span data-ttu-id="0e852-119">建立 Oracle 資料庫的連線</span><span class="sxs-lookup"><span data-stu-id="0e852-119">Create a connection to the Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)