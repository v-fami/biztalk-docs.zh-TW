---
title: "小型至中型公司的安全性案例研究 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, small distributions
- architecture, examples
- security, examples
- security, architecture
- architecture, medium distributions
ms.assetid: b33e3f2a-ddc4-47a8-92d7-511ae0cc880e
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9af0f013960e882ffe6b5c081ae1452df4aaecf1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="security-case-studies-for-small-to-medium-sized-companies"></a><span data-ttu-id="ce52c-102">小型至中型公司的安全性案例研究</span><span class="sxs-lookup"><span data-stu-id="ce52c-102">Security Case Studies for Small to Medium-Sized Companies</span></span>
<span data-ttu-id="ce52c-103">對於希望只有選取的人員或應用程式群組可以存取資料與資源的任何公司來說，安全性是關注的項目之一。</span><span class="sxs-lookup"><span data-stu-id="ce52c-103">Security is a concern of any company that is serious about making sure that only a select group of people or applications can access its data and resources.</span></span> <span data-ttu-id="ce52c-104">各公司會以許多方法來達成和實作安全性。</span><span class="sxs-lookup"><span data-stu-id="ce52c-104">Companies approach and implement security in a variety of ways.</span></span>  
  
 <span data-ttu-id="ce52c-105">本節提供在安全環境中部署 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的方針。</span><span class="sxs-lookup"><span data-stu-id="ce52c-105">This section provides guidelines for deploying Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a secure environment.</span></span> <span data-ttu-id="ce52c-106">其中提供的資訊可協助您評估 BizTalk Server 實作、中小型公司的範例架構的潛在威脅。</span><span class="sxs-lookup"><span data-stu-id="ce52c-106">It provides information to help you assess the potential threats to your BizTalk Server implementation, a sample architecture for small and medium-size companies.</span></span>  
  
 <span data-ttu-id="ce52c-107">現今若不考慮安全性，就難以使企業運作。</span><span class="sxs-lookup"><span data-stu-id="ce52c-107">It is difficult to run a business today without thinking about security.</span></span> <span data-ttu-id="ce52c-108">若您執行線上交易，您就必須保護客戶的信用卡資訊。</span><span class="sxs-lookup"><span data-stu-id="ce52c-108">If you carry out online transactions, you want to protect the credit card information of your customers.</span></span> <span data-ttu-id="ce52c-109">若您為 Fortune 500 公司工作，就要使惡意使用者遠離您的網路。</span><span class="sxs-lookup"><span data-stu-id="ce52c-109">If you work for a Fortune 500 company, you want to keep malicious users away from your networks.</span></span> <span data-ttu-id="ce52c-110">若您是桌上型電腦的使用者，您應該不會想讓病毒與蠕蟲破壞您的資料和限制您執行工作的能力。</span><span class="sxs-lookup"><span data-stu-id="ce52c-110">If you are a desktop user, you want to keep viruses and worms from damaging your data and limiting your ability to do your work.</span></span> <span data-ttu-id="ce52c-111">幾乎每一天您都會聽到新的軟體弱點；散播快速的新蠕蟲與病毒難以根絕，而且比前一個造成更多損壞；以及公司網站被惡意使用者破壞。</span><span class="sxs-lookup"><span data-stu-id="ce52c-111">Almost every day you hear or read about new software vulnerabilities; about new worms and viruses that are faster spreading, harder to eradicate, and more damaging than the previous ones; and about the Web sites of companies being defaced by malicious users.</span></span> <span data-ttu-id="ce52c-112">不論您的企業是大型或小型，擁有少數客戶或有上百萬個客戶，擁有一部電腦或上百部電腦，都必須杜絕惡意使用者與程式危害您的資料、電腦以及執行工作的能力。</span><span class="sxs-lookup"><span data-stu-id="ce52c-112">Whatever your business is—large or small, a few customers or millions of customers, one computer or hundreds of computers—you need to keep malicious users and programs (viruses, worms) from compromising your data, computers, and ability to do your job.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ce52c-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="ce52c-113">In This Section</span></span>  
  
-   [<span data-ttu-id="ce52c-114">安全性個案研究： 公司 A</span><span class="sxs-lookup"><span data-stu-id="ce52c-114">Security Case Studies: Company A</span></span>](../core/security-case-studies-company-a.md)  
  
-   [<span data-ttu-id="ce52c-115">安全性個案研究： 公司 B</span><span class="sxs-lookup"><span data-stu-id="ce52c-115">Security Case Studies: Company B</span></span>](../core/security-case-studies-company-b.md)  
  
-   [<span data-ttu-id="ce52c-116">威脅模型分析</span><span class="sxs-lookup"><span data-stu-id="ce52c-116">Threat Model Analysis</span></span>](../core/threat-model-analysis.md)  
  
-   [<span data-ttu-id="ce52c-117">小型與中型公司的範例架構</span><span class="sxs-lookup"><span data-stu-id="ce52c-117">Sample Architectures for Small & Medium-Sized Companies</span></span>](../core/sample-architectures-for-small-medium-sized-companies.md)  
  
-   [<span data-ttu-id="ce52c-118">威脅模型分析的範例案例</span><span class="sxs-lookup"><span data-stu-id="ce52c-118">Sample Scenarios for Threat Model Analysis</span></span>](../core/sample-scenarios-for-threat-model-analysis.md)