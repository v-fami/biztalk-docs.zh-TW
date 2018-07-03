---
title: 保護您的 Oracle 資料庫應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapter, security
- authorization
- data protection
- adapter, data protection
- authentication
- security
ms.assetid: c5f18b0a-1c8e-44c6-ba7e-470fa186f636
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7f61e15b94d741e6bfc2a9f951655ff4358a001
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982911"
---
# <a name="secure-your-oracle-database-applications"></a><span data-ttu-id="0ad31-102">保護您的 Oracle 資料庫應用程式</span><span class="sxs-lookup"><span data-stu-id="0ad31-102">Secure your Oracle Database applications</span></span>
## <a name="data-protection-and-security-overview"></a><span data-ttu-id="0ad31-103">資料保護與安全性概觀</span><span class="sxs-lookup"><span data-stu-id="0ad31-103">Data protection and security overview</span></span>
<span data-ttu-id="0ad31-104">資料庫通常會包含敏感性商務資訊，例如客戶帳戶詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0ad31-104">A database often contains sensitive business information such as customer account details.</span></span> <span data-ttu-id="0ad31-105">使用應用程式[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]來存取和修改這項資訊是在本機或分散式網路上可能會不小心公開它存取未經授權的動作項目，除非工作不會對保護，並保護期間的資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="0ad31-105">Applications that use the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] to access and modify this information either locally or across a distributed network might inadvertently expose it to access by unauthorized actors, unless efforts are made to protect and secure the data during transmission.</span></span> <span data-ttu-id="0ad31-106">資料保護和安全性是通常視為以下列形式：</span><span class="sxs-lookup"><span data-stu-id="0ad31-106">Data protection and security are usually thought of in the following terms:</span></span>  
  
- <span data-ttu-id="0ad31-107">*授權*控制根據要求者的身分識別資源的存取權。</span><span class="sxs-lookup"><span data-stu-id="0ad31-107">*Authorization* controls access to a resource based on the identity of the requester.</span></span>  
  
- <span data-ttu-id="0ad31-108">*驗證*提供機制來驗證要求者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="0ad31-108">*Authentication* provides mechanisms for verifying the identity of a requester.</span></span>  
  
- <span data-ttu-id="0ad31-109">*資料機密性*提供機制來保護透過加密的資料的隱私權。</span><span class="sxs-lookup"><span data-stu-id="0ad31-109">*Data confidentiality* provides mechanisms for protecting the privacy of data through encryption.</span></span>  
  
- <span data-ttu-id="0ad31-110">*資料完整性*提供機制來數位簽署資料，讓接收者可以確保資料尚未改變傳輸中。</span><span class="sxs-lookup"><span data-stu-id="0ad31-110">*Data integrity* provides mechanisms to digitally sign data, so that the receiver can ensure that the data has not been altered in-transit.</span></span>  
  
  <span data-ttu-id="0ad31-111">值得注意的另一個重要部分是使用者名稱密碼認證提供給[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0ad31-111">Another important area of concern is the user-name password credentials that you supply to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="0ad31-112">配接器會使用這些認證，以開啟 連線到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0ad31-112">The adapter uses these credentials to open connections to the Oracle database.</span></span> <span data-ttu-id="0ad31-113">在 連線 URI，可提供這些認證不過，因為使用者名稱和密碼是純文字、[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]提供替代的方法，可供您以更安全的方式提供這些認證。</span><span class="sxs-lookup"><span data-stu-id="0ad31-113">These credentials can be supplied in the connection URI; however, because the user name and password are clear text, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] provides alternative methods that you can use to supply these credentials in a more secure manner.</span></span>  
  
  <span data-ttu-id="0ad31-114">在本節中的主題提供指導方針，以協助您保護您在開發與解決方案[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0ad31-114">The topics in this section provide guidelines to help you better secure the solutions that you develop with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0ad31-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="0ad31-115">In this section</span></span>  
  
-   [<span data-ttu-id="0ad31-116">Oracle 資料庫與配接器之間的安全性</span><span class="sxs-lookup"><span data-stu-id="0ad31-116">Security between the Oracle Database and the adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/security-between-the-oracle-database-and-the-adapter.md)
  
-   [<span data-ttu-id="0ad31-117">Oracle 資料庫配接器與 BizTalk Server 安全性</span><span class="sxs-lookup"><span data-stu-id="0ad31-117">Security with the Oracle Database adapter and BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md)  
  
-   [<span data-ttu-id="0ad31-118">安全使用 Oracle 資料庫配接器進行程式設計</span><span class="sxs-lookup"><span data-stu-id="0ad31-118">Secure programming with the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/secure-programming-with-the-oracle-database-adapter.md) 
  
-   [<span data-ttu-id="0ad31-119">最佳做法</span><span class="sxs-lookup"><span data-stu-id="0ad31-119">Best practices</span></span>](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)