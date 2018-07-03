---
title: 保護您的 SAP 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security and protection
ms.assetid: 9f0fb2a2-d6e2-4561-8472-c0bf682a4798
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dade1433b0bd432b53e48da86d53d23be7512de7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005783"
---
# <a name="secure-your-sap-applications"></a><span data-ttu-id="be9ed-102">保護您的 SAP 應用程式</span><span class="sxs-lookup"><span data-stu-id="be9ed-102">Secure your SAP applications</span></span>
<span data-ttu-id="be9ed-103">SAP 系統可以包含敏感性商務資訊，例如客戶帳戶詳細資料。</span><span class="sxs-lookup"><span data-stu-id="be9ed-103">The SAP system can contain sensitive business information such as customer account details.</span></span> <span data-ttu-id="be9ed-104">使用應用程式[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]來存取和修改這項資訊是在本機或分散式網路上可能會不小心公開它存取未經授權的動作項目，除非工作不會對保護，並保護期間的資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="be9ed-104">Applications that use the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] to access and modify this information either locally or across a distributed network might inadvertently expose it to access by unauthorized actors, unless efforts are made to protect and secure the data during transmission.</span></span> <span data-ttu-id="be9ed-105">資料保護和安全性是通常視為以下列形式：</span><span class="sxs-lookup"><span data-stu-id="be9ed-105">Data protection and security are usually thought of in the following terms:</span></span>  
  
- <span data-ttu-id="be9ed-106">*授權*控制根據要求者的身分識別資源的存取權。</span><span class="sxs-lookup"><span data-stu-id="be9ed-106">*Authorization* controls access to a resource based on the identity of the requestor.</span></span>  
  
- <span data-ttu-id="be9ed-107">*驗證*提供機制來驗證要求者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="be9ed-107">*Authentication* provides mechanisms for verifying the identity of a requestor.</span></span>  
  
- <span data-ttu-id="be9ed-108">*資料機密性*提供機制來保護透過加密的資料的隱私權。</span><span class="sxs-lookup"><span data-stu-id="be9ed-108">*Data confidentiality* provides mechanisms for protecting the privacy of data through encryption.</span></span>  
  
- <span data-ttu-id="be9ed-109">*資料完整性*提供機制來數位簽署資料，讓接收者可以確保資料尚未改變傳輸中。</span><span class="sxs-lookup"><span data-stu-id="be9ed-109">*Data integrity* provides mechanisms to digitally sign data, so that the receiver can ensure that the data has not been altered in-transit.</span></span>  
  
  <span data-ttu-id="be9ed-110">在本節中的主題提供指導方針，以協助您保護您在開發與解決方案[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="be9ed-110">The topics in this section provide guidelines to help you better secure the solutions that you develop with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="be9ed-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="be9ed-111">In this section</span></span>  
  
-   [<span data-ttu-id="be9ed-112">SAP 系統與配接器之間的安全性</span><span class="sxs-lookup"><span data-stu-id="be9ed-112">Security between the SAP system and the adapter</span></span>](../../adapters-and-accelerators/adapter-sap/security-between-the-sap-system-and-the-adapter.md)
  
-   [<span data-ttu-id="be9ed-113">SAP 配接器與 BizTalk Server 安全性</span><span class="sxs-lookup"><span data-stu-id="be9ed-113">Security with the SAP adapter and BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md)
  
-   [<span data-ttu-id="be9ed-114">安全使用 SAP 配接器進行程式設計</span><span class="sxs-lookup"><span data-stu-id="be9ed-114">Secure programming with the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/secure-programming-with-the-sap-adapter.md)
  
-   [<span data-ttu-id="be9ed-115">最佳作法來保護 SAP 配接器</span><span class="sxs-lookup"><span data-stu-id="be9ed-115">Best practices to secure the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/best-practices-to-secure-the-sap-adapter.md)