---
title: 使用前置和後置處理指令碼自訂應用程式部署 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- customizing, applications
- applications, customizing
- scripts, applications
- scripts, customizing
ms.assetid: 47627394-d594-491b-9098-38c5d028a378
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7dc0afd7ed042f475a9a008125c968f401e6df92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287166"
---
# <a name="using-pre--and-post-processing-scripts-to-customize-application-deployment"></a><span data-ttu-id="364e7-102">使用前置和後置處理指令碼自訂應用程式部署</span><span class="sxs-lookup"><span data-stu-id="364e7-102">Using Pre- and Post-processing Scripts to Customize Application Deployment</span></span>
<span data-ttu-id="364e7-103">本節中的主題描述如何建立前置或後置處理指令碼，以便在匯入、安裝或解除安裝應用程式時執行動作。</span><span class="sxs-lookup"><span data-stu-id="364e7-103">The topics in this section describe how to create pre- or post-processing scripts to perform actions when an application is imported, installed, or uninstalled.</span></span> <span data-ttu-id="364e7-104">前置處理指令碼會在應用程式匯入或安裝開始前，以及在解除安裝完成後，執行一項動作或一組動作。</span><span class="sxs-lookup"><span data-stu-id="364e7-104">Pre-processing scripts perform an action or set of actions before application import or installation starts, and after uninstallation completes.</span></span> <span data-ttu-id="364e7-105">後置處理指令碼會在應用程式匯入或安裝完成後，或在解除安裝開始前，執行一項動作或一組動作。</span><span class="sxs-lookup"><span data-stu-id="364e7-105">Post-processing scripts perform an action or set of actions after application import or installation completes, or before uninstallation starts.</span></span>  
  
 <span data-ttu-id="364e7-106">例如，您可能想要包含會在安裝前執行的前置處理指令碼，以便在安裝期間覆寫資源檔以前，備份這些資源檔。</span><span class="sxs-lookup"><span data-stu-id="364e7-106">You might, for example, want to include a pre-processing script that will run before installation to back up resource files before they are overwritten during installation.</span></span> <span data-ttu-id="364e7-107">或者您可能想要執行後置處理指令碼，在安裝應用程式後將憑證新增到憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="364e7-107">Or you might want to run a post-processing script to add a certificate to the certificate store after an application is installed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="364e7-108">BizTalk Server 包括範例前置和後置處理指令碼。</span><span class="sxs-lookup"><span data-stu-id="364e7-108">BizTalk Server includes sample pre- and post-processing scripts.</span></span> <span data-ttu-id="364e7-109">使用範例指令碼的相關資訊，請參閱[範本 （應用程式部署範例）](../core/template-application-deployment-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="364e7-109">For information about using the sample scripts, see [Template (Application Deployment Sample)](../core/template-application-deployment-sample.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="364e7-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="364e7-110">In This Section</span></span>  
  
-   [<span data-ttu-id="364e7-111">建立前置或後置處理指令碼</span><span class="sxs-lookup"><span data-stu-id="364e7-111">Creating a Pre- or Post-processing Script</span></span>](../core/creating-a-pre-or-post-processing-script.md)  
  
-   [<span data-ttu-id="364e7-112">環境變數如何指示部署狀態</span><span class="sxs-lookup"><span data-stu-id="364e7-112">How Environment Variables Indicate Deployment State</span></span>](../core/how-environment-variables-indicate-deployment-state.md)  
  
-   [<span data-ttu-id="364e7-113">在部署期間檔案成品的狀態</span><span class="sxs-lookup"><span data-stu-id="364e7-113">Status of File Artifacts During Deployment</span></span>](../core/status-of-file-artifacts-during-deployment.md)  
  
-   [<span data-ttu-id="364e7-114">前置和後置處理指令碼環境變數</span><span class="sxs-lookup"><span data-stu-id="364e7-114">Pre- and Post-processing Script Environment Variables</span></span>](../core/pre-and-post-processing-script-environment-variables.md)