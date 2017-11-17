---
title: "匯出 Bindings6 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings, exporting
- exporting, bindings
ms.assetid: 052a429e-3237-44d4-8933-00aa5edfb212
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3362984eca1dcec4fb68bfbac92c30da81de8a3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="exporting-bindings"></a><span data-ttu-id="b7142-102">匯出繫結</span><span class="sxs-lookup"><span data-stu-id="b7142-102">Exporting Bindings</span></span>
<span data-ttu-id="b7142-103">本節中的主題描述如何將 BizTalk 群組、組件或應用程式的繫結匯出至 .xml 檔案中</span><span class="sxs-lookup"><span data-stu-id="b7142-103">The topics in this section describe how to export bindings for a BizTalk group, assembly, or application into an .xml file.</span></span> <span data-ttu-id="b7142-104">(繫結會定義主控件、傳送埠、傳送埠群組、接收埠、接收位置和合作對象如何與協調流程、管線、對應和結構描述產生關聯)。之後您可以將這些繫結從 .xml 檔案匯入到其他群組或應用程式。</span><span class="sxs-lookup"><span data-stu-id="b7142-104">(Bindings define how hosts, send ports, send port groups, receive ports, receive locations, parties are associated with orchestrations, pipelines, maps, and schemas.) You can then import the bindings from the .xml file into another group or application.</span></span> <span data-ttu-id="b7142-105">匯入繫結會覆寫群組或應用程式中任何同名的現有繫結。</span><span class="sxs-lookup"><span data-stu-id="b7142-105">Importing bindings overwrites any existing bindings of the same name in the group or application.</span></span> <span data-ttu-id="b7142-106">您也可以將繫結加入應用程式中，這樣並不會覆寫現有的繫結。</span><span class="sxs-lookup"><span data-stu-id="b7142-106">You can also add bindings to an application, which does not overwrite existing bindings.</span></span> <span data-ttu-id="b7142-107">加入的繫結會在您匯入該應用程式之後才生效。</span><span class="sxs-lookup"><span data-stu-id="b7142-107">The bindings that you add do not take effect until you import the application.</span></span>  
  
 <span data-ttu-id="b7142-108">您可能會在下列實例中發現，使用繫結檔案時就不需要手動設定繫結，因此可以加速應用程式部署：</span><span class="sxs-lookup"><span data-stu-id="b7142-108">You may find that using binding files speeds application deployment in the following scenarios by avoiding the need to manually configure bindings:</span></span>  
  
-   <span data-ttu-id="b7142-109">將應用程式從一個部署環境移動到另一個部署環境。</span><span class="sxs-lookup"><span data-stu-id="b7142-109">Moving an application from one deployment environment to another.</span></span>  
  
-   <span data-ttu-id="b7142-110">更新組件。</span><span class="sxs-lookup"><span data-stu-id="b7142-110">Updating an assembly.</span></span>  
  
-   <span data-ttu-id="b7142-111">將組件及其繫結一併部署到多個 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="b7142-111">Deploying an assembly together with its bindings to multiple BizTalk groups.</span></span>  
  
 <span data-ttu-id="b7142-112">如需有關如何針對這些用途使用繫結檔案的詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="b7142-112">For more information about using binding files for these purposes, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).</span></span>  
  
 <span data-ttu-id="b7142-113">如需有關匯入及新增繫結的詳細資訊，請參閱[如何匯入繫結至 BizTalk 群組](../core/how-to-import-bindings-into-a-biztalk-group.md)，[如何匯入到 BizTalk 應用程式的繫結](../core/how-to-import-bindings-into-a-biztalk-application.md)，和[如何新增繫結應用程式的檔案](../core/how-to-add-a-binding-file-to-an-application2.md)。</span><span class="sxs-lookup"><span data-stu-id="b7142-113">For more information about importing and adding bindings, see [How to Import Bindings into a BizTalk Group](../core/how-to-import-bindings-into-a-biztalk-group.md), [How to Import Bindings into a BizTalk Application](../core/how-to-import-bindings-into-a-biztalk-application.md), and [How to Add a Binding File to an Application](../core/how-to-add-a-binding-file-to-an-application2.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b7142-114">繫結檔案可能包含敏感性資料。</span><span class="sxs-lookup"><span data-stu-id="b7142-114">The binding file may contain sensitive data.</span></span> <span data-ttu-id="b7142-115">請務必採取步驟來確保檔案安全。</span><span class="sxs-lookup"><span data-stu-id="b7142-115">Be sure to take steps to secure the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7142-116">基於安全性理由，當您匯出繫結檔案時，BizTalk Server 會從該檔案移除繫結的密碼。</span><span class="sxs-lookup"><span data-stu-id="b7142-116">For security reasons, when you export a binding file, BizTalk Server removes the passwords for the bindings from the file.</span></span> <span data-ttu-id="b7142-117">匯入繫結後，您必須重新設定密碼，傳送埠和接受位置才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="b7142-117">After importing the bindings, you must reconfigure passwords for send ports and receive locations before they will function.</span></span> <span data-ttu-id="b7142-118">您可以在 BizTalk Server 管理主控台的 [傳輸屬性] 對話方塊中，為傳送埠或接收位置設定密碼。</span><span class="sxs-lookup"><span data-stu-id="b7142-118">You configure passwords in the Transport Properties dialog box of the BizTalk Server Administration console for the send port or receive location.</span></span> <span data-ttu-id="b7142-119">如需指示，請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。</span><span class="sxs-lookup"><span data-stu-id="b7142-119">For instructions, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md).</span></span> <span data-ttu-id="b7142-120">另請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="b7142-120">See also [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b7142-121">本節內容</span><span class="sxs-lookup"><span data-stu-id="b7142-121">In This Section</span></span>  
  
-   [<span data-ttu-id="b7142-122">如何匯出 BizTalk 群組的繫結</span><span class="sxs-lookup"><span data-stu-id="b7142-122">How to Export Bindings for a BizTalk Group</span></span>](../core/how-to-export-bindings-for-a-biztalk-group.md)  
  
-   [<span data-ttu-id="b7142-123">如何匯出 BizTalk 應用程式的繫結</span><span class="sxs-lookup"><span data-stu-id="b7142-123">How to Export Bindings for a BizTalk Application</span></span>](../core/how-to-export-bindings-for-a-biztalk-application.md)  
  
-   [<span data-ttu-id="b7142-124">如何匯出 BizTalk 組件的繫結</span><span class="sxs-lookup"><span data-stu-id="b7142-124">How to Export Bindings for a BizTalk Assembly</span></span>](../core/how-to-export-bindings-for-a-biztalk-assembly.md)  
  
-   [<span data-ttu-id="b7142-125">如何匯出 EDI AS2 方案的繫結</span><span class="sxs-lookup"><span data-stu-id="b7142-125">How to Export Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-export-bindings-for-an-edi-as2-solution.md)