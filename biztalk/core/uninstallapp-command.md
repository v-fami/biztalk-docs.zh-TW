---
title: "UninstallApp 命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f45c9530-8138-40f1-b279-1428c5a7fbbc
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea94335882ffbcf01b69c450ef4a5eb80ef4fa3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="uninstallapp-command"></a><span data-ttu-id="78ec2-102">UninstallApp 命令</span><span class="sxs-lookup"><span data-stu-id="78ec2-102">UninstallApp Command</span></span>
<span data-ttu-id="78ec2-103">從本機電腦解除安裝 BizTalk 應用程式，同時將應用程式從 [控制台] 的 [新增或移除程式] 所列程式清單中移除。</span><span class="sxs-lookup"><span data-stu-id="78ec2-103">Uninstalls a BizTalk application from the local computer and also removes the application from the list of programs in Add or Remove Programs in Control Panel.</span></span> <span data-ttu-id="78ec2-104">此命令與使用 [新增或移除程式] 移除應用程式具有同樣的效果。</span><span class="sxs-lookup"><span data-stu-id="78ec2-104">This command has the same effect as removing an application by using Add or Remove Programs.</span></span> <span data-ttu-id="78ec2-105">如果應用程式是由多個 .msi 檔案經數次安裝，便會解除安裝所有 .msi 檔案安裝的全部項目。</span><span class="sxs-lookup"><span data-stu-id="78ec2-105">If multiple .msi files have been installed for this application, all of the items installed by all of the .msi files are uninstalled.</span></span>  
  
 <span data-ttu-id="78ec2-106">使用此命令時所指定的應用程式名稱必須與 [新增或移除程式] 中顯示的應用程式名稱一致。</span><span class="sxs-lookup"><span data-stu-id="78ec2-106">The application name that you specify for this command must match the name of the application as displayed in Add or Remove Programs.</span></span> <span data-ttu-id="78ec2-107">如果您不確定的應用程式名稱，您可以使用**ListPackage**命令來取得它，如中所述[ListPackage 命令](../core/listpackage-command.md)。</span><span class="sxs-lookup"><span data-stu-id="78ec2-107">If you are unsure of the application name, you can use the **ListPackage** command to obtain it, as described in [ListPackage Command](../core/listpackage-command.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="78ec2-108">雖然按兩下 .msi 檔案或許可以解除安裝應用程式，事實上並不支援這種做法。</span><span class="sxs-lookup"><span data-stu-id="78ec2-108">Although it is possible to uninstall an application by double-clicking the .msi file, doing this is not supported.</span></span> <span data-ttu-id="78ec2-109">其原因在於同一個應用程式可能是由多個 .msi 檔案經數次安裝，以致這種做法未必能夠解除安裝與應用程式相關聯的所有項目。</span><span class="sxs-lookup"><span data-stu-id="78ec2-109">This is because multiple .msi files can be installed for the same application, and using this method will not uninstall all of the items associated with the application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="78ec2-110">使用方式</span><span class="sxs-lookup"><span data-stu-id="78ec2-110">Usage</span></span>  
 <span data-ttu-id="78ec2-111">**BTSTask UninstallApp /ApplicationName:** *值*</span><span class="sxs-lookup"><span data-stu-id="78ec2-111">**BTSTask UninstallApp /ApplicationName:** *value*</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="78ec2-112">參數</span><span class="sxs-lookup"><span data-stu-id="78ec2-112">Parameters</span></span>  
  
|<span data-ttu-id="78ec2-113">參數</span><span class="sxs-lookup"><span data-stu-id="78ec2-113">Parameter</span></span>|<span data-ttu-id="78ec2-114">Required</span><span class="sxs-lookup"><span data-stu-id="78ec2-114">Required</span></span>|<span data-ttu-id="78ec2-115">Description</span><span class="sxs-lookup"><span data-stu-id="78ec2-115">Description</span></span>|  
|---------------|--------------|-----------------|  
|<span data-ttu-id="78ec2-116">**/ ApplicationName** (或**/A**，請參閱 < 備註 >)</span><span class="sxs-lookup"><span data-stu-id="78ec2-116">**/ApplicationName** (or **/A**, see Remarks)</span></span>|<span data-ttu-id="78ec2-117">是</span><span class="sxs-lookup"><span data-stu-id="78ec2-117">Yes</span></span>|<span data-ttu-id="78ec2-118">要解除安裝的 BizTalk 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="78ec2-118">Name of the BizTalk application to uninstall.</span></span> <span data-ttu-id="78ec2-119">如果名稱包含空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="78ec2-119">If the name includes spaces, you must enclose it in double quotation marks (").</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="78ec2-120">範例</span><span class="sxs-lookup"><span data-stu-id="78ec2-120">Sample</span></span>  
 <span data-ttu-id="78ec2-121">**BTSTask UninstallApp /applicationname: myapplication**</span><span class="sxs-lookup"><span data-stu-id="78ec2-121">**BTSTask UninstallApp /ApplicationName:MyApplication**</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78ec2-122">備註</span><span class="sxs-lookup"><span data-stu-id="78ec2-122">Remarks</span></span>  
 <span data-ttu-id="78ec2-123">參數不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="78ec2-123">Parameters are not case-sensitive.</span></span> <span data-ttu-id="78ec2-124">您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。</span><span class="sxs-lookup"><span data-stu-id="78ec2-124">You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78ec2-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78ec2-125">See Also</span></span>  
 <span data-ttu-id="78ec2-126">[BTSTask 命令列參考](../core/btstask-command-line-reference.md) </span><span class="sxs-lookup"><span data-stu-id="78ec2-126">[BTSTask Command-Line Reference](../core/btstask-command-line-reference.md) </span></span>  
 [<span data-ttu-id="78ec2-127">如何解除安裝 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="78ec2-127">How to Uninstall a BizTalk Application</span></span>](../core/how-to-uninstall-a-biztalk-application.md)