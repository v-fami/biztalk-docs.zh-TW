---
title: 保護 SQL 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b182593-fcca-4ebc-a2fd-7684b84cfb15
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d631bc3ad87e9a8ec8ac51850b7dbe1eb244c140
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224438"
---
# <a name="secure-your-sql-applications"></a><span data-ttu-id="bb68c-102">保護 SQL 應用程式</span><span class="sxs-lookup"><span data-stu-id="bb68c-102">Secure your SQL applications</span></span>
## <a name="overview"></a><span data-ttu-id="bb68c-103">概觀</span><span class="sxs-lookup"><span data-stu-id="bb68c-103">Overview</span></span>
<span data-ttu-id="bb68c-104">SQL Server 資料庫通常會包含敏感性商務資訊，例如客戶帳戶詳細資料。</span><span class="sxs-lookup"><span data-stu-id="bb68c-104">SQL Server databases often contain sensitive business information such as customer account details.</span></span> <span data-ttu-id="bb68c-105">使用應用程式[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]來存取和修改這項資訊是在本機或分散式網路上可能會不小心公開以存取由未經授權的動作項目，除非工作所建立的保護，並保護期間的資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="bb68c-105">Applications that use the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] to access and modify this information either locally or across a distributed network might inadvertently expose it to access by unauthorized actors, unless efforts are made to protect and secure the data during transmission.</span></span> <span data-ttu-id="bb68c-106">資料保護和安全性是通常視為以下列形式：</span><span class="sxs-lookup"><span data-stu-id="bb68c-106">Data protection and security are usually thought of in the following terms:</span></span>  
  
-   <span data-ttu-id="bb68c-107">*授權*控制存取資源，根據要求者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="bb68c-107">*Authorization* controls access to a resource based on the identity of the requestor.</span></span>  
  
-   <span data-ttu-id="bb68c-108">*驗證*提供機制來驗證要求者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="bb68c-108">*Authentication* provides mechanisms for verifying the identity of a requestor.</span></span>  
  
-   <span data-ttu-id="bb68c-109">*資料機密性*提供機制來保護透過加密資料的隱私權。</span><span class="sxs-lookup"><span data-stu-id="bb68c-109">*Data confidentiality* provides mechanisms for protecting the privacy of data through encryption.</span></span>  
  
-   <span data-ttu-id="bb68c-110">*資料完整性*提供機制來數位簽署資料，讓接收者可以確認資料尚未改變傳輸中。</span><span class="sxs-lookup"><span data-stu-id="bb68c-110">*Data integrity* provides mechanisms to digitally sign data, so that the receiver can ensure that the data has not been altered in-transit.</span></span>  
  
 <span data-ttu-id="bb68c-111">另一個值得注意的重要部分是使用者名稱密碼認證提供給[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bb68c-111">Another important area of concern is the user-name password credentials that you supply to the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="bb68c-112">配接器會使用這些認證，開啟與 SQL 系統的連線。</span><span class="sxs-lookup"><span data-stu-id="bb68c-112">The adapter uses these credentials to open connections to the SQL system.</span></span> <span data-ttu-id="bb68c-113">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不允許連線 URI 中所提供的認證。</span><span class="sxs-lookup"><span data-stu-id="bb68c-113">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not allow credentials to be supplied in the connection URI.</span></span> <span data-ttu-id="bb68c-114">這可防止不小心取得公開憑證。</span><span class="sxs-lookup"><span data-stu-id="bb68c-114">This prevents the credentials from getting exposed inadvertently.</span></span> <span data-ttu-id="bb68c-115">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]提供兩種替代方法，以更安全的方式提供這些認證：</span><span class="sxs-lookup"><span data-stu-id="bb68c-115">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] provides two alternative methods to supply these credentials in a more secure manner:</span></span>  
  
 <span data-ttu-id="bb68c-116">整合式的安全性。</span><span class="sxs-lookup"><span data-stu-id="bb68c-116">Integrated Security.</span></span> <span data-ttu-id="bb68c-117">在此情況下，[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用 Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]認證。</span><span class="sxs-lookup"><span data-stu-id="bb68c-117">In this case, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] uses the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] credentials.</span></span> <span data-ttu-id="bb68c-118">您必須設定 SQL server 來接受這些認證，此方法才能運作。</span><span class="sxs-lookup"><span data-stu-id="bb68c-118">You must configure the SQL server to accept these credentials for this method to work.</span></span>  
  
 <span data-ttu-id="bb68c-119">企業單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="bb68c-119">Enterprise Single Sign-on (SSO).</span></span> <span data-ttu-id="bb68c-120">如需有關使用 SSO 的詳細資訊，請參閱[使用 SQL 配接器和 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bb68c-120">For more information about using SSO, see [Security with the SQL adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md) .</span></span>  
  
 <span data-ttu-id="bb68c-121">此章節的主題提供指導方針來協助您更安全的解決方案，開發[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bb68c-121">The topics in this section provide guidelines to help you better secure the solutions that you develop with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bb68c-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="bb68c-122">In This Section</span></span>  
  
-   [<span data-ttu-id="bb68c-123">SQL Server 與配接器之間的安全性</span><span class="sxs-lookup"><span data-stu-id="bb68c-123">Security between the SQL Server and the adapter</span></span>](../../adapters-and-accelerators/adapter-sql/security-between-the-sql-server-and-the-adapter.md)
  
-   [<span data-ttu-id="bb68c-124">使用 SQL 配接器和 BizTalk Server 安全性</span><span class="sxs-lookup"><span data-stu-id="bb68c-124">Security with the SQL adapter and BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md) 
  
-   [<span data-ttu-id="bb68c-125">保護使用 SQL 配接器進行程式設計</span><span class="sxs-lookup"><span data-stu-id="bb68c-125">Secure programming with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/secure-programming-with-the-sql-adapter.md)
  
-   [<span data-ttu-id="bb68c-126">最佳作法</span><span class="sxs-lookup"><span data-stu-id="bb68c-126">Best practices</span></span>](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md)