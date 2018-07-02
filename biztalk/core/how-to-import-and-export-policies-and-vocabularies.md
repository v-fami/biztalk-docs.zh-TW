---
title: 如何匯入和匯出原則和詞彙 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- policies, exporting
- Rule Engine Deployment Wizard
- policies, importing
- vocabularies, exporting
- vocabularies, importing
ms.assetid: c427f686-5908-4f72-9e72-46a5497274ac
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1bb235d126ca775cc8bd5a752388c948a2203e4b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968839"
---
# <a name="how-to-import-and-export-policies-and-vocabularies"></a><span data-ttu-id="7e57f-102">如何匯入和匯出原則和詞彙</span><span class="sxs-lookup"><span data-stu-id="7e57f-102">How to Import and Export Policies and Vocabularies</span></span>
<span data-ttu-id="7e57f-103">您可以使用 [規則引擎部署精靈] 來匯入或匯出原則或詞彙。</span><span class="sxs-lookup"><span data-stu-id="7e57f-103">You can use the Rules Engine Deployment Wizard to import or export a policy or vocabulary.</span></span>  

> [!NOTE]
>  <span data-ttu-id="7e57f-104">原則或詞彙使用的所有詞彙都必須先行匯入，否則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7e57f-104">All vocabularies used by a policy or vocabulary must be imported first or you will get an error.</span></span>  

### <a name="to-import-or-export-a-policy-or-vocabulary"></a><span data-ttu-id="7e57f-105">若要匯入或匯出原則或詞彙</span><span class="sxs-lookup"><span data-stu-id="7e57f-105">To import or export a policy or vocabulary</span></span>  

1. <span data-ttu-id="7e57f-106">按一下 **開始**，指向**所有程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**商務規則引擎部署精靈**。</span><span class="sxs-lookup"><span data-stu-id="7e57f-106">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Business Rules Engine Deployment Wizard**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="7e57f-107">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="7e57f-107">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="7e57f-108">若要這樣做，以滑鼠右鍵按一下 應用程式，然後按**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="7e57f-108">To do this, right-click the application, and then select **Run as administrator**.</span></span>  

2. <span data-ttu-id="7e57f-109">在 歡迎使用 頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="7e57f-109">On the welcome page, click **Next**.</span></span>  

3. <span data-ttu-id="7e57f-110">上**部署工作**頁面上，選取**匯出原則/詞彙至檔案從資料庫**或是**匯入並發佈原則/詞彙至資料庫，從檔案**，然後按一下 [**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="7e57f-110">On the **Deployment Task** page, select either **Export Policy/Vocabulary to file from database** or **Import and publish Policy/Vocabulary to database from file**, and then click **Next**.</span></span>  

4. <span data-ttu-id="7e57f-111">在 **原則存放區**頁面上，從下拉式清單中，選取可用的 SQL Server 電腦和資料庫，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="7e57f-111">On the **Policy Store** page, from the drop-down lists, select an available SQL Server computer and database, and then click **Next**.</span></span>  

5. <span data-ttu-id="7e57f-112">在 **匯出原則/詞彙**頁面上，執行下列作業，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="7e57f-112">On the **Export Policy/Vocabulary** page, do the following, and then click **Next**.</span></span>  

   1.  <span data-ttu-id="7e57f-113">選取 **原則**或是**詞彙**取決於您想要匯出/匯入。</span><span class="sxs-lookup"><span data-stu-id="7e57f-113">Select **Policy** or **Vocabulary** depending on what you want to export/import.</span></span>  

   2.  <span data-ttu-id="7e57f-114">從**原則/詞彙**下拉式清單中，選取所需的原則/詞彙。</span><span class="sxs-lookup"><span data-stu-id="7e57f-114">From the **Policy/Vocabulary** drop-down list, select the desired policy/vocabulary.</span></span>  

   3.  <span data-ttu-id="7e57f-115">按一下 **瀏覽**選取的定義檔。</span><span class="sxs-lookup"><span data-stu-id="7e57f-115">Click **Browse** to select the definition file.</span></span>  

6. <span data-ttu-id="7e57f-116">檢閱伺服器、 資料庫及原則或詞彙的詳細資訊，，然後按**下一步**。</span><span class="sxs-lookup"><span data-stu-id="7e57f-116">Review the server, database, and policy or vocabulary information, and then click **Next**.</span></span>  

7. <span data-ttu-id="7e57f-117">匯入或匯出完成後，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="7e57f-117">After the import or export is completed, click **Next**.</span></span>  

8. <span data-ttu-id="7e57f-118">檢閱匯入或匯出的完成狀態，然後按**完成**。</span><span class="sxs-lookup"><span data-stu-id="7e57f-118">Review the completion status of the import or export, and then click **Finish**.</span></span>
