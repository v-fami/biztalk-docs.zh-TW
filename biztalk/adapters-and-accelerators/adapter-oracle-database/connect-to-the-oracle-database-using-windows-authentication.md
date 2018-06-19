---
title: 連接到 Oracle 資料庫使用 Windows 驗證 |Microsoft 文件
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
ms.openlocfilehash: 840435ce334863a4b76e6ac7da0d8dd64e7d4937
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25961940"
---
# <a name="connect-to-the-oracle-database-using-windows-authentication"></a><span data-ttu-id="f8d60-102">連接到 Oracle 資料庫使用 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="f8d60-102">Connect to the Oracle Database Using Windows Authentication</span></span>
<span data-ttu-id="f8d60-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]可讓配接器用戶端使用 Windows 驗證來與 Oracle 資料庫建立連線。</span><span class="sxs-lookup"><span data-stu-id="f8d60-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] enables adapter clients to use Windows Authentication to establish a connection with the Oracle database.</span></span> <span data-ttu-id="f8d60-104">若要使用 Windows 驗證，配接器用戶端必須指定"/"的使用者名稱與保留密碼空白。</span><span class="sxs-lookup"><span data-stu-id="f8d60-104">To use Windows Authentication, the adapter clients must specify “/” for user name and leave the password blank.</span></span> <span data-ttu-id="f8d60-105">如需有關如何連接到 Oracle 資料庫使用 Windows 驗證的詳細資訊，請參閱[連接到 Oracle 資料庫，在 Visual Studio 中使用 取用配接器服務](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md)。</span><span class="sxs-lookup"><span data-stu-id="f8d60-105">For more information about connecting to the Oracle database using Windows Authentication, see [Connect to Oracle Database in Visual Studio using the Consume Adapter Service](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md).</span></span>  
  
 <span data-ttu-id="f8d60-106">若要讓配接器用戶端使用 Windows 驗證來連接到 Oracle 資料庫，您必須執行 Oracle 資料庫的電腦上執行下列工作。</span><span class="sxs-lookup"><span data-stu-id="f8d60-106">To enable adapter clients to use Windows Authentication to connect to an Oracle database, you must perform the following tasks on the computer running the Oracle database.</span></span>  
  
1.  <span data-ttu-id="f8d60-107">請確定`sqlnet.ora`底下可用的伺服器和用戶端上的檔案`ORACLE_BASE\ORACLE_HOME\network\admin\sqlnet.ora`，有下列項目：</span><span class="sxs-lookup"><span data-stu-id="f8d60-107">Make sure that the `sqlnet.ora` file on both the client and the server, available under `ORACLE_BASE\ORACLE_HOME\network\admin\sqlnet.ora`, has the following entry:</span></span>  
  
    ```  
    SQLNET.AUTHENTICATION_SERVICES= (NTS)  
    ```  
  
2.  <span data-ttu-id="f8d60-108">連接到 Oracle 資料庫，以 SYSDBA。</span><span class="sxs-lookup"><span data-stu-id="f8d60-108">Connect to the Oracle database as SYSDBA.</span></span>  
  
3.  <span data-ttu-id="f8d60-109">Oracle 資料庫中的外部使用者的身分建立的 Windows 使用者。</span><span class="sxs-lookup"><span data-stu-id="f8d60-109">Create the Windows user as an external user in the Oracle database.</span></span> <span data-ttu-id="f8d60-110">請注意，使用者名稱必須以大寫。</span><span class="sxs-lookup"><span data-stu-id="f8d60-110">Note that the user name must be in upper case.</span></span>  
  
    ```  
    CREATE USER “OPS$<DOMAIN_NAME>\<USER_NAME\>” IDENTIFIED EXTERNALLY;  
    ```  
  
4.  <span data-ttu-id="f8d60-111">授與權限給使用者。</span><span class="sxs-lookup"><span data-stu-id="f8d60-111">Grant privileges to the user.</span></span>  
  
    ```  
    GRANT CONNECT,RESOURCE TO “OPS$<DOMAIN_NAME>\<USER_NAME\>”;  
    ```  
  
5.  <span data-ttu-id="f8d60-112">若要啟用新建立的使用者，登入使用 Windows 驗證來存取 Oracle 資料庫成品中，您可以變更使用者的結構描述 SCOTT 結構描述。</span><span class="sxs-lookup"><span data-stu-id="f8d60-112">To enable the newly created user, logging in using Windows Authentication, to access the Oracle database artifacts, you can change the user’s schema to the SCOTT schema.</span></span> <span data-ttu-id="f8d60-113">您可以將下列 SQL 命令加入與 SCOTT 變更使用者的預設結構描述，當使用者登入的登入指令碼。</span><span class="sxs-lookup"><span data-stu-id="f8d60-113">You can add the following SQL command to the logon script that changes the user’s default schema to SCOTT when the user logs on.</span></span>  
  
    ```  
    alter session set current_schema=SCOTT;  
    ```  
  
6.  <span data-ttu-id="f8d60-114">即使您變更使用者的結構描述為 SCOTT 結構描述時，您將仍然無法瀏覽及產生中繼資料使用時，請參閱 Oracle 資料庫成品[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f8d60-114">Even though you changed the schema of the user to the SCOTT schema, you will still not be able to see the Oracle database artifacts while browsing and generating metadata using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="f8d60-115">這是因為新建立的使用者沒有 SCOTT 結構描述的權限。</span><span class="sxs-lookup"><span data-stu-id="f8d60-115">This is because the newly created user does not have permissions for the SCOTT schema.</span></span> <span data-ttu-id="f8d60-116">請確定您提供 SCOTT 結構描述權限給新建立的使用者。</span><span class="sxs-lookup"><span data-stu-id="f8d60-116">Make sure you provided permission for the SCOTT schema to the newly created user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8d60-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="f8d60-117">See Also</span></span>  
 <span data-ttu-id="f8d60-118">[設定 Oracle 資料庫配接器的 Oracle 用戶端](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="f8d60-118">[Configure the Oracle Client for the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md) </span></span>  
[<span data-ttu-id="f8d60-119">建立 Oracle 資料庫的連線</span><span class="sxs-lookup"><span data-stu-id="f8d60-119">Create a connection to the Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)