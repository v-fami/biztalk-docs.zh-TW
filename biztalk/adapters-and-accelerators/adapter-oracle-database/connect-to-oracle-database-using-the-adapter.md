---
title: 連接到 Oracle 資料庫使用配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection string
- uniform resource identifier
- Oracle database, connecting to
- URI
- connection URI
ms.assetid: 5d5598e5-aba0-4c73-8e97-9156475b93c4
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01b04a615d0b0b8cd83b9ed7516cd096b2c85a54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214750"
---
# <a name="connect-to-oracle-database-using-the-adapter"></a><span data-ttu-id="c2e68-102">連接到 Oracle 資料庫使用配接器</span><span class="sxs-lookup"><span data-stu-id="c2e68-102">Connect to Oracle Database using the adapter</span></span>
<span data-ttu-id="c2e68-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]使用 ODP.NET 11.1.0.7 連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c2e68-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] uses ODP.NET 11.1.0.7 to connect to the Oracle database.</span></span> <span data-ttu-id="c2e68-104">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]需要配接器用戶端提供的連接字串，呼叫統一資源識別元 (URI)，連接到 Oracle 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="c2e68-104">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] requires adapter clients to provide a connection string, called the connection Uniform Resource Identifier (URI), to connect to the Oracle database.</span></span> <span data-ttu-id="c2e68-105">就內部而言， [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] URI 會對應至連接到 Oracle 資料庫的資料庫連接字串。</span><span class="sxs-lookup"><span data-stu-id="c2e68-105">Internally, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] maps the URI to a database connection string to connect to the Oracle database.</span></span> <span data-ttu-id="c2e68-106">使用 連線 URI，配接器用戶端可以指定連線參數，以連接到外部系統。</span><span class="sxs-lookup"><span data-stu-id="c2e68-106">With a connection URI, adapter clients can specify connection parameters to connect to an external system.</span></span>  
  
 <span data-ttu-id="c2e68-107">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓配接器用戶端連接到 Oracle 資料庫中下列兩種方式：</span><span class="sxs-lookup"><span data-stu-id="c2e68-107">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] enables adapter clients to connect to the Oracle database in the following two ways:</span></span>  
  
-   <span data-ttu-id="c2e68-108">**使用 tnsnames.ora**： 連線配接器用戶端所提供的 URI 包含只 tnsnames.ora 檔案中指定的網路服務名稱。</span><span class="sxs-lookup"><span data-stu-id="c2e68-108">**Using tnsnames.ora**: The connection URI provided by the adapter client contains only the net service name specified in the tnsnames.ora file.</span></span> <span data-ttu-id="c2e68-109">配接器從 tnsnames.ora 檔案中的網路服務名稱的項目中擷取連接參數，例如伺服器名稱、 服務名稱和連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="c2e68-109">The adapter extracts the connection parameters such as server name, service name, and port number from the net service name entry in the tnsnames.ora file.</span></span> <span data-ttu-id="c2e68-110">若要使用這種方法，執行 Oracle 用戶端的電腦必須設定要在 tnsnames.ora 檔案中包含之 Oracle 資料庫的網路服務名稱。</span><span class="sxs-lookup"><span data-stu-id="c2e68-110">To use this approach, the computer running the Oracle client must be configured to include the net service name for the Oracle database in the tnsnames.ora file.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c2e68-111">由於 Oracle 用戶端的限制， **DataSourceName**中的參數 (net service name)[設定 Oracle 資料庫配接器的連線 URI](../../adapters-and-accelerators/adapter-oracle-database/configure-the-connection-uri-for-the-oracle-database-adapter.md)不能包含超過 39 個字元，如果您在交易中執行作業。</span><span class="sxs-lookup"><span data-stu-id="c2e68-111">Due to an Oracle Client limitation, the **DataSourceName** parameter (net service name) in the [Configure the connection URI for the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/configure-the-connection-uri-for-the-oracle-database-adapter.md) cannot contain more than 39 characters if you are performing operations in a transaction.</span></span> <span data-ttu-id="c2e68-112">因此，請確定為指定的值**DataSourceName**參數為小於或等於 39 個字元，如果您將在交易中執行的作業。</span><span class="sxs-lookup"><span data-stu-id="c2e68-112">Therefore, make sure that the value specified for the **DataSourceName** parameter is less than or equal to 39 characters if you will be performing operations in a transaction.</span></span>  
  
