---
title: SSO 部署概觀 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSO, deploying example
- SSO, deploying
- deploying, SSO
- SSO, multiple computers
- examples, deploying
ms.assetid: 6eccee26-c392-41fe-97fb-3afe1685540f
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c98a12c11ae735945f4e69631e7211c05c0b9186
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022364"
---
# <a name="sso-deployment-overview"></a><span data-ttu-id="f69ac-102">SSO 部署概觀</span><span class="sxs-lookup"><span data-stu-id="f69ac-102">SSO Deployment Overview</span></span>
<span data-ttu-id="f69ac-103">此範例中的系統是部署在包含下列電腦的三個網域中：</span><span class="sxs-lookup"><span data-stu-id="f69ac-103">The system in this example is deployed over three domains, containing the following computers:</span></span>  
  
 <span data-ttu-id="f69ac-104">**網域 ORCH.com**</span><span class="sxs-lookup"><span data-stu-id="f69ac-104">**Domain ORCH.com**</span></span>  
  
- <span data-ttu-id="f69ac-105">ORCH 網域控制站</span><span class="sxs-lookup"><span data-stu-id="f69ac-105">ORCH domain controller</span></span>  
  
- <span data-ttu-id="f69ac-106">HIS1、HISSO 伺服器</span><span class="sxs-lookup"><span data-stu-id="f69ac-106">HIS1, the HISSO server</span></span>  
  
- <span data-ttu-id="f69ac-107">HIS2、主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="f69ac-107">HIS2, the Master Secret Server</span></span>  
  
- <span data-ttu-id="f69ac-108">HIS3、管理資料庫</span><span class="sxs-lookup"><span data-stu-id="f69ac-108">HIS3, the Admin database</span></span>  
  
  <span data-ttu-id="f69ac-109">**網域 SQL.com**</span><span class="sxs-lookup"><span data-stu-id="f69ac-109">**Domain SQL.com**</span></span>  
  
- <span data-ttu-id="f69ac-110">SQL 網域控制站</span><span class="sxs-lookup"><span data-stu-id="f69ac-110">SQL domain controller</span></span>  
  
- <span data-ttu-id="f69ac-111">SQL2、SSO 資料庫</span><span class="sxs-lookup"><span data-stu-id="f69ac-111">SQL2, the SSO database</span></span>  
  
  <span data-ttu-id="f69ac-112">**網域 HIS.com**</span><span class="sxs-lookup"><span data-stu-id="f69ac-112">**Domain HIS.com**</span></span>  
  
- <span data-ttu-id="f69ac-113">HIS 網域控制站</span><span class="sxs-lookup"><span data-stu-id="f69ac-113">HIS domain controller</span></span>  
  
- <span data-ttu-id="f69ac-114">HIS4 資料庫</span><span class="sxs-lookup"><span data-stu-id="f69ac-114">HIS4 database</span></span>  
  
  <span data-ttu-id="f69ac-115">定義此部署的重點如下：</span><span class="sxs-lookup"><span data-stu-id="f69ac-115">The key points defining this deployment are as follows:</span></span>  
  
- <span data-ttu-id="f69ac-116">網域 ORCH.com 和網域 SQL.com 有一個雙向選擇性信任關係。</span><span class="sxs-lookup"><span data-stu-id="f69ac-116">Domain ORCH.com and domain SQL.com have a two-way selective trust relationship.</span></span>  
  
- <span data-ttu-id="f69ac-117">網域 ORCH.com 設定成原生 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 或 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] 功能等級。</span><span class="sxs-lookup"><span data-stu-id="f69ac-117">Domain ORCH.com is configured as native [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] functional level.</span></span>  
  
- <span data-ttu-id="f69ac-118">所有 SSO 服務都是在 ORCH.com 網域使用者帳戶執行 (Orch\SSOSvcUser)。</span><span class="sxs-lookup"><span data-stu-id="f69ac-118">All SSO services are running on an ORCH.com domain user account (Orch\SSOSvcUser).</span></span> <span data-ttu-id="f69ac-119">使用者設定成擁有 SQL.com 網域中 SQL2 機器的存取權限。</span><span class="sxs-lookup"><span data-stu-id="f69ac-119">The user is configured to have access permission on the SQL2 machine in the SQL.com domain.</span></span> <span data-ttu-id="f69ac-120">會為 ORCH.com 網域中的通訊協定轉換和限制委派設定使用者。</span><span class="sxs-lookup"><span data-stu-id="f69ac-120">The user is configured for protocol transition and constrain delegation within the ORCH.com domain.</span></span>  
  
- <span data-ttu-id="f69ac-121">會為執行測試程式而設定其他 ORCH.com 網域使用者 (Orch\TestAppUser)。</span><span class="sxs-lookup"><span data-stu-id="f69ac-121">Another ORCH.com domain user (Orch\TestAppUser) is set for running test programs.</span></span> <span data-ttu-id="f69ac-122">也會為通訊協定轉換和限制委派設定此使用者。</span><span class="sxs-lookup"><span data-stu-id="f69ac-122">This user is also configured for protocol transition and constrain delegation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f69ac-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f69ac-123">See Also</span></span>  
 [<span data-ttu-id="f69ac-124">部署程序</span><span class="sxs-lookup"><span data-stu-id="f69ac-124">Deployment Process</span></span>](../core/deployment-process.md)