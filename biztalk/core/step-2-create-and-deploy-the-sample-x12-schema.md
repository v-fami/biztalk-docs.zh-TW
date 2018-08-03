---
title: 步驟 2： 建立和部署範例 X12 結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5862168-6621-40ab-8c97-3f317530d34e
caps.latest.revision: 31
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 671a2ce81946b2d2e4bd4125f8b236740f566f72
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968199"
---
# <a name="step-2-create-and-deploy-the-sample-x12-schema"></a><span data-ttu-id="c2faa-102">步驟 2： 建立和部署範例 X12 結構描述</span><span class="sxs-lookup"><span data-stu-id="c2faa-102">Step 2: Create and Deploy the Sample X12 Schema</span></span>
<span data-ttu-id="c2faa-103">![步驟 11-2](../core/media/tut-step2-of-11.gif "Tut_Step2_of_11")</span><span class="sxs-lookup"><span data-stu-id="c2faa-103">![Step 2 of 11](../core/media/tut-step2-of-11.gif "Tut_Step2_of_11")</span></span>  
  
 <span data-ttu-id="c2faa-104">在此步驟中，您將建置和部署可提供範例 EDI X12 結構描述的專案，該結構描述是處理透過 AS2 傳輸之內送 EDI X12 交換的必要項目。</span><span class="sxs-lookup"><span data-stu-id="c2faa-104">In this step, you build and deploy the project that provides a sample EDI X12 schema that is required to process the incoming EDI X12 interchange transported over AS2.</span></span> <span data-ttu-id="c2faa-105">在本教學課程中，該結構描述為 X12_00401_864.xsd。</span><span class="sxs-lookup"><span data-stu-id="c2faa-105">For this tutorial, that schema is X12_00401_864.xsd.</span></span> <span data-ttu-id="c2faa-106">您不必變更 AS2 教學課程隨附的專案，只要直接建置即可。</span><span class="sxs-lookup"><span data-stu-id="c2faa-106">You do not need to change the project that is shipped with the AS2 tutorial; you just need to build it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2faa-107">本教學課程使用的結構描述檔 X12_00401_864.xsd 是儲存在 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Schemas 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="c2faa-107">The schema file X12_00401_864.xsd that this tutorial uses is stored in the folder [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Schemas.</span></span> <span data-ttu-id="c2faa-108">它已經加入到您將在此步驟中建置和部署的 Schemas 專案內。</span><span class="sxs-lookup"><span data-stu-id="c2faa-108">It has already been added to the Schemas project that you will build and deploy in this step.</span></span> <span data-ttu-id="c2faa-109">此結構描述不同於執行 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI 資料夾中的 MicrosoftEdiXsdTemplates	.exe 時下載到電腦上的 X12_00401_864.xsd 檔案。</span><span class="sxs-lookup"><span data-stu-id="c2faa-109">This schema is different from the X12_00401_864.xsd file downloaded onto your computer by executing MicrosoftEdiXsdTemplates.exe in the folder [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI.</span></span> <span data-ttu-id="c2faa-110">您必須使用已加入到 Schemas.btproj 中的 X12_00401_864.xsd 檔案，才可以執行本教學課程。</span><span class="sxs-lookup"><span data-stu-id="c2faa-110">The tutorial will only work if you use the X12_00401_864.xsd file that has been added to Schemas.btproj.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c2faa-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="c2faa-111">Prerequisites</span></span>  
 <span data-ttu-id="c2faa-112">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="c2faa-112">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-create-and-deploy-the-sample-x12-schema"></a><span data-ttu-id="c2faa-113">若要建立和部署範例 X12 結構描述</span><span class="sxs-lookup"><span data-stu-id="c2faa-113">To create and deploy the sample X12 schema</span></span>  
  
1. <span data-ttu-id="c2faa-114">開始**Microsoft Visual Studio**身為系統管理員。</span><span class="sxs-lookup"><span data-stu-id="c2faa-114">Start **Microsoft Visual Studio** as an administrator.</span></span>  
  
2. <span data-ttu-id="c2faa-115">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟解決方案 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Schemas\Schemas.sln。</span><span class="sxs-lookup"><span data-stu-id="c2faa-115">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Schemas\Schemas.sln.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="c2faa-116">本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)，</span><span class="sxs-lookup"><span data-stu-id="c2faa-116">This topic assumes that you have already added a reference from your application to the BizTalk EDI Application, which contains EDI schemas, pipelines, and orchestrations.</span></span> <span data-ttu-id="c2faa-117">如果沒有，請參閱[如何將參考加入 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。</span><span class="sxs-lookup"><span data-stu-id="c2faa-117">If not, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span></span>  
  
3. <span data-ttu-id="c2faa-118">以滑鼠右鍵按一下 [Schemas] 專案，然後**屬性**。</span><span class="sxs-lookup"><span data-stu-id="c2faa-118">Right-click the Schemas project, and then click **Properties**.</span></span> <span data-ttu-id="c2faa-119">按一下 **簽署**專案設計工具中的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c2faa-119">Click the **Signing** tab in project designer.</span></span> <span data-ttu-id="c2faa-120">請檢查**簽署組件**核取方塊，如**選擇強式金鑰名稱檔**，選取**\<新增...\>**  ，然後輸入`Schemas.snk`。</span><span class="sxs-lookup"><span data-stu-id="c2faa-120">Check the **Sign the Assembly** checkbox, for **Choose a strong key name file**, select **\<New…\>** and enter `Schemas.snk`.</span></span> <span data-ttu-id="c2faa-121">清除**保護我的金鑰檔使用密碼**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c2faa-121">Clear **Protect my key file with a password** and then click **OK**.</span></span> <span data-ttu-id="c2faa-122">關閉專案屬性對話方塊並儲存所做的變更。</span><span class="sxs-lookup"><span data-stu-id="c2faa-122">Close the project properties dialog and save the changes.</span></span>  
  
4. <span data-ttu-id="c2faa-123">建置並部署 Schemas.btproj。</span><span class="sxs-lookup"><span data-stu-id="c2faa-123">Build and deploy Schemas.btproj.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c2faa-124">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c2faa-124">Next Steps</span></span>  
 <span data-ttu-id="c2faa-125">中所述，為您的組織 (Contoso)，設定合作對象與商務設定檔[步驟 3： 為您的組織設定合作對象和商務設定檔](../core/step-3-configure-a-party-and-business-profile-for-your-organization2.md)。</span><span class="sxs-lookup"><span data-stu-id="c2faa-125">You configure a party and business profile for your organization (Contoso), as described in [Step 3: Configure a Party and Business Profile for Your Organization](../core/step-3-configure-a-party-and-business-profile-for-your-organization2.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2faa-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2faa-126">See Also</span></span>  
 [<span data-ttu-id="c2faa-127">EDI 文件結構描述</span><span class="sxs-lookup"><span data-stu-id="c2faa-127">EDI Document Schemas</span></span>](../core/edi-document-schemas.md)