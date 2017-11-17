---
title: "如何匯入和匯出原則和詞彙 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, exporting
- Rule Engine Deployment Wizard
- policies, importing
- vocabularies, exporting
- vocabularies, importing
ms.assetid: c427f686-5908-4f72-9e72-46a5497274ac
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17ba7cd8a9fc5d28d1b718e9a47ad6cf2f448ec7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-import-and-export-policies-and-vocabularies"></a><span data-ttu-id="06c41-102">如何匯入和匯出原則和詞彙</span><span class="sxs-lookup"><span data-stu-id="06c41-102">How to Import and Export Policies and Vocabularies</span></span>
<span data-ttu-id="06c41-103">您可以使用 [規則引擎部署精靈] 來匯入或匯出原則或詞彙。</span><span class="sxs-lookup"><span data-stu-id="06c41-103">You can use the Rules Engine Deployment Wizard to import or export a policy or vocabulary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06c41-104">原則或詞彙使用的所有詞彙都必須先行匯入，否則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="06c41-104">All vocabularies used by a policy or vocabulary must be imported first or you will get an error.</span></span>  
  
### <a name="to-import-or-export-a-policy-or-vocabulary"></a><span data-ttu-id="06c41-105">若要匯入或匯出原則或詞彙</span><span class="sxs-lookup"><span data-stu-id="06c41-105">To import or export a policy or vocabulary</span></span>  
  
1.  <span data-ttu-id="06c41-106">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下 **商務規則引擎部署精靈**。</span><span class="sxs-lookup"><span data-stu-id="06c41-106">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Business Rules Engine Deployment Wizard**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="06c41-107">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="06c41-107">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="06c41-108">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="06c41-108">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="06c41-109">在 歡迎使用 頁面上，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="06c41-109">On the welcome page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="06c41-110">在**部署工作**頁面上，選取 **匯出原則/詞彙至檔案從資料庫**或**匯入並發佈原則/詞彙至資料庫，從檔案**，然後按一下按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="06c41-110">On the **Deployment Task** page, select either **Export Policy/Vocabulary to file from database** or **Import and publish Policy/Vocabulary to database from file**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="06c41-111">在**原則存放區**頁面上，從下拉式清單中，選取 可用的 SQL Server 電腦和資料庫，然後再按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="06c41-111">On the **Policy Store** page, from the drop-down lists, select an available SQL Server computer and database, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="06c41-112">在**匯出原則/詞彙**頁面上，執行下列工作，，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="06c41-112">On the **Export Policy/Vocabulary** page, do the following, and then click **Next**.</span></span>  
  
    1.  <span data-ttu-id="06c41-113">選取**原則**或**詞彙**根據想要匯出/匯入。</span><span class="sxs-lookup"><span data-stu-id="06c41-113">Select **Policy** or **Vocabulary** depending on what you want to export/import.</span></span>  
  
    2.  <span data-ttu-id="06c41-114">從**原則/詞彙**下拉式清單中，選取所需的原則/詞彙。</span><span class="sxs-lookup"><span data-stu-id="06c41-114">From the **Policy/Vocabulary** drop-down list, select the desired policy/vocabulary.</span></span>  
  
    3.  <span data-ttu-id="06c41-115">按一下**瀏覽**選取的定義檔。</span><span class="sxs-lookup"><span data-stu-id="06c41-115">Click **Browse** to select the definition file.</span></span>  
  
6.  <span data-ttu-id="06c41-116">檢閱伺服器、 資料庫及原則或詞彙資訊，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="06c41-116">Review the server, database, and policy or vocabulary information, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="06c41-117">匯入或匯出完成之後，請按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="06c41-117">After the import or export is completed, click **Next**.</span></span>  
  
8.  <span data-ttu-id="06c41-118">檢閱匯入或匯出的完成狀態，然後按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="06c41-118">Review the completion status of the import or export, and then click **Finish**.</span></span>