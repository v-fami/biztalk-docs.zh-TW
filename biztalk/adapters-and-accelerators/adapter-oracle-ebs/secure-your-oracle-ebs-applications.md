---
title: 保護您的 Oracle EBS 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76147120-57a8-4959-a0ff-77d04dee06a6
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03bf79d6a1324658101c2f12de758848ce7794fa
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996943"
---
# <a name="secure-your-oracle-ebs-applications"></a><span data-ttu-id="88ee2-102">保護您的 Oracle EBS 應用程式</span><span class="sxs-lookup"><span data-stu-id="88ee2-102">Secure your Oracle EBS applications</span></span>
<span data-ttu-id="88ee2-103">Oracle E-business 應用程式處理商業機密資訊，例如客戶帳戶詳細資料。</span><span class="sxs-lookup"><span data-stu-id="88ee2-103">Oracle E-Business applications deal with sensitive business information such as customer account details.</span></span> <span data-ttu-id="88ee2-104">使用應用程式[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]來存取和修改這項資訊是在本機或分散式網路上可能會不小心公開它存取未經授權的動作項目，除非工作不會對保護，並保護期間的資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="88ee2-104">Applications that use the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] to access and modify this information either locally or across a distributed network might inadvertently expose it to access by unauthorized actors, unless efforts are made to protect and secure the data during transmission.</span></span> <span data-ttu-id="88ee2-105">資料保護和安全性是通常視為以下列形式：</span><span class="sxs-lookup"><span data-stu-id="88ee2-105">Data protection and security are usually thought of in the following terms:</span></span>  
  
- <span data-ttu-id="88ee2-106">*授權*控制根據要求者的身分識別資源的存取權。</span><span class="sxs-lookup"><span data-stu-id="88ee2-106">*Authorization* controls access to a resource based on the identity of the requester.</span></span>  
  
- <span data-ttu-id="88ee2-107">*驗證*提供機制來驗證要求者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="88ee2-107">*Authentication* provides mechanisms for verifying the identity of a requester.</span></span>  
  
- <span data-ttu-id="88ee2-108">*資料機密性*提供機制來保護透過加密的資料的隱私權。</span><span class="sxs-lookup"><span data-stu-id="88ee2-108">*Data confidentiality* provides mechanisms for protecting the privacy of data through encryption.</span></span>  
  
- <span data-ttu-id="88ee2-109">*資料完整性*提供機制來數位簽署資料，讓接收者可以確保資料尚未改變傳輸中。</span><span class="sxs-lookup"><span data-stu-id="88ee2-109">*Data integrity* provides mechanisms to digitally sign data, so that the receiver can ensure that the data has not been altered in-transit.</span></span>  
  
  <span data-ttu-id="88ee2-110">值得注意的另一個重要部分是使用者名稱密碼認證提供給[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="88ee2-110">Another important area of concern is the user-name password credentials that you supply to the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="88ee2-111">配接器會使用這些認證，以開啟 連線到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="88ee2-111">The adapter uses these credentials to open connections to the Oracle database.</span></span> <span data-ttu-id="88ee2-112">在 連線 URI，可提供這些認證不過，因為使用者名稱和密碼是純文字、[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]提供替代的方法，可供您以更安全的方式提供這些認證。</span><span class="sxs-lookup"><span data-stu-id="88ee2-112">These credentials can be supplied in the connection URI; however, because the user name and password are clear text, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] provides alternative methods that you can use to supply these credentials in a more secure manner.</span></span>  
  
  <span data-ttu-id="88ee2-113">在本節中的主題提供指導方針，以協助您保護您在開發與解決方案[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="88ee2-113">The topics in this section provide guidelines to help you better secure the solutions that you develop with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
