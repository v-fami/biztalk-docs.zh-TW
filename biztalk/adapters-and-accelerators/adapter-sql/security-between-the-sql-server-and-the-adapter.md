---
title: "SQL Server 與配接器之間的安全性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4b0fd11-6753-4f52-9be7-3b6fa330fb8b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8673aee316a8a2ef83011ab3dd85016a99df1162
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="security-between-the-sql-server-and-the-adapter"></a><span data-ttu-id="057d5-102">SQL Server 與配接器之間的安全性</span><span class="sxs-lookup"><span data-stu-id="057d5-102">Security between the SQL Server and the adapter</span></span>
<span data-ttu-id="057d5-103">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]是相容的標準方法，例如 SSO 和 IPSEC 來保護資料交換與資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="057d5-103">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is compatible with the standard methods, such as SSO and IPSEC used to secure data exchanges with the database server.</span></span> <span data-ttu-id="057d5-104">不安全的資料交換可以將資料公開給未經授權的動作項目。</span><span class="sxs-lookup"><span data-stu-id="057d5-104">Unsecured data exchanges can expose data to unauthorized actors.</span></span> <span data-ttu-id="057d5-105">如需與 SQL Server 的安全性問題的資訊，請參閱[的 SQL Server 的安全性考量](http://go.microsoft.com/fwlink/p/?LinkId=196954)SQL 文件中。</span><span class="sxs-lookup"><span data-stu-id="057d5-105">For information about security issues with SQL Server, see [Security Considerations for SQL Server](http://go.microsoft.com/fwlink/p/?LinkId=196954) in the SQL documentation.</span></span>  
  
 <span data-ttu-id="057d5-106">您可以使用網際網路通訊協定安全性 (IPsec) 來改善資料交換的安全性。</span><span class="sxs-lookup"><span data-stu-id="057d5-106">You can improve the security of data exchanges by using Internet Protocol Security (IPsec).</span></span> <span data-ttu-id="057d5-107">IPsec 是來保護通訊，網際網路通訊協定 (IP) 網路上的開放式標準的架構。</span><span class="sxs-lookup"><span data-stu-id="057d5-107">IPsec is a framework of open standards for protecting communications over Internet Protocol (IP) networks.</span></span> <span data-ttu-id="057d5-108">使用 IPSec，任何資料之間的交換[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與 SQL 加密在網路上的伺服器，讓未經授權的動作項目来使用的資料。</span><span class="sxs-lookup"><span data-stu-id="057d5-108">With IPSec, any data exchanged between the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] and the SQL server over the network is encrypted, making it difficult for unauthorized actors to use the data.</span></span> <span data-ttu-id="057d5-109">如需有關 IPsec 以及使用 IPsec 與 Microsoft 產品的詳細資訊，請參閱 Microsoft TechNet 文章[IPsec](http://go.microsoft.com/fwlink/p/?LinkId=196955)。</span><span class="sxs-lookup"><span data-stu-id="057d5-109">For more information about IPsec and about using IPsec with Microsoft products, see the Microsoft TechNet article [IPsec](http://go.microsoft.com/fwlink/p/?LinkId=196955).</span></span>  
  
 <span data-ttu-id="057d5-110">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援 SSO 和整合式安全性進行驗證，它會建立與資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="057d5-110">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports SSO and Integrated Security for authentication on the connections that it establishes with the database.</span></span> <span data-ttu-id="057d5-111">使用 SSO，這些認證會加密並儲存在登錄中。</span><span class="sxs-lookup"><span data-stu-id="057d5-111">With SSO, the credentials are encrypted and stored in the registry.</span></span> <span data-ttu-id="057d5-112">系統會使用這些認證，來決定存取權限，而不需要使用者輸入，可能會看到它們由未經授權的動作項目。</span><span class="sxs-lookup"><span data-stu-id="057d5-112">The system uses these credentials to determine access instead of requiring the user to enter them where they might be seen by unauthorized actors.</span></span> <span data-ttu-id="057d5-113">整合式的安全性以存取 SQL server 使用登入的使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="057d5-113">Integrated Security uses the credentials of the logged on user to access the SQL server.</span></span> <span data-ttu-id="057d5-114">這也就不需要使用者輸入認證。</span><span class="sxs-lookup"><span data-stu-id="057d5-114">This also eliminates the need for users to enter credentials.</span></span> <span data-ttu-id="057d5-115">資料庫管理員必須設定為接受正常運作的整合式安全性的使用者認證的 SQL。</span><span class="sxs-lookup"><span data-stu-id="057d5-115">The database administrator must configure SQL to accept the users credentials for Integrated Security to work correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="057d5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="057d5-116">See Also</span></span>  
[<span data-ttu-id="057d5-117">保護 SQL 應用程式</span><span class="sxs-lookup"><span data-stu-id="057d5-117">Secure your SQL applications</span></span>](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)