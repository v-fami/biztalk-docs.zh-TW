---
title: 建立和修改 BizTalk 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [applications], modifying
- managing [applications], creating
- applications, modifying
- applications, creating
- modifying, applications
- creating, applications
ms.assetid: d6c9ff3a-3903-40ec-bcaa-e46cbaf8a58d
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5daa9630fb8ad742d34421478a19081ad5c83f50
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238142"
---
# <a name="creating-and-modifying-biztalk-applications"></a><span data-ttu-id="c1a98-102">建立和修改 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="c1a98-102">Creating and Modifying BizTalk Applications</span></span>
<span data-ttu-id="c1a98-103">本節說明如何使用 BizTalk Server 管理主控台或 BTSTask 命令列工具來建立、設定及修改 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c1a98-103">This section describes how to use the BizTalk Server Administration console or the BTSTask command-line tool to create, configure, and modify BizTalk applications.</span></span>  
  
 <span data-ttu-id="c1a98-104">如需有關建立、 管理、 部署和更新 BizTalk 應用程式，請參閱[瞭解 BizTalk 應用程式部署和管理](../core/understanding-biztalk-application-deployment-and-management.md)。</span><span class="sxs-lookup"><span data-stu-id="c1a98-104">For background information on creating, managing, deploying, and updating BizTalk applications, see [Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md).</span></span> <span data-ttu-id="c1a98-105">如需管理成品，包括編輯其屬性，請參閱[管理成品](../core/managing-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="c1a98-105">For information about managing artifacts, including editing their properties, see [Managing Artifacts](../core/managing-artifacts.md).</span></span> <span data-ttu-id="c1a98-106">如需部署 BizTalk 應用程式的指示，請參閱[部署 BizTalk 應用程式](../core/deploying-biztalk-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="c1a98-106">For instructions on deploying BizTalk applications, see [Deploying BizTalk Applications](../core/deploying-biztalk-applications.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1a98-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="c1a98-107">In This Section</span></span>  
  
-   [<span data-ttu-id="c1a98-108">如何建立應用程式</span><span class="sxs-lookup"><span data-stu-id="c1a98-108">How to Create an Application</span></span>](../core/how-to-create-an-application.md)  
  
-   [<span data-ttu-id="c1a98-109">如何設定應用程式</span><span class="sxs-lookup"><span data-stu-id="c1a98-109">How to Configure an Application</span></span>](../core/how-to-configure-an-application.md)  
  
-   [<span data-ttu-id="c1a98-110">如何變更應用程式的名稱</span><span class="sxs-lookup"><span data-stu-id="c1a98-110">How to Change the Name of an Application</span></span>](../core/how-to-change-the-name-of-an-application.md)  
  
-   [<span data-ttu-id="c1a98-111">如何建立或新增成品</span><span class="sxs-lookup"><span data-stu-id="c1a98-111">How to Create or Add an Artifact</span></span>](../core/how-to-create-or-add-an-artifact.md)  
  
-   [<span data-ttu-id="c1a98-112">如何將連結到讀我檔案</span><span class="sxs-lookup"><span data-stu-id="c1a98-112">How to Link to a Readme File</span></span>](../core/how-to-link-to-a-readme-file.md)  
  
-   [<span data-ttu-id="c1a98-113">如何將 64 位元成品新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="c1a98-113">How to Add a 64-Bit Artifact to an Application</span></span>](../core/how-to-add-a-64-bit-artifact-to-an-application.md)  
  
-   [<span data-ttu-id="c1a98-114">如何變更預設應用程式</span><span class="sxs-lookup"><span data-stu-id="c1a98-114">How to Change the Default Application</span></span>](../core/how-to-change-the-default-application.md)  
  
-   [<span data-ttu-id="c1a98-115">如何加入另一個應用程式的參考</span><span class="sxs-lookup"><span data-stu-id="c1a98-115">How to Add a Reference to Another Application</span></span>](../core/how-to-add-a-reference-to-another-application.md)  
  
-   [<span data-ttu-id="c1a98-116">如何檢視應用程式的參考</span><span class="sxs-lookup"><span data-stu-id="c1a98-116">How to View the References of an Application</span></span>](../core/how-to-view-the-references-of-an-application.md)  
  
-   [<span data-ttu-id="c1a98-117">如何移除另一個應用程式的參考</span><span class="sxs-lookup"><span data-stu-id="c1a98-117">How to Remove a Reference to Another Application</span></span>](../core/how-to-remove-a-reference-to-another-application.md)  
  
-   [<span data-ttu-id="c1a98-118">如何將成品移至不同的應用程式</span><span class="sxs-lookup"><span data-stu-id="c1a98-118">How to Move an Artifact to a Different Application</span></span>](../core/how-to-move-an-artifact-to-a-different-application.md)  
  
-   [<span data-ttu-id="c1a98-119">如何從應用程式移除成品</span><span class="sxs-lookup"><span data-stu-id="c1a98-119">How to Remove an Artifact from an Application</span></span>](../core/how-to-remove-an-artifact-from-an-application.md)