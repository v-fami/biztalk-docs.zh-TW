---
title: "保護應用程式 Oracle EBS |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76147120-57a8-4959-a0ff-77d04dee06a6
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9a7427d36ead6ba91e0d68b1080c9ab4f5155fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="secure-your-oracle-ebs-applications"></a><span data-ttu-id="320a5-102">保護您的 Oracle EBS 應用程式</span><span class="sxs-lookup"><span data-stu-id="320a5-102">Secure your Oracle EBS applications</span></span>
<span data-ttu-id="320a5-103">Oracle E-business 應用程式可以處理敏感性商務資訊，例如客戶帳戶詳細資料。</span><span class="sxs-lookup"><span data-stu-id="320a5-103">Oracle E-Business applications deal with sensitive business information such as customer account details.</span></span> <span data-ttu-id="320a5-104">使用應用程式[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]來存取和修改這項資訊是在本機或分散式網路上可能會不小心公開以存取由未經授權的動作項目，除非工作所建立的保護，並保護期間的資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="320a5-104">Applications that use the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] to access and modify this information either locally or across a distributed network might inadvertently expose it to access by unauthorized actors, unless efforts are made to protect and secure the data during transmission.</span></span> <span data-ttu-id="320a5-105">資料保護和安全性是通常視為以下列形式：</span><span class="sxs-lookup"><span data-stu-id="320a5-105">Data protection and security are usually thought of in the following terms:</span></span>  
  
-   <span data-ttu-id="320a5-106">*授權*控制存取資源，根據要求者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="320a5-106">*Authorization* controls access to a resource based on the identity of the requester.</span></span>  
  
-   <span data-ttu-id="320a5-107">*驗證*提供機制來驗證要求者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="320a5-107">*Authentication* provides mechanisms for verifying the identity of a requester.</span></span>  
  
-   <span data-ttu-id="320a5-108">*資料機密性*提供機制來保護透過加密資料的隱私權。</span><span class="sxs-lookup"><span data-stu-id="320a5-108">*Data confidentiality* provides mechanisms for protecting the privacy of data through encryption.</span></span>  
  
-   <span data-ttu-id="320a5-109">*資料完整性*提供機制來數位簽署資料，讓接收者可以確認資料尚未改變傳輸中。</span><span class="sxs-lookup"><span data-stu-id="320a5-109">*Data integrity* provides mechanisms to digitally sign data, so that the receiver can ensure that the data has not been altered in-transit.</span></span>  
  
 <span data-ttu-id="320a5-110">另一個值得注意的重要部分是使用者名稱密碼認證提供給[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="320a5-110">Another important area of concern is the user-name password credentials that you supply to the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="320a5-111">配接器會使用這些認證，以開啟 連線到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="320a5-111">The adapter uses these credentials to open connections to the Oracle database.</span></span> <span data-ttu-id="320a5-112">這些認證可以提供在 連線 URI，不過，因為使用者名稱和密碼的純文字、[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]提供替代的方法可讓您以更安全的方式提供這些認證。</span><span class="sxs-lookup"><span data-stu-id="320a5-112">These credentials can be supplied in the connection URI; however, because the user name and password are clear text, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] provides alternative methods that you can use to supply these credentials in a more secure manner.</span></span>  
  
 <span data-ttu-id="320a5-113">此章節的主題提供指導方針來協助您更安全的解決方案，開發[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="320a5-113">The topics in this section provide guidelines to help you better secure the solutions that you develop with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
