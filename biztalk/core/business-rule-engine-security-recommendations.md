---
title: 商務規則引擎安全性建議 |Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, business rules
- Business Rules Framework, security
- business rules, security
ms.assetid: d5df1cd0-112a-4c72-b95d-cbcd1bc6a2c3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ca5506d8ed9acab63e32a4ec86b057a4b775b63
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752750"
---
# <a name="business-rule-engine-security-recommendations"></a><span data-ttu-id="202bc-102">商務規則引擎安全性建議</span><span class="sxs-lookup"><span data-stu-id="202bc-102">Business Rule Engine Security Recommendations</span></span>
<span data-ttu-id="202bc-103">商務規則引擎是商務規則架構的執行階段元件。</span><span class="sxs-lookup"><span data-stu-id="202bc-103">The Business Rule Engine is the runtime component of the Business Rule Framework.</span></span> <span data-ttu-id="202bc-104">您可以使用商務規則架構，將易讀、宣告式且語意豐富的規則連接到任何商務物件 (.NET 元件)、XML文件或資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="202bc-104">With the Business Rule Framework, you can connect highly readable, declarative, semantically rich rules to any business objects (.NET components), XML documents, or database tables.</span></span> <span data-ttu-id="202bc-105">如需有關商務規則架構的詳細資訊，請參閱 <<c0> [ 建立和使用商務規則](../core/creating-and-using-business-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="202bc-105">For more information about the Business Rule Framework, see [Creating and Using Business Rules](../core/creating-and-using-business-rules.md).</span></span> <span data-ttu-id="202bc-106">如需有關 「 商務規則引擎的詳細資訊，請參閱[規則引擎](../core/rule-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="202bc-106">For more information about the Business Rule Engine, see [Rule Engine](../core/rule-engine.md).</span></span>  
  
 <span data-ttu-id="202bc-107">商務規則引擎沒有 Windows 使用者群組，只有個別的帳戶。</span><span class="sxs-lookup"><span data-stu-id="202bc-107">There are no Windows user groups for the Business Rule Engine, only individual accounts.</span></span> <span data-ttu-id="202bc-108">BizTalk Server 使用兩個 SQL Sever 角色來限制對商務規則引擎資源的存取：</span><span class="sxs-lookup"><span data-stu-id="202bc-108">BizTalk Server restricts access to the Business Rule Engine resources by using two SQL Server roles:</span></span>  
  
 <span data-ttu-id="202bc-109">RE_Admin_Users SQL Server 角色適用於需要在商務規則引擎中執行系統管理工作 (例如部署規則) 的使用者。</span><span class="sxs-lookup"><span data-stu-id="202bc-109">The RE_Admin_Users SQL Server role is for users that need to perform administrative tasks in the Business Rule Engine, such as deploying rules.</span></span> <span data-ttu-id="202bc-110">RE_Admin_Users SQL Server  角色的成員包括 BizTalk 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="202bc-110">Members of the RE_Admin_Users SQL Server role include BizTalk administrators.</span></span>  
  
 <span data-ttu-id="202bc-111">RE_Host_Users 群組適用於不需要系統管理使用者權限，而只需執行讀取及執行規則等工作的其他所有商務規則引擎使用者。</span><span class="sxs-lookup"><span data-stu-id="202bc-111">The RE_Host_Users group is for all other users of the Business Rule Engine that do not require administrative user rights, and perform tasks such as reading and executing rules.</span></span> <span data-ttu-id="202bc-112">RE_Host_Users 角色的成員包括 BizTalk_Host_Users 角色。</span><span class="sxs-lookup"><span data-stu-id="202bc-112">Members of the RE_Host_Users role include the BizTalk_Host_Users role.</span></span> <span data-ttu-id="202bc-113">您可以使用 SQL Server 角色，實作商務規則引擎的權限，而不受 BizTalk Server 權限的影響。</span><span class="sxs-lookup"><span data-stu-id="202bc-113">You can use the SQL Server roles to implement permissions to the Business Rule Engine independent from the BizTalk Server permissions.</span></span> <span data-ttu-id="202bc-114">如需有關使用 「 商務規則引擎所需的最低權限的詳細資訊，請參閱 <<c0> [ 最小安全性使用者權限](../core/minimum-security-user-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="202bc-114">For more information about the minimum permission needed to use the Business Rule Engine, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).</span></span> <span data-ttu-id="202bc-115">建議您依照下列指導方針來保護和部署您作業環境中的商務規則引擎執行階段。</span><span class="sxs-lookup"><span data-stu-id="202bc-115">It is recommended you follow these guidelines for securing and deploying the Business Rule Engine in your environment.</span></span>  
  
-   <span data-ttu-id="202bc-116">BizTalk Server 提供帳戶供您用來將更新服務登入安裝成服務權限，而且會將該帳戶新增到商務規則引擎資料庫上的 RE_Host_Users SQL Server 角色中。</span><span class="sxs-lookup"><span data-stu-id="202bc-116">BizTalk Server gives the account you used to install the update service logon as service rights and adds it to the RE_Host_Users SQL Server role on the Business Rule Engine database.</span></span> <span data-ttu-id="202bc-117">如果您用來安裝的帳戶與要用來執行更新服務的帳戶不同，您必須從 RE_Host_Users SQL Server 角色中移除安裝帳戶。</span><span class="sxs-lookup"><span data-stu-id="202bc-117">If the account you use for installation is not the same you are going to use for running the update service, you must remove the installation account from the RE_Host_Users SQL Server role.</span></span>  

-   <span data-ttu-id="202bc-118">如果您不使用另一個 BizTalk 主控件服務帳戶相同的帳戶，也新增規則引擎服務帳戶在 BizTalkMgmtDb 和 BizTalkMsgBoxDb BTS_HOST_USERS。</span><span class="sxs-lookup"><span data-stu-id="202bc-118">If you don't use the same account as another BizTalk host service account, also add the RuleEngine service account to BTS_HOST_USERS in BizTalkMgmtDb and BizTalkMsgBoxDb.</span></span>

-   <span data-ttu-id="202bc-119">如果要使用更新服務元件，您必須將它安裝在所有 BizTalk 執行階段元件上。</span><span class="sxs-lookup"><span data-stu-id="202bc-119">If you use the Update service component, you must install it on all BizTalk runtime computers.</span></span> <span data-ttu-id="202bc-120">為了從規則引擎資料庫擷取規則，更新服務會模擬服務的呼叫者。</span><span class="sxs-lookup"><span data-stu-id="202bc-120">In order to retrieve a rule from the Rule Engine database, the update service impersonates the caller of the service.</span></span>  
  
-   <span data-ttu-id="202bc-121">根據預設，所有的 BizTalk 主控件對規則引擎成品都擁有的相同的存取層次。</span><span class="sxs-lookup"><span data-stu-id="202bc-121">By default, all BizTalk Hosts have the same level of access to rules engine artifacts.</span></span> <span data-ttu-id="202bc-122">個別主控件並沒有獨立的安全性。</span><span class="sxs-lookup"><span data-stu-id="202bc-122">There is not per-host segregation of security.</span></span> <span data-ttu-id="202bc-123">您可以使用規則引擎 API 設定個別原則的安全性。</span><span class="sxs-lookup"><span data-stu-id="202bc-123">You can configure per-policy security by using the rule engine APIs.</span></span> <span data-ttu-id="202bc-124">如需如何設定個別原則安全性的詳細資訊，請參閱[商務規則架構安全性](../core/business-rules-framework-security.md)。</span><span class="sxs-lookup"><span data-stu-id="202bc-124">For more information about how to configure per-policy security, see [Business Rules Framework Security](../core/business-rules-framework-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="202bc-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="202bc-125">See Also</span></span>  
 [<span data-ttu-id="202bc-126">處理伺服器的連接埠</span><span class="sxs-lookup"><span data-stu-id="202bc-126">Ports for the Processing Servers</span></span>](../core/ports-for-the-processing-servers.md)
