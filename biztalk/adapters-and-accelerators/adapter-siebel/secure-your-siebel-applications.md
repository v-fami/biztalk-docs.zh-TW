---
title: "保護您的 Siebel 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security and protection
- data protection
ms.assetid: 8977cbd3-0025-48d4-8203-8e9e72ea7d26
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3b597120de91b6a09fdc26b90a2cb357cdc7dd1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="secure-your-siebel-applications"></a><span data-ttu-id="22a0c-102">保護您的 Siebel 應用程式</span><span class="sxs-lookup"><span data-stu-id="22a0c-102">Secure your Siebel applications</span></span>
<span data-ttu-id="22a0c-103">Siebel 系統通常會包含敏感性商務資訊，例如客戶帳戶詳細資料。</span><span class="sxs-lookup"><span data-stu-id="22a0c-103">The Siebel system often contains sensitive business information such as customer account details.</span></span> <span data-ttu-id="22a0c-104">使用應用程式[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]來存取和修改這項資訊是在本機或分散式網路上可能會不小心公開以存取由未經授權的動作項目，除非工作所建立的保護，並保護期間的資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="22a0c-104">Applications that use the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] to access and modify this information either locally or across a distributed network might inadvertently expose it to access by unauthorized actors, unless efforts are made to protect and secure the data during transmission.</span></span> <span data-ttu-id="22a0c-105">資料保護和安全性是通常視為以下列形式：</span><span class="sxs-lookup"><span data-stu-id="22a0c-105">Data protection and security are usually thought of in the following terms:</span></span>  
  
-   <span data-ttu-id="22a0c-106">*授權*控制存取資源，根據要求者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="22a0c-106">*Authorization* controls access to a resource based on the identity of the requester.</span></span>  
  
-   <span data-ttu-id="22a0c-107">*驗證*提供機制來驗證要求者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="22a0c-107">*Authentication* provides mechanisms for verifying the identity of a requester.</span></span>  
  
-   <span data-ttu-id="22a0c-108">*資料機密性*提供機制來保護透過加密資料的隱私權。</span><span class="sxs-lookup"><span data-stu-id="22a0c-108">*Data confidentiality* provides mechanisms for protecting the privacy of data through encryption.</span></span>  
  
-   <span data-ttu-id="22a0c-109">*資料完整性*提供機制來數位簽署資料，讓接收者可以確認資料尚未改變傳輸中。</span><span class="sxs-lookup"><span data-stu-id="22a0c-109">*Data integrity* provides mechanisms to digitally sign data, so that the receiver can ensure that the data has not been altered in-transit.</span></span>  
  
 <span data-ttu-id="22a0c-110">另一個值得注意的重要部分是使用者名稱密碼認證提供給[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="22a0c-110">Another important area of concern is the user-name password credentials that you supply to the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="22a0c-111">配接器會使用這些認證來開啟連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="22a0c-111">The adapter uses these credentials to open connections to the Siebel system.</span></span> <span data-ttu-id="22a0c-112">這些認證可以提供在 連線 URI，不過，因為使用者名稱和密碼的純文字、[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]提供替代的方法可讓您以更安全的方式提供這些認證。</span><span class="sxs-lookup"><span data-stu-id="22a0c-112">These credentials can be supplied in the connection URI; however, because the user name and password are clear text, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] provides alternative methods that you can use to supply these credentials in a more secure manner.</span></span>  
  
 <span data-ttu-id="22a0c-113">此章節的主題提供指導方針來協助您更安全的解決方案，開發[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="22a0c-113">The topics in this section provide guidelines to help you better secure the solutions that you develop with the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="22a0c-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="22a0c-114">In This Section</span></span>  
  
-   [<span data-ttu-id="22a0c-115">Siebel 系統與配接器之間的安全性</span><span class="sxs-lookup"><span data-stu-id="22a0c-115">Security between the Siebel system and the adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/security-between-the-siebel-system-and-the-adapter.md)
  
-   [<span data-ttu-id="22a0c-116">使用 Siebel 配接器和 BizTalk Server 安全性</span><span class="sxs-lookup"><span data-stu-id="22a0c-116">Security with Siebel adapter and BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md)
  
-   [<span data-ttu-id="22a0c-117">安全使用 Siebel 配接器進行程式設計</span><span class="sxs-lookup"><span data-stu-id="22a0c-117">Secure programming with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/secure-programming-with-the-siebel-adapter.md)
  
-   [<span data-ttu-id="22a0c-118">若要保護 Siebel 配接器的最佳作法</span><span class="sxs-lookup"><span data-stu-id="22a0c-118">Best practices to secure the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/best-practices-to-secure-the-siebel-adapter.md)