---
title: 取代公開金鑰權杖公用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Replace Public Key Token Utility
- utilities, Replace Public Key Token Utility
- public key token
ms.assetid: ed8673b9-af06-4bd7-b8b7-7371e4dd0fed
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d546a01d615dbd6dd8146d186e484addcef200b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996279"
---
# <a name="replace-public-key-token-utility"></a><span data-ttu-id="27bf7-102">取代公開金鑰 Token 公用程式</span><span class="sxs-lookup"><span data-stu-id="27bf7-102">Replace Public Key Token Utility</span></span>
<span data-ttu-id="27bf7-103">這個公用程式可使用衍生自強式名稱組件金鑰 (.snk) 檔案的公開金鑰 Token 來取代檔案中的公開金鑰 Token 或變數。</span><span class="sxs-lookup"><span data-stu-id="27bf7-103">This utility can be used to replace either a public key token or variable in a file with a public key token derived from a strong name assembly key (.snk) file.</span></span>  
  
 <span data-ttu-id="27bf7-104">當開發人員在撰寫使用的指令碼時，此公用程式可能會很有用[BTSTask 命令列參考](../core/btstask-command-line-reference.md)部署組件。</span><span class="sxs-lookup"><span data-stu-id="27bf7-104">This utility might be useful when a developer is writing a script that uses the [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md) to deploy an assembly.</span></span> <span data-ttu-id="27bf7-105">部署若要成功，就必須提供組件的完整格式名稱，其中會包含其公開金鑰 Token。</span><span class="sxs-lookup"><span data-stu-id="27bf7-105">For the deployment to succeed, the fully qualified name of the assembly must be provided, which includes its public key token.</span></span> <span data-ttu-id="27bf7-106">組件的公開金鑰 Token 是擷取自 .snk 檔案，並且會在建立時指派給組件。</span><span class="sxs-lookup"><span data-stu-id="27bf7-106">The public key token for an assembly is extracted from an .snk file and assigned to the assembly when it is built.</span></span> <span data-ttu-id="27bf7-107">不過，組件在部署到新環境之前，常使用不同的公開金鑰 Token 重新建置。</span><span class="sxs-lookup"><span data-stu-id="27bf7-107">Before the assembly is deployed into a new environment, however, it is often rebuilt using a different public key token.</span></span> <span data-ttu-id="27bf7-108">因此，開發人員可能不知道在部署指令碼執行時，會為組件使用哪一個公開金鑰 Token。</span><span class="sxs-lookup"><span data-stu-id="27bf7-108">As a result, the developer may not know what public key token will be used for the assembly when the deployment script is run.</span></span>  
  
 <span data-ttu-id="27bf7-109">您可透過兩種方式來使用「取代公開金鑰 Token」公用程式解決這種狀況：</span><span class="sxs-lookup"><span data-stu-id="27bf7-109">There are two ways that you can use the Replace Public Key Token utility to address this situation:</span></span>  
  
-   <span data-ttu-id="27bf7-110">**案例 1。**</span><span class="sxs-lookup"><span data-stu-id="27bf7-110">**Scenario 1.**</span></span> <span data-ttu-id="27bf7-111">在部署指令碼中，開發人員可以使用公開金鑰 Token 或代表公開金鑰 Token 的預留位置。</span><span class="sxs-lookup"><span data-stu-id="27bf7-111">In the deployment script, the developer can use either a public key token or a placeholder representing the public key token.</span></span> <span data-ttu-id="27bf7-112">在執行指令碼之前，使用者可以執行「取代公開金鑰 Token」公用程式，以擷取自 .snk 檔案的公開金鑰 Token 來取代指令碼檔案中的公開金鑰 Token 或預留位置 (.snk 檔案是用來建置目的環境的組件)。</span><span class="sxs-lookup"><span data-stu-id="27bf7-112">Before running the script, a user can run the Replace Public Key Token utility to substitute the public key token or placeholder in the script file with the public key token extracted from the .snk file that was used to build the assembly for the destination environment.</span></span>  
  
-   <span data-ttu-id="27bf7-113">**案例 2。**</span><span class="sxs-lookup"><span data-stu-id="27bf7-113">**Scenario 2.**</span></span> <span data-ttu-id="27bf7-114">開發人員可以設定為自動取代新的公開金鑰 token，，如下所示的指令碼： 在指令碼開始時，叫用 「 取代公開金鑰 Token 」 公用程式，並指向包含公開金鑰 token 的.snk 檔案。</span><span class="sxs-lookup"><span data-stu-id="27bf7-114">The developer can configure the script to automatically substitute the new public key token, as follows: At the start of the script, invoke the Replace Public Key Token utility and point it to a .snk file that contains the public key token.</span></span> <span data-ttu-id="27bf7-115">在指令碼內使用環境變數 %NEWTOKEN% 來代表公開金鑰 Token。</span><span class="sxs-lookup"><span data-stu-id="27bf7-115">Within the script, use the environment variable %NEWTOKEN% to represent the public key token.</span></span> <span data-ttu-id="27bf7-116">當指令碼執行時，公用程式會從 .snk 檔案擷取公開金鑰 Token 的值，並將其設定為環境變數 %NEWTOKEN%。</span><span class="sxs-lookup"><span data-stu-id="27bf7-116">When the script runs, the utility extracts the value of the public key token from the .snk file and sets it into an environment variable %NEWTOKEN%.</span></span> <span data-ttu-id="27bf7-117">當指令碼執行時，每個 %NEWTOKEN% 執行個體都會取代為指定 .snk 檔案的公開金鑰 Token。</span><span class="sxs-lookup"><span data-stu-id="27bf7-117">When the script runs, each instance of %NEWTOKEN% will be with substituted with the public key token from the specified .snk file.</span></span> <span data-ttu-id="27bf7-118">例如：</span><span class="sxs-lookup"><span data-stu-id="27bf7-118">For example:</span></span>  
  
    ```  
    ReplacePKT.bat key.snk  
    ...  
    ...  
    gacutil /u Assembly, ... PublicKey=%NEWTOKEN% ...  
    ```  
  
