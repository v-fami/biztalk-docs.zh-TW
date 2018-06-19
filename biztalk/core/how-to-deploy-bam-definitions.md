---
title: 如何部署 BAM 定義 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, definitions [BAM]
- managing [BAM definitions], deploying definitions
- definitions [BAM], deploying
- Deploy-All command [BAM]
ms.assetid: 02b8888c-6f6c-45dd-8445-6e507a02f5f0
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 094a37d90db41e505adeaec3a31ece9128785e04
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970734"
---
# <a name="how-to-deploy-bam-definitions"></a><span data-ttu-id="a5041-102">如何部署 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="a5041-102">How to Deploy BAM Definitions</span></span>
<span data-ttu-id="a5041-103">系統管理員使用**deploy-all-definitionfile**從活頁簿匯出 BAM 管理公用程式命令，以部署 BAM 定義從 Excel 活頁簿或 XML 定義檔。</span><span class="sxs-lookup"><span data-stu-id="a5041-103">Administrators use the **deploy-all** BAM Management utility command to deploy a BAM definition from the Excel workbook or the XML definitions file exported from the workbook.</span></span> <span data-ttu-id="a5041-104">當您執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 完整安裝時，組態精靈會自動設定 BAM 組態 XML。</span><span class="sxs-lookup"><span data-stu-id="a5041-104">When you perform a complete installation of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the Configuration Wizard automatically configures the BAM Configuration XML.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5041-105">若有多個使用者使用 Excel 的 BAM 增益集，則建議使用相同版本的 Microsoft Data Access Components (MDAC)。</span><span class="sxs-lookup"><span data-stu-id="a5041-105">If multiple users are working with the BAM Add-In for Excel, we recommend that they have the same version of Microsoft Data Access Components (MDAC).</span></span> <span data-ttu-id="a5041-106">否則可能會有相容性的問題。</span><span class="sxs-lookup"><span data-stu-id="a5041-106">Otherwise, compatibility issues may arise.</span></span> <span data-ttu-id="a5041-107">特別是，如果您在安裝 MDAC 較新版本的電腦上建立範本，然後嘗試在安裝舊版 MDAC 的電腦上開啟該範本，就會發生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="a5041-107">Specifically, if you create a template on a computer with a newer version of MDAC and then attempt to open it on a computer with an older version of MDAC, a compiler error will occur.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5041-108">每個資料維度 (例如「位置」) 只能使用一個資料項目 (例如「縣/市」)。</span><span class="sxs-lookup"><span data-stu-id="a5041-108">You can use only one data item (for example, City) per data dimension (for example, Location).</span></span> <span data-ttu-id="a5041-109">其他的資料維度 (例如「地區」) 便不能再使用「縣/市」。</span><span class="sxs-lookup"><span data-stu-id="a5041-109">You cannot use City again in another data dimension, such as Region.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a5041-110">建議您在部署 BAM Excel 活頁簿 (.xls) 前先確認其安全性。</span><span class="sxs-lookup"><span data-stu-id="a5041-110">We recommend that you verify the security of BAM Excel workbooks (.xls) before you deploy them.</span></span> <span data-ttu-id="a5041-111">請使用管理電腦上的 Excel 確認 BAM Excel 活頁簿的安全性。</span><span class="sxs-lookup"><span data-stu-id="a5041-111">You use Excel on the administration computer to verify the security of BAM Excel workbooks.</span></span> <span data-ttu-id="a5041-112">在部署活頁簿之前，請先開啟活頁簿，確定巨集安全性設定為「高」，而且沒有出現任何警告。</span><span class="sxs-lookup"><span data-stu-id="a5041-112">Before you deploy a workbook, open it and ensure the macro security is set to high, and that there are no warnings.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a5041-113">在 BAM 資料庫中，"BAM_\<...\>"命名慣例保留供所有 SQL 實體 (資料表、 索引、 預存程序、 角色等等.)。*不這麼做*使用此命名慣例來建立任何 SQL 實體; 這樣的使用方式可能會導致未定義的行為。</span><span class="sxs-lookup"><span data-stu-id="a5041-113">In BAM databases, the “BAM_\<...\>” naming convention is reserved for all SQL entities (tables, indexes, stored procedures, roles, etc...). *Do not* use this naming convention to create any SQL entities; such a usage might result in an undefined behavior.</span></span>  
  
 <span data-ttu-id="a5041-114">在部署 BAM 定義 XML 檔之前，您必須確定用於建立該檔案的地區設定與部署所用之電腦的地區設定一致。</span><span class="sxs-lookup"><span data-stu-id="a5041-114">Before you can deploy a BAM definition XML file, you must ensure that the locale used to create this file matches the locale of the computer on which you are deploying it.</span></span> <span data-ttu-id="a5041-115">例如，如果您在執行 Microsoft Windows 日文版的電腦上建立檔案，則部署檔案的電腦地區設定也必須設為日文。</span><span class="sxs-lookup"><span data-stu-id="a5041-115">For example, if you create the file on a computer running a Japanese version of Microsoft Windows, the computer you deploy the file on must be set to the Japanese locale.</span></span> <span data-ttu-id="a5041-116">如果檔案和電腦的設定不一致，請將您用來執行 BAM 管理公用程式的電腦切換到正確的地區設定，並在執行公用程式之前重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="a5041-116">If the file and the computer settings do not match, you must switch the computer you use to run the BAM Management utility to the correct locale and you must restart it before running the utility.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5041-117">除非所有的語言都使用相同的字碼頁，或只使用兩種語言且其中之一為英文，否則 BAM 定義 XML 檔不可包含多種語言的文字。</span><span class="sxs-lookup"><span data-stu-id="a5041-117">The BAM definition XML file cannot contain text in multiple languages unless the languages all use the same codepage, or only two languages are included and one of them is English.</span></span>  
  
 <span data-ttu-id="a5041-118">如需有關變更電腦地區設定的詳細資訊，請參閱作業系統的「說明」。</span><span class="sxs-lookup"><span data-stu-id="a5041-118">For information about changing locale settings on your computer, see the Help for your operating system.</span></span>  
  
### <a name="to-deploy-a-bam-definition"></a><span data-ttu-id="a5041-119">部署 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="a5041-119">To deploy a BAM definition</span></span>  
  
1.  <span data-ttu-id="a5041-120">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="a5041-120">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="a5041-121">瀏覽至追蹤資料夾，輸入**C:\Program Files\Microsoft BizTalk Server\<版本\>\Tracking**在命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="a5041-121">Navigate to the tracking folder by typing **C:\Program Files\Microsoft BizTalk Server \<version\>\Tracking** at the command prompt.</span></span> <span data-ttu-id="a5041-122">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="a5041-122">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="a5041-123">型別**bm deploy-all-definitionfile-DefinitionFile:\<BAM 定義檔案\>**。</span><span class="sxs-lookup"><span data-stu-id="a5041-123">Type **bm deploy-all -DefinitionFile:\<BAM definition file\>**.</span></span>  
  
4.  <span data-ttu-id="a5041-124">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="a5041-124">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5041-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="a5041-125">See Also</span></span>  
 <span data-ttu-id="a5041-126">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="a5041-126">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="a5041-127">[BAM 管理公用程式](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="a5041-127">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="a5041-128">BAM 安全性建議</span><span class="sxs-lookup"><span data-stu-id="a5041-128">BAM Security Recommendations</span></span>](../core/bam-security-recommendations.md)