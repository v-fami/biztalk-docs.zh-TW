---
title: 如何啟動 「 商務規則編輯器 」 和載入原則 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- policies, loading
- opening, Busines Rule Composer
- Business Rule Composer, policies
- Business Rule Composer, opening
ms.assetid: 34a6034d-90b3-4ce0-9770-3790763affe3
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e56d3d2c1dde771d86f8de345d6e3b249ab394b8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977047"
---
# <a name="how-to-start-the-business-rule-composer-and-load-a-policy"></a><span data-ttu-id="d5f58-102">如何啟動 「 商務規則編輯器 」 和載入原則</span><span class="sxs-lookup"><span data-stu-id="d5f58-102">How to Start the Business Rule Composer and Load a Policy</span></span>
<span data-ttu-id="d5f58-103">本節描述如何啟動「商務規則編輯器」和載入原則。</span><span class="sxs-lookup"><span data-stu-id="d5f58-103">This section describes how to start the Business Rule Composer and load a policy.</span></span>  
  
### <a name="to-start-the-business-rule-composer"></a><span data-ttu-id="d5f58-104">啟動商務規則編輯器</span><span class="sxs-lookup"><span data-stu-id="d5f58-104">To start the Business Rule Composer</span></span>  
  
- <span data-ttu-id="d5f58-105">在上**啟動**功能表上，指向**所有程式**，指向 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，然後按一下**商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="d5f58-105">On the **Start** menu, point to **All Programs**, point to Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and then click **Business Rule Composer**.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="d5f58-106">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="d5f58-106">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="d5f58-107">若要這樣做，以滑鼠右鍵按一下 應用程式，然後按**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="d5f58-107">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
### <a name="to-load-a-policy"></a><span data-ttu-id="d5f58-108">載入原則</span><span class="sxs-lookup"><span data-stu-id="d5f58-108">To load a policy</span></span>  
  
1.  <span data-ttu-id="d5f58-109">在 「 商務規則編輯器 」 中，在**規則存放區**功能表上，按一下**負載**。</span><span class="sxs-lookup"><span data-stu-id="d5f58-109">In the Business Rule Composer, on the **Rule Store** menu, click **Load**.</span></span>  
  
2.  <span data-ttu-id="d5f58-110">在 **規則存放區**對話方塊中，於**SQL Server**下拉式清單中，選取您要連接的 SQL Server™ 電腦。</span><span class="sxs-lookup"><span data-stu-id="d5f58-110">In the **Rule Store** dialog box, in the **SQL Server** drop-down list, select the SQL Server™ computer to which you want to connect.</span></span>  
  
3.  <span data-ttu-id="d5f58-111">在 **資料庫**下拉式清單中，選取包含您想要開啟規則存放區的資料庫。</span><span class="sxs-lookup"><span data-stu-id="d5f58-111">In the **Database** drop-down list, select the database that contains the rule store you want to open.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5f58-112">規則存放區所安裝的預設資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]已**BizTalkRuleEngineDb**。</span><span class="sxs-lookup"><span data-stu-id="d5f58-112">The default database for the rule store installed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is **BizTalkRuleEngineDb**.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="d5f58-113">如果您使用新建立的 SQL Server 帳戶具有**強制執行密碼逾期**並**使用者必須變更密碼在下次登入時**選項集，「 商務規則編輯器 」 會無法連線到規則引擎 」 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d5f58-113">If you use a newly created SQL Server account that has the **Enforce password expiration** and **User must change password at next login** options set, the business rule composer will fail to connect to the Rule Engine database.</span></span>