## <a name="location-in-sdk"></a><span data-ttu-id="27bf7-119">SDK 中的位置</span><span class="sxs-lookup"><span data-stu-id="27bf7-119">Location in SDK</span></span>  
 <span data-ttu-id="27bf7-120">「取代公開金鑰 Token」公用程式位於：</span><span class="sxs-lookup"><span data-stu-id="27bf7-120">The Replace Public Key Token utility is located in:</span></span>  
  
 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="27bf7-121">SDK\Utilities\ReplacePublicKeyToken\\。</span><span class="sxs-lookup"><span data-stu-id="27bf7-121">SDK\Utilities\ReplacePublicKeyToken\\.</span></span>  
  
 <span data-ttu-id="27bf7-122">「取代公開金鑰 Token」公用程式是由三個檔案所組成：</span><span class="sxs-lookup"><span data-stu-id="27bf7-122">The Replace Public Key Token utility comprises three files:</span></span>  
  
-   <span data-ttu-id="27bf7-123">ReplacePKT.bat</span><span class="sxs-lookup"><span data-stu-id="27bf7-123">ReplacePKT.bat</span></span>  
  
-   <span data-ttu-id="27bf7-124">ReplacePKT.vbs</span><span class="sxs-lookup"><span data-stu-id="27bf7-124">ReplacePKT.vbs</span></span>  
  
-   <span data-ttu-id="27bf7-125">ReplacePKT.wsf</span><span class="sxs-lookup"><span data-stu-id="27bf7-125">ReplacePKT.wsf</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="27bf7-126">程序</span><span class="sxs-lookup"><span data-stu-id="27bf7-126">Procedures</span></span>  
 <span data-ttu-id="27bf7-127">請使用下列程序，利用擷取自 .snk 檔案的公開金鑰 Token，取代檔案中公開金鑰 Token 或預留位置的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="27bf7-127">Use the following procedure to replace all instances of a public key token or a placeholder in a file with a public key token extracted from an .snk file, as described in Scenario 1.</span></span>  
  
#### <a name="to-replace-instances-of-a-public-key-token-or-a-placeholder-in-a-file"></a><span data-ttu-id="27bf7-128">取代檔案中公開金鑰 Token 或預留位置的執行個體</span><span class="sxs-lookup"><span data-stu-id="27bf7-128">To replace instances of a public key token or a placeholder in a file</span></span>  
  
1. <span data-ttu-id="27bf7-129">確定三個「取代公開金鑰 Token」公用程式檔案 (ReplacePKT.bat、ReplacePKT.vbs、ReplacePKT.wsf)、指令碼檔案和 .snk 檔案都可以從本機電腦使用。</span><span class="sxs-lookup"><span data-stu-id="27bf7-129">Make sure that the three Replace Public Key Token utility files (ReplacePKT.bat, ReplacePKT.vbs, ReplacePKT.wsf), the script file, and the .snk file are all available from the local computer.</span></span>  
  
2. <span data-ttu-id="27bf7-130">在命令視窗中，將目錄變更為包含「取代公開金鑰 Token」公用程式檔案。</span><span class="sxs-lookup"><span data-stu-id="27bf7-130">In a command window, change the directory to the folder containing the Replace Public Key utility files.</span></span>  
  
3. <span data-ttu-id="27bf7-131">從命令提示字元中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="27bf7-131">From a command prompt, run the following command:</span></span>  
  