-   <span data-ttu-id="c2e68-113">**不使用 tnsnames.ora**： 配接器用戶端所提供的 URI 的連接包含連接參數，例如伺服器名稱、 服務名稱和連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="c2e68-113">**Without using tnsnames.ora**: The connection URI provided by the adapter clients contains the connection parameters such as server name, service name, and port number.</span></span> <span data-ttu-id="c2e68-114">在此情況下，網路服務名稱在 tnsnames.ora 檔案或實際 tnsnames.ora 檔案本身，無須任何存在於用戶端電腦上。</span><span class="sxs-lookup"><span data-stu-id="c2e68-114">In this case, the net service name in the tnsnames.ora file, or the actual tnsnames.ora file itself, does not need to be present on the client computer.</span></span> <span data-ttu-id="c2e68-115">當您有大量使用者連接到 Oracle 資料庫，在您的組織，並新增/更新伺服器不會導致以手動方式新增/更新每個用戶端電腦上 tnsnames.ora 檔案中的連線詳細資料，這是很有幫助。</span><span class="sxs-lookup"><span data-stu-id="c2e68-115">This is helpful when you have a large number of users connecting to the Oracle database in your organization, and adding/updating servers does not lead to manually adding/updating the connection details in the tnsnames.ora file on every client computer.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c2e68-116">如果您在交易中執行作業，則不支援這種連線模式。</span><span class="sxs-lookup"><span data-stu-id="c2e68-116">This mode of connectivity is not supported if you are performing operations in a transaction.</span></span> <span data-ttu-id="c2e68-117">這是因為 Oracle 用戶端的限制。</span><span class="sxs-lookup"><span data-stu-id="c2e68-117">This is due to a limitation of Oracle Client.</span></span>  
  
 <span data-ttu-id="c2e68-118">如需有關如何連接到 Oracle 資料庫的詳細資訊，請參閱[建立連接到 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="c2e68-118">For more information about connecting to the Oracle database, see [Create a connection to the Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md).</span></span>  
  
 <span data-ttu-id="c2e68-119">請確定您遵循安全性指導方針建立與 Oracle 資料庫的連接時。</span><span class="sxs-lookup"><span data-stu-id="c2e68-119">Make sure you comply with the security guidelines when establishing a connection with the Oracle database.</span></span> <span data-ttu-id="c2e68-120">如需安全性指導方針的詳細資訊，請參閱[保護 Oracle 資料庫應用程式安全](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="c2e68-120">For more information about security guidelines, see [Secure your Oracle Database applications](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md).</span></span>  
  
## <a name="windows-authentication"></a><span data-ttu-id="c2e68-121">Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="c2e68-121">Windows Authentication</span></span>  
 <span data-ttu-id="c2e68-122">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]同時支援 Windows 驗證連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c2e68-122">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports Windows Authentication while connecting to the Oracle database.</span></span> <span data-ttu-id="c2e68-123">使用 Windows 驗證時，配接器用戶端可以判斷使用者的身分識別為基礎的 Windows 登入認證，並可以利用內建安全性的 Windows 環境。</span><span class="sxs-lookup"><span data-stu-id="c2e68-123">With Windows Authentication, the adapter clients can determine a user’s identity based on Windows logon credentials, and can leverage the built-in security of the Windows environment.</span></span> <span data-ttu-id="c2e68-124">如需使用 Windows 驗證連接到 Oracle 資料庫的資訊，請參閱[連接到 Oracle 資料庫使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="c2e68-124">For information about connecting to the Oracle database by using Windows Authentication, see [Connect to the Oracle Database Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2e68-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2e68-125">See Also</span></span>  
 [<span data-ttu-id="c2e68-126">BizTalk Adapter for Oracle 資料庫的概觀</span><span class="sxs-lookup"><span data-stu-id="c2e68-126">Overview of BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)