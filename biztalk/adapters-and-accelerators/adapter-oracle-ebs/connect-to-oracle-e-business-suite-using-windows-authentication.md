---
title: 連接到使用 Windows 驗證的 Oracle E-business Suite |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0937dfd9-4a94-4d65-a42c-3c5019eefde2
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9563f754fd096efb4ab39192f1a8a21a7e6b2207
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009103"
---
# <a name="connect-to-oracle-e-business-suite-using-windows-authentication"></a><span data-ttu-id="297db-102">連接到 Oracle E-business Suite 使用 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="297db-102">Connect to Oracle E-Business Suite using Windows Authentication</span></span>
<span data-ttu-id="297db-103">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可讓配接器用戶端使用 Windows 驗證來建立與 Oracle E-business Suite 的連線。</span><span class="sxs-lookup"><span data-stu-id="297db-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] enables adapter clients to use Windows Authentication to establish a connection with the Oracle E-Business Suite.</span></span> <span data-ttu-id="297db-104">若要使用 Windows 驗證配接器用戶端必須指定"/"的使用者名稱，並將密碼保持空白。</span><span class="sxs-lookup"><span data-stu-id="297db-104">To use Windows Authentication adapter clients must specify a “/” for user name and leave the password blank.</span></span> <span data-ttu-id="297db-105">如需有關如何連接到 Oracle E-business Suite 使用 Windows 驗證的詳細資訊，請參閱 <<c0> [ 連接到 Oracle E-business Suite，在 Visual Studio 中](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="297db-105">For more information about connecting to the Oracle E-Business Suite using Windows Authentication, see [Connect to the Oracle E-Business Suite in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md).</span></span>  

## <a name="what-you-need-to-know"></a><span data-ttu-id="297db-106">您需要知道</span><span class="sxs-lookup"><span data-stu-id="297db-106">What you need to know</span></span>  
 <span data-ttu-id="297db-107">若要使用 Windows 驗證，您必須執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="297db-107">To use Windows Authentication, you must do the following:</span></span>  
  
-   <span data-ttu-id="297db-108">如果**ClientCredentialType**屬性設定為**資料庫**、 指定"/"的使用者名稱與保留密碼為空白來連接到 Oracle E-business Suite。</span><span class="sxs-lookup"><span data-stu-id="297db-108">If the **ClientCredentialType** property is set to **Database**, specify “/” for the user name and leave the password blank to connect to the Oracle E-Business Suite.</span></span>  
  
-   <span data-ttu-id="297db-109">如果**ClientCredentialType**屬性設定為**EBusiness**，指定要連接的 Oracle E-business Suite 認證。</span><span class="sxs-lookup"><span data-stu-id="297db-109">If the **ClientCredentialType** property is set to **EBusiness**, specify the Oracle E-Business Suite credentials to connect.</span></span> <span data-ttu-id="297db-110">此外，您必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="297db-110">Also, you must specify “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.</span></span>  

## <a name="enable-windows-authentication"></a><span data-ttu-id="297db-111">啟用 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="297db-111">Enable Windows Authentication</span></span>  
 <span data-ttu-id="297db-112">若要啟用使用 Windows 驗證來連接到 Oracle 資料庫配接器用戶端，您必須執行的 Oracle 資料庫的電腦上執行下列工作。</span><span class="sxs-lookup"><span data-stu-id="297db-112">To enable adapter clients to use Windows Authentication to connect to an Oracle database, you must perform the following tasks on the computer running the Oracle database.</span></span>  
  
1. <span data-ttu-id="297db-113">請確定`sqlnet.ora`上的用戶端和伺服器，可在檔案`ORACLE_BASE\ORACLE_HOME\network\admin\sqlnet.ora`，具有下列項目：</span><span class="sxs-lookup"><span data-stu-id="297db-113">Make sure that the `sqlnet.ora` file on both the client and the server, available under `ORACLE_BASE\ORACLE_HOME\network\admin\sqlnet.ora`, has the following entry:</span></span>  
  
   ```  
   SQLNET.AUTHENTICATION_SERVICES= (NTS)  
   ```  
  
2. <span data-ttu-id="297db-114">以 sysdba 身分連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="297db-114">Connect to the Oracle database as SYSDBA.</span></span>  
  
3. <span data-ttu-id="297db-115">建立為 Oracle 資料庫中的外部使用者的 Windows 使用者。</span><span class="sxs-lookup"><span data-stu-id="297db-115">Create the Windows user as an external user in Oracle database.</span></span> <span data-ttu-id="297db-116">請注意，使用者名稱必須是大寫。</span><span class="sxs-lookup"><span data-stu-id="297db-116">Note that the user name must be in upper case.</span></span>  
  
   ```  
   CREATE USER “OPS$<DOMAIN_NAME>\<USER_NAME\>” IDENTIFIED EXTERNALLY;  
   ```  
  
4. <span data-ttu-id="297db-117">授與權限給使用者。</span><span class="sxs-lookup"><span data-stu-id="297db-117">Grant privileges to the user.</span></span>  
  
   ```  
   GRANT CONNECT,RESOURCE TO “OPS$<DOMAIN_NAME>\<USER_NAME\>”;  
   ```  
  
5. <span data-ttu-id="297db-118">Oracle E-business Suite 成品可供使用的應用程式結構描述下。</span><span class="sxs-lookup"><span data-stu-id="297db-118">The Oracle E-Business Suite artifacts are available under the APPS schema.</span></span> <span data-ttu-id="297db-119">啟用新建立的使用者，登入使用 Windows 驗證，來存取 Oracle E-business Suite 的成品，您必須變更使用者的結構描述，以應用程式結構描述。</span><span class="sxs-lookup"><span data-stu-id="297db-119">To enable the newly created user, logging in using Windows Authentication, to access the Oracle E-Business Suite artifacts, the user’s schema must be changed to the APPS schema.</span></span> <span data-ttu-id="297db-120">您可以將下列 SQL 命令加入至應用程式變更使用者的預設結構描述，當使用者登入的登入指令碼。</span><span class="sxs-lookup"><span data-stu-id="297db-120">You can add the following SQL command to the logon script that changes the user’s default schema to APPS when the user logs on.</span></span>  
  
   ```  
   alter session set current_schema=APPS;  
   ```  
  
6. <span data-ttu-id="297db-121">即使您的應用程式結構描述變更的使用者結構描述，您將仍然無法查看同時瀏覽並產生中繼資料所使用的 Oracle E-business Suite 成品[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="297db-121">Even though you changed the schema of the user to APPS schema, you will still not be able to see Oracle E-Business Suite artifacts while browsing and generating metadata using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="297db-122">這是因為新建立的使用者沒有權限的應用程式結構描述。</span><span class="sxs-lookup"><span data-stu-id="297db-122">This is because the newly created user does not have permissions for the APPS schema.</span></span> <span data-ttu-id="297db-123">請確定您針對新建立的使用者提供應用程式結構描述權限。</span><span class="sxs-lookup"><span data-stu-id="297db-123">Make sure you provided permission for the APPS schema for the newly created user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="297db-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="297db-124">See Also</span></span>  
<span data-ttu-id="297db-125">[設定 Oracle 用戶端 E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="297db-125">[Configure the Oracle client for the E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md) </span></span>  
[<span data-ttu-id="297db-126">建立 Oracle E-business Suite 連線 URI</span><span class="sxs-lookup"><span data-stu-id="297db-126">Create the Oracle E-Business Suite connection URI</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)  
 [<span data-ttu-id="297db-127">建立 Oracle E-business Suite 的連線</span><span class="sxs-lookup"><span data-stu-id="297db-127">Create a connection to Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md)