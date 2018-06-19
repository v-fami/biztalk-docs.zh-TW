---
title: 保護您的 Oracle 資料庫應用程式 |Microsoft 文件
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
ms.openlocfilehash: e8601463c02e32221c369023f05ed2fd3731bb4b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214702"
---
# <a name="secure-your-oracle-database-applications"></a><span data-ttu-id="5dabf-102">保護您的 Oracle 資料庫應用程式</span><span class="sxs-lookup"><span data-stu-id="5dabf-102">Secure your Oracle Database applications</span></span>
## <a name="data-protection-and-security-overview"></a><span data-ttu-id="5dabf-103">資料保護與安全性概觀</span><span class="sxs-lookup"><span data-stu-id="5dabf-103">Data protection and security overview</span></span>
<span data-ttu-id="5dabf-104">資料庫通常會包含敏感性商務資訊，例如客戶帳戶詳細資料。</span><span class="sxs-lookup"><span data-stu-id="5dabf-104">A database often contains sensitive business information such as customer account details.</span></span> <span data-ttu-id="5dabf-105">使用應用程式[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]來存取和修改這項資訊是在本機或分散式網路上可能會不小心公開以存取由未經授權的動作項目，除非工作所建立的保護，並保護期間的資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="5dabf-105">Applications that use the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] to access and modify this information either locally or across a distributed network might inadvertently expose it to access by unauthorized actors, unless efforts are made to protect and secure the data during transmission.</span></span> <span data-ttu-id="5dabf-106">資料保護和安全性是通常視為以下列形式：</span><span class="sxs-lookup"><span data-stu-id="5dabf-106">Data protection and security are usually thought of in the following terms:</span></span>  
  
-   <span data-ttu-id="5dabf-107">*授權*控制存取資源，根據要求者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="5dabf-107">*Authorization* controls access to a resource based on the identity of the requester.</span></span>  
  
-   <span data-ttu-id="5dabf-108">*驗證*提供機制來驗證要求者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="5dabf-108">*Authentication* provides mechanisms for verifying the identity of a requester.</span></span>  
  
-   <span data-ttu-id="5dabf-109">*資料機密性*提供機制來保護透過加密資料的隱私權。</span><span class="sxs-lookup"><span data-stu-id="5dabf-109">*Data confidentiality* provides mechanisms for protecting the privacy of data through encryption.</span></span>  
  
-   <span data-ttu-id="5dabf-110">*資料完整性*提供機制來數位簽署資料，讓接收者可以確認資料尚未改變傳輸中。</span><span class="sxs-lookup"><span data-stu-id="5dabf-110">*Data integrity* provides mechanisms to digitally sign data, so that the receiver can ensure that the data has not been altered in-transit.</span></span>  
  
 <span data-ttu-id="5dabf-111">另一個值得注意的重要部分是使用者名稱密碼認證提供給[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5dabf-111">Another important area of concern is the user-name password credentials that you supply to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="5dabf-112">配接器會使用這些認證，以開啟 連線到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5dabf-112">The adapter uses these credentials to open connections to the Oracle database.</span></span> <span data-ttu-id="5dabf-113">這些認證可以提供在 連線 URI，不過，因為使用者名稱和密碼的純文字、[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]提供替代的方法可讓您以更安全的方式提供這些認證。</span><span class="sxs-lookup"><span data-stu-id="5dabf-113">These credentials can be supplied in the connection URI; however, because the user name and password are clear text, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] provides alternative methods that you can use to supply these credentials in a more secure manner.</span></span>  
  
 <span data-ttu-id="5dabf-114">此章節的主題提供指導方針來協助您更安全的解決方案，開發[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5dabf-114">The topics in this section provide guidelines to help you better secure the solutions that you develop with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5dabf-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="5dabf-115">In this section</span></span>  
  
-   [<span data-ttu-id="5dabf-116">Oracle 資料庫與配接器之間的安全性</span><span class="sxs-lookup"><span data-stu-id="5dabf-116">Security between the Oracle Database and the adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/security-between-the-oracle-database-and-the-adapter.md)
  
-   [<span data-ttu-id="5dabf-117">使用 Oracle 資料庫配接器和 BizTalk Server 安全性</span><span class="sxs-lookup"><span data-stu-id="5dabf-117">Security with the Oracle Database adapter and BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md)  
  
-   [<span data-ttu-id="5dabf-118">安全使用 Oracle 資料庫配接器進行程式設計</span><span class="sxs-lookup"><span data-stu-id="5dabf-118">Secure programming with the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/secure-programming-with-the-oracle-database-adapter.md) 
  
-   [<span data-ttu-id="5dabf-119">最佳作法</span><span class="sxs-lookup"><span data-stu-id="5dabf-119">Best practices</span></span>](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)