4. <span data-ttu-id="27bf7-132">**ReplacePKT \<**  *.snk 檔案* **\> \<** *舊公開金鑰語彙基元* **\>\<** *檔案取代* **\>**</span><span class="sxs-lookup"><span data-stu-id="27bf7-132">**ReplacePKT \<** *.snk file* **\> \<** *old public key token* **\> \<** *file to replace* **\>**</span></span>  
  
   |<span data-ttu-id="27bf7-133">選項</span><span class="sxs-lookup"><span data-stu-id="27bf7-133">Option</span></span>|<span data-ttu-id="27bf7-134">描述</span><span class="sxs-lookup"><span data-stu-id="27bf7-134">Description</span></span>|  
   |------------|-----------------|  
   |<span data-ttu-id="27bf7-135">**\<** *.snk 檔案* **\>**</span><span class="sxs-lookup"><span data-stu-id="27bf7-135">**\<** *.snk file* **\>**</span></span>|<span data-ttu-id="27bf7-136">.snk 檔案的完整路徑，此檔案所包含的公開金鑰 Token 會用來取代現有的公開金鑰 Token 或預留位置。</span><span class="sxs-lookup"><span data-stu-id="27bf7-136">Full path of the .snk file containing the public key token that you want substitute for the existing public key token or placeholder.</span></span>|  
   |<span data-ttu-id="27bf7-137">**\<** *舊公開金鑰語彙基元* **\>**</span><span class="sxs-lookup"><span data-stu-id="27bf7-137">**\<** *old public key token* **\>**</span></span>|<span data-ttu-id="27bf7-138">要取代的公開金鑰 Token 或預留位置。</span><span class="sxs-lookup"><span data-stu-id="27bf7-138">Public key token or placeholder that you want to replace.</span></span>|  
   |<span data-ttu-id="27bf7-139">**\<** *若要取代的檔案* **\>**</span><span class="sxs-lookup"><span data-stu-id="27bf7-139">**\<** *file to replace* **\>**</span></span>|<span data-ttu-id="27bf7-140">檔案的完整路徑，您要取代此檔案中的公開金鑰 Token 或預留位置。</span><span class="sxs-lookup"><span data-stu-id="27bf7-140">Full path of the file in which you want to replace the public key token or placeholder.</span></span>|  
  
    <span data-ttu-id="27bf7-141">範例</span><span class="sxs-lookup"><span data-stu-id="27bf7-141">Example:</span></span>  
  
    <span data-ttu-id="27bf7-142">**ReplacePKT.bat C:\Tokens\MyToken.snk 12ab3456cd789e12 C:\Scripts\MyScript.vbs**</span><span class="sxs-lookup"><span data-stu-id="27bf7-142">**ReplacePKT.bat C:\Tokens\MyToken.snk 12ab3456cd789e12 C:\Scripts\MyScript.vbs**</span></span>  
  
   <span data-ttu-id="27bf7-143">請使用下列程序自動在指令碼中設定環境變數，以使用衍生自 .snk 檔案的公開金鑰 Token，如案例 2 所述。</span><span class="sxs-lookup"><span data-stu-id="27bf7-143">Use the following procedure to automatically set an environment variable in a script that uses a public key token derived from an .snk file, as described in Scenario 2.</span></span>  
  
#### <a name="to-set-an-environment-variable-that-uses-a-public-key-token"></a><span data-ttu-id="27bf7-144">設定使用公開金鑰 Token 的環境變數</span><span class="sxs-lookup"><span data-stu-id="27bf7-144">To set an environment variable that uses a public key token</span></span>  
  
1.  <span data-ttu-id="27bf7-145">在指令碼檔案開頭加入以下的程式碼行：</span><span class="sxs-lookup"><span data-stu-id="27bf7-145">At the beginning of your script file, add the following line of code:</span></span>  
  
    ```  
    ReplacePKT <filename>.snk  
    ```  
  
     <span data-ttu-id="27bf7-146">何處\<*檔名*\>是要從中衍生的公開金鑰 token 的.snk 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="27bf7-146">Where \<*filename*\> is the name of the .snk file from which to derive the public key token.</span></span>  
  
    ```  
    Example: ReplacePKT.bat MyToken.snk  
    ```  
  
2.  <span data-ttu-id="27bf7-147">在指令碼檔案中，使用 `%NEWTOKEN%` 來代表公開金鑰 Token。</span><span class="sxs-lookup"><span data-stu-id="27bf7-147">In your script file, use `%NEWTOKEN%` to represent the public key token.</span></span>  
  
     <span data-ttu-id="27bf7-148">範例</span><span class="sxs-lookup"><span data-stu-id="27bf7-148">Example:</span></span>  
  
    ```  
    PublicKey=%NEWTOKEN%  
    ```  
  
3.  <span data-ttu-id="27bf7-149">將指令碼檔案提供給使用者時，請包含構成「取代公開金鑰 Token」公用程式的三個檔案 (ReplacePKT.bat、ReplacePKT.vbs、ReplacePKT.wsf)。</span><span class="sxs-lookup"><span data-stu-id="27bf7-149">When you deliver your script file to your users, include the three files that comprise the Replace Public Key Token utility (ReplacePKT.bat, ReplacePKT.vbs, ReplacePKT.wsf).</span></span> <span data-ttu-id="27bf7-150">請確定指令碼使用者先將所有這些檔案複製到檔案系統上的相同資料夾中，然後再執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="27bf7-150">Make sure that users of your script copy all of the files to the same folder on the file system before running your script.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27bf7-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27bf7-151">See Also</span></span>  
 [<span data-ttu-id="27bf7-152">SDK 中的公用程式</span><span class="sxs-lookup"><span data-stu-id="27bf7-152">Utilities in the SDK</span></span>](../core/utilities-in-the-sdk.md)